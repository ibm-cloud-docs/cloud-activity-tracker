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


# 下载事件
{: #downloading_events}

您可以将事件下载到本地文件中。您将在会话的上下文中下载事件。会话指定将下载哪些事件。下载完成后，必须删除相应会话。
{:shortdesc}

要将事件下载到本地文件中，请完成以下步骤：

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
  


## 步骤 3：创建会话
{: #step3}

需要会话来定义可供下载的事件数据的作用域，并保持下载的状态。 

使用 `ibmcloud at session create` 命令可创建会话。缺省情况下，会话包含最近两周的数据。（可选）您可以在创建会话时指定开始日期和结束日期，以指定时间范围、特定时刻以及事件的作用域。 

**注：** 

* 如果指定了开始日期和结束日期，通过会话可以访问这两个日期（含这两个日期）之间的事件。 
* 对于每个会话，不能下载超过 2 周的数据。因此，时间范围必须小于 2 周。
* 您可以下载区域中空间域或帐户域的事件。

要创建会话以用于下载特定日期的事件，请运行以下命令：

```
ibmcloud at session create -s 2017-07-25 -e 2017-07-25
```
{: codeblock}

会话将返回以下信息：

* 要下载的日期范围。
* 有关是包含可用于整个帐户的事件，还是仅包含可用于当前空间的事件的信息。缺省情况下，将获取您登录到的空间的事件。
* 下载事件所需的会话标识。
* 创建会话的用户标识。

例如：

```
$ ibmcloud at session create 
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| username     | xxx@yyy.com                               |
| create-time  | 2017-07-25T10:29:28.541092735Z            |
| access-time  | 2017-07-25T10:29:28.541092735Z            |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
| id           | 32c657c5-31c0-4a3c-a139-b380871c737a      |
| space        | 66fe4565-abab-46c9-cdcd-qf4565342345      |
+--------------+-------------------------------------------+
```
{: screen}

**提示：**要查看活动会话的列表，请运行 `ibmcloud at session list` 命令。

例如：

```
ibmcloud at session list
+--------------------------------------+--------------------------------------+---------------------+--------------------------------+--------------------------------+
| Id                                   | Space                                |Username             | Create-time                    | Access-time                    |
+--------------------------------------+--------------------------------------+---------------------+--------------------------------+--------------------------------+
| 32c657c5-31c0-4a3c-a139-b380871c737a | 66fe4565-abab-46c9-cdcd-qf4565342345 |xxx@yyy.com          | 2017-07-25T10:29:28.541092735Z | 2017-07-25T10:29:28.541092735Z |
+--------------------------------------+--------------------------------------+---------------------+--------------------------------+--------------------------------+
```
{: screen} 


## 步骤 4：将事件下载到文件
{: #step4}

要下载由会话参数指定的事件，请运行以下命令：

```
ibmcloud at download -o Events_File_Name Session_ID
```
{: codeblock}

其中


* Events_File_Name 是输出文件的名称。
* Session_ID 是会话的 GUID。您在上一步中获取此值。将此值用于 **Id** 字段。

例如：

```
ibmcloud at download -o Events_File_Name.log 32c657c5-31c0-4a3c-a139-b380871c737a
 29.89 KiB / 12.19 KiB [================================] 245.14% 9.73 MiB/s 0s
Download completed successfully
```
{: screen}

随着事件的下载，进度指示器将从 0 移至 100%。

**注：** 

* 所下载数据的格式为压缩 JSON。例如，在 Linux 系统中下载事件后，解压缩 .gz 文件，将其打开以查看 JSON 格式的数据。 
* 压缩 JSON 适合由 ElasticSearch 或 Logstash 获取。例如，如果未给定 -o，并且您是在 Linux 系统上工作，那么数据将流式传送到 stdout，以便您可以通过管道直接将其传输到自己的 Elastic 堆栈。
* 还可以使用任何可以解析 JSON 的程序来处理这些数据。 

## 步骤 5：删除会话

下载完成后，必须使用 `ibmcloud at session delete` 命令删除会话。 

运行以下命令以删除会话：

```
ibmcloud at session delete Session_ID
```
{: codeblock}

其中，Session_ID 是在先前步骤中创建的会话的 GUID。将此值用于 **Id** 字段。

例如：

```
ibmcloud at session delete 32c657c5-31c0-4a3c-a139-b380871c737a
+---------+------------------------+
| Name    | Value                  |
+---------+------------------------+
| message | Delete session success |
+---------+------------------------+
```
{: screen}




