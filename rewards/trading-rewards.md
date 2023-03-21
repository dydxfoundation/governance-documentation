---
description: 交易奖励计划概述。
---

# 交易奖励

代币供应量的 `20.2`**`%` ** (`201,883,560 $DYDX`) 按照所付费用，分配给在 dYdX 第 2 层协议上交易的用户。最初，代币供应量 (`250,000,000 $DYDX`) 的 `25.0%` 分配给交易奖励。

* 在 [DIP 16](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-16.md) 中，dYdX 社区[投票](https://dydx.community/dashboard/proposal/8)将交易奖励减少 25.0%。因此，分配给交易奖励的代币从 `25.0%` 降至 `20.2%`。
* 在 [DIP 20](https://dydx.community/dashboard/proposal/11) 中，dYdX 社区[投票](https://dydx.community/dashboard/proposal/11)将交易奖励再减少 45.0%。因此，分配给交易奖励的代币从 `20.2%` 降至 `14.5%`。

以给定时段分配的交易奖励，在 15 时段从 3,835,616 $DYDX 减少至 2,876,712 $DYDX，在 21 时段从 2,876,712 $DYDX 减少至 1,582,192 $DYDX。

**目标**

* 激励所有交易者使用 dYdX 第 2 层协议。
* 加快市场流动性以及产品的总体使用情况。

## **概述**

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>在给定时段内所支付的费用以及预估的奖励</p></figcaption></figure>

根据交易者在 dYdX 第 2 层协议上所付费用，向交易者分配 $DYDX。五年内以 28 天时段为周期，分配 $DYDX，并且不受归属或锁定限制。每时段将分配 1,582,192 $DYDX。

由于社区投票将 [DIP 16](https://dydx.community/dashboard/proposal/8) 中的交易奖励减少了 25%，即 958,904 $DYDX，在 [DIP 20](https://dydx.community/dashboard/proposal/11) 中再减少 45%，即 1,294,520 $DYDX，奖励资金库中剩余的 2,253,424 $DYDX 可通过[治理投票](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters)由 dYdX 社区使用/支出。

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

## 常见问题解答

### 谁有资格获得交易奖励？

dYdX 第 2 层协议上的所有交易者皆有资格获得交易奖励 ($DYDX)。

如 dYdX Trading Inc.[ 使用条款](https://dydx.exchange/terms)所定义，DYdX Layer 2 协议不适用于美国或受限制地区的交易者。

### 我在交易奖励计划中赚取了多少 DYDX？

在当前时段，用户可以在[**trade.dydx.exchange/portfolio/rewards**](https://trade.dydx.exchange/portfolio/rewards)查看已支付的费用和预估的交易奖励，该网站存有用户的交易数据。

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>在给定时段内所支付的费用以及预估的奖励</p></figcaption></figure>

如需查看过去时段的奖励，请访问[**dydx.community/history/rewards**](https://dydx.community/history/rewards)**。**

### 我如何申领我的交易奖励？何时可以提现并转让赚取的 $DYDX？

在交易奖励中赚取的 $DYDX 代币将在每个时段结束时得以转让。$DYDX 代币持有人必须在时段结束后等待大约 `7 天`（等待**期**）才能申领 $DYDX 代币。

7 天等待期过后，任意社区成员均可以在 [Merkle 分发合约](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract) `更新根目录` 参数上调用 `撰写` 函数，以便申领 DYDX 奖励。

步骤：

1. 在 Etherscan 的 [Merkle 分发合约](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract)页面上，单击`合约`选项卡，然后选择`以代理身份写入。`
2. 单击`连接到互联网3`按钮，连接您的互联网3钱包。

<figure><img src="../.gitbook/assets/merkle-distributor-contract.jpeg" alt=""><figcaption></figcaption></figure>

3\. 向下滚动至 `更新根目录` 参数，然后单击`撰写` 按钮。

<figure><img src="../.gitbook/assets/updateRoot-claiming.jpeg" alt=""><figcaption></figcaption></figure>

**该笔交易需要一些以太币来支付煤气费，如出现以下情况，交易将会失败：**

* 7 天等待期仍然有效，或
* 社区成员已成功调用 [Merkle 分发合约](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract) 上的 `更新根目录` 参数。

交易完成后，交易者可以在[此处](https://dydx.community/dashboard)申领他们的交易奖励。 用户需要单击`申领`、签署交易并支付煤气费才能申领 $DYDX。

![资金组合奖励概述](../.gitbook/assets/1-portfolio-overview-rewards.png)
