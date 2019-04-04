---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, change plan

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



# 變更方案
{: #change_plan}

您可以透過 {{site.data.keyword.cloud_notm}} 使用者介面，或執行 `ibmcloud service update` 指令，來變更 {{site.data.keyword.cloudaccesstraillong}} 服務方案。您可以隨時升級或降低您的方案。
{:shortdesc}

## 透過使用者介面變更服務方案
{: #change_plan_ui}

若要透過 {{site.data.keyword.cloud_notm}} 使用者介面變更服務方案，請完成下列步驟：

1. 登入 {{site.data.keyword.cloud_notm}}，然後從*儀表板* 按一下 {{site.data.keyword.cloudaccesstraillong_notm}} 服務。 
    
2. 選取**方案**標籤。

    畫面上會顯示現行方案的相關資訊。
	
3. 選取新方案以升級或降低您的方案。 

4. 按一下**儲存**。



## 透過 CLI 變更服務方案
{: #change_plan_cli}

若要透過 CLI 變更服務方案，請完成下列步驟：

1. 登入 {{site.data.keyword.cloud_notm}}。 

    執行 [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) 指令以登入 {{site.data.keyword.cloud_notm}}，然後執行 [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) 指令，以設定您要在其中佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務的組織及空間。
	
2. 執行 `ibmcloud service list` 指令來檢查現行方案，並從空間可用的服務清單中取得 {{site.data.keyword.cloudaccesstrailshort}} 服務名稱。 

    **名稱**欄位的值是您必須用來變更方案的值。 

    例如：
	
	```
	$ ibmcloud service list
    Invoking 'cf services'...

    Getting services in org MyOrg / space dev as xxx@ibm.com...
    OK

    name                       service                  plan                 bound apps                               last operation
    Activity Tracker-zt          OK                     accessTrail             premium                                update succeeded
    ```
	{: screen}
    
3. 升級或降低方案。執行 `ibmcloud service update` 指令。
    
	```
	ibmcloud service update service_name [-p new_plan]
	```
	{: codeblock}
	
	其中 
	
	* *service_name* 是服務的名稱。您可以執行 `ibmcloud service list` 指令，以取得值。
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
	    <td>free</td>
	  </tr>
	  <tr>
	    <td>超值</td>
	    <td>premium</td>
	  </tr>
	</table>
	
	例如，若要將您的方案降低為*精簡* 方案，請執行下列指令：
	
	```
	ibmcloud service update "Activity Tracker-zt" -p free
    Updating service instance Activity Tracker-zt as xxx@ibm.com...
    OK
	```
	{: screen}



