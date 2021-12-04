---
description: 流动性质押池概述。

---

# 流动性质押池

2.5%\（`25,000,000个DYDX`\）将分配给将USDC质押到流动性质押池的用户。

### 目标

* Bootstrap dYdX流动性网络效应

## 概述

流动性，尤其在正确使用时，是任何成功交易所的核心成分。为进一步提高流动性网络效应，激励专业做市商，DYDX将被分配给向流动性质押池质押USDC的用户。公认的和获批准的做市商将使用质押的USDC基于协议进行做市，从而进一步提高市场的可用流动性。做市商将无法从协议中提现USDC，要求他们只能在协议中使用。但是，如果做市商将要\（通过无盈利的交易\）损失资金，并且无法补充流动性质押池，那么一部分质押的USDC可能会亏掉。质押人将收到DYDX，其将根据每个质押者在池中总USDC中所占的份额进行连续分配。要在时段结束后能够提现USDC，质押人必须至少在时段前`14天`**（停市窗口期）**请求解除质押USDC。如果质押人不请求提现，他们质押的USDC将被转入下一纪元。

## 批准的借款人

流动性质押池合约是一种双侧、质押不足的贷款系统。

可以提现的金额取决于借款人分配比例和质押资金池中质押的可用资金总量。分配百分比和可用资金总额可以根据`LS1EpochSchedule`指定的预定义时间进行变更。借款资金只能用于dYdX Layer 2交易所。此项合约通过 `TrustedBorwerL2Proxy`合约强制执行，该合约与L2交易所合约\（`StarkPerpetual`\）互动。

初始获批准的流动性提供方包括`Wintermute`、`Sixtant`、`Kronos`、`Amber`和`MGNR`，自推出以来，他们一直在协议上积极做市。

| 事先批准的借款人 | 初始分配百分比 | 流动性提供方的详细信息 |
| :--- | :--- | :--- |
| Wintermute | `X%`待定 | [https://dydx.exchange/blog/ama-recap-wintermute](https://dydx.exchange/blog/ama-recap-wintermute) |
| Sixtant | Y%待定 | [https://dydx.exchange/blog/ama-recap-sixtant](https://dydx.exchange/blog/ama-recap-sixtant) |
| Kronos \(Wootrade\) | Z%待定 | [https://dydx.exchange/blog/ama-recap-wootrade](https://dydx.exchange/blog/ama-recap-wootrade) |
| Amber | Z%待定 |  |
| MGNR | Z%待定 |  |

当用户请求解除质押资金时，借款人下一时段的分配余额可能会低于其当前借款金额。在这种情况下，借款人负责在时段结束前偿还借款和分配余额之间的差额。如果借款人借款余额在下时段开始时超过其分配，那么预计并相信他们会在该时段开始前偿还差额。

随着借款人借款和偿还资金，他们的借款净余额将被记录在案。所有借款人借款净余额总额也会被追踪。合约持有的余额称为未借贷余额。

在考虑整个合同时，以下等式始终成立：

总活跃数 + 总非活跃数 = 借款总额 + 未借款总额

### 治理

dYdX治理负责：

* 对现有借款人进行尽职调查
* 向质押资金池添加新借款人
* 更改将借款资金分配给获批借款人的数额
   * 调用setBorrowerAllocations和setBorrowingRestriction函数，以更改某些借款人的分配。可以使用它们添加和删除借款人。增加于下一时段生效，但减少将立即限制借贷。“停市窗口期”期间无法调用这些函数。
* 时段长度和停市窗口期在创建合约时被确定，但可以由dYdX治理进行更改

### 质押余额会计处理

质押余额处于两种状态之一：

* 活跃：可以用于借款；赚取质押奖励；质押人不能提现。
* 非活跃：借款不可用；不赚取奖励；可以由质押人提现。

质押人可能具有活跃和非活跃余额的组合。资金按时段进行计算，如以下例子所示：

以下操作会影响质押余额，如下所示：

* 存款：增加活跃余额。
* 请求提现：在本时段结束时，将一些活跃资金移至非活跃状态。
* 提现：减少非活跃余额。
* 转让：将一些活跃资金转移给另一个质押人。

如果要加密一个交易时间段结束时可能计划变更余额的事实，我们将每个余额将作为三个字段的结构进行存储：currentEpoch、currentEpochBalance和nextEpochBalance。非活跃用户余额也利用shortfallCounter字段。

## 常见问题解答

### 我如何赚取质押奖励？

质押人可以随时将USDC存入流动性质押池，并立即开始赚取奖励。根据每个质押人在总资金池中的份额，不断赚取DYDX奖励。可以随时申领奖励并提现。

### 我如何存入USDC并质押到流动性质押池？

如果要存入和质押资金，用户请调用\`stake\'[函数](https://github.com/dydxprotocol/governance-private/blob/2645927b44f517f51c84e35a00a1ee810300c13f/contracts/liquidity/v1/impl/LS1Staking.sol#L59)。用户也可以调用\`stakeFor\'[函数](https://github.com/dydxprotocol/governance-private/blob/2645927b44f517f51c84e35a00a1ee810300c13f/contracts/liquidity/v1/impl/LS1Staking.sol#L64)，代表另一地址进行存入和质押。

如要将USDC质押到流动性质押池，按照以下步骤操作：

* 单击“质押”
* 首次存入时，您必须启用USDC。您仅须执行此操作一次。
* 输入您希望质押到资金池的USDC数量
* 单击“质押资金”——您需要支付质押资金和解除质押资金的gas费用

![](https://lh4.googleusercontent.com/caSDz783Gi-asRNYP8Gm8L5qv_yAuJZwEmUAfl8I1MfHecIF2In10IQCqZBCIpxeXl90eT28GGLbZyts8-x9U5w4Y6LBC4kyehMEalsZu_-aI11S6V7nwPrwtcc75m2M8847jFvv)

质押资金已经活跃，并立即开始赚取奖励。

### 奖励会计处理

在保持活跃的时期内，活跃资金会赚取奖励。这意味着，在请求提现部分资金后，这些资金将继续赚取奖励，直至时段结束。例如：

在上述情景中，用户将从t\_0至t\_2之间赚取奖励，随着该期间质押余额总数的变化而变化。如果用户仅请求提现部分余额，那么剩余的余额将在t\_2之后继续赚取奖励。

### 什么是“停市窗口期”？

停市窗口期是指一段时间，用户不能在此期间请求提现质押的资金。`requestWithdrawal`函数无法在停市窗口期间调用，停市窗口期最初配置为一个时段的最后14天。每28天开始新的时段。换句话说，用户可以在给定的时段结束前最多7天内请求提现。

### 我如何从质押资金池提现资金？需要多长时间？

对提现强制执行时段时间表，以便为质押资金池中资金的可用性提供可预测性和定期节奏。如果要在时段结束后能够提现资金，质押人必须至少在时段结束前14天请求解除质押资金。如果质押人不请求提现，他们质押的USDC将被转入下一时段

如果要提现资金，用户请调用\`requestWithdrawal\`[函数](https://github.com/dydxprotocol/governance-private/blob/master/contracts/liquidity/v1/impl/LS1Staking.sol#L73-L83)，以请求在下一时段提现资金。用户资金将持续质押，并且无法在当前时段提现。从下一时段开始，资金将变成“非活跃”，并可用于提现。

在下一时段，用户调用[\`withdrawStake\`](https://github.com/dydxprotocol/governance-private/blob/master/contracts/liquidity/v1/impl/LS1Staking.sol#L91)函数，将非活跃资金提现到指定地址。用户可以选择要提取的非活跃资金金额或调用`withdrawMaxStake`函数以提取所有非活跃资金。`\withdrawMaxStake\`函数的gas效率低于通过 eth\_call查询最大值和调用\`withdrawStake\(\)\`。

### 质押到流动性质押池的风险是什么？如果借款人未能偿还债务，会发生什么？

非质押贷款的质押标准要高得多，借款人必须达到该标准。流动性提供方不能从协议中提现质押的USDC，要求他们只在协议中使用。但是，如果流动性提供方将失去资金交易，并且无法通过外部资金来源补充其借贷的分配，那么质押的USDC可能会亏损。

在这种情况下，如果借款人迟迟未偿还请求提现的资金，那么不活跃资金可能会因出现资金缺口而受到按比例计算的社会化损失。如果无质押贷款出现违约，则逾期的借款人将面临严重的声誉损害。

合约偿债能力：

在任何时候，合约将根据质押余额和借款余额之间的关系处于以下其中一种状态：

| ![](https://lh3.googleusercontent.com/nTJuAC4WSmhOiAGkM6r-YWzy6z2MIHQnydr8U0n-TReAh_gfqD6ZyalxQpYv9RNBsJzrlw78QB_wp9utqBc-PQZipwzWpxDifD1_zEtyVBhYXRl_f8V-iDMwLBO70LQsftDlXrsr) | ![](https://lh3.googleusercontent.com/x_Yev8ZJrYYm8FTDSdoj0jDXEBY_b9xOC69lpQudQdoALQ_tuQFEbFc5hAU6TbpGNCB6J2BsjMwHb59GrCqR52747j45jSC_BmyzyiY72gTRk4oamv35gO8PPZalA43COZF1pgtP) |
| :--- | :--- |
| ![](https://lh6.googleusercontent.com/wX37DQoW9oR4OhJzb4hc5ZxPE1X05OPfyETbUv7WTY0b__WH2PydjJoBuQIREHgeWL18GDn7E1ORgGmcre0R6iYPmwSsdFNzBZ7DBPs0wkajjoDBjxDYDPHcet_-dPPAyS1GWL0v) |  |

在以下情况下，合约无法偿债：

* 借款余额总额超过总活跃余额
* 同等地：总非活跃余额超过了未借贷余额总数
* 同等地：可提现余额总额超过合约的USDC余额

否则，合约被认为是可以偿债。

因为借款受限于借款人分配的活跃资金比例，并且由于非活跃余额只能在不同时段之间增加（除了“裸”USDC转移到合约的情况），合约通常只能在不同时段之间的过渡期间从可以偿债进入无法偿债状态。

在个人借款人自己的分配余额低于其未清借款余额之前，始终会有至少有一个星期的通知。只有在时段之间，才能发生这样的过渡。

当合约无法偿债时，用户可能无法提现他们所欠的所有资金。此外，如果对资金缺口是否将得到解决以及多快的速度存在任何不确定性，那么这种情况就会带来额外风险：

1. 用户可能会不愿意质押额外资金，因为这样可能会使他们处于无法回收资金的境地。
2. 当前质押的用户可能会不愿意“退出去”并尽快提现，以最大限度地提高他们资金回笼机会。

亏损通过指数来跟踪，指数代表特定资金缺口事件期间转换为债务的非活跃资金的比例。每个质押人的非活跃余额都存储一个缓存的资金短缺计数器，表示与上次更新余额的时间相比，过去发生的资金缺口数量。非活跃余额产生的任何损失都将变成质押人债务余额的平等信贷。如需了解有关指数计算方式的更多信息，请查阅LS1DebtAccounting。

如果合约资不抵债，markDebt\(\)函数可能会被\（任何人\）调用，目标是超过其分配的借款人。他们借款余额超过分配余额的数额被称为他们的债务余额。债务余额从借款余额中挪出，并转入专门用于计算未缴资金缺口债务的特别余额。

对质押资金的会计处理进行同样的调整。相当于债务数额的数额从非活跃余额中删除，并添加到对质押人欠款的特别余额核算中。每个质押人不活跃余额将进行折扣，他们将以债务形式收到相应的金额。这样，无法偿债导致的损失将在所有持有非活跃余额的质押人中社会化\（按比例\）。

该过程如下所示：

![](https://lh5.googleusercontent.com/2b2e67wVF3DL32NU0ykTVV0PJWaJ_bdmRQRKgx-5c3_qr_nWNYsuE77JviLtbBxXzASEfIp2Fw4hvzRPeM1a7TAIxq0NYUfo3dZLUhChilDpa5Ygq-YugSvNXKmyf2ul3GQM22SZ)

如果负债的借款人偿还债务\（或者如果另一方，例如治理，代表其偿还债务\），那么欠债的质押人可以按照先到先得的原则收回资金。

### 债务代表什么？

债务

### 如果借款人违约，质押人是否有任何追索权？

当对借款人调用MarkDebt\(\)时，借款人失去从合约中借贷任何更多资金的权利。该权利可以通过治理恢复。

可能在与基金会的做市商协议中添加内容

