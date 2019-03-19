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



# 導覽至 Kibana 儀表板
{: #launch_kibana}

您可以從 {{site.data.keyword.Bluemix}} 的 {{site.data.keyword.cloudaccesstrailshort}} 使用者介面啟動 Kibana，或是直接從 Web 瀏覽器啟動 Kibana。
{:shortdesc}
   

##  從 Activity Tracker 服務的儀表板導覽至 Kibana
{: #launch_Kibana_from_at}

Kibana 顯示的活動日誌包括所有資源的事件，這些資源部署在您登入的 {{site.data.keyword.cloud_notm}} 組織的空間內，以及佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務的位置。

完成下列步驟，以從 {{site.data.keyword.cloudaccesstrailshort}} 服務的儀表板導覽至 Kibana：

1. 登入 {{site.data.keyword.cloud_notm}} 帳戶。

    {{site.data.keyword.cloud_notm}} 儀表板位於：[https://cloud.ibm.com/login ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://cloud.ibm.com/login){:new_window}。
    
	使用您的使用者 ID 及密碼登入之後，會開啟 {{site.data.keyword.cloud_notm}} 使用者介面。

2. 從 {{site.data.keyword.cloud_notm}} 儀表板選取 {{site.data.keyword.cloudaccesstrailshort}} 服務。 
    
3. 選取**受管理**標籤。

4. 若要檢視空間事件，請在*檢視日誌*欄位選取**空間日誌**。**附註：**這是預設視圖。然後，按一下**在 Kibana 中檢視**。 

    Kibana 儀表板隨即開啟。**ActivityTracker_Space_Dashboard_in_24h** 儀表板會載入，並將時間過濾器設為過去 24 小時。

5. 若要檢視帳戶事件，請在*檢視日誌*欄位選取**帳戶日誌**。然後，按一下**在 Kibana 中檢視**。 

    **ActivityTracker_Account_Dashboard_in_24h** 儀表板會載入，並將時間過濾器設為過去 24 小時。
	
	
##  從 Web 瀏覽器導覽至 Kibana
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
            <td>[https://logging.eu-fra.bluemix.net](https://logging.eu-fra.bluemix.net) </td>
          </tr>
          <tr>
            <td>雪梨</td>
            <td>[https://logging.au-syd.bluemix.net](https://logging.au-syd.bluemix.net) </td>
          </tr>
		  <tr>
            <td>英國</td>
            <td>[https://logging.eu-gb.bluemix.net](https://logging.eu-gb.bluemix.net)</td>
          </tr>
		  <tr>
            <td>美國南部</td>
            <td>[https://logging.ng.bluemix.net](https://logging.ng.bluemix.net) </td>
          </tr>
    </table>
	
	這時會開啟 Kibana 中的「探索」頁面。
	
2. 驗證您已登入您要檢視的 {{site.data.keyword.cloud_notm}} 帳戶，並分析活動日誌。

3. 選取**網域**。

    選取**帳戶**，以檢視帳戶網域中的事件。選取**空間**，以檢視空間網域中的事件。

您在 Kibana 中看到的事件，對應於在您啟動 Kibana 之地區中選取的網域所管理的事件。


## 限制
{: #launch_kibana_limitations}

 由於 Kibana 中的限制，您不能在相同階段作業中一次開啟多個 Kibana 瀏覽器分頁，以檢視不同的空間或帳戶。因此，如果您一次同時開啟了兩個以上的階段作業，並將範圍從空間變更為帳戶（反之亦然），則可能會遇到問題。
	



