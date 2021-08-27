# 如何在dYdX上开空单（做空）

**dYdX简介**

**dYdX是基于以太坊二层开发的去中心化衍生品交易平台，采用了「链外撮合+链上结算」的设计，使资金与交易更加安全及透明，同时也保证了较高的性能及响应速度。dYdX作为全球领先的去中心化合约交易平台有着显著的优势：在交易手续费方面费用低，无gas成本；在取款处理效率方面速度极快，无需等待即可从Layer 2取款；在安全和私密性上，StarkWare的二层技术通过零识证明提高了安全性和隐私性；在交易处理方面，dYdX交易可立即执行并且数小时内在区块链上完成确认；在保证金利用率方面，dYdX可以交叉使用保证金，一个账户访问不同交易对的仓位。**

**什么是空单（做空）**

**空单指的是投资者预期未来市场行情会下跌，通过买入一定数量的数字资产看跌合约的订单叫做空单，同时也叫做空。而在买入空单时，可以通过缴纳一定保证金开设相应倍数杠杆来放大资产的购买力。**

**买入空单后，可在市场下跌时再卖出空单合约从而获利。具体收益计算方法根据所开本位不同，计算方法也不同，具体分为币本位和U本位，因为dYdX为U本位合约，所以我们这里只介绍U本位合约收益计算。收益计算比较简单，即「单张合约价值x买入合约的数量x所开杠杆倍数x下跌比例」；**

**如何开设空单（做空）**

**再完成链接钱包并存款之后，您就可以进行开仓交易了，首先我们选择要开仓的交易对，目前dYdX开设了ETH- USD、BTC- USD、LINK- USD交易对。点击左上角的交易对，下拉选择您要开仓的交易对，这里我们以BTC- USD为例；**

![](https://lh4.googleusercontent.com/r95ZjztF39-3QXXAuZi0ieQh43n-Rsiz1bL_H4_eJdgdALehkKZ_Pwj_gu6-7R3YalQlZbBGeM38YKJwbuMBli9z3WSqFfqm23rBfMqdDHT-CVTA1ERQKvCkvzGSs80Y0c1F839b=s0)![](https://lh6.googleusercontent.com/f38J4PXbSWzx8QyumqOqbKoWpNF7He7j1NV5E5zKk-yaC64xwElcOCxme8fnP4GZ3jqLGB194Ott0DP0Zc6mxAaAGAhFcc_9_uf0ixltGTYSd2eIrNhteydYElK7xIgC08zqFyOG=s0)

**选择完交易对后我们在下方可以看到「市价交易」和「限价交易」：**

**「市价交易」是按照最优市场价来立即进行买卖，适合小额交易，其特点是成交速度快。**

**「限价交易」是按照设定价格来挂单匹配交易，适合于大额交易，成交速度相对较慢，但是成交价位比较准确。**

![](https://lh3.googleusercontent.com/iz4HSWNF8BHOqdv8iXkp0FP5lKvgxr_MAz-D8sG9QUlcrcw0lKu8nWFbkGuRLYQJzjHtvB09Ou048D9dUvQDEU11bjhsYxW-YFByDHaM3elSNRsFE12aAsMGDVAdQEM5czXjFIwT=s0)

**1）市价交易**

**选择「市价交易」，我们可以通过卖出做空。输入响应数量的BTC（设置杠杆倍数）来卖出合约；或者直接直接通过滑动条来进行选择杠杆倍数（1X-25X）和合约方向其中红色为做空。这里需要注意下，做空表示未来预期市场为下跌，并且杠杆倍数越高，越容易受到币价波动的影响，被平仓的风险增高，所以请根据自己的风险承受能力，选择适合自己的杠杆，设置好杠杆倍数后，点击「下市价订单」进行下单。**

![](https://lh6.googleusercontent.com/TtBxpEQlJGNC9096qJAMDVaYBkOoXD99Y4Yjw_UVpLCvpDG5UjrHzU9dB7IEmWXB2Cefu5UYejn0Y8QInvnC_-oR8eoSODAKj0167sXusmvEmRRf9ldfNNBp_OPWGKGZnqIL9GFh=s0)

**2）限价交易**

**选择「限价交易」，限价交易与市价交易基本相同，唯一不同的是限价交易需要设定挂单价格。**

**具体操作为：输入响应数量的BTC并输入限价价格。以合约数量乘以限定价格除以保证金本金（设置杠杆倍数）来买入合约；或者直接直接通过滑动条来进行选择杠杆倍数（1X-25X）和买入方向其中绿色为做空。点击下限价单。**

![](https://lh3.googleusercontent.com/yoeMoJ9sll-XPICrpsTTjiprnn0I8rBEU6trxzm4bVIR5dOQ7yQLLdXroX8-yJ9Yqx0g4RPycaKuOPEY1YNUhLp0NcuOsVM4vH38aPovbIPHVFEoIva3KzGj5bntp64oAvUOCSh6=s0)

**下单之后，用户会签名授权 dYdX 在他们的服务器上撮合这笔交易；如果交易还未撮合交易成功，则会在右下方「订单」中显示您所下订单。**

![](https://lh3.googleusercontent.com/4Y104j26Jwo1C42ePvjQBH__SLhzTq4YLdS9YNNouBza5IUDRKx-APwu1YJyKAdr7Gue-XC1u2o3B4LhtJNvY3_16oqBvY4zM2ots5vylW3K-GfkmqvS5GfplcGrzmDYFo2CPLVT=s0)

**如果交易完成，则会在左下方「全部成交」中显示该笔订单。用户可以在这里查看这笔交易的具体细节和它在链上的连接。**![](https://lh5.googleusercontent.com/VXJCKjmlVsPYZtLNduicXYqKssKPwaAfoQ2BFGvhqGMngULeI4u7Zn4199MHbkIxEG5LTmKos3ND3BZhHx5R875DesfLIvrWkhRO29_vzs9ksnC-kgemeUD6APhGzi_T88Lrkb5X=s0)

**同时开仓之后，你可以在「当前持仓」这里跟踪仓位的盈亏以及查看目前仓位的杠杆倍数和清算价格，并以此制定止盈止损策略。**![](https://lh6.googleusercontent.com/q4tyzIQFizi5Y_1mZQUr-4bfCSEoIgCm8cFfvRppkSl5KAvebMFAeCTnX_h9OnsbX7SLi4c6zpQo3dgGyZa_O55DezA8srfHsaGZWR0X4ZT-o3u3NK99sj-nu9lqOOaH0ikYIX7G=s0)  
****

