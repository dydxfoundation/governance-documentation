---
description: Overview of the User Trading Rewards program.
---

# Trading Rewards

25% \(`250,000,000 DYDX`\) will be distributed to users who trade on the Protocol based on a combination of fees paid and open interest.

**Objectives**

* Incentivize all traders to use dYdX Layer 2 Perpetuals
* Accelerate market liquidity and overall product usage

## **Overview**

![](../.gitbook/assets/image%20%283%29.png)

DYDX will be distributed to traders based on a formula that rewards a combination of fees paid and open interest on the dYdX Layer 2 Protocol. DYDX will be distributed on a 28-day epoch basis over five years and is not subject to any vesting or lockups. 3,835,616 DYDX will be distributed per epoch.

The Cobb-Douglas function is used to compute how much DYDX is awarded to each trader during each epoch:

$$
w\ =\ \left(\frac{f}{F}\right)^{\alpha } \times \ \left(\frac{d}{D}\right)^{1-\alpha }
$$

$$
r=R\times \frac{w}{\sum\limits _{n} w_{n}} \ \ ,n=1,2...k
$$

| Term | Definition |
| :--- | :--- |
| r | Reward for a specific trader. |
| R | Total reward to be split between all traders in the pool for the epoch. |
| f | Total fees paid by a trader in this epoch. |
| w | Individual trader score. |
| $${\sum\limits _{n} w_{n}}$$ | Sum of all trader scores. |
| F | Total fees paid across all traders in this epoch. |
| d | A trader’s total weighted open interest \(measured hourly\) across all markets in this epoch. |
| D | Total weighted open interest \(measured hourly\) across all markets in this epoch. |
| k | Total number of traders in this epoch. |
| α | A constant in the range that determines the weight of fees vs open interest. At the outset α=0.7. |

The following example illustrates Trading Rewards earned by Traders A, B, and C using the formula listed above:

![](https://lh4.googleusercontent.com/LWYcMg6ImkQCV1aVsS2jVwjcFfTmBG4u7JZHrnf4l4MmHcxCZlu_af57UaSgHhr6TYi9thIyr8794SECk6_E8Vn4sR2QJFniUSbQGhIZZrkvTf0QRHmzzvt6awR9N8kxHhCooRp4)

## FAQ

### Who is eligible for trading rewards?

All traders on dYdX Layer 2 perpetuals are eligible to receive DYDX as trading rewards.

This product is not available to traders in the United States or Restricted Territories, as defined in dYdX’s [Terms of Use](https://dydx.exchange/terms).

### How much DYDX did I earn in the Trading Rewards program?

In a given epoch, users can see fees paid, average open interest, and estimated trading rewards here.

### How do I claim my Trading Rewards? When can I withdraw and transfer my earned DYDX?

Earned DYDX tokens via Trading Rewards will be transferable at the end of each epoch. DYDX token holders are required to wait approximately `7 days` \(**Waiting Period**\) after the end of the epoch to claim their tokens. Once tokens have been claimed, they can be used or delegated to dYdX governance.

Traders can claim their trading rewards at the end of every epoch [here](https://dydx.community/dashboard). 

Users will need to click on "Claim", sign a transaction, and pay gas fees to claim DYDX.

![](../.gitbook/assets/image%20%284%29.png)

### What is Open Interest?

Open interest is the total number of outstanding perpetual contracts that have not been settled for an asset. Open interest equals the total number of bought or sold contracts, not the total of both added together. Increasing open interest represents new or additional money coming into the market while decreasing open interest indicates money flowing out of the market.

Below is a table of trading activity in the options market for traders, A, B, C, D, and E. Open interest is calculated in USDC terms following the trading activity for each day:

| Time | Trading Activity | Open Interest \(USDC\) |
| :--- | :--- | :--- |
| July 1 | **Trader A** buys 1 BTC at $30,000 and **Trader B** sells 1 BTC at $30,000 | $30,000 |
| July 3 | **Trader C** buys 5 BTC at $30,000 and **Trader D** sells 5 BTC at $30,000 | $180,000 |
| July 5 | **Trader A** sells 1 BTC at $30,000 and **Trader D** buys 1 BTC at $30,000 | $150,000 |
| July 10 | **Trader E** buys 5 BTC at $30,000 and **Trader C** sells 5 BTC at $30,000 | $150,000 |

In the context of the Trading Rewards formula, open interest is measured hourly across all markets and a weighted average across a given epoch is used to calculate rewards.

### What is dYdX’s fee schedule?

dYdX uses a maker-taker fee model for determining its trade fees. There are two types of orders on dYdX — Maker and Taker orders.

* Maker orders are orders that do not immediately fill and rest on the order book — these orders add depth and liquidity to the order book. 
* Taker orders, on the other hand, immediately cross existing Maker orders. They remove liquidity from the order book.

Maker and Taker fees are determined using a 30-day volume-weighted Fee Schedule. The standard fee schedule is available [here](https://help.dydx.exchange/en/articles/4798040-perpetual-trade-fees). DYDX holders may receive a [trading fee discount](trading-rewards.md) based on their current holdings of DYDX.

