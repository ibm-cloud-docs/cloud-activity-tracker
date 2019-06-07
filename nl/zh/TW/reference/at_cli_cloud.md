---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, CLI

subcollection: cloud-activity-tracker

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}
{:deprecated: .deprecated}


# IBM Cloud Activity Tracker CLI
{: #at_cli_cloud}

您可以使用 {{site.data.keyword.cloudaccesstraillong}} CLI 來管理 {{site.data.keyword.cloudaccesstrailshort}} 事件。
{: shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} 已淘汰。從 2019 年 5 月 9 日開始，您無法佈建新的 {{site.data.keyword.cloudaccesstrailshort}} 實例。現有的超值方案實例將支援到 2019 年 9 月 30 日為止。若要繼續監視 {{site.data.keyword.cloud_notm}} 帳戶的活動，請佈建 [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) 的實例。
{: deprecated}


**必要條件**
* 在執行指令之前，請先使用 `ibmcloud login` 指令登入 {{site.data.keyword.Bluemix}}，以產生存取記號並鑑別您的階段作業。
* 若要使用 CLI 管理事件，您必須具有付費方案。

{{site.data.keyword.cloudaccesstraillong}} CLI 外掛程式支援 Linux、Mac 及 Windows 平台。

<table>
  <caption>用來管理 {{site.data.keyword.cloudaccesstrailshort}} 的指令</caption>
  <tr>
    <th>指令</th>
    <th>使用時機</th>
  </tr>
  <tr>
    <td>[ibmcloud at](#base)</td>
    <td>請使用這個指令來取得 CLI 的相關資訊，例如版本或指令清單。</td>
  </tr>
  <tr>
    <td>[ibmcloud at delete](#delete)</td>
    <td>請使用這個指令來刪除 {{site.data.keyword.cloudaccesstrailshort}} 事件。</td>
  </tr>
  <tr>
    <td>[ibmcloud at download](#download)</td>
    <td>請使用這個指令來將 {{site.data.keyword.cloudaccesstrailshort}} 日誌下載至本端檔案。</td>
  </tr>
  <tr>
    <td>[ibmcloud at help](#help)</td>
    <td>請使用這個指令來取得如何使用 CLI 的說明，以及所有指令的清單。</td>
  </tr>
  <tr>
    <td>[ibmcloud at option](#option)</td>
    <td>請使用這個指令來檢視或變更空間或帳戶中可用的 {{site.data.keyword.cloudaccesstrailshort}} 事件選項（例如保留）。</td>
  </tr>
  <tr>
    <td>[ibmcloud at session create](#session_create)</td>
    <td>請使用這個指令來建立新的階段作業。</td>
  </tr>
  <tr>
    <td>[ibmcloud at session delete](#session_delete)</td>
    <td>請使用這個指令來刪除階段作業。</td>
  </tr>  
  <tr>
    <td>[ibmcloud at session list](#session_list)</td>
    <td>請使用這個指令來列出作用中階段作業及其 ID。</td>
  </tr>  
  <tr>
    <td>[ibmcloud at session show](#session_show)</td>
    <td>請使用這個指令來顯示單一階段作業的狀態。</td>
  </tr>   
  <tr>
    <td>[ibmcloud at status](#status)</td>
    <td>請使用這個指令來檢視 {{site.data.keyword.cloudaccesstrailshort}} 中儲存之事件的狀態相關資訊。</td>
  </tr>
  </table>


## ibmcloud at
{: #base}

提供 CLI 版本及如何使用 CLI 的相關資訊。

```
ibmcloud at [parameters]
```
{: codeblock}

**參數**

<dl>
<dt>--help, -h</dt>
<dd>設定此參數以顯示指令清單，或取得一個指令的說明。</dd>

<dt>--version, -v</dt>
<dd>設定此參數以列印 CLI 的版本。</dd>
</dl>

**範例**

若要取得指令清單，請執行下列指令：

```
ibmcloud at --help
```
{: codeblock}

若要取得 CLI 的版本，請執行下列指令：

```
ibmcloud at --version
```
{: codeblock}


## ibmcloud at delete
{: #delete}

刪除 {{site.data.keyword.cloudaccesstrailshort}} 事件。

```
ibmcloud at delete [parameters] [arguments..]
```
{: codeblock}

**參數**

<dl>
  <dt>--start value, -s value</dt>
  <dd>（選用）以「世界標準時間 (UTC) 」設定開始日期：*YYYY-MM-DD*，例如 `2017-01-02`。<br>預設值設為 2 週前。
  </dd>
  
  <dt>--end value, -e value</dt>
  <dd>（選用）以「世界標準時間 (UTC) 」設定結束日期：*YYYY-MM-DD*。<br>日期的 UTC 格式是 **YYYY-MM-DD**，例如 `2017-01-02`。<br>預設值設為現行日期。
  </dd>
  
  <dt>--search-time value, -T value</dt>
  <dd>（選用）您可以設定此參數，以刪除在特定日期儲存數小時的事件。欄位的格式為：0-23
  </dd>

</dl>


**範例**

若要刪除 2017 年 6 月 22 日的事件，請執行下列指令：
```
ibmcloud at delete -s 2017-06-22 -e 2017-06-22
```
{: codeblock}

您會收到與下列輸出類似的資訊：

`Deleted successfully`
`"6 logs were deleted, freeing 13737 bytes."`


## ibmcloud at download
{: #download}

將 {{site.data.keyword.cloudaccesstrailshort}} 事件下載至本端檔案，或將它們串流到 Windows 和 Mac OS X 中的終端機視窗，或串流到 Linux 終端機的 stdout。 

**附註：**若要下載檔案，您必須先建立階段作業。階段作業根據日期範圍來定義要下載的事件。您會在階段作業的環境定義內下載事件。 

```
ibmcloud at download [parameters] [arguments...]
```
{: codeblock}

**參數**

<dl>
<dt>--output value, -o value</dt>
<dd>（選用）設定下載事件之本端輸出檔的路徑和檔名。<br>預設值為連字號 (-)。<br>將此參數設為預設值，即會將日誌輸出至標準輸出。</dd>
</dl>

**引數**

<dl>
<dt>階段作業 ID</dt>
<dd>設定在執行 `ibmcloud at session create` 指令時，您會取得的階段作業 ID 值。此值指出在下載事件時要使用的階段作業。<br>**附註：**`ibmcloud at session create` 指令會提供參數，控制要下載哪些事件。</dd>
</dl>

**附註：**下載完成之後，若要重新下載相同的資料，您必須使用不同的檔案或不同的階段作業。

**範例**

若要將事件下載至稱為 `events.log` 的檔案中，請執行下列指令：

```
ibmcloud at download -o events.log 1db6ce16-824d-4d50-bd40-37f1d8fea9b7
```
{: screen}

您會收到與下列輸出類似的資訊： 

```
6.70 KiB / 3.06 KiB [========] 219.03% 8.60 MiB/s 0s
Download completed successfully
```
{: screen}


## ibmcloud at help
{: #help}

提供如何使用指令的相關資訊。

```
ibmcloud at help [parameters]
```
{: codeblock}

**參數**

<dl>
<dt>指令</dt>
<dd>設定您要取得其說明的指令名稱。
</dd>
</dl>


**範例**

若要取得如何執行指令以檢視 {{site.data.keyword.cloudaccesstrailshort}} 狀態的說明，請執行下列指令：

```
ibmcloud at help status
```
{: codeblock}


## ibmcloud at option
{: #option}

顯示或變更可用於空間之事件的保留期間。設定保留原則時，如果已達到保留天數，則會自動刪除事件。

* 期間以天數為設定的單位。
* 預設值為 **-1**，也就是說，事件會儲存而不刪除。

**附註：**依預設，會儲存所有事件。如果您未設定保留期間，則必須使用 `ibmcloud at delete` 指令手動刪除它們。 

```
ibmcloud at option [parameters] [arguments...]
```
{: codeblock}

**參數**

<dl>
<dt>--retention value, -r value</dt>
<dd>（選用）設定保留天數。<br> 預設值為 *-1* 天。</dd>

<dt>--at-account-level, -a </dt>
<dd>（選用）設定此參數，以列出每一個空間網域及帳戶網域中所儲存之事件的保留期間相關資訊。

</dl>

**範例**

若要查看您已登入之空間的現行保留期間，請執行下列指令：

```
ibmcloud at option
```
{: codeblock}

其輸出類似如下：

```
+--------------------------------------+-----------+
|               SPACEID                | RETENTION |
+--------------------------------------+-----------+
| 2af890ce-fb4f-4e41-a975-901a56ed1f11 |        30 |
+--------------------------------------+-----------+
```
{: screen}


若要將您已登入之空間的現行保留期間變更為 25 天，請執行下列指令：

```
ibmcloud at option -r 25
```
{: codeblock}

其輸出類似如下：

```
+--------------------------------------+-----------+
|               SPACEID                | RETENTION |
+--------------------------------------+-----------+
| 2af890ce-fb4f-4e41-a975-901a56ed1f11 |        25 |
+--------------------------------------+-----------+
```
{: screen}



## ibmcloud at session create
{: #session_create}

建立新的階段作業。

**附註：**在一個空間裡，您可以有最多 30 個並行階段作業。階段作業是針對使用者而建立。無法在空間中的使用者之間共用階段作業。

```
ibmcloud at session create [parameters] [arguments...]
```
{: codeblock}

**參數**

<dl>
  <dt>--at-account-level, -a </dt>
  <dd>（選用）將範圍設為帳戶層次。</br>設定此值以取得帳戶資訊。<br>如果未指定此參數，預設值只會設為現行空間，亦即，您使用 `ibmcloud cf login` 指令登入的空間。
  </dd>

  <dt>--start value, -s value</dt>
  <dd>（選用）以「世界標準時間 (UTC) 」設定開始日期：*YYYY-MM-DD*，例如 `2017-01-02`。<br>預設值設為 2 週前。
  </dd>
  
  <dt>--end value, -e value</dt>
  <dd>（選用）以「世界標準時間 (UTC) 」設定結束日期：*YYYY-MM-DD*，例如 `2017-01-02`。<br>預設值設為現行日期。
  </dd>

  <dt>--search-time value, -T value</dt>
  <dd>（選用）您可以設定此參數，以刪除在特定日期儲存數小時的事件。欄位的格式為：0-23
  </dd>


 </dl>

**傳回的值**

<dl>
<dt>Access-Time</dt>
<dd>指出前次使用階段作業的時間戳記。</dd>

<dt>Create-Time</dt>
<dd>對應於建立階段作業之日期和時間的時間戳記。</dd>

<dt>Date-Range</dt>
<dd>指出用來過濾事件的天數。識別為在此日期範圍內的事件，可以透過階段作業進行管理。</dd>

<dt>ID</dt>
<dd>階段作業 ID。</dd>

<dt>Space</dt>
<dd>階段作業作用中的空間 ID。</dd>

<dt>Type-Account</dt>
<dd>這個值設為 **ActivityTracker**。</dd>

<dt>Username</dt>
<dd>建立階段作業之使用者的 {{site.data.keyword.IBM_notm}} ID。</dd>
</dl>


**範例**

若要建立 2017 年 7 月 10 日的階段作業，請執行下列指令：

```
ibmcloud at session create -s 2017-07-10 -e 2017-07-10
```
{: screen}

其輸出類似如下：

```
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| id           | 9b8c4db8-5841-4993-a449-305815a53a8e      |
| space        | xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx      |
| username     | xxx@yyy.com                               |
| create-time  | 2017-07-25T11:54:00.20042645Z             |
| access-time  | 2017-07-25T11:54:00.20042645Z             |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
+--------------+-------------------------------------------+
```
{: screen}



## ibmcloud at session delete
{: #session_delete}

刪除由階段作業 ID 指定的階段作業。

```
ibmcloud at session delete [arguments...]
```
{: codeblock}


**引數**

<dl>
<dt>階段作業 ID</dt>
<dd>您要刪除之階段作業的 ID。<br>您可以使用 `ibmcloud at session list` 指令來取得所有作用中階段作業 ID。</dd>
</dl>

**範例**

若要刪除階段作業 ID 為 *b8c4db8-5841-4993-a449-305815a53a8e* 的階段作業，請執行下列指令：

```
ibmcloud at session delete 9b8c4db8-5841-4993-a449-305815a53a8e
```
{: screen}

其輸出類似如下：

```
+---------------+--------------------------+
|    NAME       |     VALUE                |
+---------------+--------------------------+
|  message      | Delete session success   |
+---------------+--------------------------+
```
{: screen}


## ibmcloud at session list
{: #session_list}

列出作用中階段作業及其 ID。

```
ibmcloud at session list 
```
{: codeblock}

**傳回的值**

<dl>
<dt>ID</dt>
<dd>階段作業 ID。</dd>

<dt>SPACE</dt>
<dd>階段作業作用中的空間 ID。</dd>

<dt>USERNAME</dt>
<dd>建立階段作業之使用者的 {{site.data.keyword.IBM_notm}} ID。</dd>

<dt>CREATE-TIME</dt>
<dd>對應於建立階段作業之日期和時間的時間戳記。</dd>

<dt>ACCESS-TIME</dt>
<dd>指出前次使用階段作業的時間戳記。</dd>
</dl>
 
**範例**

若要列出階段作業，請執行下列指令：

```
ibmcloud at session list
```
{: screen}

其輸出類似如下：

```
+--------------------------------------+--------------------------------------+-----------------------------------+--------------------------------+--------------------------------+
| ID                                   | SPACE                                | USERNAME                          | CREATE-TIME                    | ACCESS-TIME                    |
+--------------------------------------+--------------------------------------+-----------------------------------+--------------------------------+--------------------------------+
| fa3f1970-21f3-4e32-b480-1ffb41badc16 | 12345678-fb4f-acdf-a975-11335678r3fg | xxx@yyy.com                       | 2017-07-10T09:04:07.916788069Z | 2017-07-10T09:04:07.916788069Z |
| 9b8c4db8-5841-4993-a449-305815a53a8e | 12345678-fb4f-acdf-a975-11335678r3fg | xxx@yyy.com                       | 2017-07-11T09:19:14.666532796Z | 2017-07-12T09:19:14.666532796Z |
+--------------------------------------+--------------------------------------+-----------------------------------+--------------------------------+--------------------------------+
```
{: screen}


## ibmcloud at session show
{: #session_show}

顯示單一階段作業的狀態。

```
ibmcloud at session show [arguments...]
```
{: codeblock}

**引數**

<dl>
<dt>階段作業 ID</dt>
<dd>您要取得其資訊之作用中階段作業的 ID。</dd>
</dl>

**傳回的值**

<dl>
<dt>Access-Time</dt>
<dd>指出前次使用階段作業的時間戳記。</dd>

<dt>Create-Time</dt>
<dd>對應於建立階段作業之日期和時間的時間戳記。</dd>

<dt>Date-Range</dt>
<dd>指出用來過濾事件的天數。識別為在此日期範圍內的事件，可以透過階段作業進行管理。</dd>

<dt>id</dt>
<dd>階段作業 ID。</dd>

<dt>Space</dt>
<dd>階段作業作用中的空間 ID。</dd>

<dt>Type-Account</dt>
<dd>這個值設為 **ActivityTracker**。</dd>

<dt>Username</dt>
<dd>建立階段作業之使用者的 {{site.data.keyword.IBM_notm}} ID。</dd>
</dl>

**範例**

若要顯示階段作業 ID 為 *b8c4db8-5841-4993-a449-305815a53a8e* 之階段作業的詳細資料，請執行下列指令：

```
ibmcloud at session show 9b8c4db8-5841-4993-a449-305815a53a8e
```
{: screen}

其輸出類似如下：

```
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| create-time  | 2017-07-25T11:54:00.20042645Z             |
| access-time  | 2017-07-25T11:54:00.20042645Z             |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
| id           | 9b8c4db8-5841-4993-a449-305815a53a8e      |
| space        | xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx      |
| username     | xxx@yyy.com                               |
+--------------+-------------------------------------------+
```
{: screen}


## ibmcloud at status
{: #status}

傳回 {{site.data.keyword.cloudaccesstrailshort}} 事件狀態的相關資訊。

```
ibmcloud at status [parameters] [arguments...]
```
{: codeblock}

**參數**

<dl>
  <dt>--start value, -s value</dt>
  <dd>（選用）以「世界標準時間 (UTC) 」設定開始日期：*YYYY-MM-DD*，例如 `2017-01-02`。<br>預設值設為 2 週前。
  </dd>
  
  <dt>--end value, -e value</dt>
  <dd>（選用）以「世界標準時間 (UTC) 」設定結束日期：*YYYY-MM-DD*，例如 `2017-01-02`。<br>預設值設為現行日期。
  </dd>
  
  <dt>--at-account-level, -a </dt>
  <dd>（選用）將範圍設為帳戶層次。<br> **附註：**設定此值以取得帳戶資訊。<br>如果未指定此參數，預設值只會設為現行空間，亦即，您使用 `ibmcloud cf login` 指令登入的空間。
  </dd>
  
</dl>


**附註：未指定開始和結束日期時，**`ibmcloud at status` 指令只會報告 {{site.data.keyword.cloudaccesstrailshort}} 中儲存的最後兩週事件。 

**傳回的值**   

<dl>
  <dt>DATE</dt>
  <dd>「世界標準時間 (UTC) 」的日期：*YYYY-MM-DD*，例如 `2017-01-02`。
  </dd>
  
  <dt>COUNT</dt>
  <dd>事件總數。</dd>
  
  <dt>SIZE</dt>
  <dd>事件的大小總計 (MB)。</dd>

  <dt>TYPES</dt>
  <dd>這個值設為 **ActivityTracker**。</dd>
  
  <dt>SEARCHABLE</dt>
  <dd>此欄位指出是否可以在 Kibana 中搜尋事件。<br>當 **SEARCHABLE** 欄位的值設為 *None* 時，可以下載事件，但您無法在 Kibana 中分析這些事件。</dd>
  
</dl>

**範例**

若要顯示 2017 年 7 月 20 日的事件詳細資料，請執行下列指令：

```
ibmcloud at status -s 2017-07-20 -e 2017-07-20
```
{: codeblock}


您會收到與下列輸出類似的資訊：

```
+------------+-----------+-------+------------------+--------------+
|   Date     |  Count    | Size  | Types            |  Searchable  | 
+------------+-----------+-------+------------------+--------------+
| 2017-07-20 |    1      | 2531  | ActivityTracker  | All          | 
+------------+-----------+-------+------------------+--------------+
```
{: screen}


