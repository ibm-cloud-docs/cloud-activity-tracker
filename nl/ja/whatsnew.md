---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, news

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

# 新機能
{: #whatsnew}

{{site.data.keyword.cloudaccesstrailshort}} に関する最新のフィーチャーと統合について説明します。
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} は非推奨になりました。 2019 年 5 月 9 日以降、新しい {{site.data.keyword.cloudaccesstrailshort}} インスタンスをプロビジョンできません。 既存のプレミアム・プランのインスタンスは、2019 年 9 月 30 日までサポートされます。 {{site.data.keyword.cloud_notm}} アカウントのアクティビティーのモニタリングを続行するには、[{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) のインスタンスをプロビジョンします。
{: deprecated}

{{site.data.keyword.cloudaccesstrailshort}} と統合されたサービスの最新リストについては、[クラウド・サービス](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-cloud_services#cloud_services)を参照してください。
{: important}


## 2019 年 3 月
{: #march2019}

* {{site.data.keyword.cloudaccesstrailshort}} CLI

Activity Tracker CLI の問題を特定しました。 この問題に対処するために、CLI の新しいバージョンをリリースします。

コマンド・ラインから `ibmcloud login` を使用して {{site.data.keyword.cloud_notm}} にログインし、{{site.data.keyword.cloudaccesstrailshort}} コマンドを実行すると、次のエラーが発生します。`失敗: 無許可` 実行するすべての {{site.data.keyword.cloudaccesstrailshort}} コマンド。 

一方、CLI での作業を続行するには、次のコマンドを使用して {{site.data.keyword.cloud_notm}} にログインします。

| 地域 | コマンド |
|--------|---------|
| `米国南部` | `bx login -a api.ng.bluemix.net -o OrgName -s SpaceName` |
| `EU DE`    | `bx login -a api.eu-de.bluemix.net -o OrgName -s SpaceName` |
| `EU DE`    | `bx login -a api.au-syd.bluemix.net -o OrgName -s SpaceName` |
{: caption="表 1. コマンド" caption-side="top"} 

## 2019 年 2 月
{: #february2019}

* **{{site.data.keyword.GlobalizationPipeline_short}} サービスを {{site.data.keyword.cloudaccesstrailshort}} でモニターできます。**

    {{site.data.keyword.GlobalizationPipeline_short}} は、アプリケーション開発者が翻訳済みアプリケーションをグローバルな顧客に素早くリリースすることを可能にします。

    {{site.data.keyword.cloudaccesstrailshort}} イベントについて詳しくは、[{{site.data.keyword.GlobalizationPipeline_short}} によって生成されるイベント](/docs/services/GlobalizationPipeline?topic=GlobalizationPipeline-gpat_events#gpat_events)を参照してください。








