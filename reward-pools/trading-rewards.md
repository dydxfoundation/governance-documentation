---
description: 用户交易奖励计划概述。

---

# 交易奖励

25% \（`250,000,000个DYDX`\）将根据支付的费率与未平仓合约的组合分配给根据协议进行交易的用户。

**目标**

* 激励所有交易者使用dYdX Layer 2永续合约
* 加快市场流动性以及产品的总体使用情况

## **概述**

![](../.gitbook/assets/image%20%283%29.png)

DYDX将根据一条公式分配给交易者，该公式奖励在dYdX Layer 2协议上支付的交易费用和未平仓量的组合。DYDX将在五年内以28天时段为周期进行分配，不受任何兑现或锁定的限制。每个纪元内将分配3,835,616个DYDX。

Cobb-Douglas函数用来计算每个时段内给予每个交易者的DYDX数量：

$$
w\ =\ \left(\frac{f}{F}\right)^{\alpha } \times \ \left(\frac{d}{D}\right)^{1-\alpha }
$$

$$
r=R\times \frac{w}{\sum\limits _{n} w_{n}} \ \ ,n=1,2...k
$$

| 术语 | 定义 |
| :--- | :--- |
| r | 特定交易者的奖励。 |
| R | 将在该时段中资金池中所有交易者之间分配的总奖励。 |
| f | 本时段交易者支付的总费用。 |
| 周 | 个人交易者分数。 |
| $${\sum\limits &lt;g id="1" ctype="italic" equiv-text="_"&gt;{n} w</g>{n}}$$ | 所有交易者分数的总和。 |
| F | 本时段内所有交易者支付的总费用。 |
| 日 | 本时段内一个交易者对所有交易对的总加权未平仓合约\（每小时测量\）。 |
| 日 | 本时段所有市场的总加权未平仓合约\（每小时测量\）。 |
| k | 本时段的交易者总数。 |
| α | 确定费率权重与未平仓合约对比的范围中的常量。开始时，α=0.7。 |

以下例子说明了交易者A、B和C使用上面列出的公式所赚取的交易奖励：

![](https://lh4.googleusercontent.com/LWYcMg6ImkQCV1aVsS2jVwjcFfTmBG4u7JZHrnf4l4MmHcxCZlu_af57UaSgHhr6TYi9thIyr8794SECk6_E8Vn4sR2QJFniUSbQGhIZZrkvTf0QRHmzzvt6awR9N8kxHhCooRp4)

## 常见问题解答

### 谁有资格获得交易奖励？

dYdX Layer 2永续合约的所有交易者都有资格获得DYDX作为交易奖励。

如dYdX的[使用条件](https://dydx.exchange/terms)所定义，该产品不提供给美国或受限制地区的交易者。

### 我在交易奖励计划中赚取了多少DYDX？

在特定时段，用户可以在此处查阅支付的费用、平均未平仓合约和估计的交易奖励。

### 我如何申领我的交易奖励？何时可以提现并转让我赚取的DYDX？

通过交易奖励赚取的DYDX代币将在每个时段结束时可以转让。DYDX代币持有人必须在时段结束后等待大约`7天`\（**等待期**\）才能申领代币。在申领代币之后，可以使用代币或委托给dYdX治理。

交易者可以在[此处](https://dydx.community/dashboard)在每个时段结束时申领他们的交易奖励。

用户需要单击“申领”，签署交易，并支付Gas费用以申领DYDX。

![](../.gitbook/assets/image%20%284%29.png)

### 什么是未平仓合约？

未平仓合约是资产尚未结算的未平仓永续合约总数。未平仓合约等于买卖合约的总数，而不是两者合在一起。持仓量增加表示新的或额外的资金进入市场，而持仓量减少表示资金流出市场。

下表是交易者A、B、C、D和E的期权市场交易活动表。未平仓合约按照每天的交易活动以USDC计算：

| 时间 | 交易活动 | 未平仓合约\(USDC\) |
| :--- | :--- | :--- |
| 7月1日 | **交易者A**以30,000美元的价格购买1个BTC，**交易者B**以30,000美元卖出1个BTC | 30,000美元 |
| 7月3日 | **交易者C**以30,000美元的价格购买5个BTC，**交易者D**以30,000美元卖出5个BTC | 180,000美元 |
| 7月5日 | **交易者A**以30,000美元的价格卖出1个BTC，**交易者D**以30,000美元的价格买入1个BTC | 150,000美元 |
| 7月10日 | **交易者E**以30,000美元的价格买入5个BTC，**交易者C**以30,000美元卖出5个BTC | 150,000美元 |

在交易奖励公式中，所有市场的未平仓合约每小时进行测量，并使用特定时段的加权平均数来计算奖励。

### dYdX的费率表是什么？

dYdX使用挂单-吃单费模型来确定其交易费用。dYdX上有两种类型的订单，即挂单订单和吃单订单。

* 挂单订单是不会立即全部成交且停留在订单簿上的订单-这些订单增加了订单簿的深度和流动性。
* 另一方面，吃单订单会立即将现有挂单订单交叉。它们会从订单簿中移除流动性。

做市商和市场接收者费用使用30天的成交量加权费用表来确定。如需标准费率表，请在[此处](https://help.dydx.exchange/en/articles/4798040-perpetual-trade-fees)查阅。DYDX持有人根据DYDX的当前持有量可以获得[交易费率折扣](trading-rewards.md)。
