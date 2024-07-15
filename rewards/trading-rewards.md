---
description: 거래 보상 프로그램 개요
---

#

토큰 공급량의 `14.5`**`%`**(`144,693,506 $ethDYDX`)가 dYdX v3상에서 거래하는 사용자에게 지급된 수수료를 기준으로 분배하여 할당됩니다. 초기에는 토큰 공급량의 `25.0%`(`250,000,000$ethDYDX`)가 거래 보상으로 할당되었습니다.

* [DIP 16](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-16.md)에서 dYdX 커뮤니티는 거래 보상을 25.0% 감소시키기로 [결정했습니다](https://dydx.community/dashboard/proposal/8). 그 결과, 거래 보상을 위한 할당은 `25.0%`에서 `20.2%`로 감소했습니다.
* [DIP 20](https://dydx.community/dashboard/proposal/11)에서 dYdX 커뮤니티는 거래 보상을 45.0% 더 감소시키기로 [결정했습니다](https://dydx.community/dashboard/proposal/11). 그 결과, 거래 보상을 위한 할당은 `20.2%`에서 `14.5%`로 감소했습니다.
*   [DIP 29](https://dydx.community/dashboard/proposal/16)에서 dYdX 커뮤니티는 dYdX v3의 에폭 30-32에 해당하는 거래 보상을 ⅓ 줄이기로 [결정했으며](https://dydx.community/dashboard/proposal/16) 해당 값은 다음과 같습니다.

    * 에폭 30: 1,054,795 $ethDYDX
    * 에폭 31: 527,398 $ethDYDX
    * 에폭 32: 0 $ethDYDX

    DIP 29에서 dYdX 커뮤니티는 거래 보상 할당량의 나머지를 거래 보상을 위한 dYdX 체인으로 마이그레이션하기로 결정했습니다.

특정 에폭에서 분배된 거래 보상은 3,835,616$ethDYDX에서 다음과 같이 감소했거나 감소할 것입니다.

* 에폭 15에서 2,876,712$ethDYDX,
* 에폭 21에서 1,582,192$ethDYDX,
* 에폭 30에서 1,054,795 $ethDYDX,
* 에폭 31에서 527,398$ethDYDX,
* 에폭 32 이상에서 0$ethDYDX.

에폭 31 이후에는 dYdX v3에 대한 거래 보상이 없습니다. dYdX v3의 [DIP 29](https://dydx.community/dashboard/proposal/16)와 dYdX Chain의 [제안 2](https://www.mintscan.io/dydx/proposals/2)에서 dYdX 커뮤니티는 dYdX v3 [보상 Treasury Vester의](https://etherscan.io/address/0xb9431e19b29b952d9358025f680077c3fd37292f) 미획득 $ethDYDX의 나머지 금액을 dYdX [체인 보상 Treasury Vester(`dydx1wxje320an3karyc6mjw4zghs300dmrjkwn7xtk)`](https://www.mintscan.io/dydx/address/dydx1wxje320an3karyc6mjw4zghs300dmrjkwn7xtk)에 크레딧으로 투표했고, dYdX Chain의 거버넌스 승인을 조건으로 dYdX Chain에서 거래 보상으로 분배했습니다.

**목표**

* 모든 트레이더가 dYdX v3를 이용하도록 장려합니다.
* 시장 유동성 및 전반적인 상품 사용을 가속화합니다.

## **개요**

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>특정 에폭에서 지불한 수수료 및 예상 보상</p></figcaption></figure>

$ethDYDX는 dYdX v3상에서 지급된 수수료를 기준으로 트레이더들에게 분배되었습니다. $ethDYDX는 5년 동안 28일 에폭 기준으로 배포되었으며, 어떠한 페스팅 또는 락업도 적용되지 않았습니다.

[DIP 29](https://dydx.community/dashboard/proposal/16)에서 dYdX 커뮤니티는 dYdX v3의 에폭 30-32에 해당하는 거래 보상을 ⅓ 줄이기로 [결정했으며](https://dydx.community/dashboard/proposal/16) 해당 값은 다음과 같습니다.

* 에폭 30: 1,054,795 $ethDYDX
* 에폭 31: 527,398 $ethDYDX
* 에폭 32 및 나머지 모든 에폭: 0$ethDYDX



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

##

거래 보상을 통해 획득한 $ethDYDX는 각 에폭이 종료되면 양도할 수 있습니다. $ethDYDX 토큰 보유자는 $ethDYDX 토큰을 청구하려면 에폭 종료 후 약 `7일`(**대기 기간**) 동안 기다려야 합니다.

7일의 대기 기간 후 모든 커뮤니티 회원은 [머클 배포자 계약](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract)의 `updateRoot` 파라미터에서 `Write` 함수를 호출하여 $ethDYDX 보상을 클레임 가능한 상태로 만들 수 있습니다.

단계:

1. Etherscan의 [머클 배포자 계약](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract)에서 `계약` 탭을 클릭하고 `프록시로 작성`을 선택합니다.
2. `Web3에 연결` 버튼을 클릭하고 Web3 지갑을 연결하십시오.

<figure><img src="../.gitbook/assets/merkle-distributor-contract.jpeg" alt=""><figcaption></figcaption></figure>

3\. `updateRoot` 파라미터까지 아래로 스크롤한 다음 `작성` 버튼을 클릭합니다.

<figure><img src="../.gitbook/assets/updateRoot-claiming.jpeg" alt=""><figcaption></figcaption></figure>



* 7일의 대기 기간이 여전히 진행 중인 경우, 또는
* 커뮤니티 회원이 이미 [머클 배포자 계약](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract)에서 `updateRoot` 파라미터를 성공적으로 호출한 경우

거래가 완료되면 트레이더는 [여기](https://dydx.community/dashboard)에서 거래 보상을 청구할 수 있습니다. 사용자가 $ethDYDX를 클레임하려면 `청구` 클릭하고 거래에 서명한 후 가스 수수료를 지불해야 합니다.

![보상 포트폴리오 개요](../.gitbook/assets/1-portfolio-overview-rewards.png)

## FAQ

<details>

<summary>거래 보상을 받을 수 있는 자격은 무엇입니까?</summary>

dYdX v3의 모든 트레이더는 $ethDYDX를 거래 보상으로 받을 수 있었습니다.

dYdX Trading Inc.의 [이용약관](https://dydx.exchange/terms)에 따라 미국 또는 제한 지역의 트레이더는 dYdX v3를 이용할 수 없습니다.

</details>

<details>

<summary>거래 보상 프로그램에서 $ethDYDX를 얼마나 획득했나요?</summary>

현재 에폭에 사용자는 사용자의 거래 데이터가 있는 [**trade.dydx.exchange/portfolio/rewards**](https://trade.dydx.exchange/portfolio/rewards)에서 지불한 수수료와 예상 거래 보상을 확인할 수 있습니다.

지난 에폭의 보상은 [**dydx.community/history/rewards**](https://dydx.community/history/rewards)에서 확인하실 수 있습니다**.**

</details>
