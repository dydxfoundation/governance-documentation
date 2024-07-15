---
description: 交易奖励计划概述。
---

#

`14.5`**`%`** (`144,693,506 $ethDYDX`) 的代币供应将根据用户在 dYdX v3 上交易所付的费用分配给用户。 最初，代币供应量 (`250,000,000 $ethDYDX`) 的 `25.0%` 分配给交易奖励。

* 在 [DIP 16](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-16.md) 中，dYdX 社区[投票](https://dydx.community/dashboard/proposal/8)将交易奖励减少 25.0%。因此，分配给交易奖励的代币从 `25.0%` 降至 `20.2%`。
* 在 [DIP 20](https://dydx.community/dashboard/proposal/11) 中，dYdX 社区[投票](https://dydx.community/dashboard/proposal/11)将交易奖励再减少 45.0%。因此，分配给交易奖励的代币从 `20.2%` 降至 `14.5%`。
*   在 [DIP 29](https://dydx.community/dashboard/proposal/16) 中，dYdX 社区[投票](https://dydx.community/dashboard/proposal/16)决定将 dYdX v3 上的交易奖励从 30-32 时段减少 ⅓，减为以下值：

    * 时段 30：1,054,795 $ethDYDX
    * 时段 31：527,398 $ethDYDX
    * 时段 32：0 $ethDYDX

    请注意，在 DIP 29 中，dYdX 社区投票决定将剩余的交易奖励分配迁移到 dYdX Chain 上作为交易奖励。

在特定时段分配的交易奖励将从 3,835,616 $ethDYDX 减少为以下值：

* 时段 15：2,876,712 $ethDYDX；
* 时段 21：1,582,192 $ethDYDX；
* 时段 30：1,054,795 $ethDYDX；
* 时段 31：527,398 $ethDYDX；
* 32 及以后时段：0 $ethDYDX。

在时段 31 之后，dYdX v3 上将没有任何交易奖励。在 dYdX v3 上的 [DIP 29](https://dydx.community/dashboard/proposal/16) 和 dYdX 链上的 [提议 2](https://www.mintscan.io/dydx/proposals/2) 中，dYdX 社区投票决定将 dYdX v3 [奖励资金库归属者](https://etherscan.io/address/0xb9431e19b29b952d9358025f680077c3fd37292f) 上剩余的未归属 $ethDYDX 金额转入 [dYdX 链奖励资金库归属者 `(dydx1wxje320an3karyc6mjw4zghs300dmrjkwn7xtk)`](https://www.mintscan.io/dydx/address/dydx1wxje320an3karyc6mjw4zghs300dmrjkwn7xtk)，并在 dYdX 链上作为交易奖励进行分配，但前提是在 dYdX 链上获得治理批准。

**目标**

* 激励所有交易者使用 dYdX v3。
* 加快市场流动性以及产品的总体使用情况。

## **概述**

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>在给定时段内所支付的费用以及预估的奖励</p></figcaption></figure>

此前，$ethDYDX 根据在 dYdX v3 上支付的费用分配给交易者。$ethDYDX 在五年内以 28 天的时段为基础分配，不受任何约束或锁定。

在 [DIP 29](https://dydx.community/dashboard/proposal/16) 中，dYdX 社区[投票](https://dydx.community/dashboard/proposal/16)决定将 dYdX v3 上的交易奖励从 30-32 时段减少 ⅓，减为以下值：

* 时段 30：1,054,795 $ethDYDX
* 时段 31：527,398 $ethDYDX
* 时段 32 和所有剩余时段：0 $ethDYDX



<figure><img src="../.gitbook/assets/1-trading-rewards-formula-new.png" alt=""><figcaption></figcaption></figure>

$$
r=R\times \frac{w}{\sum\limits _{n} w_{n}} \ \ ,n=1,2...k
$$

| 术语 | 定义 |
| ---------------------------- | ----------------------------------------------------------------------- |
| r | 特定交易者的奖励。 |
| R | 将在该时段中资金池中所有交易者之间分配的总奖励。 |
| f | 本时段交易者支付的总费用。 |
| 周 | 个人交易者分数。 |
| $${\sum\limits _{n} w_{n}}$$ | 所有交易者分数的总和。 |
| k | 本时段的交易者总数。 |

在 [DIP-13](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-13.md) 中，dYdX 社区投票表决，将公式简化为基于交易者在给定时段内支付的总费用。

##

通过“交易奖励”赚取的 $ethDYDX 代币可以在每个时段结束时转账。$ethDYDX 代币持有人必须在时段结束后等待约 `7 天`（**等待期**）才能申领 $ethDYDX 代币。

在 7 天等待期过后，社区成员均可在[“Merkle 分配”合约](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract)`“更新根目录”`参数上调用`“撰写”`函数，来申领 $ethDYDX 奖励。

步骤：

1. 在 Etherscan 的 [Merkle 分发合约](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract)页面上，单击`合约`选项卡，然后选择`以代理身份写入。`
2. 单击`连接到 Web3` 按钮，连接您的 Web3 钱包。

<figure><img src="../.gitbook/assets/merkle-distributor-contract.jpeg" alt=""><figcaption></figcaption></figure>

3\. 向下滚动至 `updateRoot` 参数，然后单击 `Write` 按钮。

<figure><img src="../.gitbook/assets/updateRoot-claiming.jpeg" alt=""><figcaption></figcaption></figure>



* 7 天等待期仍然有效，或
* 社区成员已成功调用 [Merkle 分发合约](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract) 上的 `updateRoot` 参数。

交易完成后，交易者可以在[此处](https://dydx.community/dashboard)申领他们的交易奖励。 用户需要单击`申`领、签署交易并支付 gas 费才能申领 $ethDYDX。

![资金组合奖励概述](../.gitbook/assets/1-portfolio-overview-rewards.png)

## 常见问题解答

<details>

<summary>谁有资格获得交易奖励？</summary>

dYdX v3 上的所有交易者都有资格获得 $ethDYDX 作为交易奖励。

dYdX v3 不适用于在 dYdX Trading Inc 的[《使用条款》](https://dydx.exchange/terms)中规定的位于美国或受限制地区的交易者。

</details>

<details>

<summary>我在“交易奖励”计划中赚取了多少 $ethDYDX？</summary>

在当前时段，用户可以在[**trade.dydx.exchange/portfolio/rewards**](https://trade.dydx.exchange/portfolio/rewards)查看已支付的费用和预估的交易奖励，该网站存有用户的交易数据。

如需查看过去时段的奖励，请访问[**dydx.community/history/rewards**](https://dydx.community/history/rewards)**。**

</details>
