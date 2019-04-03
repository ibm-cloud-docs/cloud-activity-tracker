---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

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


# {{site.data.keyword.cloudaccesstrailshort}} 事件
{: #events}

使用 {{site.data.keyword.cloudaccesstrailfull}} 服务以跟踪 {{site.data.keyword.Bluemix}} 中的 {{site.data.keyword.cloudaccesstrailshort}}。
{:shortdesc}



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
