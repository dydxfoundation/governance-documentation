---
description: Overview of the Liquidity Provider rewards Program.
---

# Liquidity Provider Rewards

**5.2%** (`52,458,925 $DYDX`) of the token supply is allocated to be distributed to liquidity providers ("LPs") based on formulas that reward a combination of maker volume, uptime, two-sided depth, bid-ask spreads, and the number of markets supported. Initially, **7.5%** (`75,000,000 $DYDX`)  of the token supply  was allocated for LP rewards.

* In [DIP 24](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-24.md), the dYdX community [voted](https://dydx.community/dashboard/proposal/14) to reduce Liquidity Provider Rewards by 50% from    `1,150,685 DYDX` per epoch to `575,343 DYDX` per epoch. As a result, the allocation for LP rewards decreased from `7.5%` to `5.2%`.&#x20;

**Objectives**

* Improve two-sided liquidity and programmatically reward liquidity providers.

## **Overview**

To incentivize market liquidity, $DYDX will be distributed to liquidity providers based on formulas that reward participation in markets, maker volume, two-sided depth, spread (vs. mid-market), and uptime on dYdX’s Layer 2 Protocol. Any Ethereum address can earn these rewards, subject to a minimum maker volume threshold of 0.25% of maker volume in the preceding epoch. $DYDX will be distributed on a 28-day epoch basis over five years and are not subject to any vesting or lockups. 575,343 $DYDX will be distributed per epoch.

The following functions are used to compute how much $DYDX should be rewarded to each liquidity provider per epoch. In [DIP 15](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-15.md), the dYdX community voted to revise the LP rewards formula by splitting the functions for BTC/ETH markets and non BTC/ETH markets. In [DIP 19](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-19.md), the dYdX community voted to re-allocate the 0.05 $stkDYDX weight to MakerVolume.&#x20;

Overall, the weighting of volume in the functions was increased in all markets. The amount of $DYDX earned is determined by the relative share of each participant’s $$Q_{FINAL}$$ ($$Q_{BTC}$$+​$$Q_{ETH}$$+$$Q_{non BTC/ETH}$$​).

<figure><img src="../.gitbook/assets/Updated LP Rewards Formulas.png" alt=""><figcaption></figcaption></figure>

Orders below a certain **minimum depth** (size) ($$MinDepth$$) per market are excluded, and orders over a certain **maximum spread** (mid-market spread) ($$MaxSpread$$) market are excluded as well.

Liquidity provider performance is monitored and calculated on a minute-by-minute basis (using randomized sampling) and aggregated into a $$Q_{SCORE}$$ for a given market. Given minute-by-minute sampling, each epoch has 28 days \* 24 hours \* 60 minutes of data points—40,320 data points per epoch in total.

Liquidity providers earn monthly rewards based on their relative $$Q_{FINAL}$$ share per epoch.

The above formula is broken out into step-by-step calculations below for detail:

| _Maker Volume_                                                                          | Total maker volume for the Epoch.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| --------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <img src="../.gitbook/assets/1-qbid-formula.png" alt="" data-size="original">           | <p>Assume a liquidity provider has multiple open bid orders (1 BTC at $29,900, 5 BTC at $29,850, 10 BTC at $29,500) on the BTC-USD order book and BTC is currently at $30,000 (based on mid-market). Assume MinDepth is $5000 and MaxSpread vs. mid-market is $200, or 67 Basis Points ($200/30000). A BP is one-hundredth of one percent.<br></p><p><span class="math">Q_{BID} = (1\ \times \left(\frac{$29,900}{$100/30000}\right)) + (5\ \times \left(\frac{$29,850}{$150/30000}\right))</span></p><p><br><span class="math">Q_{BID}</span>is calculated every minute using random sampling.<br></p>    |
| <img src="../.gitbook/assets/1-qask-formula.png" alt="" data-size="original">           | <p>Assume a liquidity provider has multiple open ask orders (0.1 BTC at $30,100, 5 BTC at $30,150, 10 BTC at $30,175) on the BTC-USD order book and BTC is currently trading at $30,000 (based on mid-market). Assume MinDepth is $5000 and MaxSpread vs. mid-market is $200, or 67 Basis Points ($200/30000). A BP is one-hundredth of one percent.</p><p><span class="math">Q_{ASK} = (5\ \times \left(\frac{$30,150}{$150/30000}\right)) + (10\ \times \left(\frac{$30,175}{$175/30000}\right))</span></p><p><br><span class="math">Q_{ASK}</span> is calculated every minute at a random interval.</p> |
| <img src="../.gitbook/assets/1-qmin-formula.png" alt="" data-size="original">           | <p>Rewards 2-sided liquidity by taking the minimum of <span class="math">Q_{BID}</span> and <span class="math">Q_{ASK}</span>.<br></p><p>Calculated every minute.</p>                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| <img src="../.gitbook/assets/1-qpoech-formula.png" alt="" data-size="original">         | $$Q_{EPOCH}$$is the sum of all $$Q_{MIN}$$in a given epoch.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| <img src="../.gitbook/assets/1-q-uptime-epoch-formula.png" alt="" data-size="original"> | $$Uptime_{EPOCH}$$is the time in an epoch that a given market maker was live and quoting on both the bid and ask sides with order sizes greater than stated order minimum (noted below by market) and spreads smaller than stated maximum spread (noted below by market).                                                                                                                                                                                                                                                                                                                                  |
| <img src="../.gitbook/assets/1-qfinal-epoch-formula.png" alt="" data-size="original">   | $$Q_{FINAL}$$normalizes $$Q_{EPOCH}$$to account for uptime                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |

Each market will have its own rewards pool that will be weighted differently. In [DIP 15](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-15.md), the dYdX community voted to reduce the allocation of total rewards in BTC-USD and ETH-USDC to 10% each. The set of weights applied to each market is as follows:

| Market                  | % Allocation of Total Rewards Pool                               |
| ----------------------- | ---------------------------------------------------------------- |
| BTC-USD                 | 10%                                                              |
| ETH-USD                 | 10%                                                              |
| Other perpetual markets | ![](../.gitbook/assets/1-other-perpetual-markets-lp-weights.png) |

## FAQ

### Who is eligible for liquidity provider rewards?

All liquidity providers who have achieved a minimum of 0.25% of maker volume on the dYdX Layer 2 Protocol in the prior epoch are eligible to receive $DYDX as rewards in a given epoch.

The dYdX Layer 2 Protocol is not available to liquidity providers in the United States or Restricted Territories, as defined in dYdX Trading Inc.’s [Terms of Use](https://dydx.exchange/terms).

### How much $DYDX did I earn in the Liquidity Provider Rewards program?

In a given epoch, liquidity providers earn yield based on their relative $$Q_{SCORE}$$ in a given pair’s market. Each pair has its own relative reward amount set by governance. The expected amount of DYDX earned is displayed in the [LP Rewards Dashboard](https://p.datadoghq.com/sb/dc160ddf0-b32271920202875868dc46be6b66cf87?tpl\_var\_Market=btc\&from\_ts=1661805073576\&to\_ts=1661891473576\&live=true) and can be determined based on the number of liquidity providers involved, the relative $$Q_{SCORE}$$, and the amount of reward available for a given pair.

### How do I claim my Liquidity Provider Rewards?

Liquidity Provider Rewards are surfaced in the [dYdX API](https://docs.dydx.exchange/). Although not surfaced on the governance user interface, they are still claimable via the governance at the end of every epoch [here](https://dydx.community/dashboard).

### When can I withdraw and transfer my claimed $DYDX Liquidity Provider Rewards?

$DYDX tokens rewarded via the Liquidity Provider Rewards will become claimable and transferable once the initial transfer restriction period is lifted.

Starting in Epoch 1, $DYDX tokens rewarded via the Liquidity Provider Rewards will become claimable `7 days` (**Waiting Period**) after the end of each epoch.

### How are two-sided depth, bid-ask spread, and uptime defined and measured?

**Two-sided depth**

A two-sided liquidity provider is a firm or individual who actively quotes two-sided markets on the dYdX Layer 2 Protocol, providing bids and asks for a given market. They provide liquidity to the protocol overall.

For instance, a liquidity provider in the BTC-USD market may provide a quote of $30,000-$30,100, 10x50. This means that they bid (they will buy) 10 BTC for $30,000 and also offer (they will sell) 50 BTC at $30,100. Other market participants may then buy (lift the offer) from the liquidity provider at $30,100 or sell to them (hit the bid) at $30,000.

Liquidity providers are assessed on their ability to provide both bids and asks on a given market. Liquidity providers who only quote on 1-side (either just bids or asks) are excluded from receiving rewards due to the min() function.

**Mid-market spread**

One common measure of liquidity is the bid-ask spread: the spread between the highest bid (order to buy) price and the lowest ask (order to sell) price in a market. The difference between the bid and the ask, the spread, is the principal transaction cost of trading (outside commissions), and it is collected by the liquidity provider by processing orders at the bid and ask prices. The spread measures the cost of transacting immediately to a user.

The mid-market spread specifically takes the midpoint of the market. With this formula, orders below the MinDepth amount for each market are excluded also.

For instance, if a liquidity provider’s bid price for BTC-USD is $30,000 and the ask price is $30,100, then the bid-ask spread is $100. The mid-market price is $30,050, and the mid-market spread is $50.

**Uptime**

Liquidity provider uptime is critical for markets, especially in periods of high volatility. By applying an exponent of 5 to $$Uptime_{epoch}$$ as an input to the $$Q_{FINAL}$$, the rewards are skewed towards liquidity providers who maintain 2-sided liquidity constantly. In other words, a liquidity provider who provides uptime 99% of the time is exponentially more valuable than a liquidity provider who provides 90% uptime.

Uptime is defined as the percentage of time orders are in a given market providing liquidity on a minute-by-minute basis (with randomized sampling). Uptime excludes periods of time when outages exist on the dYdX Layer 2 Protocol itself. There may be edge cases where the exchange is slow or not accepting orders (but is not an outage)—in which case the above would not apply (but that would be considered a bug and all liquidity providers would be similarly affected, as with outages).

### How is the maximum spreads per market defined?

No $$Q_{BID}$$ or $$Q_{ASK}$$will be generated when the spread is above a given market’s $$MaxSpread$$.

The initial Max Spreads are as follows:

| Market                  | Max Spread vs Mid-Market (Bid and Ask) |
| ----------------------- | -------------------------------------- |
| BTC-USD                 | 20 bps                                 |
| ETH-USD                 | 20 bps                                 |
| Other perpetual markets | 40 bps                                 |

### How is the minimum depth (size) per market defined?

No $$Q_{BID}$$ or $$Q_{ASK}$$will be generated when the size is below a given market’s $$MinDepth$$.

The initial Min Depths are as follows:

| **Market**              | **Min Depth (Bid and Ask)** |
| ----------------------- | --------------------------- |
| BTC-USD                 | $5000                       |
| ETH-USD                 | $5000                       |
| Other perpetual markets | $1000                       |
