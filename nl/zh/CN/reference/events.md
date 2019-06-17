---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, events

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
{:deprecated: .deprecated}


# {{site.data.keyword.cloudaccesstrailshort}} 事件
{: #events}

使用 {{site.data.keyword.cloudaccesstrailfull}} 服务以跟踪 {{site.data.keyword.Bluemix}} 中的 {{site.data.keyword.cloudaccesstrailshort}}。
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} 已被弃用。从 2019 年 5 月 9 日开始，您无法供应新的 {{site.data.keyword.cloudaccesstrailshort}} 实例。对现有高端套餐实例的支持会持续到 2019 年 9 月 30 日。要继续监视 {{site.data.keyword.cloud_notm}} 帐户的活动，请供应 [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) 的实例。
{: deprecated}


## 事件列表
{: #actions}

下表列出生成事件的操作：

<table>
  <caption>表 1. 生成事件的操作列表</caption>
  <tr>
    <th>操作</th>
	  <th>描述</th>
  <tr>
  <tr>
    <td>read.events</td>
	  <td>获取有关存储的事件的信息。</td>
  </tr>
  <tr>
    <td>create.sessions</td>
	  <td>创建可用于下载事件的会话。</td>
  </tr>
  <tr>
    <td>delete.session</td>
	  <td>删除会话。</td>
  </tr>
  <tr>
    <td>read.sessions</td>
	  <td>列出会话。</td>
  </tr>
  <tr>
    <td>download.events</td>
	  <td>下载事件。</td>
  </tr>
  <tr>
    <td>delete.events</td>
	  <td>删除事件。</td>
  </tr>
</table>


## 在何处查找事件
{: #ui}
 	
{{site.data.keyword.cloudaccesstrailshort}} 事件在供应 {{site.data.keyword.cloudaccesstrailshort}} 服务的 Cloud Foundry 空间中提供。
