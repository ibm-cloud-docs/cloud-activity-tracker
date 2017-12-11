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


# 更改套餐
{: #change_plan}

可以在 {{site.data.keyword.Bluemix_notm}} 服务“仪表板”中或通过运行 `cf update-service` 命令来更改 {{site.data.keyword.cloudaccesstraillong}} 服务套餐。您可以随时将套餐升级或降级。
{:shortdesc}

## 通过 UI 更改服务套餐
{: #change_plan_ui}

要在 {{site.data.keyword.Bluemix_notm}} 服务“仪表板”中更改服务套餐，请完成以下步骤：

1. 登录到 {{site.data.keyword.Bluemix_notm}}，然后在 {{site.data.keyword.Bluemix_notm}}“仪表板”中单击 {{site.data.keyword.cloudaccesstraillong_notm}} 服务。 
    
2. 在 {{site.data.keyword.Bluemix_notm}} UI 中，选择**套餐**选项卡。

    这将显示有关当前套餐的信息。
	
3. 选择新套餐以将现有套餐升级或降级。 

4. 单击**保存**。



## 通过 CLI 更改服务套餐
{: #change_plan_cli}

要在 Bluemix 中通过 CLI 更改服务套餐，请完成以下步骤：

1. 登录到 {{site.data.keyword.Bluemix_notm}} 区域、组织和空间。 

    ```
    cf login -a Endpoint
    ```
    {: codeblock}
	
	其中，*Endpoint* 是用于登录到 {{site.data.keyword.Bluemix_notm}} 的 URL。此 URL 对于每个区域各不相同。
	
	<table>
	    <caption>用于访问 {{site.data.keyword.Bluemix_notm}} 的端点的列表</caption>
		<tr>
		  <th>区域</th>
		  <th>URL</th>
		</tr>
		<tr>
		  <td>美国南部</td>
		  <td>api.ng.bluemix.net</td>
		</tr>
		<tr>
		  <td>英国</td>
		  <td>api.eu-gb.bluemix.net</td>
		</tr>
		<tr>
		  <td>德国</td>
		  <td>api.eu-de.bluemix.net</td>
		</tr>
	</table>

    按照指示信息进行操作。输入您的 {{site.data.keyword.Bluemix_notm}} 凭证，然后选择组织和空间。 

    例如，运行以下命令以登录到美国南部区域：
	
	```
	cf login -a api.ng.bluemix.net
	```
	{: codeblock}
	
2. 运行 `cf services` 命令来检查当前套餐，并从空间中可用的服务列表中获取 {{site.data.keyword.cloudaccesstrailshort}} 服务名称。 

    字段 **name** 的值是更改套餐时必须使用的值。 

    例如：
	
	```
	$ cf services
    Getting services in org MyOrg / space dev as xxx@yyy.com...
    OK
    
    name                            service              plan          bound apps      last operation
    Activity Tracker-oj            activityTracker       premium                       create succeeded
    ```
	{: screen}
    
3. 将套餐升级或降级。运行 `cf update-service` 命令。
    
	```
	cf update-service service_name [-p new_plan]
	```
	{: codeblock}
	
	其中
 
	
	* *service_name* 是服务的名称。可以运行 `cf services` 命令来获取值。
	* *new_plan* 是套餐的名称。
	
	下表列出了不同套餐及其支持的值：
	
	<table>
	  <caption>表 1. 套餐列表。</caption>
	  <tr>
	    <th>套餐</th>
	    <th>名称</th>
	  </tr>
	  <tr>
	    <td>Lite</td>
	    <td>lite</td>
	  </tr>
	  <tr>
	    <td>高级</td>
	    <td>premium</td>
	  </tr>
	</table>
	
	例如，要将现有套餐降级为 *Lite* 套餐，请运行以下命令：
	
	```
	cf update-service "Activity Tracker-oj" -p lite
    Updating service instance Activity Tracker-oj as xxx@yyy.com...
    OK
	```
	{: screen}

4. 验证新套餐是否已更改。运行 `cf services` 命令。

    ```
	cf services
    Getting services in org MyOrg / space dev as xxx@yyy.com...
    OK

    name                   service            plan      bound apps   last operation
    Activity Tracker-oj    activityTracker    lite                   update succeeded
	```
	{: screen}






