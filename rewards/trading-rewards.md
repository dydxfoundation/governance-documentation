---
description: トレード報酬プログラムの概要。
---

# トレード報酬

dYdXレイヤ2プロトコルで取引を行うユーザーに対して、支払われた手数料に基づいて初回のトークン提供額（`2億5,000万DYDX`）の`25.00％`が割り当てられました。[DIP 16](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-16.md)において、dYdXコミュニティは取引報酬を25％引き下げることに[合意しました](https://dydx.community/dashboard/proposal/8)。その結果、所与のエポックで配分される取引報酬はエポック15において383万5,616DYDXから287万6,712DYDXに減少しました。

**目的**

* dYdXレイヤー2プロトコルの使用をすべてのトレーダーに促進する。
* マーケットの流動性および全体的な商品利用を加速する。

## **概要**

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>所定のエポックにおける支払済みの手数料と推定される報酬</p></figcaption></figure>

dYdXレイヤ2プロトコルで支払われた手数料に基づき、トレーダーにDYDXが配分されます。DYDXは、5年間にわたって28日間のエポックを基本として提供され、権利確定やロックアップの対象にはなりません。287万6,712DYDXはエポックごとに提供されます。

コミュニティが取引報酬を383万5,616DYDXから287万6,712DYDXへと25％減少させることに合意したため、報酬基金に加算される残りの95万8,904DYDXはdYdXコミュニティが[ガバナンス投票](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters)で使用/指示することができます。

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

### どのような人がトレード報酬の対象になるのですか？

dYdXレイヤ2プロトコルの全トレーダーは、トレード報酬としてDYDXを受取る資格を有しています。

dYdXレイヤ2プロトコルは、dYdX Trading Inc.の[利用規約](https://dydx.exchange/terms)に定義されているように、米国または制限地域のトレーダーにはご利用いただけません。

### トレード報酬プログラムでどれくらいDYDXを獲得できたのかを知ることはできますか？

現在のエポックでは、ユーザーは[**trade.dydx.exchange/portfolio/rewards**](https://trade.dydx.exchange/portfolio/rewards)で、支払われた手数料と推定されるトレード報酬を確認できます。

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>所定のエポックにおける支払済みの手数料と推定される報酬</p></figcaption></figure>

過去のエポックからの報酬は、[**dydx.community/history/rewards**](https://dydx.community/history/rewards)でご覧いただけます**。**

### トレード報酬を請求するにはどうすればよいですか？いつから獲得したDYDXを出金および移動することができますか？

トレード報酬で獲得したDYDXトークンは、各エポックの終了時から移動することができるようになります。DYDXトークン保有者は、エポックの終了から約`7日`間（**待機期間**）待機した後にDYDXトークンを請求できます。

7日間の待機期間後、コミュニティメンバーは[Merkleディストリビュータコントラクト](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract)上の`updateRoot`パラメータで`Write`関数を呼び出して、DYDX報酬を請求できるようにすることができます。

ステップ：

1. Etherscanの[Merkleディストリビュータコントラクト](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract)ページで、`コントラクト`タブをクリックし、`プロキシとして書き込む`を選択します。
2. `Web3に接続する`ボタンをクリックし、Web3ウォレットを接続します。

<figure><img src="../.gitbook/assets/merkle-distributor-contract.jpeg" alt=""><figcaption></figcaption></figure>

3\. `updateRoot`パラメータまで下にスクロールし、`書き込み`ボタンをクリックします。

<figure><img src="../.gitbook/assets/updateRoot-claiming.jpeg" alt=""><figcaption></figcaption></figure>

**このトランザクションには、Gas（ガス）代のためにETHが必要となり、以下の場合トランザクションは失敗します。**

* 7日間の待機期間がまだ有効な場合
* コミュニティメンバーが、すでに[Merkleディストリビュータコントラクト](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract)で`updateRoot`パラメータを呼び出している場合

トランザクションが確定した後、トレーダーは[こちら](https://dydx.community/dashboard)から取引報酬を請求できます。DYDXを請求するには、`請求`をクリックし、トランザクションに署名して、Gas（ガス）代を支払う必要があります。

![報酬のポートフォリオ概要](../.gitbook/assets/1-portfolio-overview-rewards.png)
