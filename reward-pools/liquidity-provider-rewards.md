---
description: 유동성 공급자 보상 개요

---

# 유동성 공급자 보상

7.5%\(`75,000,000 DYDX`\)는 가동시간, 양방향 호가, 매수가 및 매도가의 차이 및 지원 시장 수의 조합을 보상하는 공식을 기반으로 유동성 공급자에게 할당됩니다.

**목표**

* 양면 유동성을 개선하고 유동성 공급자를 프로그래밍 방식으로 보상합니다.

## **개요**

시장 유동성을 장려하기 위해 DYDX는 시장 참여, 양방향 호가, 스프레드\(미드마켓 대비\), dYdX 레이어 2 프로토콜에 대한 가동시간을 보상하는 공식을 기반으로 하여 유동성 공급자에게 배포될 것입니다. 모든 이더락 주소는 이러한 보상을 받을 수 있으며, 이는 이전 순환 내 생산자 거래량 5%의 최소 생산자 규모 임계치를 기준으로 합니다. DYDX는 5년에 걸쳐 28일 에포크 기반으로 배포되며 베스팅이나 락업이 적용되지 않습니다. 1,150,685 DYDX가 순환당 배포됩니다.

다음 기능은 에포크당 각 유동성 공급자에게 얼마나 보상해야 하는지 계산하는데 사용됩니다. 획득하는 DYDX의 양은 각 참가자 $$Q_{FINAL}$$의 상대적 비중에 의해 결정됩니다.

![](https://lh6.googleusercontent.com/0cDsOz823Q4TxMJmBn1qqh9M0caQfYuRr6tqgdTfadGWsSn-h6mQd4xkoLsBVIXuSi767ruq17xnGZaneymMZDY6O-5r1pbJT0ozMgYBZ8hj0fdNwZBGPijWXOdCEzYf49QJkEYr)

시장당 특정 **최소 뎁스**\(크기\)\($$MinSize$$\) 미만의 주문은 제외되며, 특정 **최대 스프레드**\(미드마켓 스프레드\)\($$MaxSpread$$\)를 넘어서는 주문도 제외됩니다.

유동성 공급자의 성과를 분 단위로 모니터링되고 계산되며\(무작위 샘플링 사용\), 특정 시장에 대해 $$Q_{SCORE}$$ \($$Q_{FINAL}$$\)(으)로 집계됩니다. 분 단위 샘플링을 감안할 때, 각 에폭에는 28일 \* 24시간 \* 60분의 데이터 포인트(에포크당 총합 40,320 데이터 포인트)가 포함됩니다.

유동성 공급자는 에폭당 상대적 $$Q_{FINAL}$$ 비중에 따라 월간 보상을 받습니다.

위의 공식의 자세한 내용은 아래의 단계별 계산으로 나뉩니다.

<table>
  <thead>
    <tr>
      <th style="text-align:left">용어 (계산 순서)</th>
      <th style="text-align:left">정의</th>
      <th style="text-align:left">설명 / 예</th>
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
        <p>유동성 공급자가 여러 개의 공개 매수 주문을 가지고 있다고 가정합니다($29,900에 0.1 BTC,           $29,850에 5 BTC, $29,500에 10 BTC입니다). 이는 BTC-USD 오더북 상에 있으며 BTC는           현재 $30,000입니다(미드마켓 기준). TargetDepth를 $5000라고 가정하고
          TargetSpread 대 미드마켓은 $150(USD 기준)입니다.<br /></p>
        <p></p>
        <p>

          <br />은(는) 랜덤 샘플링을 사용하여 1분마다 계산됩니다.<br /></p>
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
        <p>유동성 공급자가 여러 개의 공개 매도 주문을 가지고 있다고 가정합니다($30,100에 0.1 BTC,           $31,200에 5 BTC, $31,300에 10 BTC입니다). 이는 BTC-USD 오더북 상에 있으며 BTC는           현재 $30,000에 거래됩니다(미드마켓 기준). TargetDepth는
          $5000이며 TargetSpread 대 미드마켓은 $150(USD 기준)라고 가정합니다.</p>
        <p></p>
        <p></p>
        <p>          <br />은(는) 임의 간격으로 1분마다 계산됩니다.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <img src="https://lh5.googleusercontent.com/NFiIrqk0GpxShUTMvywPxbIUYewahGzCZQUSIue6GwEluEgDy1_FrrlGmWjwJI_qdqHB5h2OMJhf7P3gWxX64sSkl5ldZNZ6qvVHdHGxRfRJp_V6wXwGkxQJMIn8c2N4BZHU8YcJ" alt />
      </td>
      <td style="text-align:left">
        <p>의 최소량을 취하여 양방향 유동성을 보상합니다.
<br />          </p>
        <p>1분마다 계산합니다.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <img src="https://lh5.googleusercontent.com/Zge9XwAIKExLapir2KtmQU_Hf6WYoFeCzr7gWmiMxWF3K2mDPdRsThIM3uJiyQp-GZ1VR5rcDGrTpgREjhGACboCo2CeDIRAC5OlnfkQQwW0AVLmvtqFsrWK0AE-TbG39ndNreSR" alt />
      </td>
      <td style="text-align:left">지정된 에폭 내 모든 수의 합계입니다.</td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <img src="https://lh6.googleusercontent.com/D2pCRVlr0ARtcHcbjWTDFa4edOMHkqk9-s09KwuKKZts82jaAG_zr09kJQZroO9Qd7fz9Z65cG3oH4RoWKd6B_7iKBGTbK6sAW7EGJmrb3v2e_jqAXMnq7BuZIgdu_KwCsrfBKM3" alt />
      </td>
      <td style="text-align:left">특정 마켓 메이커가 활동한 한 에폭 내 시간 비율입니다.
        및 인용(가동 시간).</td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p></p>
        <p>
          <img src="https://lh4.googleusercontent.com/alasGvASJao4t8C1fFPcA5pI6MZIoM0SZQIlYSmAEedmXnMupVZNY4fPWxkF6u9XSwuUxjStbqYoSbfH9I7m8MWPtRYUnGm3LsW6a3smHDEUbXoLhlKYQgNXoUu2gcMb-x7zKlVt" alt />
        </p>
      </td>
      <td style="text-align:left">가동 시간을 고려한 정규화</td>
    </tr>
  </tbody>
</table>

각 무기한 시장은 다르게 가중치를 부여할 자체 보상 풀을 보유할 것입니다. 각 시장에 적용되는 가중치의 초기 세트는 다음과 같습니다.

| 시장 | 총 보상 풀의 할당 비율(%) |
| :--- | :--- |
| BTC-USD | 20% |
| ETH-USD | 20% |
| 기타 무기한 시장 | ![](../.gitbook/assets/screen-shot-2021-07-15-at-1.20.17-pm.png) |

## FAQ

### 유동성 공급자 보상을 받을 자격이 있는 사람은 누구입니까?

이전 에폭에서 dYdX 레이어 2 퍼페츄얼에 대해 최소 5%의 메이커 볼륨을 달성한 모든 유동성 공급자는 특정 에폭에서 보상으로 DYDX를 받을 수 있습니다.

에폭 0의 경우 dYdX Trading은 수치를 합산하여 적격한 마켓 메이커를 결정합니다. dYdX Trading은 어떤 마켓 메이커가 이 임계값에 도달하는지를 결정할 것입니다.

이 상품은 dYdX의 [이용 약관](https://dydx.exchange/terms)에 정의된 대로 미국 또는 제한 지역의 거래자에게는 제공되지 않습니다.

### 유동성 공급자 보상 프로그램에서 얼마나 DYDX를 적립했습니까?

특정 에폭에 유동성 공급자는 특정 페어의 시장에서 상대적 $Q_{SCORE}}$$을(를) 기준으로 수익률을 얻습니다. 각 페어은 거버넌스가 설정한 상대적 보상 금액을 갖추고 있습니다. 획득할 DYDX의 예상 규모는 관련된 마켓 메이커의 수, 상대적 $$Q_{SCORE}$$, 특정 페어가 제공하는 보상 금액을 기준으로 하여 결정될 수 있습니다.

### 유동성 공급자 보상을 어떻게 청구할 수 있습니까?

유동성 공급자 보상은 [dYdX API](https://docs.dydx.exchange/)에 표시됩니다. 거버넌스 사용자 인터페이스에 나타나지는 않지만, 각 에폭이 끝날 때마다 [여기](https://dydx.community/dashboard)에서 거버넌스를 통해 청구할 수 있습니다.

### 청구된 DYDX 유동성 공급자 보상을 언제 인출하고 이체할 수 있습니까?

거래 보상을 통해 획득한 DYDX 토큰은 각 에폭이 끝나고 `7일` (**대기** 기간) 이후 이체할 수 있습니다.

### 양면 뎁스, 매수-매도 호가 스프레드 및 업타임을 정의하고 측정하는 방법은 무엇입니까?

**양면 뎁스**

양면 유동성 공급자는 특정 시장에 대해 매수 및 매도 호가를 제시하며 dYdX에서 양면 시장의 호가를 적극적으로 제시하는 회사 또는 개인입니다. 이들은 전반적으로 탈중앙화 거래소에 유동성을 제공합니다.

예를 들어, BTC-USD 시장의 마켓 메이커는 $30,000~$30,100, 10x50의 호가를 제시할 수 있습니다. 즉, $30,000에 10 BTC를 입찰\(매수\)하고 $30,100에 50 BTC를 제공\(매도\)한다는 의미입니다. 그러면 다른 시장 참가자는 마켓 메이커로부터 $30,100에 매수\(매도 호가 수락\)하거나 $30,000에 매도\(매수 호가 수락\)할 수 있습니다.

유동성 공급자는 주어진 시장에서 매수 및 매도 호가를 모두 제시할 수 있는 능력에 따라 평가됩니다. 한 방향으로만 호가를 제시\(매수 호가 또는 매도 호가만 제시\)하는 유동성 공급자는 최소\(\) 기능으로 인해 보상을 받을 수 없습니다.

**미드마켓 스프레드**

유동성의 한 가지 일반적인 척도는 매수-매도 호가 스프레드입니다. 시장 내 최고 매수 호가\(구매 주문\) 및 최저 매도 호가\(판매 주문\) 간의 스프레드입니다. 매수 및 매도 호가의 차이인 스프레드는 트레이딩의 주요 거래 비용\(외부 수수료\)으로, 매수 호가와 매도 호가로 주문을 처리하여 유동성 공급자가 징수합니다. 스프레드는 사용자에게 즉시 거래 비용을 측정합니다.

미드마켓 스프레드는 시장의 중간 지점을 차지합니다. 이 공식을 통해 각 시장에 대한 MinDepth 금액 이하의 주문 또한 제외됩니다.

예를 들어 BTC-USD에 대한 유동성 공급자의 매수 호가가 $30,000이고 매도 호가가 $30,100인 경우 매수-매도 호가 스프레드는 $100입니다. 미드마켓 가격은 $30,050이며 미드마켓 스프레드는 $50입니다.

**업타임**

유동성 공급자의 업타임은 시장에 매우 중요하며, 특히 변동성이 높은 기간에 더 그렇습니다. 5의 지수를 $$Uptime_{epoch}$$에 $$Q_{FINAL}$$에 대한 입력으로 적용하면 해당 보상은 양면 유동성을 일관되게 유지한 유동성 공급자를 향해 치우칩니다. 즉, 시간의 99%를 업타임으로 제공하는 유동성 공급자는 90%의 업타임을 제공하는 마켓 메이커보다 기하급수적으로 가치가 높아집니다.

업타임은 주어진 시장에서 유동성을 제공하는 주문이 존재하는 시간의 비율로 정의되며 분 단위로 측정됩니다\(무작위 샘플링 사용\). 업타임에서 거래소가 중단되는 시간은 제외됩니다. 교환이 느리거나 주문을 수락하지 않는 엣지 사례가 발생할 수 있습니다 \(그러나 사용 불능은 아닙니다\). 이러한 경우 위 내용은 적용되지 않을 수 있습니다\(그러나 버그로 간주될 수 있으며 모든 마켓 메이커는 사용 불능과 유사한 영향을 받을 수 있습니다\).

### 시장당 최대 스프레드를 어떻게 정의합니까?

$$Q_{BID}$$ 또는 $$Q_{ASK}$$은(는) 스프레드가 주어진 시장의 $$MaxSpread$$보다 높을 때 생성됩니다.

초기 최대 스프레드는 다음과 같습니다.

| 시장 | 최대 스프레드 대 미드마켓\(매수 및 매도 호가\) |
| :--- | :--- |
| BTC-USD | 20 bps |
| ETH-USD | 20 bps |
| 기타 퍼페추얼 시장 | 40 bps |

### 시장당 최소 크기를 어떻게 정의합니까?

$$Q_{BID}$$ 또는 $$Q_{ASK}$$은(는) 크기가 주어진 시장의 $$MinSize$$보다 낮으면 생성됩니다.

초기 최소 크기는 다음과 같습니다.

| **시장** | **최소 크기\(매수 및 매도 호가\)** |
| :--- | :--- |
| BTC-USD | $5000 |
| ETH-USD | $5000 |
| 기타 퍼페추얼 시장 | $1000 |

