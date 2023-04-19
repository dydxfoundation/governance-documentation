---
description: Overview of the Trading Rewards program.
---

# Trading Rewards

`20.2`**`%`** (`201,883,560 $DYDX`) of the token supply is allocated to be distributed to users who trade on the dYdX Layer 2 Protocol based on fees paid. Initially, `25.0%` of the token supply (`250,000,000 $DYDX`) was allocated for trading rewards.&#x20;

* In [DIP 16](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-16.md), the dYdX community [voted](https://dydx.community/dashboard/proposal/8) to reduce trading rewards by 25.0%. As a result, the allocation for trading rewards decreased from `25.0%` to `20.2%`.&#x20;
* In [DIP20](https://dydx.community/dashboard/proposal/11), the dYdX community [voted](https://dydx.community/dashboard/proposal/11) to reduce trading rewards by a further 45.0%. As a result, the allocation for trading rewards decreased from `20.2%` to `14.5%`.&#x20;

Trading rewards distributed in a given epoch were reduced from 3,835,616 $DYDX to 2,876,712 $DYDX in Epoch 15, and from 2,876,712 $DYDX to 1,582,192 $DYDX in Epoch 21.

**Objectives**

* Incentivize all traders to use the dYdX Layer 2 Protocol.
* Accelerate market liquidity and overall product usage.

## **Overview**

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>Fees paid and estimated rewards in a given epoch</p></figcaption></figure>

$DYDX will be distributed to traders based on fees paid on the dYdX Layer 2 Protocol. $DYDX will be distributed on a 28-day epoch basis over five years and is not subject to any vesting or lockups. 1,582,192 $DYDX will be distributed per epoch.

With the community voting to proceed with a 25% reduction in trading rewards by 958,904 $DYDX in [DIP16](https://dydx.community/dashboard/proposal/8), and a further 45% by 1,294,520 $DYDX in [DIP20](https://dydx.community/dashboard/proposal/11), the remaining 2,253,424 $DYDX that accrues in the Rewards Treasury can be used/directed by the dYdX community with a [governance vote](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters).

<figure><img src="../.gitbook/assets/1-trading-rewards-formula-new.png" alt=""><figcaption></figcaption></figure>

$$
r=R\times \frac{w}{\sum\limits _{n} w_{n}} \ \ ,n=1,2...k
$$

| Term                         | Definition                                                              |
| ---------------------------- | ----------------------------------------------------------------------- |
| r                            | Reward for a specific trader.                                           |
| R                            | Total reward to be split between all traders in the pool for the epoch. |
| f                            | Total fees paid by a trader in this epoch.                              |
| w                            | Individual trader score.                                                |
| $${\sum\limits _{n} w_{n}}$$ | Sum of all trader scores.                                               |
| k                            | Total number of traders in this epoch.                                  |

In [DIP-13](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-13.md), the dYdX Community voted to simplify the formula to be based on total fees paid by a trader in a given epoch.

## FAQ

### Who is eligible for trading rewards?

All traders on the dYdX Layer 2 protocol are eligible to receive $DYDX as trading rewards.

The dYdX Layer 2 Protocol is not available to traders in the United States or Restricted Territories, as defined in dYdX Trading Inc.’s [Terms of Use](https://dydx.exchange/terms).

### How much DYDX did I earn in the Trading Rewards program?

In the current epoch, users can see fees paid and estimated trading rewards at [**trade.dydx.exchange/portfolio/rewards**](https://trade.dydx.exchange/portfolio/rewards) where users' trading data exists.

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>Fees paid and estimated rewards in a given epoch</p></figcaption></figure>

Rewards from past epochs can be viewed at [**dydx.community/history/rewards**](https://dydx.community/history/rewards)**.**

### How do I claim my Trading Rewards? When can I withdraw and transfer my earned $DYDX?

Earned $DYDX tokens via Trading Rewards will be transferable at the end of each epoch. $DYDX token holders are required to wait approximately `7 days` (**Waiting Period**) after the end of the epoch to claim their $DYDX tokens.&#x20;

After the 7-day waiting period, any community member can call the `Write` function on the`updateRoot` parameter on the [Merkle Distributor contract](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract) to make DYDX rewards claimable.&#x20;

Steps:

1. On the [Merkle Distributor contract](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract) page on Etherscan, click on the `Contract` tab, and select `Write as Proxy.`
2. Click on the `Connect to Web3` button and connect your Web3 Wallet.

<figure><img src="../.gitbook/assets/merkle-distributor-contract.jpeg" alt=""><figcaption></figcaption></figure>

3\. Scroll down to the `updateRoot` parameter, and click on the `Write` button.

<figure><img src="../.gitbook/assets/updateRoot-claiming.jpeg" alt=""><figcaption></figcaption></figure>

**This transaction would require some ETH for gas fees, and will the transaction will fail if:**

* The 7-day waiting period is still in effect, or
* A community member has already successfully called the `updateRoot` parameter on the [Merkle Distributor contract](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract).

Once the transaction is finalized, traders can claim their Trading Rewards [here](https://dydx.community/dashboard). Users will need to click on `Claim`, sign a transaction, and pay gas fees to claim $DYDX.

![Portfolio overview of rewards](../.gitbook/assets/1-portfolio-overview-rewards.png)
