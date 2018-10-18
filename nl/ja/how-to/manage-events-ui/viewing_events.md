---

copyright:
  years: 2016, 2018
lastupdated: "2018-07-09"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}



# イベントの表示
{: #view_acc_events}

{{site.data.keyword.cloudaccesstrailshort}} UI を介して {{site.data.keyword.Bluemix_notm}} コンソールで、または Kibana を介して、イベントを表示できます。
{:shortdesc}
   

## アカウント・イベントの表示
{: #account_events}

{{site.data.keyword.cloudaccesstrailshort}} UI または Kibana を介して、{{site.data.keyword.cloudaccesstrailshort}} アカウント・ドメイン内のイベントを表示できます。

**アカウント所有者**は、{{site.data.keyword.cloudaccesstrailshort}} UI または Kibana を介して {{site.data.keyword.cloudaccesstrailshort}} アカウント・ドメイン内のイベントを表示する許可を持っています。

**アカウントのメンバー**が地域のアカウント・イベントを表示するには、以下を考慮する必要があります。

* {{site.data.keyword.cloudaccesstrailshort}} がプロビジョンされたスペースで*開発者*役割を持っている必要があります。詳しくは、[CF 役割の付与](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_cf_role)を参照してください。

* その地域での*ビューアー* 役割が指定された、{{site.data.keyword.loganalysisshort}} サービスの IAM ポリシーを持っている必要があります。ビューアー役割は、必要な最小の IAM 役割です。詳しくは、[IAM 許可の付与](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_iam_policy)を参照してください。

* Kibana を介してイベントを表示できます。Kibana の起動方法について詳しくは、『[Web ブラウザーから Kibana へのナビゲート](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_kibana.html#launch_Kibana_from_browser)』を参照してください。



## スペース・イベントの表示
{: #space_events}

{{site.data.keyword.cloudaccesstrailshort}} スペース・ドメイン内のイベントを、{{site.data.keyword.cloudaccesstrailshort}} UI を介して表示できます。プレミアム・プランをご使用の場合は、Kibana を介してイベントを表示することもできます。

**アカウント所有者**は、任意の {{site.data.keyword.cloudaccesstrailshort}} スペース・ドメインのイベントを表示する許可を持っています。

**アカウントのメンバー**は、{{site.data.keyword.cloudaccesstrailshort}} がプロビジョンされたスペースで*開発者* 役割を持っている必要があります。


