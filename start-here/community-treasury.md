---
description: コミュニティトレジャリーの概要
---

#

トークン供給の**`26.1％`**（`261,133,225$ethDYDX`）は、dYdXコミュニティがコントリビューター支援金、コミュニティイニシアチブ、流動性マイニング、およびその他のプログラムに継続的に使用するためにコミュニティトレジャリーに割り当てられます。当初、コミュニティトレジャリーにトークン供給の`5.0％`（`5000万$ethDYDX`）が[割り当てられ](https://docs.dydx.community/dydx-governance/start-here/dydx-allocations)、766,703$ethDYDXがエポックごとにコミュニティトレジャリーに帰属しました。現在、コミュニティトレジャリーに3,787,251$ethDYDXが帰属しているのは、複数のガバナンス提案により、dYdXコミュニティの各エポックで利用可能な$ethDYDXの金額が3,020,548$ethDYDX増加したためです。

* [DIP 14](https://dydx.community/dashboard/proposal/7) - USDCのステーキングの報酬を0に設定（エポックあたり383,562$ethDYDX）、
* [DIP 16](https://dydx.community/dashboard/proposal/8) - 取引報酬を25％削減（エポックあたり958,904$ethDYDX）、
* [DIP 17](https://dydx.community/dashboard/proposal/9) - $DYDXのステーキングの報酬を0に設定（エポックあたり383,562$ethDYDX）、
* [DIP 20](https://dydx.community/dashboard/proposal/11) - 取引報酬をさらに45％削減（エポックあたり1,294,520$ethDYDX）さらに
* [DIP 24](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-24.md) - 流動性プロバイダー報酬を50%削減（エポックあたり575,342$ethDYDX）。
*   [DIP 29](https://dydx.community/dashboard/proposal/16) - dYdX v3のエポック30～32から⅓の流動性プロバイダー報酬を以下の値に減らします。

    * エポック30：383,562 $ethDYDX
    * エポック31：191,781 $ethDYDX
    * エポック32：0 $ethDYDX

    エポック31以降は、dYdX v3に対する流動性プロバイダーの報酬はありません。DIP 29において、dYdXコミュニティはdYdX v3のエポック30～32から取引報酬を⅓減少させることに投票しましたが、残りの取引報酬の配分はdYdX取引報酬チェーンに移行されました。

2023年11月18日、dYdXコミュニティは、コミュニティ基金で発生したethDYDX残高をイーサリアムからdYdXチェーンに橋渡しすることを[投票](https://dydx.community/dashboard/proposal/16)しました。ブリッジされると、DYDXはdYdXコミュニティによってdYdXチェーンのガバナンス投票で使用できます。



**目的**

* dYdXの成長を推進するプログラムやイニシアチブに資金を提供。
* コミュニティNFT、ハッカソン、分析ダッシュボード、ミーム、スワッグ、サードパーティ製のツール、翻訳、その他のプロジェクトに資金を提供する助成プログラムを構築。
* クラス最高のガバナンスシステムを構築し、強固なガバナンスを促進。

## 概要

コミュニティトレジャリーでは$ethDYDXを保有しており、$ethDYDXの保有者が助成金、新しい流動性マイニングプール、またはその他のプログラムのいずれに使用するかを決定します。$ethDYDXは、5年間にわたって継続的にコミュニティトレジャリーに帰属します。コミュニティトレジャリーからのethDYDXを使用するには、ガバナンス投票が必要になります。

5年後、ガバナンスにより永続的なインフレ（年間最大`2％`）の実行が決定された場合、新たにできた$ethDYDXがコミュニティトレジャリーで利用可能になります。

## FAQ

<details>

<summary>コミュニティトレジャリーで$ethDYDXはどのように帰属していますか？</summary>

以前は、コミュニティトレジャリーヴェスター（詳細は[こちら](https://docs.dydx.community/dydx-governance/resources/technical-overview#governance-architecture-overview)）は毎秒[`0.3169242627`](tel:03169242627)ドルのethDYDXをコミュニティトレジャリーに帰属させていました。$ethDYDXが付与されると、コミュニティトレジャリーベスターで`請求`関数を呼び出すと、既得の$ethDYDXがコミュニティトレジャリーに移動されます。dYdXコミュニティメンバーは、[ここ](https://etherscan.io/address/0x08a90Fe0741B7DeF03fB290cc7B273F1855767D8#writeContract)からEtherscanで`請求`関数を呼び出して（Gas（ガス）代にETHが必要です）、既得の$ethDYDXをコミュニティトレジャリーベスターからコミュニティトレジャリーに移動させることができます。

dYdXコミュニティによるコミュニティトレジャリーの管理詳細は、dYdX財団の[利用規約](https://dydx.foundation/terms)をご参照ください。

![](../.gitbook/assets/image.png)

</details>

