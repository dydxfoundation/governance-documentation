---
description: 流动性提供方奖励计划概述。
---

#

最初，**7.5%** (`75,000,000 $ethDYDX`)  的代币供应量分配用于 LP 奖励。

* 在 [DIP 24](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-24.md)，dYdX 社区[投票](https://dydx.community/dashboard/proposal/14)决定将流动性提供方奖励削减 50%，从每个时段 `1,150,685 $ethDYDX` 降至每个时段 `575,343 $ethDYDX`。因此，LP 奖励的分配从 `7.5%` 降至 `5.2%`。
*   在 [DIP 29](https://dydx.community/dashboard/proposal/16) 中，dYdX 社区[投票](https://dydx.community/dashboard/proposal/16)决定将 dYdX v3 上的 LP 奖励从 30-32 时段减少 ⅓，减为以下值：

    * 时段 30：383,562 $ethDYDX
    * 时段 31：191,781 $ethDYDX
    * 时段 32：0 $ethDYDX

    在时段 31 之后，dYdX v3 上将没有任何 LP 奖励。 因此，LP 奖励的分配从 `5.2%` 降至 `3.2%`。

由于在 dYdX Chain 上没有提供流动性提供者奖励的分配，dYdX 社区在 DIP 29 中投票将剩余的流动性提供者奖励分配迁移到 dYdX Chain 社区库中。

**目标**

* 改善双侧流动性并以程序化方式奖励流动性提供方。

## **概述**

为了激励市场流动性，$ethDYDX 将根据公式分配给流动性提供方，这些公式奖励在 dYdX v3 上的参与做市、挂单量、双侧深度、价差（与中间市场相比），以及正常运行时间。

在 [DIP 15](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-15.md) 中，dYdX 社区投票修订了 LP 奖励公式，将 BTC/ETH 市场和非 BTC/ETH 市场函数分开。在 [DIP 19](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-19.md) 中，dYdX 社区投票赞成将 0.05 stkDYDX 权重重新分配给挂单量。

所赚 ethDYDX 金额由各参与者 $$Q_{FINAL}$$ ($$Q_{BTC}$$+​$$Q_{ETH}$$+$$Q_{non BTC/ETH}$$​) 的相对份额决定。

<figure><img src="../.gitbook/assets/Updated LP Rewards Formulas.png" alt=""><figcaption></figcaption></figure>

每个交易对低于特定**最低深度**（大小）($$MinDepth$$)的订单会被排除，超过特定**最大价差**（中间市场价差）($$MaxSpread$$)交易对的订单也会被排除。

鉴于逐分钟的抽样，每个时段都有28天\*24小时\*60分钟的数据点——每个时段总共40,320个数据点。

流动性提供方根据其相对的$$Q_{FINAL}$$赚取每月奖励。

上述公式分为下面的逐步计算，详情如下：

| _挂单量_ | 该时段的总挂单量。 |
| --------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <img src="../.gitbook/assets/1-qbid-formula.png" alt="" data-size="original"> | <p></p>假设流动性提供方有多个公开出价订单（1个BTC为29,900美元，5个BTC，价格为29,850美元，10个BTC，价格为29,500美元），基于BTC-USD订单簿，BTC目前为30,000美元（基于中间市场）。假设假设MinDepth为5,000美元，MaxSpread对中间市场的比值为200美元，即6.7个基点（200/30,000美元）。<br>基点是1%的1/100。<p></p><span class="math">Q_{BID} = (1\ \times \left(\frac{$29,900}{$100/30000}\right)) + (5\ \times \left(\frac{$29,850}{$150/30000}\right))</span><p></p><br><span class="math">Q_{BID}</span> 以随机采样每分钟计算得出。<br> |
| <img src="../.gitbook/assets/1-qask-formula.png" alt="" data-size="original"> | <p></p>假设流动性提供方有多个公开询价订单（0.1个BTC为30,100美元，5个BTC，价格为30,150美元，10个BTC，价格为30,175美元）基于BTC-USD订单簿，BTC目前交易价格为30,000美元（基于中间市场）。假设假设MinDepth为5,000美元，MaxSpread对中间市场的比值为200美元，即67个基点（200/30,000美元）。基点是1%的1/100。<p></p><span class="math">Q_{ASK} = (5\ \times \left(\frac{$30,150}{$150/30000}\right)) + (10\ \times \left(\frac{$30,175}{$175/30000}\right))</span><p></p><br><span class="math">Q_{ASK}</span>每分钟根据随机间隔进行计算。 |
| <img src="../.gitbook/assets/1-qmin-formula.png" alt="" data-size="original"> | <p></p>通过取<span class="math">Q_{BID}</span>和<span class="math">Q_{ASK}</span>的最小值来奖励双边流动性。<br><p></p>每分钟计算。 |
| <img src="../.gitbook/assets/1-qpoech-formula.png" alt="" data-size="original"> | $$Q_{EPOCH}$$是一个给定时段中所有$$Q_{MIN}$$的总和。 |
| <img src="../.gitbook/assets/1-q-uptime-epoch-formula.png" alt="" data-size="original"> | $$Uptime_{EPOCH}$$ 是指特定做市商实时时段的时间，买卖双方报价均大于规定的最低订单量（按市场在下面注明）并且价差小于规定的最大价差（按市场在下面注明）。 |
| <img src="../.gitbook/assets/1-qfinal-epoch-formula.png" alt="" data-size="original"> | $$Q_{FINAL}$$正常化$$Q_{EPOCH}$$，以计入正常运行时间 |

每个交易对将拥有自己的奖励资金池，并以不同的方式加权。在 [DIP 15](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-15.md) 中，dYdX 社区投票赞成将总奖励（BTC-USD 和 ETH-USDC）的分配量分别降至 10%。适用于每个交易对的加权组如下：

| 交易对 | 总奖励池的分配百分比 |
| ----------------------- | ---------------------------------------------------------------- |
| BTC-USD | 10% |
| ETH-USD | 10% |
| 其他永续交易对 | ![](../.gitbook/assets/1-other-perpetual-markets-lp-weights.png) |

## 常见问题解答

<details>

<summary>谁有资格获得流动性提供方奖励？</summary>

凡是在前一时段在 dYdX v3 上达到最少 0.25% 挂单量的流动性提供方，均有资格在特定时段内获得 ethDYDX 作为奖励。

dYdX v3 不适用于在 dYdX Trading Inc 的[《使用条款》](https://dydx.exchange/terms)中规定的位于美国或受限制地区的流动性提供方。

</details>

<details>

<summary>我在“流动性提供方奖励”计划中赚取了多少 $ethDYDX？</summary>

在一个特定时段，流动性提供方根据其在特定交易对的市场的相对$$Q_{SCORE}$$赚取收益。每个交易对各自的相对奖励金额由治理确定。赚取的 ethDYDX 预计金额会显示在 [“LP 奖励控制面板”](https://p.datadoghq.com/sb/dc160ddf0-b32271920202875868dc46be6b66cf87?tpl\_var\_Market=btc\&from\_ts=1661805073576\&to\_ts=1661891473576\&live=true)中，可根据所涉及的流动性提供方数量、相对$$Q_{SCORE}$$，以及给定交易对的可用奖励金额来确定。

</details>

<details>

<summary>我如何申领流动性提供方奖励？</summary>

流动性提供方奖励显示在[dYdX API](https://docs.dydx.exchange/)上。尽管在治理用户界面中没有出现，但仍可在[此处](https://dydx.community/dashboard)在每个时段结束时通过治理来申领。

</details>

<details>

<summary>“我何时可以支取并转账申领的 $ethDYDX “流动性提供方奖励”？</summary>

一旦初始转账限制期限取消，即可申领和转账通过“流动性提供方奖励”获得的 $ethDYDX 代币。

从1 时段开始，通过“流动性提供方奖励”获得的 $ethDYDX 代币可以在每个时段结束后 `7 天`（**等待期**）开始申领。

</details>

<details>

<summary>两侧深度、买卖价差以及正常运行时间如何定义和衡量？</summary>

* **双侧深度**



* **中间市场价差**



* **正常运行时间**

流动性提供方的正常运行时间对市场至关重要，尤其是在高度波动时期。通过将5的指数应用到$$Uptime_{epoch}$$作为$$Q_{FINAL}$$的输入，奖励会偏向于不断保持两侧流动性的流动性提供方。换言之，提供99%正常运行时间的流动性提供方比提供90%正常运行时间的做市商在指数上价值更高。



</details>

<details>

<summary>每个交易对的最大价差是如何定义的？</summary>

当价差高于给定交易对的$$MaxSpread$$时，不会生成$$Q_{BID}$$或$$Q_{ASK}$$。

初始最大价差如下：

*
*
*

</details>

<details>

<summary>如何定义每个交易对的最低深度（规模）？</summary>

当规模低于给定交易对的$$MinDepth$$时，不会生成$$Q_{BID}$$或$$Q_{ASK}$$。

初始最小深度如下：

*
*
*

</details>

