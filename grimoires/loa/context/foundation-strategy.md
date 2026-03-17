# Berachain Foundation Strategy & Ecosystem Developments

*Sources: Berachain Foundation EOY Update (Dec 2025), Berachaindevs announcements (Feb–Mar 2026), Furthermore.app data (Mar 17, 2026). Data through March 17, 2026.*

---

## The "Bera Builds Businesses" Pivot

### Context

The Berachain Foundation published an end-of-year update in late December 2025 / early January 2026 marking a strategic shift. The traditional L1 playbook — public goods, free ecosystem support, token incentives — had not reliably translated into token value. After a sustained bear market from TGE (Feb 2025) through end of year, the Foundation reoriented toward a fundamentals-driven, revenue-first model.

The framing: **"PoL emissions are not subsidies. Bera builds businesses."**

### Win Conditions (Stated)
1. Berachain becomes **emissions-neutral** — protocol revenue offsets emissions
2. Berachain becomes **profitable** — revenue exceeds emissions
3. Berachain **reinvests profits** into asymmetric growth and/or buybacks

These are stepwise goals, not simultaneous targets. The Foundation explicitly noted that Berachain's valuation framework is not primarily revenue-centric — but baseline revenue enables the chain to control its own destiny regardless of market conditions.

### EOY Numbers (Dec 2025)
- 25M+ BERA staked in PoL (ATH at time of writing)
- $30M+ in PoL revenue distributed to BGT/BERA holders — top 5 chain by revenue distributed to tokenholders
- $250M+ TVL supported by PoL
- $100M+ stablecoins on-chain
- ~50% of circulating BERA removed from functional supply via PoL and DeFi
- $32M+ DAT cash allocated to BERA buybacks (highest cash/MC ratio among DATs at the time)
- BERA available on Kraken, Bybit, OKX

---

## Execution Plan: Narrow Focus Model

The Foundation announced a shift from broad ecosystem support to deep, hands-on involvement with **3–5 high-conviction applications**. Mix of internal incubation and revenue-sharing or equity partnerships.

### Target Profile
- $10M+ BERA/HONEY demand driver
- $10M+ annual revenue potential
- S-tier founding team
- Distribution beyond crypto-natives

### Tools Available
- PoL emissions directed to partner vaults
- Berachain team providing GtM, product development, fundraising, distribution support
- DAT (Discretionary Asset Treasury) for acquisitions

### What Doesn't Change
Existing community builders continue to receive support — but steered toward the above profile.

---

## New Emissions Routing (Feb 16, 2026)

### The Change

A protocol-level emissions split was introduced, announced by Tio (Head of Product) on February 16, 2026.

**Before**: 100% of BGT emissions flow through validator cutting boards.

**After**: A portion is routed at the protocol level **before** hitting validator cutting boards.

### Structure
```
Block Minted → BGT Emissions
    ├── 5%  → Dedicated Emission Allocation (protocol-controlled)
    │         └── Chain-owned apps / revenue-positive 3rd parties
    └── 95% → Validator Reward Allocation (standard cutting board market)
```

The 5% dedicated stream was the initial allocation. This is explicitly a **targeted refinement**, not a replacement of validator-driven PoL. Validator-driven allocation remains the default for 95% of emissions.

### First Dedicated Allocation: BEND

The inaugural recipient of the dedicated stream was BEND, Berachain's native money market. The initial split within the dedicated 5%:
- 0x6Dc3...6ff0: ~53%
- 0xDc52...d4eE: ~47%

BEND was selected because it directly onboards desired collaterals to Berachain, provides access to stable yield for users, and generates a sustainable revenue stream for the protocol.

### Eligibility for Dedicated Streams

Third-party applications seeking dedicated streams must demonstrate a credible path to **$1+ in revenue for every $1 of BGT received**, measured over time. This is a target, not an immediately enforced requirement. Specifics to be outlined as PoL pilot programs are rolled out.

Additional context from the Foundation: The goal is to transform PoL from a cost center (currently emitting ~$0.7 in incentives for $1 of BGT) into a **revenue generator at the chain level** over time.

### Why This Matters for PoL Mechanics
This is the first protocol-level override of pure validator-market emission routing. It represents the Foundation using BeraChef's governance authority to reserve emission capacity for strategically important applications — complementary to, not competing with, BRIP-0006 (Baseline Cutting Board).

---

## Updated Reward Vault Criteria (Feb 18, 2026)

Two days after the emissions routing change, the Foundation published updated criteria for Reward Vault continued whitelisting. Vaults failing to meet criteria are subject to removal from emissions eligibility.

### Three Criteria

**1. Ongoing Demand**
- Must show recent, organic demand for emissions
- Signals: active BGT allocation, recent third-party incentives
- Inactivity threshold: 30 days without meaningful activity → subject to removal

**2. External Incentive Alignment**
- PoL is designed to reflect external demand
- Vaults relying primarily on self-directed or circular incentives subject to removal
- Competitive third-party incentives are a strong positive signal

**3. Demonstrated Network Contribution**
- Emissions must translate to observable network value
- Evaluation criteria:
  - Is the vault meaningfully used in an active product or workflow?
  - Does it convert emissions into sustained onchain activity (not short-lived spikes)?
  - Does it contribute to economic activity, liquidity, or core primitives?
  - Does it drive demand for BERA, HONEY, majors, off-chain crypto-decorrelated yield, or new distribution outside current Berachain users?
- Immediate revenue not required, but must have credible connection between emissions, long-term network value, and vault sustainability

**The standard**: Vaults that consume emissions without producing observable impact may be removed.

### What Came Next (Feb–Mar 2026)
- Affected Reward Vaults removed from emissions eligibility (blacklist published)
- Inflation reduction implemented
- Protocol-level updates to improve emissions routing communicated
- Longer-term: PoL pilot programs to target $1 emissions → $1+ protocol revenue

---

## Additional Protocol Developments (Feb–Mar 2026)

### Zap Staking

BERA staking via hub.berachain.com/stake now supports cross-chain zaps. Users can stake BERA directly from Ethereum, Base, Polygon, and other chains — no manual bridging required. "No extra steps. Just stake → earn."

### X402: HTTP-Native Payments

X402 is a payments standard enabling HTTP-native onchain payments. Announced live on Berachain February 24, 2026.

- HONEY is the settlement asset
- Enables APIs, agents, and autonomous systems to request and receive onchain payments programmatically
- No complex checkout flows or manual coordination
- Particularly relevant for AI agents and autonomous workflows: enables real-time monetization of agent services using HONEY
- Berachain positions itself as advantageous for this use case due to low swap fees (reduces per-transaction overhead for high-frequency agent payments)

### New Ecosystem Teams (EOY Update)

The Foundation highlighted several incoming teams aligned with the "Bera Builds Businesses" thesis:

**Real-world yield & financial primitives:**
- **Liquid Royalty (SAIL.r)** — tokenized e-commerce royalties; $20M in additional assets onboarding near-term; $1B pipeline
- **SukukFi** — Shariah-compliant tokenized telecom bonds; $10M+ in contracts
- **PortFi** — Stablecoin-native infrastructure for global trade (buyer-led financing)
- **Credi.fi** — On-chain borrowing against real credit scores
- **BrownFi** — Cross-chain elastic AMM
- **Bizzed.ai / Bkinsey** — On-chain PE shop; completed 2 revenue-generating acquisitions

**Consumer, media & brands:**
- **KDA3** — Sports & entertainment fan engagement/ticketing (Napoli, Canada Basketball)
- **Starglow** — K-pop creator monetization; working with major idol groups in Korea
- **Freequency** — Consumer product studio; partnered with major web2 brands and IPs
- **Scrambled** — Gen-Z group buying and social wagering
- **Gethoney.io** — P2P payments and lending

---

## Furthermore.app — Live Ecosystem Data (Mar 17, 2026)

*Furthermore.app is a Berachain analytics dashboard tracking validators, BGT derivatives, reward vaults, and incentive markets. Data below is a snapshot as of March 17, 2026 — not real-time.*

### Validator Network Overview

| Metric | 3m Value | 1Y Value |
|--------|----------|----------|
| Average Boost APR | 42.52% | 43.50% |
| Total Boost Amounts | 376.78K BGT | 392.10K BGT |
| Active Boost Users | 16,740 | 16,740 |

**Top Validators by 24h Emissions:**

| Validator | Boost % | Boosts (BGT) | Emissions (24h) | Commission |
|-----------|---------|--------------|-----------------|------------|
| Luganodes | 51.12% | 792.51K | 2.58K BGT | 0% |
| StakeLab | 0.05% | 728.31K | 2.53K BGT | 0% |
| Kingnodes | 21.12% | 654.76K | 2.53K BGT | 0% |
| RockawayX | 75.08% | 873.65K | 2.50K BGT | 0% |
| DeSpread | 75.06% | 726.00K | 2.49K BGT | 0% |
| Pier Two | 79.02% | 706.45K | 2.47K BGT | 0% |
| Frequency | 54.28% | 513.63K | 2.26K BGT | 20% |
| wallahi | 0% | 389.03K | 2.23K BGT | 5% |
| BicroStrategy | 0.21% | 396.45K | 2.22K BGT | 5% |

**Other notable validators:**
- The Honey Jar: 633.70 BGT accumulated, 57.11% boost, 20% commission
- Beradrome X apDAO: 67.38 BGT, 32.82% boost, 5% commission
- Smilee Finance: 406.96 BGT, 0% boost, 5% commission
- CoinSummer Labs: 1.45K BGT, 70.35%, 0% commission
- P2P.org: 1.27K BGT, 64.24%, 20% commission

**Commission distribution**: Most major validators run 0% or 5%. Several unnamed validators and smaller named validators run 10–20%.

**Boost concentration**: Top validators by boost amount hold 700K–874K BGT delegated. The BGT boost market is concentrated at the top.

### BGT Derivatives (Mar 17, 2026)

| Token | Price | Premium to BERA |
|-------|-------|-----------------|
| BGT | $0.653 | Redeems 1:1 to BERA |
| iBGT (Infrared) | $0.670 | +2.62% |
| LBGT | $0.636 | -2.52% |
| stBGT | $0.613 | -6.08% |

**Notable**: stBGT spiked to 40–60%+ premium briefly in late February/early March 2026 before collapsing. Timing coincides with the emissions routing change announcement (Feb 16) and vault criteria update (Feb 18) — likely related to speculative repositioning around protocol-level emission access.

Over the 1-year view, BGT derivatives historically tracked well, with premiums compressing toward parity as the bear market extended.

### Reward Vaults (36 with BGT Capture, Mar 17, 2026)

**Top vaults by USD/BGT incentive rate:**

| Rank | Vault | Protocol | USD/BGT | BGT Capture | TVL |
|------|-------|----------|---------|-------------|-----|
| 1 | Spank Ass | Bullas | $0.72 | 0.02% | — |
| 2 | Stake LBGT/pBERA | Kodiak | $0.60 | 0.01% | $29.93K |
| 3 | Stake SAIL.r-USDe | Kodiak | $0.58 | 6.31% | $1.37M |
| 4 | apDAO Treasury Vault | apDAO | $0.58 | 0.03% | — |
| 5 | BeraPaw Rewards | BeraPaw | $0.57 | 8.50% | $10.94K |
| 6 | Stake WBERA/BERO | Kodiak | $0.57 | 0% | $21.73K |
| 7 | Stake WIZZ/WBERA | HUB | $0.57 | 0% | $20.83K |
| 8 | Yeet in the BGT Auction | Yeet | $0.57 | 11.34% | $25.61K |
| 9 | Stake osBGT/sWBERA | Kodiak | $0.56 | 9.64% | $3.66M |
| 10 | Stake eWBERA/osBGT | Kodiak | $0.56 | 9.38% | $3.15M |

**Vaults by BGT capture % (top):**
- Yeet in the BGT Auction: 11.34%
- Stake osBGT/sWBERA: 9.64%
- Stake eWBERA/osBGT: 9.38%
- Lend Honey on Re7 vault (BEND): 8.97%
- BeraPaw Rewards: 8.50%
- Stake sUSDe/Honey (Kodiak): 4.67%
- Stake All-in-One Honey (Honeypot Finance): 4.90%
- sweETH (Sumer): 4.84%
- Stake for BGT rewards (Kodiak): 5.31%

**Notable TVL vaults:**
- Lend Honey on Re7 vault (BEND): $16.27M
- Stake sUSDe/Honey (Kodiak): $6.07M
- Stake hiBERO/HONEY (Beradrome): $5.83M
- Stake hOHM/HONEY (Origami Finance): $5.52M
- Stake SAIL.r-USDe (Kodiak): $1.37M

**Other vaults visible in data (no BGT capture but active):**
Stake WBTC/HONEY ($1.52M), Stake USDe/Honey ($3.92M), Stake DOLO/WBERA ($343.82K), Stake WETH/HONEY ($1.26M), Stake USDC.e/HONEY ($1.30M), Stake stBGT/BERA ($64.33K), Stake brBTC/uniBTC ($23.52M)

### SAIL.r Senior Vault — Incentive Market Data

*Source: Furthermore.app vault overview panel, as of March 17, 2026.*

| Metric | 7d | 30d | 3m | 1Y |
|--------|----|----|-----|-----|
| Incentives Distributed | $59,562 | $364,121 | $2,071,505 | $34,125,926 |
| Avg USD/BGT | $0.35 | $0.35 | $0.34 | $0.34 |
| Total Active Incentives | $76K | $76K | $76K | $76K |
| Incentives Paid (7d) | $64,056 | — | — | — |

**Orderbook depth (current):**
- $0.58/BGT (1.13x): 14.84% capture
- $0.57/BGT (1.15x): 11.34% capture
- $0.56/BGT (1.16x): 19.02% capture
- $0.54/BGT (1.21x): 15.06% capture

**Narrative context**: SAIL.r launched as a major incentive payer in the Berachain vault market. The 1Y data shows significant early incentive volumes (peak ~600K/week in mid-2025) declining to current ~$60K/week. Avg USD/BGT compressed from highs of $6+ at launch to a stable ~$0.34-0.35 today — converging toward the market equilibrium rate.

---

## Hypha Note on Data Currency

All Furthermore data in this file reflects a single snapshot taken March 17, 2026. Validator boosts, vault rankings, BGT derivative premiums, and incentive rates change continuously. This data provides **baseline context and reference points** — not live state. Query furthermore.app directly for current figures.

The SAIL.r vault data is included here because it directly relates to apDAO's treasury strategy (apGP26) and VUX design benchmarks. For those purposes, the trends matter more than the specific numbers.
