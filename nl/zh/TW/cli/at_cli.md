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

# IBM Cloud Activity Tracker CLI
{: #at_cli}

{{site.data.keyword.cloudaccesstraillong}} CLI 是一個 CF 外掛程式，您可以用來管理 {{site.data.keyword.cloudaccesstrailshort}} 事件。
{: shortdesc}

**必要條件**
* 在執行指令之前，請先使用 `cf login` 指令登入 {{site.data.keyword.Bluemix}}，以產生 {{site.data.keyword.Bluemix_short}} 存取記號並鑑別您的階段作業。

若要瞭解如何使用 {{site.data.keyword.cloudaccesstrailshort}} CLI，請參閱[透過 CLI 管理 {{site.data.keyword.cloudaccesstrailshort}} 事件](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#managing_events)。 

{{site.data.keyword.cloudaccesstraillong}} CLI 外掛程式支援 Linux、Mac 及 Windows 平台。

<table>
  <caption>用來管理 {{site.data.keyword.cloudaccesstrailshort}} 的指令</caption>
  <tr>
    <th>指令</th>
    <th>使用時機</th>
  </tr>
  <tr>
    <td>[cf at](#base)</td>
    <td>請使用這個指令來取得 CLI 的相關資訊，例如版本或指令清單。</td>
  </tr>
  <tr>
    <td>[cf at delete](#delete)</td>
    <td>請使用這個指令來刪除 {{site.data.keyword.cloudaccesstrailshort}} 事件。</td>
  </tr>
  <tr>
    <td>[cf at download](#download)</td>
    <td>請使用這個指令來將 {{site.data.keyword.cloudaccesstrailshort}} 日誌下載至本端檔案。</td>
  </tr>
  <tr>
    <td>[cf at help](#help)</td>
    <td>請使用這個指令來取得如何使用 CLI 的說明，以及所有指令的清單。</td>
  </tr>
  <tr>
    <td>[cf at option](#option)</td>
    <td>請使用這個指令來檢視或變更 {{site.data.keyword.Bluemix_notm}} 空間或帳戶中可用的 {{site.data.keyword.cloudaccesstrailshort}} 事件選項（例如保留）。</td>
  </tr>
  <tr>
    <td>[cf at session create](#session_create)</td>
    <td>請使用這個指令來建立新的階段作業。</td>
  </tr>
  <tr>
    <td>[cf at session delete](#session_delete)</td>
    <td>請使用這個指令來刪除階段作業。</td>
  </tr>  
  <tr>
    <td>[cf at session list](#session_list)</td>
    <td>請使用這個指令來列出作用中階段作業及其 ID。</td>
  </tr>  
  <tr>
    <td>[cf at session show](#session_show)</td>
    <td>請使用這個指令來顯示單一階段作業的狀態。</td>
  </tr>   
  <tr>
    <td>[cf at status](#status)</td>
    <td>請使用這個指令來檢視 {{site.data.keyword.cloudaccesstrailshort}} 中儲存之事件的狀態相關資訊。</td>
  </tr>
  <tr>
    <td>[cf at trail](#trail)</td>
    <td>請使用這個指令將事件傳送至 {{site.data.keyword.cloudaccesstrailshort}}。</td>
  </tr>
  </table>


## cf at
{: #base}

提供 CLI 版本及如何使用 CLI 的相關資訊。

```
cf at [parameters]
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
cf at --help
```
{: codeblock}

若要取得 CLI 的版本，請執行下列指令：

```
cf at --version
```
{: codeblock}


## cf at delete
{: #delete}

刪除 {{site.data.keyword.cloudaccesstrailshort}} 事件。

```
cf at delete [parameters] [arguments..]
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
  
</dl>

**範例**

若要刪除 2017 年 6 月 22 日的事件，請執行下列指令：
```
cf at delete -s 2017-06-22 -e 2017-06-22
```
{: codeblock}

您會收到與下列輸出類似的資訊：

`Deleted successfully`
`"6 logs were deleted, freeing 13737 bytes."`


## cf at download
{: #download}

將 {{site.data.keyword.cloudaccesstrailshort}} 事件下載至本端檔案，或將它們串流到 Windows 和 Mac OS X 中的終端機視窗，或串流到 Linux 終端機的 stdout。 

**附註：**若要下載檔案，您必須先建立階段作業。階段作業根據日期範圍來定義要下載的事件。您可以在階段作業的環境定義內下載事件。如需相關資訊，請參閱 [cf at session create](/docs/services/CloudActivityTracker/reference/at_cli.html#session_create)。

```
cf at download [parameters] [arguments...]
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
<dd>設定在執行 `cf at session create` 時，您會取得的階段作業 ID 值。此值指出在下載事件時要使用的階段作業。<br>**附註：**`cf at session create` 指令會提供參數，控制要下載哪些事件。</dd>
</dl>

**附註：**下載完成之後，若要重新下載相同的資料，您必須使用不同的檔案或不同的階段作業。

**範例**

若要將事件下載至稱為 `events.log` 的檔案中，請執行下列指令：

```
cf at download -o events.log 1db6ce16-824d-4d50-bd40-37f1d8fea9b7
```
{: screen}

您會收到與下列輸出類似的資訊： 

```
6.70 KiB / 3.06 KiB [========] 219.03% 8.60 MiB/s 0s
Download completed successfully
```
{: screen}


## cf at help
{: #help}

提供如何使用指令的相關資訊。

```
cf at help [parameters]
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
cf at help status
```
{: codeblock}


## cf at option
{: #option}

顯示或變更可用於 {{site.data.keyword.Bluemix_notm}} 空間之事件的保留期間。設定保留原則時，如果已達到保留天數，則會自動刪除事件。

* 期間以天數為設定的單位。
* 預設值為 **-1**，也就是說，事件會儲存而不刪除。

**附註：**依預設，會儲存所有事件。如果您未設定保留期間，則必須使用 `cf at delete` 指令手動刪除它們。 

```
cf at option [parameters] [arguments...]
```
{: codeblock}

**參數**

<dl>
<dt>--retention value, -r value</dt>
<dd>（選用）設定保留天數。<br> 預設值為 *-1* 天。</dd>

</dl>

**範例**

若要查看您已登入之空間的現行保留期間，請執行下列指令：

```
cf at option
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
cf at option -r 25
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



## cf at session create
{: #session_create}

建立新的階段作業。

**附註：**在一個空間裡，您可以有最多 30 個並行階段作業。階段作業是針對使用者而建立。無法在空間中的使用者之間共用階段作業。

```
cf at session create [parameters] [arguments...]
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
 </dl>

**回覆值**

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
cf at session create -s 2017-07-10 -e 2017-07-10
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



## cf at session delete
{: #session_delete}

刪除由階段作業 ID 指定的階段作業。

```
cf at session delete [arguments...]
```
{: codeblock}


**引數**

<dl>
<dt>階段作業 ID</dt>
<dd>您要刪除之階段作業的 ID。<br>您可以使用 `cf at session list` 指令來取得所有作用中階段作業 ID。</dd>
</dl>

**範例**

若要刪除階段作業 ID 為 *b8c4db8-5841-4993-a449-305815a53a8e* 的階段作業，請執行下列指令：

```
cf at session delete 9b8c4db8-5841-4993-a449-305815a53a8e
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


## cf at session list
{: #session_list}

列出作用中階段作業及其 ID。

```
cf at session list 
```
{: codeblock}

**回覆值**

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
cf at session list
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


## cf at session show
{: #session_show}

顯示單一階段作業的狀態。

```
cf at session show [arguments...]
```
{: codeblock}

**引數**

<dl>
<dt>階段作業 ID</dt>
<dd>您要取得其資訊之作用中階段作業的 ID。</dd>
</dl>

**回覆值**

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
cf at session show 9b8c4db8-5841-4993-a449-305815a53a8e
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


## cf at status
{: #status}

傳回 {{site.data.keyword.cloudaccesstrailshort}} 事件狀態的相關資訊。

```
cf at status [parameters] [arguments...]
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
  <dd>（選用）將範圍設為帳戶層次。<br> **附註：**設定此值以取得帳戶資訊。<br>如果未指定此參數，預設值只會設為現行空間，亦即，您使用指令 `cf login` 登入的空間。
  </dd>
  
</dl>


**附註：未指定開始和結束日期時，**`cf at status` 指令只會報告 {{site.data.keyword.cloudaccesstrailshort}} 中儲存的最後兩週事件。 

**回覆值**   

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
cf at status -s 2017-07-20 -e 2017-07-20
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



## cf at trail
{: #trail}

將序列化事件傳送至 {{site.data.keyword.cloudaccesstrailshort}}。

```
cf at trail [parameters] [arguments...]
```
{: codeblock}

**參數**

<dl>
  <dt>--file FILE, -f FILE</dt>
  <dd>（選用）以 `PATH/filename` 格式指定事件檔案。
  </dd>
  
  <dt>--type FORMAT, -t FORMAT</dt>
  <dd>（選用）指定檔案中所包含之事件的格式。有效值為：*cadf* 和 *kong*。<br> 使用 *CADF* 可傳送符合 CADF 格式的事件。使用 *KONG* 可傳送符合 Kong 格式的事件。<br> **附註：**您只能在一個檔案中傳送相同類型的事件。
  </dd>
 </dl>
 
**範例**

若要傳送序列化的 CADF 事件至 {{site.data.keyword.cloudaccesstrailshort}}，請執行下列指令：

```
cf at trail -t cadf -f events.log
```
{: codeblock}

其中，*events.log* 是包含您要傳送至 {{site.data.keyword.cloudaccesstrailshort}} 之事件的檔案。此檔案包含符合 CADF 格式的事件。

您會收到與下列輸出類似的資訊：

```
+--------------------------------------+---------------------------+
|            ID                        |          Value            |
+--------------------------------------+---------------------------+
| bbb170dc-2b0a-42d4-b560-b416f3308869 | B0UtwP1FhemsZIr4rTJVKA==  |
+--------------------------------------+---------------------------+
| 688f1194-2305-4367-8ece-f468e67c19fb | KLCG9f++usNolgvutRCR1Q==  |
+--------------------------------------+---------------------------+
```
{: screen}
