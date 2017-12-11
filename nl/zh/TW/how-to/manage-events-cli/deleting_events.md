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

# 刪除事件
{: #deleting_events}

使用 *cf at delete* 指令來手動刪除 {{site.data.keyword.Bluemix}} 空間中儲存在 {{site.data.keyword.cloudaccesstrailshort}} 中的事件。
{:shortdesc}

## 刪除事件
{: #viewing_events}

使用 `cf at status` 指令來檢視大小、計數及事件是否可用於在 Kibana 中進行分析。如需相關資訊，請參閱 [cf at status](/docs/services/cloud-activity-tracker/cli/at_cli.html#status)。

1. 登入 {{site.data.keyword.Bluemix_notm}} 地區、組織及空間。 

    ```
    bx login -a Endpoint
    ```
    {: codeblock}
	
	其中 *Endpoint* 是登入 {{site.data.keyword.Bluemix_notm}} 用的 URL。每個地區的 URL 都不同。
	
	<table>
	    <caption>要存取 {{site.data.keyword.Bluemix_notm}} 的端點清單</caption>
		<tr>
		  <th>地區</th>
		  <th>URL</th>
		</tr>
		<tr>
		  <td>美國南部</td>
		  <td>api.ng.bluemix.net</td>
		</tr>
	</table>

    遵循指示。 

    例如，執行下列指令以登入美國南部地區：
	
	```
	bx login -a api.ng.bluemix.net
	```
	{: codeblock}
	
	然後，設定組織及空間。執行下列指令：

    ```
    bx target -o OrgName -s SpaceName
    ```
   {: codeblock}

    其中

    * OrgName 是組織的名稱。
    * SpaceName 是空間的名稱。

2. 執行 *cf at status* 指令。

    ```
    $ bx cf at status -a -s YYYY-MM-DD -e YYYY-MM-DD 
    ```
    {: codeblock}
    
    其中
    
    * *-a* 用來指定要求適用於帳戶中的所有空間。
    * *-s* 用來以「世界標準時間 (UTC) 」設定開始日期：*YYYY-MM-DD*。
    * *-e* 用來以「世界標準時間 (UTC) 」設定結束日期：*YYYY-MM-DD*。
    	
	使用 `cf at status` 指令搭配 **-s** 選項以設定開始日，搭配 **-e** 設定結束日期。例如：

    * `bx cf at status` 提供過去 2 週的資訊。
    * `bx cf at status -s 2017-05-03` 提供從 2017 年 5 月 3 日至現行日期的資訊。
    * `bx cf at status -s 2017-05-03 -e 2017-05-08` 提供 2017 年 5 月 3 日到 2017 年 5 月 8 日之間的資訊。 
 
    使用 `cf at status` 指令搭配 **-a** 選項以將範圍設為帳戶。
	
    例如，若要取得在 2017 年 6 月 10 日時可用之事件的相關資訊，請執行下列指令：
    
    ```
    $ bx cf at status -s 2017-06-10 -e 2017-06-10
    +------------+-------+------+------------+
    | Date       | Count | Size | Searchable |
    +------------+-------+------+------------+
    | 2017-07-10 | 1     | 2531 | All        |
    +------------+-------+------+------------+
    ```
    {: screen}
	














