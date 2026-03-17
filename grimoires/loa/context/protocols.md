# Ecosystem Protocols

## Infrared Finance

**What it is**: Infrared is the leading liquid staking infrastructure layer for Berachain. It builds around PoL to maximize value capture, providing liquid solutions for BGT and BERA, node infrastructure, and vaults.

**Core problem solved**: BGT is soulbound and non-transferable. iBGT makes it composable. BERA staking requires technical validator setup. iBERA removes that barrier.

### Tokens

**iBGT** — Liquid BGT wrapper
- Backed 1:1 by BGT earned by liquidity deposited in Infrared vaults
- Not redeemable for BGT (one-way)
- Not liquid unless deposited (must be staked in Infrared vaults to earn rewards)
- Enables BGT to be used in DeFi: lending, trading, LP

**iBERA** — Liquid BERA staking token (LST)
- Backed 1:1 by BERA staked with Infrared's validator set
- Can be used in DeFi: lending, borrowing, trading
- APR based on validator sweep events (not fixed reward rate)
- Rewards distributed during sweep events; APR annualized from most recent sweep

**IR** — Infrared's native governance token
- Delegated Incentive System: stake IR → receive sIR → earn fee rewards + governance power
- User vaults: fee generation, siBGT fees → buyback and distribute IR (auto-compounds in sIR)
- Protocol vaults: stake IR → direct PoL Reward Vault emissions for chosen strategies
- Red Fund: portion of protocol fees buy back and lock IR for 12 months, then used as PoL incentives
- Distribution: Ecosystem 20% unlock at TGE (24mo linear); Contributors/Investors/Foundation 1yr cliff, 10% unlock, 24mo linear

### iVaults
- Pool deposits and deploy DeFi strategies (e.g., BYUSD-HONEY iVault)
- Earn combination of iBGT yield and strategy-specific yields
- Diversifying over time

### Fee Structure
| Fee Type | Rate | Description |
|----------|------|-------------|
| HarvestOperatorFeeRate | 10% | On operator rewards |
| HarvestVaultFeeRate | 10% | On iBGT vault rewards |
| HarvestBribesFeeRate | 10% | On bribe rewards from staking |
| HarvestBoostFeeRate | 1–10% | Dynamic based on iBGT premium over BERA |
| Swap to iBGT/iBERA | 0% | |
| Swap to single asset | 0.05% | |
| Swap to LP tokens | 0.2% | |

**BGT yield not subject to any fee.**

### APR Calculation
- PoL vaults + iBGT: reward rate from smart contract, updated every 20 minutes
- iBERA: sweep-event based, annualized from most recent distribution

### Key Contract Addresses
- IR: `0xa1b644aec990ad6023811ced36e6a2d6d128c7c9`
- BERA adaptor: `0xfd0fA49F8aA1d61dA390E10EAD23C650B0F9C2B5`

---

## Kodiak Finance

**What it is**: Kodiak is Berachain's native concentrated liquidity DEX, built around Islands (managed LP positions) and deep PoL integration.

**Core role in ecosystem**: Primary liquidity venue for most Berachain native token pairs. KDK/xKDK token system creates protocol-owned liquidity alignment.

### Key Features
- Concentrated liquidity AMM
- Islands: managed LP positions that auto-rebalance
- KDK: governance token
- xKDK: escrowed KDK with yield-bearing properties
- Deep integration with Beradrome (Trifecta partnerships)
- Major LP pairs: HONEY-WBERA, HONEY-USDC, YEET-WBERA, BERO-oBERO, and more

### Trifecta
Partnership structure between Kodiak, Beradrome, and selected protocols. Trifecta LP positions earn multiple reward streams simultaneously: oBERO (from Beradrome), KDK/xKDK (from Kodiak), swap fees, and any protocol-specific rewards.

---

## Goldilocks DAO

**What it is**: Goldilocks is a DAO building custom DeFi infrastructure for Berachain. Core products: Goldiswap (novel AMM), Goldilend (NFT lending), Goldivaults (yield tokenization).

**apDAO relationship**: apDAO holds perpetual 5% governance power over Goldilocks DAO via partnership agreement.

### LOCKS Token

LOCKS is the ERC20 governance token of Goldilocks DAO. Only staked LOCKS holders have voting rights.

**Key properties**:
- Never trades below floor price (guaranteed by Goldiswap mechanics)
- Staking earns PORRIDGE (not new LOCKS — no dilution of floor)
- Stakers can borrow up to floor price in HONEY (interest-free, liquidation-free)
- Initial supply: 190,000,000 (34M team, 156M seed investors)
- Team tokens: permanently staked and locked forever
- Seed investor tokens: 3-month lock, then 12-month linear vest

**Delegation**: Users can delegate voting weight without locking tokens.

### PORRIDGE Token

PORRIDGE is the staking reward token. It functions as a call option on LOCKS at floor price ("stirring").

- 1 PORRIDGE = right to buy 1 LOCKS at floor price from Goldiswap
- Staking rate: 0.4 PORRIDGE per staked LOCKS annually (governance-adjustable)
- Initial DAO treasury: 250,000,000 PORRIDGE
- No sell tax on PORRIDGE trades
- Liquidity provided on Kodiak

### Goldiswap (AMM Mechanics)

Goldiswap manages LOCKS supply, price, and behavior via two reserve pools:

**FSL (Floor Support Liquidity)**: Backs the floor price. Floor = FSL / total supply.
**PSL (Price Support Liquidity)**: Market-driven. Determines premium above floor.

**Pricing Formula**:
```
Market Price = Floor Price + (PSL / TotalSupply) × ((FSL + PSL) / FSL)^6
```

This ensures:
- LOCKS never trades below floor
- Volatility increases exponentially as PSL/FSL ratio rises
- When PSL/FSL reaches 0.5, all HONEY from buys redirects to FSL (floor protection)

**5% sell tax**: All LOCKS sales taxed 5%, 100% sent to PSL.
**0.3% buy fee**: Sent to DAO treasury.

**Floor Raising Mechanism**:
- When PSL/FSL ratio hits target T, portion of PSL transfers to FSL → permanent floor increase
- After floor raise, new target = 1.02 × T
- If PSL/FSL stuck below T, T decreases daily (easier to reach) — floor never stops rising

### Locked LOCKS (Borrowing)

Staked LOCKS can be used as collateral:
- Borrow up to full floor price in HONEY
- Zero liquidation risk (floor can never decrease)
- Zero ongoing interest
- One-time origination fee: 3% (to DAO treasury)
- Borrowed HONEY counted in FSL → doesn't dilute floor

### Goldivaults

Vaults that tokenize future yield of yield-bearing positions. Users can trade and speculate on the value of that yield. Provides yield tokenization infrastructure across Berachain DeFi.

### Goldilend

NFT lending platform for bluechip Berachain NFTs. Collateralized borrowing against high-value NFT positions.

---

## Beradrome

**What it is**: Berachain's native restaking and liquidity marketplace. Solidly-inspired ve(3,3) system rebuilt with novel token design, a bonding curve, and liquidation-free borrowing.

**Core differentiation from standard Solidly forks**: BERO has a price floor, oBERO is a call option (not a direct emission), hiBERO has 1-week unlock (not 4-year lock), and the bonding curve provides built-in liquidity.

### Token System

**BERO** — Core token
- Managed by bonding curve
- Minimum price floor: 1 HONEY per BERO (guaranteed)
- Backed by HONEY in Floor Reserves
- Market price discovery via Market Reserves (virtual bonding curve)
- 5% sell tax on BERO → PSL (price support)
- 0.3% buy fee → DAO treasury

**hiBERO** — Staked BERO (governance + yield)
- Equivalent to veSOLID but with major upgrades
- 1-week unlock (vs. 4-year lock in standard Solidly)
- Earns: 20% of weekly oBERO emissions, swap fees, BGT (when whitelisted), voting fees/bribes
- Can borrow up to 1 HONEY per hiBERO: interest-free, liquidation-free, 2.5% one-time fee
- To unstake: repay loans + reset votes + wait for epoch end

**oBERO** — Call option on BERO at floor price
- Issued to gauges as liquidity incentives (based on hiBERO votes)
- Exercise: 1 oBERO → buy 1 BERO at 1 HONEY (floor price)
- Alternative: burn oBERO into permanent voting power (cannot borrow against burned oBERO)
- Functions like option premium: valuable if BERO trades above floor

### Bonding Curve Mechanics

**Floor Reserves**: Back BERO's minimum value
- Users can always redeem 1 BERO for 1 HONEY
- Constant-option bonding curve for unlimited scale
- LPs earn oBERO (allowing purchase at floor price)

**Market Reserves**: Discover BERO's market price
- Virtual bonding curve (x × y = k, starts with virtual HONEY)
- Price at or above floor based on demand
- Buy and sell anytime with deep virtual liquidity

**Example**: Starting with 100 BERO, 100 virtual HONEY (K=10,000). User adds 25 real HONEY to buy 20 BERO → new state: 125 HONEY × 80 BERO = 10,000.

### Emissions

- Weekly oBERO emissions start at 80,000 oBERO (4% of initial 2M supply)
- Decay: 1% per week
- Distribution: 80% to gauges (based on hiBERO votes), 20% to hiBERO stakers, 5% to team multisig
- No fixed supply cap — emissions continue indefinitely

### Governance (Voting)

- hiBERO holders vote weekly to direct oBERO emissions to gauges
- Voting rewards (bribes) accrue continuously after vote; claimable anytime
- One action per epoch (vote, switch, or reset)
- Votes persist to next epoch if unchanged
- Epoch resets: Thursday 00:00 UTC
- vAPR = primary metric for profit-maximizing voters

### Real Deal

Protocol bribing program:
- Protocols commit $ amount of bribes over first 12 months
- Receive equal dollar value of permanently locked voting power (burned oBERO → hiBERO)
- $2.5M+ committed at launch
- 50% of initial supply sold via Real Deal

### Vortex

Bonus BERA distribution program:
- 1,500 BERA per 4-week period
- Requires burning ≥30 oBERO in the period
- Share of pool = user burns / total burns × 1,500 BERA
- 3-month program duration, funded by BERA RFA tokens

### Liquidity Trifecta

Partnership between Beradrome, Yeet, and Kodiak for multi-stream LP rewards.
Example (BERA-YEET LP in Beradrome vault):
- LPs earn: oBERO, KDK, xKDK, swap fees
- Voters earn: BERA (from Beradrome validator), HONEY (from fees + validator flows), YEET bribes
- Creates self-reinforcing flywheel: more bribes → more votes → more rewards → more LPs

### Tokenomics (Initial Supply: 2,000,000 BERO)
- 5% (100k) → community as oBERO (airdrop)
- 15% (300k) → community as hiBERO (permanent voting power)
- 50% (1M) → protocols/DAOs as hiBERO via Real Deal
- 20% (400k) → team as hiBERO (permanently locked)
- 10% (200k) → ecosystem votes supporting BERO/BERA/HONEY liquidity

### Key Contract Addresses (Mainnet)
- BERO: `0x7838CEc5B11298Ff6a9513Fa385621B765C74174`
- oBERO: `0x40A8d9efE6A2C6C9D193Cc0A4476767748E68133`
- hiBERO: `0x7F0976b52F6c1ddcD4d6f639537C97DE22fa2b69`
- Voter: `0xd7ea36ECA1cA3E73bC262A6D05DB01E60AE4AD47`
- Reward Vault: `0x63233e055847eD2526d9275a6cD1d01CAAFC09f0`

---

## BEND (Berachain Native Lending)

**What it is**: Berachain's native lending protocol, forked from Morpho v1. Enables efficient lending and borrowing with native PoL integration. Primarily HONEY as the loan asset.

**Key distinction from other lending protocols**: Permissionless immutable market creation, isolated risk per market, and native BGT yield for lenders via PoL Reward Vaults.

### Architecture

**Markets**: Each market pairs one collateral asset with one loan asset.
- Immutable parameters set at creation
- Isolated risk (no cross-market contamination)
- Lenders access markets through Vaults, not directly
- Borrowers interact with markets directly (supply collateral, borrow loan asset)

**Vaults**: ERC-4626 yield-generating contracts managed by Curators.
- Pool deposits and allocate across approved markets
- Curator sets which markets vault can use + supply caps (timelocked changes)
- Allocator manages day-to-day supply/withdraw queues
- Guardian can revoke pending timelocked changes

**Roles**:
- Owner: Top authority, appoints Curator/Allocator, sets fees
- Curator: Decides what markets are allowed (strategy + risk)
- Allocator: Decides how to allocate within Curator-approved markets
- Guardian: Safety check, can revoke pending changes
- Public Allocator contract: Can be set as Allocator for permissionless reallocation

### Active Markets
| Collateral | Loan | Market ID |
|-----------|------|-----------|
| wsRUSD | HONEY | `0x04d3b8b00...` |
| WBTC | HONEY | `0x950962c1c...` |
| sUSDe | HONEY | `0x1ba7904c7...` |
| wgBERA | HONEY | `0x63c2a7c20...` |
| WETH | HONEY | `0x1f05d324f...` |
| WBERA | HONEY | `0x147b032db...` |
| iBERA | HONEY | `0x594de722a...` |

### LTV and Health Factor

**LTV** = (Borrowed Amount / Collateral Value in Loan Token) × 100%

**LLTV** = Liquidation LTV — fixed per market, set at creation from governance-approved list.
- If LTV ≥ LLTV → position liquidatable
- Example: LLTV 86% → position at risk once LTV hits 86%
- WBERA/HONEY example LLTV: 94.5% (`945000000000000000` in WAD)

**Health Factor** = (Collateral Value × LLTV) / Borrowed Amount
- > 1.0 = healthy
- ≤ 1.0 = eligible for liquidation

### Interest Rate Model (AdaptiveCurveIRM)

The only IRM used in BEND markets. Targets **90% utilization**.

- Below 90%: borrow rate falls to encourage borrowing
- Above 90%: borrow rate rises to encourage repayments and more supply
- Immutable: cannot be changed post-deployment
- Adaptive: rate at target (r₉₀%) shifts over time based on utilization error
- If utilization stays at 100% for 5 days, r₉₀% can roughly double

**Constants**:
- CURVE_STEEPNESS (kd): 4
- ADJUSTMENT_SPEED (kp): 50/seconds per year
- TARGET_UTILIZATION: 90%
- INITIAL_RATE_AT_TARGET: 4%/year
- MIN_RATE_AT_TARGET: 0.1%/year
- MAX_RATE_AT_TARGET: 200%/year

**Borrow APY** = e^(borrowRate × 31,536,000) - 1
**Supply APY** = Borrow APY × utilization × (1 - fee)

### Liquidation

- Not an auction — first liquidator to act wins
- Liquidator repays debt → receives collateral at discount (Liquidation Incentive Factor)
- LIF at 86% LLTV ≈ 1.05 (5% bonus)
- LIF formula: min(maxLIF, 1/((1-β) × (1-LLTV))) where β=0.3, maxLIF=1.15
- Full incentive goes to liquidator (no BEND protocol fee)
- Bad debt: if collateral falls below debt, shortfall is lenders' loss (isolated per market)

### Yield Sources for Lenders

1. **Native APY**: Interest paid by borrowers, collected via vault share price increase
2. **BGT Yield**: Stake vault receipt tokens in whitelisted PoL Reward Vault → earn BGT
   - Must stake AND claim BGT separately
   - BGT yield exempt from all fees

### Fees

**Platform fee**: Charged at market level, retained by Berachain Foundation
**Performance fee**: Charged at vault level, 100% to Curator (subject to change)
**BGT yield**: No fees

### Public Allocator

Smart contract enabling just-in-time liquidity reallocation. When a borrower needs more than a single market has:
1. Borrow request triggers shortfall detection
2. Public Allocator moves idle vault supply from other markets into needed market
3. Borrow completes — user sees deep liquidity, risk stays isolated

Curators set flow caps (maxIn/maxOut per market) to constrain reallocation.

### Flash Loans

- Uncollateralized borrow-and-repay within one transaction
- No fee (beyond gas)
- Must repay in same transaction or full revert
- Use cases: arbitrage, collateral swap, self-liquidation

### Morpho Contract Address
`0x24147243f9c08d835C218Cda1e135f8dFD0517D0`

---

## Apiary Finance

**What it is**: Apiary is a BGT-accumulation and issuance protocol. It allows protocols and DAOs to access BGT-aligned capital through bonds (apBonds) and issues apHive — a token representing a claim on BGT yield.

**apDAO relationship**: apDAO invested up to $50k via apGP28 (Feb 2026) — $25k pre-bond + $25k matching. apDAO receives 25% of initial $APIARY supply at $100k FDV.

### Core Mechanics
- apBonds: protocols borrow against their BGT exposure, generating yield for apDAO
- apHive: issued to small DAOs, BGT-rich protocols, and SEAT holders as bonus (not the core product)
- iBGT backstop: Apiary's yield is backstopped by iBGT
- Supply constraints: deliberately limited to maintain value

### apDAO Strategic Thesis
- BGT accumulation flywheel: treasury-aligned protocol that feeds back into BGT
- Compounding: yield from apBonds compounds into more BGT exposure
- Strong supply constraints = maintained value for apHive

---

## Liquid Royalty Protocol (SAIL.r)

**What it is**: Revenue-based financing protocol on Berachain. Projects sell future revenue as Royalty Tokens in exchange for immediate capital. SAIL.r is the primary Royalty Token.

**Core concept**: "Merchant cash advance" model for DeFi. Protocol sells % of future revenue at a discount. Investors buy Royalty Tokens and receive ongoing revenue share.

### Key Mechanics
- Revenue sharing: SAIL.r holders receive proportional share of protocol revenue
- No maturity date: tokens accrue revenue until fully redeemed
- Discount rate: investors pay less than face value for future revenue rights
- SAIL.r-USDe LP on Kodiak: major yield source for holders

### apDAO Context
- SAIL.r-USDe BGT APR benchmark: ~51.80% (used in VUX simulations)
- SAIL.r royalty yield: ~5.13%
- Price history: Feb–Mar 2026 (~$13–$14 range, very thin volume)

---

## Vase Finance

**Status**: Pre-launch as of March 17, 2026. Rumored docs release ~2 weeks out.

**Known**: Vase Finance is an upcoming protocol in the Berachain ecosystem. Specific mechanics, token structure, and PoL integration unknown pending official documentation.

**Note**: Hypha will be updated when docs are available. Do not speculate on Vase mechanics.

---

## Protocol Relationship Map

| Protocol | Primary Role | PoL Integration | apDAO Relationship |
|----------|-------------|-----------------|-------------------|
| Infrared | Liquid staking (iBGT, iBERA) | Core — manages validator + reward vaults | Major holding, iBGT used in strategies |
| Kodiak | DEX + concentrated liquidity | Reward vaults for LP positions | LP venues for treasury strategies |
| Goldilocks | LOCKS AMM + lending | Reward vaults for LOCKS | 5% perpetual governance power |
| Beradrome | Liquidity marketplace + ve(3,3) | oBERO emissions via gauges | apGP22: $95k BERO/BERA LP deployment |
| BEND | Native lending | BGT yield via PoL reward vaults | wBERA/HONEY and related markets |
| Apiary | BGT bonds + apHive | BGT accumulation flywheel | apGP28: $50k investment |
| SAIL.r | Revenue-based financing | SAIL.r-USDe LP BGT yields | Benchmark in treasury modeling |
| Vase Finance | TBD | TBD | TBD (pre-launch) |
