---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, VSI events, tutorial

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


# 使用 {{site.data.keyword.cloudaccesstrailshort}} 来监视 {{site.data.keyword.BluVirtServers_short}} 和 {{site.data.keyword.baremetal_short}}
{: #vsi}

使用此教程可了解如何在 {{site.data.keyword.cloud_notm}} 帐户中配置用户，以便您可以监视在使用 {{site.data.keyword.BluVirtServers_short}} 和 {{site.data.keyword.baremetal_short}} 时生成的 {{site.data.keyword.cloudaccesstrailshort}} 事件。
{:shortdesc}

{{site.data.keyword.BluVirtServers}} 是可扩展的虚拟服务器。要获取专用的核心和内存分配，需要付费购买。如果您在寻找能在几分钟内完成添加且有权访问映像模板等功能的计算资源，那么这是不错的选择。 
* 有关更多信息，请参阅[{{site.data.keyword.BluVirtServers_short}}](/docs/vsi?topic=virtual-servers-about-virtual-servers#about-virtual-servers)。 
* 有关生成 {{site.data.keyword.cloudaccesstrailshort}} 事件的操作的列表，请参阅 [{{site.data.keyword.BluVirtServers_short}} 生成的事件](/docs/vsi?topic=virtual-servers-at_events#at_events)。

{{site.data.keyword.baremetal_short}} 是单租户物理服务器，通过对硬件资源的低级别访问来为您提供性能和控制。 
* 有关更多信息，请参阅[{{site.data.keyword.baremetal_long}}](/docs/bare-metal?topic=bare-metal-about#about)。
* 有关生成 {{site.data.keyword.cloudaccesstrailshort}} 事件的操作的列表，请参阅 [{{site.data.keyword.baremetal_short}} 生成的事件](/docs/bare-metal?topic=bare-metal-at_events#at_events)。

**要使用户能够生成 {{site.data.keyword.BluVirtServers_short}} 和 {{site.data.keyword.baremetal_short}} {{site.data.keyword.cloudaccesstrailshort}} 事件，该用户必须有权访问 IBM Cloud 控制台中的基础架构资源。**
{: tip}

## 步骤 1. 将 SoftLayer 帐户链接到 {{site.data.keyword.cloud_notm}} 帐户
{: #vsi_step1}

** 要生成 {{site.data.keyword.cloudaccesstrailshort}} 事件，必须将 SoftLayer 帐户链接到 {{site.data.keyword.cloud_notm}} 帐户。有关更多信息，请参阅[切换到 IBM 标识和链接帐户](/docs/account?topic=account-unifyingaccounts#link_accounts)。

将 SoftLayer 帐户链接到 {{site.data.keyword.cloud_notm}} 帐户时，请考虑以下信息：
* 所有新帐户都将自动接收 IBM 标识，并且支持现有 SoftLayer 帐户（SAML 联合帐户除外）切换到 IBM 标识认证。

* 计划链接到 {{site.data.keyword.cloud_notm}} 帐户的每个 SoftLayer 帐户都必须由具有唯一电子邮件地址的唯一 IBM 标识拥有。
* 要从现有 SoftLayer 帐户切换到 IBM 标识，请创建 IBM 标识，然后使用注册代码进行确认。
* 帐户切换到 IBM 标识帐户后，您可以链接 SoftLayer 帐户和 {{site.data.keyword.cloud_notm}} 帐户，以使用组合基础架构即服务 (IaaS) 和平台即服务 (PaaS) 资源。 

要链接帐户，请完成以下步骤：
1. [请求 IBM 标识和注册代码](/docs/account?topic=account-unifyingaccounts#reqIBMidandregcode)
2. [使用注册代码来确认 IBM 标识](/docs/account?topic=account-unifyingaccounts#confIBMiduseregcode)
3. [链接 IBM 标识帐户](/docs/account?topic=account-unifyingaccounts#link_user_account)


## 步骤 2. 为用户授予基础架构许可权
{: #vsi_step2}

**注：**如果通过 *{{site.data.keyword.cloud_notm}} 基础架构门户网站*授予许可权，那么用户无权访问 *{{site.data.keyword.cloud_notm}} 基础架构*仪表板来管理设备，并且 {{site.data.keyword.cloudaccesstrailshort}} 事件也不会生成。**您必须通过 {{site.data.keyword.cloud_notm}} 帐户来为用户授予基础架构许可权以管理设备。这些操作会生成 {{site.data.keyword.cloudaccesstrailshort}} 事件。**
{: tip}

 要为用户授予基础架构许可权，请完成以下步骤：

1. [登录到 {{site.data.keyword.cloud_notm}} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://cloud.ibm.com/login){:new_window}。
    
	使用您的用户标识和密码登录后，{{site.data.keyword.cloud_notm}} UI 会打开。

2. 在菜单栏中，单击**管理** &gt; **帐户**，然后选择**用户**。 

3. 选择要为其授予使用设备的许可权的用户。

4. 选择**分配访问权**。

5. 选择**分配对 SoftLayer 帐户的访问权**。{{site.data.keyword.cloud_notm}} 基础架构门户网站将在 {{site.data.keyword.cloud_notm}} 的上下文中打开。

6. 设置要授予用户以管理设备的许可权。选择**门户网站许可权**。然后在**设备**部分中，为用户授予管理设备所需的许可权。例如，您可以更改`查看虚拟服务器详细信息`、`重新引导服务器并查看 IPMI 系统信息`、`升级服务器`或`发出操作系统重装并启动急救内核`的许可权。

7. 保存门户网站许可权。当选择**设备访问权**时，系统会提示您保存更改。单击**保存**。

8. 设置用户可以管理的设备。在**设备访问权**部分中，选择物理设备。然后，单击**更新设备访问权**。






