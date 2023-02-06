---
description: コミュニティトレジャリーの概要
---

# コミュニティ基金

`16.2`**···`%`** (`1億6,200万4,734 $DYDX`) のトークン供給は、dYdXコミュニティが貢献者の助成、コミュニティのイニシアチブ、流動性マイニング、その他のプログラムのために継続的に使用するために、****コミュニティ基金に割り当てられます。当初、コミュニティトレジャリーにトークン提供の`5.0％`（`5,000万 $DYDX`）が割り当てられ、76万6,703 $DYDXがエポックごとにコミュニティトレジャリーに帰属しました。現在、249万2,731 $DYDXがコミュニティトレジャリーに帰属していますが、これは3つのガバナンス提案により、dYdXコミュニティが利用できる$DYDXの金額がエポックごとに172万6,028 $DYDX増加したことによります。

* [DIP 14](https://dydx.community/dashboard/proposal/7) - USDCのステーキングの報酬を0に設定（エポックあたり383,562 $DYDX）、
* （2）[DIP 16](https://dydx.community/dashboard/proposal/8) -取引報酬を25％削減（エポックあたり958,904 $DYDX）、
* （3）[DIP 17](https://dydx.community/dashboard/proposal/9) - $DYDXのステーキングの報酬を0に設定（エポックあたり383,562 $DYDX）。



**目的**

* dYdXの成長を推進するプログラムやイニシアチブに資金を提供。
* コミュニティNFT、ハッカソン、分析ダッシュボード、ミーム、スワッグ、サードパーティ製のツール、翻訳、その他のプロジェクトに資金を提供する助成プログラムを構築。
* クラス最高のガバナンスシステムを構築し、強固なガバナンスを促進。

## 概要

コミュニティトレジャリーでは$DYDXを保有しており、$DYDXの保有者が助成金、新しい流動性マイニングプール、またはその他のプログラムのいずれに使用するかを決定します。$DYDXは、5年間にわたって継続的にコミュニティトレジャリーに属します。コミュニティトレジャリーから$DYDXを使用するには、ガバナンス投票が必要になります。

5年後、ガバナンスにより永続的なインフレ（年間`最大2％`）の実行が決定された場合、新たにできた$DYDXがコミュニティトレジャリーで利用可能になります。

## FAQ

### コミュニティ基金で$DYDXはどのように帰属していますか？

コミュニティ基金ベスター（詳細は[こちら](https://docs.dydx.community/dydx-governance/resources/technical-overview#governance-architecture-overview)）は、コミュニティ基金に毎秒[`0.3169242627`](tel:03169242627)$DYDXを付与します。$DYDXが付与されると、コミュニティ基金ベスターで`請求`関数を呼び出すことで、既得の$DYDXがコミュニティ基金に移動されます。dYdXコミュニティメンバーは[、ここから](https://etherscan.io/address/0x08a90Fe0741B7DeF03fB290cc7B273F1855767D8#writeContract)Etherscanで`請求`関数を呼び出して（Gas（ガス）代にETHが必要です）、既得の$DYDXをコミュニティ基金ベスターからコミュニティ基金に移動させることができます。

<figure><img src="../.gitbook/assets/claim-function-CT-vester.png" alt=""><figcaption></figcaption></figure>

### コミュニティトレジャリーの既得残高は？

dYdXコミュニティメンバーは、コミュニティトレジャリーの既得残高を[こちら](https://dydx.shippooor.xyz/)で確認できます。\\また、dYdX財団では、各エポックの終了時にコミュニティトレジャリーの既得残高を[エポックレビュー](https://dydx.foundation/blog)で公表しています。dYdXコミュニティはコミュニティ基金の既得$DYDXに加えて、（1）取引報酬を25％削減し（95万8,904$DYDX）、（2）USDCのステーキング報酬を0（38万3,562$DYDX）に設定し、（3）$DYDXのステーキング報酬を0（38万3,562$DYDX）に設定することに合意したため、それにより報酬基金に加算される$DYDXにもアクセスできます。エポック17から、1,726,028 $DYDXは各エポックで報酬基金に加算され、[ガバナンス投票](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters)でdYdXコミュニティによって使用できます。

### 誰がコミュニティ基金から$DYDXを使用する提案を提出できますか？

提案する実行力が十分にあればどのユーザーも提案を提出することができます。コミュニティトレジャリーから$DYDXを使用するには、ガバナンス投票が必要になります。提案を行う場合、dYdXの改善提案（DIP）の[提案ライフサイクル](../voting-and-governance/dip-proposal-lifecycle.md)に記載されているDIPを提出してください。

### コミュニティトレジャリーからの資金を使う提案を構築するにはどうすればよいですか？

Reverieは、5M dYdX（[短いタイムロック投票](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-process#short-timelock-executor)の[しきい値](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters#timelock-parameters)）以上のdYdXコミュニティメンバーが$DYDXをコミュニティ基金から宛先アドレスに$DYDXを送り込む提案を作成する方法について、包括的な、技術的、ステップバイステップガイドをまとめました。テクニカルガイドにアクセスするには、[こちら](https://app.gitbook.com/o/-MeNgGQU0ucT2xo4s8-T/s/-MeNfSkgj48hU0q8Zbjn/\~/changes/EyisuFjLIyJ7K9RzaTfJ/technical-guide-on-building-a-dydx-community-treasury-spending-proposal)をクリックしてください。

### コミュニティトレジャリーにはどのようなタイプの提案を提出することができますか？

コミュニティが管理する基金は、可能性を大きく広げます。dYdXレイヤ2プロトコルのエコシステムの成長を促進できるエコシステム助成金などにより、さまざまな試みやイニシアチブを期待できます。
