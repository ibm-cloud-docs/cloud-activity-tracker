---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, download events

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
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}

# 下載事件
{: #downloading_events}

您可以將事件下載至本端檔案。您會在階段作業的環境定義內下載事件。階段作業指定將下載哪些事件。下載完成之後，您必須刪除階段作業。
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} 已淘汰。從 2019 年 5 月 9 日開始，您無法佈建新的 {{site.data.keyword.cloudaccesstrailshort}} 實例。現有的超值方案實例將支援到 2019 年 9 月 30 日為止。若要繼續監視 {{site.data.keyword.cloud_notm}} 帳戶的活動，請佈建 [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) 的實例。
{: deprecated}


請完成下列步驟，將事件下載至本端檔案：

## 步驟 1：登入 {{site.data.keyword.cloud_notm}}
{: #prereq}

登入 {{site.data.keyword.cloud_notm}}。請完成下列步驟：

1. 執行 [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) 指令以登入 {{site.data.keyword.cloud_notm}}。
2. 執行 [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) 指令，以設定您要在其中佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務的組織及空間。

**附註：**設定在其中佈建 {{site.data.keyword.cloudaccesstrailshort}} 的組織及空間。

## 步驟 2：識別可用的事件
{: #step2}

請使用 `ibmcloud at status` 指令來查看空間網域中可用事件的相關資訊。

* 若要取得空間網域中事件的相關資訊，請執行 `ibmcloud at status` 指令。
* 若要取得帳戶網域中事件的相關資訊，請執行 `ibmcloud at status` 指令並搭配 `-a` 選項。

如需相關資訊，請參閱[檢視事件資訊](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-viewing_event_status#viewing_event_status)。
  


## 步驟 3：建立階段作業
{: #step3}

需要階段作業以定義可供下載的事件資料範圍，以及保留下載的狀態。 

請使用 `ibmcloud at session create` 指令來建立階段作業。依預設，階段作業會包括過去 2 週的資料。在建立階段作業時，您可以選擇性地指定開始日期和結束日期，以指定時間範圍、當天的特定小時，以及事件的範圍。 

**附註：** 

* 當您指定開始日期和結束日期時，階段作業可讓您存取這些內含日期之間的事件。 
* 您無法在每個階段作業下載超過 2 週的資料。因此，時間範圍必須小於 2 週。
* 您可以下載地區中空間網域或帳戶網域的事件。

若要建立階段作業用來下載特定日期的事件，請執行下列指令：

```
ibmcloud at session create -s 2017-07-25 -e 2017-07-25
```
{: codeblock}

階段作業會傳回下列資訊：

* 要下載的日期範圍。
* 指出要包含可用於整個帳戶的事件還是僅包含現行空間事件的資訊。依預設，您會收到您已登入之空間的事件。
* 下載事件所需的階段作業 ID。
* 建立階段作業的使用者 ID。

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

**提示：**若要查看作用中階段作業的清單，請執行 `ibmcloud at session list` 指令。

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


## 步驟 4：將事件下載至檔案
{: #step4}

若要下載由階段作業參數指定的事件，請執行下列指令：

```
ibmcloud at download -o Events_File_Name Session_ID
```
{: codeblock}

其中

* Events_File_Name 是輸出檔的名稱。
* Session_ID 是階段作業的 GUID。您在前一個中已得到這個值。請將此值用於 **Id** 欄位。

例如：

```
ibmcloud at download -o Events_File_Name.log 32c657c5-31c0-4a3c-a139-b380871c737a
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

下載完成之後，您必須使用 `ibmcloud at session delete` 指令來刪除階段作業。 

請執行下列指令以刪除階段作業：

```
ibmcloud at session delete Session_ID
```
{: codeblock}

其中 Session_ID 是前一個步驟中所建立之階段作業的 GUID。請將此值用於 **Id** 欄位。

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




