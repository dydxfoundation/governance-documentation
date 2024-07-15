---
description: >-
  ガバナンスプロセスDRCの作成、スナップショットの選択の作成、DIPの作成、スナップショットの選択、DIPの選択、DIPのキューキング、DIPの実行のステップ・バイ・ステップの概要
---

#

dYdX Foundationが作成したこのガイドは、dYdXのコミュニティがdYdXのガバナンスプロセスを理解する上で役立ちます。このガイドでは、以下の内容についてのステップ・バイ・ステップの概要を説明しています。

* [フォーラムディスカッション（オフチェーン）](governance-guide.md#step-1-forum-discussions-drc-creation-off-chain-and-drc-feedback)
* [DRCの作成（オフチェーン）](governance-guide.md#step-1-forum-discussions-drc-creation-off-chain-and-drc-feedback)
* [スナップショットの選択の作成（オフチェーン）](governance-guide.md#step-2-drc-snapshot-polling-off-chain)
* [スナップショットの選択](governance-guide.md#how-to-vote-on-a-snapshot-poll)
* [DIPの作成（オフチェーン）](governance-guide.md#step-3-dip-creation-off-chain-proposal)
* [DIPの作成（オンチェーン）](governance-guide.md#step-1-on-chain-dip-drafting)
* [DIPの選択（オンチェーン）](governance-guide.md#how-to-vote-on-a-dip)
* [DIPのキューイング（オンチェーン）](governance-guide.md#how-to-queue-a-proposal)
* [DIPの実行（オンチェーン）](governance-guide.md#how-to-execute-a-proposal)

このガイドで紹介されている2つの例は、_DIP 2（オフチェーンの提案） - 流動性プロバイダー報酬のしきい値の引き下げ_、および_DIP 3（オンチェーンの提案） - セーフティモジュールの復元_、です。

## DIP 2（オフチェーンの提案） - 流動性プロバイダー報酬のしきい値の引き下げ

_**要約：**_

エポック6で、dYdXコミュニティはマーケットメーカーのLP報酬ボリュームのしきい値を1％から0.25％に引き下げる[スナップショット](https://commonwealth.im/dydx/snapshot/dydxgov.eth/0x785066561be1e5d170eb28960da5ef2643ee0d0c3d590fd797c028512cc6be43)に賛成しました。エポック2でLP報酬のしきい値を5％から1％に引き下げており、それと同じプロセスでエポック6での引き下げが行われます（1％から0.25％へ）。LP報酬ボリュームのしきい値を5％から1％に引き下げるステップ・バイ・ステップの概要は以下のとおりです。

コミュニティの過半数（投票数399、$ethDYDXの86％）は、流動性プロバイダー報酬が得られるボリュームのしきい値を5％から1％に引き下げる[スナップショット](https://forums.dydx.community/snapshot/dydxgov.eth/QmXtS7CGVX7C5v2JdcJpsqWAeZrStQcogSQpP6zzhzwLmN)に投票しました。マーケットメーカーが流動性プロバイダー報酬を得られるボリュームのしきい値を5％から1％に引き下げる[オフチェーンDIP](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-2.md)は、DeFiance CapitalのJacob Goh氏（jteam0x）によって提出されました。エポック2のしきい値である1%を満たしたマーケットメーカーは、エポック3で流動性プロバイダー報酬を獲得する資格がありました。この提案ではオンチェーンのスマートコントラクトの変更は必要ありませんでした。

_**背景：**_

流動性プロバイダー[報酬プログラム](https://docs.dydx.community/dydx-governance/rewards/liquidity-provider-rewards)の一環として、このプロトコルのマーケットメイクを行う流動性プロバイダーに対してエポック（28日間）ごとに115万685$ethDYDXが分配されます。報酬は、稼働時間、両方向のデプス、ビッドアスクスプレッド、およびサポートされているマーケット数の組み合わせに基づく報酬公式に基づいて分配されます。流動性プロバイダーがこの報酬プログラムの対象になるためには、前のエポックにおいて総メーカーボリュームの最小限度割合を提供する必要があります。

dYdXのコミュニティには、流動性プロバイダー報酬のしきい値に関して「即時かつ取り消し不能なコントロール」が存在します。コミュニティをコントロールするパラメータの完全なリストは[こちら](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters)をご覧ください。

コミュニティには流動性プロバイダー報酬のしきい値を引き下げる動機が与えられています。これは新しいマーケットメーカーや中小規模のマーケットメーカーにdYdXプラットフォームの流動性を高めるインセンティブが与えられるためです。さらに、プラットフォームのマーケットメーカー数を増やすことでdYdXプロトコルの一層の分散化が可能になります。

次に、dYdXのガバナンスが実際にどのように機能するかについてステップ・バイ・ステップの概要を説明します。dYdXのガバナンスプロセスの詳細については[こちら](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle)をご覧ください。

### **ステップ1 - フォーラムディスカッション、DRCの作成（オフチェーン）、およびDRCのフィードバック**

_**説明：**_

dYdXのガバナンスプロセスは、[ガバナンスフォーラム](https://dydx.forum/)によって推進されます。コミュニティメンバーはディスカッションスレッドにポストやコメントを行うことで、オフチェーンの大まかなコンセンサスを達成します。フォーラムディスカッションおよびDRCの作成の詳細については[こちら](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle)をご覧ください。\\注 - 運営subDAOは、[コミュニティ投票のコモンウェルスからDiscourseへの移行](https://snapshot.org/#/dydxgov.eth/proposal/0xa5e77732dd24edd26bd41b089969b3662c29eb41c3bacd35cb2931ca55882a8f)に際する新しいフォーラムとして[**https://dydx.forum/**](https://dydx.forum/)を立ち上げました。このガイドでは以前のDRCのディスカッションに関する言及の一部において引き続きコモンウェルスを対象にしていますが、あらゆる新しいディスカッションは新たに立ち上げられた[**Discourse**](https://dydx.forum/)フォーラムで行う必要があります。\


_**DIP 2への適用**_：

Three Arrows CapitalのSu Zhu氏（zhusu）は、流動性プロバイダー報酬のしきい値を引き下げるための[オフチェーンのフォーラムディスカッション](https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives/)を作成しました。WintermuteのEvgeny氏、KronosのBen氏、SixtantのJosh氏など、さまざまなコミュニティメンバーがディスカッションに参加し、貴重なフィードバックを提供しています。

![https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives/](../.gitbook/assets/2-reduce-mm-incentives.png)

![https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives/](../.gitbook/assets/2-reduce-mm-incentives-2.png)

#### _Discourseに投稿およびコメントする方法：_

* メールアカウントでDiscourseに登録し、[こちら](https://dydx.forum/)からdYdXコミュニティに参加してください。

<figure><img src="../.gitbook/assets/Screenshot 2023-04-19 at 10.59.27 AM.png" alt=""><figcaption></figcaption></figure>

* スレッドを選択し、コメントをスクロールし、コメントにいいねや返信をしましょう。
* 「**新しい**トピック」をクリックしてトピックカテゴリを選択することで、新しいディスカッションスレッドを作成するか、DRCを投稿します。

<figure><img src="../.gitbook/assets/Screenshot 2023-04-19 at 11.03.33 AM.png" alt=""><figcaption></figcaption></figure>

* DRCを作成する場合、[こちら](https://github.com/dydxfoundation/dip/blob/master/DIP-X.md)からテンプレートに従ってください。「[提案のライフサイクル](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle)」の「_DRCの作成_」で概説しているように、DRCには少なくとも以下の内容を含めなければなりません：
  * DRCの短い、簡潔なタイトル
  * 提案の短い、簡潔な説明
  * DRCの合理的理由（例：なぜ？）
  * フォーラムポストのタイトルにはDRC：\[DRCの短いタイトルを挿入]（例えば、DRC：新しいマーケットリクエスト）を含めなければなりません。
  * コミュニティのメンバーがオフチェーンの改善の選択のために使用できるコミュニティ調査

### **ステップ2 - DRCのスナップショットの選択（オフチェーン）**

_**説明：**_

コミュニティが大まかなコンセンサスを達成した後、10Kの提案権を有するコミュニティメンバーは[スナップショット](https://snapshot.org/#/)のDRCの選択（オフチェーン）を作成できます。[提案権](https://docs.dydx.community/dydx-governance/voting-and-governance/voting)により、提案の作成および維持ができるようになります。スナップショットは、ユーザーがオフチェーンでセンチメントを表示できるようにする単純な選択インターフェースです。スナップショットでの投票は、投票に使用したアドレスが保有または委任しガバナンストークンの数によって重み付けられます。 スナップショットの選択を行うコミュニティメンバーは、DRC、選択システム、選択開始日、選択終了日、およびスナップショットブロック番号の詳細を提供する必要があります。選択期間は5日間とし、（_13.2秒のブロックタイムに基づいて）_1日の選択遅延を経て選択を開始するものとします。選択遅延により、dYdXのコミュニティメンバーにはDRCの詳細な学習、$ethDYDXの購入、ガバナンストークンの投票権を委任するための時間が付与されます。ガバナンストークンを保有しているか、スナップショットブロック番号以前に投票権を委任されていたコミュニティメンバーは、投票権を有しています。スナップショットの選択の詳細については[こちら](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle)をご覧ください。

_**DIP 2への適用**_：

コミュニティメンバーは、Su Zhu氏のポストに関するフィードバックを提供しました。コミュニティによって以下の報酬のしきい値が提案されました：

* [0.5％](https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives?comment=body) - Three Arrows CapitalのSu Zhu氏、
* [1％](https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives?comment=4972) - BitTradingのSam氏、
* [2.5％](https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives?comment=4855) - Kronos/WOO NetworkのBen氏、
* [5％](https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives?comment=4872) - WintermuteのEvgeny氏。

次に、Su Zhu氏は以下のオプションが付くスナップショットの選択を作成しました：

* MMのしきい値を1％まで引き下げる
* MMのしきい値を2.5％まで引き下げる
* MMのしきい値を5％で維持する

![https://snapshot.org/#/dydxgov.eth/proposal/QmXtS7CGVX7C5v2JdcJpsqWAeZrStQcogSQpP6zzhzwLmN](../.gitbook/assets/2-create-snapshot.png)

#### _スナップショットの選択方法：_

* イーサリアムウォレットでスナップショットに登録し、[こちら](https://snapshot.org/#/dydxgov.eth)からdYdXの提案をフォローしてください。

![https://snapshot.org/#/dydxgov.eth](../.gitbook/assets/2-register-snapshot.png)

* アクティブなスナップショットに投票するには、スナップショットの投票がアクティブになる時点でガバナンストークンを保有しているか、またはスナップショットブロック番号以前にアドレスに委任された投票権を有している必要があります。
* 選択を行うには、提案をクリックして「はい」または「いいえ」を選択し、その後で「選択」をクリックします。

#### _スナップショットの選択の作成方法：_

* スナップショットの投票を作成するには、**最小でも10k ガバナンストークンの保有**および/または提案の作成に**使用するアドレスに委任された投票権を有している**必要があります。
* スナップショットの提案は、提案ごとに最大10アクションまで、1つまたは複数のアクションで構成できます。アクションとは、提案で指定された変更を指します。
* 提案権の最小要件である10k DYDXを満たしている場合、「**新しい提案**」を選択し、以下のコンテンツ要件に従って空欄に記入してください。

<figure><img src="../.gitbook/assets/Screenshot 2023-04-19 at 11.08.42 AM.png" alt=""><figcaption><p>dYdXスナップショットページ - 「新しい提案の作成」ボタン</p></figcaption></figure>

<figure><img src="../.gitbook/assets/Screenshot 2023-04-19 at 11.09.33 AM.png" alt=""><figcaption><p>ここにスナップショットの詳細を記載し、DRCへのリンクを必ず添えてください。</p></figcaption></figure>

DRCのスナップショット選択のコンテンツ要件：

* DRCの詳細（フォーラムディスカッションへのリンク付き）、
* 選択システム、
* （_13.2秒のブロックタイムに基づいて）_選択開始日と選択終了日は合計4日間に設定します。また、
* スナップショット選択は、選択開始の1日前（\~6570ブロック）前にポストされます。

スナップショット選択の拘束力のある要件

ほとんどの意思決定においてスナップショット選択はシグナルとして機能しますが、スマートコントラクトを変更するような拘束力のある結果にはオンチェーン選択が必要です。オンチェーンでのスマートコントラクトのコールが必要でない意思決定の場合、特にトレードおよび流動性プロバイダーの報酬公式の変更については、スナップショットの選択は拘束力を有する最終選択であるとみなされます。上記のコンテンツ要件に加えて、オフチェーン制御されている変数に対する拘束力ある選択としてのスナップショット選択には、以下の内容を含めなければなりません。

* 二者択一オプション明確化のため、アドレスは提案への賛成または反対のいずれかを選択します。

![](../.gitbook/assets/2-snapshot-binary-voting.png)

* 選択後、関連情報はIPFSに保存されます。レポートが自動的に生成され、ダウンロードできます。

![https://snapshot.org/#/dydxgov.eth/proposal/QmXtS7CGVX7C5v2JdcJpsqWAeZrStQcogSQpP6zzhzwLmN](../.gitbook/assets/2-snapshot-ipfs.png)

### **ステップ3 - DIPの作成（オフチェーン提案）**

_**説明**：_

（1）スナップショット選択の結果、オフチェーンパラメーター（トレード報酬やLP報酬公式の変更など）が更新される場合、および（2）コミュニティメンバーがオンチェーンスマートコントラクトの変更提案を提出したい場合、DIPを作成する必要があります。オンチェーンでのスマートコントラクトの更新が必要でない場合、スナップショット選択の結果はオフチェーンDIPで定式化され、dYdX FoundationのGithubのPending-DIPブランチにプルリクエストを通じて提出される必要があります。DIPはスナップショット選択の結果を反映する必要があります。DIPは、[こちら](https://github.com/dydxfoundation/dip/blob/master/DIP-X.md)からご覧いただけるテンプレートに含まれる情報を指定する必要があります。

_**DIP 2への適用**_：

この場合、[DIP](https://github.com/jteamdc/dip/blob/master/content/dips/DIP-2.md)は@Jteamdcによって執筆されました。

![https://github.com/jteamdc/dip/blob/master/content/dips/DIP-2.md](../.gitbook/assets/2-dip-example.png)

DIP 2のドラフト提案が完了したとき、@Jteamdcは使用中のブランチからdYdX FoundationのPending-DIPブランチに対して、\*\*\*\*[のプルリクエスト](https://github.com/dydxfoundation/dip/pull/8)を作成しました。dYdX Foundationが提案を確認し、署名した後、Pending-DIPの変更はマスターブランチに統合されました。

![https://github.com/dydxfoundation/dip/pulls](../.gitbook/assets/2-dip-pending-merge.png)

流動性プロバイダー報酬のしきい値を引き下げる必要はないため、このプロセスは完了し、変更は次のエポック期間に有効になります。

#### _DIPの作成方法：_

* DIPはスナップショットでのオフチェーンDIP選択の結果に基づく必要があり、提案ごとに最大10アクションまで、1つまたは複数のアクションで構成できます。アクションとは提案で指定された変更を指します。詳細については「[DIPの作成](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle#6.-proposal-queuing-and-execution)」で確認できます。
* Githubの口座に登録：[https://github.com/signup](https://github.com/signup) 。
* [こちら](https://github.com/dydxfoundation/dip)からdYdXのレポページに移動し、Github口座の下でレポをフォークします。

![https://github.com/dydxfoundation/dip](../.gitbook/assets/2-dip-create-1.png)

* フォークされたDIPレポで、DIPの内容を含むディレクトリに移動します：[https://github.com/\[user\_name\]/dip/tree/master/content/dips](https://github.com/yt8073/dip/tree/master/content/dips) 。

![](../.gitbook/assets/2-dip-create-2.png)

* dipsフォルダを選択：[https://github.com/\[user\_name\]/dip/tree/master/content](https://github.com/Jwatts15/dip/tree/master/content) 。

![](../.gitbook/assets/2-dip-create-3.png)

[こちら](https://github.com/dydxfoundation/DIP/blob/master/DIP-X.md)のdipsフォルダには、DIPテンプレートをフォローしているこれまでの提案のディレクトリが含まれています。

![https://github.com/dydxfoundation/dip/tree/master/content/dips](../.gitbook/assets/2-dip-create-4.png)

* プロポーザルの記述を開始する前に、フォークされたブランチが最新バージョンのマスターブランチに対応していることを確認してください。DIPレポの旧バージョンを使用している場合、フォークされたバージョンが最新の変更に対応していることを確認してください。フォークされたバージョンのリベーシングについては、こちらから手順を確認できます：[https://stackoverflow.com/questions/7929369/how-to-rebase-local-branch-onto-remote-master](https://stackoverflow.com/questions/7929369/how-to-rebase-local-branch-onto-remote-master)
* [DIPテンプレート](https://github.com/dydxfoundation/DIP/blob/master/DIP-X.md)を提案の情報を使用して編集します。DIPレポをフォークしていない場合、管理者ではないため、編集アイコンを選択するとマスターからのレポが自動的にフォークされます。

![https://github.com/dydxfoundation/DIP/blob/master/DIP-X.md](../.gitbook/assets/2-dip-create-5.png)

* [テンプレート](https://github.com/dydxfoundation/DIP/blob/master/DIP-X.md)をフォローし、`content/dips/` ディレクトリのリポジトリのフォークにDIPを追加します。以下のDIPステータスのネーミングコンベンションに従ってください。

![](../.gitbook/assets/2-dip-create-6.png)

DIPステータス：

* WIP - まだ開発中のDIP。
* 提案済み - オンチェーン提案の準備ができているDIP。
* 承認済み - dYdXコミュニティによる実装が承認されたDIP。
* 実装済み - メインネットにリリースされたDIP。
* 拒否 - 拒否されたDIP。
* すべてのコンテンツが正しいことを確認した後、dYdX FoundationのPending-DIPブランチに対して、作業ブランチからのプルリクエストを作成します。外部のパーティーがマスターブランチへのマージを希望する場合、IPFSジョブが失敗するため、dYdX Foundationのマスターブランチに対するこのプルリクエストは提出**しないで**ください。一例として、[こちら](https://github.com/dydxfoundation/dip/pull/8)のプルリクエストを使用してください。

![](../.gitbook/assets/2-dip-status-1.png)

* レビュー後、dYdX FoundationはPending-DIPブランチからマスターブランチへの変更をマージします。

![https://github.com/dydxfoundation/dip/pull/9](../.gitbook/assets/2-dip-status-2.png)

* **マージ**前にジョブが自動的に実行され、IPFSにDIPをアップロードします。DIPのアップロードはこちらから確認できます：[https://github.com/dydxfoundation/dip/pull/9/checks](https://github.com/dydxfoundation/dip/pull/9/checks)
* DIPは、[**`dip`**](https://github.com/dydxfoundation/dip)`/`[`content`](https://github.com/dydxfoundation/dip/tree/master/content)`/`**`dips`**`/`の下に追加されます。

![](../.gitbook/assets/2-dip-status-3.png)

この提案ではオンチェーンでのスマートコントラクト変更の必要はないため、このプロセスは完了し、変更は次のエポック期間に有効になります。

## DIP 3（オンチェーン提案） - セーフティモジュールの復元

_**要約：**_

11月1日、セーフティモジュールのステーキングプールの機能を復元するため、ParadigmのDan Robinson氏によってオンチェーン[DIP](https://dydx.community/dashboard/proposal/3)が作成されました。コミュニティの過半数（投票者数251、約142M ethDYDX）は、セーフティモジュールの機能の復元に賛成しました。10日間の選択期間の後、コミュニティメンバーがキューを呼び出し、提案を7日間のタイムロック遅延に移動させるために3日間程度を要しました。11月20日、セーフティモジュールは復元され、クリーンな状態にリセットされました。

_**背景：**_

dYdXのセーフティモジュールは、dYdXプロトコルのバックストップに使用できる分散型資金プールをブートストラップするように設計されたステーキングコントラクトです。ユーザーは$ethDYDXをセーフティプールにステーキングし、$ステーキングDYDX（1：1）を受け取ります。$ステーキングDYDXは、$ethDYDXと同じ投票権および提案権を有するERC-20として移転されるトークン化したポジションです。ショートフォールイベントの場合、ステーキングされた$ethDYDXをスラッシュし、損失を軽減する必要があります。セーフティステーキングプールでethDYDXをステーキングするユーザーに対して、$ethDYDXのトークンサプライからその2.5％（2,500万$ethDYDX）が分配されます。セーフティステーキングプールの詳細については[こちら](https://dydx.foundation/blog/en/safety-staking)をご覧ください。

[セーフティステーキングプール報酬](https://docs.dydx.community/dydx-governance/staking-pools/safety-staking-pool)の一環として、ステーカーにエポック（28日間）ごとに383,562$ethDYDXが分配されます。報酬はステーカーに秒単位で分配されます。

dYdXのコミュニティには、セーフティモジュールのスマートコントラクトパラメータに関して「即時かつ取り消し不能なコントロール」が存在します。コミュニティをコントロールするパラメータの完全なリストは[こちら](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters)をご覧ください。

9月8日午後3時（UTC）に、$ethDYDXトークンの移動制限が解除され、dYdXセーフティモジュールへのステーキングが実質的に開始されました。ほぼ1時間にわたって、50を超えるアドレスが約157K ethDYDXをステーキングしました。デプロイメントプロセスでバグによるエラーが発生し、セーフティモジュールにステーキングしたアドレスに対してはステーキングDYDXが発行されませんでした。その結果、各ステーカーの資金がコントラクトにスタックされ、dYdXチームではdYdXガバナンスUIでのステーキングを無効化しました。

[DIP 1](https://dydx.community/dashboard/proposal/0)はセーフティモジュールの復元機能を提案しました。これは影響を受けたアドレスが資金を回復し、補償としてステーキングされたトークンの10％相当を受け取るというものでした。コミュニティ感情は[DIP 1 - セーフティモジュールの復旧とステーカーの回復](https://dydx.community/dashboard/proposal/0)を強く支持していましたが、長いタイムロック選択の可決に必要な100M $ethDYDXの最小選択者数を満たせなかったため、この提案は否決されました。その結果、DeFiance Capitalのジェイコブ・ゴー（jteam0x）は[DIP 4 - セーフティモジュール・ステーカーの払い戻しと補償](https://dydx.community/dashboard/proposal/2)を作成し、影響を受けたアドレスに対し、逃した報酬分と迷惑料を補償しました。[DIP 4](https://dydx.community/dashboard/proposal/2)には、ステーキングされたトークンのリカバリーコントラクトのデプロイおよび影響を受けたアドレスに対するRewards Treasuryからの10％補償が含まれていました。DIPは、あまり厳格でないショートタイムロックのガバナンスパラメータによって管理されました。

DIPの提案ライフサイクルは通常、DIPの作成まで一貫しています。DIP 3（オンチェーン）とDIP 2（オフチェーン）の主要な違いは、DIP 3ではオンチェーン選択とスマートコントラクトのデプロイメントが必要だった点にあります。フォーラムディスカッション、DRCの作成、ドラフトDIPの作成のプロセスは同じであるため、オンチェーンDIPのドラフト要件に関するステップ・バイ・ステップのディスカッションを開始します。詳細については以下のリンク先をご覧ください：

* dYdXのガバナンスプロセス - [https://docs.dydx.community/dydx-governance/voting-and-governance/dip-posal-lifecycle](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle) 。
* セーフティモジュールのインシデントレポート - [https://dydx.foundation/blog/en/outage-1](https://dydx.foundation/blog/en/outage-1) 。
* オフチェーンのフォーラムディスカッション **-** [https://commonwealth.im/dydx/posal/discussion/1743-safety-staking-pool-on-pause](https://commonwealth.im/dydx/proposal/discussion/1743-safety-staking-pool-on-pause) 。
* オフチェーンDRC **-** [https://commonwealth.im/dydx/proposal/discussion/1770-drc-incident-report-of-the-safety-module-outage-proposed-solution](https://commonwealth.im/dydx/proposal/discussion/1770-drc-incident-report-of-the-safety-module-outage-proposed-solution)
* オフチェーンDRCのスナップショット選択 **-** [https://snapshot.org/#/dydxgov.eth/proposal/QmbJ5QxHr1pyShKTDaF5DjAr6vxQn8DVxshH2fyWgzDCBn](https://snapshot.org/#/dydxgov.eth/proposal/QmbJ5QxHr1pyShKTDaF5DjAr6vxQn8DVxshH2fyWgzDCBn)
* Githubで提案されたDIP** - ** [https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-3.md ](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-3.md)

### **ステップ1 - オンチェーンDIPのドラフティング**

_**説明：**_

dYdXプロトコルのガバナンスに影響を与えるオンチェーンDIPのドラフティングでは、スマートコントラクトの変更の実装のための具体的なステップを概説する必要があります。コミュニティがスナップショットから大まかなコンセンサスを達成した後か、または以前に失敗したDIPの後、十分な提案権を有するコミュニティメンバーは新しいオンチェーンDIPを提出できます。提案権のしきい値、タイムロックの実行管理者、その他のガバナンスパラメータの詳細については[こちら](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters)をご覧ください。

_**DIP 3への適用：**_

この場合、[DIP](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-3.md)はParadigmのDan Robinson氏によって執筆されました。この提案にはオンチェーンのスマートコントラクトの変更が含まれており、特定のスマートコントラクトの実装リンクも含まれていました。

![https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-3.md](../.gitbook/assets/2-dip3-example-1.png)

SafetyModuleV2.solのデプロイメントコントラクトからセーフティフォルダに移動すると、提案の実行方法に関する具体的かつ詳細な記述が含まれているREADMEが表示されます。

![](../.gitbook/assets/2-dip3-example-1a.png)

READMEに含まれる提案の実装手順はこちらです：[https://github.com/dydxfoundation/governance-contracts/tree/master/safet](https://github.com/dydxfoundation/governance-contracts/tree/master/contracts/safety)y 。

![https://github.com/dydxfoundation/governance-contracts/tree/master/contracts/safety](../.gitbook/assets/2-dip3-example-2.png)

![https://github.com/dydxfoundation/governance-contracts/tree/master/contracts/safety](../.gitbook/assets/2-dip3-example-3.png)

![https://github.com/dydxfoundation/governance-contracts/tree/master/contracts/safety](../.gitbook/assets/2-dip3-example-4.png)

#### _オンチェーンDIP（WIP）のドラフト方法：_

* 新しいウォレットでDIPを作成します。デプロイメントプロセスでは環境変数としてシードフレーズを入力する必要があるため、オンチェーンDIPの作成にはワンオフウォレットを使用することを推奨します。
* DIPの作成に必要な提案権をワンオフウォレットに委任します。[こちら](https://dydx.community/dashboard)から提案権を委任できます。提案権の異なるしきい値は以下のとおりで、[こちら](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters)からご覧いただけます。
  * ショートタイムロック：総供給量の0.5％（提案権：5M）
  * Starkwareの実行管理者：総供給量の0.5％（提案権：5M）
  * ロングタイムロックの実行管理者：総供給量の2.0％（提案権：20M）
  * Merkle Pauserの実行管理者：総供給量の0.5％（提案権：5M）
* Alchemyキーを作成します。Alchemyキーでは、イーサリアムとのインタラクションやスマートコントラクトのデプロイのためにイーサリアムノードを実行する必要はありません。Alchemyキーの作成ガイドは[こちら](https://docs.alchemy.com/alchemy/introduction/getting-started)からご覧いただけます。

![https://docs.alchemy.com/alchemy/introduction/getting-started](../.gitbook/assets/2-draft-dip-example-1.png)

イーサリアムと「開始」を選択します。

![](../.gitbook/assets/2-draft-dip-example-2.png)

必要な情報を入力し、Goerli Network、「アプリの作成」の順に選択します。

<figure><img src="../.gitbook/assets/2-draft-dip-example-3.png" alt=""><figcaption></figcaption></figure>

口座を作成した後、[こちら](https://docs.alchemy.com/alchemy/introduction/getting-started)から設定指示に従います。

「4. 構築の開始」で「最初のスマートコントラクトのデプロイを行う」を選択し、ガイドに従います。

![https://docs.alchemy.com/alchemy/introduction/getting-started](../.gitbook/assets/2-draft-dip-example-4.png)

* Windowsのコマンドラインからデフォルトのターミナルアプリを開くか、iTermをダウンロードします：[https://iterm2.com/](https://iterm2.com/) 。
* Node.jsおよびnpmのダウンロードやインストールが済んでいない場合、以下から行います：[https://docs.npmjs.com/downloading-and-installing-node-js-and-npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm) 。
* Hardhatはイーサリアムソフトウェアのコンパイルおよびテストのための開発ツールです。Hardhatはこちらからインストールできます：[https://hardhat.org/tutorial/setsing-up-the-environment.html](https://hardhat.org/tutorial/setting-up-the-environment.html) 。
* 提案されたスマートコントラクトの実装をドラフトします。
* IPFSのハッシュが自動的に生成され、[こちら](https://github.com/dydxfoundation/dip/tree/master/content/ipfs-dips)から入手できます。IPFSのハッシュは、ファイル名`DIP-[新しいDIP #]-ipfs-hashes.json`のdYdX Foundationのディレクトリに含まれます。

![https://github.com/dydxfoundation/dip/tree/master/content/ipfs-dips](../.gitbook/assets/2-draft-dip-example-5.png)

* 新しいファイル（`DIP-[新しいDIP #]-ipfs-hashes.json`）を選択した後、エンコードされたHashを使用していることを確認します。

![https://github.com/dydxfoundation/dip/blob/master/content/ipfs-dips/DIP-3-Ipfs-hashes.json](../.gitbook/assets/2-draft-dip-example-6.png)

### **ステップ2 - オンチェーンDIPの提出**

_**説明：**_

コミュニティメンバーが提案されたスマートコントラクトの実装が正しいことを確認し、DIPが確定した後、そのDIPをオンチェーンで提出できます。オンチェーンDIPが作成されると、提案は選択遅延の「保留」状態に進み、それが1日間（約6,570ブロック）続きます。ユーザーのスナップショットは選択遅延後に、$ethDYDXの保有と委任された投票権を考慮して記録されます。次に、提案は「アクティブ」状態に進み、提案の種類に応じて選択期間は2〜10日間になります。提案が実行される場合、提案の種類に応じて変化する最小クォーラムと最小選択差の要件を満たす必要があります。DIPが最小クォーラム、最小選択差、選択コミュニティメンバーの多数要件を満たす場合、任意のアドレスが提案をタイムロックのキューに移動させるためのキューを呼び出すことができます。このタイムロックコントラクトは、dYdXコミュニティによって選択されたトランザクションのキュー、キャンセル、実行を行うことができます。タイムロックのキューの期間は提案の種類によって異なります。

_**DIP 3への適用：**_

Paradigmのチームが`SafetyModuleV2.sol`のソリディティコードを決定しました。

![https://github.com/dydxfoundation/governance-contracts/blob/master/contracts/safety/v2/SafetyModuleV2.sol](../.gitbook/assets/2-draft-dip-example-7.png)

Paradigmのチームが、ローカルとフォークされたメインネットの両方でのアップデートをシミュレートしました。その後、テストスイートが実行され、メインネットでのガバナンス提案の実行に続いて完全な機能復元が行われます。

Paradigmのチームが以下のスクリプトを実行することで、スマートコントラクトのアップデートをデプロイしました。

**セーフティモジュールのリカバリーのデプロイメント**

`ALCHEMY_KEY=<... のエクスポート>`

`MNEMONIC=<... のエクスポート>`

`npx hardhat --network mainnet deploy:safety-module-recovery`\
`--dydx-token-address 0x92D6C1e31e14520e676a687F0a93788B716BEff5`\
`--short-timelock-address 0x64c7d40c07EFAbec2AafdC243bF59eaF2195c6dc`\
`--rewards-treasury-address 0x639192D54431F8c816368D3FB4107Bc168d0E871`

**ガバナンス提案：セーフティモジュールの修正**

`ALCHEMY_KEY=<... のエクスポート>`

`MNEMONIC=<... のエクスポート>`

`npx hardhat --network mainnet deploy:safety-module-fix-proposal`\`--proposal-ipfs-hash-hex 0x...`\
`--governor-address 0x7E9B1672616FF6D6629Ef2879419aaE79A9018D2`\
`--long-timelock-address 0xEcaE9BF44A21d00E2350a42127A377Bf5856d84B`\
`--safety-module-address 0x65f7BA4Ec257AF7c55fd5854E5f6356bBd0fb8EC`\
`--safety-module-proxy-admin-address 0x6aaD0BCfbD91963Cf2c8FB042091fd411FB05b3C`\
`--safety-module-new-impl-address 0x...`

**ガバナンス提案：セーフティモジュールの補償**

`ALCHEMY_KEY=<... のエクスポート>`

`MNEMONIC=<... のエクスポート>`

`npx hardhat --network mainnet deploy:safety-module-compensation-proposal`\
`--proposal-ipfs-hash-hex 0x...`\
`--dydx-token-address 0x92D6C1e31e14520e676a687F0a93788B716BEff5`\
`--governor-address 0x7E9B1672616FF6D6629Ef2879419aaE79A9018D2`\
`--short-timelock-address 0x64c7d40c07EFAbec2AafdC243bF59eaF2195c6dc`\
`--rewards-treasury-address 0x639192D54431F8c816368D3FB4107Bc168d0E871`\
`--safety-module-recovery-address 0x...`

DIPは[https://dydx.community/dashboard](https://dydx.community/dashboard)に同時にポストされました。

![https://dydx.community/dashboard](../.gitbook/assets/2-draft-dip-example-8.png)

![https://dydx.community/dashboard](../.gitbook/assets/2-draft-dip-example-9.png)

dYdXのガバナンスコントラクトは、0x7e9b1672616ff6d6629ef2879419aae79a9018d2: [https://etherscan.io/txs?a=0x7e9b1672616ff6d6629ef2879419aaae79a9018d2\&p=10](https://etherscan.io/txs?a=0x7e9b1672616ff6d6629ef2879419aae79a9018d2\&p=10) です。

DIPのデプロイはEtherscan：[https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad) で確認できます。

このDIPは2021年11月1日、ブロック13532376で作成されました。将来の6,570ブロックの場合、DIPのステータスは「保留」です。

![https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](../.gitbook/assets/2-draft-dip-example-10.png)

ethDYDXの保有者は、ブロック13538946で「アクティブ」状態に移行した時にDIPを選択できました。

最初の選択は2021年11月2日午後5時51分22秒（UTC）に行われ（ブロック13538959）、オンチェーンDIPが作成された時点から6,583ブロックでした。

![https://etherscan.io/tx/0xc3d0ace92be4ac3da40dc17f45a573d4dbd83d31f7a95733071de883ded67a4f](../.gitbook/assets/2-draft-dip-example-11.png)

ロングタイムロックに関する10日間の選択期間後、コミュニティメンバーはキューを呼び出すことで提案を7日間のタイムロック遅延に移行させることができます。DIP 3では、コミュニティメンバーがキューを呼び出すのに約3日間かかりました。

![https://etherscan.io/tx/0x3402372aa549d2270a6b5d4f84884ae2bfec6922fc808703b47d53b27d288c81](../.gitbook/assets/2-draft-dip-example-12.png)

7日間のタイムロック遅延の後、DIPはオンチェーンで実行されました。

![https://etherscan.io/tx/0xfd332147899fd3ef1db62f262ffae92bbd7d18a5ed4e142eb0407a173dbf0453](../.gitbook/assets/2-draft-dip-example-13.png)

オンチェーンでDIPが実行された時点で、[https://dydx.community/dashboard/proposal/3](https://dydx.community/dashboard/proposal/3) のDIPステータスは「実行済み」に更新されました。

![](../.gitbook/assets/2-draft-dip-example-14.png)

注：（1）提案はタイムロックの遅延直後に開始される7日間の期間内に実行される必要があり、（2）提案を行うアドレスはDIPが実行されるまでの間、各タイムロックコントラクトで必要な提案権の最小額を維持する必要があります（提案権は5Mまたは20M）。

#### _オンチェーンDIPの提出方法：_

* DIPを作成するのに十分な提案権を有していることを確認します。詳細については「[DIPの作成](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle)」をご覧ください。
  * ショートタイムロックの実行管理者：総供給量の0.5％（提案権：5M）
  * Starkwareの実行管理者：総供給量の0.5％（提案権：5M）
  * ロングタイムロックの実行管理者：総供給量の2.0％（提案権：20M）
  * Merkle Pauserの実行管理者：総供給量の0.5％（提案権：5M）
* ガス代を支払うためのETHがウォレットにあることを確認します。
* イーサリアムメインネットネットワークのAlchemyでアプリを作成します。

![https://dashboard.alchemyapi.io/](../.gitbook/assets/2-draft-dip-example-15.png)

* アプリが作成された後、「キーを表示」をクリックしてAlchemyキー（7LOaQtguSm2kSEcFXQH88B）を入手します：[https://eth-mainnet.alchemyapi.io/v2/7LOaQtgusm2kSEcFXQH88B-EN_K7t\_ul](https://eth-mainnet.alchemyapi.io/v2/7LOaQtguSm2kSEcFXQH88B-EN\_K7t\_ul)

![https://dashboard.alchemyapi.io/apps/xogmjmlex8tlmr95](../.gitbook/assets/2-draft-dip-example-16.png)

* Node.jsとnpmをダウンロードおよびインストールします：[https://docs.npmjs.com/downloading-and-installing-node-js-and-npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm) 。
* Hardhat：[https://hardhat.org/tutorial/setsing-up-the-environment.html](https://hardhat.org/tutorial/setting-up-the-environment.html) をインストールします。
* ドラフトしたスクリプトを実行します。
* ガバナンスコントラクトをチェックして、提案がオンチェーンで作成されたことを確認します：[https://etherscan.io/txs?a=0x7e9b1672616ff6d6629ef2879419aaae79a9018d2\&p=10](https://etherscan.io/txs?a=0x7e9b1672616ff6d6629ef2879419aae79a9018d2\&p=10) 。
* 提案を提出したアドレスは、提案が実行されるまでの間、各タイムロックコントラクトで必要な提案権の最小限度額を維持する必要があります。

#### _DIPでの選択方法：_

* ガス代を支払うためのETHがウォレットにあることを確認します。
* DIPを以下から選ぶことで、アクティブDIPを選択することができます：[https://dydx.community/dashboard](https://dydx.community/dashboard) 。

![](../.gitbook/assets/2-draft-dip-example-17.png)

選択期間は提案の種類によって異なります。詳細については「[DIPの作成](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle)」で確認できます。

* ショートタイムロックの実行管理者：4日間
* Starkwareの実行管理者：4日間
* ロングタイムロックの実行管理者：10日間
* Merkle Pauserの実行管理者：2日間

#### _提案をキューする方法：_

成功した提案をキューすることで、タイムロックの遅延を開始することができます。

* Ethを含む互換性のあるウォレットを使用していることを確認します。
* Etherscanの「コントラクト」タブに移動し、「コントラクトを書く」をクリックします。ガバナンスコントラクトは[こちら](https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2#writeContract)をご覧ください。

![https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2#writeContract](../.gitbook/assets/2-draft-dip-example-queue-1.png)

* キューを選択し、「proposalId」を提出します。

![](../.gitbook/assets/2-draft-dip-example-queue-2.png)

「proposalId」はDIPが作成された時点で、Etherscanで確認できます：[https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad) 。

* 「クリックして詳細を見る」を選択します。

![https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](../.gitbook/assets/2-draft-dip-example-queue-3.png)

* 「入力データのデコード」を選択します。

![https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](../.gitbook/assets/2-draft-dip-example-queue-4.png)

![https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](../.gitbook/assets/2-draft-dip-example-queue-5.png)

#### _提案の実行方法：_

タイムロックの遅延後、成功した提案を実行することができます。

* Etherscanの「コントラクト」タブに移動し、「コントラクトを書く」をクリックします。ガバナンスコントラクトは[こちら](https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2#writeContract)をご覧ください。

![https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2#writeContract](../.gitbook/assets/2-draft-dip-example-execute-1.png)

* 「実行」を選択し、「proposalId」を提出します。

![https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2#writeContract](../.gitbook/assets/2-draft-dip-example-execute-2.png)

* 上記の手順（「_提案をキューする方法_」）に続いて、「proposalId」を見つけます。
* 「payableAmount (ether)」に「0」を入力します。
