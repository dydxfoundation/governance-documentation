---
description: ガバナンスアーキテクチャおよびスマートコントラクトの概要。
---

# テクニカル概要

## ガバナンスアーキテクチャの概要

dYdXのオンチェーン・ガバナンスは以下の機能をサポートしています。

* 提案の作成および選択
* 提案の開始時に保有しているトークンのスナップショット
* 選択権および提案権に関する個別の委任
* 提案数、定足数、選択の差異基準を含むガバナンス基準の設定
* 選択のカウント方法を決定する「ガバナンス戦略」スマートコントラクトの置き換え
* 以下の内容を許可する複数の実行管理者契約の構成：
  *
    1. ショートタイムロックの実行管理者による迅速なプロトコルのアップグレードおよび資金の配分。
  *
    1. ロングタイムロックの実行管理者によるガバナンスのアップグレード。

dYdXガバナンスをサポートするスマートコントラクトは6つあります。

* **`DydxToken`契約**：アドレスが有する選択権や任意のブロック番号での提案権に関するクエリをサポートするスナップショットを維持します。選択権と提案権に関する個別の委任をサポートします。
* \*\*`DydxGovernor`契約：\*\*提案を追跡し、実行管理者のスマートコントラクトを通じて提案を実行することができます。
* **`実行管理者`契約**：ガバナンスによって選択された取引のキュー、キャンセル、実行ができます。提案が承認されると、提案で指定された実行管理者契約によって提案内の関数呼び出しが実行される可能性があります。キューされた取引は、実行管理者契約に定められている期間内に実行することが可能です。
* \*\*\*\***`優先タイムロック`コントラクト：タイムロックコントラクトと同じですが、優先度コントローラーが優先期間**（タイムロックの遅延終了の7日前）以内にトランザクションを執行することが可能になります。
* **`ガバナンス戦略`契約**：選択票数カウントのロジックが含まれています。現在、DYDXトークンおよびセーフティモジュールからの選択数をカウントします。ロングタイムロックによりアップグレードできます。
* **`セーフティモジュール`の契約**：DYDXトークンのステーク、ステークされたポジションのトークン化、報酬の獲得のためのロジックが含まれており、選択権、提案権、およびアンダーライングトークンの委任に関する機能を保持します。

{% tabs %}
{% tab title="Mainnet" %}
| 契約                       | アドレス                                       |
| ------------------------ | ------------------------------------------ |
| DydxToken                | 0x92D6C1e31e14520e676a687F0a93788B716BEff5 |
| DydxGovernor             | 0x7E9B1672616FF6D6629Ef2879419aaE79A9018D2 |
| ショートタイムロックの執行管理者         | 0x64c7d40c07EFAbec2AafdC243bF59eaF2195c6dc |
| Chainlinkアダプター           | 0x99B0599952a4FD2d1A1561Fa4C010827EaD30354 |
| 流動性ステーキング                | 0x5Aa653A076c1dbB47cec8C1B4d152444CAD91941 |
| 請求プロキシ                   | 0x0fd829C3365A225FB9226e75c97c3A114bD3199e |
| StarkExヘルパーガバナー          | 0x0db9b3F7Dd83e29C9bece8E5e1089bA4369E694a |
| StarkExリムーバーガバーV2        | 0xFCAac0F14deA11eDe11Afcb875f29130e1ad5ec0 |
| 報酬基金のプロキシ管理者             | 0x40D6992cbd03E0DC1c2DE9606D29Cb245E737a5d |
| Merkleディストリビューターのプロキシ管理者 | 0x6C5cd3aD7A16Ae207D221908E6b997d9B0DcD7b0 |
| 流動性ステーキングプロキシ管理者         | 0xAc5D8bCD13da463bea96c75f9085c4e40037F790 |
| StarkProxy \[0]          | 0x0b2B08AC98a1568A34208121c26F4F41a9e0FbB6 |
| StarkProxy \[1]          | 0x3e6E9EFb0A677a24F47093a22044dc5451A028cF |
| StarkProxy \[2]          | 0xCB7fa3a2F47b62293Cc2E1a4C7752fC72E49FCe2 |
| StarkProxy \[3]          | 0x16BEC2D9A010e7D8b2D576d17893C52Ddbfe4C06 |
| StarkProxy \[4]          | 0x531F3BE462F10386D01FBeD7fAD1d20A61Ce7874 |
| StarkProxyのプロキシ管理者 \[0]  | 0xE16718eace44e0CB06b9cd164490A69A6425D1e3 |
| StarkProxyのプロキシ管理者 \[1]  | 0x78e899e576C3565C3219dbC9Ea5042A9DBed36d3 |
| StarkProxyのプロキシ管理者 \[2]  | 0x15774D4555fEfD57C9Fc8b11C8beba993eafcc13 |
| StarkProxyのプロキシ管理者 \[3]  | 0x4d9460e5C958f46a1Fe129954A069a37972f16EA |
| StarkProxyのプロキシ管理者 \[4]  | 0xfa45DCDbEc82C94082d283B62506320DB8632054 |
{% endtab %}
{% endtabs %}

## オープンソースコードおよび監査済み契約

ガバナンス契約およびステーキングプールのすべてのスマートコントラクトのソースコードは、[https://github.com/dydxfoundation/governance-contracts](https://github.com/dydxfoundation/governance-contracts)をご覧ください。

dydx.communityでホストされているガバナンスフロントエンドのソースコードは、[こちら](https://github.com/dydxfoundation/pnyx)をご覧ください。

すべての主要な新しいスマートコントラクトは、Peckshieldによって監査されました。重要または優先度の高いセキュリティの問題は見つかりませんでした。コアガバナンスおよびトークンに関する契約は、[CertiK](https://www.certik.io)、[Certora](https://www.certora.com)、[Peckshield](https://peckshield.com/en)によって監査され、数ヶ月間メインネットで試行済みのAAVAガバナンス契約から派生しています。

## コアガバナンス契約

![Red dashed lines indicate contract is upgradeable](<../.gitbook/assets/Screen Shot 2021-09-03 at 5.17.43 PM.png>)

### DydxToken

DydxToken契約はAaveによりインスパイアされました。dYdXチームによってマイナーな変更が行われました。

DYDXは、イーサリアムメインネットの[0x92D6C1e31e14520e676a687F0a93788B716BEff5](https://etherscan.io/address/0x92d6c1e31e14520e676a687f0a93788b716beff5)にデプロイされています。コミットから構築されました\[近日公開予定]。

**ABI**

\[近日公開]

### DydxGovernor

DydxGovernor契約はAaveによりインスパイアされました。dYdXによってマイナーな変更が行われました。

ガバナーは、イーサリアムメインネットの[0x7E9B1672616FF6D6629Ef2879419aaE79A9018D2](https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2)にデプロイされています。コミットから構築されました\[近日公開予定]。

### GovernanceStrategy（ガバナンス戦略）

GovernanceStrategy（ガバナンス戦略）コントラクトはAaveによりインスパイアされました。

戦略はイーサリアムメインネットの[0x90Dfd35F4a0BB2d30CDf66508085e33C353475D9](https://etherscan.io/address/0x90Dfd35F4a0BB2d30CDf66508085e33C353475D9)にデプロイされています。コミットから構築されました\[近日公開予定]。

**ABI**

\[近日公開]

### 実行管理者

実行管理者契約はAaveによりインスパイアされました。dYdXによってマイナーな変更が行われました。

**ロングタイムロック**は、イーサリアムメインネットの[0xEcaE9BF44A21d00E2350a42127A377Bf5856d84B](https://etherscan.io/address/0xecae9bf44a21d00e2350a42127a377bf5856d84b)にデプロイされています。コミットから構築されました\[近日公開予定]。

**ABI**

\[近日公開]

**ショートタイムロック**は、イーサリアムメインネットの[0xEcaE9BF44A21d00E2350a42127A377Bf5856d84B](https://etherscan.io/address/0xecae9bf44a21d00e2350a42127a377bf5856d84b)にデプロイされています。コミットから構築されました\[近日公開予定]。

**ABI**

\[近日公開]

**Merkleタイムロック**は、イーサリアムメインネットの[0xd98e7A71BacB6F11438A8271dDB2EFd7f9361F52](https://etherscan.io/address/0xd98e7a71bacb6f11438a8271ddb2efd7f9361f52)にデプロイされています。コミットから構築されました\[近日公開予定]。

**ABI**

\[近日公開]

**Starkwareのプライオリティタイムロック**は、イーサリアムメインネットの[0xa306989BA6BcacdECCf3C0614FfF2B8C668e3CaE](https://etherscan.io/address/0xa306989ba6bcacdeccf3c0614fff2b8c668e3cae)にデプロイされています。コミットから構築されました\[近日公開予定]。

**ABI**

\[近日公開]

## DYDXのインセンティブ契約

### Merkleディストリビュータ

![Red dashed lines indicate contract is upgradeable](<../.gitbook/assets/Screen Shot 2021-09-03 at 5.23.50 PM.png>)

Merkleディストリビューターのスマートコントラクトは、Merkleの残高ツリーに従ってDYDXトークン報酬を配布します。各ユーザーの累積報酬残高によりツリーを定期的に更新できることで、時間の経過に伴い新しい報酬をユーザーに提供できます。

提案されているMerkleルートをオラクル契約によって返される最新の値に設定することで、更新が実行されます。提案されているMerkleルートは、待機期間が経過した後でアクティブにできます。待機期間中、提案されたルートが間違っているか悪意がある場合、dYdXガバナンスにはMerkleルートを凍結する機会があります。ShortTimelockExecutorでは、ルートの更新の一時停止を解除することができます。

Merkleディストリビューターのスマートコントラクトは、UniswapおよびBadgerのデザインにインスパイアされました。スマートコントラクトは、イーサリアムメインネットの0x01d3348601968aB85b4bb028979006eac235a588にデプロイされています。コミットから構築されました\[近日公開予定]。

**ABI**

\[近日公開]

### 安全モジュール

![Red dashed lines indicate contract is upgradeable](<../.gitbook/assets/Screen Shot 2021-09-03 at 5.24.45 PM.png>)

セーフティモジュールは、プロトコルのセキュリティに向けてDYDXをステークするユーザーにDYDX報酬を提供するステーキングプールです。

**ABI**

\[近日公開]

### 流動性モジュール

![Red dashed lines indicate contract is upgradeable](<../.gitbook/assets/Screen Shot 2021-09-03 at 5.25.30 PM.png>)

流動性モジュールは、ステーキングおよび借入のためのスマートコントラクトの集合体であり、dYdXレイヤ2取引所でのマーケット作成目的のUSDC資金の割り当てを奨励します。

ステーカーはUSDCをステーキングする際にDYDX報酬を獲得します。ステークされた資金はレピュテーションに基づき、無担保で事前に承認された特定のパートナーによって借り入れされる場合があります。資金はL2取引所でのみ使用できます。これはStarkExパーペチュアル取引所契約と相互に適用されるStarkProxy契約を通じて実施されます。

![A diagram of the Liquidity module](<../.gitbook/assets/image (66).png>)

### StarkProxy

この契約により、所有者はLiquidityStakingから資金を借り、StarkPerpetualでそれらの資金を使用できます。所有者は追加資金を入金することが可能で、借入金額を超える資金は自由に出金できます。この契約はStarkwareによって作成され、以前に監査およびデプロイされた[StarkPerpetual](https://github.com/starkware-libs/starkex-contracts/tree/master/scalable-dex/contracts/src/perpetual)契約と相互に適用されます。

### 資金調達契約

![Red dashed lines indicate contract is upgradeable](<../.gitbook/assets/Screen Shot 2021-09-03 at 5.26.09 PM.png>)

TreasuryVester（基金ベスター）契約は、[Uniswap](https://github.com/Uniswap/governance/blob/master/contracts/TreasuryVester.sol)によりインスパイアされました。

ショートタイムロックでは、ガバナンスで承認されたアクションのみ実行できます。

2つの基金ベスターおよび基金契約がありますが、1つはインセンティブ契約報酬であり、もう1つは「一般目的」の基金を保有するものです。

各基金はガバナンスにより管理されているため、資金を任意のアドレスに移動したり、任意ののアドレスがいずれかの基金にある資金を使用することを承認したりすることができます。たとえば、ガバナンスは報酬プログラムにトークンの承認制限を設定する必要があります。

各基金ベスターは、対応する基金に関して5年間（2021年8月3日～2026年8月3日）にわたりリニアにトークンを保有します。

## 周辺契約

### Chainlink Oracle-Powered Rewards（取引および流動性プロバイダーに関する報酬）

このシステムの目標は、オラクル署名者の分散型ネットワークを通じて、dYdXレイヤ2取引所を利用してトレーダーが獲得したDYDXトークンの報酬を計算および公開することです。配布プログラムの開始以来、各ユーザーが獲得した累積報酬を含む報酬はMerkleツリーに保存されます。各エポック、MerkleルートはMerkleDistributorV1スマートコントラクトで更新され、前回のエポックで獲得した報酬が反映されます。

当社はChainlink Oracleシステムと統合しており、報酬データをオンチェーンで掲載します。IPNSを使用して、ChainlinkがMerkleツリーの構築に使用する取引データを掲載します。IPNSを使用することで、以前のエポックと同じIPNSリンクの下に最新のエポックの取引データを掲載できます。つまり、データの場所は変更されません。

生の取引データから適切な報酬を計算した後、ChainlinkはMerkleの報酬ツリーをIPFSに掲載します。Merkleツリーのデータを有するIPFS CIDは、そのエポックの報酬に関するMerkleツリーと共にMerkleディストリビューター契約に保存されます。

以下のフローチャートは、Chainlink Oracle-Powered Rewardsのシステムアーキテクチャを示しています。

![](<../.gitbook/assets/Merkle Distributor.png>)

### その他の資産

* dYdX Foundationのブランド資産は[**こちら**](https://dydx.foundation/brand)で利用可能です\*\*\*\*
