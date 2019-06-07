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

# 新增功能
{: #whatsnew}

瞭解 {{site.data.keyword.cloudaccesstrailshort}} 的最新特性和整合。
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} 已淘汰。從 2019 年 5 月 9 日開始，您無法佈建新的 {{site.data.keyword.cloudaccesstrailshort}} 實例。現有的超值方案實例將支援到 2019 年 9 月 30 日為止。若要繼續監視 {{site.data.keyword.cloud_notm}} 帳戶的活動，請佈建 [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) 的實例。
{: deprecated}

如需與 {{site.data.keyword.cloudaccesstrailshort}} 整合的最新服務清單，請參閱[雲端服務](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-cloud_services#cloud_services)。
{: important}


## 2019 年 3 月
{: #march2019}

* {{site.data.keyword.cloudaccesstrailshort}} CLI

我們已識別 Activity Tracker CLI 的問題。即將釋出新版 CLI 以解決此問題。

如果您從指令行使用 `ibmcloud login` 登入 {{site.data.keyword.cloud_notm}}，然後執行 {{site.data.keyword.cloudaccesstrailshort}} 指令，則對於您執行的任何 {{site.data.keyword.cloudaccesstrailshort}} 指令，您會得到下列錯誤 `Failed: Unauthorized`。 

同時，若要繼續使用 CLI，請使用下列指令登入 {{site.data.keyword.cloud_notm}}：

|地區|指令|
|--------|---------|
| `US South` | `bx login -a api.ng.bluemix.net -o OrgName -s SpaceName` |
| `EU DE`     | `bx login -a api.eu-de.bluemix.net -o OrgName -s SpaceName` |
| `EU DE`     | `bx login -a api.au-syd.bluemix.net -o OrgName -s SpaceName` |
{: caption="表 1. 指令" caption-side="top"} 

## 2019 年 2 月
{: #february2019}

* **您可以使用 {{site.data.keyword.cloudaccesstrailshort}} 來監視 {{site.data.keyword.GlobalizationPipeline_short}} 服務。**

    {{site.data.keyword.GlobalizationPipeline_short}} 讓應用程式開發人員能快速地將翻譯過的應用程式發行給全球客戶。

    如需 {{site.data.keyword.cloudaccesstrailshort}} 事件的相關資訊，請參閱 [{{site.data.keyword.GlobalizationPipeline_short}} 所產生的事件](/docs/services/GlobalizationPipeline?topic=GlobalizationPipeline-gpat_events#gpat_events)。








