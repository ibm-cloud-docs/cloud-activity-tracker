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

使用本指導教學，學習如何使用 {{site.data.keyword.cloudaccesstrailshort}} CLI 來透過指令行管理事件。瞭解如何取得儲存事件的相關資訊、如何下載儲存在 {{site.data.keyword.IBM_notm}} Cloud 中的事件，或如何刪除事件。
{:shortdesc}

請完成下列步驟：

1. [佈建 {{site.data.keyword.keymanagementservicelong_notm}} 並產生事件](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#tutorial2_step1)
2. [取得儲存事件的相關資訊 (ibmcloud at status)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#tutorial2_step2)
2. [指定透過建立階段作業來下載哪些日誌 (ibmcloud at session create)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#tutorial2_step3)
3. [取得實際日誌資料 (ibmcloud at download)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#tutorial2_step4)
4. [下載完成之後刪除階段作業 (ibmcloud at session delete)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#tutorial2_step5)
5. [手動刪除不需要的日誌 (ibmcloud at delete)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#tutorial2_step6)


## 假設
{: #tutorial2_assumptions}

1. 您有 {{site.data.keyword.cloud_notm}} 使用者 ID，其具有開發人員許可權，可以在佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務的 {{site.data.keyword.cloud_notm}} 帳戶空間中運作。 

    如需如何佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務的相關資訊，請參閱[佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務](/docs/services/cloud-activity-tracker/how-to/provision.html#provision)。

2. 您已使用超值方案來佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務的實例。

    **附註：**{{site.data.keyword.cloudaccesstrailshort}} CLI 無法與精簡方案一起使用。

3. 您已在本端系統中安裝 {{site.data.keyword.cloudaccesstrailshort}} CLI。您若要能使用 {{site.data.keyword.cloudaccesstrailshort}} CLI 來透過指令行管理事件，這是必要項目。 

    如需安裝 {{site.data.keyword.cloudaccesstrailshort}} CLI 的相關資訊，請參閱[配置 {{site.data.keyword.cloudaccesstrailshort}} CLI](/docs/services/cloud-activity-tracker/how-to/config_cli.html#config_cli)。

4. 您已透過指令行登入 {{site.data.keyword.cloud_notm}}。對於本指導教學，請從終端機執行下列指令： 

    `ibmcloud login -a api.ng.bluemix.net`，以登入美國南部地區。如需相關資訊，請參閱 [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login)。
    
    `ibmcloud target -o OrgName -s SpaceName`，以設定佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務的目標組織及空間。如需相關資訊，請參閱 [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target)。


## 步驟 1：佈建 IBM Key Protect 服務並產生事件 
{: #tutorial2_step1}
	
請完成下列步驟，以在 {{site.data.keyword.cloud_notm}} 中佈建 {{site.data.keyword.keymanagementserviceshort}} 服務，並產生事件：

1. 在美國南部地區佈建 {{site.data.keyword.keymanagementserviceshort}} 服務的實例。如需相關資訊，請參閱[從 IBM Cloud 主控台佈建](/docs/services/key-protect/provision.html#provision)。

2. 針對您計劃用來使用金鑰的使用者定義 {{site.data.keyword.cloud_notm}} 許可權。 

    * 使用者需要一個 IAM 原則，且服務角色設為*管理員* 或*撰寫者* 才能建立金鑰。
	* 使用者需要一個 IAM 原則，且服務角色設為*管理員* 才能刪除金鑰。
	* 使用者需要一個 IAM 原則，且服務角色設為*讀者* 才能查看金鑰。 

3. 使用 {{site.data.keyword.keymanagementserviceshort}} 服務建立安全金鑰，以產生 {{site.data.keyword.cloudaccesstrailshort}} 事件資料。如需相關資訊，請參閱[建立新金鑰](/docs/services/key-protect/create-standard-keys.html#create-standard-keys)。

{{site.data.keyword.cloudaccesstrailshort}} 事件會因為建立金鑰而產生。

## 步驟 2：取得儲存事件的相關資訊
{: #tutorial2_step2}

{{site.data.keyword.keymanagementserviceshort}} 事件可在 {{site.data.keyword.cloudaccesstrailshort}} 帳戶網域中取得。

在本指導教學中，{{site.data.keyword.keymanagementserviceshort}} 事件可在美國南部帳戶網域中取得，此網域是您佈建 {{site.data.keyword.keymanagementserviceshort}} 服務的地區。 

請執行下列指令，以取得在特定日期收集之事件的相關資訊：

```
ibmcloud at status -s startDate -e endDate -a
```
{: codeblock}

其中 

* `-s` 用來設定開始日。 
* `startDate` 代表開始日期。格式為 *YYYY-MM-DD*。
* `-e` 用來設定結束日期。
* `endDate` 代表結束日期。格式為 *YYYY-MM-DD*。
* `-a` 用來指出包括帳戶網域上的事件。

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

此指令將計算 2017 年 6 月 25 日的事件。{{site.data.keyword.cloudaccesstrailshort}} 是廣域服務，因此，日期使用「世界標準時間」。若要取得完整的當地時間日，您可能需要下載多個 UTC 日。




## 步驟 3：指定要下載的事件
{: #tutorial2_step3}

下載事件之前，請先建立階段作業。階段作業指定將下載哪些事件。


請使用下列指令來建立階段作業：

```
ibmcloud at session create -s startDate -e endDate -a
```
{: codeblock}

其中 

* `-s` 用來設定開始日。 
* `startDate` 代表開始日期。格式為 *YYYY-MM-DD*。
* `-e` 用來設定結束日期。
* `endDate` 代表結束日期。格式為 *YYYY-MM-DD*。
* `-a` 用來指出包括帳戶網域上的事件。

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

* `-s` 用來設定開始日。
* `-e` 用來設定結束日期。
* `-a` 用來指出包括帳戶網域上的事件。

有一個與階段作業相關聯的開始日期及結束日期。download 指令將包含這些內含日期之間的事件。

指令輸出中的重要部分是階段作業 `Id`。在 download 指令中會參照它。

若要取得現有階段作業的相關資訊，請鍵入 `ibmcloud at session list`。

若要進一步瞭解階段作業及 `ibmcloud at session create` 指令，請參閱 [CLI 參考資料](/docs/services/cloud-activity-tracker/reference/at_cli_cloud.html#session_create)。

請使用 `ibmcloud at session help create` 來取得指令行的說明。

## 步驟 4：下載針對階段作業所定義的範圍而識別的事件
{: #tutorial2_step4}

若要下載由階段作業參數指定的事件，請執行下列指令：

```
ibmcloud at events download -o outputFile sessionID
```
{: codeblock}

* `-o` 參數會指定輸出檔。
* `outputFile` 是本端檔案的名稱。
* `sessionID` 最後指定。您可以從 `ibmcloud at session create` 指令的輸出取得階段作業 ID 的值。

所下載資料的格式為壓縮 JSON。 

例如：

```
$ ibmcloud at events download -o events.log 21b19aeb-3d32-4c60-b912-517609c62db2
 6.70 KiB / 3.06 KiB [================================================================================================================================================================] 219.03% 8.60 MiB/s 0s
Download Successful
```
{: screen} 

進度指示器會在事件下載時從 0 移動到 100%。

若要進一步瞭解 `ibmcloud at download` 指令，請參閱 [CLI 參考資料](/docs/services/cloud-activity-tracker/reference/at_cli_cloud.html#download)。

請使用 `ibmcloud at help download` 來取得指令行的說明。

## 步驟 5：刪除階段作業
{: #tutorial2_step5}

下載完成之後，請刪除階段作業。執行下列指令：

```
ibmcloud at session delete sessionID
```
{: codeblock}

其中 

* `sessionID` 是您要刪除之階段作業的 ID。

階段作業數目有限制。不會自動刪除階段作業。您必須手動刪除不需要的階段作業。 

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

若要進一步瞭解 `ibmcloud at session delete` 指令，請參閱 [CLI 參考資料](/docs/services/cloud-activity-tracker/reference/at_cli_cloud.html#session_delete)。

請使用 `ibmcloud at session help delete` 來取得指令行的說明。

## 步驟 6：自動從 Activity Tracker 刪除事件
{: #tutorial2_step6}

您可以在 {{site.data.keyword.cloudaccesstrailshort}} 中控制自己的事件保留。您可以手動刪除事件，也可以自動刪除事件。

若要從空間手動刪除事件，請執行 `ibmcloud at delete` 指令。例如：

```
$ ibmcloud at delete -s 2017-07-25 -e 2017-07-25
Deleted successfully
"6 logs were deleted,freeing 13737 bytes."
```
{: screen}

若要進一步瞭解 `ibmcloud at delete` 指令，請參閱 [CLI 參考資料](/docs/services/cloud-activity-tracker/reference/at_cli_cloud.html#delete)。

請使用 `ibmcloud at help delete` 來取得指令行的說明。

**附註：**若要自動刪除事件，您可以使用 CLI 指令 `ibmcloud at option` 設定保留原則。如需相關資訊，請參閱 [CLI 參考資料](/docs/services/cloud-activity-tracker/reference/at_cli_cloud.html#option)。


