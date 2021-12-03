---
description: 流动性提供方奖励概览。

---

# 流动性提供方奖励

7.5%\（`75,000,000个DYDX`\）根据一条公式向流动性提供方分配，按照正常运行时间、双侧深度、买卖差额和所支持交易对数量的组合进行奖励。

**目标**

* 改善双侧流动性并以程序化方式奖励流动性提供方

## **概述**

为了激励交易对流动性，DYDX将根据一条公式分配给流动性提供方，该公式奖励对dYdX Layer 2协议的参与做市、双侧深度、价差\（与中间相比\）和正常运行时间。任何以太坊地址都可以赚取这些奖励，但条件是挂单量起点最低为前一纪元挂单量的5%。DYDX将在五年内以28天时段为周期进行分配，不受任何兑现或锁定的限制。每个纪元内将分配1,150,685个DYDX。

以下函数用于计算每个时段每个流动性提供方应当得到多少DYDX奖励。获得的DYDX金额由每个参与者的$$Q_{FINAL}$$的相对份额决定：

![](https://lh6.googleusercontent.com/0cDsOz823Q4TxMJmBn1qqh9M0caQfYuRr6tqgdTfadGWsSn-h6mQd4xkoLsBVIXuSi767ruq17xnGZaneymMZDY6O-5r1pbJT0ozMgYBZ8hj0fdNwZBGPijWXOdCEzYf49QJkEYr)

每个交易对低于特**定最低深**度\（大小\）\($$MinSize$$\)的订单会被排除，超过特**定最大价**差\（中间交易对价差\）\($$MaxSpread$$\)交易对的订单也会被排除。

流动性提供方的表现按分钟进行监测和计算，\（使用随机抽样\），并就特定交易对将汇总为 $$Q_{SCORE}$$ \($$Q_{FINAL}$$\)。鉴于逐分钟的抽样，每个时段都有28天\*24小时\*60分钟的数据点——每个时段总共40,320个数据点。

流动性提供方根据其相对的$$Q_{FINAL}$$赚取每月奖励。

上述公式分为下面的逐步计算，详情如下：

<table>
  <thead>
    <tr>
      <th style="text-align:left">术语（按计算顺序）</th>
      <th style="text-align:left">定义</th>
      <th style="text-align:left">说明/示例</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p></p>
        <p>
          <img src="https://lh6.googleusercontent.com/XsZKdkJn9NkEP2Mso2HmGmCjzAOihckJ9MwSBQlHGO8eaMFPYpmNTXb6XNkmWKIfACtryaum41hdn-sPOukO1OJbEWIaDA3xyeNow48NNic_GoC5IIe4MGdLM0LN6InhAYrkxfbz" alt />
        </p>
      </td>
      <td style="text-align:left">
        <p>假设流动性提供方有多个公开出价订单（0.1 BTC为29,900美元，          5 BTC，29,800美元，10 BTC，29,500美元），基于BTC-USD 订单簿和BTC
          目前为30,000美元（基于中间市场）。假设目标深度为5,000美元          相对于中间市场目标价差为150美元（以美元计）。
          <br />
        </p>
        <p></p>
        <p>
          <br />每分钟都使用随机抽样计算。
          <br />
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p></p>
        <p>
          <img src="https://lh5.googleusercontent.com/uxfSceooDx_9syd0kVXz7bNopBlxm4z1vKzs55QRYntJ4bsCXMBcAYEjAzLLd4yyYVLaqL93UfxSACki00hgtcf9C72tlzV-CtDgiQh-f5rjbC8JTF14DKCBmOSLUlmgoqnej9N4" alt />
        </p>
      </td>
      <td style="text-align:left">
        <p>假设流动性提供方有多个公开询价订单（0.1 BTC为30,100美元，
          5 BTC，31,200美元，10 BTC，31,300美元）基于BTC-USD订单簿和BTC
          目前交易价格为30,000美元（基于中间市场）。假设目标深度
         为5,000美元，相对于中间市场目标价差为150美元（以美元计）。</p>
        <p></p>
        <p></p>
        <p>
          <br />每分钟根据随机间隔进行计算。</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <img src="https://lh5.googleusercontent.com/NFiIrqk0GpxShUTMvywPxbIUYewahGzCZQUSIue6GwEluEgDy1_FrrlGmWjwJI_qdqHB5h2OMJhf7P3gWxX64sSkl5ldZNZ6qvVHdHGxRfRJp_V6wXwGkxQJMIn8c2N4BZHU8YcJ" alt />
      </td>
      <td style="text-align:left">
        <p>通过取最小值来奖励双边流动性。
          <br />
        </p>
        <p>每分钟计算。</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <img src="https://lh5.googleusercontent.com/Zge9XwAIKExLapir2KtmQU_Hf6WYoFeCzr7gWmiMxWF3K2mDPdRsThIM3uJiyQp-GZ1VR5rcDGrTpgREjhGACboCo2CeDIRAC5OlnfkQQwW0AVLmvtqFsrWK0AE-TbG39ndNreSR" alt />
      </td>
      <td style="text-align:left">是特定时段中的全体总和。</td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <img src="https://lh6.googleusercontent.com/D2pCRVlr0ARtcHcbjWTDFa4edOMHkqk9-s09KwuKKZts82jaAG_zr09kJQZroO9Qd7fz9Z65cG3oH4RoWKd6B_7iKBGTbK6sAW7EGJmrb3v2e_jqAXMnq7BuZIgdu_KwCsrfBKM3" alt />
      </td>
      <td style="text-align:left">是指特定做市商实时时段的时间百分比
        和报价（正常运行时间）。</td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p></p>
        <p>
          <img src="https://lh4.googleusercontent.com/alasGvASJao4t8C1fFPcA5pI6MZIoM0SZQIlYSmAEedmXnMupVZNY4fPWxkF6u9XSwuUxjStbqYoSbfH9I7m8MWPtRYUnGm3LsW6a3smHDEUbXoLhlKYQgNXoUu2gcMb-x7zKlVt" alt />
        </p>
      </td>
      <td style="text-align:left">正常化，以计入正常运行时间</td>
    </tr>
  </tbody>
</table>

每个永续交易对将拥有自己的奖励资金池，并以不同的方式加权。适用于每个交易对的初始加权组如下：

| 交易对 | 总奖励池的分配百分比 |
| :--- | :--- |
| BTC–USD | 20% |
| ETH-USD | 20% |
| 其他永续交易对 | ![](../.gitbook/assets/screen-shot-2021-07-15-at-1.20.17-pm.png) |

## 常见问题解答

### 谁有资格获得流动性提供方奖励？

所有在上一时段以dYdX Layer 2永续合约达到至少5%市场交易量的流动性提供方，都有资格在特定时段获得DYDX作为奖励。

对于0时段，dYdX Trading将运行数字，以确定哪些做市商有资格。dYdX Trading将决定哪些做市商达到此阈值。

如dYdX的[使用条款](https://dydx.exchange/terms)所规定，该产品不提供给美国或受限制地区的交易者。

### 我在流动性提供方奖励计划中赚取了多少DYDX？

在一个特定时段，流动性提供方根据其在特定交易对的市场的相对$$Q_{SCORE}$$赚取收益。每个交易对各自的相对奖励金额由治理确定。DYDX的预期金额可以根据参与的做市商人数、相对$$Q_{SCORE}$$以及给定交易对的可用奖励金额来确定。

### 我如何申领流动性提供方奖励？

流动性提供方奖励显示在[dYdX API](https://docs.dydx.exchange/)上。尽管在治理用户界面中没有出现，但仍可在[此处](https://dydx.community/dashboard)在时段结束时通过治理来申领。

### 我何时可以提现并转让申领的DYDX流动性提供方奖励？

通过交易奖励赚取的DYDX代币将在每个时段结束后`7天`内\（**等待期间**\）可以转让。

### 我们如何定义和衡量双侧深度、出价询价价差和正常运行时间？

**双侧深度**

双侧流动性提供方是公司或个人，他们积极在dYdX上报价双侧交易对，向特定交易对出价和询价。他们为去中心化交易所整体提供流动性。

例如，BTC-USD交易对的做市商可能提供30,000-30,100美元，10x50的报价。这意味着他们以30,000美元的价格出价\（他们将购买\）10 BTC，并以30,100美元的价格提供\（他们将出售\）50 BTC。其他做市参与方可以按照30,100美元的价格从做市商处购买\（取消出价\），或者以30,000美元的价格向他们卖出\（中标\）。

根据流动性提供方在特定交易对上提供出价和询价的能力，对其进行评估。由于min\(\)函数，仅在1侧报价\（只是出价或询价\）的流动性提供者被排除在获得奖励之外。

**中间市场价差**

流动性的一种常见衡量标准是买卖价差：交易对中最高出价\（买入订单\）价格和最低卖出\（卖出订单\）价格之间的价差。买卖差价，即价差，是交易的主要交易成本\（外部佣金\），它由流动性提供方通过以买卖价格处理订单来收取。价差衡量立即与用户进行交易的成本。

中间市场价差特别采用了市场的中值。通过该公式，每个交易对MinDepth水平以下的订单也被排除。

例如，如果一个流动性提供方对BTC-USD的出价为30,000美元，而要价为30,100美元，那么价差为100美元。中间市场价格为30,050美元，那么中间市场价差为50美元。

**正常运行时间**

流动性提供方的正常运行时间对市场至关重要，尤其是在高度波动时期。通过将5的指数应用到$$Uptime_{epoch}$$作为$$Q_{FINAL}$$的输入，奖励会偏向于不断保持两侧流动性的流动性提供方。换言之，提供99%正常运行时间的流动性提供方比提供90%正常运行时间的做市商在指数上价值更高。

正常运行时间定义为在给定交易对中按分钟提供流动性\（随机抽样\）的时间订单的百分比。正常运行时间不包括交易所面临中断的时段。可能存在交易所缓慢或不接受订单\（但不是中断\）的边缘情况 - 在这种情况下，上述情况不适用\（但这将被视为错误，所有做市商都会受到类似的影响，与中断一样）。

### 我们如何定义每种交易对的最大价差？

当价差高于给定交易对的$$MaxSpread$$时，不会生成$$Q_{BID}$$或$$Q_{ASK}$$。

初始最大价差如下：

| 交易对 | 最大点价差对比中间市场\（出价和询价\） |
| :--- | :--- |
| BTC–USD | 20基点 |
| ETH-USD | 20基点 |
| 其他永续交易对 | 40基点 |

### 我们如何定义每种交易对的最小规模？

当规模低于特定交易对的 $$MinSize$$ 时，不会产生 $$Q_{BID}$$ 或 $$Q_{ASK}$$。

初始最小规模如下：

| **交易对** | **最小规模\（出价和询价\）** |
| :--- | :--- |
| BTC–USD | 5,000美元 |
| ETH-USD | 5,000美元 |
| 其他永续交易对 | 1,000美元 |

