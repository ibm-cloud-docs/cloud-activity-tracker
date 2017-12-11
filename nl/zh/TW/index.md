---

copyright:
  years: 2016, 2017
lastupdated: "2017-09-17"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 入門指導教學
{: #getting-started-with-cla}

{{site.data.keyword.cloudaccesstrailfull}} 服務會記錄使用者起始的活動，這些活動會在 {{site.data.keyword.IBM}} 雲端中變更服務的狀態。使用本指導教學，學習如何使用 {{site.data.keyword.cloudaccesstrailfull}} 服務來監視使用者與「雲端」服務的互動。
{:shortdesc}

此入門指導教學的目標如下：

1. 顯示如何佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務。
2. 顯示如何使用雲端服務來產生自動由 {{site.data.keyword.cloudaccesstrailshort}} 服務收集的活動事件。事件會符合雲端審核資料聯盟 (CADF) 標準。
3. 顯示如何使用預先定義的 {{site.data.keyword.cloudaccesstrailshort}} 儀表板，以監視服務的雲端活動。

下圖顯示當使用者起始的活動變更服務的狀態時，發生的不同元件和動作：

![當使用者起始的活動變更服務的狀態時，發生的元件和動作](images/AT_f1.png "當使用者起始的活動變更服務的狀態時，發生的元件和動作")



## 開始之前
{: #prereqs}

建立 [{{site.data.keyword.Bluemix_notm}} 帳戶](https://console.bluemix.net/registration/)。您的使用者 ID 必須是 {{site.data.keyword.Bluemix_notm}} 帳戶的成員或擁有者，且在您計劃使用 {{site.data.keyword.cloudaccesstrailshort}} 服務的空間中具有開發人員許可權。


## 步驟 1：佈建 Activity Tracker
{: #step1}

您必須將 {{site.data.keyword.cloudaccesstrailshort}} 服務佈建在要監視其活動的雲端服務佈建所在的相同地區及空間中。佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務之後，會自動從該空間中佈建之選定雲端服務收集事件。如需您可以透過 {{site.data.keyword.cloudaccesstrailshort}} 監視活動的服務清單，請參閱[支援的雲端服務](/docs/services/cloud-activity-tracker/cloud_services.html#cloud_services)。

**附註：**本指導教學顯示如何使用 {{site.data.keyword.cloudaccesstrailshort}} 服務來監視使用者與雲端服務 {{site.data.keyword.keymanagementservicelong_notm}} 的互動。{{site.data.keyword.keymanagementserviceshort}} 服務可用於美國南部。因此，您必須在美國南部地區佈建 {{site.data.keyword.cloudaccesstrailshort}}，佈建在提供 {{site.data.keyword.keymanagementserviceshort}} 服務的相同空間。若要查看服務可用之地區的相關資訊，請參閱[依地區列出的服務](/docs/services/services_region.html#services_region)。

請完成下列步驟，以在 {{site.data.keyword.Bluemix_notm}} 中佈建 {{site.data.keyword.cloudaccesstraillong_notm}} 服務的實例：

1. 登入 {{site.data.keyword.Bluemix_notm}} 帳戶。

    {{site.data.keyword.Bluemix_notm}} 儀表板位於：[http://bluemix.net ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://bluemix.net){:new_window}。
    
	使用您的使用者 ID 及密碼登入之後，會開啟 {{site.data.keyword.Bluemix_notm}} 使用者介面。

2. 按一下**型錄**。即會開啟 {{site.data.keyword.Bluemix_notm}} 上可用的服務清單。

3. 選取**安全**種類，以過濾顯示的服務清單。

4. 按一下 **Activity Tracker** 磚。 

5. 配置定義將佈建服務之處的資訊。 

    如下表所示輸入資料： 

    <table>
	  <caption>表 1. 佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務所需的欄位</caption>
	  <tr>
	    <th width="50%">欄位</th>
		<th width="50%">值</th>
	  </tr>
	  <tr>
	    <td>選取要部署在哪個地區：</td>
		<td>美國南部</td>
	  </tr>
	  <tr>
	    <td>選擇組織：</td>
		<td>選取您計劃監視活動所在的組織。</td>
	  </tr>
	  <tr>
	    <td>選擇空間：</td>
		<td>在組織中選取您計劃監視活動所在的空間。</td>
	  </tr>
	</table>

6. 按一下**建立**，以在您已登入的 {{site.data.keyword.Bluemix_notm}} 空間中佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務。
   

## 步驟 2：佈建雲端服務 
{: #step2}
	
請完成下列步驟，以在 {{site.data.keyword.Bluemix_notm}} 美國南部地區中佈建 {{site.data.keyword.keymanagementserviceshort}} 服務的實例：

1. 登入 {{site.data.keyword.Bluemix_notm}} 帳戶。

    {{site.data.keyword.Bluemix_notm}} 儀表板位於：[http://bluemix.net ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://bluemix.net){:new_window}。
	
	使用您的使用者 ID 及密碼登入之後，會開啟 {{site.data.keyword.Bluemix_notm}} 使用者介面。

2. 按一下**型錄**。即會開啟 {{site.data.keyword.Bluemix_notm}} 上可用的服務清單。

    選取**安全**種類，以過濾顯示的服務清單。

3. 選取 **Key Protect** 磚。

4. 配置定義將佈建服務之處的資訊。 

    如下表所示輸入資料： 

    <table>
	  <caption>表 2. 佈建 {{site.data.keyword.keymanagementserviceshort}} 服務所需的欄位</caption>
	  <tr>
	    <th width="50%">欄位</th>
		<th width="50%">值</th>
	  </tr>
	  <tr>
	    <td>選取要部署在哪個地區：</td>
		<td>美國南部</td>
	  </tr>
	  <tr>
	    <td>選擇組織：</td>
		<td>選取您選擇佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務的組織。</td>
	  </tr>
	  <tr>
	    <td>選擇空間：</td>
		<td>選取您選擇佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務的空間。</td>
	  </tr>
	</table>

5. 按一下**建立**，以在您已登入的 {{site.data.keyword.Bluemix_notm}} 空間中佈建 {{site.data.keyword.keymanagementserviceshort}} 服務。


## 步驟 3：產生 Activity Tracker 事件
{: # step3}

在此步驟中，使用 {{site.data.keyword.keymanagementserviceshort}} 服務建立安全金鑰，以產生 {{site.data.keyword.cloudaccesstrailshort}} 事件資料。 

完成下列步驟，以產生 {{site.data.keyword.cloudaccesstrailshort}} 事件：

1. 從 {{site.data.keyword.Bluemix_notm}} 儀表板中，選取 **Key Protect** 服務。{{site.data.keyword.keymanagementserviceshort}} 儀表板隨即開啟。然後，選取**管理**標籤。

2. 按一下**新增金鑰**。即會開啟一個新視窗。

3. 選取**產生金鑰**，並完成下列步驟：

    * 輸入金鑰的名稱，例如 *MyFirstKey*。

    * 為金鑰選擇一個演算法。

    * 按一下**新增金鑰**。 
	
{{site.data.keyword.cloudaccesstrailshort}} 事件會因為建立金鑰而產生。

## 步驟 4：監視 Activity Tracker 事件
{: #step4}

在此步驟中，透過 {{site.data.keyword.Bluemix_notm}} 使用者介面來驗證是否已產生 {{site.data.keyword.cloudaccesstrailshort}} 事件。

請完成下列步驟來驗證是否已建立事件：

1. 從 {{site.data.keyword.Bluemix_notm}} 儀表板中，選取 {{site.data.keyword.cloudaccesstrailshort}} 服務。服務儀表板隨即開啟。

2. 配置視圖，以搜尋在您佈建服務及新增金鑰時產生的 {{site.data.keyword.keymanagementserviceshort}} 事件。

    * 針對*檢視日誌* 欄位選取**空間日誌**。
    * 針對*搜尋欄位* 欄位選取 **target.name**。
    * 在*過濾器* 欄位中，輸入 **ibm-key-protect**。
	
    顯示的資料會顯示過去 24 小時可用的 {{site.data.keyword.keymanagementserviceshort}} 事件。 
	
	![事件的使用者介面視圖](images/bmx_ui_space_view.png "事件的使用者介面視圖")


## 後續步驟
{: #next_steps}

接著，使用 {{site.data.keyword.cloudaccesstrailshort}} 預先定義 Kibana 儀表板來監視及分析事件日誌。若要啟動 Kibana，請參閱[導覽至 Kibana 儀表板](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_kibana.html#launch_kibana)。 

依預設，在 Kibana 中，空間活動日誌是透過 **ActivityTracker_Space_Search_in_24h** 儀表板來顯示：

![事件的 Kibana 視圖](images/kibana_space_view.png "事件的 Kibana 視圖")

您也可以使用 {{site.data.keyword.cloudaccesstrailshort}} CLI，從指令行管理事件。如需相關資訊，請參閱[檢視事件資訊](/docs/services/cloud-activity-tracker/how-to/manage-events-cli/viewing_event_information.html#viewing_event_status)。

                                                                                                                      

