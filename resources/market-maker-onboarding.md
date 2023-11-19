---
description: >-
  dYdXチームではマーケットメーカーのオンボーディングを容易にするために、このガイドラインを作成しました。統合ステップを開始する前に、ドキュメント全体をお読みください。
---

# マーケットメーカーのオンボーディング

## dYdXが推奨するマーケットメーカーのオンボーディングフロー：

1. 選択したイーサリアムウォレットをdYdX L2パーペチュアルプロトコルに接続してください。
2. パーペチュアル口座に$USDCを入金します。
3. STARKキーを生成する必要があります。これはレイヤー2で口座を識別し、ブラウザでローカルに保存されます。STARKキーではdYdXユーザーとイーサリアム口座アドレスを関連付けています。ユーザーは最初にイーサリアムキーとSTARKキーとのリンク署名リクエストを行い、その他のオペレーションが実行される前にdYdXのスマートコントラクトにSTARKキーを登録する必要があります。「STARKキーを生成」をクリックし、トランザクションに署名します。署名は無料であり、トランザクションを伴いません。STARKキーはお客様のウォレットでいつでも再作成できます。

また、プログラマティックトレーダーは以下の方法でSTARKキーペアを取得する場合があります。

```
key_pair_with_y_coordinate = client.onboarding.derive_stark_key(
  # Optional if eth_private_key or web3.eth.defaultAccount was provided.
  ethereum_address='ethereumAddress',
)
```

STARKキーの詳細についてはこちらをご覧ください。

4\.次に、APIキーが必要になりますが、これはイーサリアム署名が必要であるか、またはWeb3プロバイダーを介して取得しなければなりません。注：イーサリアム署名はAPIキーのオンボーディングおよび管理にのみ必要であり、取引には必要ありません。取引にはSTARKキーの署名が必要です。APIキーは以下の関数を使用して登録、入手できます。

_登録：_

```
api_key_response = client.api_keys.create_api_key(
# Optional if eth_private_key or web3.eth.defaultAccount was provided.
ethereum_address='0x0123...',
)
```

_入手：_

```
api_keys = client.private.get_api_keys()
```

_代替手段（3.および4.）：_秘密鍵をオンラインで利用したくない場合、以下の手順でSTARKキーを安全に生成して必要な資金を入手できます。

a. dYdXパーペチュアル取引所からは、ウェブブラウザ内の任意の場所を右クリックし、開発者ツールをオープンする検査を選択してください。

b. アプリケーション > ローカルストレージ > https://trade.dydx.exchange

c. STARK\_KEY\_PAIRSを選択し、ウォレットアドレスの横にあるドロップダウンをクリックして、STARK秘密キーを取得します。

d. API\_KEY\_PAIRSを選択し、ウォレットアドレスの横にあるドロップダウンをクリックしてAPIキー、共通鍵、パスフレーズを入手します。
