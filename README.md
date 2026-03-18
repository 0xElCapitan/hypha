# hypha

**A neutral historian and builder's companion for the Berachain ecosystem.**

> *Named after fungal hyphae — the microscopic threads that form mycelium and route nutrients through the network. Hypha maps how Proof of Liquidity routes incentives between protocols, validators, and vaults as one connected system. It does not pick winners. It maps terrain.*

---

## Install

```bash
/constructs install hypha
```

Or manually: copy `grimoires/loa/context/` into your project's grimoires directory.

---

## Commands

| Command | What it does |
|---------|-------------|
| `/map [target]` | Trace how a protocol, vault, or token connects to the PoL network |
| `/dig [topic]` | Deep retrieval on a specific mechanic, proposal, or concept |
| `/flows [entry-point]` | Follow BGT or incentive flows from a validator, vault, or protocol |
| `/build [idea]` | Builder mode — what exists, what's been tried, how your idea plugs in |
| `/bounds` | Surface knowledge gaps, data cutoffs, and uncertainty flags |

---

## What's Covered

**Berachain Core**
PoL lifecycle, BGT/BERA two-token model, validator economics, BeraChef cutting boards, reward vault mechanics, incentive marketplace, $HONEY stablecoin, BGT emission formula, February 2026 protocol-level emissions routing split, updated vault whitelisting criteria.

**Ecosystem Protocols**
Infrared Finance (iBGT, iBERA, iVaults), Kodiak (concentrated liquidity, Islands, Trifecta), Goldilocks (LOCKS/PORRIDGE, Goldiswap floor mechanics, no-liquidation borrowing), Beradrome (BERO/oBERO, bonding curve, Vortex), BEND (Morpho v1 fork, AdaptiveCurveIRM), Apiary Finance (BGT bonds, apHive), SAIL.r (revenue-based financing, royalty tokens).

**apDAO Governance**
Complete record of all 35 proposals (apGP1–apGP28 + pre-numbered era). SEAT mechanics, treasury structure, participation crisis arc, delegation unlock, governance pattern analysis. apGP12 frontend bug corrected.

**Protocol Improvement History (BRIPs)**
BRIP-0000 through BRIP-0009 — EL fork decision, gas fee modifications, Stable Block Time, cutting board automation, preconfirmations architecture, bera-geth deprecation (April 9, 2026 sunset).

**Foundation Strategy**
"Bera Builds Businesses" pivot, EOY 2025 numbers, new emissions routing (5%/95% split), updated vault criteria, ecosystem partner teams, X402 payments, Zap Staking.

**Historical Data**
BERA, iBGT, LOCKS, SAIL.r price history from launch through March 2026. Furthermore.app validator network, BGT derivatives, reward vault rankings, and SAIL.r incentive market snapshot (March 17, 2026).

---

## Knowledge Base

```
grimoires/loa/context/
├── identity.md              # Persona, voice, mycelium frame, reasoning approach
├── berachain-core.md        # PoL mechanics, BGT/BERA, validators, BeraChef, HONEY
├── protocols.md             # All major Berachain ecosystem protocols
├── apdao.md                 # Complete apDAO governance history
├── price-history.md         # Token price data and market context
├── boundaries.md            # Epistemic standards, known gaps, what Hypha defers on
├── brips.md                 # BRIP protocol improvement history
└── foundation-strategy.md  # Foundation strategy, ecosystem data, Furthermore snapshot
```

---

## Known Gaps (v0.2.0)

- Vase Finance: pre-launch, docs pending
- BRIP-0008 final values: discussion phase, hysteresis constants TBD
- THJ internal perspective: member/contributor view only
- Real-time data: static as of March 17, 2026

---

## Built With

Framework: [Loa](https://github.com/0xHoneyJar/loa) by @janitooor / The Honey Jar
Knowledge: El Capitan (apDAO)
Constructs platform: [constructs.network](https://constructs.network)
