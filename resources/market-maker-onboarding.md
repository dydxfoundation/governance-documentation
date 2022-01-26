---
description: >-
  为了方便做市商进行入门培训，dYdX团队制作了本指南。在开始任何集成步骤之前，请通读整个文档。
---

# 做市商入门培训

## dYdX建议的做市商入门培训流程：

1. 将您的首选以太坊钱包连接到dYdX L2永续协议。
2. 将USDC存入您的永续合约账户。
3. 您需要生成一个STARK密钥，用于在Layer 2识别您的账户并保存在本地浏览器中。Stark密钥将dydX用户与以太坊账户地址相关联，因此用户必须首先请求签署以太坊密钥与STARK密钥的链接，然后在dYdX智能合约上注册STARK密钥，才能执行任何其他用户操作。单击“生成Stark密钥”并签名交易。签名是免费的，而且不会发送交易。您可以随时使用钱包找回Stark密钥。

或者，程序化交易者可以使用以下方法导出他们的STARK密钥对：

```
key_pair_with_y_coordinate = client.onboarding.derive_stark_key(
  # Optional if eth_private_key or web3.eth.defaultAccount was provided.
  ethereum_address='ethereumAddress',
)
```

有关STARK密钥的更多信息，请在此处查阅。

4\。接下来，您需要一个以太坊签名或通过Web 3提供方来签名的API密钥。请注意，以太坊签名仅用于注册和管理API密钥，而不用于交易——交易要求使用STARK密钥签名。可以使用以下功能注册和获得API密钥：

_注册：_

```
api_key_response = client.api_keys.create_api_key(
# Optional if eth_private_key or web3.eth.defaultAccount was provided.
ethereum_address='0x0123...',
)
```

_获得：_

```
api_keys = client.private.get_api_keys()
```

_或者（3.和4.）_，如果您不希望私钥在线，您可以通过以下步骤安全地生成STARK密钥以获取所需的凭据。

a. 在dYdX永续合约交易所中，右键单击网络浏览器中的任意位置，然后选择“检查”以打开“开发人员工具”

b. 转到“应用程序”>“本地存储”>https://trade.dydx.exchange

c. 选择“STARK\_KEY\_PAIRS”并单击您的钱包地址旁的下拉菜单，以获取stark私钥

d 选择“API\_KEY\_PAIRS”并单击您的钱包地址旁边的下拉菜单，以获取API密钥、加密密钥和密码
