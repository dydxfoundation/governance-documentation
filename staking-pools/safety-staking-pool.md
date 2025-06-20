---
description: 保险质押池概述
hidden: true
---

# 🔐 安全模块

从 2022 年 11 月 28 日起，安全模块已不再有效。在 [DIP 17](https://dydx.community/dashboard/proposal/9) 中，dYdX社区[投票](https://dydx.community/dashboard/proposal/7)决定，通过将安全模块每秒奖励设置为 0，有效地关闭安全模块。

流动性模块奖励分配中所有剩余的ethDYDX已迁移到dYdX链社区资金库。

有关dYdX链社区资金库的更多信息，请参阅[此处](https://app.gitbook.com/s/7eKRye9zrZIr1Pp3Q3Mu/modules/community-treasury)。



## DYDX取消质押和提现

要在时段结束后支取ethDYDX，质押人必须在时段结束前至少`3天`**（停市窗口期）**申请支取资金。如质押人未申请支取，其质押的$ethDYDX将转入下一时段。

在**停市窗口期**期间，无法请求提现。

在 [DIP 17](https://dydx.community/dashboard/proposal/9) 中，dYdX社区[投票](https://dydx.community/dashboard/proposal/7)决定，将停市窗口期时长从`14天`缩短至`3天`。

## 常见问题解答

<details>

<summary>什么是“停市窗口期”？</summary>

停市窗口期是指一段时间，用户不能在此期间请求提取 $stkDYDX。停市窗口期期间，无法调用 `请求提款` 函数，该窗口期被配置为一个时段的最后 `3 天`。每28天开始一个新的时段。换句话说，用户可以在给定时段结束前最多 `3 天`请求提现。

</details>

<details>

<summary>我如何从质押资金池提现资金？需要多长时间？</summary>

对提现强制执行时段时间表，以确保能预测资金池资金情况，并保持节奏规律。如要在时段结束后提现，质押人必须在时段结束前至少`3天`申请资金提现。如质押人未申请支取，其质押的$ethDYDX将转入下一时段。

如果要支取资金，用户调用`` `requestWithdrawal```函数，请求在下一时段支取资金。用户资金将持续质押，并且无法在当前时段提现。从下一时段开始，资金将变成“非活跃”，并可用于提现。

在下一时段，用户可调用```withdrawStake` ``函数，将非活跃资金支取到指定地址。用户可以选择要支取的非活跃资金金额或调用 ```withdrawMaxStake` ``函数来支取所有非活跃资金。请注意，```withdrawMaxStake```函数的gas效率低于通过 eth\_call查询最大值和调用```withdrawStake()```。

要从“安全模块”中支取$ethDYDX，请按照以下步骤操作：

* 转到[**dydx.community/dashboard/pools/safety**](https://dydx.community/dashboard/pools/safety)\*\*\*\*
* 单击“**请求**”，并输入您希望从资金池中支取的 $ethDYDX 金额。
* 单击“**请求提现**”。您需要支付gas费才能提现资金。
* 如质押者在当前时段结束的至少 `3天`前申请支取$ethDYDX，则可在下一时段开始时支取$ethDYDX。

</details>

