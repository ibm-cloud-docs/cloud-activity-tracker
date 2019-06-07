---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, IAM

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

# 授予查看事件的许可权
{: #grant_permissions}

在 {{site.data.keyword.cloud}} 中，您可以将 Cloud Foundry 角色和/或 IAM 角色分配给用户。这些角色可定义用户在您使用 {{site.data.keyword.cloudaccesstrailshort}} 服务时可执行的任务。  
{:shortdesc}

不推荐使用 {{site.data.keyword.cloudaccesstrailfull}}。从 2019 年 5 月 9 日开始，无法供应新的 {{site.data.keyword.cloudaccesstrailshort}} 实例。对现有高端套餐实例的支持会持续到 2019 年 9 月 30 日。要继续监视 {{site.data.keyword.cloud_notm}} 帐户的活动，请供应 [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) 的实例。
{: deprecated}

## 授予查看帐户事件的许可权
{: #grant_acc_events}

要允许用户查看区域中的帐户事件，请向用户授予以下许可权：

1. 在供应 {{site.data.keyword.cloudaccesstrailshort}} 的区域中，空间中的 *Developer* 角色。 

    有关更多信息，请参阅[授予 CF 角色](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-grant_permissions#grant_cf_role)。

2. 具有区域中 *viewer* 角色的 {{site.data.keyword.loganalysisshort}} 服务的 IAM 策略。 

    viewer 角色是必需的最低 IAM 角色。 
	
	有关更多信息，请参阅[授予 IAM 许可权](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-grant_permissions#grant_iam_policy)。


## 授予查看空间事件的许可权
{: #grant_space_events}

要允许用户查看区域中的空间事件，请向用户授予以下许可权：

* 在供应 {{site.data.keyword.cloudaccesstrailshort}} 的区域中，空间中的 *Developer* 角色。 

    有关更多信息，请参阅[授予 CF 角色](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-grant_permissions#grant_cf_role)。


## 授予 IAM 许可权
{: #grant_iam_policy}

要授予用户 IAM 角色，请考虑以下信息：

* 您必须有权向帐户中的其他用户分配策略，或者您必须是帐户所有者。如果您不是帐户所有者，那么必须拥有 {{site.data.keyword.loganalysisshort}} 服务的 IAM 策略的**管理员**角色。

* 定义策略时，可以指定区域来定义您授予用户查看帐户域事件的访问权的区域。

要授予用户查看帐户域中事件的许可权，请完成以下步骤：

1. [登录到 {{site.data.keyword.cloud_notm}} 控制台 ![外部链接图标](../../../icons/launch-glyph.svg "外部链接图标")](https://cloud.ibm.com/login){:new_window}。
	
	使用您的用户标识和密码登录后，{{site.data.keyword.cloud_notm}} UI 会打开。

2. 单击菜单栏中的**管理 > 帐户 > 用户**。 

    *用户*窗口会显示当前所选帐户中用户及其电子邮件地址的列表。
	
3. 如果用户是帐户成员，请从列表中选择用户名，或者单击*操作*菜单中的**管理用户**。

    如果用户不是帐户成员，请参阅[邀请用户](/docs/iam?topic=iam-iamuserinv#iamuserinv)。

4. 在**访问策略**部分中，单击**分配访问权**，然后选择**分配对资源的访问权**。

    这将打开*向用户分配资源访问权** 窗口。

5. 输入有关策略的信息。下表列出了定义策略所需的字段： 

    <table>
	  <caption>用于配置 IAM 策略的字段的列表。</caption>
	  <tr>
	    <th>字段</th>
		<th>值</th>
	  </tr>
	  <tr>
	    <td>服务</td>
		<td>*IBM Cloud Log Analysis*</td>
	  </tr>	  
	  <tr>
	    <td>区域</td>
		<td>您可以指定在哪些区域中授予用户处理事件的访问权。选择一个或多个区域，或者选择**所有当前区域**以授予对所有区域的访问权。</td>
	  </tr>
	  <tr>
	    <td>服务实例</td>
		<td>选择*所有服务实例*。</td>
	  </tr>
	  <tr>
	    <td>角色</td>
		<td>选择一个或多个 IAM 角色。<br>有效角色为*管理员*、*操作员*、*编辑者*和*查看者*。</td>
	  </tr>
     </table>
	
6. 单击**分配**。
	
您配置的策略适用于所选区域。 


## 授予 CF 角色
{: #grant_cf_role}

要授予用户 CF 角色，请考虑以下信息：

* 在组织和空间中，您必须有权为用户分配 Cloud Foundry 角色。 

* 只有 **developer** 角色允许用户查看事件。

要授予用户查看空间事件的访问权，请完成以下步骤：

1. [登录到 {{site.data.keyword.cloud_notm}} 控制台 ![外部链接图标](../../../icons/launch-glyph.svg "外部链接图标")](https://cloud.ibm.com/login){:new_window}。
	
	使用您的用户标识和密码登录后，{{site.data.keyword.cloud_notm}} UI 会打开。

2. 单击菜单栏中的**管理 > 帐户 > 用户**。 

    *用户*窗口会显示当前所选帐户中用户及其电子邮件地址的列表。
	
3. 如果用户是帐户成员，请从列表中选择用户名，或者单击*操作*菜单中的**管理用户**。

    如果用户不是帐户成员，请参阅[邀请用户](/docs/iam?topic=iam-iamuserinv#iamuserinv)。

4. 选择 **Cloud Foundry 访问权**。然后选择组织。

    这将列出该组织中可用的空间。

5. 选择一个空间。然后，从菜单操作中，选择**编辑空间角色**。

6. 选择 **Developer**。
	
7. 单击**保存角色**。




