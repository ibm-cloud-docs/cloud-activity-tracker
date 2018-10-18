---

copyright:
  years: 2016, 2018
lastupdated: "2018-09-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# 删除事件
{: #deleting_events}

使用 *ibmcloud at delete* 命令可手动删除 {{site.data.keyword.cloudaccesstrailshort}} 中存储的事件。
{:shortdesc}

完成以下步骤：

## 步骤 1：登录到 {{site.data.keyword.Bluemix_notm}}
{: #prereq}

登录到 {{site.data.keyword.Bluemix_notm}}。完成以下步骤：

1. 运行 [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) 命令以登录到 {{site.data.keyword.Bluemix_notm}}。
2. 运行 [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) 命令，以设置要在其中供应 {{site.data.keyword.cloudaccesstrailshort}} 服务的组织和空间。

**注：**设置要在其中供应 {{site.data.keyword.cloudaccesstrailshort}} 的组织和空间。

## 步骤 2：确定可用的事件
{: #step2}

使用 `ibmcloud at status` 命令可查看空间域中可用的事件的相关信息。

* 要获取空间域中事件的相关信息，请运行 `ibmcloud at status` 命令。
* 要获取帐户域中事件的相关信息，请运行带有 `-a` 选项的 `ibmcloud at status` 命令。

有关更多信息，请参阅[查看事件信息](/docs/services/cloud-activity-tracker/how-to/viewing_event_information.html#viewing_event_status)。
	
  
## 步骤 3：删除事件
{: #step3}
	
要删除事件，请运行 `ibmcloud at delete` 命令。

```
ibmcloud at delete -s YYYY-MM-DD -e YYYY-MM-DD 
```
{: codeblock}
    
其中


* *-s* 用于设置开始日期，格式为全球标准时间 (UTC)：*YYYY-MM-DD*。
* *-e* 用于设置结束日期，格式为全球标准时间 (UTC)：*YYYY-MM-DD*。

例如，要删除 2017 年 6 月 10 日的事件，请运行以下命令：

```
ibmcloud at delete -s 2017-06-10 -e 2017-06-10
```
{: screen}

您会收到有关已删除的事件记录的信息。










