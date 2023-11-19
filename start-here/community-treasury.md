---
description: 社区资金库概述。
---

# 社区资金库

代币供应量的 **`24.2%`**（`241,735,862 $ethDYDX`）分配给 dYdX 社区资金库，供 dYdX 社区持续用于捐赠者赠款、社区举措、流动性采矿，以及其他计划。最初，代币供应量的 `5.0%`（`50,000,000 $ethDYDX`）分配给社区资金库，每个时段 766,703 $ethDYDX 提供给[社区资金库](https://docs.dydx.community/dydx-governance/start-here/dydx-allocations)。 目前，3,787,251 $ethDYDX 提供给社区资金库，因为一些治理提案增加了 dYdX 社区每个时段可用的 $ethDYDX 金额，增至 3,020,548 $ethDYDX ：

* [DIP 14](https://dydx.community/dashboard/proposal/7)：质押 USDC 的奖励设为 0（每个时段 383,562 $ethDYDX），
* [DIP 16](https://dydx.community/dashboard/proposal/8)： 交易奖励削减 25%（每个时段 958,904 $ethDYDX），
* [DIP 17](https://dydx.community/dashboard/proposal/9)： 质押 $DYDX 的奖励设为 0（每个时段 383,562 $ethDYDX），
* [DIP 20](https://dydx.community/dashboard/proposal/11)：交易奖励进一步削减 45%（每个时段 1,294,520 $ethDYDX），以及
* [DIP 24](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-24.md)：将“流动性提供方奖励”削减 50% （每个时段 575,342 $ethDYDX）。



**目标**

* 推动dYdX增长的资金计划和倡议。
* 制定资助计划，为社区NFT、黑客马拉松、分析仪表板、memes、swag、第三方工具、翻译和其他项目提供资金。
* 开发一流的治理体系并激励稳健的治理。

## 概述

社区资金库将保留 $ethDYDX ，由 $ethDYDX 持有人决定使用，可用于赠款、新的流动资金矿池，或其它任何计划。 $ethDYDX 将在五年内连续提供给社区资金库。从社区资金库中支出任何 ethDYDX 都必须进行治理投票。

如果五年后，治理决定执行永续性通货膨胀（最高年度通货膨胀率为`2%`），任何新创的 $ethDYDX 将提供给社区资金库。

## 常见问题解答

### 如何提供 $ethDYDX 给“社区资金库”？

每秒钟，“社区资金库授予方”（在[此处](https://docs.dydx.community/dydx-governance/resources/technical-overview#governance-architecture-overview)查看详细信息）都会提供 [`0.3169242627`](tel:03169242627) $ethDYDX 给“社区资金库”。 一旦 $ethDYDX 授予完成后，在“社区资金库授予方”上调用`申领`函数，即可将已授予的 $ethDYDX 转至“社区资金库”。 dYdX 社区的成员均可在[此处](https://etherscan.io/address/0x08a90Fe0741B7DeF03fB290cc7B273F1855767D8#writeContract)调用 Etherscan 上的`申领`函数（需要一些以太币来支付 gas 费），将已授予的 $ethDYDX 从“社区资金库授予方”转至“社区资金库”。

有关 dYdX 社区对于社区资金库控制的更多详细信息，请参阅 dYdX 基金会的[使用条款](https://dydx.foundation/terms)。

<figure><img src="../.gitbook/assets/claim-function-CT-vester.png" alt=""><figcaption></figcaption></figure>

### 社区资金库的归属结余是多少？

dYdX 社区成员可以在[此处](https://dydx.shippooor.xyz/)查看社区资金库的归属结余。 \
\
此外，在每个时段结束时，dYdX 基金会都会在[时段回顾](https://dydx.foundation/blog)中公布社区资金库的归属结余，仅供参考。除了分配在“社区资金库”中的 $ethDYDX 之外，dYdX 社区还可以通过下列投票获得“奖励资金库”中积累的 ethDYDX：

* [DIP 14](https://dydx.community/dashboard/proposal/7)：质押 USDC 的奖励设为 0（每个时段 383,562 $ethDYDX）。
* [DIP 16](https://dydx.community/dashboard/proposal/8)： 交易奖励削减 25%（每个时段 958,904 $ethDYDX），
* [DIP 17](https://dydx.community/dashboard/proposal/9)： 质押 $ethDYDX 的奖励设为 0（每个时段 383,562 $ethDYDX），
* [DIP 20](https://dydx.community/dashboard/proposal/11)：交易奖励进一步削减 45%（每个时段 1,294,520 $ethDYDX），以及
* [DIP 24](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-24.md)：将“流动性提供方奖励”削减 50% （每个时段 575,342 $ethDYDX）。

从时段 26 开始，每个时段将在“奖励资金库”中积累 3,595,890 $ethDYDX，并可由 dYdX 社区通过[治理投票](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters)来使用。

### 谁可以从“社区资金库”提交使用 ethDYDX 的提案？

任何拥有足够提议权力的用户都可以提交提议。从社区资金库中支出任何 ethDYDX 都必须进行治理投票。如要提交提议，请按照[DIP提议生命周期](../voting-and-governance/dip-proposal-lifecycle.md)中所述，提交dYdX改进提议(DIP)。

### 对于使用社区资金库的资金，您会如何制定提案？

Reverie 已经编制了一份综合性的分步技术指南，讲解拥有超过五百万 $ethDYDX（[短时间锁投票](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-process#short-timelock-executor)的[提案阈值](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters#timelock-parameters)）提案权的 dYdX 社区成员如何制定提案，将 ethDYDX 从“社区资金库”转至目的地地址。单击[此处](https://app.gitbook.com/o/-MeNgGQU0ucT2xo4s8-T/s/-MeNfSkgj48hU0q8Zbjn/\~/changes/EyisuFjLIyJ7K9RzaTfJ/technical-guide-on-building-a-dydx-community-treasury-spending-proposal)查阅技术指南。

### 可以向社区资金库提交哪些类型的提议？

一个由社区管理的资金库打开了充满可能性的世界。我们希望看到各种尝试和方案，包括生态系统赠款，这些可以促进dYdX v3 的生态系统增长。
