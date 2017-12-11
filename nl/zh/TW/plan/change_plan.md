---

copyright:
  years: 2017
lastupdated: "2017-09-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# 變更方案
{: #change_plan}

您可以在 {{site.data.keyword.Bluemix_notm}} 中的服務「儀表板」變更 {{site.data.keyword.cloudaccesstraillong}} 服務方案，或執行 `cf update-service` 指令來變更。您可以隨時升級或降低您的方案。
{:shortdesc}

## 透過使用者介面變更服務方案
{: #change_plan_ui}

若要在 {{site.data.keyword.Bluemix_notm}} 中的服務「儀表板」變更服務方案，請完成下列步驟：

1. 登入 {{site.data.keyword.Bluemix_notm}}，然後從 {{site.data.keyword.Bluemix_notm}} 儀表板按一下 {{site.data.keyword.cloudaccesstraillong_notm}} 服務。 
    
2. 在 {{site.data.keyword.Bluemix_notm}} 使用者介面中選取**方案**標籤。

    畫面上會顯示現行方案的相關資訊。
	
3. 選取新方案以升級或降低您的方案。 

4. 按一下**儲存**。



## 透過 CLI 變更服務方案
{: #change_plan_cli}

若要透過 CLI 變更 Bluemix 中的服務方案，請完成下列步驟：

1. 登入 {{site.data.keyword.Bluemix_notm}} 地區、組織及空間。 

    ```
    cf login -a Endpoint
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
		<tr>
		  <td>英國</td>
		  <td>api.eu-gb.bluemix.net</td>
		</tr>
		<tr>
		  <td>德國</td>
		  <td>api.eu-de.bluemix.net</td>
		</tr>
	</table>

    遵循指示。輸入您的 {{site.data.keyword.Bluemix_notm}} 認證，選取組織和空間。 

    例如，執行下列指令以登入美國南部地區：
	
	```
	cf login -a api.ng.bluemix.net
	```
	{: codeblock}
	
2. 執行 `cf services` 指令來檢查現行方案，並從空間可用的服務清單中取得 {{site.data.keyword.cloudaccesstrailshort}} 服務名稱。 

    **名稱**欄位的值是您必須用來變更方案的值。 

    例如：
	
	```
	$ cf services
	Getting services in org MyOrg / space dev as xxx@yyy.com...
	OK
    
	name                            service              plan          bound apps      last operation
	Activity Tracker-oj            activityTracker       premium                       create succeeded
	```
	{: screen}
    
3. 升級或降低方案。執行 `cf update-service` 指令。
    
	```
	cf update-service service_name [-p new_plan]
	```
	{: codeblock}
	
	其中 
	
	* *service_name* 是服務的名稱。您可以執行 `cf services` 指令，以取得值。
	* *new_plan* 是方案的名稱。
	
	下表列出不同的方案及其支援的值：
	
	<table>
	  <caption>表 1. 方案清單。</caption>
	  <tr>
	    <th>方案</th>
	    <th>名稱</th>
	  </tr>
	  <tr>
	    <td>精簡</td>
	    <td>lite</td>
	  </tr>
	  <tr>
	    <td>進階</td>
	    <td>premium</td>
	  </tr>
	</table>
	
	例如，若要將您的方案降低為*精簡* 方案，請執行下列指令：
	
	```
	cf update-service "Activity Tracker-oj" -p lite
	Updating service instance Activity Tracker-oj as xxx@yyy.com...
	OK
	```
	{: screen}

4. 驗證新的方案已變更。執行 `cf services` 指令。

	```
	cf services
	Getting services in org MyOrg / space dev as xxx@yyy.com...
	OK

	name                   service            plan      bound apps   last operation
	Activity Tracker-oj    activityTracker    lite                   update succeeded
	```
	{: screen}






