---
description: 流动性质押池概述
---

# 🔋 流动🔋模块

流动性质押池自 2022 年 9 月 29 日起不再运行。在 [DIP 14](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-14.md) 中，dYdX社区[投票](https://dydx.community/dashboard/proposal/7)决定，通过将流动性质押池的每秒奖励设定为 0，有效地停用流动性质押池和借款池。

流动idity 模块奖励分配中剩余的所有 ethDYDX 都将迁移到 dYdX 链社区资金库。

有关dYdX链社区资金库的更多信息，请参阅[此处](https://app.gitbook.com/s/7eKRye9zrZIr1Pp3Q3Mu/modules-and-parameters/community-treasury)。

## **质押**概述

目前，在流动性质押池中质押的 $USDC 不会获得奖励。

## USDC解除质押和提现

质押人必须在[时段](../start-here/epochs.md)结束前至少 `****3 天`（**停市窗口期**）请求提取 $USDC，才能在该时段结束后提取质押人的 $USDC。如果质押人不请求提现，则其质押的 $USDC 将转入下一时段。

在**停市窗口期**期间，无法请求提现。

## 常见问题解答

<details>

<summary>停市窗口期是什么？</summary>

停市窗口期是指用户无法申请将质押$USDC提现的一段时间。停市窗口期期间，无法调用 `请求提款` 函数，该窗口期被配置为一个时段的最后 `3 天`。每28天开始一个新的时段。换句话说，用户可以在给定时段结束前至少 `3 天`申请下个时段的提现。

</details>

<details>

<summary>我如何从质押池提现$USDC？需要多长时间？</summary>

质押人必须在某一时段结束前至少`3 天`请求解除$USDC质押，才能在该时段结束之后提取质押人的$USDC。如果质押人不请求提现，则其质押的 $USDC 将转入下一时段。

如要提取$USDC，用户需调用 `requestWithdrawal`功能，以申请在下一时段提现$USDC。用户资金将持续质押，并且无法在当前时段提现。从下一时段开始，资金将变成“非活跃”，并可用于提现。

在下一时段，用户调用 `撤回质押` 函数，将不活跃的 $USDC 提取到特定地址。用户可以选择要提取的非活跃资金金额或调用`撤回最大股权`函数以提取所有非活跃资金。`撤回最大股权` 函数的瓦斯效率低于通过eth\_call 查询最大值和调用 `撤回质押()`。

要在流动性质押池中解除 $USDC 质押，按照以下步骤操作：

* 转到[**https://dydx.community/dashboard/staking-pool/liquidity**](https://dydx.community/dashboard/staking-pool/liquidity)\*\*\*\*
* 单击“**请求**”(Request)
* 输入您希望从资金池中支取的$USDC金额，然后单击“**请求支取**”(Request withdraw)。您需要支付gas费来解除质押$USDC。
* 如果质押人在当前时段结束前至少 `3 天`（**停市窗口期**）请求解除质押$USDC，则可以在下一时段开始时支取$USDC。

</details>

###
