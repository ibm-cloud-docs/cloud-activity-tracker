---

copyright:
  years: 2016, 2017
lastupdated: "2017-09-17"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 入门教程
{: #getting-started-with-cla}

{{site.data.keyword.cloudaccesstrailfull}} 服务会记录用户发起的用于在 {{site.data.keyword.IBM}} 云中更改服务状态的活动。使用本教程可了解如何使用 {{site.data.keyword.cloudaccesstrailfull}} 服务来监视用户与云服务的交互。
{:shortdesc}

本入门教程的目标如下：

1. 说明如何供应 {{site.data.keyword.cloudaccesstrailshort}} 服务。
2. 说明如何使用云服务来生成由 {{site.data.keyword.cloudaccesstrailshort}} 服务自动收集的活动事件。事件符合 Cloud Auditing Data Federation (CADF) 标准。
3. 说明如何使用预定义的 {{site.data.keyword.cloudaccesstrailshort}} 仪表板来监视服务的云活动。

下图显示用户发起的活动更改服务状态时涉及的不同组件和操作：

![用户发起的活动更改服务状态时涉及的组件和操作](images/AT_f1.png "用户发起的活动更改服务状态时涉及的组件和操作")



## 开始之前
{: #prereqs}

创建 [{{site.data.keyword.Bluemix_notm}} 帐户](https://console.bluemix.net/registration/)。用户标识必须是 {{site.data.keyword.Bluemix_notm}} 帐户的成员或所有者，并且在您计划使用 {{site.data.keyword.cloudaccesstrailshort}} 服务的空间中具有开发者许可权。


## 步骤 1：供应 Activity Tracker
{: #step1}

必须在供应要监视其活动的云服务所在的区域和空间中供应 {{site.data.keyword.cloudaccesstrailshort}} 服务。供应 {{site.data.keyword.cloudaccesstrailshort}} 服务后，将从该空间中供应的所选云服务中自动收集事件。有关可通过 {{site.data.keyword.cloudaccesstrailshort}} 监视其活动的服务的列表，请参阅[支持的云服务](/docs/services/cloud-activity-tracker/cloud_services.html#cloud_services)。

**注：**本教程说明如何使用 {{site.data.keyword.cloudaccesstrailshort}} 服务来监视用户与云服务 {{site.data.keyword.keymanagementservicelong_notm}} 的交互。{{site.data.keyword.keymanagementserviceshort}} 服务在美国南部可用。因此，您必须在美国南部区域中 {{site.data.keyword.keymanagementserviceshort}} 服务可用的空间中供应 {{site.data.keyword.cloudaccesstrailshort}}。要查看有关服务在哪个区域中可用的信息，请参阅[按区域列出的服务](/docs/services/services_region.html#services_region)。

要在 {{site.data.keyword.Bluemix_notm}} 中供应 {{site.data.keyword.cloudaccesstraillong_notm}} 服务的实例，请完成以下步骤：

1. 登录到您的 {{site.data.keyword.Bluemix_notm}} 帐户。

    可在以下地址找到 {{site.data.keyword.Bluemix_notm}}“仪表板”：[http://bluemix.net ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://bluemix.net){:new_window}。
    
	使用您的用户标识和密码登录后，{{site.data.keyword.Bluemix_notm}} UI 会打开。

2. 单击**目录**。这将打开 {{site.data.keyword.Bluemix_notm}} 上可用的服务的列表。

3. 选择**安全性**类别以过滤显示的服务列表。

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
		<td>选择您计划监视其活动的组织。</td>
	  </tr>
	  <tr>
	    <td>选择空间：</td>
		<td>选择所选组织中您计划监视其活动的空间。</td>
	  </tr>
	</table>

6. 单击**创建**以在您登录到的 {{site.data.keyword.Bluemix_notm}} 空间中供应 {{site.data.keyword.cloudaccesstrailshort}} 服务。
   

## 步骤 2：供应云服务 
{: #step2}
	
要在 {{site.data.keyword.Bluemix_notm}} 美国南部区域中供应 {{site.data.keyword.keymanagementserviceshort}} 服务的实例，请完成以下步骤：

1. 登录到您的 {{site.data.keyword.Bluemix_notm}} 帐户。

    可在以下地址找到 {{site.data.keyword.Bluemix_notm}}“仪表板”：[http://bluemix.net ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://bluemix.net){:new_window}。
	
	使用您的用户标识和密码登录后，{{site.data.keyword.Bluemix_notm}} UI 会打开。

2. 单击**目录**。这将打开 {{site.data.keyword.Bluemix_notm}} 上可用的服务的列表。

    选择**安全性**类别以过滤显示的服务列表。

3. 选择 **Key Protect** 磁贴。

4. 配置用于定义要供应服务的位置的信息。 

    如下表所示输入数据： 

    <table>
	  <caption>表 2. 供应 {{site.data.keyword.keymanagementserviceshort}} 服务所必需的字段</caption>
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
		<td>选择已选中用于供应 {{site.data.keyword.cloudaccesstrailshort}} 服务的组织。</td>
	  </tr>
	  <tr>
	    <td>选择空间：</td>
		<td>选择已选中用于供应 {{site.data.keyword.cloudaccesstrailshort}} 服务的空间。</td>
	  </tr>
	</table>

5. 单击**创建**以在您登录到的 {{site.data.keyword.Bluemix_notm}} 空间中供应 {{site.data.keyword.keymanagementserviceshort}} 服务。


## 步骤 3：生成 Activity Tracker 事件
{: # step3}

在此步骤中，使用 {{site.data.keyword.keymanagementserviceshort}} 服务创建安全密钥以生成 {{site.data.keyword.cloudaccesstrailshort}} 事件数据。 

要生成 {{site.data.keyword.cloudaccesstrailshort}} 事件，请完成以下步骤：

1. 在 {{site.data.keyword.Bluemix_notm}}“仪表板”中，选择 **Key Protect** 服务。这将打开 {{site.data.keyword.keymanagementserviceshort}} 仪表板。然后，选择**管理**选项卡。

2. 单击**添加密钥**。这将打开一个新窗口。

3. 选择**生成密钥**，然后完成以下步骤：

    * 输入密钥的名称，例如 *MyFirstKey*。

    * 为密钥选择算法。

    * 单击**添加密钥**。 
	
创建密钥会生成 {{site.data.keyword.cloudaccesstrailshort}} 事件。

## 步骤 4：监视 Activity Tracker 事件
{: #step4}

在此步骤中，通过 {{site.data.keyword.Bluemix_notm}} UI 验证是否生成了 {{site.data.keyword.cloudaccesstrailshort}} 事件。

要验证是否已创建事件，请完成以下步骤：

1. 在 {{site.data.keyword.Bluemix_notm}}“仪表板”中，选择 {{site.data.keyword.cloudaccesstrailshort}} 服务。这将打开该服务仪表板。

2. 将该视图配置为搜索在供应该服务并添加密钥时已生成的 {{site.data.keyword.keymanagementserviceshort}} 事件。

    * 对于*查看日志*字段，选择**空间日志**。
    * 对于*搜索字段*字段，选择 **target.name**。
    * 在*过滤器*字段中，输入 **ibm-key-protect**。
	
    显示的数据是最近 24 小时可用的 {{site.data.keyword.keymanagementserviceshort}} 事件。 
	
	![事件的 UI 视图](images/bmx_ui_space_view.png "事件的 UI 视图")


## 后续步骤
{: #next_steps}

接下来，使用 {{site.data.keyword.cloudaccesstrailshort}} 预定义的 Kibana 仪表板来监视和分析事件日志。要启动 Kibana，请参阅[导航至 Kibana 仪表板](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_kibana.html#launch_kibana)。 

缺省情况下，在 Kibana 中，空间活动日志通过 **ActivityTracker_Space_Search_in_24h** 仪表板显示：

![事件的 Kibana 视图](images/kibana_space_view.png "事件的 Kibana 视图")

还可以使用 {{site.data.keyword.cloudaccesstrailshort}} CLI 通过命令行来管理事件。有关更多信息，请参阅[查看事件信息](/docs/services/cloud-activity-tracker/how-to/manage-events-cli/viewing_event_information.html#viewing_event_status)。

                                                                                                                      

