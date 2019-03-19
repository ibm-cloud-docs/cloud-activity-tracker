---

copyright:
  years: 2016, 2019
lastupdated: "2019-01-23"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# 服務實例事件  
{: #at_events_rc}

身為安全性管理者、審核員或管理員，您可以使用 {{site.data.keyword.cloudaccesstrailfull}} 服務來追蹤使用者及應用程式如何與 {{site.data.keyword.Bluemix}} 服務互動。
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull_notm}} 服務會記錄使用者起始的活動，這些活動會在 {{site.data.keyword.cloud_notm}} 中變更服務的狀態。如需相關資訊，請參閱[關於 {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#activity_tracker_ov )。

若要開始監視您的使用者動作，請參閱 [{{site.data.keyword.cloudaccesstrailfull_notm}}](/docs/services/cloud-activity-tracker/index.html#getting-started-with-cla)。 

## 佈建及管理服務實例的事件
{: #at_events_rc_provision}

下表列出在呼叫時會產生事件的 API 方法：

<table>
  <caption>產生事件的動作</caption>
  <tr>
    <th>動作</th>
	  <th>說明</th>
  </tr>
  <tr>
    <td><i>service_name</i>.instance.create</td>
	  <td>當您佈建服務實例時，會產生事件。</td>
  </tr>
  <tr>
    <td><i>service_name</i>.instance.update</td>
	  <td>當您重新命名服務實例或變更服務方案時，會產生事件。</td>
  </tr>
  <tr>
    <td><i>service_name</i>.instance.delete</td>
	  <td>在刪除服務實例時，會產生事件。</td>
  </tr>
</table>


##  管理與服務實例相關聯之 API 金鑰的事件
{: #at_events_rc_keys}

下表列出在呼叫時會產生事件的 API 方法：

<table>
  <caption>產生事件的動作</caption>
  <tr>
    <th>動作</th>
	  <th>說明</th>
  </tr>
  <tr>
    <td><i>service_name</i>.key.create</td>
	  <td>透過服務實例使用者介面的*服務認證* 區段為服務實例建立 API 金鑰時，會產生事件。</td>
  </tr>
  <tr>
    <td><i>service_name</i>.key.delete</td>
	  <td>從服務實例使用者介面的*服務認證* 區段中刪除與服務實例相關聯的 API 金鑰時，會產生事件。</td>
  </tr>
</table>

##  將服務實例連結至應用程式的事件
{: #at_events_rc_bind}

下表列出在呼叫時會產生事件的 API 方法：

<table>
  <caption>產生事件的動作</caption>
  <tr>
    <th>動作</th>
	  <th>說明</th>
  </tr>
  <tr>
    <td><i>service_name</i>.binding.create</td>
	  <td>當您將服務實例連結至應用程式時，會產生事件。</td>
  </tr>
  <tr>
    <td><i>service_name</i>.binding.delete</td>
	  <td>當您從應用程式取消連結服務實例時，會產生事件。</td>
  </tr>
</table>




## 尋找事件的位置
{: #at_events_rc_ui}

{{site.data.keyword.cloudaccesstrailshort}} 事件可在**美國南部**地區**帳戶網域**中取得。

若要檢視這些事件，您必須在**美國南部**地區中佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務的實例。然後，您必須開啟 {{site.data.keyword.cloudaccesstrailshort}} 使用者介面，並切換至帳戶網域以查看事件。如需相關資訊，請參閱[檢視帳戶事件](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/viewing_events.html#view_acc_events_account_events)。


