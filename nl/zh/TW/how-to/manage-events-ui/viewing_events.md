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



# 檢視事件
{: #view_acc_events}

您可以透過 {{site.data.keyword.Bluemix_notm}} 主控台中的 {{site.data.keyword.cloudaccesstrailshort}} 使用者介面或透過 Kibana 來檢視事件。
{:shortdesc}
   

## 檢視帳戶事件
{: #account_events}

您可以透過 {{site.data.keyword.cloudaccesstrailshort}} 使用者介面或透過 Kibana，在 {{site.data.keyword.cloudaccesstrailshort}} 帳戶網域中檢視事件。

**帳戶擁有者**有許可權可以透過 {{site.data.keyword.cloudaccesstrailshort}} 使用者介面或透過 Kibana，在 {{site.data.keyword.cloudaccesstrailshort}} 帳戶網域中檢視事件。

身為**帳戶中的成員**，請考量下列資訊以檢視地區中的帳戶事件：

* 在佈建 {{site.data.keyword.cloudaccesstrailshort}} 的空間中，您必須具有*開發人員* 角色。如需相關資訊，請參閱[授與 CF 角色](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_cf_role)。

* 您必須具有 {{site.data.keyword.loganalysisshort}} 服務的 IAM 原則，其含有該地區的*檢視者* 角色。「檢視者」角色是必要的最小 IAM 角色。如需相關資訊，請參閱[授與 IAM 許可權](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_iam_policy)。

* 您可以透過 Kibana 來檢視事件。如需如何啟動 Kibana 的相關資訊，請參閱[從 Web 瀏覽器導覽至 Kibana](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_kibana.html#launch_Kibana_from_browser)。



## 檢視空間事件
{: #space_events}

您可以透過 {{site.data.keyword.cloudaccesstrailshort}} 使用者介面，在 {{site.data.keyword.cloudaccesstrailshort}} 空間網域中檢視事件。如果您有超值方案，也可以透過 Kibana 來查看事件。

**帳戶擁有者**有許可權可以檢視任何 {{site.data.keyword.cloudaccesstrailshort}} 空間網域的事件。

身為**帳戶中的成員**，在佈建 {{site.data.keyword.cloudaccesstrailshort}} 的空間中，您必須具有*開發人員* 角色。


