---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, launch Kibana

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


# 開啟 Kibana 儀表板
{: #launch_kibana}

您可以從 {{site.data.keyword.cloud_notm}} 的 {{site.data.keyword.cloudaccesstrailshort}} 使用者介面啟動 Kibana，或是直接從 Web 瀏覽器啟動 Kibana。
{:shortdesc}
   
{{site.data.keyword.cloudaccesstrailfull}} 已淘汰。從 2019 年 5 月 9 日開始，您無法佈建新的 {{site.data.keyword.cloudaccesstrailshort}} 實例。現有的超值方案實例將支援到 2019 年 9 月 30 日為止。若要繼續監視 {{site.data.keyword.cloud_notm}} 帳戶的活動，請佈建 [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) 的實例。
{: deprecated}


##  從 Activity Tracker 服務的儀表板開啟 Kibana
{: #launch_Kibana_from_at}

Kibana 顯示的活動日誌包括所有資源的事件，這些資源部署在您登入的 {{site.data.keyword.cloud_notm}} 組織的空間內，以及佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務的位置。

完成下列步驟，以從 {{site.data.keyword.cloudaccesstrailshort}} 服務的儀表板導覽至 Kibana：

1. 登入 {{site.data.keyword.cloud_notm}} 帳戶。

    {{site.data.keyword.cloud_notm}} 儀表板位於：[https://cloud.ibm.com/login ![外部鏈結圖示](../../../icons/launch-glyph.svg "外部鏈結圖示")](https://cloud.ibm.com/login){:new_window}。
    
	使用您的使用者 ID 及密碼登入之後，會開啟 {{site.data.keyword.cloud_notm}} 使用者介面。

2. 從 {{site.data.keyword.cloud_notm}} 儀表板選取 {{site.data.keyword.cloudaccesstrailshort}} 服務。 
    
3. 選取**受管理**標籤。

4. 若要檢視空間事件，請在*檢視日誌*欄位選取**空間日誌**。**附註：**這是預設視圖。然後，按一下**在 Kibana 中檢視**。 

    Kibana 儀表板隨即開啟。**ActivityTracker_Space_Dashboard_in_24h** 儀表板會載入，並將時間過濾器設為過去 24 小時。

5. 若要檢視帳戶事件，請在*檢視日誌*欄位選取**帳戶日誌**。然後，按一下**在 Kibana 中檢視**。 

    **ActivityTracker_Account_Dashboard_in_24h** 儀表板會載入，並將時間過濾器設為過去 24 小時。
	
	
##  從 Web 瀏覽器開啟 Kibana
{: #launch_Kibana_from_browser}

完成下列步驟，以從瀏覽器啟動 Kibana：

1. 在您要監視事件的地區，開啟 Web 瀏覽器並啟動 Kibana。然後，登入 Kibana 使用者介面。
    
    例如，下表列出了每個地區啟動 Kibana 時必須使用的 URL：
      
    <table>
          <caption>表 1. 每個地區啟動 Kibana 的 URL</caption>
           <tr>
            <th>地區</th>
            <th>URL</th>
          </tr>
          <tr>
            <td>德國</td>
            <td>`https://logging.eu-fra.bluemix.net`</td> </tr>
          <tr>
            <td>雪梨</td>
            <td>`https://logging.au-syd.bluemix.net` </td>
          </tr>
		  <tr>
            <td>英國</td>
            <td>`https://logging.eu-gb.bluemix.net`</td>
          </tr>
		  <tr>
            <td>美國南部</td>
            <td>`https://logging.ng.bluemix.net`</td> </tr>
    </table>
	
	這時會開啟 Kibana 中的「探索」頁面。
	
2. 驗證您已登入您要檢視的 {{site.data.keyword.cloud_notm}} 帳戶，並分析活動日誌。

3. 檢視空間或帳戶事件

* 按一下顯示您登入資訊的 Kibana 視窗右上角。
* 在**網域**中的下拉清單選取空間或帳戶。
* 針對空間事件，在「空間」下拉清單選取感興趣的**空間**。
* 針對帳戶事件，在「帳戶」下拉清單選取正確的**帳戶**。

4. 調整搜尋時間

* Kibana 預設搜尋時間設為前 15 分鐘。
* 在右上方的灰色列按一下`前 15 分鐘`。
* 選取您要看到多久以前的事件。可搜尋前 3 天的事件。挑選 3 天以內的時間範圍。

5. 過濾以便只顯示 Activity Tracker 事件
* 在 Kibana 中直接檢視時，您可能會同時遇到 Logs 和 Activity Tracker 事件。
* 在搜尋列輸入 `type:ActivityTracker`，只顯示 Activity Tracker 事件。

您在 Kibana 中看到的事件，對應於在您啟動 Kibana 之地區中選取的網域所管理的事件。

## 限制
{: #launch_kibana_limitations}

* 由於 Kibana 中的限制，您不能在相同階段作業中一次開啟多個 Kibana 瀏覽器分頁，以檢視不同的空間或帳戶。因此，如果您一次同時開啟了兩個以上的階段作業，並將範圍從空間變更為帳戶（反之亦然），則可能會遇到問題。
* 依預設，只有帳戶擁有者可以檢視帳戶事件。若要讓其他人能檢視帳戶事件，請遵循[檢視帳戶事件](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-view_acc_events#view_acc_events)中的指示。



