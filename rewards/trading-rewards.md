---
description: トレード報酬プログラムの概要。
---

# 取引報酬

トークン供給の`20.2`**`％`**（`201,883,560 $DYDX`)は、支払われた手数料に基づいてdYdXレイヤー2プロトコルで取引するユーザーに分配されるように割り当てられます。当初、取引報酬にトークン供給の25.0%（`2億5000万$DYDX```）が割り当てられました。

* [DIP 16](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-16.md)では、dYdXコミュニティーが取引報酬を25.0%削減することに[投票](https://dydx.community/dashboard/proposal/8)しました。その結果、取引報酬の割り当ては`25.0%`から`20.2%`に減少しました。
* [DIP20](https://dydx.community/dashboard/proposal/11)では、dYdXコミュニティーが取引報酬をさらに45.0%削減することに[投票](https://dydx.community/dashboard/proposal/11)しました。その結果、取引報酬の割り当ては`20.2%`から`14.5%`に減少しました。

特定の時代に分配された取引報酬は、エポック15で3,835,616 $DYDXから2,876,712 $DYDXに、エポック21で2,876,712 $DYDXから1,582,192 $DYDXに減少しました。

**目的**

* dYdXレイヤ2プロトコルの使用をすべてのトレーダーに促進する。
* マーケットの流動性および全体的な商品利用を加速する。

## **概要**

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>所定のエポックにおける支払済みの手数料と推定される報酬</p></figcaption></figure>

dYdXレイヤ2プロトコルで支払われた手数料に基づき、トレーダーに$dYdXが配分されます。$dYdXは、5年間にわたって28日間のエポックを基本として提供され、権利確定やロックアップの対象にはなりません。エポックごとに1,582,192 $DYDXが配布されます。

[DIP16](https://dydx.community/dashboard/proposal/8)で958,904 $DYDXの取引報酬を25％削減し、[DIP20](https://dydx.community/dashboard/proposal/11)で1,294,520 $DYDXをさらに45％削減することをコミュニティーの投票で決定した場合、報酬トレジャリーに生じる残りの2,253,424 $DYDXはdYdXコミュニティーが[ガバナンス投票](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters)によって使用/指示できるようになります。

<figure><img src="../.gitbook/assets/1-trading-rewards-formula-new.png" alt=""><figcaption></figcaption></figure>

$$
r=R\times \frac{w}{\sum\limits _{n} w_{n}} \ \ ,n=1,2...k
$$

| 用語 | 定義 |
| ---------------------------- | ----------------------------------------------------------------------- |
| r | 特定のトレーダーに対する報酬。 |
| R | 全トレーダー間で分割するためにエポックごとにプールされている報酬総額。 |
| f | このエポックでトレーダーが支払った手数料総額。 |
| w | 個々のトレーダーのスコア。 |
| $${\sum\limits _{n} w_{n}}$$ | 全トレーダーのスコアの合計。 |
| k | このエポックでのトレーダーの総数。 |

[DIP-13](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-13.md)において、dYdXコミュニティは公式を簡素化し、所与のエポックでトレーダーが支払った手数料の総額に基づくものにすることで合意しました。

## FAQ

### 取引報酬の対象者とは？

dYdXレイヤ2プロトコル上のすべてのトレーダーは、取引報酬として$dYdXを受ける資格があります。

dYdXレイヤ2プロトコルは、dYdX Trading Inc.の[利用規約](https://dydx.exchange/terms)に定義されているように、米国または制限地域のトレーダーにはご利用いただけません。

### 取引報酬プログラムで獲得したDYDXを確認できますか？

現在のエポックでは、ユーザーは[**trade.dydx.exchange/portfolio/rewards**](https://trade.dydx.exchange/portfolio/rewards)で、支払われた手数料と推定される取引報酬を確認できます。

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>所定のエポックにおける支払済みの手数料と推定される報酬</p></figcaption></figure>

過去のエポックからの報酬は、[**dydx.community/history/rewards**](https://dydx.community/history/rewards)でご覧いただけます**。**

### 取引報酬を請求するにはどうすればよいですか？いつから獲得した$dYdXを出金および移動することができますか？

取引報酬で獲得した$dYdXトークンは、各エポックの終了時から移動することができるようになります。$DYDXトークン保有者は、エポックの終了から約`7日`間（**待機期間**）待機した後に$DYDXトークンを請求できます。

7日間の待機期間後、コミュニティメンバーは[Merkleディストリビュータコントラクト](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract)上の`updateRoot`パラメータで`Write`関数を呼び出して、DYDX報酬を請求できるようにすることができます。

ステップ：

1. Etherscanの[Merkleディストリビュータコントラクト](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract)ページで、`コントラクト`タブをクリックし、`プロキシとして書き込む`を選択します。
2. `Web3に接続する`ボタンをクリックし、Web3ウォレットを接続します。

<figure><img src="../.gitbook/assets/merkle-distributor-contract.jpeg" alt=""><figcaption></figcaption></figure>

3\. `updateRoot`パラメータまで下にスクロールし、`書き込み`ボタンをクリックします。

<figure><img src="../.gitbook/assets/updateRoot-claiming.jpeg" alt=""><figcaption></figcaption></figure>

**このトランザクションには、ガス代のためにETHが必要となり、以下の場合トランザクションは失敗します。**

* 7日間の待機期間がまだ有効な場合
* コミュニティメンバーが、すでに[Merkleディストリビュータコントラクト](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract)で`updateRoot`パラメータを呼び出している場合

トランザクションが確定した後、トレーダーは[こちら](https://dydx.community/dashboard)から取引報酬を請求できます。$DYDXを請求するには、`請`求をクリックし、トランザクションに署名して、ガス代を支払う必要があります。

![報酬のポートフォリオ概要](../.gitbook/assets/1-portfolio-overview-rewards.png)
