---

copyright:
  years: 2016, 2017

lastupdated: "2017-09-07"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# 使用 Activity Tracker CLI 管理事件
{: #tutorial2}

使用本教程可了解如何使用 {{site.data.keyword.cloudaccesstrailshort}} CLI 通过命令行来管理事件。了解如何获取有关已存储事件的信息，如何下载 {{site.data.keyword.IBM_notm}} 云中存储的事件或如何删除事件。
{:shortdesc}

完成以下步骤：

1. [供应 {{site.data.keyword.IBM_notm}} Key Protect 服务并生成事件](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step1)
2. [获取有关已存储事件的信息 (cf at status)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step2)
2. [通过创建会话指定要下载的日志 (cf at session create)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step3)
3. [获取实际日志数据 (cf at download)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step4)
4. [下载完成后删除会话 (cf at session delete)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step5)
5. [手动删除不需要的日志 (cf at delete)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step6)


## 假定
{: #assumptions}

1. 您有 {{site.data.keyword.Bluemix_notm}} 用户标识，该用户标识具有开发者许可权，可以在供应 {{site.data.keyword.IBM_notm}} Cloud {{site.data.keyword.cloudaccesstrailshort}} 服务的 {{site.data.keyword.Bluemix_notm}} 帐户的空间中工作。 

    有关如何供应 {{site.data.keyword.cloudaccesstrailshort}} 服务的更多信息，请参阅[供应 {{site.data.keyword.cloudaccesstrailshort}} 服务](/docs/services/cloud-activity-tracker/how-to/provision.html#provision)。

2. 已在本地系统中安装 {{site.data.keyword.cloudaccesstrailshort}} CF 插件。这是能够使用 {{site.data.keyword.cloudaccesstrailshort}} CLI 通过命令行来管理事件所必需的条件。 

    有关安装 {{site.data.keyword.cloudaccesstrailshort}} CF 插件的更多信息，请参阅[配置 {{site.data.keyword.cloudaccesstrailshort}} CLI](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#config_at_cli)。

3. 您已通过命令行使用以下命令登录到 {{site.data.keyword.Bluemix_notm}}：

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

    例如，运行以下命令以登录到美国南部区域：
	
	```
	bx cf login -a api.ng.bluemix.net
	```
	{: codeblock}

	**注：**您必须登录到 {{site.data.keyword.Bluemix_notm}} 中供应 {{site.data.keyword.cloudaccesstrailshort}} 服务的区域、组织和空间，才能通过命令行来运行 {{site.data.keyword.cloudaccesstrailshort}} 命令和管理事件。
	
	接下来，设置组织和空间。运行以下命令：

    ```
    bx target -o OrgName -s SpaceName
    ```
    {: codeblock}

    其中


    * OrgName 是组织的名称。
    * SpaceName 是空间的名称。


## 步骤 1：供应 IBM Key Protect 服务并生成事件 
{: #step1}
	
1. 要在 {{site.data.keyword.Bluemix_notm}} 中供应 {{site.data.keyword.keymanagementserviceshort}} 服务的实例，请完成以下步骤：

    1. 登录到您的 {{site.data.keyword.Bluemix_notm}} 帐户。

        可在以下地址找到 {{site.data.keyword.Bluemix_notm}}“仪表板”：[http://bluemix.net](http://bluemix.net)

        使用您的用户标识和密码登录后，{{site.data.keyword.Bluemix_notm}} UI 会打开。

    2. 单击**目录**。这将打开 {{site.data.keyword.Bluemix_notm}} 上可用的服务的列表。

        选择**安全性**类别以过滤显示的服务列表。

    3. 选择 **Key Protect** 磁贴。

    4. 单击**创建**以在您登录到的 {{site.data.keyword.Bluemix_notm}} 空间中供应 {{site.data.keyword.keymanagementserviceshort}} 服务。

2. 要生成 {{site.data.keyword.cloudaccesstrailshort}} 事件，请完成以下步骤：

    1. 在 {{site.data.keyword.Bluemix_notm}}“仪表板”中，选择 {{site.data.keyword.keymanagementserviceshort}} 服务。这将打开 {{site.data.keyword.keymanagementserviceshort}} 仪表板。然后，选择**管理**选项卡。

    2. 单击**添加密钥**。这将打开一个新窗口。

        ![用于添加密钥的 {{site.data.keyword.keymanagementserviceshort}} 窗口](images/KP_f2.gif)

    3. 选择**生成密钥**，然后完成以下步骤：

        * 输入密钥的名称，例如 *MyFirstKey*。

        * 为密钥选择算法。

        * 单击**添加密钥**。 

3. 验证是否已创建事件：

    1. 在 {{site.data.keyword.Bluemix_notm}}“仪表板”中，选择 {{site.data.keyword.cloudaccesstrailshort}} 服务。这将打开该服务仪表板。

    2. 将该视图配置为搜索在供应该服务并添加密钥时已生成的 {{site.data.keyword.keymanagementserviceshort}} 事件。

        * 对于*查看日志*字段，选择**空间日志**。
	    * 对于*搜索字段*字段，选择 **target.name**。
	    * 在*过滤器*字段中，输入 **ibm-key-protect**。
	
	    显示的数据对应于最近 24 小时可用的 {{site.data.keyword.keymanagementserviceshort}} 事件。 

	    ![{{site.data.keyword.cloudaccesstrailshort}}“管理”选项卡](images/KP_f3.gif)

## 步骤 2：获取有关已存储事件的信息
{: #step2}

检查哪些事件可供下载。例如，如果在当天供应并添加了密钥，请运行以下命令来获取有关今天所收集事件的信息：

```
bx cf at status -s 2017-07-25 -e 2017-07-25
+------------+-------+-------+------------+
| Date       | Count | Size  | Searchable |
+------------+-------+-------+------------+
| 2017-07-25 | 12    | 34994 | All        |
+------------+-------+-------+------------+
```
{: screen}

此命令将统计 2017 年 6 月 25 日的事件计数。{{site.data.keyword.cloudaccesstrailshort}} 是一个全球服务，因此，天数依据全球标准时间确定。要获取本地时间一整天的信息，可能需要下载多个 UTC 天。

要查看多天的信息，请使用 `-s` 来设置开始日期，并使用 `-e` 来设置结束日期。 

要了解有关 `cf at status` 命令的更多信息，请参阅 [CLI 参考](/docs/services/cloud-activity-tracker/cli/at_cli.html#status)。

使用 `bx cf at help status` 可从命令行获取相关帮助。

## 步骤 3：指定要下载的事件
{: #step3}

下载事件之前，请创建会话：

* 会话指定将下载哪些事件。
* 如果事件下载中断，会话支持从其停止位置恢复下载。

使用以下命令创建会话：

```
bx cf at session create -s 2017-07-25 -e 2017-07-25
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

会话关联有开始日期和结束日期。download 命令将包含位于这两个日期（含这两个日期）之间的事件。缺省日期范围为仅当天。 

命令输出的重要部分是会话 `Id`。download 命令中会引用此标识。

要获取有关现有会话的信息，请输入 `cf at session list`。

要了解有关会话和 `cf at session create` 命令的更多信息，请参阅 [CLI 参考](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_create)。

使用 `cf at session help create` 可从命令行获取相关帮助。

## 步骤 4：下载针对为会话定义的作用域所确定的事件
{: #step4}

要下载由会话参数指定的事件，请运行以下命令：

```
$ bx cf at events download -o events.log 21b19aeb-3d32-4c60-b912-517609c62db2
 6.70 KiB / 3.06 KiB [================================================================================================================================================================] 219.03% 8.60 MiB/s 0s
Download Successful
```

* `-o` 参数指定输出文件。
* 会话标识在最后指定。可以从 `cf at session create` 命令的输出中获取会话标识的值。
* 随着事件的下载，进度指示器将从 0 移至 100%。

所下载数据的格式为压缩 JSON。 

要了解有关 `cf at download` 命令的更多信息，请参阅 [CLI 参考](/docs/services/cloud-activity-tracker/cli/at_cli.html#download)。

使用 `bx cf at help download` 可从命令行获取相关帮助。

## 步骤 5：删除会话
{: #step5}

下载完成后，请删除相应会话。 

会话数是有限的。会话不会自动删除。必须手动删除不需要的会话。 

```
$ bx cf at session delete 21b19aeb-3d32-4c60-b912-517609c62db2
+---------+------------------------+
| name    | value                  |
+---------+------------------------+
| message | Delete session success |
+---------+------------------------+
```

要了解有关 `cf at session delete` 命令的更多信息，请参阅 [CLI 参考](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_delete)。

使用 `bx cf at session help delete` 可从命令行获取相关帮助。

## 步骤 6：手动从 Activity Tracker 中删除事件
{: #step6}

可以在 {{site.data.keyword.cloudaccesstrailshort}} 中控制自己的事件保留时间。可以手动删除事件，也可以自动删除事件。

要手动删除事件，请运行 `cf at delete` 命令。例如：

```
$ bx cf at delete -s 2017-07-25 -e 2017-07-25
Deleted successfully
"6 logs were deleted,freeing 13737 bytes."
```

要了解有关 `cf at delete` 命令的更多信息，请参阅 [CLI 参考](/docs/services/cloud-activity-tracker/cli/at_cli.html#delete)。

使用 `bx cf at help delete` 可从命令行获取相关帮助。

**注：**要自动删除事件，可以使用 CLI 命令 `cf at option` 来设置保留时间策略。有关更多信息，请参阅 [CLI 参考](/docs/services/cloud-activity-tracker/cli/at_cli.html#option)


