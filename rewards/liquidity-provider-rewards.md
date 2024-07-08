---
description: Overview of the Liquidity Provider rewards Program.
---

# ⚖️ Liquidity Provider Rewards

**3.3%** (`32,794,525 $ethDYDX`) of the token supply is allocated to be distributed to liquidity providers ("LPs") based on formulas that reward a combination of maker volume, uptime, two-sided depth, bid-ask spreads, and the number of markets supported. Initially, **7.5%** (`75,000,000 $ethDYDX`) of the token supply was allocated for LP rewards.

* In [DIP 24](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-24.md), the dYdX community [voted](https://dydx.community/dashboard/proposal/14) to reduce Liquidity Provider Rewards by 50% from   `1,150,685 $ethDYDX` per epoch to `575,343 $ethDYDX` per epoch. As a result, the allocation for LP rewards decreased from `7.5%` to `5.2%`.&#x20;
*   In [DIP 29](https://dydx.community/dashboard/proposal/16), the dYdX community [voted](https://dydx.community/dashboard/proposal/16) to reduce LP rewards by ⅓ from Epoch 30-32 on dYdX v3 to the following values:

    * Epoch 30: 383,562 $ethDYDX
    * Epoch 31: 191,781 $ethDYDX
    * Epoch 32: 0 $ethDYDX

    After Epoch 31, there will not be any LP rewards on dYdX v3. As a result, the allocation for LP rewards decreased from `5.2%` to `3.2%`.&#x20;

Since there is no distribution of Liquidity Provider rewards on dYdX Chain, the dYdX community in DIP 29 voted to migrate the remaining allocation for Liquidity Provider rewards to the dYdX Chain Community Treasury.

**Objectives**

* Improve two-sided liquidity and programmatically reward liquidity providers.

## **Overview**

To incentivize market liquidity, $ethDYDX will be distributed to liquidity providers based on formulas that reward participation in markets, maker volume, two-sided depth, spread (vs. mid-market), and uptime on dYdX v3. Any Ethereum address can earn these rewards, subject to a minimum maker volume threshold of 0.25% of maker volume in the preceding epoch. $ethDYDX was distributed on a 28-day epoch basis over five years and are not subject to any vesting or lockups.&#x20;

The following functions calculate how much $ethDYDX should be rewarded to each liquidity provider per epoch. In [DIP 15](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-15.md), the dYdX community voted to revise the LP rewards formula by splitting the functions for BTC/ETH markets and non BTC/ETH markets. In [DIP 19](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-19.md), the dYdX community voted to re-allocate the 0.05 stkDYDX weight to MakerVolume.&#x20;

Overall, the volume weighting in the functions was increased in all markets. The amount of ethDYDX earned is determined by the relative share of each participant’s $$Q_{FINAL}$$ ($$Q_{BTC}$$+​$$Q_{ETH}$$+$$Q_{non BTC/ETH}$$​).

<figure><img src="../.gitbook/assets/Updated LP Rewards Formulas.png" alt=""><figcaption></figcaption></figure>

Orders below a certain **minimum depth** (size) ($$MinDepth$$) per market are excluded, and orders over a certain **maximum spread** (mid-market spread) ($$MaxSpread$$) market are excluded as well.

Liquidity provider performance is monitored and calculated minute-by-minute (using randomized sampling) and aggregated into a $$Q_{SCORE}$$ for a given market. Given minute-by-minute sampling, each epoch has 28 days \* 24 hours \* 60 minutes of data points—40,320 data points per epoch in total.

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

<details>

<summary>Who is eligible for liquidity provider rewards?</summary>

All liquidity providers who have achieved a minimum of 0.25% of maker volume on dYdX v3 in the prior epoch are eligible to receive ethDYDX as rewards in a given epoch.

dYdX v3 is not available to liquidity providers in the United States or Restricted Territories, as defined in dYdX Trading Inc.’s [Terms of Use](https://dydx.exchange/terms).

</details>

<details>

<summary>How much $ethDYDX did I earn in the Liquidity Provider Rewards program?</summary>

In a given epoch, liquidity providers earn yield based on their relative $$Q_{SCORE}$$ in a given pair’s market. Each pair has its own relative reward amount set by governance. The expected amount of ethDYDX earned is displayed in the [LP Rewards Dashboard](https://p.datadoghq.com/sb/dc160ddf0-b32271920202875868dc46be6b66cf87?tpl\_var\_Market=btc\&from\_ts=1661805073576\&to\_ts=1661891473576\&live=true) and can be determined based on the number of liquidity providers involved, the relative $$Q_{SCORE}$$, and the amount of reward available for a given pair.

</details>

<details>

<summary>How do I claim my Liquidity Provider Rewards?</summary>

Liquidity Provider Rewards are surfaced in the [dYdX API](https://docs.dydx.exchange/). Although not surfaced on the governance user interface, they are still claimable via the governance at the end of every epoch [here](https://dydx.community/dashboard).

</details>

<details>

<summary>When can I withdraw and transfer my claimed $ethDYDX Liquidity Provider Rewards?</summary>

$ethDYDX tokens rewarded via the Liquidity Provider Rewards will become claimable and transferable once the initial transfer restriction period is lifted.

Starting in Epoch 1, $ethDYDX tokens rewarded via the Liquidity Provider Rewards will become claimable `7 days` (**Waiting Period**) after the end of each epoch.

</details>

<details>

<summary>How are two-sided depth, bid-ask spread, and uptime defined and measured?</summary>

* **Two-sided depth**

A two-sided liquidity provider on dYdX v3 is someone who actively quotes both buy and sell prices for a market, providing liquidity to the protocol. For example, in the BTC-USD market, they might offer to buy 10 BTC at $30,000 and sell 50 BTC at $30,100. Other participants can then trade with them at these prices. Liquidity providers are evaluated based on their ability to provide both buy and sell prices. Those who only quote on one side are excluded from rewards.

* **Mid-market spread**

The bid-ask spread is a common measure of liquidity, representing the difference between the highest bid (buy) price and the lowest ask (sell) price in a market. It is the main cost of trading and is collected by liquidity providers. The mid-market spread, which is the midpoint of the market, is another measure. For example, if the bid price for BTC-USD is $30,000 and the ask price is $30,100, the bid-ask spread is $100, and the mid-market spread is $50.

* **Uptime**

Liquidity provider uptime is critical for markets, especially in periods of high volatility. By applying an exponent of 5 to $$Uptime_{epoch}$$ as an input to the $$Q_{FINAL}$$, the rewards are skewed towards liquidity providers who maintain 2-sided liquidity constantly. In other words, a liquidity provider who provides uptime 99% of the time is exponentially more valuable than a liquidity provider who provides 90% uptime.

Uptime is the percentage of time orders are actively providing liquidity in a market, measured on a minute-by-minute basis with randomized sampling. It excludes periods when the dYdX Layer 2 Protocol is experiencing outages but may not account for occasional slowness or order acceptance issues, which would be considered bugs affecting all liquidity providers similarly.

</details>

<details>

<summary>How is the maximum spreads per market defined?</summary>

No $$Q_{BID}$$ or $$Q_{ASK}$$will be generated when the spread is above a given market’s $$MaxSpread$$.

The initial Max Spreads are as follows:

* BTC-USD: 20 bps
* ETH-USD: 20 bps
* other perpetual markets: 40 bps

</details>

<details>

<summary>How is the minimum depth (size) per market defined?</summary>

No $$Q_{BID}$$ or $$Q_{ASK}$$will be generated when the size is below a given market’s $$MinDepth$$.

The initial Min Depths are as follows:

* BTC-USD: $5000
* ETH-USD: $5000
* Other perpetual market: $1000

</details>

