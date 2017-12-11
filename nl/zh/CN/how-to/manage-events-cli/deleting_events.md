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

# 删除事件
{: #deleting_events}

使用 *delete* 命令可手动删除 {{site.data.keyword.cloudaccesstrailshort}} 中为 {{site.data.keyword.Bluemix}} 空间存储的事件。
{:shortdesc}

## 删除事件
{: #viewing_events}

使用 `cf at status` 命令可查看事件的大小、计数以及事件是否可供在 Kibana 中进行分析。有关更多信息，请参阅 [cf at status](/docs/services/cloud-activity-tracker/cli/at_cli.html#status)。

1. 登录到 {{site.data.keyword.Bluemix_notm}} 区域、组织和空间。 

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

2. 运行 *cf at status* 命令。

    ```
    $ bx cf at status -a -s YYYY-MM-DD -e YYYY-MM-DD 
    ```
    {: codeblock}
    
    其中

    
    * *-a* 用于指定该请求应用于帐户中的所有空间。
    * *-s* 用于设置开始日期，格式为全球标准时间 (UTC)：*YYYY-MM-DD*。
    * *-e* 用于设置结束日期，格式为全球标准时间 (UTC)：*YYYY-MM-DD*。
    	
	使用带有选项 **-s**（用于设置开始日期）和 **-e**（用于设置结束日期）的 `cf at status` 命令。例如：

    * `bx cf at status` 提供最近 2 周的信息。
    * `bx cf at status -s 2017-05-03` 提供从 2017 年 5 月 3 日到当天的信息。
    * `bx cf at status -s 2017-05-03 -e 2017-05-08` 提供从 2017 年 5 月 3 日到 2017 年 5 月 8 日之间的信息。 
 
    使用带有选项 **-a**（用于将域设置为帐户）的 `cf at status` 命令。
	
    例如，要获取有关 2017 年 6 月 10 日的可用事件的信息，请运行以下命令：
    
    ```
    $ bx cf at status -s 2017-06-10 -e 2017-06-10
    +------------+-------+------+------------+
    | Date       | Count | Size | Searchable |
    +------------+-------+------+------------+
    | 2017-07-10 | 1     | 2531 | All        |
    +------------+-------+------+------------+
    ```
    {: screen}
	














