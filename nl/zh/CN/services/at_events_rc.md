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


# 服务实例事件  
{: #at_events_rc}

作为安全主管、审计员或管理者，您可以使用 {{site.data.keyword.cloudaccesstrailfull}} 服务来跟踪用户和应用程序与 {{site.data.keyword.Bluemix}} 服务的交互方式。
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull_notm}} 服务会记录用户发起的用于在 {{site.data.keyword.cloud_notm}} 中更改服务状态的活动。有关更多信息，请参阅[关于 {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#activity_tracker_ov )。

要开始监视用户的操作，请参阅[{{site.data.keyword.cloudaccesstrailfull_notm}}](/docs/services/cloud-activity-tracker/index.html#getting-started-with-cla)。 

## 用于供应和管理服务实例的事件
{: #at_events_rc_provision}

下表列出调用时生成事件的 API 方法：

<table>
  <caption>用于生成事件的操作</caption>
  <tr>
    <th>操作</th>
	  <th>描述</th>
  </tr>
  <tr>
    <td><i>service_name</i>.instance.create</td>
	  <td>供应服务实例时，将生成事件。</td>
  </tr>
  <tr>
    <td><i>service_name</i>.instance.update</td>
	  <td>重命名服务实例或更改服务套餐时，将生成事件。</td>
  </tr>
  <tr>
    <td><i>service_name</i>.instance.delete</td>
	  <td>删除服务实例时，将生成事件。</td>
  </tr>
</table>


##  用于管理与服务实例相关联的 API 密钥的事件
{: #at_events_rc_keys}

下表列出调用时生成事件的 API 方法：

<table>
  <caption>用于生成事件的操作</caption>
  <tr>
    <th>操作</th>
	  <th>描述</th>
  </tr>
  <tr>
    <td><i>service_name</i>.key.create</td>
	  <td>通过服务实例 UI 的*服务凭证*部分为服务实例创建 API 密钥时，将生成事件。</td>
  </tr>
  <tr>
    <td><i>service_name</i>.key.delete</td>
	  <td>从服务实例 UI 的*服务凭证*部分删除与服务实例相关联的 API 密钥时，将生成事件。</td>
  </tr>
</table>

##  用于将服务实例绑定到应用程序的事件
{: #at_events_rc_bind}

下表列出调用时生成事件的 API 方法：

<table>
  <caption>用于生成事件的操作</caption>
  <tr>
    <th>操作</th>
	  <th>描述</th>
  </tr>
  <tr>
    <td><i>service_name</i>.binding.create</td>
	  <td>将服务实例绑定到应用程序时，将生成事件。</td>
  </tr>
  <tr>
    <td><i>service_name</i>.binding.delete</td>
	  <td>取消服务实例与应用程序的绑定时，将生成事件。</td>
  </tr>
</table>




## 在何处查找事件
{: #at_events_rc_ui}

{{site.data.keyword.cloudaccesstrailshort}} 事件在**美国南部**区域**帐户域**中提供。

要查看这些事件，必须在**美国南部**区域中供应 {{site.data.keyword.cloudaccesstrailshort}} 服务的实例。然后，必须打开 {{site.data.keyword.cloudaccesstrailshort}} UI，并切换到帐户域以查看事件。有关更多信息，请参阅[查看帐户事件](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/viewing_events.html#view_acc_events_account_events)。


