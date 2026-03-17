# Price History & Market Context

*Source: CoinGecko daily snapshots. Data through March 6, 2026. Not real-time.*

---

## BERA

**Data range**: February 6, 2025 → March 6, 2026

| Period | Price | Context |
|--------|-------|---------|
| Feb 6, 2025 (launch) | ~$8.58 | Berachain mainnet launch. Initial ATH period. |
| Feb–Mar 2025 | $6–$8.58 | Early euphoria, rapid sell-off as TGE trading begins |
| Mar–Jun 2025 | $2–$5 | Sustained decline. Bear market sets in post-TGE. |
| Jul–Oct 2025 | $1–$3 | apDAO participation crisis period. Member burnout from poor ecosystem performance. |
| Nov 2025–Jan 2026 | $0.8–$1.5 | Continued decline. Post-delegation era begins but price doesn't recover. |
| Mar 6, 2026 | ~$0.538 | Recent price. Down ~94% from ATH. |

**Market cap at launch**: ~$917M
**Market cap Mar 6, 2026**: ~$123M

**Narrative significance**: The BERA price arc is inseparable from the apDAO governance crisis. The bear market that followed TGE directly caused member burnout and participation collapse. The DAO's governance reforms (apGP6, apGP13) were responses to an ecosystem-wide participation failure driven largely by price environment.

---

## iBGT (Infrared BGT)

**Data range**: February 28, 2025 → March 6, 2026

| Period | Price | Context |
|--------|-------|---------|
| Feb 28, 2025 | ~$10.55 | Shortly after Infrared launch |
| Mar 2025 | $9.93–$10.55 | Tight range, premium to BERA (BGT ≠ BERA in value terms) |
| Mar 6, 2026 | ~$0.543 | Converged toward BERA price over time |

**Note**: iBGT tracks BGT, which can be burned 1:1 for BERA. Over time, iBGT price converges toward BERA price minus any discount for the wrapper.

---

## LOCKS (Goldilocks)

**Data range**: April 29, 2025 → March 6, 2026

| Period | Price | Context |
|--------|-------|---------|
| Apr 29, 2025 (launch) | ~$0.0201 | Goldilocks TGE |
| May–Jun 2025 | $0.019–$0.020 | Early price discovery near floor |
| Jul–Oct 2025 | Varied | Market activity within bonding curve mechanics |
| Mar 6, 2026 | ~$0.011 | Recent price, near/below initial |

**Key mechanic**: LOCKS floor price can never decrease due to Goldiswap mechanics. Market price shown here is above floor; if it appears below initial, may reflect market reserve dynamics.

**apGP26 context**: At time of apGP26 (Dec 2025), OHM was trading at ~80% premium to its liquid backing. This informed the ≥60% Olympus CDs / ≤40% hOHM allocation.

---

## SAIL.r (Liquid Royalty Protocol)

**Data range**: February 23, 2026 → March 6, 2026

| Period | Price | Context |
|--------|-------|---------|
| Feb 23–26, 2026 | ~$13.06–$13.37 | Early post-launch period |
| Mar 4–6, 2026 | ~$13.77–$13.99 | Gradual appreciation |

**Volume note**: Extremely thin volume ($85k–$698 daily). Price discovery still early.

**Benchmarks used in apDAO treasury modeling**:
- SAIL.r royalty yield: ~5.13%
- SAIL.r-USDe BGT APR: ~51.80% (Kodiak LP)
- hVUX staking benchmark reference: GlazeCorp's 26.3%

---

## Market Context Summary

The full Berachain ecosystem has operated in a sustained bear market since TGE (Feb 2025). Key tokens:

| Token | Launch | Peak | Mar 2026 | Decline |
|-------|--------|------|----------|---------|
| BERA | Feb 2025 | ~$8.58 | ~$0.54 | ~94% |
| iBGT | Feb 2025 | ~$10.55 | ~$0.54 | ~95% |
| LOCKS | Apr 2025 | ~$0.020 | ~$0.011 | ~45% |
| SAIL.r | Feb 2026 | ~$13.99 | ~$13.99 | N/A (new) |

**Interpretation for builders and historians**:
- Berachain protocols have been building and shipping through a deep bear market
- PoL mechanics continue to function regardless of token prices — BGT flows, incentives are paid, vaults are active
- The ecosystem's DeFi primitive stack (Infrared, Kodiak, Goldilocks, BEND, Beradrome) matured during the downturn
- apDAO's treasury strategies and governance evolution happened under sustained price pressure
- Any thesis about "what Berachain looks like in a bull market" is genuinely unproven — the ecosystem has only existed in decline

---

## Data Limitations

- CoinGecko daily snapshots — not real-time, not intraday
- BERA and iBGT data appears to have some duplicate entries at launch (same price for consecutive days — CoinGecko initialization artifact)
- LOCKS market cap shows $0 — likely due to bonding curve supply elasticity making circulating supply hard to calculate
- SAIL.r market cap shows $0 — very new token, data still being populated
- Do not use these figures for trading decisions — use live oracle data
