---
description: >-
  마켓 메이커의 온보딩을 쉽게 만들기 위해 dYdX 팀은 이 가이드를 만들었습니다. 모든 통합 단계를 시작하기 전에 문서 전체를 읽으시기 바랍니다.
---

# 마켓 메이커 온보딩

## dYdX 추천 마켓 메이커 온보딩 순서:

1. 선호하는 이더리움 지갑을 dYdX L2 무기한 프로토콜에 연결하세요.
2. 무기한 계정에 USDC를 입금합니다.
3. 레이어 2에서 계정을 식별하고 브라우저에 로컬로 저장되는 STARK 키를 생성해야 합니다. Stark 키는 dYdX 사용자를 이더리움 계정 주소에 연결하므로 사용자는 먼저 Stark 키와 이더리움 키의 연결 고리에 대해 서명을 요청해야 하며, 다른 작업을 수행하기 전에 Stark 키를 dYdX의 스마트 계약에 등록해야 합니다. 'Stark 키 생성' 을 클릭하고 거래에 서명하세요. 서명은 무료이며 트랜잭션을 전송하지 않습니다. Stark 키는 귀하의 지갑으로 언제든지 복구할 수 있습니다.

또한, 프로그래밍 방식 트레이더는 다음 방법을 사용하여 Stark 키 쌍을 도출할 수 있습니다.

```
key_pair_with_y_coordinate = client.onboarding.derive_stark_key(
  # Optional if eth_private_key or web3.eth.defaultAccount was provided.
  ethereum_address='ethereumAddress',
)
```

STARK 키에 대한 자세한 내용을 여기를 참조하세요.

4\. 다음으로는 이더리움 서명 또는 웹 3 공급자를 필요로 하는 API 키가 필요합니다. 참고로 이더리움 서명은 API 키의 온보딩 및 관리에만 필요하며 거래에는 필요하지 않습니다. STARK 키 서명은 거래에 필요합니다. API 키는 다음 기능을 사용하여 등록 및 획득할 수 있습니다.

_등록:_

```
api_key_response = client.api_keys.create_api_key(
# Optional if eth_private_key or web3.eth.defaultAccount was provided.
ethereum_address='0x0123...',
)
```

_획득:_

```
api_keys = client.private.get_api_keys()
```

_대안(3. 및 4.)_, 개인의 키가 온라인 상태가 되기를 원치 않을 경우, 다음 단계를 통해 STARK 키를 안전하게 생성하여 필요한 자격 증명을 얻을 수 있습니다.

a. dYdX 무기한 거래소에서 웹 브라우저의 아무 곳이나 오른쪽 클릭하여 '검사'를 선택하여 '개발자 도구'를 엽니다

b. 애플리케이션 > 로컬 저장소> https://trade.dydx.exchange로 이동하세요

c. STARK\_KEY\_PAIRS를 선택하고 지갑 주소 옆의 드롭다운 메뉴를 클릭하여 Stark 개인 키를 확인하세요

d. API\_KEY\_PAIRS를 선택하고 지갑 주소 옆의 드롭다운 메뉴를 클릭하여 API 키, 비밀번호 및 암호 문구를 확인하세요
