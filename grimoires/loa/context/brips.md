# Berachain Improvement Proposals (BRIPs)

*Source: Official Berachain BRIP repository. Data as of March 17, 2026.*

BRIPs are Berachain's formal design document process for proposed changes to the protocol, tooling, and standards. They serve as both a structured review mechanism and a historical record of technical decisions.

---

## BRIP Process (BRIP-0000)

**Type**: Meta | **Status**: Final | **Author**: aBear | **Created**: Apr 14, 2025

The BRIP process defines lifecycle stages:

- **Draft** → **Review** → **Accepted** → **Final**
- Alternative exits: **Rejected** or **Withdrawn**
- Living status available for continuously updated documents

**Types**: Core (consensus changes), Informational (descriptive), Meta (process changes). Note: Standard type was proposed but struck from the process.

Editors act as neutral stewards, not gatekeepers. Authors may request transitions; editors apply them based on community input.

---

## BRIP-0001: Execution Layer Forked Clients

**Type**: Core | **Status**: Accepted | **Authors**: calbera, rezbera | **Created**: Jun 2, 2025

### Context
Berachain launched with unmodified EL clients (Geth, Reth, Nethermind) to maximize developer compatibility. After 4+ months of mainnet observation, forking became necessary due to fundamental differences from Ethereum: significantly sparser network topology, 2-second block times, and instant finality vs. Ethereum's 12-second blocks and ~12-minute finality.

### Decision
Berachain Labs exclusively supports **bera-geth** and **bera-reth** forks going forward. All major EIPs from upstream Ethereum hard forks will continue to be adopted.

### Key Specifications
- **Fork naming convention**: Ethereum hard fork name + iteration number. Example: first modification on Prague fork = `Prague1`, second = `Prague2`. Mirrors beacon-kit's convention (e.g. `Deneb1`, `Electra1`)
- **Release naming**: Mirrors op-geth pattern — upstream version embedded in release string (e.g. `v1.101511.0` = built on upstream v1.15.11, `.0` = first release on that base)
- **Diff maintenance**: Using @protolambda's Fork Diff tool for clean upstream merge tracking
- **Rationale**: Standard practice across all major non-Ethereum EVM chains (Optimism, Polygon, Arbitrum, etc.)

---

## BRIP-0002: Gas Fee Modifications

**Type**: Core | **Status**: Accepted | **Author**: rezbera | **Created**: May 29, 2025

**Requires**: BRIP-0001 (EL fork)

### Changes
Two complementary modifications to Berachain's fee market:

**1. Minimum Gas Price Floor**: 1 gwei (1 × 10⁹ wei) — prevents spam via near-zero arbitrage flooding.

**2. Modified Base Fee Adjustment**: `BASE_FEE_MAX_CHANGE_DENOMINATOR` changed from 8 → 48.

### Rationale
With 2-second blocks, the original 12.5% max swing per block = 6.25% per second fluctuation — far exceeding Ethereum's ~1.05%/second. Changing the denominator to 48 reduces the per-block swing to ~2.1%, matching Ethereum's per-second volatility profile (~1.05%/second). Wallets can now predict base fees with Ethereum-equivalent reliability.

### Implementation
```
MIN_BASE_FEE = 1 gwei
BASE_FEE_MAX_CHANGE_DENOMINATOR = 48  (was: 8)
```
A hard fork is required. Backward-compatible with existing wallets and applications.

---

## BRIP-0003: Stable Block Time (SBT)

**Type**: Core | **Status**: Accepted | **Authors**: aBear, fridrik01 | **Created**: Jun 16, 2025

### Problem
Validators previously controlled block timing via a static `timeout_commit` parameter (default 500ms). This created inconsistent block intervals and assumed ⅔ of validators would agree on configuration — without dynamic adaptability to network stalls or multi-round consensus.

### Solution
Algorithmic delay model that dynamically targets a fixed average block interval (2 seconds):

```
expectedBlockTime = initialTime + (TargetBlockTime × (currentHeight - initialHeight))
```

- If blocks are early: add delay
- If blocks are on time: proceed immediately  
- If blocks are late: catch up rapidly
- If chain halted >5 minutes (`MaxDelayBetweenBlocks`): reset checkpoint to prevent block rush

### Key Parameters
- `TargetBlockTime`: 2 seconds
- `MaxDelayBetweenBlocks`: 5 minutes (resets checkpoint if exceeded, avoiding catch-up rushes after halts/upgrades)
- `SBTEnableHeight`: New consensus parameter — SBT activates at specified block height; cannot be disabled once enabled
- State sync not supported in v1 (future work)

**Significance for PoL**: Stabilizes BGT inflation by ensuring consistent block production intervals.

---

## BRIP-0004: Enshrined Proof of Liquidity

*Note: BRIP-0004 document was not included in this knowledge base. It is referenced as a dependency by BRIP-0005, BRIP-0006, and BRIP-0009. Key outputs referenced in those BRIPs:*

- Introduced **real-time cutting board execution** (eliminated queue delays)
- Introduced **`valRewardAllocator` role** — a hot key for cutting board management separate from the cold `operator` key
- Introduced **`ParentProposerPubkey`** field in execution block headers — enables enshrined PoL reward distribution by identifying the block proposer on-chain
- Required bera-geth fork (bera-geth `core/types/block.go` modification)

---

## BRIP-0005: Default BGT Distribution Strategy for Validators

**Type**: Core | **Status**: Draft | **Authors**: rezbera, calbera, aBear, fridrik01 | **Created**: Aug 27, 2025

**Requires**: BRIP-0004

### Problem
Even with real-time cutting boards (BRIP-0004), validators must manually configure allocations. Optimal configuration requires deep technical knowledge of incentive markets and constant monitoring. Most validators lack the sophistication or time to do this well.

### Solution
Opt-in **sidecar service** that automatically computes and executes optimal BGT distribution strategies. The execution client queries the sidecar when building blocks; the sidecar returns signed cutting board transactions to include as the first transactions in the block.

### Architecture
- **Execution client**: Sends current block number to sidecar via HTTP POST to `/strategy`; includes resulting signed transactions at start of block; falls back gracefully if sidecar times out
- **Sidecar**: Maintains own data (incentive data, vault info, pricing oracles); signs transactions with `valRewardAllocator` key; manages hot key rotation
- **Strategy**: Maximize USD value of incentives captured, using offchain/onchain price oracles

### Key Design Decisions
- Sidecar receives only block number (not full block context) in Phase 1 — simpler, faster to ship
- Same sidecar works for both bera-geth and bera-reth
- Compromise exposure limited: worst case is BGT directed to wrong vaults until `operator` key revokes

### Phases
- **Phase 1**: Block number only in sidecar request; strategy transactions at start of block
- **Phase 2**: Execution receipts of partially-built block included; strategy transactions at end of block for better state visibility

**Status**: Draft. Strategy algorithm not yet fully specified.

---

## BRIP-0006: Baseline Cutting Board Automation

**Type**: PoL | **Status**: Draft | **Authors**: astro-bera, bar-bera, GrizzlyBera | **Created**: Oct 17, 2025

**Requires**: BRIP-0004

### Problem
The "passive validator" problem: validators who don't update cutting boards emit BGT to vaults with no active incentives, degrading overall PoL economic efficiency. BRIP-0005 addresses active validators who want to optimize; BRIP-0006 addresses the baseline for all others.

### Solution
Foundation-managed **baseline cutting board** maintained by an offchain bot, with automatic fallback for inactive validators.

### Mechanism
- New contract: **RewardAllocatorFactory** — holds baseline allocation, managed by `ALLOCATION_SETTER` role (granted to Foundation)
- Modified **BeraChef**: If a validator hasn't updated their cutting board within `raInactivityBlockSpan` blocks, `getActiveRewardAllocation` returns the baseline allocation instead
- `raInactivityBlockSpan` is a governance-controlled parameter

### Baseline Strategy Algorithm
For each whitelisted vault and each whitelisted incentive token:
1. Get token price from Pyth (skip if stale per `PRICE_TTL`)
2. Calculate USD yield per BGT (`emissionUsdPerBgt`)
3. Adjust for vault depletion risk (cap yield if remaining incentives insufficient)
4. Rank vaults by yield; allocate max weight to highest yielding vaults first

Returns ordered allocations filling `BeraChef.maxNumWeightsPerRewardAllocation` slots. Returns `NO_STRATEGY` if no viable vaults found.

**Note**: Complementary to BRIP-0005, not a replacement. BRIP-0005 = active validator optimization. BRIP-0006 = passive fallback.

---

## BRIP-0007: Berachain Preconfirmations

**Type**: Core | **Status**: Draft | **Authors**: rezbera, calbera, aBear, fridrik01, grizzlybera, tio | **Created**: Oct 22, 2025

### Summary
A pre-confirmation system providing significantly reduced transaction inclusion latency — targeting sub-200ms confirmations for users who accept relaxed trust assumptions. Opt-in fast path that does not reduce safety of the base consensus layer.

### Architecture Components

**Sequencer** (extension on Bera-Reth):
- Begins building partial blocks when Beacon-Kit signals an upcoming proposer whitelisted for preconf
- Executes transactions in parallel against in-memory state; seals partial blocks every ~200ms
- Broadcasts sealed partial blocks to configured RPC nodes via `preconf_newPartialBlock` websocket API
- Provides full block to Beacon-Kit for CometBFT consensus when `engine_getPayload` called

**RPC Nodes** (Bera-Reth with optional add-on):
- Receive and validate partial block signatures against known sequencer public key
- Re-execute partial blocks against current state for validity
- Override standard Ethereum APIs (`eth_getBalance`, `eth_getTransactionCount`, `eth_getBlockByNumber`, etc.) to serve pre-confirmed state when available
- Partial block state held in memory only; reverted immediately on new canonical head

**Beacon-Kit modifications**:
- Validates that next proposer is in the preconf whitelist before triggering sequencer payload building
- Validators in preconf network preference sequencer payloads but validate against local state via `NewPayload`
- Fallback to local block building if: sequencer provides invalid block, sequencer out of sync, or `GetPayload` times out

### Design Principles
- **Liveness first**: Any component failure → chain falls back to standard 2s block building seamlessly
- **Consistency**: Pre-confirmed state targets finalization, but rare reorgs possible in disaster scenarios. CEXs and latency-sensitive apps may choose to avoid preconf
- **Minimal operator overhead**: Built as Bera-Reth extension rather than new binary

### Adoption Plan
- Phase 1: Select validators, dedicated preconf RPC endpoints
- Phase 2: Wider validator rollout, dedicated endpoints
- Phase 3: Most validators, standard RPC endpoints serve preconf state

---

## BRIP-0009: Deprecation of bera-geth

**Type**: Core | **Status**: Draft | **Authors**: calbera, fridrik01, grizzlybera | **Created**: Jan 11, 2026

**Requires**: BRIP-0001, BRIP-0004

### Decision
Deprecate **bera-geth** (Go-ethereum fork). Consolidate exclusively to **bera-reth** (Rust/Reth SDK fork) as the single supported execution client.

### Rationale
- **Future protocol features** (specifically BRIP-0007 preconfirmations) require deep reth-sdk integration for block builder and RPC modifications — already available in Rust ecosystem, would require major architectural changes in Go
- **Maintenance overhead**: Duplicate CI/CD, dual upstream merge processes, doubled audit surface for every protocol change
- **Reth SDK architecture**: Cleaner modularity for Berachain-specific features; better compatibility with ecosystem tooling (e.g., Flashbots' rbuilder)
- **Performance**: Rust characteristics better suited to 2s block times

### Required Migration
**beacon-kit dependency**: beacon-kit currently imports bera-geth as a library for the `ParentProposerPubkey` field (introduced by BRIP-0004). To complete deprecation:
1. Implement `ParentProposerPubkey` logic directly in beacon-kit
2. Remove bera-geth from `go.mod`
3. Update `geth-primitives` package to work with upstream go-ethereum types

**Validators**: Must migrate from bera-geth to bera-reth during the transition window. No hard fork required for the deprecation itself — both clients implement the same protocol.

### Security Note
Moving to a single execution client increases centralization risk: if bera-reth has a bug, there is no alternative client to "disagree" with it. This is acknowledged as a tradeoff.

---

## Execution Timeline (Real-World)

**Bera-Geth Sunset Announcement**: March 13, 2026 (@berachaindevs)
- All node operators must switch to bera-reth
- Security patches for bera-geth continue until **April 9, 2026**
- A chain fork **after April 9** will cause bera-geth clients to lose consensus and stop following the chain
- Migration resources: docs.berachain.com (quickstart, monitoring, production checklist)
- New snapshot distribution points: snapshots.berachain.com and bepolia.snapshots.berachain.com

---

## BRIP Dependency Map

```
BRIP-0001 (EL Fork)
    └── BRIP-0002 (Gas Fees) — requires fork to enforce
    └── BRIP-0009 (Deprecate bera-geth) — builds on fork decision

BRIP-0004 (Enshrined PoL) [not in knowledge base]
    └── BRIP-0005 (Validator Sidecar) — requires real-time cutting board
    └── BRIP-0006 (Baseline Cutting Board) — requires real-time cutting board
    └── BRIP-0009 (Deprecate bera-geth) — ParentProposerPubkey migration

BRIP-0007 (Preconfirmations) — motivates BRIP-0009 (needs reth-sdk)
```

---

## Known Gaps

- **BRIP-0004 full text**: Not in this knowledge base. Referenced indirectly through dependent BRIPs.
- **BRIP-0008**: Not included — unknown status/content.
- **BRIP-0005 strategy algorithm**: Marked TODO in the draft; not fully specified.
- **BRIP-0006 implementation**: Bot and smart contracts to be open-sourced; not yet deployed.
- **BRIP-0007 sequencer**: Not yet deployed as of March 17, 2026; Phase 1 rollout ongoing.
