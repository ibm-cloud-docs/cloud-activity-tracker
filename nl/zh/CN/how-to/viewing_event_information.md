---

copyright:
  years: 2016, 2019
lastupdated: "2019-02-18"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# 查看事件信息
{: #viewing_event_status}

使用 `ibmcloud at status` 命令可获取有关在 {{site.data.keyword.cloudaccesstrailshort}} 中为 {{site.data.keyword.Bluemix}} 空间收集和存储的事件的信息。
{:shortdesc}

您可以获取有关 teh 事件日志大小、记录数以及事件是否可供在 Kibana 中进行分析的信息。 

完成以下步骤以查看有关事件日志的信息：

## 步骤 1：登录到 {{site.data.keyword.cloud_notm}}
{: #viewing_event_status_step1}

登录到 {{site.data.keyword.cloud_notm}}。完成以下步骤：

1. 运行 [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) 命令以登录到 {{site.data.keyword.cloud_notm}}。
2. 运行 [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) 命令，以设置要在其中供应 {{site.data.keyword.cloudaccesstrailshort}} 服务的组织和空间。

**注：**设置在其中供应 {{site.data.keyword.cloudaccesstrailshort}} 的组织和空间。

## 步骤 2：确定可用的事件
{: #viewing_event_status_step2}

使用 `ibmcloud at status` 命令，以查看有关可供在空间域中使用的事件的信息。

* 要获取有关空间域中事件的信息，请运行命令 `ibmcloud at status`。
* 要获取有关帐户域中事件的信息，请运行命令 `ibmcloud at status`（带选项 `-a`）。

```
$ ibmcloud at status -a -s YYYY-MM-DD -e YYYY-MM-DD 
```
{: codeblock}
    
其中

    
* *-a* 用于指定该请求适用于帐户域。
* *-s* 用于设置开始日期，格式为全球标准时间 (UTC)：*YYYY-MM-DD*。
* *-e* 用于设置结束日期，格式为全球标准时间 (UTC)：*YYYY-MM-DD*。

例如，要查看空间域中最近 2 周的可用事件，请运行以下命令：

```
$ ibmcloud at status
```
{: codeblock}
    
例如，运行此命令的输出为：
    
```
+------------+--------+------------+
|    DATE    |  COUNT | SEARCHABLE |
+------------+--------+------------+
| 2017-07-24 |    16  |    None    |
+------------+--------+------------+
| 2017-07-25 |   1224 |    All     |
+------------+--------+------------+
```
{: screen}

**注：**{{site.data.keyword.cloudaccesstrailshort}} 服务是使用全球标准时间 (UTC) 的全局服务。天定义为 UTC 天。要获取本地时间特定一天的事件，可能需要下载多个 UTC 天。
	














