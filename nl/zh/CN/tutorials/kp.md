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


# 使用 {{site.data.keyword.cloudaccesstrailshort}} 监视 {{site.data.keyword.keymanagementserviceshort}} 活动
{: #kp}

使用本教程可了解如何使用 {{site.data.keyword.cloudaccesstrailfull}} 服务来监视用户与 {{site.data.keyword.keymanagementserviceshort}} 服务的交互。
{:shortdesc}

本教程的目标如下：

1. 说明如何供应 {{site.data.keyword.cloudaccesstrailshort}} 服务。
2. 说明如何使用云服务来生成由 {{site.data.keyword.cloudaccesstrailshort}} 服务自动收集的活动事件。事件符合 [Cloud Auditing Data Federation (CADF) 标准 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.dmtf.org/sites/default/files/standards/documents/DSP0262_1.0.0.pdf){: new_window}。
3. 说明如何使用预定义的 {{site.data.keyword.cloudaccesstrailshort}} 仪表板来监视服务的云活动。

下图显示用户发起的活动更改服务状态时涉及的不同组件和操作：

![用户发起的活动更改服务状态时涉及的组件和操作](../images/AT_f1.png "用户发起的活动更改服务状态时涉及的组件和操作")



## 开始之前
{: #kp_prereqs}

创建 [{{site.data.keyword.cloud_notm}} 帐户](https://cloud.ibm.com/registration/)。用户标识必须是 {{site.data.keyword.cloud_notm}} 帐户的成员或所有者，并且在您计划使用 {{site.data.keyword.cloudaccesstrailshort}} 服务的空间中具有开发者许可权。


## 步骤 1：供应 Activity Tracker
{: #kp_step1}

供应 {{site.data.keyword.cloudaccesstrailshort}} 服务的区域必须与供应要监视其活动的云服务的区域相同。供应 {{site.data.keyword.cloudaccesstrailshort}} 服务后，将从所选云服务中自动收集事件。 

**注：**本教程说明如何使用 {{site.data.keyword.cloudaccesstrailshort}} 服务来监视用户与美国南部区域云服务 {{site.data.keyword.keymanagementservicelong_notm}} 的交互。因此，您必须在美国南部区域供应 {{site.data.keyword.cloudaccesstrailshort}}。要查看有关服务在哪个区域中可用的信息，请参阅[按区域列出的服务](/docs/resources/services_region.html#services_region)。

要在 {{site.data.keyword.cloud_notm}} 中供应 {{site.data.keyword.cloudaccesstraillong_notm}} 服务的实例，请完成以下步骤：

1. 登录到 {{site.data.keyword.cloud_notm}}。

    可在以下地址找到 {{site.data.keyword.cloud_notm}} 仪表板：[http://cloud.ibm.com ![外部链接图标](../../../icons/launch-glyph.svg "外部链接图标")](http://cloud.ibm.com){:new_window}。
    
	使用您的用户标识和密码登录后，{{site.data.keyword.cloud_notm}} UI 会打开。

2. 单击**目录**。这将打开 {{site.data.keyword.cloud_notm}} 上可用的服务的列表。

3. 选择**安全性和身份**类别以过滤显示的服务列表。

    **注：**该服务还在**开发者工具**类别中提供。

4. 单击 **Activity Tracker** 磁贴。 

5. 配置用于定义要供应服务的位置的信息。 

    如下表所示输入数据： 

    <table>
	  <caption>表 1. 供应 {{site.data.keyword.cloudaccesstrailshort}} 服务所必需的字段</caption>
	  <tr>
	    <th width="50%">字段</th>
		<th width="50%">值</th>
	  </tr>
	  <tr>
	    <td>选择要在其中部署的区域：</td>
		<td>美国南部</td>
	  </tr>
	  <tr>
	    <td>选择组织：</td>
		<td>选择计划用于供应 {{site.data.keyword.cloudaccesstrailshort}} 服务的组织。</td>
	  </tr>
	  <tr>
	    <td>选择空间：</td>
		<td>选择所选组织中您计划供应 {{site.data.keyword.cloudaccesstrailshort}} 服务的空间。</td>
	  </tr>
	</table>

6. 单击**创建**以在您登录到的空间中供应 {{site.data.keyword.cloudaccesstrailshort}} 服务。
   

## 步骤 2：配置云服务  
{: #kp_step2}

此教程说明如何监视 {{site.data.keyword.cloud_notm}} 中 {{site.data.keyword.keymanagementserviceshort}} 服务的 API 活动。

完成以下步骤以在 {{site.data.keyword.cloud_notm}} 中配置 {{site.data.keyword.keymanagementserviceshort}} 服务：

1. 在美国南部区域中供应 {{site.data.keyword.keymanagementserviceshort}} 服务的实例。有关更多信息，请参阅[从 IBM Cloud 控制台供应](/docs/services/key-protect/provision.html#provision)。

2. 针对计划使用密钥的用户定义 {{site.data.keyword.cloud_notm}} 许可权。 

    * 用户需要通过服务角色设置为 *manager* 或 *writer* 的 IAM 策略，才能创建密钥。
	* 用户需要通过服务角色设置为 *manager* 的 IAM 策略，才能删除密钥。
	* 用户需要通过服务角色设置为 *reader* 的 IAM 策略，才能查看密钥。 


## 步骤 3：生成 Activity Tracker 事件
{: #kp_step3}

在此步骤中，使用 {{site.data.keyword.keymanagementserviceshort}} 服务创建安全密钥以生成 {{site.data.keyword.cloudaccesstrailshort}} 事件数据。有关更多信息，请参阅[创建新密钥](/docs/services/key-protect/create-standard-keys.html#create-standard-keys)。

* 创建密钥会生成 {{site.data.keyword.cloudaccesstrailshort}} 事件。
* {{site.data.keyword.cloudaccesstrailshort}} 事件在 {{site.data.keyword.cloudaccesstrailshort}} **帐户域**中提供，此域在生成事件的 {{site.data.keyword.cloud_notm}} 区域中提供。 

## 步骤 4：监视 Activity Tracker 事件
{: #kp_step4}

在此步骤中，通过 {{site.data.keyword.cloud_notm}} UI 验证是否生成了 {{site.data.keyword.cloudaccesstrailshort}} 事件。

要验证是否已创建事件，请完成以下步骤：

1. 授予用户查看帐户事件的许可权。有关更多信息，请参阅[查看帐户事件](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/viewing_events.html#view_acc_events_account_events)和[授予许可权以查看帐户事件](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_acc_events)。

2. 在 {{site.data.keyword.cloud_notm}}“仪表板”中，选择 {{site.data.keyword.cloudaccesstrailshort}} 服务。这将打开该服务仪表板。

3. 将该视图配置为搜索在供应该服务并添加密钥时已生成的 {{site.data.keyword.keymanagementserviceshort}} 事件。

    * 对于*查看日志*字段，选择**帐户日志**。
    * 在*搜索字段*中选择** target.typeURI_str**，在*过滤器*字段中输入 **kms/secrets**。
	
    显示的数据是最近 24 小时可用的 {{site.data.keyword.keymanagementserviceshort}} 事件。 
	


## 后续步骤
{: #kp_next_steps}

接下来，使用 {{site.data.keyword.cloudaccesstrailshort}} 预定义的 Kibana 仪表板来监视和分析事件日志。要启动 Kibana，请参阅[导航至 Kibana 仪表板](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_kibana.html#launch_kibana)。缺省情况下，在 Kibana 中，空间活动日志通过 **ActivityTracker_Space_Dashboard_in_24h** 仪表板显示：

还可以使用 {{site.data.keyword.cloudaccesstrailshort}} CLI 通过命令行来管理事件。有关更多信息，请参阅[查看事件信息](/docs/services/cloud-activity-tracker/how-to/viewing_event_information.html#viewing_event_status)。



