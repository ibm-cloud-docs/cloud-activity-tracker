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



# 使用 Activity Tracker CLI 管理事件
{: #tutorial2}

使用本教程可了解如何使用 {{site.data.keyword.cloudaccesstrailshort}} CLI 通过命令行来管理事件。了解如何获取有关已存储事件的信息，如何下载 {{site.data.keyword.IBM_notm}} 云中存储的事件或如何删除事件。
{:shortdesc}

完成以下步骤：

1. [供应 {{site.data.keyword.keymanagementservicelong_notm}} 并生成事件](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#tutorial2_step1)
2. [获取有关存储的事件的信息 (ibmcloud at status)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#tutorial2_step2)
2. [通过创建会话指定要下载的日志 (ibmcloud at session create)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#tutorial2_step3)
3. [获取实际日志数据 (ibmcloud at download)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#tutorial2_step4)
4. [下载完成后删除会话 (ibmcloud at session delete)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#tutorial2_step5)
5. [手动删除不需要的日志 (ibmcloud at delete)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#tutorial2_step6)


## 假定
{: #tutorial2_assumptions}

1. 您有 {{site.data.keyword.cloud_notm}} 用户标识，该用户标识具有开发者许可权，可以在供应 {{site.data.keyword.cloudaccesstrailshort}} 服务的 {{site.data.keyword.cloud_notm}} 帐户的空间中工作。 

    有关如何供应 {{site.data.keyword.cloudaccesstrailshort}} 服务的更多信息，请参阅[供应 {{site.data.keyword.cloudaccesstrailshort}} 服务](/docs/services/cloud-activity-tracker/how-to/provision.html#provision)。

2. 您已使用高端套餐供应 {{site.data.keyword.cloudaccesstrailshort}} 服务的实例。

    **注：**{{site.data.keyword.cloudaccesstrailshort}} CLI 不可用于轻量套餐。

3. 已在本地系统中安装 {{site.data.keyword.cloudaccesstrailshort}} CLI。这是能够使用 {{site.data.keyword.cloudaccesstrailshort}} CLI 通过命令行来管理事件所必需的条件。 

    有关安装 {{site.data.keyword.cloudaccesstrailshort}} CLI 的更多信息，请参阅[配置 {{site.data.keyword.cloudaccesstrailshort}} CLI](/docs/services/cloud-activity-tracker/how-to/config_cli.html#config_cli)。

4. 您已通过命令行登录到 {{site.data.keyword.cloud_notm}}。对于本教程，从终端运行以下命令： 

    `ibmcloud login -a api.ng.bluemix.net`，用于登录到美国南部区域。有关更多信息，请参阅 [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login)。
    
    `ibmcloud target -o OrgName -s SpaceName`，用于设置供应 {{site.data.keyword.cloudaccesstrailshort}} 服务的目标组织和空间。有关更多信息，请参阅 [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target)。


## 步骤 1：供应 IBM Key Protect 服务并生成事件 
{: #tutorial2_step1}
	
完成以下步骤以在 {{site.data.keyword.cloud_notm}} 中供应 {{site.data.keyword.keymanagementserviceshort}} 服务并生成事件：

1. 在美国南部区域中供应 {{site.data.keyword.keymanagementserviceshort}} 服务的实例。有关更多信息，请参阅[从 IBM Cloud 控制台供应](/docs/services/key-protect/provision.html#provision)。

2. 针对计划使用密钥的用户定义 {{site.data.keyword.cloud_notm}} 许可权。 

    * 用户需要通过服务角色设置为 *manager* 或 *writer* 的 IAM 策略，才能创建密钥。
	* 用户需要通过服务角色设置为 *manager* 的 IAM 策略，才能删除密钥。
	* 用户需要通过服务角色设置为 *reader* 的 IAM 策略，才能查看密钥。 

3. 使用 {{site.data.keyword.keymanagementserviceshort}} 服务创建安全密钥以生成 {{site.data.keyword.cloudaccesstrailshort}} 事件数据。有关更多信息，请参阅[创建新密钥](/docs/services/key-protect/create-standard-keys.html#create-standard-keys)。

创建密钥会生成 {{site.data.keyword.cloudaccesstrailshort}} 事件。

## 步骤 2：获取有关已存储事件的信息
{: #tutorial2_step2}

{{site.data.keyword.keymanagementserviceshort}} 事件在 {{site.data.keyword.cloudaccesstrailshort}} 帐户域中提供。

在本教程中，{{site.data.keyword.keymanagementserviceshort}} 事件在美国南部帐户域中提供，也就是您供应 {{site.data.keyword.keymanagementserviceshort}} 服务的区域。 

运行以下命令以获取有关在特定日期收集的事件的信息：

```
ibmcloud at status -s startDate -e endDate -a
```
{: codeblock}

其中
 

* `-s` 用于设置开始日期。 
* `startDate` 表示开始日期。格式为 *YYYY-MM-DD*。
* `-e` 用于设置结束日期。
* `endDate` 表示结束日期。格式为 *YYYY-MM-DD*。
* `-a` 用于指示在帐户域中包含事件。

例如：

```
ibmcloud at status -s 2017-07-25 -e 2017-07-25 -a
+------------+-------+-------+------------+
| Date       | Count | Size  | Searchable |
+------------+-------+-------+------------+
| 2017-07-25 | 12    | 34994 | All        |
+------------+-------+-------+------------+
```
{: screen}

此命令将统计 2017 年 6 月 25 日的事件计数。{{site.data.keyword.cloudaccesstrailshort}} 是一个全球服务，因此，天数依据全球标准时间确定。要获取本地时间一整天的信息，可能需要下载多个 UTC 天。




## 步骤 3：指定要下载的事件
{: #tutorial2_step3}

下载事件之前，请创建会话。会话指定将下载哪些事件。


使用以下命令来创建会话：

```
ibmcloud at session create -s startDate -e endDate -a
```
{: codeblock}

其中
 

* `-s` 用于设置开始日期。 
* `startDate` 表示开始日期。格式为 *YYYY-MM-DD*。
* `-e` 用于设置结束日期。
* `endDate` 表示结束日期。格式为 *YYYY-MM-DD*。
* `-a` 用于指示在帐户域中包含事件。

例如：

```
ibmcloud at session create -s 2017-07-25 -e 2017-07-25 -a
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| id           | 21b19aeb-3d32-4c60-b912-517609c62db2      |
| space        | 667fb895-b5f5-46c9-9f0e-cf4587341095      |
| username     | xxx@yyy.com                               |
| create-time  | 2017-07-25T18:33:22.678350874Z            |
| access-time  | 2017-07-25T18:33:22.678350874Z            |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
+--------------+-------------------------------------------+
```
{: screen}

其中
 

* `-s` 用于设置开始日期。
* `-e` 用于设置结束日期。
* `-a` 用于指示在帐户域中包含事件。

会话具有关联的开始日期和结束日期。download 命令将包含位于这两个日期（含这两个日期）之间的事件。

命令输出的重要部分是会话 `Id`。download 命令中会引用此标识。

要获取有关现有会话的信息，请输入 `ibmcloud at session list`。

要了解有关会话和 `ibmcloud at session create` 命令的更多信息，请参阅 [CLI 参考](/docs/services/cloud-activity-tracker/reference/at_cli_cloud.html#session_create)。

使用 `ibmcloud at session help create` 可从命令行获取相关帮助。

## 步骤 4：下载针对为会话定义的作用域所确定的事件
{: #tutorial2_step4}

要下载由会话参数指定的事件，请运行以下命令：

```
ibmcloud at events download -o outputFile sessionID
```
{: codeblock}

* `-o` 参数指定输出文件。
* `outputFile` 是本地文件的名称。
* 最后指定 `sessionID`。可以从 `ibmcloud at session create` 命令的输出中获取会话标识的值。

所下载数据的格式为压缩 JSON。 

例如：

```
$ ibmcloud at events download -o events.log 21b19aeb-3d32-4c60-b912-517609c62db2
 6.70 KiB / 3.06 KiB [================================================================================================================================================================] 219.03% 8.60 MiB/s 0s
Download Successful
```
{: screen} 

随着事件的下载，进度指示器将从 0 移至 100%。

要了解有关 `ibmcloud at download` 命令的更多信息，请参阅 [CLI 参考](/docs/services/cloud-activity-tracker/reference/at_cli_cloud.html#download)。

使用 `ibmcloud at help download` 可从命令行获取相关帮助。

## 步骤 5：删除会话
{: #tutorial2_step5}

下载完成后，请删除相应会话。运行以下命令：

```
ibmcloud at session delete sessionID
```
{: codeblock}

其中
 

* `sessionID` 是要删除的会话的标识。

会话数是有限的。会话不会自动删除。必须手动删除不需要的会话。 

例如： 

```
$ ibmcloud at session delete 21b19aeb-3d32-4c60-b912-517609c62db2
+---------+------------------------+
| name    | value                  |
+---------+------------------------+
| message | Delete session success |
+---------+------------------------+
```
{: screen}

要了解有关 `ibmcloud at session delete` 命令的更多信息，请参阅 [CLI 参考](/docs/services/cloud-activity-tracker/reference/at_cli_cloud.html#session_delete)。

使用 `ibmcloud at session help delete` 可从命令行获取相关帮助。

## 步骤 6：从 Activity Tracker 中自动删除事件
{: #tutorial2_step6}

可以在 {{site.data.keyword.cloudaccesstrailshort}} 中控制自己的事件保留时间。可以手动删除事件，也可以自动删除事件。

要从空间手动删除事件，请运行 `ibmcloud at delete` 命令。例如：

```
$ ibmcloud at delete -s 2017-07-25 -e 2017-07-25
Deleted successfully
"6 logs were deleted,freeing 13737 bytes."
```
{: screen}

要了解有关 `ibmcloud at delete` 命令的更多信息，请参阅 [CLI 参考](/docs/services/cloud-activity-tracker/reference/at_cli_cloud.html#delete)。

使用 `ibmcloud at help delete` 可从命令行获取相关帮助。

**注：**要自动删除事件，可以使用 CLI 命令 `ibmcloud at option` 来设置保留时间策略。有关更多信息，请参阅 [CLI 参考](/docs/services/cloud-activity-tracker/reference/at_cli_cloud.html#option)


