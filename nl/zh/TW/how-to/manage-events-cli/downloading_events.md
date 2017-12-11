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

# 下載事件
{: #downloading_events}

您可以將事件下載至本端檔案或將資料以管道傳送至另一個程式。您會在階段作業的環境定義內下載事件。階段作業指定將下載哪些事件。如果事件下載遭到岔斷，則階段作業讓您能從它岔斷之處繼續下載。下載完成之後，您必須刪除階段作業。
{:shortdesc}

請完成下列步驟，將 {{site.data.keyword.Bluemix_notm}} 空間中的可用事件下載至本端檔案：

## 步驟 1：登入 Bluemix
{: #prereq}

開始之前，請登入 {{site.data.keyword.cloudaccesstrailshort}} 服務佈建所在的 {{site.data.keyword.Bluemix_notm}} 地區、組織及空間。 

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

## 步驟 2：識別可用的事件
{: #step2}

1. 使用 `cf at status` 指令來查看可用的事件。

    例如，若要查看過去 2 週可用的事件，請執行下列指令：

    ```
    $ bx cf at status
    ```
    {: codeblock}
    
    例如，執行這個指令的輸出為：
    
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

    **附註：**{{site.data.keyword.cloudaccesstrailshort}} 服務是使用「世界標準時間 (UTC)」的廣域服務。「日」的定義為 UTC 日。若要取得當地時間之特定日的事件，您可能需要下載多個 UTC 日。
	
	如需相關資訊，請參閱 [cf at status](/docs/services/cloud-activity-tracker/cli/at_cli.html#status)。


## 步驟 3：建立階段作業
{: #step3}

需要階段作業以定義可供下載的事件資料範圍，以及保留下載的狀態。 

請使用 [cf at session create](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_create) 指令來建立階段作業。在建立階段作業時，您可以選擇性地指定開始日期和結束日期。 

**附註：**當您指定開始日期和結束日期時，階段作業可讓您存取這些內含日期之間的事件。 

若要建立階段作業來下載現行日期的事件，請執行下列指令：

```
bx cf at session create 
```
{: codeblock}

階段作業會傳回下列資訊：

* 要下載的日期範圍。預設值為現行 UTC 日期。
* 指出要包含可用於整個帳戶的事件還是僅包含現行空間事件的資訊。依預設，您會收到您已登入之空間的事件。
* 下載事件所需的階段作業 ID。
* 建立階段作業的使用者 ID。

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

**提示：**若要查看作用中階段作業的清單，請執行 [cf at session list](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_list) 指令。

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


## 步驟 4：將事件下載至檔案
{: #step4}

若要下載由階段作業參數指定的事件，請執行下列指令：

```
bx cf at download -o Events_File_Name Session_ID
```
{: codeblock}

其中

* Events_File_Name 是輸出檔的名稱。
* Session_ID 是階段作業的 GUID。您在前一個中已得到這個值。請將此值用於 **Id** 欄位。

例如：

```
bx cf at download -o Events_File_Name.log 32c657c5-31c0-4a3c-a139-b380871c737a
 29.89 KiB / 12.19 KiB [================================] 245.14% 9.73 MiB/s 0s
Download completed successfully
```
{: screen}

進度指示器會在事件下載時從 0 移動到 100%。

**附註：** 

* 所下載資料的格式為壓縮 JSON。例如，當您在 Linux 系統下載事件，請解壓縮 .gz 檔並開啟它，以查看 JSON 格式的資料。 
* 壓縮的 JSON 適用於 ElasticSearch 或 Logstash 的汲取。例如，如果未提供 -o ，而您是在 Linux 系統上工作，則資料將串流至 stdout，以便您可以將其直接以管道傳送到自己的 Elastic 堆疊。
* 您也可以使用可以剖析 JSON 的任何程式來處理資料。 

## 步驟 4：刪除階段作業

下載完成之後，您必須使用 [cf at session delete](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_delete) 指令來刪除階段作業。 

請執行下列指令以刪除階段作業：

```
bx cf at session delete Session_ID
```
{: codeblock}

其中 Session_ID 是前一個步驟中所建立之階段作業的 GUID。請將此值用於 **Id** 欄位。

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




