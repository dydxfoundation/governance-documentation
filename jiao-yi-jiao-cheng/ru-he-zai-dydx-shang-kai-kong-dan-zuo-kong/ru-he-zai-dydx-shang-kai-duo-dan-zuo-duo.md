# 如何在dYdX上开多单（做多）

**dYdX简介**

**dYdX是基于以太坊二层开发的去中心化衍生品交易平台，采用了「链外撮合+链上结算」的设计，使资金与交易更加安全及透明，同时也保证了较高的性能及响应速度。dYdX作为全球领先的去中心化合约交易平台有着显著的优势：在交易手续费方面费用低，无gas成本；在取款处理效率方面速度极快，无需等待即可从Layer 2取款；在安全和私密性上，StarkWare的二层技术通过零识证明提高了安全性和隐私性；在交易处理方面，dYdX交易可立即执行并且数小时内在区块链上完成确认；在保证金利用率方面，dYdX可以交叉使用保证金，一个账户访问不同交易对的仓位。**

**什么是多单（做多）**

**多单指的是投资者预期未来市场行情会上涨，通过买入一定数量的数字资产看涨合约的订单叫做多单，同时也叫做多。而在买入多单时，可以通过缴纳一定保证金开设相应倍数杠杆来放大资产的购买力。**

**买入多单后，可在市场上涨时再卖出看涨合约从而获利。具体收益计算方法根据所开本位不同，计算方法也不同，具体分为币本位和U本位，因为dYdX为U本位合约，所以我们这里只介绍U本位合约收益计算。收益计算比较简单，即「单张合约价值x买入合约的数量x所开杠杆倍数x上比例」；**

**如何开设多单（做多）**

**再完成链接钱包并存款之后，您就可以进行开仓交易了，首先我们选择要开仓的交易对，目前dYdX开设了ETH- USD、BTC- USD、LINK- USD交易对。点击左上角的交易对，下拉选择您要开仓的交易对，这里我们以BTC- USD为例；**

![](https://lh3.googleusercontent.com/aJP1FAU67fdEw4WCjbALYa0\_J6HL8xTwlKCJNBiHFRDvIeSZtox9Zy7fTqf8MPGpF41WLh0Wgaiw5QOeHkBzwYSc9xd01gHqn8jrzk8Rxij5vsz-N6JXcdCHP8gRHYHWHSzRXgNY=s0)![](https://lh6.googleusercontent.com/gnvEvxO0qfu1rCMbV1Ml9\_xYdit3uaOMOvQn8eCf7lQcVZkQPuZtwkp6Jbot2I9uNx8rLfh3zt0IwftmuEhEaYltD0bGY7FIYGx38Jc3tyhco1140o89Ao4E85bByGNvop3gABP2=s0)

**选择完交易对后我们在下方可以看到「市价交易」和「限价交易」：**

**「市价交易」是按照最优市场价来立即进行买卖，适合小额交易，其特点是成交速度快。**

**「限价交易」是按照设定价格来挂单匹配交易，适合于大额交易，成交速度相对较慢，但是成交价位比较准确。**

![](https://lh4.googleusercontent.com/ynnQqHA2mimG382Zp6o\_LFPPkUtvpjMm1SM4CXUkN6W1-Cnq1mQelyI1heOnqY9azZJfa41tLfrNAlvOcUmoR\_mbETlEfESl43wJFE6a7LvuhhL4ih4MuPn75QV0BOZBrw-ce73u=s0)

**1）市价交易**

**选择「市价交易」，我们可以通过买入做多。输入响应数量的BTC（设置杠杆倍数）来买入合约；或者直接直接通过滑动条来进行选择杠杆倍数（1X-25X）和买入方向其中绿色为做多。这里需要注意下，做多表示未来预期市场为上涨，并且杠杆倍数越高，越容易受到币价波动的影响，被平仓的风险增高，所以请根据自己的风险承受能力，选择适合自己的杠杆，设置好杠杆倍数后，点击「下市价订单」进行下单。**

![](https://lh4.googleusercontent.com/YLoJW7hxKpAhGFhrOgK5ztDXRm22D6CRLCWhe8Cjw6u3y79we9rENkHQLi\_j9I8Bf2llfyYA6KF-eGeWiq2Lg8IgM9LraLeCXghwAhBLGeFBxX\_01xRgHSkXWJCreBXjpIWXk7ye=s0)

**2）限价交易**

**选择「限价交易」，限价交易与市价交易基本相同，唯一不同的是限价交易需要设定挂单价格。**

**具体操作为：输入响应数量的BTC并输入限价价格。以合约数量乘以限定价格除以保证金本金（设置杠杆倍数）来买入合约；或者直接直接通过滑动条来进行选择杠杆倍数（1X-25X）和买入方向其中绿色为做多。点击下限价单。**

![](https://lh6.googleusercontent.com/hHSWw9LGv\_ejJxmH1Enpx4CNLvvU4FrYpJxotoIWH7tKWIP2iKJ7uuLAE-bHk1XynMCTr9Viccs25dBC21FKp-R3u4zqb5JntBMUc3NkDs7BQyaCXihCcJqNserGS0Kk6dmr5lhg=s0)

**下单之后，用户会签名授权 dYdX 在他们的服务器上撮合这笔交易；如果交易还未撮合交易成功，则会在右下方「订单」中显示您所下订单。**

![](https://lh3.googleusercontent.com/T-PdR-uLnvNmxftg5mrZ0WjhdWNyOVqlg3yRmGiXh\_uZwThI4xRm3AkvrxzIsa6G9AffEyFw1t-D6I8TCsz5Efxr\_atFP1ZzNd\_TxTrj-7onghP4UyyvEd9EjvN2HiMzLkBygXiE=s0)

**如果交易完成，则会在左下方「全部成交」中显示该笔订单。用户可以在这里查看这笔交易的具体细节和它在链上的连接。**![](https://lh5.googleusercontent.com/zvDeq-7vm-DzTaKXYZlaR-255\_0OyNKvG9vFKy-hYgD0kPPXs11V\_e4IvjYAkPrhblGGbAp6V9vc3JWSoTwuC\_aELLa59ZOrO7TDVfU4lX0-9ZyUHiEwMZsIQHWza5YMU77PrVna=s0)

**同时开仓之后，你可以在「当前持仓」这里跟踪仓位的盈亏以及查看目前仓位的杠杆倍数和清算价格，并以此制定止盈止损策略。**![](https://lh3.googleusercontent.com/g-GNZ1pN5GnEJ1wrh-L2XrlIPkK79\_Ub9IzaOju3nI-CVTsp0jHxUtbOheNthXGwZdsrFPl-2ZW1dNOJ\_7Sniag7XrMZ2vv-WSZtuwlfgMQbgIhOzUoIKo5w-akZzf\_4Xc7Ffw6T=s0)
