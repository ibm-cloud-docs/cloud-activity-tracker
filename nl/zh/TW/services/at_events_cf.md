---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, Cloud Foundry events, CF

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


# Cloud Foundry 事件
{: #cf}

請使用 {{site.data.keyword.cloudaccesstrailfull}} 服務來追蹤與 {{site.data.keyword.Bluemix}} 中的核心平台服務互動。
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} 已淘汰。從 2019 年 5 月 9 日開始，您無法佈建新的 {{site.data.keyword.cloudaccesstrailshort}} 實例。現有的超值方案實例將支援到 2019 年 9 月 30 日為止。若要繼續監視 {{site.data.keyword.cloud_notm}} 帳戶的活動，請佈建 [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) 的實例。
{: deprecated}

下列清單概述將事件傳送至 {{site.data.keyword.cloudaccesstrailshort}} 服務的不同核心平台作業： 

* 佈建服務、移除服務，以及變更服務的名稱。
* 為帳戶中的使用者授與、更新及撤銷 Cloud Foundry 空間角色。
* 建立平台 API 金鑰、重新命名平台金鑰，以及刪除平台金鑰。


## 與型錄服務互動時所產生的事件
{: #cf_catalog}

當您佈建服務、移除服務，以及變更服務名稱時，會產生一個事件，並將該事件傳送至 {{site.data.keyword.cloudaccesstrailshort}} 中與可供帳戶使用該服務之 Cloud Foundry 空間相關聯的空間網域。 

例如，您在美國南部地區的空間 B 中佈建服務 A。即會產生一個事件。若要查看事件，您必須在美國南部（在您佈建該服務的相同空間）中佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務。然後，您可以透過 {{site.data.keyword.cloudaccesstrailshort}} 服務使用者介面來查看事件。

下表列出會產生事件的型錄動作：

<table>
  <caption>型錄動作</caption>
  <tr>
    <th>動作</th>
	  <th>說明</th>
  <tr>
  <tr>
    <td>`audit.service_instance.create`</td>
	<td>當您在 Cloud Foundry 空間中佈建服務時，會建立事件。</td>
  </tr>
  <tr>
    <td>`audit.service_instance.update`</td>
	<td>當您變更 Cloud Foundry 空間中可用服務的名稱時，會建立事件。</td>
  </tr>
  <tr>
    <td>`audit.service_instance.delete`</td>
	<td>當您從帳戶中的 Cloud Foundry 空間移除服務時，會建立事件。</td>
  </tr>
</table>


 	

## 管理帳戶中的 Cloud Foundry 角色時所產生的事件
{: #cf_cfroles} 

當您為帳戶中的使用者授與或撤銷（刪除）Cloud Foundry 角色時，會產生事件，並將該事件傳送至 {{site.data.keyword.cloudaccesstrailshort}} 中和授與或撤銷該角色之 Cloud Foundry 空間相關聯的空間網域。 

例如，您在美國南部地區的空間 B 中，為使用者 A 授與*空間管理員* 角色。即會產生一個事件。若要查看事件，您必須在美國南部（在您要管理使用者 CF 許可權的相同空間）中佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務。然後，您可以透過 {{site.data.keyword.cloudaccesstrailshort}} 服務使用者介面來查看事件。


下表列出當您管理使用者的 Cloud Foundry 角色時，會產生 {{site.data.keyword.cloudaccesstrailshort}} 事件的動作：

<table>
  <caption>管理 Cloud Foundry 角色的動作</caption>
  <tr>
    <th>動作</th>
	<th>說明</th>
  <tr>
  <tr>
    <td>`audit.user.space_manager_add`</td>
	<td>在 Cloud Foundry 空間中為使用者授與*管理員* 角色。</td>
  </tr>
  <tr>
    <td>`audit.user.space_developer_add`</td>
	<td>在 Cloud Foundry 空間中為使用者授與*開發人員* 角色。</td>
  </tr>
  <tr>
    <td>`audit.user.space_auditor_add`</td>
	<td>在 Cloud Foundry 空間中為使用者授與*審核* 角色。</td>
  </tr>
  <tr>
    <td>`audit.user.space_manager_remove`</td>
	<td>在 Cloud Foundry 空間中刪除使用者的*管理員* 角色。</td>
  </tr>
  <tr>
    <td>`audit.user.space_developer_remove`</td>
	<td>在 Cloud Foundry 空間中刪除使用者的*開發人員* 角色。</td>
  </tr>
  <tr>
    <td>`audit.user.space_auditor_remove`</td>
	<td>在 Cloud Foundry 空間中刪除使用者的*審核* 角色。</td>
  </tr>
</table>






	
 	
 	
