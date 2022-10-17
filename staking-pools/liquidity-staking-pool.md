---
description: 流动性质押池概述
---

# 流动性模块

初始代币供应量的 `2.50%` （`25,000,000 个 DYDX`） 分配给将 USDC 质押到流动性质押池的用户。 流动性质押池自 2022 年 9 月 29 日起不再运行。在 [DIP 14](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-14.md) 中，dYdX 社区[投票](https://dydx.community/dashboard/proposal/7)决定将每秒流动性质押池奖励设置为 0，以便有效逐步终止流动性质押池和借款池。\
\
此前，DYDX 分发给将 USDC 质押到流动性质押池的用户。社区批准的流动性提供方使用质押的 USDC 基于 dYdX Layer 2 协议进行做市，从而进一步提高市场的可用流动性。流动性提供方被限制使用 dYdX Layer 2 协议以外的借贷资金。

## **质押**概述

目前，在流动性质押池中质押的 USDC 不会获得奖励。

先前分配给 USDC 质押人的 383,562 个 DYDX 将在奖励资金库中积累，并可由 dYdX 社区通过[治理投票](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters)来使用。

## USDC解除质押和提现

质押人必须在[**时段**](../start-here/epochs.md)结束前至少 `3 天`请求提现 USDC（**停市窗口期**），才能在该时段结束后提现质押人的 USDC。如果质押人不请求提现，他们质押的USDC将被转入下一纪元。

在**停市窗口期**期间，无法请求提现。

在 [DIP 14](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-14.md) 中，dYdX 社区 [投票](https://dydx.community/dashboard/proposal/7) 决定将停市窗口期从 `14 天`减少至 `3 天`。

## 什么是stkUSDC？

将USDC存入并质押到流动性质押池的USDC持有人，将获得代币化头寸（**stkUSDC**）。stkUSDC在用户质押USDC时铸造，并在用户调用`withdrawStake`时进行烧制。在USDC离开质押人钱包的同一笔交易中，stkUSDC进入质押人钱包；解除质押时，反之亦然。

stkUSDC余额可能是活跃的或不活跃的。活跃的stkUSDC可以作为ERC-20转让，但不能提现。不活跃的stkUSDC可以提现，但不能转让。例如，用户的钱包中有100个活跃和100个不活跃的stkUSDC，用户的余额将显示200个stkUSDC，但如果用户试图转让超过100个stkUSDC，则转让将失败。

质押人在时段结束前要求提现的质押余额将被视为无效，因此不可转让。

## 常见问题解答

### 什么是“停市窗口期”？

停市窗口期是指一段时间，用户不能在此期间请求提现质押的USDC。停市窗口期期间，无法调用 `requestWithdrawal` 函数，该窗口期被配置为一个时段的最后 `3 天`。每28天开始新的时段。换句话说，用户可以在给定时段结束前最多 `3 天`请求提现。

### 我如何从质押资金池提现USDC？需要多长时间？

要想在某时段结束后能够提现 USDC，质押人必须至少在该时段结束前 `3 天`请求解除质押 USDC。如果质押人不请求提现，他们质押的USDC将被转入下一纪元。

如果要提现 USDC，用户请调用`requestWithdrawal`，以请求在下一时段提现USDC。用户资金将持续质押，并且无法在当前时段提现。从下一时段开始，资金将变成“非活跃”，并可用于提现。

在下一时段，用户将调用`withdrawStake`函数，将非活跃USDC提现至特定地址。用户可以选择要提取的非活跃资金金额或调用\`withdrawMaxStake\`函数以提取所有非活跃资金。`withdrawMaxStake` 函数的 gas 效率低于通过 eth\_call 查询最大值和调用 `withdrawStake()`。

如要将USDC解除质押到流动性质押池，按照以下步骤操作：

* 转到[**https://dydx.community/dashboard/staking-pool/liquidity**](https://dydx.community/dashboard/staking-pool/liquidity)\*\*\*\*
* 单击“**请求**”，以打开以下模式：

![请求提现](../.gitbook/assets/1-withdraw-from-liquidity-pool.png)

* 输入您希望请求从资金池中提现的USDC金额，然后单击“**请求提现**”。您需要支付gas费以解除质押USDC。
* 如果质押人在当前时段结束前至少 `3 天`（**停**市窗口期）请求解除质押 USDC，则可以在下一时段开始时提现 USDC。

### 治理可以更改哪些参数？

dYdX治理负责：

* 将 USDC 质押到流动性质押池的每秒奖励
* 将新借款人添加到质押流动性资金池中，和/或从资金池中删除现有借款人
* 更改将借款USDC分配给获批借款人的数额
  * 调用`setBorrowerAllocations`和`setBorrowingRestriction`函数，以更改某些借款人的分配。可以使用它们添加和删除借款人。增加将于下一时段生效，但减少将立即限制借贷。“停市窗口期”期间无法调用这些函数。
* 时段长度和停市窗口期在创建合约时确定，但可以更改
