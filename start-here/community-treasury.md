---
description: 커뮤니티 트레저리에 대한 개요
---

# 트레저리

초기 토큰 공급량(`50,000,000DYDX`)의 `5.00%`는 기여자 보조금, 커뮤니티 이니셔티브, 유동성 채굴 및 기타 프로그램을 통해 지속적으로 할당되도록 커뮤니티 트레저리에 분배됩니다.

**목표**

* dYdX의 성장을 주도하는 프로그램 및 이니셔티브에 자금을 지원합니다.
* 커뮤니티 NFT, 해커톤, 분석 대시보드, 밈, 스웨그, 타사 도구, 번역 및 기타 프로젝트에 자금을 제공하기 위한 그랜트 프로그램을 개발합니다.
* 최고 수준의 거버넌스 시스템을 개발하고 강력한 거버넌스를 장려합니다.

## 개요

커뮤니티 금고는 DYDX를 보유하여 보조금, 신규 유동성 채굴 풀 또는 기타 프로그램에 대해 사용할지 결정할 수 있습니다. DYDX는 5년간 지속되는 기준으로 커뮤니티 금고에 귀속됩니다. 커뮤니티 금고에서 모든 DYDX를 지출하려면 거버넌스 투표를 거쳐야 합니다.

5년 후에 거버넌스가 영구 인플레이션(연간 최대 `2%`의 인플레이션 수준)을 시행하기로 결정하면, 새롭게 발행되는 DYDX는 커뮤니티 트레저리에서 사용할 수 있습니다.

## FAQ

### DYDX는 커뮤니티 트레저리에 어떻게 귀속됩니까?

1초마다 커뮤니티 트레저리 베스터(자세한 내용은 [여기](https://docs.dydx.community/dydx-governance/resources/technical-overview#governance-architecture-overview)를 참조)가 [`0.316924262732`](tel:03169242627)DYDX를 커뮤니티 트레저리에 할당합니다. DYDX가 귀속되면 커뮤니티 트레저리 베스터에서 `claim` 함수를 호출하여 귀속된 DYDX를 커뮤니티 트레저리로 이전시킬 수 있습니다. 모든 dYdX 커뮤니티 회원이 Etherscan의 [여기](https://etherscan.io/address/0x08a90Fe0741B7DeF03fB290cc7B273F1855767D8#writeContract)에서 `claim` 함수를 호출하여(가스 수수료를 위해 일부 ETH 필요) 커뮤니티 트레저리 베스터로부터 커뮤니티 트레저리로 귀속된 DYDX를 이동시킬 수 있습니다.

<figure><img src="../.gitbook/assets/claim-function-CT-vester.png" alt=""><figcaption></figcaption></figure>

### 커뮤니티 트레저리의 귀속 잔액은 무엇입니까?

dYdX 커뮤니티 회원은 [여기](https://dydx.shippooor.xyz/)에서 커뮤니티 트레저리의 귀속 잔액을 볼 수 있습니다. \
\
또한, dYdX Foundation은 각 에폭 말에 [에폭 검토](https://dydx.foundation/blog)를 통해 커뮤니티 트레저리의 귀속 잔액을 공표합니다. 커뮤니티 트레저리의 귀속 DYDX 외에도 dYdX 커뮤니티는 (1) 거래 보상을 25% 낮추고(958,904 DYDX) (2) USDC 스테이킹 보상을 0으로 설정(383,562 DYDX)하며 (3) DYDX 스테이킹 보상을 0으로 설정(383,562 DYDX)하기로 결정한 투표의 결과로 보상 트레저리에 발생한 DYDX에 접근할 수 있습니다. 에폭 17부터 1,726,028 DYDX는 각 에폭 보상 트레저리에 누적되며 [거버넌스 투표](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters)를 통해 dYdX 커뮤니티에서 사용할 수 있습니다.

### 커뮤니티 트레저리에서 DYDX 토큰을 지출할 제안은 누가 제출할 수 있습니까?

충분한 제안권을 보유한 사용자는 누구든 제안을 제출할 수 있습니다. 커뮤니티 금고의 DYDX를 지출하려면 거버넌스 투표를 거쳐야 합니다. 제안을 제출하려면 [DIP 제안 수명 주기](../voting-and-governance/dip-proposal-lifecycle.md)에 명시된 대로 dYdX 개선 제안(DIP)을 제출하시기 바랍니다.

### 커뮤니티 트레저리에서 자금을 지출할 제안 작성은 어떻게 할 수 있습니까?

Reverie는 5M DYDX 이상([단기 타임락 투표](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-process#short-timelock-executor)에 대한 [계획안 임계값](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters#timelock-parameters))의 계획안 권한을 가진 dYdX 커뮤니티 구성원이 커뮤니티 트레저리에서 목적지 주소로 DYDX를 전송하는 계획안을 작성하는 방법에 대한 포괄적이고 기술적인 단계별 가이드를 작성했습니다. 기술 가이드에 액세스하려면 [여기](https://app.gitbook.com/o/-MeNgGQU0ucT2xo4s8-T/s/-MeNfSkgj48hU0q8Zbjn/\~/changes/EyisuFjLIyJ7K9RzaTfJ/technical-guide-on-building-a-dydx-community-treasury-spending-proposal)를 클릭하십시오.

### 커뮤니티 트레저리에 어떤 유형의 제안을 제출할 수 있습니까?

커뮤니티 관리 금고는 가능성의 세계를 열어 줍니다. 우리는 dYdX Layer 2 프로토콜의 생태계 성장을 촉진할 수 있는 생태계 보조금을 포함하는 다양한 실험 및 이니셔티브를 보고 싶습니다.
