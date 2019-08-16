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


# 转换到 {{site.data.keyword.at_full_notm}}
{: #transition}

{{site.data.keyword.cloudaccesstrailfull}} 在 2019 年 5 月 9 日被弃用。[了解更多](https://www.ibm.com/blogs/cloud-archive/2019/04/deprecating-ibm-cloud-activity-tracker/)。该服务已替换为 {{site.data.keyword.at_full_notm}}。[了解更多](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started)。
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} 已被弃用。从 2019 年 5 月 9 日开始，您无法供应新的 {{site.data.keyword.cloudaccesstrailshort}} 实例。对现有高端套餐实例的支持会持续到 2019 年 9 月 30 日。要继续监视 {{site.data.keyword.cloud_notm}} 帐户的活动，请供应 [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) 的实例。
{: deprecated}


要迁移至 {{site.data.keyword.at_full_notm}}，请完成以下步骤： 

1. 将 {{site.data.keyword.cloudaccesstrailfull}} 中存储的事件保存一份副本以供长期搜索。您可以使用 {{site.data.keyword.cloudaccesstrailshort}} CLI 或 API。 

    对于包含旧 {{site.data.keyword.cloudaccesstrailshort}} 实例的每个 Cloud Foundry 空间，以及您目前监视的每个区域中的每个帐户域，务必保存其空间事件。

    * [使用 CLI 下载事件](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-downloading_events)。

    * [使用 API 下载事件](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-downloading_events_api)。

2. 供应 [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-provision)。

    每个区域只能供应 1 个实例。 
    
3. 创建并配置访问组以管理 {{site.data.keyword.cloud_notm}} 中的许可权。 

    * [对用户或服务标识授予管理许可权](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-iam_manage_events)。

    * [对用户或服务标识授予用户许可权](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-iam_view_events)。

4. 在 {{site.data.keyword.at_full_notm}} 中定义视图和仪表板，以用于分析和管理事件。[了解更多](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-views)。

    将 Kibana 仪表板迁移到 LogDNA 仪表板不是自动执行的。您必须手动实施新的仪表板。 

    请注意，在 LogDNA 中您只能实现直方图和饼图这两种可视化效果。

5. [可选] 配置 {{site.data.keyword.at_full_notm}} 实例的归档。 

    您可以将事件归档到 {{site.data.keyword.cos_full_notm}} (COS)。[了解更多](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-archiving)。

    **注：**您负责供应 COS 实例以用于将事件归档，并负责维护归档事件。 

    只有具有付费套餐的 {{site.data.keyword.at_full_notm}} 实例才需要执行此步骤。

6. 探索其他功能，例如[警报](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-alerts)。


当您准备好停止通过旧 {{site.data.keyword.cloudaccesstrailshort}} 实例监视云活动时，请完成以下步骤：

1. 从 {{site.data.keyword.cloud_notm}} 控制台中删除旧 {{site.data.keyword.cloudaccesstrailshort}} 实例。
2. 除去用户对这些旧实例的所有许可权。 


