---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, IAM events

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


# IAM 事件
{: #at_events_iam}

作为安全主管、审计员或管理者，您可以使用 {{site.data.keyword.cloudaccesstrailfull}} 服务来跟踪用户和应用程序与 {{site.data.keyword.Bluemix}} 中 {{site.data.keyword.iamlong}} (IAM) 服务的交互方式。
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull_notm}} 服务会记录用户发起的用于在 {{site.data.keyword.cloud_notm}} 中更改服务状态的活动。有关更多信息，请参阅[关于 {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov)。

要开始监视用户的操作，请参阅[{{site.data.keyword.cloudaccesstrailfull_notm}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started-with-cla#getting-started-with-cla)。 

发起方可以为用户、服务或应用程序。
{: tip}

## 管理访问组事件
{: #at_events_iam_access}

下表列出生成事件的操作：

|操作|描述|
|----------|---------|
| `iam-groups.group.create`   |发起方创建访问组时，将生成事件。| 
| `iam-groups.group.read`     |发起方查看与访问组相关的信息时，将生成事件。|
| `iam-groups.group.update`   |发起方更新组名或描述时，将生成事件。|
| `iam-groups.group.delete`   |发起方删除访问组时，将生成事件。|
| `iam-groups.member.add`     |发起方将成员添加至访问组时，将生成事件。|
| `iam-groups.member.delete`  |发起方从访问组除去成员时，将生成事件。|
| `iam-groups.member.read`    |发起方检查成员的成员资格时，将生成事件。|
| `iam-groups.rule.read`      |发起方查看访问组中的规则时，将生成事件。|
| `iam-groups.rule.create`    |发起方将规则添加至访问组时，将生成事件。|
| `iam-groups.rule.update`    |发起方修改规则名称时，将生成事件。|
| `iam-groups.rule.delete`    |发起方从访问组删除规则时，将生成事件。|
{: caption="表 1. 管理访问组操作" caption-side="top"} 



## 使用服务标识事件
{: #at_events_iam_serviceids}

下表列出生成事件的操作：

|操作|描述|
|----------|---------|
| `iam-identity.account-serviceid.create` |发起方创建服务标识时，将生成事件。| 
| `iam-identity.account-serviceid.update` |发起方重命名服务标识或修改其描述时，将生成事件。| 
| `iam-identity.account-serviceid.delete` |发起方删除服务标识时，将生成事件。| 
{: caption="表 2. 使用服务标识操作" caption-side="top"} 


## 使用 API 密钥事件
{: #at_events_iam_apikeys}

下表列出生成事件的操作：

|操作|描述|
|----------|---------|
| `iam-identity.user-apikey.create`      |发起方创建 API 密钥时，将生成事件。| 
| `iam-identity.user-apikey.update`      |发起方重命名 API 密钥或修改其描述时，将生成事件。|  
| `iam-identity.user-apikey.delete`      |发起方删除 API 密钥时，将生成事件。|  
| `iam-identity.serviceid-apikey.create` |发起方创建服务标识的 API 密钥时，将生成事件。|  
| `iam-identity.serviceid-apikey.delete` |发起方删除服务标识的 API 密钥时，将生成事件。|  
{: caption="表 3. 使用 API 密钥操作" caption-side="top"} 


## 登录事件
{: #at_events_iam_login}

下表列出生成事件的操作：

|操作|描述|
|----------|---------|
| `iam-identity.user-apikey.login`         |用户使用 API 密钥登录到 {{site.data.keyword.cloud_notm}} 时，将生成事件。|  
| `iam-identity.serviceid-apikey.login`    |发起方使用与服务标识关联的 API 密钥登录 {{site.data.keyword.cloud_notm}} 时，将生成事件。|  
| `iam-identity.user-identitycookie.login` |这是发起方请求新的身份 cookie 以执行操作时生成的事件。|
| `iam-identity.user-refreshtoken.login`   |这是发起方登录到 IBM Cloud 时生成的事件，或者是已登录到 IBM Cloud 的发起方请求新的刷新令牌以执行操作时生成的事件。|
{: caption="表 4. 用户登录操作" caption-side="top"} 


## 管理策略事件
{: #at_events_iam_policies}

下表列出生成事件的操作：

|操作|描述|
|----------|---------|
| `iam-am.policy.create` |发起方将策略添加到用户或访问组时，将生成事件。|
| `iam-am.policy.delete` |发起方修改用户或访问组的策略的许可权时，将生成事件。|
| `iam-am.policy.update` |发起方删除分配给用户或访问组的策略时，将生成事件。|
{: caption="表 5. 管理策略操作" caption-side="top"} 


## 查看事件
{: #at_events_iam_ui}

{{site.data.keyword.cloudaccesstrailshort}} 事件在**美国南部**区域**帐户域**中提供。

要查看这些事件，必须在**美国南部**区域中供应 {{site.data.keyword.cloudaccesstrailshort}} 服务的实例。然后，必须打开 {{site.data.keyword.cloudaccesstrailshort}} UI，并切换到帐户域以查看事件。 

有关更多信息，请参阅[查看帐户事件](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-view_acc_events#view_acc_events_account_events)。



