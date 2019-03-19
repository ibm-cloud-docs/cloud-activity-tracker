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


# IAM 事件
{: #at_events_iam}

身為安全性管理者、審核員或管理員，您可以使用 {{site.data.keyword.cloudaccesstrailfull}} 服務來追蹤使用者及應用程式如何與 {{site.data.keyword.Bluemix}} 中的 {{site.data.keyword.iamlong}} (IAM) 服務互動。
{:shortdesc}

{{site.data.keyword.cloudaccesstrailshort}} 服務會記錄使用者起始的活動，這些活動會在 {{site.data.keyword.cloud_notm}} 中變更服務的狀態。如需相關資訊，請參閱[關於 {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#activity_tracker_ov )。

若要開始監視您的使用者動作，請參閱 [{{site.data.keyword.cloudaccesstrailfull_notm}}](/docs/services/cloud-activity-tracker/index.html#getting-started-with-cla)。 

起始者可以是使用者、服務或應用程式。
{: tip}

## 管理存取群組事件
{: #at_events_iam_access}

下表列出產生事件的動作：

|動作|說明|
|----------|---------|
| `iam-groups.group.create`   | 起始者建立存取群組時會產生事件。| 
| `iam-groups.group.read`     | 起始者查看與存取群組相關的資訊時會產生事件。|
| `iam-groups.group.update`   | 起始者更新群組名稱或說明時會產生事件。|
| `iam-groups.group.delete`   | 起始者刪除存取群組時會產生事件。|
| `iam-groups.member.add`     | 起始者將成員新增至存取群組時會產生事件。|
| `iam-groups.member.delete`  | 起始者從存取群組中移除成員時會產生事件。|
| `iam-groups.member.read`    | 起始者檢查成員的成員資格時會產生事件。|
| `iam-groups.rule.read`      | 起始者檢視存取群組中的規則時會產生事件。|
| `iam-groups.rule.create`    | 起始者將規則新增至存取群組時會產生事件。|
| `iam-groups.rule.update`    | 起始者修改規則名稱時會產生事件。|
| `iam-groups.rule.delete`    | 起始者從存取群組中刪除規則時會產生事件。|
{: caption="表 1. 管理存取群組動作" caption-side="top"} 



## 使用服務 ID 事件
{: #at_events_iam_serviceids}

下表列出產生事件的動作：

|動作|說明|
|----------|---------|
| `iam-identity.account-serviceid.create` | 起始者建立服務 ID 時會產生事件。| 
| `iam-identity.account-serviceid.update` | 起始者重新命名服務 ID 或修改其說明時會產生事件。| 
| `iam-identity.account-serviceid.delete` | 起始者刪除服務 ID 時會產生事件。| 
{: caption="表 2. 使用服務 ID 動作" caption-side="top"} 


## 使用 API 金鑰事件
{: #at_events_iam_apikeys}

下表列出產生事件的動作：

|動作|說明|
|----------|---------|
| `iam-identity.user-apikey.create`      | 起始者建立 API 金鑰時會產生事件。| 
| `iam-identity.user-apikey.update`      | 起始者重新命名 API 金鑰或修改其說明時會產生事件。|  
| `iam-identity.user-apikey.delete`      | 起始者刪除 API 金鑰時會產生事件。|  
| `iam-identity.serviceid-apikey.create` | 起始者建立服務 ID 的 API 金鑰時會產生事件。|  
| `iam-identity.serviceid-apikey.delete` | 起始者刪除服務 ID 的 API 金鑰時會產生事件。|  
{: caption="表 3. 使用 API 金鑰動作" caption-side="top"} 


## 登入事件
{: #at_events_iam_login}

下表列出產生事件的動作：

|動作|說明|
|----------|---------|
| `iam-identity.user-apikey.login`         |使用者使用 API 金鑰登入 {{site.data.keyword.cloud_notm}} 時會產生事件。|  
| `iam-identity.serviceid-apikey.login`    |起始者使用與服務 ID 相關聯的 API 金鑰登入 {{site.data.keyword.cloud_notm}} 時會產生事件。|  
| `iam-identity.user-identitycookie.login` | 這是當起始者要求新的身分 Cookie 來執行動作時所產生的事件。|
| `iam-identity.user-refreshtoken.login`   | 這是當起始者登入 IBM Cloud 時，或是已登入 IBM Cloud 的起始者要求新的重新整理記號來執行動作時，所產生的事件。|
{: caption="表 4. 使用者登入動作" caption-side="top"} 


## 管理原則事件
{: #at_events_iam_policies}

下表列出產生事件的動作：

|動作|說明|
|----------|---------|
| `iam-am.policy.create` | 起始者將原則新增至使用者或存取群組時會產生事件。|
| `iam-am.policy.delete` | 起始者修改使用者或存取群組的原則許可權時會產生事件。|
| `iam-am.policy.update` | 起始者刪除指派給使用者或存取群組的原則時會產生事件。|
{: caption="表 5. 管理原則動作" caption-side="top"} 


## 檢視事件
{: #at_events_iam_ui}

{{site.data.keyword.cloudaccesstrailshort}} 事件可在**美國南部**地區**帳戶網域**中取得。

若要檢視這些事件，您必須在**美國南部**地區中佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務的實例。然後，您必須開啟 {{site.data.keyword.cloudaccesstrailshort}} 使用者介面，並切換至帳戶網域以查看事件。如需相關資訊，請參閱[檢視帳戶事件](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/viewing_events.html#account_events)。

