---
description: Overview of the Trading Rewards program.
---

# Trading Rewards

`14.5`**`%`** (`144,693,506 $ethDYDX`) of the token supply is allocated to be distributed to users who trade on dYdX v3 based on fees paid. Initially, `25.0%` of the token supply (`250,000,000 $ethDYDX`) was allocated for trading rewards.&#x20;

* In [DIP 16](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-16.md), the dYdX community [voted](https://dydx.community/dashboard/proposal/8) to reduce trading rewards by 25.0%. As a result, the allocation for trading rewards decreased from `25.0%` to `20.2%`.&#x20;
* In [DIP 20](https://dydx.community/dashboard/proposal/11), the dYdX community [voted](https://dydx.community/dashboard/proposal/11) to reduce trading rewards by a further 45.0%. As a result, the allocation for trading rewards decreased from `20.2%` to `14.5%`.&#x20;
*   In [DIP 29](https://dydx.community/dashboard/proposal/16), the dYdX community [voted](https://dydx.community/dashboard/proposal/16) to reduce trading rewards by ⅓ from Epoch 30-32 on dYdX v3 to the following values:

    * Epoch 30: 1,054,795 $ethDYDX
    * Epoch 31: 527,398 $ethDYDX
    * Epoch 32: 0 $ethDYDX

    Note, in DIP 29 the dYdX community voted to migrate the remaining allocation of Trading Rewards to the dYdX Chain for Trading Rewards.&#x20;

Trading rewards distributed in a given epoch were/will be reduced from 3,835,616 $ethDYDX to:

* 2,876,712 $ethDYDX in Epoch 15,
* 1,582,192 $ethDYDX in Epoch 21,
* 1,054,795 $ethDYDX in Epoch 30,
* 527,398 $ethDYDX in Epoch 31,
* 0 $ethDYDX in Epoch 32 onwards.

After Epoch 31, there will not be any trading rewards on dYdX v3. In [DIP 29](https://dydx.community/dashboard/proposal/16) on dYdX v3 and [Proposal 2](https://www.mintscan.io/dydx/proposals/2) on dYdX Chain, the dYdX community voted to credit the remaining amount of unvested $ethDYDX in dYdX v3 [Rewards Treasury Vester](https://etherscan.io/address/0xb9431e19b29b952d9358025f680077c3fd37292f) to the [dYdX Chain Rewards Treasury Vester `(dydx1wxje320an3karyc6mjw4zghs300dmrjkwn7xtk)`](https://www.mintscan.io/dydx/address/dydx1wxje320an3karyc6mjw4zghs300dmrjkwn7xtk)and subsequently distributed as trading rewards on the dYdX Chain, subject to the governance approval on dYdX Chain.&#x20;

**Objectives**

* Incentivize all traders to use dYdX v3.
* Accelerate market liquidity and overall product usage.

## **Overview**

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>Fees paid and estimated rewards in a given epoch</p></figcaption></figure>

Previously, $ethDYDX was distributed to traders based on fees paid on dYdX v3. $ethDYDX was distributed on a 28-day epoch basis over five years and was not subject to any vesting or lockups.&#x20;

In [DIP 29](https://dydx.community/dashboard/proposal/16), the dYdX community [voted](https://dydx.community/dashboard/proposal/16) to reduce trading rewards by ⅓ from Epoch 30-32 on dYdX v3 to the following values:

* Epoch 30: 1,054,795 $ethDYDX
* Epoch 31: 527,398 $ethDYDX
* Epoch 32 and all remaining epochs: 0 $ethDYDX



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

All traders on dYdX v3 were eligible to receive $ethDYDX as trading rewards.

dYdX v3 is not available to traders in the United States or Restricted Territories, as defined in dYdX Trading Inc.’s [Terms of Use](https://dydx.exchange/terms).

### How much $ethDYDX did I earn in the Trading Rewards program?

In the current epoch, users can see fees paid and estimated trading rewards at [**trade.dydx.exchange/portfolio/rewards**](https://trade.dydx.exchange/portfolio/rewards) where users' trading data exists.

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>Fees paid and estimated rewards in a given epoch</p></figcaption></figure>

Rewards from past epochs can be viewed at [**dydx.community/history/rewards**](https://dydx.community/history/rewards)**.**

### How do I claim my Trading Rewards? When can I withdraw and transfer my earned ethDYDX?

Earned $ethDYDX tokens via Trading Rewards will be transferable at the end of each epoch. $ethDYDX token holders are required to wait approximately `7 days` (**Waiting Period**) after the end of the epoch to claim their $ethDYDX tokens.&#x20;

After the 7-day waiting period, any community member can call the `Write` function on the`updateRoot` parameter on the [Merkle Distributor contract](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract) to make $ethDYDX rewards claimable.&#x20;

Steps:

1. On the [Merkle Distributor contract](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract) page on Etherscan, click on the `Contract` tab, and select `Write as Proxy.`
2. Click on the `Connect to Web3` button and connect your Web3 Wallet.

<figure><img src="../.gitbook/assets/merkle-distributor-contract.jpeg" alt=""><figcaption></figcaption></figure>

3\. Scroll down to the `updateRoot` parameter, and click on the `Write` button.

<figure><img src="../.gitbook/assets/updateRoot-claiming.jpeg" alt=""><figcaption></figcaption></figure>

**This transaction would require some ETH for gas fees, and will the transaction will fail if:**

* The 7-day waiting period is still in effect, or
* A community member has already successfully called the `updateRoot` parameter on the [Merkle Distributor contract](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract).

Once the transaction is finalized, traders can claim their Trading Rewards [here](https://dydx.community/dashboard). Users will need to click on `Claim`, sign a transaction, and pay gas fees to claim $ethDYDX.

![Portfolio overview of rewards](../.gitbook/assets/1-portfolio-overview-rewards.png)
