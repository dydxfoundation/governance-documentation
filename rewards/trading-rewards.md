---
description: 거래 보상 프로그램 개요
---

# 거래 보상

토큰 공급량의 `20.2`**`%` ** (`201,883,560 $DYDX`)는 지불된 수수료를 기준으로 dYdX 레이어 2 프로토콜에서 거래하는 사용자에게 분배되도록 할당됩니다. 처음에는 토큰 공급량의 `25.0%`(`250,000,000 DYDX`)가 거래 보상을 위해 할당되었습니다. [DIP 16](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-16.md)에서 dYdX 커뮤니티는 거래 보상을 25.0% 줄이는 것을 지지하는 [투표를 했습니다](https://dydx.community/dashboard/proposal/8). 그 결과, 거래 보상을 위한 할당은 `25.0%`에서 `20.2%`로 감소했습니다. 주어진 에폭에 배포된 거래 보상은 에폭 15에서 3,835,616 DYDX에서 2,876,712 DYDX로 감소했습니다.

**목표**

* dYdX Layer 2 프로토콜을 사용하도록 모든 트레이더를 장려합니다.
* 시장 유동성 및 전반적인 상품 사용을 가속화합니다.

## **개요**

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>특정 에폭에서 지불한 수수료 및 예상 보상</p></figcaption></figure>

$DYDX는 dYdX 레이어 2 프로토콜에서 지불한 수수료를 기반으로 거래자에게 배포됩니다. $DYDX는 5년 동안 28일 순환을 기준으로 배포될 예정이며 모든 베스팅 또는 락업에서 제외됩니다. 2,876,712 $DYDX는 에폭당 배포됩니다.

커뮤니티가 투표를 통해 3,835,616 $DYDX에서 2,876,712 $DYDX로 거래 보상을 25% 낮추기로 결정함에 따라 보상 트레저리에 축적된 잔여 958,904 $DYDX는 dYdX 커뮤니티에서 [거버넌스 투표](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters)를 통해 사용/관리할 수 있습니다.

<figure><img src="../.gitbook/assets/1-trading-rewards-formula-new.png" alt=""><figcaption></figcaption></figure>

$$ r=R\times \frac{w}{\sum\limits _{n} w_{n}} \ \ ,n=1,2...k $$

| 기간 | 정의 |
| ---------------------------- | ----------------------------------------------------------------------- |
| r | 특정 트레이더에 대한 보상 |
| R | 에폭 동안 풀에 있는 모든 트레이더 간에 분할될 총 보상 |
| f | 이 에폭에서 트레이더가 지불하는 총 수수료입니다. |
| 주 | 개별 트레이더 점수입니다. |
| $${\sum\limits _{n} w_{n}}$$ | 모든 트레이더 점수의 합계입니다. |
| k | 이 에폭 내 총 트레이더 수 |

[DIP-13](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-13.md)의 투표에서 dYdX 커뮤니티는 주어진 에폭에 거래자가 지불한 총 수수료에 기반하도록 공식을 단순화하기로 결정했습니다.

## FAQ

### 거래 보상을 받을 수 있는 자격은 무엇입니까?

dYdX 레이어 2 프로토콜의 모든 트레이더는 거래 보상으로 $DYDX를 받을 수 있습니다.

dYdX 레이어 2 프로토콜은 dYdX Trading Inc.의 [이용 약관](https://dydx.exchange/terms)에 정의된 바와 같이 미국 또는 제한 지역의 유동성 공급자가 이용할 수 없습니다.

### 거래 보상 프로그램에서 DYDX가 얼마나 적립되었습니까?

현재 에폭에 사용자는 사용자의 거래 데이터가 있는 [**trade.dydx.exchange/portfolio/rewards**](https://trade.dydx.exchange/portfolio/rewards)에서 지불한 수수료와 예상 거래 보상을 확인할 수 있습니다.

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>특정 에폭에서 지불한 수수료 및 예상 보상</p></figcaption></figure>

지난 에폭의 보상은 [**dydx.community/history/rewards**](https://dydx.community/history/rewards)에서 확인하실 수 있습니다**.**

### 거래 보상을 어떻게 클레임할 수 있습니까? 획득한 $DYDX를 언제 인출하고 양도할 수 있습니까?

거래 보상을 통해 획득한 $DYDX 토큰은 각 에폭이 종료될 때 양도할 수 있습니다. $DYDX 토큰 보유자가 $DYDX 토큰을 클레임하려면 에폭이 종료되고 약 `7일`(**대기 기간**)을 기다려야 합니다.

7일의 대기 기간 후 커뮤니티 회원은 [머클 배포자 계약](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract)의 `updateRoot` 파라미터에서 `Write` 함수를 호출하여 DYDX 보상을 청구 가능한 상태로 만들 수 있습니다.

단계:

1. Etherscan의 [머클 배포자 계약](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract)에서 `계약` 탭을 클릭하고 `프록시로 작성`을 선택합니다.
2. `Web3에 연결` 버튼을 클릭하고 Web3 지갑을 연결하십시오.

<figure><img src="../.gitbook/assets/merkle-distributor-contract.jpeg" alt=""><figcaption></figcaption></figure>

3\. `updateRoot` 파라미터까지 아래로 스크롤한 다음 `작성` 버튼을 클릭합니다.

<figure><img src="../.gitbook/assets/updateRoot-claiming.jpeg" alt=""><figcaption></figcaption></figure>

**이 거래에는 가스 수수료를 위해 일부 ETH가 필요하며 다음의 경우 거래는 일어나지 않습니다.**

* 7일의 대기 기간이 여전히 진행 중인 경우, 또는
* 커뮤니티 회원이 이미 [머클 배포자 계약](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract)에서 `updateRoot` 파라미터를 성공적으로 호출한 경우

거래가 완료되면 트레이더는 [여기](https://dydx.community/dashboard)에서 거래 보상을 청구할 수 있습니다. 사용자가 $DYDX를 청구하려면 `청구`를 클릭하고 거래에 서명하여 가스 수수료를 지불해야 합니다.

![보상 포트폴리오 개요](../.gitbook/assets/1-portfolio-overview-rewards.png)
