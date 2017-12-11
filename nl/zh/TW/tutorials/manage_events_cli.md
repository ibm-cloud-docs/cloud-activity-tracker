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

使用本指導教學，學習如何使用 {{site.data.keyword.cloudaccesstrailshort}} CLI 來透過指令行管理事件。瞭解如何取得儲存事件的相關資訊、如何下載儲存在 {{site.data.keyword.IBM_notm}} Cloud 中的事件，或如何刪除事件。
{:shortdesc}

請完成下列步驟：

1. [佈建 {{site.data.keyword.IBM_notm}} Key Protect 服務並產生事件](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step1)
2. [取得儲存事件的相關資訊 (cf at status)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step2)
2. [指定建立階段作業時要下載什麼日誌 (cf at session create)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step3)
3. [取得實際日誌資料 (cf at download)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step4)
4. [下載完成之後刪除階段作業 (cf at session delete)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step5)
5. [手動刪除不需要的日誌 (cf at delete)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step6)


## 假設
{: #assumptions}

1. 您有 {{site.data.keyword.Bluemix_notm}} 使用者 ID ，它有開發人員許可權，可以在佈建 {{site.data.keyword.IBM_notm}} Cloud {{site.data.keyword.cloudaccesstrailshort}} 服務的 {{site.data.keyword.Bluemix_notm}} 帳戶空間中使用。 

    如需如何佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務的相關資訊，請參閱[佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務](/docs/services/cloud-activity-tracker/how-to/provision.html#provision)。

2. 您已在本端系統中安裝 {{site.data.keyword.cloudaccesstrailshort}} CF 外掛程式。您若要能使用 {{site.data.keyword.cloudaccesstrailshort}} CLI 來透過指令行管理事件，這是必要項目。 

    如需安裝 {{site.data.keyword.cloudaccesstrailshort}} CF 外掛程式的相關資訊，請參閱[配置 {{site.data.keyword.cloudaccesstrailshort}} CLI](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#config_at_cli)。

3. 您已使用下列指令，透過指令行登入 {{site.data.keyword.Bluemix_notm}}：

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

    例如，執行下列指令以登入美國南部地區：
	
	```
	bx cf login -a api.ng.bluemix.net
	```
	{: codeblock}

	**附註：**您必須登入 {{site.data.keyword.cloudaccesstrailshort}} 服務佈建所在的 {{site.data.keyword.Bluemix_notm}} 地區、組織和空間，以便能夠透過指令行來執行 {{site.data.keyword.cloudaccesstrailshort}} 指令及管理事件。
	
	然後，設定組織及空間。執行下列指令：

    ```
    bx target -o OrgName -s SpaceName
    ```
    {: codeblock}

    其中

    * OrgName 是組織的名稱。
    * SpaceName 是空間的名稱。


## 步驟 1：佈建 IBM Key Protect 服務並產生事件 
{: #step1}
	
1. 請完成下列步驟，以在 {{site.data.keyword.Bluemix_notm}} 中佈建 {{site.data.keyword.keymanagementserviceshort}} 服務的實例：

    1. 登入 {{site.data.keyword.Bluemix_notm}} 帳戶。

        {{site.data.keyword.Bluemix_notm}} 儀表板位於：[http://bluemix.net](http://bluemix.net)

        使用您的使用者 ID 及密碼登入之後，會開啟 {{site.data.keyword.Bluemix_notm}} 使用者介面。

    2. 按一下**型錄**。即會開啟 {{site.data.keyword.Bluemix_notm}} 上可用的服務清單。

        選取**安全**種類，以過濾顯示的服務清單。

    3. 選取 **Key Protect** 磚。

    4. 按一下**建立**，以在您已登入的 {{site.data.keyword.Bluemix_notm}} 空間中佈建 {{site.data.keyword.keymanagementserviceshort}} 服務。

2. 完成下列步驟，以產生 {{site.data.keyword.cloudaccesstrailshort}} 事件：

    1. 從 {{site.data.keyword.Bluemix_notm}} 儀表板中，選取 {{site.data.keyword.keymanagementserviceshort}} 服務。{{site.data.keyword.keymanagementserviceshort}} 儀表板隨即開啟。然後，選取**管理**標籤。

    2. 按一下**新增金鑰**。即會開啟一個新視窗。

        ![新增金鑰的 {{site.data.keyword.keymanagementserviceshort}} 視窗](images/KP_f2.gif)

    3. 選取**產生金鑰**，並完成下列步驟：

        * 輸入金鑰的名稱，例如 *MyFirstKey*。

        * 為金鑰選擇一個演算法。

        * 按一下**新增金鑰**。 

3. 驗證是否已建立事件：

    1. 從 {{site.data.keyword.Bluemix_notm}} 儀表板中，選取 {{site.data.keyword.cloudaccesstrailshort}} 服務。服務儀表板隨即開啟。

    2. 配置視圖，以搜尋在您佈建服務及新增金鑰時產生的 {{site.data.keyword.keymanagementserviceshort}} 事件。

        * 針對*檢視日誌* 欄位選取**空間日誌**。
	    * 針對*搜尋欄位* 欄位選取 **target.name**。
	    * 在*過濾器* 欄位中，輸入 **ibm-key-protect**。
	
	    顯示的資料會對應於過去 24 小時可用的 {{site.data.keyword.keymanagementserviceshort}} 事件。 

	    ![{{site.data.keyword.cloudaccesstrailshort}} 管理標籤](images/KP_f3.gif)

## 步驟 2：取得儲存事件的相關資訊
{: #step2}

請檢查有哪些事件可供下載。例如，如果您在現行日期佈建並新增金鑰，請執行下列指令，以取得今天收集之事件的相關資訊：

```
bx cf at status -s 2017-07-25 -e 2017-07-25
+------------+-------+-------+------------+
| Date       | Count | Size  | Searchable |
+------------+-------+-------+------------+
| 2017-07-25 | 12    | 34994 | All        |
+------------+-------+-------+------------+
```
{: screen}

此指令將計算 2017 年 6 月 25 日的事件。{{site.data.keyword.cloudaccesstrailshort}} 是廣域服務，因此，日期使用「世界標準時間」。若要取得完整的當地時間日，您可能需要下載多個 UTC 日。

若要查看多天的資訊，請使用 `-s` 來設定開始日，並使用 `-e` 來設定結束日期。 

若要進一步瞭解 `cf at status` 指令，請參閱 [CLI 參考資料](/docs/services/cloud-activity-tracker/cli/at_cli.html#status)。

請使用 `bx cf at help status` 來取得指令行的說明。

## 步驟 3：指定要下載的事件
{: #step3}

下載事件之前，請先建立階段作業：

* 階段作業指定將下載哪些事件。
* 如果事件下載遭到岔斷，則階段作業讓您能從它岔斷之處繼續下載。

請使用下列指令以建立階段作業：

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

有一個與階段作業相關聯的開始日期和結束日期。download 指令將包含這些內含日期之間的事件。預設日期範圍為僅限當天。 

指令輸出中的重要部分是階段作業 `Id`。在 download 指令中會參照它。

若要取得現有階段作業的相關資訊，請鍵入 `cf at session list`。

若要進一步瞭解階段作業及 `cf at session create` 指令，請參閱 [CLI 參考資料](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_create)。

請使用 `cf at session help create` 來取得指令行的說明。

## 步驟 4：下載針對階段作業所定義的範圍而識別的事件
{: #step4}

若要下載由階段作業參數指定的事件，請執行下列指令：

```
$ bx cf at events download -o events.log 21b19aeb-3d32-4c60-b912-517609c62db2
 6.70 KiB / 3.06 KiB [================================================================================================================================================================] 219.03% 8.60 MiB/s 0s
Download Successful
```

* `-o` 參數會指定輸出檔。
* 階段作業 ID 最後指定。您可以從 `cf at session create` 指令的輸出取得階段作業 ID 的值。
* 進度指示器會在事件下載時從 0 移動到 100%。

所下載資料的格式為壓縮 JSON。 

若要進一步瞭解 `cf at download` 指令，請參閱 [CLI 參考資料](/docs/services/cloud-activity-tracker/cli/at_cli.html#download)。

請使用 `bx cf at help download` 來取得指令行的說明。

## 步驟 5：刪除階段作業
{: #step5}

下載完成之後，請刪除階段作業。 

階段作業數目有限制。不會自動刪除階段作業。您必須手動刪除不需要的階段作業。 

```
$ bx cf at session delete 21b19aeb-3d32-4c60-b912-517609c62db2
+---------+------------------------+
| name    | value                  |
+---------+------------------------+
| message | Delete session success |
+---------+------------------------+
```

若要進一步瞭解 `cf at session delete` 指令，請參閱 [CLI 參考資料](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_delete)。

請使用 `bx cf at session help delete` 來取得指令行的說明。

## 步驟 6：從 Activity Tracker 手動刪除事件
{: #step6}

您可以在 {{site.data.keyword.cloudaccesstrailshort}} 中控制自己的事件保留。您可以手動刪除事件，也可以自動刪除事件。

若要手動刪除事件，請執行 `cf at delete` 指令。例如：

```
$ bx cf at delete -s 2017-07-25 -e 2017-07-25
Deleted successfully
"6 logs were deleted,freeing 13737 bytes."
```

若要進一步瞭解 `cf at delete` 指令，請參閱 [CLI 參考資料](/docs/services/cloud-activity-tracker/cli/at_cli.html#delete)。

請使用 `bx cf at help delete` 來取得指令行的說明。

**附註：**若要自動刪除事件，您可以使用 CLI 指令 `cf at option` 設定保留原則。如需相關資訊，請參閱 [CLI 參考資料](/docs/services/cloud-activity-tracker/cli/at_cli.html#option)。


