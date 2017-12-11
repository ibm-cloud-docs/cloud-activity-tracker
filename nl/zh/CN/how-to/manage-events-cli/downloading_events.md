---

copyright:
  years: 2016, 2017
lastupdated: "2017-09-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 下载事件
{: #downloading_events}

可以将事件下载到本地文件或通过管道将数据传输到其他程序。您将在会话的上下文中下载事件。会话指定将下载哪些事件。如果事件下载中断，会话支持从其停止位置恢复下载。下载完成后，必须删除相应会话。
{:shortdesc}

要将 {{site.data.keyword.Bluemix_notm}} 空间中可用的事件下载到本地文件，请完成以下步骤：

## 步骤 1：登录到 Bluemix
{: #prereq}

开始之前，请登录到供应了 {{site.data.keyword.cloudaccesstrailshort}} 服务的 {{site.data.keyword.Bluemix_notm}} 区域、组织和空间。 

```
bx login -a Endpoint
```
{: codeblock}
	
其中，*Endpoint* 是用于登录到 {{site.data.keyword.Bluemix_notm}} 的 URL。此 URL 对于每个区域各不相同。
	
<table>
    <caption>用于访问 {{site.data.keyword.Bluemix_notm}} 的端点的列表</caption>
	<tr>
	  <th>区域</th>
	  <th>URL</th>
	</tr>
	<tr>
	  <td>美国南部</td>
	  <td>api.ng.bluemix.net</td>
	</tr>
</table>

按照指示信息进行操作。 

例如，运行以下命令以登录到美国南部区域：
	
```
bx login -a api.ng.bluemix.net
```
{: codeblock}

接下来，设置组织和空间。运行以下命令：

```
bx target -o OrgName -s SpaceName
```
{: codeblock}

其中


* OrgName 是组织的名称。
* SpaceName 是空间的名称。

## 步骤 2：确定可用的事件
{: #step2}

1. 使用 `cf at status` 命令可查看哪些事件可用。

    例如，要查看最近 2 周的可用事件，请运行以下命令：

    ```
    $ bx cf at status
    ```
    {: codeblock}
    
    例如，运行此命令的输出为：
    
    ```
    +------------+--------+-------+--------------------+------------+
    |    DATE    |  COUNT | SIZE  |       TYPES        | SEARCHABLE |
    +------------+--------+-------+--------------------+------------+
    | 2017-07-24 |    16  | 3020  | ActivityTracker    |   None     |
    +------------+--------+-------+--------------------+------------+
    | 2017-07-25 |   1224 | 76115 | ActivityTracker    |    All     |
    +------------+--------+-------+--------------------+------------+
    ```
    {: screen}

    **注：**{{site.data.keyword.cloudaccesstrailshort}} 服务是使用全球标准时间 (UTC) 的全局服务。天定义为 UTC 天。要获取本地时间特定一天的事件，可能需要下载多个 UTC 天。
	
	有关更多信息，请参阅 [cf at status](/docs/services/cloud-activity-tracker/cli/at_cli.html#status)。


## 步骤 3：创建会话
{: #step3}

需要会话来定义可供下载的事件数据的作用域，并保持下载的状态。 

使用命令 [cf at session create](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_create) 来创建会话。（可选）创建会话时，可以指定开始日期和结束日期。 

**注：**指定开始日期和结束日期时，会话将提供对这两个日期（含这两个日期）之间的事件的访问权。 

要创建会话以用于下载当天的事件，请运行以下命令：

```
bx cf at session create 
```
{: codeblock}

会话将返回以下信息：

* 要下载的日期范围。缺省值是当前 UTC 日期。
* 有关是包含可用于整个帐户的事件，还是仅包含可用于当前空间的事件的信息。缺省情况下，将获取您登录到的空间的事件。
* 下载事件所需的会话标识。
* 创建会话的用户标识。

例如：

```
$ bx cf at session create 
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

**提示：**要查看活动会话的列表，请运行命令 [cf at session list](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_list)。

例如：

```
bx cf at session list
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
bx cf at download -o Events_File_Name Session_ID
```
{: codeblock}

其中


* Events_File_Name 是输出文件的名称。
* Session_ID 是会话的 GUID。您在上一步中获取此值。将此值用于 **Id** 字段。

例如：

```
bx cf at download -o Events_File_Name.log 32c657c5-31c0-4a3c-a139-b380871c737a
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

下载完成后，必须使用 [cf at session delete](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_delete) 命令删除相应会话。 

运行以下命令以删除会话：

```
bx cf at session delete Session_ID
```
{: codeblock}

其中，Session_ID 是在先前步骤中创建的会话的 GUID。将此值用于 **Id** 字段。

例如：

```
bx cf at session delete 32c657c5-31c0-4a3c-a139-b380871c737a
+---------+------------------------+
| Name    | Value                  |
+---------+------------------------+
| message | Delete session success |
+---------+------------------------+
```
{: screen}




