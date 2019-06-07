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

# 新增内容
{: #whatsnew}

了解 {{site.data.keyword.cloudaccesstrailshort}} 的最新功能和集成。
{:shortdesc}

不推荐使用 {{site.data.keyword.cloudaccesstrailfull}}。从 2019 年 5 月 9 日开始，无法供应新的 {{site.data.keyword.cloudaccesstrailshort}} 实例。对现有高端套餐实例的支持会持续到 2019 年 9 月 30 日。要继续监视 {{site.data.keyword.cloud_notm}} 帐户的活动，请供应 [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) 的实例。
{: deprecated}

有关与 {{site.data.keyword.cloudaccesstrailshort}} 集成的服务的最新列表，请参阅[云服务](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-cloud_services#cloud_services)。
{: important}


## 2019 年 3 月
{: #march2019}

* {{site.data.keyword.cloudaccesstrailshort}} CLI

我们已确定 Activity Tracker CLI 存在的问题。我们将发布此 CLI 的新版本来解决该问题。

如果您通过在命令行中使用 `ibmcloud login` 登录到 {{site.data.keyword.cloud_notm}}，然后运行了 {{site.data.keyword.cloudaccesstrailshort}} 命令，那么对于运行的任何 {{site.data.keyword.cloudaccesstrailshort}} 命令，都会收到以下错误：`失败：未获授权`。 

同时，要继续使用此 CLI，请使用以下命令登录到 {{site.data.keyword.cloud_notm}}：

|区域|命令|
|--------|---------|
| `US South` | `bx login -a api.ng.bluemix.net -o OrgName -s SpaceName` |
| `EU DE`    | `bx login -a api.eu-de.bluemix.net -o OrgName -s SpaceName` |
| `EU DE`    | `bx login -a api.au-syd.bluemix.net -o OrgName -s SpaceName` |
{: caption="表 1. 命令" caption-side="top"} 

## 2019 年 2 月
{: #february2019}

* **您可以使用 {{site.data.keyword.cloudaccesstrailshort}} 来监视 {{site.data.keyword.GlobalizationPipeline_short}} 服务。**


    {{site.data.keyword.GlobalizationPipeline_short}} 支持应用程序开发者快速将翻译的应用程序发布到全球客户。

    有关 {{site.data.keyword.cloudaccesstrailshort}} 事件的信息，请参阅 [{{site.data.keyword.GlobalizationPipeline_short}} 生成的事件](/docs/services/GlobalizationPipeline?topic=GlobalizationPipeline-gpat_events#gpat_events)。








