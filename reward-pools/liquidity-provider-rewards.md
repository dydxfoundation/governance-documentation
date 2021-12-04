---
description: 流動性プロバイダー報酬の概要。

---

# 流動性プロバイダーの報酬

稼働時間、両方向のデプス、売買スプレッド、およびサポートされているマーケット数の組み合わせによる報酬計算公式に基づき、流動性プロバイダーには7.5％ \（`7,500万DYDX`\）が提供されます。

**目的**

* 両方向の流動性を改善し、流動性プロバイダーにプログラムによる報酬を提供します。

## **概要**

マーケットの流動性を利用できるようにするため、DYDXはマーケット参入、両方向のデプス、スプレッド \（対ミッドマーケット\）、およびdYdXレイヤ2プロトコルの稼働時間から計算される報酬計算公式に基づき、流動性プロバイダーに提供されます。イーサリアムのアドレスでは、前身のエポックにおけるメーカーボリュームの5％の最小メーカーボリューム基準値を条件とし、かかる報酬を獲得できます。DYDXは5年間にわたって28日間のエポックを基本として提供され、権利確定やロックアップの対象にはなりません。115万685ドル DYDXは、各エポックにて提供されます。

エポックごとに流動性プロバイダーにどのくらいのDYDXが報酬として支払われるかを計算するには、以下の関数を使用します。得られるDYDXの量は、各参加者の$$Q_{FINAL}$$の相対的なシェアによって決定されます。

![](https://lh6.googleusercontent.com/0cDsOz823Q4TxMJmBn1qqh9M0caQfYuRr6tqgdTfadGWsSn-h6mQd4xkoLsBVIXuSi767ruq17xnGZaneymMZDY6O-5r1pbJT0ozMgYBZ8hj0fdNwZBGPijWXOdCEzYf49QJkEYr)

マーケットごとに一定の**最小デプス** \(size\) \($$MinSize$$\)を下回る注文および一定の**最大スプレッド** \(ミッドマーケットスプレッド\) \($$MaxSpread$$$\)を上回る注文は除外されます。

流動性プロバイダーのパフォーマンスは分単位で監視および計算され \（ランダム化されたサンプリングを使用\）、所与のマーケットの$$Q_{SCORE}$$\($$Q_{FINAL}$$\)に集約されます。分単位のサンプリングにより、各エポックには28日間\* 24時間\* 60分のデータポイント（1エポックあたり合計40,320データポイント）があります。

流動性プロバイダーは、エポックごとの相対的な$$Q_{FINAL}$$のシェアに基づいて月次報酬を得ます。

上記の公式の詳細は以下のような逐次段計算に分かれています。

<table>
  <thead>
    <tr>
      <th style="text-align:left">用語（計算順）</th>
      <th style="text-align:left">定義</th>
      <th style="text-align:left">説明/例</th>
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
        <p>流動性プロバイダーが、BTC-USDのオーダーブックで複数のオープンオーダー（29,900ドルで0.1BTC、
29,800ドルで5BTC、29,500ドルで10BTC）を保持しており、BTCは
現在3万ドル（ミッドマーケットに基づく）であると仮定します。TargetDepthが5,000ドル、
TargetSpread対ミッドマーケットは150ドル（USD条件）であると仮定します。<br />
</p>
        <p></p>
        <p><br />ランダムサンプリングを使用して分単位で計算します。<br />
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
        <p>流動性プロバイダーが、BTC-USDのオーダーブックで複数のオープンアスクオーダー（30,100ドルで0.1BTC、
31,200ドルで5BTC、31,300ドルで10BTC）を保持しており、BTCは
現在3万ドル（ミッドマーケットに基づく）で取引されていると仮定します。TargetDepthは
5,000ドル、TargetSpread対ミッドマーケットは150ドル（USD条件）であると仮定します。</p>
        <p></p>
        <p></p>
        <p><br />ランダムな間隔により分単位で計算されます。</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <img src="https://lh5.googleusercontent.com/NFiIrqk0GpxShUTMvywPxbIUYewahGzCZQUSIue6GwEluEgDy1_FrrlGmWjwJI_qdqHB5h2OMJhf7P3gWxX64sSkl5ldZNZ6qvVHdHGxRfRJp_V6wXwGkxQJMIn8c2N4BZHU8YcJ" alt />
      </td>
      <td style="text-align:left">
        <p>最小値を取ることで、両方向の流動性に報酬を与えます。<br /></p>
        <p>毎分計算されます。</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <img src="https://lh5.googleusercontent.com/Zge9XwAIKExLapir2KtmQU_Hf6WYoFeCzr7gWmiMxWF3K2mDPdRsThIM3uJiyQp-GZ1VR5rcDGrTpgREjhGACboCo2CeDIRAC5OlnfkQQwW0AVLmvtqFsrWK0AE-TbG39ndNreSR" alt />
      </td>
      <td style="text-align:left">所与のエポックにおけるすべての合計です。</td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <img src="https://lh6.googleusercontent.com/D2pCRVlr0ARtcHcbjWTDFa4edOMHkqk9-s09KwuKKZts82jaAG_zr09kJQZroO9Qd7fz9Z65cG3oH4RoWKd6B_7iKBGTbK6sAW7EGJmrb3v2e_jqAXMnq7BuZIgdu_KwCsrfBKM3" alt />
      </td>
      <td style="text-align:left">エポックにおいて、特定のマーケットメーカーが取引および
建値の提示を行っていた時間の割合です（稼働時間）。</td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p></p>
        <p>
          <img src="https://lh4.googleusercontent.com/alasGvASJao4t8C1fFPcA5pI6MZIoM0SZQIlYSmAEedmXnMupVZNY4fPWxkF6u9XSwuUxjStbqYoSbfH9I7m8MWPtRYUnGm3LsW6a3smHDEUbXoLhlKYQgNXoUu2gcMb-x7zKlVt" alt />
        </p>
      </td>
      <td style="text-align:left">正規化して稼働時間を説明します。</td>
    </tr>
  </tbody>
</table>

各パーペチュアルマーケットには、加重が異なる独自の報酬プールがあります。各マーケットに適用される最初の加重値のセットは以下のとおりです。

| マーケット | 総報酬プールの配分率 |
| :--- | :--- |
| BTC-USD | 20％ |
| ETH-USD | 20％ |
| その他のパーペチュアルマーケット | ![](../.gitbook/assets/screen-shot-2021-07-15-at-1.20.17-pm.png) |

## FAQ

### 流動性プロバイダー報酬の対象者は誰ですか？

過去のエポックのdYdXレイヤ2パーペチュアルで最小メーカーボリュームである5％を達成したすべての流動性プロバイダーは、所定のエポックでDYDXを報酬として受け取る資格があります。

エポック0では、dYdX Tradingがどのマーケットメーカーが適格であるかを判断します。dYdX Tradingはどのマーケットメーカーがこの基準値に達しているかを判断します。

dYdXの[利用規約](https://dydx.exchange/terms)に定められているように、この商品は米国または制限地域のトレーダーにはご利用いただけません。

### 流動性プロバイダー報酬プログラムでDYDXをどのくらい獲得しましたか？

所定のエポックでは、流動性プロバイダーは所定のペアのマーケットにおける相対的な$$Q_{SCORE}$$に基づいてイールドを獲得します。各ペアには、ガバナンスによって設定された相対的な報酬額があります。獲得できるDYDXの期待値は、関与するマーケットメーカーの数、相対的な$$Q_{SCORE}$$、および所定のペアでの報酬額に基づき決定されます。

### 流動性プロバイダー報酬を請求するにはどうすればよいですか？

流動性プロバイダー報酬は、[dYdX API](https://docs.dydx.exchange/)に表示されます。ガバナンスのユーザーインターフェースには表示されないものの、[ここ](https://dydx.community/dashboard)での各エポックの終了時にガバナンスを通じて請求することが可能です。

### 請求済みのDYDX流動性プロバイダー報酬はいつ出金および移転することができますか？

取引報酬として獲得したDYDXトークンは、各エポックの終了後`7日間`\（**待機期間**\）を経過すると移転可能になります。

### 両方向のデプス、売買スプレッド、および稼働時間はどのように定義および測定するのでしょうか？

**両方向のデプス**

両方向の流動性プロバイダーとは、dYdXで両方向のマーケットで積極的にクォートする企業または個人を指しており、マーケットで多くの呼値を提示します。全体として分散型取引所に流動性を提供します。

たとえば、BTC-USDマーケットでマーケットメーカーが3万ドル - 3万100ドル、10x50を提示しているとします。これはつまり、3万ドルで10BTC\（購入する\）と提示し、3万100ドルで50BTC\（売却する\）と提示していることになります。その他のマーケット参加者は、このマーケットメーカーから3万ドルで\（オファーを押し上げて\）購入するか、マーケットメーカーに3万100ドルで\（約定して\）売却することができます。

流動性プロバイダーは、所定のマーケットでの両方向の価格提示能力について評価されます。一方向 \（売値または買値\）のみクォートする流動性プロバイダーは、min\(\)関数により報酬の受け取り対象から除外されます。

**ミッドマーケットのスプレッド**

流動性の一般的な尺度の1つとして、ビッド・アスク・スプレッドがあります。これはマーケットにおける最も高い買値\（買い注文\）と最も安い売値\（売り注文\）の差を指します。買値と売値の差であるスプレッドは主な取引コスト\（手数料以外\）であり、その買値と売値で注文を処理することで流動性プロバイダーが受け取ります。このスプレッドはユーザーに対する取引費用を直ちに測定します。

ミッドマーケット・スプレッドは、このマーケットでの中央値を指しています。この公式では各マーケットでMinDepth額を下回る注文も除外されます。

たとえば、流動性プロバイダーのBTC-USDの買値が3万ドルで、売値が3万100ドルである場合、ビッド・アスク・スプレッドは100ドルになります。ミッドマーケット価格は3万50ドルであり、ミッドマーケット・スプレッドは50ドルになります。

**稼働時間**

流動性プロバイダーの稼働時間はマーケット、特にボラティリティが高い期間において重要です。$$Q_{FINAL}$$の入力値の1つである$$Uptime_{epoch}$$に5の指数を適用することで、報酬は両方向の流動性を絶えず維持する流動性プロバイダーの方にスキューします。言い換えれば、稼働時間99％の流動性プロバイダーは90％のマーケットメーカーよりも指数関数的に価値が高いことになります。

稼働時間は、分単位で流動性を提供している所定のマーケットにおけるタイムオーダーの割合として定義されます\（ランダムサンプリングによる\）。稼働時間は取引所が停止している時間を除きます。取引所での処理が遅いとか、注文を受けていない\（ただし停止ではない\）など、上記のケースが適用されないようなエッジケースが存在する可能性があります\（そうしたものがバグとみなされ、すべてのマーケットメーカーが停止状態と同様の影響を受けることがあります）。

### マーケットごとの最大スプレッドをどのように定義しますか？

スプレッドが所定のマーケットの$MaxSpread$を上回っている場合、$$Q_{BID}$$や$$Q_{ASK}$$は生成されません。

最初の最大スプレッドは以下のとおりです。

| マーケット | 最大スプレッド対ミッドマーケット \（売値および買値\） |
| :--- | :--- |
| BTC-USD | 20bps |
| ETH-USD | 20bps |
| その他のパーペチュアルマーケット | 40bps |

### マーケットごとの最小サイズはどのように定義しますか？

サイズが所定のマーケットの$$MinSize$$を下回っている場合、$$Q_{BID}$$や$$Q_{ASK}$$は生成されません。

最初の最小サイズは以下のとおりです。

| **マーケット** | **最小サイズ \（買値および売値\）** |
| :--- | :--- |
| BTC-USD | 5,000ドル |
| ETH-USD | 5,000ドル |
| その他のパーペチュアルマーケット | 1,000ドル |

