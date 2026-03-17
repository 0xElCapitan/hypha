# Berachain Core Mechanics

## What is Berachain?

Berachain is an EVM-identical Layer 1 blockchain built on Proof-of-Liquidity (PoL) and the BeaconKit modular consensus framework. It delivers high performance while maintaining full compatibility with Ethereum tooling and upgrades.

**EVM Identical**: Same execution runtime as Ethereum Mainnet. Uses lightly modified forks of Geth and Reth. Supports all standard RPC namespaces. Any EVM upgrade (e.g., Dencun) can be adopted immediately.

**BeaconKit**: Modular consensus framework developed by Berachain. Integrates CometBFT consensus for single-slot finality (SSF), optimistic payload building (reduces block times ~40%), and full EIP compatibility.

---

## Proof of Liquidity (PoL)

PoL is Berachain's novel economic mechanism. It radically changes how L1 economics are structured — prioritizing ecosystem liquidity over baseline validator rewards.

### Core Insight
Traditional PoS chains have one token do everything: secure the chain, pay gas, govern rewards. PoL splits these functions into two tokens, separating security from incentives.

### The Two-Token Model

**$BERA** — Gas and security token
- Validators stake BERA to secure the chain and join the Active Set
- Minimum stake: 250,000 BERA | Maximum: 10,000,000 BERA
- Active Set: Top 69 validators by BERA stake
- Block proposal probability proportional to staked BERA
- Gas fees are burned (deflationary pressure)
- Can be staked in the BERA PoL Yield Vault (sWBERA) for 33% of redirected PoL incentives

**$BGT** — Governance and rewards token
- Soulbound: non-transferable, earned only by productive ecosystem activity
- Distributed by validators when proposing blocks
- Can be delegated to validators to boost their emissions
- Can be burned 1:1 for BERA (one-way)
- Used for governance voting (independently of delegation)
- Earns dApp fees from BEX and HoneySwap via FeeCollector

### The PoL Lifecycle

1. **Validator earns block reward**: Selected validator receives base BGT emission + variable emission based on boost percentage
2. **Validator directs emissions**: Distributes variable BGT to whitelisted Reward Vaults of their choosing (via BeraChef cutting board)
3. **Validator receives incentives**: Protocols pay incentive tokens to validators for directing BGT to their vaults
4. **Users provide liquidity**: Deposit assets into protocols, receive receipt tokens, stake in Reward Vaults
5. **Users earn BGT**: Proportional to their share of each vault
6. **BGT holders boost validators**: Delegate BGT to validators to increase their boost, earning a share of incentive tokens
7. **Cycle continues**: Higher delegation → more boost → larger variable emissions → more incentives → attracts more delegation

---

## BGT Emissions Structure

When a validator proposes a block, BGT is emitted via two components:

**Base Emission (B)**
- Fixed amount per block
- Paid directly to the block-producing validator
- Does not depend on boost

**Variable Emission (Reward Vault Emission)**
- Depends on validator's boost (x = % of total BGT delegated to this validator)
- Distributed to Reward Vaults per the validator's cutting board (weighted allocation)
- Validators receive protocol incentives in exchange for directing emissions

### Emission Formula
```
emission = B + max(m, (a+1)(1 - 1/(1+ax^b)) × R)
```

Parameters:
- x = boost (fraction of total BGT delegated to validator, range 0–1)
- B = base rate (fixed BGT per block)
- R = reward rate (base BGT for reward vaults)
- a = boost multiplier (higher = more important to have boost)
- b = convexity parameter (higher = penalizes low boost more)
- m = minimum boosted reward rate (floor for low-boost validators)

Sample parameters: B=0.4, R=1.1, a=3.5, b=0.4, m=0

**Max block inflation** (at 100% boost): `B + max(m, aR)`

BGT is distributed to Reward Vault stakers over a sliding 3-day window. New distributions push the window forward, creating continuous streaming.

---

## Validator Economics

### Active Set
- Top 69 validators by BERA stake
- Block proposal probability ∝ staked BERA share
- Must maintain stake minimum (250k BERA) to remain in Active Set

### Validator Revenue Streams
1. Gas fees + priority fees
2. Protocol incentive tokens (for directing BGT emissions to reward vaults)
3. Base BGT block reward

### Boost Mechanics
- Boost = validator's BGT delegation / total network BGT delegation
- Higher boost → larger variable emission per block → more incentives captured
- BGT delegation does not risk slashing (only BERA stake can be slashed)

### Cutting Board (BeraChef)
- Each validator sets a Reward Allocation: list of vaults + percentage weights (must sum to 100%)
- 450 block delay before allocation changes take effect
- If validator doesn't update cutting board within 302,400 blocks (~7 days), BeraChef applies baseline allocation directing emissions to active incentive vaults
- Default commission: 5% of incentive tokens | Maximum: 20%
- Commission changes require 16,382 block waiting period

---

## BeraChef

BeraChef is the configuration layer of PoL. It manages:
- Reward Allocations (validator cutting boards)
- Validator commission rates
- Vault whitelisting (only governance-approved vaults receive BGT)

---

## Reward Vaults

Reward Vaults are the only way to earn BGT. They are smart contracts where users stake receipt tokens to earn BGT proportional to their vault share.

### How They Work
1. User takes an action that earns a receipt token (e.g., provides liquidity on BEX, gets LP token)
2. User stakes receipt token in the corresponding Reward Vault
3. User earns BGT proportional to their share of the vault
4. Validator directs emissions to the vault based on their cutting board
5. Protocols deposit incentive tokens to attract validator emissions

### Vault Requirements
- Must be whitelisted through BGT governance to receive validator emissions
- Any vault can be created permissionlessly via BeraHub
- Whitelisting requires a governance proposal

### Emission Modes
**Duration-based (legacy)**: Fixed reward duration (3–7 days), BGT distributed evenly over period
**Target rate mode**: Vault calculates optimal distribution period to maintain target emission rate

### Incentive Mechanics
- Protocols can offer up to 2 different incentive tokens per vault
- Incentive rate = tokens per BGT received (exchange rate set by protocol Token Manager)
- Rate can increase (with new deposits) but cannot decrease until supply exhausted
- Tokens cannot be withdrawn once deposited
- 33% of all incentive tokens are redirected to BERA stakers (Incentive Collector → auctions for WBERA → distributes to sWBERA stakers)

---

## Incentive Marketplace

The Incentive Marketplace is how protocols compete for validator BGT emissions.

**Participants:**
- **Boosters**: BGT holders who delegate to validators, earning a share of incentive tokens captured
- **Validators**: Direct BGT emissions to vaults, capture incentive tokens (minus their commission), distribute remainder to boosters
- **Protocols**: Offer incentive tokens to attract validator emissions to their vaults

**Distribution Flow:**
1. BGT holder boosts validator (increases validator's emission per block)
2. Validator proposes block, receives BGT emissions
3. Validator directs emissions to vaults (per cutting board), captures incentive tokens
4. Validator takes commission (max 20%), distributes rest to boosters
5. 33% of incentive tokens redirected to BERA stakers via auction

---

## $HONEY Stablecoin

$HONEY is Berachain's native stablecoin, fully collateralized and soft-pegged to USD.

**Minting**: Deposit whitelisted collateral → HoneyFactory mints HONEY
- Current collateral: USDC, BYUSD (pyUSD), USDT0, USDe
- Mint rates configurable by BGT governance per collateral
- Current: 100% mint rate (0% mint fee) for most; 0.05% redeem fee for USDC/USDe; 0.1% mint fee for USDT/BYUSD

**Basket Mode**: Safety mechanism activating when any collateral depegs
- Redemption: Instead of choosing collateral, user receives proportional share of all collateral
- Minting: If all collateral depegged, must provide proportional amounts of all

**BGT Holders** receive fees from HONEY minting/redemption.

---

## BERA Staking (sWBERA)

BERA holders can stake directly into the BERA PoL Yield Vault:
- ERC4626-compliant vault accepting native BERA and WBERA
- Earns 33% of all PoL protocol incentives (via Incentive Collector auction mechanism)
- 7-day unbonding period for withdrawals
- Auto-compounds rewards
- Receives WBERA tokens (sWBERA) representing staked position

---

## Key Contracts & Parameters

**Active Set**: 69 validators max
**Min validator stake**: 250,000 BERA
**Max validator stake**: 10,000,000 BERA
**BGT burn ratio**: 1:1 for BERA (one-way)
**Incentive redirection**: 33% to BERA stakers
**Max validator commission**: 20%
**Default commission**: 5%
**Commission change delay**: 16,382 blocks
**Cutting board update delay**: 450 blocks
**Baseline cutting board trigger**: 302,400 blocks (~7 days) without update
**BGT distribution window**: 3 days (sliding)

---

## Protocol-Level Emissions Routing (Feb 16, 2026)

As of February 16, 2026, Berachain introduced a protocol-level emissions split — the first override of pure validator-market BGT routing since mainnet launch.

### Structure

```
Block Minted → BGT Emissions
    ├── X%  → Dedicated Emission Allocation (protocol-controlled)
    │          • Chain-owned apps (e.g., BEND)
    │          • Revenue-positive 3rd party applications
    └── (100-X)% → Validator Reward Allocation (standard cutting board)
```

Initial split: **5% dedicated / 95% validator-market**. Dedicated percentage subject to governance adjustment.

### Rationale
Certain network-critical applications need consistent, predictable emissions to function — and no group has stronger incentive to drive BERA value than the Foundation's core suite. Validator-driven PoL remains the primary mechanism (95%); the dedicated stream is a targeted refinement for strategic applications.

### Eligibility for Dedicated Streams
Applications must demonstrate a credible path to **$1+ in protocol revenue for every $1 of BGT received**, measured over time. This is a long-term target, not an immediate enforcement threshold.

### First Recipient: BEND
BEND (native money market, Morpho v1 fork) received the first dedicated allocation. Rationale: onboards desirable collaterals, provides stable yield access, generates sustainable protocol revenue.

---

## Updated Reward Vault Criteria (Feb 18, 2026)

Reward Vault whitelisting now requires meeting three criteria for continued eligibility:

**1. Ongoing Demand** — Active BGT allocation and third-party incentives. Vaults inactive for 30+ days subject to removal.

**2. External Incentive Alignment** — Must reflect genuine external demand. Self-directed or circular incentives are a negative signal; competitive third-party incentives are a positive signal.

**3. Demonstrated Network Contribution** — Emissions must produce observable value: sustained onchain activity, contributions to liquidity or core primitives, demand drivers for BERA/HONEY/majors or off-chain yield. Immediate revenue not required; long-term credibility is.

**Standard**: Vaults consuming emissions without producing observable impact may be removed.
