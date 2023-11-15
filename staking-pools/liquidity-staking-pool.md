---
description: 流动性质押池概述
---

# 流动性模块

代币供应量的 `0.6%` (`5,753,430 $ethDYDX)` 分配给将 $USDC 质押到流动性质押池的用户。最初，代币供应量的 `2.50%`（`25,000,000 $ethDYDX`）分配给把 $USDC 质押到“流动质押池”的用户。 流动性质押池自 2022 年 9 月 29 日起不再运行。在 [DIP 14](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-14.md) 中，dYdX 社区[投票](https://dydx.community/dashboard/proposal/7)决定将每秒“流动性质押池”奖励设置为 0，以便有效逐步终止“流动性质押池”和“借款池”。\
\此前，$ethDYDX 分配给将 $USDC 质押到“流动性质押池”的用户。社区批准的流动性提供方使用质押的 $USDC 在 dYdX v3 上做市，从而进一步提高市场间的流动性。流动提供方不可使用 dYdX v3 之外的借款资金。

## **质押**概述

目前，在流动性质押池中质押的 $USDC 不会获得奖励。

先前分配给 USDC 质押人的 383,562 $ethDYDX 将在奖励资金库中积累，并可由 dYdX 社区通过[治理投票](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters)来使用。

## USDC解除质押和提现

质押人必须在[时段](../start-here/epochs.md)结束前至少 `****3 天`（**停市窗口期**）请求提取 $USDC，才能在该时段结束后提取质押人的 $USDC。如果质押人不请求提现，则其质押的 $USDC 将转入下一时段。

在**停市窗口期**期间无法请求提现。

在 [DIP 14](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-14.md) 中，dYdX 社区 [投票](https://dydx.community/dashboard/proposal/7) 决定将停市窗口期从 `14 天`减少至 `3 天`。

## 什么是stkUSDC？

将 $USDC 存入并质押到“流动性质押池”的 USDC 持有人，将获得代币化头寸（$**stkUSDC**）。用户质押 $USDC 时铸造 $stkUSDC，用户调用`“撤回质押”`时则销毁。在 $USDC 离开质押人钱包的同一笔交易中，$stkUSDC 进入质押人钱包；解除质押时，反之亦然。

$stkUSDC 余额既可是活跃的，也可是不活跃的。活跃的 $stkUSDC 可以当作 ERC-20 转让，但不能提现。不活跃的 $stkUSDC 可以提现，但不能转让。例如，用户的钱包中有 100 个活跃和 100 个不活跃的 $stkUSDC，用户的余额会显示 200 个 $stkUSDC，但如果用户试图转账超过 100 个 $stkUSDC，则会转账失败。

质押人在时段结束前要求提现的质押余额将被视为无效，因此不可转让。

## 常见问题解答

### 停市窗口期是什么？

停市窗口期是指一段时间，在此期间，用户不能请求提取质押的 $USDC。停市窗口期期间，无法调用 `请求提款` 函数，该窗口期被配置为一个时段的最后 `3 天`。每28天开始新的时段。换句话说，用户可以在给定时段结束前最多 `3 天`请求提现。

### 我如何从质押池提取 $USDC？需要多长时间？

质押人必须在某一时段结束前至少 `3 天`请求解除 $USDC 质押，才能在该时段结束之后提取质押人的 $USDC。如果质押人不请求提现，则其质押的 $USDC 将转入下一时段。

如要提取 $USDC，用户调用 `请求提款`，以请求在下一时段提取 $USDC。用户资金将持续质押，并且无法在当前时段提现。从下一时段开始，资金将变成“非活跃”，并可用于提现。

在下一时段，用户调用 `撤回质押` 函数，将不活跃的 $USDC 提取到特定地址。用户可以选择要提取的非活跃资金金额或调用`撤回最大股权`函数以提取所有非活跃资金。`撤回最大股权` 函数的瓦斯效率低于通过eth\_call 查询最大值和调用 `撤回质押()`。

要在流动性质押池中解除 $USDC 质押，按照以下步骤操作：

* 转到[**https://dydx.community/dashboard/staking-pool/liquidity**](https://dydx.community/dashboard/staking-pool/liquidity)\*\*\*\*
* 单击“**请求**”，以打开以下模式：

![请求提现](../.gitbook/assets/1-withdraw-from-liquidity-pool.png)

* 输入您希望从资金池中支取的 $USDC 金额，然后单击“**请求支取**”。您需要支付 gas 费来解除质押 $USDC。
* 如果质押人在当前时段结束前至少 `3 天`（**停市窗口期**）请求解除质押 $USDC，则可以在下一时段开始时支取 $USDC。

### 治理可以更改哪些参数？

dYdX治理负责：

* 将 $USDC 质押到“流动性质押池”的每秒奖励
* 将新借款人添加到质押流动性资金池中，和/或从资金池中删除现有借款人
* 更改将借款 $USDC 分配给获批借款人的数额
  * 调用`setBorrowerAllocations`和`setBorrowingRestriction`函数，以更改某些借款人的分配。可以使用它们添加和删除借款人。增加将于下一时段生效，但减少将立即限制借贷。“停市窗口期”期间无法调用这些函数。
* 时段长度和停市窗口期在创建合约时确定，但可以更改
