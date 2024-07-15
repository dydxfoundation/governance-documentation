---
description: 커뮤니티 트레저리에 대한 개요
---

#

토큰 공급량의 **`26.1%`** (`261,133,225 $ethDYDX`)가 dYdX 커뮤니티의 커뮤니티 금고에 할당되므로 기여자 보조금, 커뮤니티 이니셔티브, 유동성 채굴 및 기타 프로그램에 지속적으로 사용할 수 있습니다. 초기에는 토큰 공급량의 `5.0%`(`50,000,000$ethDYDX`)가 커뮤니티 금고에 [할당되었으며](https://docs.dydx.community/dydx-governance/start-here/dydx-allocations), 에폭마다 766,703$ethDYDX가 커뮤니티 금고에 귀속되었습니다. 현재 3,787,251$ethDYDX가 커뮤니티 금고에 귀속되며, 이는 여러 거버넌스의 제안으로 인해 각 에폭마다 dYdX 커뮤니티에서 이용 가능한 $ethDYDX 액수가 3,020,548$ethDYDX로 증가했기 때문입니다.

* [DIP 14](https://dydx.community/dashboard/proposal/7) - USDC 스테이킹 보상을 0으로 설정(에폭당 383,562$ethDYDX),
* [DIP 16](https://dydx.community/dashboard/proposal/8) - 거래 보상 25% 감소(에폭당 958,904 $ethDYDX),
* [DIP 17](https://dydx.community/dashboard/proposal/9) - $DYDX 스테이킹에 대한 보상을 0으로 설정(에폭당 383,562$ethDYDX),
* [DIP 20](https://dydx.community/dashboard/proposal/11) - 거래 보상을 45%까지 추가 감소(에폭당 1,294,520$ethDYDX),
* [DIP 24](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-24.md) - 유동성 공급자 보상 50% 감소(에폭당 575,342$ethDYDX).
*   [DIP 29](https://dydx.community/dashboard/proposal/16) - dYdX v3의 에폭 30-32에서 다음 값으로 유동성 공급자 보상을 ⅓ 감소:

    * 에폭 30: 383,562 $ethDYDX
    * 에폭 31: 191,781 $ethDYDX
    * 에폭 32: 0 $ethDYDX

    에폭 31 이후에는 dYdX v3에 대한 거래 보상이 없습니다. DIP 29에서 dYdX 커뮤니티는 dYdX v3의 에폭 30-32에 해당하는 거래 보상을 ⅓ 줄이기로 결정했지만, 거래 보상 할당량의 나머지는 거래 보상을 위해 dYdX 체인으로 마이그레이션되었습니다.

2023년 11월 18일, dYdX 커뮤니티는 이더리움에서 dYdX 체인으로 커뮤니티 트레저리에 누적된 ethDYDX 잔액을 연결하기로 [결정했습니다](https://dydx.community/dashboard/proposal/16). 브리징 이후, dYdX 커뮤니티는 dYdX 체인에서 거버넌스 투표를 통해 DYDX를 사용할 수 있습니다.



**목표**

* dYdX의 성장을 주도하는 프로그램 및 이니셔티브에 자금을 지원합니다.
* 커뮤니티 NFT, 해커톤, 분석 대시보드, 밈, 스웨그, 타사 도구, 번역 및 기타 프로젝트에 자금을 제공하기 위한 그랜트 프로그램을 개발합니다.
* 최고 수준의 거버넌스 시스템을 개발하고 강력한 거버넌스를 장려합니다.

## 개요

커뮤니티 금고는 $ethDYDX를 보유하며, $ethDYDX 보유자들이 이를 보조금, 새로운 유동성 채굴 풀 또는 기타 프로그램을 위해 사용할 것인지를 결정합니다. $ethDYDX는 5년 동안 지속적으로 커뮤니티 금고에 귀속됩니다. 커뮤니티 금고의 ethDYDX를 지출하려면 거버넌스 투표를 거쳐야 합니다.

5년 후에 거버넌스가 영구 인플레이션(연간 최대 `2%`의 인플레이션 수준)을 시행하기로 결정하면, 새롭게 발행되는 $ethDYDX를 커뮤니티 금고에서 사용할 수 있습니다.

## FAQ

<details>

<summary>$ethDYDX는 어떠한 방식으로 커뮤니티 금고에 귀속되나요?</summary>

이전에는 커뮤니티 트레저리 베스터(자세한 내용은 [여기](https://docs.dydx.community/dydx-governance/resources/technical-overview#governance-architecture-overview)를 참조)가 매 초마다 커뮤니티 트레저리에 [`0.3169242627`](tel:03169242627) $ethDYDX를 부여했습니다. $ethDYDX가 귀속되면 커뮤니티 트레저리 베스터에서 `claim` 함수를 호출하여 귀속된 $ethDYDX를 커뮤니티 트레저리로 이전합니다. dYdX 커뮤니티 회원이라면 누구나 [여기에서](https://etherscan.io/address/0x08a90Fe0741B7DeF03fB290cc7B273F1855767D8#writeContract) Etherscan의 `claim` 함수를 호출할 수 있으며(가스 수수료를 위해 ETH 필요), 이로써 커뮤니티 트레저리 베스터를 통해 귀속된 $DYDX를 커뮤니티 금고로 이동시킬 수 있습니다.

dYdX 커뮤니티의 커뮤니티 재무 관리에 대한 자세한 내용은 dYdX 재단의 [이용 약관](https://dydx.foundation/terms)을 참조하십시오.

![](../.gitbook/assets/image.png)

</details>

