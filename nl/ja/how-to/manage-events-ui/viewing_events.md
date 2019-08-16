---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, view events, UI

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

# イベントの表示
{: #view_acc_events}

{{site.data.keyword.cloudaccesstrailshort}} UI を介して {{site.data.keyword.cloud_notm}} コンソールで、または Kibana を介して、イベントを表示できます。
{:shortdesc}
   
{{site.data.keyword.cloudaccesstrailfull}} は非推奨になりました。 2019 年 5 月 9 日以降、新しい {{site.data.keyword.cloudaccesstrailshort}} インスタンスをプロビジョンできません。 既存のプレミアム・プランのインスタンスは、2019 年 9 月 30 日までサポートされます。 {{site.data.keyword.cloud_notm}} アカウントのアクティビティーのモニタリングを続行するには、[{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) のインスタンスをプロビジョンします。
{: deprecated}


## アカウント・イベントの表示
{: #view_acc_events_account_events}

{{site.data.keyword.cloudaccesstrailshort}} UI または Kibana を介して、{{site.data.keyword.cloudaccesstrailshort}} アカウント・ドメイン内のイベントを表示できます。

**アカウント所有者**は、{{site.data.keyword.cloudaccesstrailshort}} UI または Kibana を介して {{site.data.keyword.cloudaccesstrailshort}} アカウント・ドメイン内のイベントを表示する許可を持っています。

**アカウントのメンバー**が地域のアカウント・イベントを表示するには、以下を考慮する必要があります。

* {{site.data.keyword.cloudaccesstrailshort}} がプロビジョンされたスペースで*開発者*役割を持っている必要があります。 詳しくは、[CF 役割の付与](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-grant_permissions#grant_cf_role)を参照してください。

* その地域での*ビューアー* 役割が指定された、{{site.data.keyword.loganalysisshort}} サービスの IAM ポリシーを持っている必要があります。 ビューアー役割は、必要な最小の IAM 役割です。 詳しくは、[IAM 許可の付与](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-grant_permissions#grant_iam_policy)を参照してください。

* Kibana を介してイベントを表示できます。 Kibana の起動方法について詳しくは、『[Web ブラウザーから Kibana へのナビゲート](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-launch_kibana#launch_Kibana_from_browser)』を参照してください。



## スペース・イベントの表示
{: #view_acc_events_space_events}

{{site.data.keyword.cloudaccesstrailshort}} スペース・ドメイン内のイベントを、{{site.data.keyword.cloudaccesstrailshort}} UI を介して表示できます。 プレミアム・プランをご使用の場合は、Kibana を介してイベントを表示することもできます。

**アカウント所有者**は、任意の {{site.data.keyword.cloudaccesstrailshort}} スペース・ドメインのイベントを表示する許可を持っています。

**アカウントのメンバー**は、{{site.data.keyword.cloudaccesstrailshort}} がプロビジョンされたスペースで*開発者* 役割を持っている必要があります。


