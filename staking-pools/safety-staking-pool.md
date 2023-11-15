---
description: 保险质押池概述
---

# 保险模块

代币供应量的 `0.5%`（`5,049,079 $ethDYDX）`分配给了把 $ethDYDX 质押到“安全池”以支持系统的用户。 最初，代币供应量的 `2.50%`（`25,000,000 $ethDYDX`）分配给了把 ethDYDX 质押到“安全池”的用户。 从 2022 年 11 月 28 日起，安全模块已不再有效。在 [DIP 17](https://dydx.community/dashboard/proposal/9) 中，dYdX 社区[投票](https://dydx.community/dashboard/proposal/7)将每秒安全模块奖励设置为 0，以便有效逐步关闭安全模块。\


此前，$ethDYDX 分配给了把 $ethDYDX 质押到“安全模块”的用户。安全模块是一个去中心化基金，用于 dYdX 协议破产或其他问题的情况。

“安全模块”中质押的 ethDYDX 保留其提议权和投票权，以及授权能力。

## 概述

目前，在“安全模块”中质押的 $ethDYDX 并未赚取奖励。

先前分配给 $ethDYDX 质押人的 383,562 $ethDYDX 将在"奖励资金库"中积累，并可由 dYdX 社区通过[治理投票](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters)来使用。

## DYDX 取消质押和取款

如果要在时段结束后能够支取 ethDYDX，质押人必须至少在时段结束前 `3 天`**（停市窗口期）**请求支取资金。如果质押人不请求支取，他们质押的 $ethDYDX 则被转入下一时段。

在**停市窗口期**期间，无法请求提现。

在 [DIP 17](https://dydx.community/dashboard/proposal/9) 中，dYdX 社区[投票](https://dydx.community/dashboard/proposal/7)将停市窗口期长度从 `14 天`缩短至 `3 天`。



## 常见问题解答

### 什么是“停市窗口期”？

停市窗口期是指一段时间，用户不能在此期间请求提取 $stkDYDX。停市窗口期期间，无法调用 `请求提款` 函数，该窗口期被配置为一个时段的最后 `3 天`。每28天开始新的时段。换句话说，用户可以在给定时段结束前最多 `3 天`请求提现。

### 我如何从质押资金池提现资金？需要多长时间？

对提现强制执行时段时间表，以便为资金池中资金的可用性提供可预测性和定期节奏。如果要在时段结束后能够提现资金，质押人必须至少在时段结束前 `3 天`请求提现资金。如果质押人不请求支取，他们质押的 $ethDYDX 则被转入下一时段。

如果要支取资金，用户调用`` `requestWithdrawal```函数，请求在下一时段支取资金。用户资金将持续质押，并且无法在当前时段提现。从下一时段开始，资金将变成“非活跃”，并可用于提现。

在下一时段，用户调用```withdrawStake` ``函数，将非活跃资金支取到指定地址。用户可以选择要支取的非活跃资金金额或调用 ```withdrawMaxStake` ``函数来支取所有非活跃资金。请注意，```withdrawMaxStake```函数的 gas 效率低于通过 eth\_call 查询最大值和调用```withdrawStake()```。

要从“安全模块”中支取 $ethDYDX，请按照以下步骤操作：

* 转到[**dydx.community/dashboard/pools/safety**](https://dydx.community/dashboard/pools/safety)\*\*\*\*
* 单击“**请求**”，并输入您希望从资金池中支取的 $ethDYDX 金额。
* 单击“**请求提现**”。您需要支付gas费才能提现资金。
* 如果质押者在当前时段结束的至少 `3 天`前请求支取 $ethDYDX，则可在下一时段开始时支取 $ethDYDX。

