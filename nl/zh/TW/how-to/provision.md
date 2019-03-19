---

copyright:
  years: 2016, 2019
lastupdated: "2019-02-18"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}



# 佈建 Activity Tracker
{: #provision}

您可以從 {{site.data.keyword.Bluemix}} 使用者介面或從指令行，佈建 {{site.data.keyword.cloudaccesstraillong}} 服務。
{:shortdesc}


## 從使用者介面佈建
{: #provision_ui}

請完成下列步驟，以在 {{site.data.keyword.cloud_notm}} 中佈建 {{site.data.keyword.cloudaccesstraillong_notm}} 服務的實例：

1. 登入 {{site.data.keyword.cloud_notm}} 帳戶。

    {{site.data.keyword.cloud_notm}} 使用者介面位於：[http://bluemix.net ![外部鏈結圖示](../../../icons/launch-glyph.svg "外部鏈結圖示")](http://bluemix.net){:new_window}。
    
	使用您的使用者 ID 及密碼登入之後，會開啟 {{site.data.keyword.cloud_notm}} 使用者介面。

2. 按一下**型錄**。即會開啟 {{site.data.keyword.cloud_notm}} 上可用的服務清單。

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
		<td>有效值為：美國南部、英國、德國、雪梨</td>
	  </tr>
	  <tr>
	    <td>選擇組織：</td>
		<td>選取您計劃監視活動的組織。</td>
	  </tr>
	  <tr>
	    <td>選擇空間：</td>
		<td>在您已選取的組織中選取計劃監視活動的空間。</td>
	  </tr>
	</table>

6. 選取服務方案。 

    依預設，會設定 **free** 方案。

    如需相關資訊，請參閱[服務方案](/docs/services/cloud-activity-tracker/how-to/change_plan.html#change_plan)。
	
7. 按一下**建立**，以在您已登入的 {{site.data.keyword.cloud_notm}} 空間中佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務。
  
 

## 從 CLI 佈建
{: #provision_cli}

請完成下列步驟，以透過指令行在 {{site.data.keyword.cloud_notm}} 中佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務的實例：

1. [必要條件] 安裝 {{site.data.keyword.cloud_notm}} CLI。

   如需相關資訊，請參閱[安裝 {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-ibmcloud-cli#ibmcloud-cli)。
   
   如果已安裝 CLI，請繼續進行下一步。
    
2. 登入 {{site.data.keyword.cloud_notm}}。 

    執行 [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) 指令以登入 {{site.data.keyword.cloud_notm}}，然後執行 [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) 指令，以設定您要在其中佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務的組織及空間。
	
3. 執行 `ibmcloud service create` 指令，以佈建實例。

    ```
	ibmcloud service create service_name service_plan service_instance_name
	```
	{: codeblock}
	
	其中
	
	* service_name 是服務的名稱，即 **accessTrail**。
	* service_plan 是服務方案名稱。如需方案的清單，請參閱[服務方案](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#activity_tracker_ov_plan)。
	* service_instance_name 是您要用於建立之新服務實例的名稱。

	例如，若要建立具有標準方案的 {{site.data.keyword.cloudaccesstrailshort}} 服務實例，請執行下列指令：
	
	```
	ibmcloud service create accessTrail free my_activitytracker_svc
	```
	{: codeblock}
	
4. 驗證服務已順利建立。執行下列指令：

    ```	
	ibmcloud service list
	```
	{: codeblock}
	
	執行指令的輸出看起來如下：
	
	```
    Getting services in org MyOrg / space MySpace as xxx@yyy.com...
    OK
    
    name                           service                  plan                   bound apps              last operation
    my_activitytracker_svc         accessTrail             free                                            create succeeded
	```
	{: screen}

	




