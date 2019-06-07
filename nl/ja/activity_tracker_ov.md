---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, overview

subcollection: cloud-activity-tracker

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}



# {{site.data.keyword.cloudaccesstrailshort}} の紹介
{: #activity_tracker_ov}

{{site.data.keyword.cloudaccesstrailfull}} サービスを使用して、アプリケーションが {{site.data.keyword.cloud_notm}} サービスとどのように対話するのかをトラッキングします。 {{site.data.keyword.cloudaccesstrailshort}} を使用して異常なアクティビティーをモニターすることで、規制監査要件に準拠することができます。 収集されるイベントは、Cloud Auditing Data Federation (CADF) 標準に準拠しています。
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} は非推奨になりました。2019 年 5 月 9 日以降、新しい {{site.data.keyword.cloudaccesstrailshort}} インスタンスをプロビジョンできません。既存のプレミアム・プランのインスタンスは、2019 年 9 月 30 日までサポートされます。{{site.data.keyword.cloud_notm}} アカウントのアクティビティーのモニタリングを続行するには、[{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) のインスタンスをプロビジョンします。
{: deprecated}

* {{site.data.keyword.cloudaccesstrailshort}} は、クラウド内の IT リソースに対する高水準のセキュリティー・ガバナンスを実現します。
* {{site.data.keyword.cloudaccesstrailshort}} は、管理者が 1 つの場所で API アクティビティーの取り込み、保管、表示、検索、およびモニターを行えるようにするソリューションを提供します。
* {{site.data.keyword.cloudaccesstrailshort}} は、イベントをダウンロードする機能を提供します。ダウンロードしたイベントは監査証跡レポートを生成するために使用できます。 組織が社内規定および外部の業界や国の規制に準拠するために、これらのレポートが必要になることがあります。

アプリケーションの実行場所がオンプレミス、ハイブリッド・クラウド、またはパブリック・クラウドのいずれであるかに関係なく、社内のポリシーおよび業界の規定に準拠することは、すべての組織の戦略にとって重要な要件です。 {{site.data.keyword.cloudaccesstrailshort}} サービスでは、API 呼び出しをモニターして企業のポリシーおよび市場の業界固有の規定への準拠の証拠を生成するためのフレームワークおよび機能を提供します。

クラウド環境 ({{site.data.keyword.cloud_notm}} など) で作業をする場合、社内のポリシーと業界や国ベースの準拠要件に従って、ワークロードやデータの監査とモニターに関するクラウド戦略を立てる必要があります。 {{site.data.keyword.cloudaccesstrailshort}} サービスを通じて登録された情報を使用することで、セキュリティー・インシデントを特定し、無許可アクセスを検出して、規制上および社内の監査要件に準拠することができます。

例えば、{{site.data.keyword.cloudaccesstrailshort}} アクティビティー・ログを使用して、以下の情報を識別できます。

* クラウド・サービスに対して API 呼び出しを行ったユーザー。
* API 呼び出しが行われたソース IP アドレス。
* API 呼び出しが行われたタイム・スタンプ。
* API 呼び出しの状況。


## イベントの収集
{: #activity_tracker_ov_collect}

{{site.data.keyword.cloudaccesstrailshort}} サービスは、{{site.data.keyword.cloud_notm}} 内の選択されたクラウド・サービスに対して行われる API 呼び出しおよびその他のアクションに関連したアクティビティー・データを取り込みます。 

* イベントは自動的に収集されます。 
* {{site.data.keyword.cloudaccesstrailshort}} で収集されるイベントは、Cloud Auditing Data Federation (CADF) 標準に準拠しています。 CADF 標準は、クラウド環境にあるアプリケーションのセキュリティーの認証、管理、および監査に必要な情報が含まれた、フルイベント・モデルを定義しています。
* {{site.data.keyword.cloudaccesstrailshort}} は、ドメイン別にイベントを保管およびグループ化します。 地域ごとに 1 つのアカウント・ドメインがあり、Cloud Foundry スペースごとに 1 つのスペース・ドメインがあります。 

CADF イベント・モデルには、以下のコンポーネントが含まれています。

<table>
  <caption>表 1. CADF イベント・モデル内のコンポーネント</caption>
  <tr>
    <th>コンポーネント</th>
	<th>説明</th>
  </tr>
  <tr>
    <td>アクション</td>
	<td>アクションは、イニシエーターが実行する、実行を試みる、あるいは完了を待っている、操作またはアクティビティーです。</td>
  </tr>
  <tr>
    <td>イニシエーター</td>
	<td>イニシエーターは、API 呼び出しを行って CADF イベントを生成するリソースです。 起動されるイベントは、API 呼び出しで要求されるアクションによって異なります。</td>
  </tr>
  <tr>
    <td>オブザーバー</td>
	<td>オブザーバーは、CADF イベントで利用可能な情報から CADF レコードを作成して保管するリソースです。</td>
  </tr>
  <tr>
    <td>結果</td>
	<td>結果は、ターゲットに対するアクションの状況です。</td>
  </tr>
  <tr>
    <td>ターゲット</td>
	<td>ターゲットは、アクションが実行される、実行を試みられる、あるいは完了の処理待ち中の、対象のリソースです。</td>
  </tr>
</table>


{{site.data.keyword.IBM_notm}} パブリック・クラウド内の {{site.data.keyword.cloudaccesstrailshort}} ログを使用するときには、以下の事項を考慮してください。

* {{site.data.keyword.IBM_notm}} パブリック・クラウドで実行されるリソースに対する API 呼び出しの監査レコードのみを保管できます。
* {{site.data.keyword.IBM_notm}} パブリック・クラウドのストレージのみがイベント収集のために使用されます。
* 情報は 3 日間保管されます。 それ以降、情報は先入れ先出し (FIFO) 法で削除されます。
* タイプが*アクティビティー* である CADF イベントが {{site.data.keyword.cloudaccesstrailshort}} サービスによってサポートされます。


## Activity Tracker のプロビジョン
{: #activity_tracker_ov_provision}

アカウント・ドメインを通して使用可能なイベントを表示するには、API アクティビティーをモニターしたい地域の Cloud Foundry スペースに {{site.data.keyword.cloudaccesstrailshort}} サービスをプロビジョンする必要があります。 **アカウント所有者**のみが、アカウント・イベントを表示できます。

スペース・ドメインを通して使用可能なイベントを表示するには、API アクティビティーをモニターしたいスペースに {{site.data.keyword.cloudaccesstrailshort}} サービスをプロビジョンする必要があります。

{{site.data.keyword.cloudaccesstrailshort}} サービスをプロビジョンする方法について詳しくは、[{{site.data.keyword.cloudaccesstrailshort}} サービスのプロビジョン](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-provision#provision)を参照してください。



## アクティビティー・ログの分析
{: #activity_tracker_ov_analyze}

アクティビティー・ログの分析は、{{site.data.keyword.cloud_notm}} 内で {{site.data.keyword.cloudaccesstrailshort}} UI を介して行うか、オープン・ソース・ツールである Kibana を使用して行うことができます。 特定のスペースで使用可能なイベントをモニターするか、アカウント・レベルで使用可能なイベントをモニターすることができます。

{{site.data.keyword.cloud_notm}} 内で {{site.data.keyword.cloudaccesstrailshort}} UI を介して、過去 24 時間のアクティビティー・ログの検索、分析、およびモニターを行うことができます。 詳しくは、[{{site.data.keyword.cloudaccesstrailshort}} UI へのナビゲート](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-launch_at_ui#launch_at_ui)を参照してください。

{{site.data.keyword.cloudaccesstrailshort}} Kibana ダッシュボードを使用して Kibana を介して、または、ユーザー独自のカスタム・ダッシュボードを作成することによって、過去 3 日間のアクティビティー・ログの検索、分析、およびモニターを行うことができます。 **注:** この機能を使用できるのは、**プレミアム**・プランのユーザーです。

* Kibana の起動方法について詳しくは、[Kibana ダッシュボードへのナビゲート](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-launch_kibana#launch_kibana)を参照してください。 
* Kibana でイベントを分析するために使用できるフィールドのリストについては、[{{site.data.keyword.cloudaccesstrailshort}} イベントのフィールド](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-at_event#at_event)を参照してください。



## 地域
{: #activity_tracker_ov_regions}

{{site.data.keyword.cloudaccesstrailshort}} サービスは、以下の地域で使用可能です。

* ドイツ
* シドニー
* 英国 (ライト・プランのみが使用可能です)
* 米国南部


## サービス・プラン
{: #activity_tracker_ov_plan}

{{site.data.keyword.cloudaccesstrailshort}} サービスには複数のプランが用意されています。

プランは {{site.data.keyword.cloud_notm}} UI またはコマンド・ラインを使用して変更できます。 プランのアップグレード、またはライト・プランへの切り替えは、いつでも実行できます。 サービス・プランのアップグレードについて詳しくは、[プランの変更](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-change_plan#change_plan)を参照してください。 

使用可能なプランの概要を次の表に示します。

<table>
    <caption>表 1. イベントの取り込み、イベントの保存、およびイベントのエクスポートの機能</caption>
      <tr>
        <th>プラン</th>
        <th>イベントの取り込み</th>
        <th>イベントの保存</th>
		<th>イベントのエクスポート</th>
      </tr>
      <tr>
        <td>ライト (デフォルト)</td>
        <td>いいえ</td>
        <td>過去 3 日間</td>
		<td>いいえ</td>
      </tr>
      <tr>
        <td>プレミアム</td>
        <td>はい</td>
        <td>構成可能な日数。</td>
		<td>はい</td>
      </tr>
</table>

<table>
    <caption>表 2. イベントの管理および表示の機能</caption>
      <tr>
        <th>プラン</th>
		    <th>API</th>
		    <th>CLI</th>
        <th>Kibana</th>
      </tr>
      <tr>
        <td>ライト (デフォルト)</td>
		    <td>いいえ</td>
		    <td>いいえ</td>
        <td>いいえ</td>
      </tr>
      <tr>
        <td>プレミアム</td>
		    <td>はい</td>
		    <td>はい</td>
        <td>はい</td>
      </tr>
</table>

**注:** イベント・ストレージの 1 カ月のコストは、請求サイクルの平均として計算されます。

## セキュリティー
{: #activity_tracker_ov_security}

{{site.data.keyword.cloudaccesstrailshort}} サービスでの処理を行うときには、セキュリティーに関する以下の情報を考慮してください。

* {{site.data.keyword.cloudaccesstrailshort}} イベントを生成する IBM サービスは、{{site.data.keyword.IBM_notm}} クラウドのセキュリティー・ポリシーに従います。 詳しくは、[Trust the security and privacy of IBM Cloud ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/cloud/security){: new_window} を参照してください。
* {{site.data.keyword.cloudaccesstrailshort}} サービスは、クラウド・サービスの状態を変更するユーザー開始アクションを取り込みます。 この情報からデータベースまたはアプリケーションに直接アクセスすることはできません。
* 許可されたユーザーのみが {{site.data.keyword.cloudaccesstrailshort}} イベント・ログの表示およびモニターを行うことができます。 各ユーザーは、{{site.data.keyword.cloud_notm}} での固有の ID によって識別されます。
