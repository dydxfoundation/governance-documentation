---
description: 유동성 스테이킹 풀 개요
hidden: 진실
---

# 🔋 유동성 모듈

유동성 스테이킹 풀은 2022년 9월 29일부로 더 이상 활성화되지 않습니다. [DIP 14](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-14.md)에서 dYdX 커뮤니티는 유동성 스테이킹 풀 보상을 초당 0으로 설정하여 유동성 스테이킹 풀 및 차입 풀을 효과적으로 종료하기로 [결정했습니다](https://dydx.community/dashboard/proposal/7).

유동성 모듈 보상 할당에서 나머지 모든 ethDYDX는 dYdX 체인 커뮤니티 트레저리로 이전되었습니다.

dYdX 체인 커뮤니티 트레저리에 대한 자세한 내용은 여기에서 확인할 수 [있습니다](https://app.gitbook.com/s/7eKRye9zrZIr1Pp3Q3Mu/modules/community-treasury).

## **스테이킹** 개요

현재 유동성 스테이킹 풀에서 스테이킹된 $USDC는 보상을 받지 않고 있습니다.

## USDC 스테이킹 해제 및 인출

스테이커는 반드시 해당 에포크가 종료하기 최소 `3일`(**블랙아웃 기간**) 전에 USDC 인출을 요청해야 [**에포크**](../start-here/epochs.md) 종료 후 인출할 수 있습니다. 스테이커가 인출을 요청하지 않으면 스테이킹된 $USDC는 다음 에포크로 이월됩니다.

**블랙아웃 기간**에는 인출을 요청할 수 없습니다.

## FAQ

<details>

<summary>블랙아웃 기간이란 무엇입니까?</summary>

블랙아웃 기간은 사용자가 스테이킹된 $USDC의 인출을 요청할 수 없는 기간입니다. 블랙아웃 기간 동안에는 `requestWithdrawal` 기능을 호출할 수 없습니다. 처음 이 기간은 에포크의 마지막 `3일`로 구성됩니다. 28일마다 새로운 에폭이 시작됩니다. 즉, 사용자는 주어진 에폭이 종료되기 최대 `3일` 전에 다음 에폭에 대한 인출을 요청할 수 있습니다.

</details>

<details>

<summary>어떻게 스테이킹 풀에서 $USDC를 인출합니까? 시간이 얼마나 소요됩니까?</summary>

스테이커는 에포크가 종료되기 최소 `3일` 전에 $USDC 스테이킹을 해제해야 해당 에포크가 종료된 후 스테이커의 $USDC를 인출할 수 있습니다. 스테이커가 인출을 요청하지 않으면 스테이킹된 $USDC는 다음 에폭으로 롤오버됩니다.

$USDC를 인출하려면 사용자는 `requestWithdrawal` 기능을 호출하여 다음 에폭에 대한 $USDC 인출을 요청합니다. 현재 에포크 동안 사용자 자금은 스테이킹된 상태로 유지되며 인출할 수 없습니다. 다음 에포크가 시작될 때 자금은 "비활성" 상태가 되어 인출할 수 있게 됩니다.

다음 에포크에서 사용자는 `withdrawStake` 기능을 호출하여 비활성 $USDC를 특정 주소로 인출합니다. 사용자는 인출하려는 비활성화 자금의 양을 선택하거나, \`withdrawMaxStake\` 기능을 호출하여 모든 비활성 자금을 인출할 수 있습니다. `withdrawMaxStake` 기능은 eth\_call을 통해 최대값을 쿼리하고 `withdrawStake()`를 호출하는 것보다 가스 효율이 낮습니다.

유동성 풀에 대한 $USDC의 스테이킹을 해제하려면 다음 단계를 따르세요.

* [**https://dydx.community/dashboard/staking-pool/liquidity**](https://dydx.community/dashboard/staking-pool/liquidity)\*\*\*\*로 이동합니다.
* **"요청"을** 클릭합니다.
* 풀에서 인출을 요청하고 싶은 $USDC의 금액을 입력하고 '**인출 요청**'을 클릭합니다. $USDC 스테이킹을 해제하려면 가스 수수료를 지불해야 합니다.
* 현재 에포크가 종료되기 최소 `3일`(**언스테이킹 기간**) 전에 $USDC 스테이킹 해제를 요청한 스테이커는 다음 에포크를 시작할 때 $USDC를 인출할 수 있습니다.

</details>

###
