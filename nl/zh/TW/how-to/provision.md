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


# 佈建 Activity Tracker 服務
{: #provision}

您可以從 {{site.data.keyword.Bluemix}} 使用者介面或從指令行來佈建 {{site.data.keyword.cloudaccesstraillong}} 服務。
{:shortdesc}


## 從使用者介面佈建
{: #ui}

請完成下列步驟，以在 {{site.data.keyword.Bluemix_notm}} 中佈建 {{site.data.keyword.cloudaccesstraillong_notm}} 服務的實例：

1. 登入 {{site.data.keyword.Bluemix_notm}} 帳戶。

    {{site.data.keyword.Bluemix_notm}} 儀表板位於：[http://bluemix.net ![外部鏈結圖示](../../../icons/launch-glyph.svg "外部鏈結圖示")](http://bluemix.net){:new_window}。
    
	使用您的使用者 ID 及密碼登入之後，會開啟 {{site.data.keyword.Bluemix_notm}} 使用者介面。

2. 按一下**型錄**。即會開啟 {{site.data.keyword.Bluemix_notm}} 上可用的服務清單。

3. 選取**安全**種類，以過濾顯示的服務清單。

    服務也可提供於 **DevOps** 種類下。

4. 按一下 **Activity Tracker** 磚。

5. 配置定義將佈建服務之處的資訊。 

    如下表所示輸入資料： 

    <table>
	  <caption>表 1. 佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務所需的欄位</caption>
	  <tr>
	    <th>欄位</th>
		<th>值</th>
	  </tr>
	  <tr>
	    <td>選取要部署在哪個地區：</td>
		<td>有效值為：美國南部、英國、德國</td>
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

6. 選取服務方案。 

    依預設，會設定 **free** 方案。

    如需相關資訊，請參閱[服務方案](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#plans)。
	
7. 按一下**建立**，以在您已登入的 {{site.data.keyword.Bluemix_notm}} 空間中佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務。
  
 

## 從 CLI 佈建
{: #cli}

請完成下列步驟，以透過指令行在 {{site.data.keyword.Bluemix_notm}} 中佈建 {{site.data.keyword.cloudaccesstraillong_notm}} 服務的實例：

1. 安裝 Cloud Foundry (CF) CLI。如果已安裝 CF CLI，請繼續進行下一步。

   如需相關資訊，請參閱[安裝 cf CLI ![外部鏈結圖示](../../../icons/launch-glyph.svg "外部鏈結圖示")](http://docs.cloudfoundry.org/cf-cli/install-go-cli.html){: new_window}。 
    
2. 登入 {{site.data.keyword.Bluemix_notm}} 地區、組織及空間。 

    例如，若要登入美國南部地區，請執行下列指令：

    ```
    cf login -a https://api.ng.bluemix.net
    ```
    {: codeblock}

    遵循指示。輸入您的 {{site.data.keyword.Bluemix_notm}} 認證，選取組織和空間。
	
3. 執行 `cf create-service` 指令，以佈建實例。

	```
	cf create-service service_name service_plan service_instance_name
	```
	{: codeblock}
	
	其中
	
	* service_name 是服務的名稱，亦即 **activityTracker**。
	* service_plan 是服務方案名稱。如需方案清單，請參閱[服務方案](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#plans)。
	* service_instance_name 是您要用於建立之新服務實例的名稱。
	
	如需 cf 指令的相關資訊，請參閱 [cf create-service](/docs/cli/reference/cfcommands/index.html#cf_create-service)。

	例如，若要建立具有精簡方案的 {{site.data.keyword.cloudaccesstrailshort}} 服務實例，請執行下列指令：
	
	```
	cf create-service activityTracker free my_activity_tracker_svc
	```
	{: codeblock}
	
4. 驗證服務已順利建立。執行下列指令：

	```	
	cf services
	```
	{: codeblock}
	
	執行指令的輸出看起來如下：
	
	```
    Getting services in org MyOrg / space MySpace as xxx@yyy.com...
    OK
    
    name                           service                  plan                   bound apps              last operation
    my_activity_tracker_svc        activityTracker          free                                           create succeeded
	```
	{: screen}

	



