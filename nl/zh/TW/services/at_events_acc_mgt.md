---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, account events

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

# 帳戶管理事件  
{: #at_events_acc_mgt}

身為安全性管理者、審核員或管理員，您可以使用 {{site.data.keyword.cloudaccesstrailfull}} 服務來追蹤使用者及應用程式如何與 {{site.data.keyword.Bluemix}} 帳戶互動。
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} 已淘汰。從 2019 年 5 月 9 日開始，您無法佈建新的 {{site.data.keyword.cloudaccesstrailshort}} 實例。現有的超值方案實例將支援到 2019 年 9 月 30 日為止。若要繼續監視 {{site.data.keyword.cloud_notm}} 帳戶的活動，請佈建 [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) 的實例。
{: deprecated}

{{site.data.keyword.cloudaccesstrailfull_notm}} 服務會記錄使用者起始的活動，這些活動會在 {{site.data.keyword.cloud_notm}} 中變更服務的狀態。如需相關資訊，請參閱[關於 {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov)。

若要開始監視您的使用者動作，請參閱 [{{site.data.keyword.cloudaccesstrailfull_notm}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started)。 



## 管理帳戶的事件
{: #at_events_acc_mgt_account}

下表列出在呼叫時會產生事件的 API 方法：

<table>
  <caption>產生事件的動作</caption>
  <tr>
    <th>動作</th>
	  <th>說明</th>
  </tr>
  <tr>
    <td>billing.account.create</td>
	  <td>將帳戶 ID 指派給帳戶之後，當您佈建該帳戶時會產生事件。</td>
  </tr>
  <tr>
    <td>billing.account.update</td>
	  <td>當您更新帳戶的相關資訊時，會產生事件。</td>
  </tr>
  <tr>
    <td>billing.account.active</td>
	  <td>驗證帳戶時會產生事件，亦即，當該帳戶變成作用中時會產生事件。</td>
  </tr>
  <tr>
    <td>billing.account.subscription.create</td>
	  <td>當您建立<a href="/docs/account?topic=account-accounts#subscription-account">訂閱帳戶</a>時，會產生事件。</td>
  </tr>
</table>



## 管理使用者的事件
{: #at_events_acc_mgt_users}

下表列出在呼叫時會產生事件的 API 方法：

<table>
  <caption>產生事件的動作</caption>
  <tr>
    <th>動作</th>
	  <th>說明</th>
  </tr>
  <tr>
    <td>user-management.user.create</td>
	  <td>當您將邀請傳送至使用者以加入帳戶時，會產生事件。</br>帳戶擁有者是帳戶中唯一可執行此動作的使用者。</td>
  </tr>
  <tr>
    <td>user-management.user.active</td>
	  <td>當您啟動帳戶中的使用者時，會產生事件。</br>當使用者驗證其電子郵件位址時，即會產生事件。</td>
  </tr>
  <tr>
    <td>user-management.user.delete</td>
	  <td>當您從帳戶中移除使用者時，會產生事件。</br>帳戶擁有者是帳戶中唯一可執行此動作的使用者。</td>
  </tr>
</table>

## 管理組織的事件
{: #at_events_acc_mgt_org}

下表列出在呼叫時會產生事件的 API 方法：

<table>
  <caption>產生事件的動作</caption>
  <tr>
    <th>動作</th>
	  <th>說明</th>
  </tr>
  <tr>
    <td>billing.account.org.create</td>
	  <td>當您將組織新增至帳戶時，會產生事件。</td>
  </tr>
</table>

## 尋找事件的位置
{: #at_events_acc_mgt_ui}

{{site.data.keyword.cloudaccesstrailshort}} 事件可在**美國南部**地區**帳戶網域**中取得。 

若要檢視這些事件，您必須在**美國南部**地區中佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務的實例。然後，您必須開啟 {{site.data.keyword.cloudaccesstrailshort}} 使用者介面，並切換至帳戶網域以查看事件。 

如需相關資訊，請參閱[檢視帳戶事件](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-view_acc_events#view_acc_events_account_events)。








