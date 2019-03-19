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



# 查看事件
{: #view_acc_events}

您可以通过 {{site.data.keyword.cloud_notm}} 控制台中的 {{site.data.keyword.cloudaccesstrailshort}} UI 或通过 Kibana 来查看事件。
{:shortdesc}
   

## 查看帐户事件
{: #view_acc_events_account_events}

您可以通过 {{site.data.keyword.cloudaccesstrailshort}} UI 或 Kibana 查看 {{site.data.keyword.cloudaccesstrailshort}} 帐户域中的事件。

**帐户所有者**具有通过 {{site.data.keyword.cloudaccesstrailshort}} UI 或 Kibana 查看 {{site.data.keyword.cloudaccesstrailshort}} 帐户域中事件的权限。

作为**帐户中的成员**，请考虑以下信息来查看区域中的帐户事件：

* 在供应 {{site.data.keyword.cloudaccesstrailshort}} 的空间中，您必须具有 *developer* 角色。有关更多信息，请参阅[授予 CF 角色](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_cf_role)。

* 针对具有该区域中 *viewer* 角色的 {{site.data.keyword.loganalysisshort}} 服务，您必须具有 IAM 策略。viewer 角色是必需的最低 IAM 角色。有关更多信息，请参阅[授予 IAM 许可权](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_iam_policy)。

* 您可以通过 Kibana 查看事件。有关如何启动 Kibana 的更多信息，请参阅[通过 Web 浏览器导航至 Kibana](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_kibana.html#launch_Kibana_from_browser)。



## 查看空间事件
{: #view_acc_events_space_events}

您可以通过 {{site.data.keyword.cloudaccesstrailshort}} UI 查看 {{site.data.keyword.cloudaccesstrailshort}} 空间域中的事件。如果您具有高端套餐，那么还可以通过 Kibana 来查看事件。

**帐户所有者**具有查看任何 {{site.data.keyword.cloudaccesstrailshort}} 空间域事件的权限。

作为**帐户中的成员**，您必须具有供应 {{site.data.keyword.cloudaccesstrailshort}} 的空间中的 *developer* 角色。


