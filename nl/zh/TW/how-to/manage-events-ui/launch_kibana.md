---

copyright:
  years: 2016, 2017

lastupdated: "2017-09-17"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# 導覽至 Kibana 儀表板
{: #launch_kibana}

您可以從 {{site.data.keyword.Bluemix}} 的 {{site.data.keyword.cloudaccesstrailshort}} 使用者介面啟動 Kibana，或是直接從 Web 瀏覽器啟動 Kibana。
{:shortdesc}
   

##  從 Activity Tracker 服務的儀表板導覽至 Kibana
{: #launch_Kibana_from_at}

Kibana 顯示的活動日誌包括所有資源的事件，這些資源部署在您登入的 {{site.data.keyword.Bluemix_notm}} 組織的空間內，以及佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務的位置。

完成下列步驟，以從 {{site.data.keyword.cloudaccesstrailshort}} 服務的儀表板導覽至 Kibana：

1. 登入 {{site.data.keyword.Bluemix_notm}} 帳戶。

    {{site.data.keyword.Bluemix_notm}} 儀表板位於：[http://bluemix.net ![外部鏈結圖示](../../../../icons/launch-glyph.svg "外部鏈結圖示")](http://bluemix.net){:new_window}。
    
	使用您的使用者 ID 及密碼登入之後，會開啟 {{site.data.keyword.Bluemix_notm}} 使用者介面。

2. 從 {{site.data.keyword.Bluemix_notm}} 儀表板選取 {{site.data.keyword.cloudaccesstrailshort}} 服務。 
    
3. 選取**受管理**標籤。

4. 按一下**進階視圖**。 

    Kibana 儀表板隨即開啟。

依預設，**ActivityTracker_Space_Dashboard_in_24h** 儀表板會載入，並將時間過濾器設為過去 24 小時。 


	
	
##  從 Web 瀏覽器導覽至 Kibana
{: #launch_Kibana_from_browser}

Kibana 顯示的日誌資訊包括所有資源的事件，這些資源部署在您登入的 {{site.data.keyword.Bluemix_notm}} 組織的空間內。

完成下列步驟，以從瀏覽器啟動 Kibana：

1. 開啟 Web 瀏覽器，並啟動 Kibana。然後，登入 Kibana 使用者介面。
    
    例如，下表列出了每個地區啟動 Kibana 時必須使用的 URL：
      
    <table>
          <caption>表 1. 每個地區啟動 Kibana 的 URL</caption>
           <tr>
            <th>地區</th>
            <th>URL</th>
          </tr>
          <tr>
            <td>美國南部</td>
            <td>[https://logging.ng.bluemix.net](https://logging.ng.bluemix.net) </td>
          </tr>
		  <tr>
            <td>英國</td>
            <td>[https://logmet.eu-gb.bluemix.net](https://logmet.eu-gb.bluemix.net)</td>
          </tr>
    </table>
	
	這時會開啟 Kibana 中的「探索」頁面。
	
2. 驗證您已登入 {{site.data.keyword.Bluemix_notm}} 帳戶、組織及您要檢視的空間，並分析活動日誌。

    您可以在您已登入的空間中，查看可用的事件及日誌。

3. 若要過濾事件，請從功能表列選取**開啟**。

    畫面上會顯示儲存的儀表板清單。
	
4. 若要檢視您已登入之空間的事件，請選取 **ActivityTracker_Space_Dashboard_in_24h**。


## 限制
{: #limitations}

 由於 Kibana 中的限制，您不能在相同階段作業中一次開啟多個 Kibana 瀏覽器分頁，以檢視不同的空間或帳戶。因此，如果您一次同時開啟了兩個以上的階段作業，並將範圍從空間變更為帳戶（反之亦然），則可能會遇到問題。
	



