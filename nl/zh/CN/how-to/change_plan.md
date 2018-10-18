---

copyright:
  years: 2016, 2018
lastupdated: "2018-09-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}



# 更改套餐
{: #change_plan}

您可以通过 {{site.data.keyword.Bluemix_notm}} UI 或运行 `ibmcloud service update` 命令来更改 {{site.data.keyword.cloudaccesstraillong}}服务套餐。您可以随时将套餐升级或降级。
{:shortdesc}

## 通过 UI 更改服务套餐
{: #change_plan_ui}

要通过 {{site.data.keyword.Bluemix_notm}} UI 更改服务套餐，请完成以下步骤：

1. 登录到 {{site.data.keyword.Bluemix_notm}}，然后单击*仪表板*中的 {{site.data.keyword.cloudaccesstraillong_notm}} 服务。 
    
2. 选择**套餐**选项卡。

    这将显示有关当前套餐的信息。
	
3. 选择新套餐以将现有套餐升级或降级。 

4. 单击**保存**。



## 通过 CLI 更改服务套餐
{: #change_plan_cli}

要通过 CLI 更改服务套餐，请完成以下步骤：

1. 登录到 {{site.data.keyword.Bluemix_notm}}。 

    运行 [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) 命令，以登录到 {{site.data.keyword.Bluemix_notm}}，然后运行 [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) 命令来设置要在其中供应 {{site.data.keyword.cloudaccesstrailshort}} 服务的组织和空间。
	
2. 运行 `ibmcloud service list` 命令来检查当前套餐，并从空间中可用的服务列表中获取 {{site.data.keyword.cloudaccesstrailshort}} 服务名称。 

    字段 **name** 的值是更改套餐时必须使用的值。 

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
    
3. 将套餐升级或降级。运行 `ibmcloud service update` 命令。
    
	```
	ibmcloud service update service_name [-p new_plan]
	```
	{: codeblock}
	
	其中
 
	
	* *service_name* 是服务的名称。要获取此值，可以运行 `ibmcloud service list` 命令。
	* *new_plan* 是套餐的名称。
	
	下表列出了不同套餐及其支持的值：
	
	<table>
	  <caption>表 1. 套餐列表。</caption>
	  <tr>
	    <th>套餐</th>
	    <th>名称</th>
	  </tr>
	  <tr>
	    <td>轻量</td>
	    <td>free</td>
	  </tr>
	  <tr>
	    <td>高端</td>
	    <td>premium</td>
	  </tr>
	</table>
	
	例如，要将现有套餐降级为*轻量*套餐，请运行以下命令：
	
	```
	ibmcloud service update "Activity Tracker-zt" -p free
    Updating service instance Activity Tracker-zt as xxx@ibm.com...
    OK
	```
	{: screen}



