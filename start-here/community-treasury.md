---
description: 社区资金库概述。
---

# 社区资金库

**`24.2%`**(`241,735,862 $DYDX`) 的代币供应将分配给社区资金库，由 dYdX 社区通过贡献者赠款、社区倡议、流动性挖掘和其他计划持续进行分配。最初，代币供应量的 `5.0%``` ([50,000,000 $DYDX](https://docs.dydx.community/dydx-governance/start-here/dydx-allocations)) 分配给社区资金库，每个时段，766,703 $DYDX 归属于社区资金库。目前，3,787,251 $DYDX 归属于社区资金库，因为几项治理提案导致 dYdX 社区每个时段的可用 $DYDX 增加 3,020,548 $DYDX：

* [DIP 14](https://dydx.community/dashboard/proposal/7) - 质押 USDC 的奖励设为 0（每个时段 383,562 $DYDX）。
* [DIP 16](https://dydx.community/dashboard/proposal/8) - 交易奖励削减 25%（每个时段 958,904 $DYDX），
* [DIP 17](https://dydx.community/dashboard/proposal/9) - 质押 $DYDX 的奖励设为 0（每个时段 383,562 $DYDX）。
* [DIP 20](https://dydx.community/dashboard/proposal/11) - 交易奖励进一步削减 45%（每个时段 1,294,520 $DYDX），以及
* [DIP 24](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-24.md) - 将流动性提供方奖励削减 50% （每个时段 575,342 $DYDX）。



**目标**

* 推动dYdX增长的资金计划和倡议。
* 制定资助计划，为社区NFT、黑客马拉松、分析仪表板、memes、swag、第三方工具、翻译和其他项目提供资金。
* 开发一流的治理体系并激励稳健的治理。

## 概述

社区资金库将保留 $DYDX，用途由 $DYDX 持有人自行决定，无论是用于拨款、新流动性矿池还是其他计划。五年内，$DYDX 将陆续归属于社区资金库。凡是从社区资金库支出 $DYDX，皆须通过治理投票。

如果五年后，治理决定颁布永续性通货膨胀（最高年度通货膨胀率为 `2%`），则新铸造的 $DYDX 可供社区资金库使用。

## 常见问题解答

### $DYDX 如何归属于社区资金库？

每秒钟，社区资金库归属者（在此处[查](https://docs.dydx.community/dydx-governance/resources/technical-overview#governance-architecture-overview)看详细信息）都会将 [`0.3169242627`](tel:03169242627) 个 $DYDX 归属于社区资金库。 归属了 $DYDX 之后，在社区资金库归属器调用`申领`函数，则将归属的 $DYDX 转移至社区资金库。dYdX 社区的成员均可在此处调用 Etherscan `上的申领`函数（需要一些以太币来支付 gas 费），以便将已归属的 $DYDX 从社区资金库归属者[转移](https://etherscan.io/address/0x08a90Fe0741B7DeF03fB290cc7B273F1855767D8#writeContract)至社区资金库。

<figure><img src="../.gitbook/assets/claim-function-CT-vester.png" alt=""><figcaption></figcaption></figure>

### 社区资金库的归属结余是多少？

dYdX 社区成员可以在[此处](https://dydx.shippooor.xyz/)查看社区资金库的归属结余。 \
\
此外，在每个时段结束时，dYdX 基金会都会在[时段回顾](https://dydx.foundation/blog)中公布社区资金库的归属结余。除了分配在社区资金库中的 $DYDX 之外，dYdX 社区还可以通过下列投票获得奖励资金库中积累的 $DYDX：

* [DIP 14](https://dydx.community/dashboard/proposal/7) - 质押 USDC 的奖励设为 0（每个时段 383,562 $DYDX）。
* [DIP 16](https://dydx.community/dashboard/proposal/8) - 交易奖励削减 25%（每个时段 958,904 $DYDX），
* [DIP 17](https://dydx.community/dashboard/proposal/9) - 质押 $DYDX 的奖励设为 0（每个时段 383,562 $DYDX）。
* [DIP 20](https://dydx.community/dashboard/proposal/11) - 交易奖励进一步削减 45%（每个时段 1,294,520 $DYDX），以及
* [DIP 24](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-24.md) - 将流动性提供方奖励削减 50% （每个时段 575,342 $DYDX）。

从时段 26 开始，每个时段将在奖励资金库中积累 3,595,890 $DYDX，并可由 dYdX 社区通过[治理投票](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters)来使用。

### 谁可以提交社区资金库 $DYDX 代币的支出提案？

任何拥有足够提议权力的用户都可以提交提议。凡是从社区资金库支出 $DYDX，皆须通过治理投票。如要提交提议，请按照[DIP提议生命周期](../voting-and-governance/dip-proposal-lifecycle.md)中所述，提交dYdX改进提议(DIP)。

### 对于使用社区资金库的资金，您会如何制定提案？

Reverie 已经编制了一份综合性的分步技术指南，讲解拥有超过 5 百万 $DYDX（[短时间锁投票](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-process#short-timelock-executor)[的提案阈值](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters#timelock-parameters)）提案权的 dYdX 社区成员如何制定提案，将 $DYDX 从社区资金库转移到目的地地址。单击[此处](https://app.gitbook.com/o/-MeNgGQU0ucT2xo4s8-T/s/-MeNfSkgj48hU0q8Zbjn/\~/changes/EyisuFjLIyJ7K9RzaTfJ/technical-guide-on-building-a-dydx-community-treasury-spending-proposal)查阅技术指南。

### 可以向社区资金库提交哪些类型的提议？

一个由社区管理的资金库打开了充满可能性的世界。我们希望看到各种尝试和方案，包括生态系统补偿金，这些可以促进dYdX Layer 2协议的生态系统增长。
