---

copyright:
  years: 2016, 2019
lastupdated: "2019-06-06"

keywords: IBM Cloud, Activity Tracker, migration

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


# {{site.data.keyword.at_full_notm}} への移行
{: #transition}

{{site.data.keyword.cloudaccesstrailfull}} は、2019 年 5 月 9 日に非推奨になりました。[詳細はこちら](https://www.ibm.com/blogs/cloud-archive/2019/04/deprecating-ibm-cloud-activity-tracker/)。サービスは {{site.data.keyword.at_full_notm}} に置き換えられます。[詳細はこちら](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started)。
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} は非推奨になりました。 2019 年 5 月 9 日以降、新しい {{site.data.keyword.cloudaccesstrailshort}} インスタンスをプロビジョンできません。 既存のプレミアム・プランのインスタンスは、2019 年 9 月 30 日までサポートされます。 {{site.data.keyword.cloud_notm}} アカウントのアクティビティーのモニタリングを続行するには、[{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) のインスタンスをプロビジョンします。
{: deprecated}


{{site.data.keyword.at_full_notm}} にマイグレーションするには、以下のステップを実行します。 

1. 長期間の検索のために {{site.data.keyword.cloudaccesstrailfull}} に保管されているイベントのコピーを保存します。{{site.data.keyword.cloudaccesstrailshort}} CLI または API を使用できます。 

    レガシー {{site.data.keyword.cloudaccesstrailshort}} インスタンスがある各 Cloud Foundry スペース用と、現在モニターしている各地域の各アカウント・ドメイン用のスペース・イベントを保存するようにしてください。

    * [CLI を使用して、イベントをダウンロードします](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-downloading_events)。

    * [API を使用して、イベントをダウンロードします](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-downloading_events_api)。

2. [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-provision) をプロビジョンします。

    1 地域につき 1 つのインスタンスのみプロビジョンできます。 
    
3. {{site.data.keyword.cloud_notm}} での許可の管理のために、アクセス・グループを作成して構成します。 

    * [ユーザーまたはサービス ID に管理許可を付与します](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-iam_manage_events)。

    * [ユーザーまたはサービス ID にユーザー許可を付与します](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-iam_view_events)。

4. イベントを分析および管理するために、{{site.data.keyword.at_full_notm}} にビューおよびダッシュボードを定義します。[詳細はこちら](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-views)。

    Kibana ダッシュボードから LogDNA ダッシュボードへのマイグレーションは自動化されていません。新しいダッシュボードを手動で実装する必要があります。 

    LogDNA では、実装可能な可視化はヒストグラムとパイだけであることに注意してください。

5. [オプション] {{site.data.keyword.at_full_notm}} インスタンスのアーカイブを構成します。 

    イベントは {{site.data.keyword.cos_full_notm}} (COS) にアーカイブできます。[詳細はこちら](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-archiving)。

    **注:** イベントのアーカイブ使用される COS インスタンスのプロビジョン、およびアーカイブされたイベントの保守は、お客様の責任で行ってください。 

    このステップは、有料プランがある {{site.data.keyword.at_full_notm}} インスタンスにのみ必要です。

6. [アラート](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-alerts)などのその他のフィーチャーを探索します。


レガシー {{site.data.keyword.cloudaccesstrailshort}} インスタンスを使用したクラウド・アクティビティーのモニタリングを停止する準備ができたら、以下のステップを実行します。

1. {{site.data.keyword.cloud_notm}} コンソールから、レガシー {{site.data.keyword.cloudaccesstrailshort}} インスタンスを削除します。
2. これらのレガシー・インスタンスを操作するユーザーに対するすべての許可を削除します。 


