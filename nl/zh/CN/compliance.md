---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, compliance

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


# 合规性
{: #compliance}

[{{site.data.keyword.cloud_notm}} 提供了根据 IBM 严格安全标准构建的云平台和服务](/docs/security/compliance.html#compliance)。{{site.data.keyword.cloudaccesstraillong}} 服务是专为 {{site.data.keyword.cloud_notm}} 而构建的 DevOps 服务。
{:shortdesc}


## 一般数据保护条例

《一般数据保护条例》(GDPR) 致力于在整个欧盟建立协调的数据保护法律框架，目标是让公民重获对个人数据的控制权，同时对世界各地托管和“处理”这些数据的组织实施严格的规定。该条例还引入了有关在欧盟内外自由移动个人数据的规定。 

**免责声明：** {{site.data.keyword.cloudaccesstrailshort}} 服务会存储和显示 {{site.data.keyword.cloud_notm}} 中您帐户下运行的云资源的事件记录。在 {{site.data.keyword.cloudaccesstrailshort}} 中存储的任何事件条目都不得包含个人信息 (PI)，因为企业中的其他用户可能会访问这些事件条目，{{site.data.keyword.IBM_notm}} 也可能会访问这些事件条目来为云服务提供支持。

### 区域
{: #compliance_regions}

{{site.data.keyword.cloudaccesstrailshort}} 服务遵循提供该服务的 {{site.data.keyword.cloud_notm}} Public 区域中的 GDPR 规定。


### 数据保留
{: #compliance_data_retention}

{{site.data.keyword.cloudaccesstrailshort}} 服务包含 2 个数据存储库，用于存储事件数据。 

* 一个存储库用于存储可通过 Kibana 进行分析的事件数据。标准或轻量套餐仅会将数据存储在此存储库中。数据保留时间为 3 天。
* 一个长期存储库，用于托管高端套餐的事件数据。在您配置保留策略或执行手动删除操作之前，这些事件数据会一直存储在该存储库中。缺省情况下，会无限期保留事件。


### 数据删除
{: #compliance_data_deletion}

请考虑以下信息：

* 为 Kibana 提供数据的存储库中存储的事件将在 3 天后删除。

* 长期存储库中存储的事件将在您配置保留策略后几天内删除，或者需要您手动将它们删除。 



如果将付费套餐更改为标准套餐或轻量套餐，那么长期存储库中的事件大约将在一天后删除。

您可以随时开具支持凭单来请求删除所有数据。有关开具 IBM 支持凭单的信息，请参阅[获取支持](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support)。



### 更多信息
{: #compliance_info}

有关更多信息，请参阅：

[{{site.data.keyword.cloud_notm}} 安全合规性](/docs/overview?topic=overview-security#compliance)

[GDPR - {{site.data.keyword.IBM_notm}} 官方页面 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/data-responsibility/gdpr/){:new_window}



