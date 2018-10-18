---

copyright:
  years: 2016, 2018
lastupdated: "2018-07-09"

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

您可以通过 {{site.data.keyword.Bluemix_notm}} 控制台中的 {{site.data.keyword.cloudaccesstrailshort}} UI 或通过 Kibana 来查看事件。
{:shortdesc}
   

## 查看帐户事件
{: #account_events}

您可以通过 {{site.data.keyword.cloudaccesstrailshort}} UI 或 Kibana 查看 {{site.data.keyword.cloudaccesstrailshort}} 帐户域中的事件。

**帐户所有者**具有通过 {{site.data.keyword.cloudaccesstrailshort}} UI 或 Kibana 查看 {{site.data.keyword.cloudaccesstrailshort}} 帐户域中事件的权限。

作为**帐户中的成员**，请考虑以下信息来查看区域中的帐户事件：

* 在供应 {{site.data.keyword.cloudaccesstrailshort}} 的空间中，您必须具有*开发者*角色。有关更多信息，请参阅[授予 CF 角色](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_cf_role)。

* 您必须以该区域中的*查看者*角色具有 {{site.data.keyword.loganalysisshort}} 服务的 IAM 策略。查看者角色是 IAM 角色的最低要求。有关更多信息，请参阅[授予 IAM 权限](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_iam_policy)。

* 您可以通过 Kibana 查看事件。有关如何启动 Kibana 的更多信息，请参阅[通过 Web 浏览器导航至 Kibana](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_kibana.html#launch_Kibana_from_browser)。



## 查看空间事件
{: #space_events}

您可以通过 {{site.data.keyword.cloudaccesstrailshort}} UI 查看 {{site.data.keyword.cloudaccesstrailshort}} 空间域中的事件。如果您具有高端套餐，那么还可以通过 Kibana 来查看事件。

**帐户所有者**具有查看任何 {{site.data.keyword.cloudaccesstrailshort}} 空间域事件的权限。

作为**帐户中的成员**，您必须具有供应 {{site.data.keyword.cloudaccesstrailshort}} 的空间的*开发者*角色。


