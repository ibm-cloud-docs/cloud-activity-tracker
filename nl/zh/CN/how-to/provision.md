---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, provision instance

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


# 供应 Activity Tracker
{: #provision}

您可以从 {{site.data.keyword.cloud_notm}} UI 或从命令行供应 {{site.data.keyword.cloudaccesstraillong}} 服务。
{:shortdesc}

不推荐使用 {{site.data.keyword.cloudaccesstrailfull}}。从 2019 年 5 月 9 日开始，无法供应新的 {{site.data.keyword.cloudaccesstrailshort}} 实例。对现有高端套餐实例的支持会持续到 2019 年 9 月 30 日。要继续监视 {{site.data.keyword.cloud_notm}} 帐户的活动，请供应 [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) 的实例。
{: deprecated}

## 通过 UI 供应
{: #provision_ui}

要在 {{site.data.keyword.cloud_notm}} 中供应 {{site.data.keyword.cloudaccesstraillong_notm}} 服务的实例，请完成以下步骤：

1. [登录到 {{site.data.keyword.cloud_notm}} 帐户 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://cloud.ibm.com/login){:new_window}。
    
	使用您的用户标识和密码登录后，{{site.data.keyword.cloud_notm}} UI 会打开。

2. 单击**目录**。这将打开 {{site.data.keyword.cloud_notm}} 上可用的服务的列表。

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
		<td>有效值包括：“美国南部”、“英国”、“德国”和“悉尼”</td>
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

    有关更多信息，请参阅[服务套餐](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-change_plan#change_plan)。
	
7. 单击**创建**以在您登录到的 {{site.data.keyword.cloud_notm}} 空间中供应 {{site.data.keyword.cloudaccesstrailshort}} 服务。
  
 

## 通过 CLI 供应
{: #provision_cli}

要通过命令行在 {{site.data.keyword.cloud_notm}} 中供应 {{site.data.keyword.cloudaccesstrailshort}} 服务的实例，请完成以下步骤：

1. [先决条件] 安装 {{site.data.keyword.cloud_notm}} CLI。

   有关更多信息，请参阅[安装 {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-ibmcloud-cli#ibmcloud-cli)。
   
   如果 CLI 已安装，请继续执行下一步。
    
2. 登录到 {{site.data.keyword.cloud_notm}}。 

    运行 [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) 命令以登录到 {{site.data.keyword.cloud_notm}}，然后运行 [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) 命令以设置要在其中供应 {{site.data.keyword.cloudaccesstrailshort}} 服务的组织和空间。
	
3. 运行 `ibmcloud service create` 命令以供应实例。

    ```
	  ibmcloud service create service_name service_plan service_instance_name
    ```
	  {: codeblock}
	
	  其中
	
	  * service_name 是服务的名称，即 **accessTrail**。

	  * service_plan 是服务套餐名称。有关套餐的列表，请参阅[服务套餐](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-change_plan#change_plan)。

	  * service_instance_name 是要用于所创建的新服务实例的名称。

	  例如，要使用标准套餐创建 {{site.data.keyword.cloudaccesstrailshort}} 服务的实例，请运行以下命令：	
	
	  ```
	  ibmcloud service create accessTrail free my_activitytracker_svc
   ```
	  {: codeblock}
	
4. 验证服务是否已成功创建。运行以下命令：

  ```	
	ibmcloud service list
 ```
	{: codeblock}
	
	运行命令的输出如下所示：
	
	```
        Getting services in org MyOrg / space MySpace as xxx@yyy.com...
    OK
name                           service                  plan                   bound apps              last operation
    my_activitytracker_svc         accessTrail             free                                            create succeeded
	```
	{: screen}

	




