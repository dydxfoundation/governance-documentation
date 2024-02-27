---
description: 社区资金库概述。
---

# 社区资金库

**`26.1%`** (`261,133,225 $ethDYDX`) 的代币供应分配给社区金库，供 dYdX 社区持续用于贡献者赠款、社区计划、流动性挖掘和其他计划。最初，`5.0%`（`50,000,000 $ethDYDX`）的代币供应[分配](https://docs.dydx.community/dydx-governance/start-here/dydx-allocations)给社区资金库，每个时段有 766,703 个 $ethDYDX 提供给社区资金库。 目前，3,787,251 $ethDYDX 提供给社区资金库，因为一些治理提案增加了 dYdX 社区每个时段可用的 $ethDYDX 金额，增至 3,020,548 $ethDYDX ：

* [DIP 14](https://dydx.community/dashboard/proposal/7)：质押 USDC 的奖励设为 0（每个时段 383,562 $ethDYDX），
* [DIP 16](https://dydx.community/dashboard/proposal/8)： 交易奖励削减 25%（每个时段 958,904 $ethDYDX），
* [DIP 17](https://dydx.community/dashboard/proposal/9)： 质押 $DYDX 的奖励设为 0（每个时段 383,562 $ethDYDX），
* [DIP 20](https://dydx.community/dashboard/proposal/11)：交易奖励进一步削减 45%（每个时段 1,294,520 $ethDYDX），以及
* [DIP 24](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-24.md)：将“流动性提供方奖励”削减 50% （每个时段 575,342 $ethDYDX）。
*   [DIP 29](https://dydx.community/dashboard/proposal/16)：将 dYdX v3 上时段 30-32 的流动性提供者奖励减少 ⅓，减为以下值：

    * 时段 30：383,562 $ethDYDX
    * 时段 31：191,781 $ethDYDX
    * 时段 32：0 $ethDYDX

    在时段 31 之后，dYdX v3 上将没有任何流动性提供者奖励。 在 DIP 29 中，dYdX 社区投票决定将 dYdX v3 上时段 30-32 的交易奖励减少 ⅓，然而剩余的交易奖励分配已被迁移到 dYdX Chain 作为交易奖励。

在 2023 年 11 月 18 日，dYdX 社区[投票](https://dydx.community/dashboard/proposal/16)决定将在以太坊上积累的社区资金库中的 ethDYDX 余额桥接到 dYdX Chain 上。桥接后，DYDX 可以由 dYdX 社区在 dYdX Chain 上进行治理投票后使用。



**目标**

* 推动dYdX增长的资金计划和倡议。
* 制定资助计划，为社区NFT、黑客马拉松、分析仪表板、memes、swag、第三方工具、翻译和其他项目提供资金。
* 开发一流的治理体系并激励稳健的治理。

## 概述

社区资金库将保留 $ethDYDX ，由 $ethDYDX 持有人决定使用，可用于赠款、新的流动资金矿池，或其它任何计划。 $ethDYDX 将在五年内连续提供给社区资金库。从社区资金库中支出任何 ethDYDX 都必须进行治理投票。

如果五年后，治理决定执行永续性通货膨胀（最高年度通货膨胀率为`2%`），任何新创的 $ethDYDX 将提供给社区资金库。

## 常见问题解答

### 如何提供 $ethDYDX 给“社区资金库”？

此前，社区资金库归属者（在 [此处](https://docs.dydx.community/dydx-governance/resources/technical-overview#governance-architecture-overview)查看详细信息）每秒钟都会将 [`0.3169242627`](tel:03169242627) 个 $ethDYDX 归属于社区资金库。 一旦 $ethDYDX 归属完成后，在“社区资金库归属者”上调用 `申领` 函数，即可将已归属的 $ethDYDX 转至“社区资金库”。 dYdX 社区的成员均可在 [此处](https://etherscan.io/address/0x08a90Fe0741B7DeF03fB290cc7B273F1855767D8#writeContract) 调用 Etherscan 上的 `申领` 函数（需要一些以太币来支付 gas 费），将已归属的 $ethDYDX 从“社区资金库归属者”转至“社区资金库”。

有关 dYdX 社区对于社区资金库控制的更多详细信息，请参阅 dYdX 基金会的[使用条款](https://dydx.foundation/terms)。

<figure><img src="../.gitbook/assets/claim-function-CT-vester.png" alt=""><figcaption></figcaption></figure>

###

###

