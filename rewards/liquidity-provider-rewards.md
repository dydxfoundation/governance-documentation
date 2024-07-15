---
description: 유동성 공급자 보상 프로그램 개요
---

#

처음 토큰 공급량의 **7.5%**(`75,000,000 $ethDYDX`)는 유동성 공급자에게 보상으로 돌아갑니다.

* [DIP 24](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-24.md)에서 dYdX 커뮤니티는 유동성 공급자 보상을 에폭당 `1,150,685$ethDYDX`에서 `575,343$ethDYDX`로 50% 감소하기로 [결정했습니다](https://dydx.community/dashboard/proposal/14). 그 결과, 유동성 공급자에게 할당되는 보상은 `7.5%`에서 `5.2%`로 감소했습니다.
*   [DIP 29](https://dydx.community/dashboard/proposal/16)에서 dYdX 커뮤니티는 dYdX v3의 에폭 30-32에서 다음 값으로 LP 보상을 ⅓ 줄이기로 [결정했습니다.](https://dydx.community/dashboard/proposal/16)

    * 에폭 30: 383,562 $ethDYDX
    * 에폭 31: 191,781 $ethDYDX
    * 에폭 32: 0 $ethDYDX

    에폭 31 이후에는 dYdX v3에 대한 LP 보상이 없습니다. 그 결과, 유동성 공급자에게 할당되는 보상은 `5.2%`에서 `3.2%`로 감소했습니다.

dYdX 체인에는 유동성 공급자 보상 분배가 없으므로 DIP 29의 dYdX 커뮤니티는 유동성 공급자 보상에 대한 나머지 할당을 dYdX 체인 커뮤니티 트레저리로 마이그레이션하기로 결정했습니다.

**목표**

* 양면 유동성을 개선하고 유동성 공급자를 프로그래밍 방식으로 보상합니다.

## **개요**

시장 유동성을 장려하기 위해 $ethDYDX는 dYdX v3에서의 시장 참여, 마켓 메이커 거래량, 양방향 호가, 스프레드(미드마켓 대비), 업타임을 보상하는 공식을 기반으로 유동성 공급자에게 배포될 것입니다.

[DIP 15](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-15.md)에서 dYdX 커뮤니티는 BTC/ETH 시장과 비 BTC/ETH 시장 간의 함수를 분할하여 LP 보상 공식을 개정하기로 결정했습니다. [DIP 19](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-19.md)에서 dYdX 커뮤니티는 0.05 stkDYDX 무게를 메이커 볼륨에 재할당하기로 결정했습니다.

획득하는 ethDYDX 양은 각 참가자의 $$Q_{FINAL}$$ ($$Q_{BTC}$$+​$$Q_{ETH}$$+$$Q_{non BTC/ETH}$$​)에 대한 상대적 지분으로 결정됩니다.

<figure><img src="../.gitbook/assets/Updated LP Rewards Formulas.png" alt=""><figcaption></figcaption></figure>

시장당 특정 **최소 호가**(규모) ($$최소호가$$) 미만의 주문은 제외되며, 시장의 특정 **최대 스프레드**(중간 시장 스프레드) ($$최대스프레드$$)를 초과하는 주문도 마찬가지로 제외됩니다.

분 단위 샘플링을 감안할 때, 각 에폭에는 28일 \* 24시간 \* 60분의 데이터 포인트(에포크당 총합 40,320 데이터 포인트)가 포함됩니다.

유동성 공급자는 에폭당 상대적 $$Q_{FINAL}$$ 비중에 따라 월간 보상을 받습니다.

위의 공식은 자세한 정보를 위해 아래의 단계별 계산으로 나뉩니다.

| _마켓 메이커 거래량_ | 에폭 동안의 총 마켓 메이커 거래량입니다. |
| --------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <img src="../.gitbook/assets/1-qbid-formula.png" alt="" data-size="original"> | <p></p>유동성 공급자가 BTC-USD 호가창에 여러 미결 입찰 주문(29,900달러에 1BTC, 29,580달러에 5BTC, 29,500달러에 10BTC)이 있으며 BTC는 현재 30,000달러(중간 시장 기준)라고 가정해 봅시다. 최소 호가는 5,000달러이며 중간 시장 대비 최대 스프레드는 200달러 또는 67 기준 포인트(200달러/30,000)라고 가정해 봅시다. BP는 1%의 100분의 1입니다.<br><p></p><span class="math">Q_{BID} = (1\ \times \left(\frac{$29,900}{$100/30000}\right)) + (5\ \times \left(\frac{$29,850}{$150/30000}\right))</span><p></p><br><span class="math">Q_{BID}</span>는 임의의 샘플링을 사용하여 1분마다 계산됩니다.<br> |
| <img src="../.gitbook/assets/1-qask-formula.png" alt="" data-size="original"> | <p></p>유동성 공급자가 BTC-USD 호가창에 여러 미결 매도 주문(30,100달러에 0.1BTC, 30,150달러에 5BTC, 30,175달러에 10BTC)가 있으며 BTC는 현재 30,000달러(중간 시장 기준)에 거래되고 있다고 가정해 봅시다. 최소 호가는 5,000달러이며 중간 시장 대비 최대 스프레드는 200달러 또는 67 기준 포인트(200달러/30,000)라고 가정해 봅시다. BP는 1%의 100분의 1입니다.<p></p><span class="math">Q_{ASK} = (5\ \times \left(\frac{$30,150}{$150/30000}\right)) + (10\ \times \left(\frac{$30,175}{$175/30000}\right))</span><p></p><br><span class="math">Q_{ASK}</span>는 임의의 간격으로 1분마다 계산됩니다. |
| <img src="../.gitbook/assets/1-qmin-formula.png" alt="" data-size="original"> | <p></p><span class="math">Q_{BID}</span>와 <span class="math">Q_{ASK}</span>의 최소 금액을 취하여 양방향 유동성을 보상합니다.<br><p></p>1분마다 계산합니다. |
| <img src="../.gitbook/assets/1-qpoech-formula.png" alt="" data-size="original"> | $$Q_{EPOCH}$$는 주어진 에폭의 모든 $$Q_{MIN}$$의 합계입니다. |
| <img src="../.gitbook/assets/1-q-uptime-epoch-formula.png" alt="" data-size="original"> | $$Uptime_{EPOCH}$$은 특정 마켓 메이커가 활동한 한 에폭 내 시간이며 명시된 주문 최소값(시장별로 하단에 명시)보다 큰 주문 규모와 명시된 최대 스프레드(시장별로 하단에 명시)보다 작은 스프레드로 매수 및 매도를 모두 호가합니다. |
| <img src="../.gitbook/assets/1-qfinal-epoch-formula.png" alt="" data-size="original"> | $$Q_{FINAL}$$는 $$Q_{EPOCH}$$를 정규화하여 가동 시간을 고려합니다 |

각 시장은 다르게 가중치를 부여할 자체 보상 풀을 보유할 것입니다. [DIP 15](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-15.md)에서 dYdX 커뮤니티는 BTC-USD 및 ETH-USDC의 총 보상 할당을 각각 10%로 줄이기로 투표했습니다. 각 시장에 적용되는 가중치의 세트는 다음과 같습니다.

| 시장 | 총 보상 풀의 할당 비율(%) |
| ----------------------- | ---------------------------------------------------------------- |
| BTC-USD | 10% |
| ETH-USD | 10% |
| 기타 퍼페추얼 시장 | ![](../.gitbook/assets/1-other-perpetual-markets-lp-weights.png) |

## FAQ

<details>

<summary>유동성 공급자 보상을 받을 자격이 있는 사람은 누구입니까?</summary>

이전 에폭에서 dYdX v3에 대한 메이커 거래량의 0.25%라는 최소치를 달성한 모든 유동성 공급자는 특정 에폭에서 ethDYDX를 보상으로 받을 수 있는 자격이 주어집니다.

dYdX Trading Inc.의 [이용약관](https://dydx.exchange/terms)에 따라 미국 또는 제한 지역의 유동성 공급자는 dYdX v3 이용이 불가능합니다.

</details>

<details>

<summary>유동성 공급자 프로그램에서 $ethDYDX를 얼마나 획득했나요?</summary>

특정 에폭에 유동성 공급자는 특정 페어의 시장에서 상대적 $Q_{SCORE}}$$을(를) 기준으로 수익률을 얻습니다. 각 페어은 거버넌스가 설정한 상대적 보상 금액을 갖추고 있습니다. 받은 ethDYDX의 예상 금액은 [LP 보상 대시보드](https://p.datadoghq.com/sb/dc160ddf0-b32271920202875868dc46be6b66cf87?tpl\_var\_Market=btc\&from\_ts=1661805073576\&to\_ts=1661891473576\&live=true)에 표시되며, 유동성 공급자, 상대적 $$Q_{SCORE}$$ 및 특정 페어에서 제공되는 보상 금액에 기반하여 결정될 수 있습니다.

</details>

<details>

<summary>유동성 공급자 보상을 어떻게 클레임할 수 있습니까?</summary>

유동성 공급자 보상은 [dYdX API](https://docs.dydx.exchange/)에 표시됩니다. 거버넌스 사용자 인터페이스에 나타나지는 않지만, 각 에폭이 끝날 때마다 [여기](https://dydx.community/dashboard)에서 거버넌스를 통해 클레임할 수 있습니다.

</details>

<details>

<summary>클레임된 $ethDYDX 유동성 공급자 보상을 언제 인출 및 이체할 수 있나요?</summary>

유동성 공급자 보상을 통해 보상받은 $ethDYDX 토큰은 초기 양도 제한 기간이 해제되면 클레임 및 양도 가능한 상태가 됩니다.

에폭 1부터 유동성 공급자 보상을 통해 보상받은 $ethDYDX 토큰은 각 에폭 종료 후 `7일`(**대기 기간**) 뒤에 클레임할 수 있습니다.

</details>

<details>

<summary>양면 뎁스, 매수-매도 호가 스프레드, 업타임은 어떻게 정의 및 측정됩니까?</summary>

* **양면 뎁스**



* **미드마켓 스프레드**



* **업타임**

유동성 공급자의 업타임은 시장에 매우 중요하며, 특히 변동성이 높은 기간에 더 그렇습니다. 5의 지수를 $$Uptime_{epoch}$$에 $$Q_{FINAL}$$에 대한 입력으로 적용하면 해당 보상은 양면 유동성을 일관되게 유지한 유동성 공급자를 향해 치우칩니다. 즉, 시간의 99%를 업타임으로 제공하는 유동성 공급자는 90%의 업타임을 제공하는 유동성 공급자보다 기하급수적으로 가치가 높아집니다.



</details>

<details>

<summary>시장당 최대 스프레드는 어떻게 정의됩니까?</summary>

$$Q_{BID}$$ 또는 $$Q_{ASK}$$은(는) 스프레드가 주어진 시장의 $$MaxSpread$$보다 높을 때 생성됩니다.

초기 최대 스프레드는 다음과 같습니다.

*
*
*

</details>

<details>

<summary>시장당 최소 뎁스(크기)는 어떻게 정의됩니까?</summary>

$$Q_{BID}$$ 또는 $$Q_{ASK}$$은(는) 크기가 주어진 시장의 $$MinDepth$$보다 낮으면 생성됩니다.

초기 최소 뎁스는 다음과 같습니다.

*
*
*

</details>

