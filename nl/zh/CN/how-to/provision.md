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


# 供应 Activity Tracker 服务
{: #provision}

可以通过 {{site.data.keyword.Bluemix}} UI 或命令行供应 {{site.data.keyword.cloudaccesstraillong}} 服务。
{:shortdesc}


## 通过 UI 供应
{: #ui}

要在 {{site.data.keyword.Bluemix_notm}} 中供应 {{site.data.keyword.cloudaccesstraillong_notm}} 服务的实例，请完成以下步骤：

1. 登录到您的 {{site.data.keyword.Bluemix_notm}} 帐户。

    可在以下地址找到 {{site.data.keyword.Bluemix_notm}}“仪表板”：[http://bluemix.net ![外部链接图标](../../../icons/launch-glyph.svg "外部链接图标")](http://bluemix.net){:new_window}。
    
	使用您的用户标识和密码登录后，{{site.data.keyword.Bluemix_notm}} UI 会打开。

2. 单击**目录**。这将打开 {{site.data.keyword.Bluemix_notm}} 上可用的服务的列表。

3. 选择**安全性**类别以过滤显示的服务列表。

    该服务还在 **DevOps** 类别下提供。

4. 单击 **Activity Tracker** 磁贴。

5. 配置用于定义要供应服务的位置的信息。 

    如下表所示输入数据： 

    <table>
	  <caption>表 1. 供应 {{site.data.keyword.cloudaccesstrailshort}} 服务所必需的字段</caption>
	  <tr>
	    <th>字段</th>
		<th>值</th>
	  </tr>
	  <tr>
	    <td>选择要在其中部署的区域：</td>
		<td>有效值包括：“美国南部”、“英国”和“德国”</td>
	  </tr>
	  <tr>
	    <td>选择组织：</td>
		<td>选择您计划监视其活动的组织。</td>
	  </tr>
	  <tr>
	    <td>选择空间：</td>
		<td>选择所选组织中您计划监视其活动的空间。</td>
	  </tr>
	</table>

6. 选择服务套餐。 

    缺省情况下，已设置**免费**套餐。

    有关更多信息，请参阅[服务套餐](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#plans)。
	
7. 单击**创建**以在您登录到的 {{site.data.keyword.Bluemix_notm}} 空间中供应 {{site.data.keyword.cloudaccesstrailshort}} 服务。
  
 

## 通过 CLI 供应
{: #cli}

要通过命令行在 {{site.data.keyword.Bluemix_notm}} 中供应 {{site.data.keyword.cloudaccesstraillong_notm}} 服务的实例，请完成以下步骤：

1. 安装 Cloud Foundry (CF) CLI。如果 CF CLI 已安装，请继续执行下一步。

   有关更多信息，请参阅[安装 cf CLI ![外部链接图标](../../../icons/launch-glyph.svg "外部链接图标")](http://docs.cloudfoundry.org/cf-cli/install-go-cli.html){: new_window}。 
    
2. 登录到 {{site.data.keyword.Bluemix_notm}} 区域、组织和空间。 

    例如，要登录到美国南部区域，请运行以下命令：

    ```
    cf login -a https://api.ng.bluemix.net
    ```
    {: codeblock}

    按照指示信息进行操作。输入您的 {{site.data.keyword.Bluemix_notm}} 凭证，然后选择组织和空间。
	
3. 运行 `cf create-service` 命令以供应实例。

    ```
	cf create-service service_name service_plan service_instance_name
	```
	{: codeblock}
	
	其中
	
	* service_name 是服务的名称，即 **activityTracker**。
	* service_plan 是服务套餐名称。有关套餐列表，请参阅[服务套餐](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#plans)。
	* service_instance_name 是要用于所创建的新服务实例的名称。
	
	有关该 cf 命令的更多信息，请参阅 [cf create-service](/docs/cli/reference/cfcommands/index.html#cf_create-service)。

	例如，要使用 Lite 套餐创建 {{site.data.keyword.cloudaccesstrailshort}} 服务的实例，请运行以下命令：
	
	```
	cf create-service activityTracker free my_activity_tracker_svc
	```
	{: codeblock}
	
4. 验证服务是否已成功创建。运行以下命令：

    ```	
	cf services
	```
	{: codeblock}
	
	运行命令的输出如下所示：
	
	```
    Getting services in org MyOrg / space MySpace as xxx@yyy.com...
    OK
    
    name                           service                  plan                   bound apps              last operation
    my_activity_tracker_svc        activityTracker          free                                           create succeeded
	```
	{: screen}

	



