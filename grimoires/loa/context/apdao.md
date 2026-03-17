# ApiologyDAO (apDAO)

## What is apDAO?

ApiologyDAO exists at the financial core of the Berachain ecosystem, functioning as a "hive" that bootstraps cultural and financial liquidity across DeFi protocols on Berachain. It supports and grows key protocols by strategically directing investments and resources, fostering deep integrations and liquidity.

Like bees, apDAO pollinates across the application layer — all for the strategic benefit of the hive.

**Origin**: Incubated by The Honey Jar (THJ) for the benefit of the entire Berachain ecosystem. Genesis was driven by Honeycomb NFT holders seeking to combine their holdings to direct greater influence across Berachain.

**Fat Bera Thesis**: The founding thesis — protocols with endogenous apps that capture value and share with exogenous protocols, apps, and the community will become prosperous zones of power in DeFi. apDAO leverages long-term alignment to compound resources and foster ecosystem growth.

---

## Structure

apDAO operates in 3 tiers:

### Beekeepers
The operational heart of apDAO. Initially fulfilled by The Honey Jar (THJ Corp.), which controls:
- Smart contract maintenance
- Governance administration
- Community outreach + partnerships
- Website domain + social accounts (X, Discord)
- Product + treasury management
- Multisig operations + marketing

Compensation: 10% of liquid backing treasury allocations. The DAO can vote to replace THJ at any time.

### Core Contributors
Elite individuals appointed by community vote. Bridge between community and Beekeepers.
- Discord moderation and community guidelines
- Collect + relay community feedback
- Signers of DAO treasury multisig
- May be elevated to Beekeepers based on contributions

### General Members
All DAO members. No specific requirements beyond community guidelines. May become Core Contributors through recognized valuable contributions.

---

## SEAT NFT Mechanics

apDAO membership is represented by soulbound ERC721A NFTs (SEAT tokens).

### Acquisition
**Genesis**: 420-hour period requiring deposit of 7 THJ NFTs (one from each collection) = 1 seat. Multiple sets = multiple seats.

Required collections:
1. Honey Comb (Ethereum)
2. Honey Jar Gen 1 (Ethereum)
3. Honey Jar Gen 2 (Arbitrum)
4. Honey Jar Gen 3 (Zora)
5. Honey Jar Gen 4 (Optimism)
6. Honey Jar Gen 5 (Base)
7. Honey Jar Gen 6 (Ethereum)

**Post-genesis**: Auction House only.

**Supply**: 5,898 total seats. 3,232 pre-allocated to MijaniDAO, THJ, and partners. 2,666 available for genesis.

### Transfer Restrictions
Seats are soulbound — non-transferable EXCEPT:
- To/from Liquid Backing Treasury (for loans/defaults)
- To/from Auction House (for sale)

### Governance Token Integration
Each SEAT is linked to Station X governance tokens:
- Minted when claiming or receiving a seat
- Burned when transferring to LBT or Auction House

### Exit Mechanisms

**Auction Queue**:
1. Member adds seat to Auction House queue
2. While queued, member loses access and voting rights
3. Pyth Entropy VRF randomly selects 1 seat per day from queue
4. Auction runs at reserve price = RFV + configurable buffer (default 10%)
5. If sold: original owner receives proceeds minus fees; LBT receives fee
6. If no bids: LBT redeems backing (minus fall fee), NFT is burned → increases backing for all remaining holders

**LBT Loan Default**:
1. Member borrows from LBT against their seat
2. Failure to repay by deadline triggers liquidation
3. Treasury burns NFT, member loses membership
4. Default increases backing for all remaining holders (up-only mechanic)

### Up-Only Mechanics
Every exit — whether auction, default, or burn — increases the withdrawable backing per remaining seat. The system is designed so no member action can decrease the value backing other members' seats.

---

## Treasuries

apDAO operates 2 active treasuries:

### Liquid Backing Treasury (LBT)
- Primary treasury backing the Real Floor Value (RFV) of each SEAT
- Continuously seeded by DAO revenues: validator operations, auction house fees, partner revenue shares, yield strategies
- Members can borrow against it at RFV (interest rate per apGP1: 2%)
- Loan terms: 1 day minimum to 1 year maximum
- Loan defaults: increase backing for remaining holders
- Auction reserve pricing: RFV + configurable buffer (default 10%)
- Up-only design: every treasury interaction trends toward increasing per-seat backing

### Growth Treasury
- Catches everything else
- Holds: Honeycomb + HJ NFTs from genesis (locked forever per apGP1), partner governance tokens (never-sell pledge), and discretionary investments
- Partner token strategy: harvest yield and governance benefits, never sell
- Investment arm: directed toward compounding ecosystem plays over immediate liquidity
- Legacy documentation refers to this as "Honey Treasury" + "Diamond Paw Treasury" — operationally they're one

---

## Governance Framework

### 4 Tracks

| Track | Purpose | Submission | Voting | Quorum | Threshold |
|-------|---------|-----------|--------|--------|-----------|
| PLZ | Community requests, non-binding guidance | 1 day | 4 days | ~11.25% (post-apGP6) | Simple majority |
| Tardfi | Legal/structural changes, partnerships, framework changes | 5 days | 10 days | 30% | >60% supermajority |
| Dev | Smart contract configuration, auction/LBT parameters | 1 day | 7 days | ~18.75% | Simple majority |
| Honey | Financial management, treasury investments | 2 days | 5 days | ~24.75% | >60% supermajority |

*Quorums reduced 25% by apGP6. Effective quorums further adjusted by delegation dynamics.*

### Delegation System (apGP13)
- Introduced September 2025 — near-unanimous passage (1766 For / 3 Against)
- Fully revocable at any time
- Maximum 5% of voting power per single delegate (concentration cap)
- Transparent on-chain voting record
- Effect: DAO now functions at 12-20% participation via delegates, consistent quorum

### Proposal Requirements
- Title, Proposer, Track
- Summary
- Justification (strategic relevance)
- Requested Actions (precise + calculable for financial proposals)
- Supporting Materials

**Frequency**: 1 active proposal per track per member per 14 days
**Rejected proposals**: 30-day cooldown before resubmission (with justification for reconsideration)
**Review period**: Beekeepers review before vote opens (cannot cancel without cause; can provide refinement feedback)

### Voting Outcomes
- **Approved**: Meets quorum + approval threshold → binding, queued for execution
- **Rejected**: Fails quorum or approval threshold → 30-day resubmission cooldown
- **Failed**: Met quorum but missed approval threshold (contested on merit)
- **Pending**: Review period ended, voting not yet started or never started

### Important Governance Notes
- **Onchain immutability**: Once a proposal is signed to the blockchain, it cannot be edited. If improvements are needed, a new proposal must be submitted. This is why multiple sequential attempts exist (apGP20→21→22, apGP23→24, apGP11→12).
- **apGP12 UI bug**: Platform incorrectly shows apGP12 as "Failed." It passed. 687 abstentions (45.6% of votes cast) were not counted by the frontend. Actual quorum: 26.87% / 24.75% required. Proposal executed.
- **apGP9 withdrawal**: Author withdrew apGP9 (OHM strategy) after apGP8 (BTC) failed — reasoned OHM wasn't worth pushing if BTC couldn't pass. Rejection was by author request, not quorum failure.

---

## Governance History

### The Participation Crisis Arc (May–October 2025)

The early governance period was defined by participation failure — not ideological opposition.

**Root causes**:
- TGE bear market: BERA launched at ~$8.58 (Feb 2025), declined steadily to ~$0.54 by March 2026
- Ecosystem underperformance compounded member disengagement
- Governance gridlock feedback loop: failures → burnout → more failures
- Original quorum thresholds too high for bear market participation levels

**Signature examples of participation failure**:
- apGP19 (Bera Rebase NFTs): 1147 For / 32 Against — 97% support, missed quorum by 1.82%
- Treasury Wallet Separation: 2112 For / 4 Against — 98% support, missed 40% quorum by 2%
- BBC: Attempted 3+ times in "Pending" state (0 votes) before finally reaching a vote in apGP8

### Turning Points

**apGP6 (Quorum Adjustment, June 2025)**: Passed with 41.89% — the last time the DAO cleared old high thresholds. Reduced all quorums by 25%. Bought critical breathing room.

**apGP13 (Delegation, September 2025)**: The true structural unlock. Near-unanimous (1766/3). Transformed participation dynamics — members who checked out could delegate to active participants, maintaining governance function without requiring personal engagement.

### Post-Delegation Era (October 2025 onward)

No proposal has failed to meet quorum since apGP13. Pass rate near-perfect. Key dynamics:
- Quorum consistently met at 12-20% via delegation
- Members may return and reclaim agency as market sentiment improves
- The DAO is structurally healthy but intentionally lean — not broken, calibrated

---

## Complete Proposal Record

### PRE-NUMBERED ERA

**Core Contributor Membership Tier** | Tardfi | ⏳ Pending (never voted)
- Requires: 3mo Berachain activity, 1 Honeycomb, 500 BGT delegated, 1 approved proposal
- Compensation: 200 BERA/month

**eBay-Style Max Bidding** (odcpw) | Dev | ❌ Rejected — 0 votes
- Auto-bidding system: set max bid, contract auto-increments to ceiling
- Died in participation crisis

**Treasury Wallet Separation** (odcpw) | Tardfi | ❌ Failed — 2112/4, 38.05%/40% quorum
- 98% support, missed quorum by 2%
- Most painful near-miss of the participation crisis era

**Enable Formatting in Proposal Discussions** | PLZ | ❌ Rejected — 0 votes

**Auction Timing Optimization** (odcpw) | Dev | ✅ Passed — 1324/75, 25.25%
- 1-month rotation of auction durations (18h, 27h, etc.) to test global participation

**APDao PoL Reward Vault** | PLZ | ❌ Rejected — 0 votes
- Predecessor to apDAO Reward Vault

**apDAO Reward Vault** (Beorn) | Honey | ✅ Passed — 2139/7, 38.66%
- Create PoL Reward Vault using BERA incentives
- 25k BERA test phase, up to 70k BERA/week
- Strategy: incentives → BGT emissions → recycle into BERA/fatBERA

**Henlo** | PLZ | ❌ Rejected — 0 votes
- Predecessor to Allocate $HENLO proposal

**Allocate $HENLO into Henlockers** (Xabbu) | Honey | ✅ Passed — 1577/279, 33.56%
- Deploy ~800M HENLO (~50% of holdings) into lockers
- Meaningful opposition (279 Against, 15%)

---

### NUMBERED ERA

**apGP1: DAO Genesis** (THJ Corp.) | Genesis | ✅ Passed — 2024/11, 36.51%
- Foundational governance: 4 tracks adopted
- THJ contracted as Beekeepers (10% of LBT allocations)
- Genesis NFTs: never sell/transfer; Partner tokens: never sell
- Whitelisted: BeraHub, Kodiak, Beradrome, Euler, Infrared, Smilee, etc.
- Preferred stable: NECT
- Auction params: 1 day, 10% reserve buffer, 5% bid increment, 10% fee
- LBT params: 2% interest, 1 day–1 year term

**apGP6: Quorum Adjustment** (Cory) | Tardfi | ✅ Passed — 2343/4, 41.89%
- Reduced all quorums 25%: PLZ→11.25%, Tardfi→30%, Dev→18.75%, Honey→24.75%
- Critical governance survival vote — last time old high quorums were cleared

**BBC Attempt 1, 2, 3** | Honey | ⏳ Pending × 3 — 0 votes each
- Never made it to a live vote; participation failure at review stage

**apGP8: Bitcoin Reserve Strategy** | Honey | ❌ Failed — 443/418, 15.50%/24.75%
- Allocate 5-20% of yield + airdrops into wBTC
- Both participation failure AND genuine ideological split (nearly 50/50 on votes cast)
- BBC saga ends here — never found sufficient community alignment

**apGP9: OHM-Aligned Treasury Strategy** | Honey | ❌ Rejected (author withdrawal)
- Allocate 5-20% of yield into hOHM via Olympus CDs / Cooler Loans
- Author stood down after apGP8 (BTC) failed — reasoned OHM wouldn't pass either

**apGP10: Activate Reward Vault Deployments** | Honey | ✅ Passed — 1561/1, 27.85%
- Authorize Beekeepers to deploy assets into approved reward vaults
- No trading; yield deployment only; flexibility across approved assets

**apGP11: Deploy Treasury BERA to BakerDAO** | Honey | ⏳ Pending (never voted)
- Predecessor to apGP12

**apGP12: Deploy Treasury BERA to BakerDAO** (odcpw) | Honey | ✅ PASSED — 590/230, 26.87%
- Mint BREAD using BERA via CDP (99% LTV), deploy borrowed BERA for multiple yield streams
- ⚠️ FRONTEND BUG: Platform shows "Failed" — INCORRECT. 687 abstentions not counted.
- Actual result: quorum met (26.87% / 24.75%), proposal passed and executed

**apGP13: Governance Delegation** | Tardfi | ✅ Passed — 1766/3, 31.56%
- Introduced fully revocable delegation, max 5% per delegate
- LANDMARK VOTE: near-unanimous, transformed DAO participation dynamics

**apGP14: Seat Buyback** | Honey | ❌ Failed — 826/169, 18.63%/24.75%
- Buy back up to 100 seats over 100 days to increase NAV
- Strong support ratio, pre-delegation participation failure

**apGP15: APDAO x YAT Partnership (YEET Contribution)** | Honey | ✅ Passed — 1369/67, 27.46%
- Contribute YEET to YAT in exchange for shYEET
- Liquidity for locked YEET, yield exposure

**apGP16: YAT x ApDAO Proposal (BERA Contribution)** | Honey | ❌ Failed — 595/679, 26.52%
- Contribute 10k BERA to YAT treasury
- GENUINELY CONTESTED: 53% Against on votes cast. Quorum met, DAO voted No.
- Community approved the YEET leg (apGP15) but rejected the BERA leg — healthy governance

**apGP17: Strategic Acquisition of OG Bera NFTs** | Honey | ❌ Rejected — 0 votes

**apGP18: Acquiring Foundation Rebase NFTs** | Honey | ❌ Rejected — 0 votes

**apGP19: Bera Rebase NFT Acquisition** (Cory) | Honey | ❌ Failed — 1147/32, 22.93%/24.75%
- Up to 10,000 BERA budget for high-yield rebase NFTs
- 97% support, missed quorum by 1.82% — most painful near-miss of participation crisis

**apGP20: Bootstrap BERO/BERA Liquidity (Attempt 1)** | Honey | ❌ Rejected — 0 votes

**apGP21: Bootstrap BERO/BERA Liquidity (Attempt 2)** | Honey | ❌ Rejected — 0 votes

**apGP22: Bootstrap BERO/BERA Liquidity** (El Capitan) | Honey | ✅ Passed — 829/242, 19.20%
- Deploy liquidity to unlock Beradrome Reward Vault (~$95k)
- Earn ~70% APR in oBERO, strengthen Beradrome validator alignment
- Third attempt; post-delegation quorum threshold low enough to pass
- 242 Against (22.6%) — meaningful but minority opposition

**apGP23: SMILEE Airdrop Yield Deployment (Attempt 1)** | Honey | ❌ Rejected — 0 votes

**apGP24: SMILEE Airdrop Yield Deployment** (El Capitan) | Honey | ✅ Passed — 915/66, 17.49%
- Deploy SMILEE airdrop into yield + accumulation loop
- Phase 1 (0–69 days): Accumulate SMILEE, add liquidity
- Phase 2: Continue accumulation, route yield to Liquid Backing Treasury

**apGP25: SCOUT Acquisition Framework** (odcpw, El Capitan) | PLZ | ✅ Passed — 824/3, 14.74%
- Standardized acquisition framework: template, in-scope asset definitions, faster execution
- Enabled repeatable pathway for treasury acquisitions
- apGP26 was the first proposal executed under SCOUT

**apGP26: BTC & OHM Macro Reserve Sleeve** (El Capitan) | Honey | ✅ Passed — 863/9, 15.54%
- Route 20% of BERA yield into BTC (10%) + OHM (10%)
- OHM strategy: ≥60% in Olympus CDs, ≤40% in hOHM vaults; OHM trading at ~80% premium to liquid backing
- Resurrection of BTC/OHM thesis from apGP8/9 era, now under SCOUT framework
- Near-unanimous after previous failures — market conditions and framework made it viable

**apGP27: Zodiac Roles Module** (El Capitan) | PLZ | ✅ Passed — 723/3, 12.89%
- Enable role-based execution on multisig
- Faster execution for time-sensitive operations without full multisig coordination
- Maintains governance control while reducing bottlenecks

**apGP28: Apiary Finance Strategic Partnership** (SJ, NomadBera, El Capitan, Cory) | Honey | ✅ Passed — 1069/10, 19.05%
- Invest up to $50k into Apiary Finance (25k pre-bond + 25k matching)
- apDAO receives 25% of initial $APIARY supply at $100k FDV
- Thesis: BGT accumulation flywheel, treasury-aligned, strong supply constraints
- Risk: smart contract risk, 50% slash if matching not met
- 99.1% approval — strongest community conviction of post-delegation era

---

## Governance Pattern Analysis

### Iteration Patterns (Proposals That Took Multiple Attempts)
| Proposal | Attempts | Final Outcome |
|----------|----------|--------------|
| Bootstrap BERO/BERA Liquidity | 3 (apGP20, 21, 22) | ✅ Passed apGP22 |
| SMILEE Yield Deployment | 2 (apGP23, 24) | ✅ Passed apGP24 |
| BTC Reserve | 2 (apGP8, then apGP26 under SCOUT) | ✅ Passed apGP26 |
| Deploy to BakerDAO | 2 (apGP11 pending, apGP12) | ✅ Passed apGP12 |
| Bitcoin Collective (BBC) | 4+ attempts | ❌ Never passed |

### El Capitan Governance Track Record
Author or co-author: apGP22, apGP24, apGP25, apGP26, apGP27, apGP28
Pass rate: 100% (6/6)
Range: operational (apGP27), financial (apGP22, 24, 26), structural (apGP25), partnerships (apGP28)

### Healthy Governance Signals
- apGP16: Quorum met, voted down 53% — system working, community said no on merit
- apGP22: 22% Against on a passed proposal — not a rubber stamp
- apGP12: 687 abstentions (45.6%) — engagement without strong conviction

---

## Partnerships & Ecosystem Relationships

**Active partnerships (non-exhaustive)**:
Beradrome, Ramen Finance, Goldilocks, Yeet, Plug, MijaniDAO, Beraborrow, Booga Beras, D2 Finance, ApiaryFi, Steady Teddys

**Partnership structure — Diamond Paw model**:
- apDAO pledges to never sell governance tokens received from partners
- Harvests yield and governance benefits instead
- Directs portion of BGT/oBERO emissions to partner protocol vaults
- Exercises governance power in partner protocols for long-term stability

**Why protocols work with apDAO**:
- Direct access to most long-term-aligned members of Berachain community
- Diamond Paw = permanent governance ally
- Emissions voting = liquidity support
- Protocol governance = collaborative, growth-oriented participation

---

## Membership Benefits

**Revenue Sharing**: Members share revenues earned by DAO treasuries (validator, auction house, partner yields, strategies)

**Governance Rights**: Vote on internal DAO decisions, Berachain BGT vault voting, Beradrome vault voting, protocol governance voting

**Community Perks**: "Supercharged Honeycomb" — deposited NFTs earn compounded rewards as the largest collective Honeycomb holder. apDAO receives the most significant protocol incentives directed at Honeycomb holders.
