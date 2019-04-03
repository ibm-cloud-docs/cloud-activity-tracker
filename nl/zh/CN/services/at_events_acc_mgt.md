---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

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

# 帐户管理事件  
{: #at_events_acc_mgt}

作为安全主管、审计员或管理者，您可以使用 {{site.data.keyword.cloudaccesstrailfull}} 服务来跟踪用户和应用程序与 {{site.data.keyword.Bluemix}} 帐户的交互方式。
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull_notm}} 服务会记录用户发起的用于在 {{site.data.keyword.cloud_notm}} 中更改服务状态的活动。有关更多信息，请参阅[关于 {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov)。

要开始监视用户的操作，请参阅[{{site.data.keyword.cloudaccesstrailfull_notm}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started-with-cla#getting-started-with-cla)。 



## 用于管理帐户的事件
{: #at_events_acc_mgt_account}

下表列出调用时生成事件的 API 方法：

<table>
  <caption>用于生成事件的操作</caption>
  <tr>
    <th>操作</th>
	  <th>描述</th>
  </tr>
  <tr>
    <td>billing.account.create</td>
	  <td>在帐户标识分配给帐户后，供应此帐户，将生成事件。</td>
  </tr>
  <tr>
    <td>billing.account.update</td>
	  <td>更新帐户相关信息时，将生成事件。</td>
  </tr>
  <tr>
    <td>billing.account.active</td>
	  <td>验证帐户时，将生成事件，即，当帐户变为活动状态时将生成事件。</td>
  </tr>
  <tr>
    <td>billing.account.subscription.create</td>
	  <td>创建<a href="/docs/account?topic=account-accounts#subscription-account">预订帐户</a>时，将生成事件。</td>
  </tr>
</table>



## 用于管理用户的事件
{: #at_events_acc_mgt_users}

下表列出调用时生成事件的 API 方法：

<table>
  <caption>用于生成事件的操作</caption>
  <tr>
    <th>操作</th>
	  <th>描述</th>
  </tr>
  <tr>
    <td>user-management.user.create</td>
	  <td>向用户发送加入帐户邀请时，将生成事件。</br>帐户所有者是帐户中唯一可以执行此操作的用户。</td>
  </tr>
  <tr>
    <td>user-management.user.active</td>
	  <td>激活帐户中用户时，将生成事件。</br>用户验证其电子邮件地址时，将生成事件。</td>
  </tr>
  <tr>
    <td>user-management.account.user.delete</td>
	  <td>从帐户中除去用户时，将生成事件。</br>帐户所有者是帐户中唯一可以执行此操作的用户。</td>
  </tr>
</table>

## 用于管理组织的事件
{: #at_events_acc_mgt_org}

下表列出调用时生成事件的 API 方法：

<table>
  <caption>用于生成事件的操作</caption>
  <tr>
    <th>操作</th>
	  <th>描述</th>
  </tr>
  <tr>
    <td>billing.account.org.create</td>
	  <td>将组织添加到帐户时，将生成事件。</td>
  </tr>
</table>

## 在何处查找事件
{: #at_events_acc_mgt_ui}

{{site.data.keyword.cloudaccesstrailshort}} 事件在**美国南部**区域**帐户域**中提供。 

要查看这些事件，必须在**美国南部**区域中供应 {{site.data.keyword.cloudaccesstrailshort}} 服务的实例。然后，必须打开 {{site.data.keyword.cloudaccesstrailshort}} UI，并切换到帐户域以查看事件。 

有关更多信息，请参阅[查看帐户事件](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-view_acc_events#view_acc_events_account_events)。








