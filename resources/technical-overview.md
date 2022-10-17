---
description: 治理架构和智能合约概述。
---

# 技术概述

## 治理架构概述

dYdX链上治理支持以下功能：

* 创建提议并对其进行投票
* 在提议开始时，对代币持有量进行快照
* 委托单独投票和提议权
* 设定治理阈值，包括提议、法定人数和投票差额阈值
* 代替“治理战略”智能合约，该合约决定了计票方式
* 配置多个执行器合约，允许：
  * 通过短时间锁执行器进行快速协议升级和资金分配；
  * 通过长时间锁执行器进行治理升级。

有6个智能合约支持dYdX治理：

* **`DydxToken` 合约**：保留支持查询地址投票或任何区块编号提议权的快照。支持单独委托投票权和提议权。
* **`DydxJordine` 合约**：跟踪提议并可以通过执行器智能合约执行提议。
* **`执行器`合约**：可以排队、取消和执行由治理投票的交易。如果提议通过，则提议中调用的功能可以由提议中指定的执行器合约执行。排队的交易可以在延迟后执行，其期限由执行器合约确定。
* **`优先`**时间锁**合约：**与时间锁合约相同，但允许**优先级******控制器在时间锁延迟之前，在优先期（7天）内执行交易。
* **`治理战略`合约**：包含计票逻辑。目前，统计票数来自DYDX代币和保险模块。可以通过长时间锁进行升级。
* **`保险模块`合约**：包含质押 DYDX 代币的逻辑，表示质押的头寸，并赚取奖励，同时保留了基本代币的投票权和提议权利和委托功能。

{% tabs %}
{% tab title="Mainnet" %}
| 合约                             | 地址                                    |
| ------------------------------------ | ------------------------------------------ |
| DydxToken                            | 0x92D6C1e31e14520e676a687F0a93788B716BEff5 |
| DydxGovernor                         | 0x7E9B1672616FF6D6629Ef2879419aaE79A9018D2 |
| 短时间锁执行器              | 0x64c7d40c07EFAbec2AafdC243bF59eaF2195c6dc |
| 长时间锁执行器               | 0xEcaE9BF44A21d00E2350a42127A377Bf5856d84B |
| Merkle-Pauser时间锁执行器      | 0xd98e7A71BacB6F11438A8271dDB2EFd7f9361F52 |
| Starkware优先时间锁执行器 | 0xa306989BA6BcacdECCf3C0614FfF2B8C668e3CaE |
| 奖励资金库                     | 0x639192D54431F8c816368D3FB4107Bc168d0E871 |
| 社区资金库                   | 0xE710CEd57456D3A16152c32835B5FB4E72D9eA5b |
| 保险模块                        | 0x65f7BA4Ec257AF7c55fd5854E5f6356bBd0fb8EC |
| 治理战略                   | 0x90Dfd35F4a0BB2d30CDf66508085e33C353475D9 |
| 奖励资金库归属者              | 0xb9431E19B29B952d9358025f680077C3Fd37292f |
| 社区资金库归属者            | 0x08a90Fe0741B7DeF03fB290cc7B273F1855767D8 |
| Merkle分配器                   | 0x01d3348601968aB85b4bb028979006eac235a588 |
| Chainlink适配器                    | 0x99B0599952a4FD2d1A1561Fa4C010827EaD30354 |
| 流动性质押                    | 0x5Aa653A076c1dbB47cec8C1B4d152444CAD91941 |
| 申领代理                         | 0x0fd829C3365A225FB9226e75c97c3A114bD3199e |
| StarkEx Helper治理者              | 0x0db9b3F7Dd83e29C9bece8E5e1089bA4369E694a |
| StarkEx Remover治理者V2          | 0xFCAac0F14deA11eDe11Afcb875f29130e1ad5ec0 |
| 奖励资金库代理管理者         | 0x40D6992cbd03E0DC1c2DE9606D29Cb245E737a5d |
| 社区资金库代理管理者       | 0x9d51599A6b10f562619D8ef2EFDcA1B68aE80D03 |
| 保险模块代理管理            | 0x6aaD0BCfbD91963Cf2c8FB042091fd411FB05b3C |
| Merkle分配器代理管理       | 0x6C5cd3aD7A16Ae207D221908E6b997d9B0DcD7b0 |
| 流动性质押代理管理        | 0xAc5D8bCD13da463bea96c75f9085c4e40037F790 |
| StarkProxy \[0]                      | 0x0b2B08AC98a1568A34208121c26F4F41a9e0FbB6 |
| StarkProxy \[1]                      | 0x3e6E9EFb0A677a24F47093a22044dc5451A028cF |
| StarkProxy \[2]                      | 0xCB7fa3a2F47b62293Cc2E1a4C7752fC72E49FCe2 |
| StarkProxy \[3]                      | 0x16BEC2D9A010e7D8b2D576d17893C52Ddbfe4C06 |
| StarkProxy \[4]                      | 0x531F3BE462F10386D01FBeD7fAD1d20A61Ce7874 |
| StarkProxy代理管理 \[0]          | 0xE16718eace44e0CB06b9cd164490A69A6425D1e3 |
| StarkProxy代理管理 \[1]          | 0x78e899e576C3565C3219dbC9Ea5042A9DBed36d3 |
| StarkProxy代理管理 \[2]          | 0x15774D4555fEfD57C9Fc8b11C8beba993eafcc13 |
| StarkProxy 代理管理者 \[3]          | 0x4d9460e5C958f46a1Fe129954A069a37972f16EA |
| StarkProxy代理管理 \[4]          | 0xfa45DCDbEc82C94082d283B62506320DB8632054 |
{% endtab %}
{% endtabs %}

## 开放源代码和审计

治理合约和质押资金池的所有智能合约源代码，请访问[https://github.com/dydxfoundation/governance-contracts](https://github.com/dydxfoundation/governance-contracts)。

dydx.community 托管的治理前端的源代码，请访问[此处](https://github.com/dydxfoundation/pnyx)。

所有主要的新智能合约都已由 Peckshield 进行审计。没有发现重大或高度优先的安全问题。核心治理和代币合约是根据Aave治理合约质押的，该合约由[CertiK](https://www.certik.io/)、[Certora](https://www.certora.com/)和[Peckshield](https://peckshield.com/en)进行审计，并已在主网上进行了数月的攻防测试。

## 核心治理合约

![红色虚线表示合约可以升级](../.gitbook/assets/3-core-governance-contracts-1.png)

### DydxToken

DydxToken合约受到Aave的启发。dYdX团队作了微小变更。

DYDX部署在以太坊主网上：[0x92D6C1e31e14520e676a687F0a93788B716BEff5](https://etherscan.io/address/0x92d6c1e31e14520e676a687f0a93788b716beff5)。根据承诺建立，\[即将推出]。

**ABI**

\[即将推出]

### DydxGovernor

DydxGovernor合约受到Aave的启发。dYdX作了微小变更。

治理者部署在以太坊主网上：[0x7E9B1672616FF6D629Ef2879419aaE79A9018D2](https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2)。根据承诺建立，\[即将推出]。

### 治理战略

治理战略合约受到Aave的启发。

策略部署在[0x90Dfd35F4a0BB2d30CDf66508085e33C353475D9](https://etherscan.io/address/0x90Dfd35F4a0BB2d30CDf66508085e33C353475D9)以太坊主网上。根据承诺建立，\[即将推出]。

**ABI**

\[即将推出]

### 执行器

执行器合约受到Aave的启发。dYdX作了微小变更。

**长时间锁**在以太坊主网上部署：[0xEcaE9BF44A21d0E2350a42127A377Bf5856d84B](https://etherscan.io/address/0xecae9bf44a21d00e2350a42127a377bf5856d84b)。根据承诺建立，\[即将推出]。

**ABI**

\[即将推出]

**短时间锁**在以太坊主网上部署：[0xEcaE9BF44A21d0E2350a42127A377Bf5856d84B](https://etherscan.io/address/0xecae9bf44a21d00e2350a42127a377bf5856d84b)。根据承诺建立，\[即将推出]。

**ABI**

\[即将推出]

**Merkle 时间锁**部署在以太坊主网上：[0xd98e7A71BacB6F11438A8271dDB2EFd7f9361F52](https://etherscan.io/address/0xd98e7a71bacb6f11438a8271ddb2efd7f9361f52)。根据承诺建立，\[即将推出]。

**ABI**

\[即将推出]

**Starkware 优先时间锁**部署在以太坊主网上：[0xa306989BA6bcacdECf3C0614Ff2B8C68e3CaE](https://etherscan.io/address/0xa306989ba6bcacdeccf3c0614fff2b8c668e3cae)。根据承诺建立，\[即将推出]。

**ABI**

\[即将推出]

## DYDX奖励合同

### Merkle分配器

![红色虚线表示合约可以升级](../.gitbook/assets/3-core-governance-contracts-2.png)

Merkle分配器智能合约根据Merkle余额树分配DYDX代币奖励。可以根据每个用户的累计奖励余额定期更新，从而允许随着时间的推移向用户分配新的奖励。

通过将提议的Merkle根设置为预言机合约返回的最新价值来进行更新。在等待期过后，可以推出提议的Merkle根。在等待期间，如果提议的根不正确或恶意，则dYdX治理将有机会冻结Merkle根。根更新可以由短时间锁执行器暂停。

Merkle分配器智能合约受到Uniswap和Badger设计的启发。智能合约部署在以太坊主网上：0x01d348601968aB85b4b028979006eac235a588。根据承诺建立，\[即将推出]。

**ABI**

\[即将推出]

### 保险模块

![红色虚线表示合约可以升级](../.gitbook/assets/3-core-governance-contracts-3.png)

保险模块是质押资金池，向质押DYDX以获得协议安全性的人群提供DYDX奖励。

**ABI**

\[即将推出]

### 流动性模块

![红色虚线表示合约可以升级](../.gitbook/assets/3-core-governance-contracts-4.png)

流动性模块是质押和借款的智能合约集，激励了 USDC 资金分配，以达到 dYdX layer 2 交易所的做市目的。

质押人因质押USDC而赚取DYDX奖励。质押资金可以由某些事先批准的合伙人根据信誉为基础进行借贷，无需质押。资金只能用于L2交易所，这通过StarkProxy合约强制执行，该合约与StarkExperty永续交易所合约进行互动。

![流动性模块图表](../.gitbook/assets/3-core-governance-contracts-5.png)

### StarkProxy

该合约允许所有者从LiquidityStaking中借贷资金，并在StarkPermal上使用这些资金。其他资金可以由质押人寄存，任何超过借款金额的资金也可以自由提现。该合约与[StarkPerpetual](https://github.com/starkware-libs/starkex-contracts/tree/master/scalable-dex/contracts/src/perpetual)合约互动，后者由Starkware编写，并且此前经审计和部署。

### 资金库合约

![红色虚线表示合约可以升级](../.gitbook/assets/3-core-governance-contracts-6.png)

TreasuryVester合约受到[Uniswap](https://github.com/Uniswap/governance/blob/master/contracts/TreasuryVester.sol)的启发。

短时间锁只能执行治理批准的操作。

有两种资金库归属者与资金库合约，一种是激励合约奖励，另一种是持有“普通用途”资金库的资金。

由于治理控制每个资金库，它可以将资金转至任何地址，和/或批准任何地址从任一资金库中支出资金。例如，奖励计划需要由治理设定的代币批准限额。

每个资金库归属者将在大约5年内（2021年8月3日 - 2026年8月3日）将代币线性归属至相应的资金库。

## 外围合约

### Chainlink预言机支持的奖励（交易和流动性提供方奖励）

该系统的目标是通过去中心化的预言机签名者网络，计算和发布交易者使用 dYdX layer 2 交易所获得的 DYDX 代币奖励。奖励存储在Merkle树上，该树包含了自分配计划开始以来每个用户的累计奖励。每个时段，Merkle根都在MerkleDistributorV1智能合约上更新，以反映上一时段赚取的奖励。

我们已经与Chainlink预言机系统整合，在链上公布奖励数据。我们使用IPNS来发布Chainlink用于构建Merkle树的交易数据。通过使用IPNS，我们可以根据与前几时段相同的IPNS链接发布最新时段的交易数据，这意味着数据的位置不会变更。

在计算原始交易数据的适当奖励后，Chainlink将Merkle奖励树发布给IPFS。带有Merkle树数据的IPFS CID存储在Merkle分配器合约上，以及该时段奖励的Merkle根。

下表显示Chainlink预言机支持的奖励系统架构：

![](../.gitbook/assets/3-core-governance-contracts-merkle-distributor.png)

### 其他资产

* dYdX基金会品牌资产，可在[**此处**](https://dydx.foundation/brand)查阅\*\*\*\*
