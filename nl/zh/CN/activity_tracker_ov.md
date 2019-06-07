---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, overview

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



# 关于 {{site.data.keyword.cloudaccesstrailshort}}
{: #activity_tracker_ov}

使用 {{site.data.keyword.cloudaccesstrailfull}} 服务可跟踪应用程序与 {{site.data.keyword.cloud_notm}} 服务进行交互的情况。使用 {{site.data.keyword.cloudaccesstrailshort}} 可监视异常活动，以及满足监管审计要求。收集的事件符合 Cloud Auditing Data Federation (CADF) 标准。
{:shortdesc}

不推荐使用 {{site.data.keyword.cloudaccesstrailfull}}。从 2019 年 5 月 9 日开始，无法供应新的 {{site.data.keyword.cloudaccesstrailshort}} 实例。对现有高端套餐实例的支持会持续到 2019 年 9 月 30 日。要继续监视 {{site.data.keyword.cloud_notm}} 帐户的活动，请供应 [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) 的实例。
{: deprecated}

* {{site.data.keyword.cloudaccesstrailshort}} 为云中的 IT 资源提供了高等级的安全管理。
* {{site.data.keyword.cloudaccesstrailshort}} 为管理员提供了在一个位置中捕获、存储、查看、搜索和监视 API 活动的解决方案。
* {{site.data.keyword.cloudaccesstrailshort}} 提供了下载事件以用于生成审计跟踪报告的功能。您可能需要这些报告，以便您的组织符合内部条例和外部行业与国家或地区法规。

符合内部策略和行业法规是任何组织的策略中的关键要求，与应用程序的运行位置（内部部署、混合云或公共云）无关。{{site.data.keyword.cloudaccesstrailshort}} 服务提供了框架和功能，可监视 API 调用并生成证据，证明符合公司政策和特定于行业的市场监管。

在云环境（例如，{{site.data.keyword.cloud_notm}}）中工作时，必须根据内部策略以及基于行业和国家或地区的合规要求，计划用于审计和监视工作负载与数据的云策略。可以使用通过 {{site.data.keyword.cloudaccesstrailshort}} 服务注册的信息来确定安全事件，检测未经授权的访问，以及符合监管和内部审计要求。

例如，可以使用 {{site.data.keyword.cloudaccesstrailshort}} 活动日志来确定以下信息：

* 对云服务发起 API 调用的用户。
* 发起 API 调用的源 IP 地址。
* 发起 API 调用时的时间戳记。
* API 调用的状态。


## 收集事件
{: #activity_tracker_ov_collect}

{{site.data.keyword.cloudaccesstrailshort}} 服务捕获对 {{site.data.keyword.cloud_notm}} 中所选云服务发起的 API 调用和其他操作的相关活动数据。 

* 事件会自动收集。 
* {{site.data.keyword.cloudaccesstrailshort}} 中收集的事件符合 Cloud Auditing Data Federation (CADF) 标准。CADF 标准定义了完整事件模型，包含证明、管理和审计云环境中应用程序安全性所需的信息。
* {{site.data.keyword.cloudaccesstrailshort}} 按域存储和分组事件。每个区域都有一个帐户域，并且每个 Cloud Foundry 空间都有一个空间域。 

CADF 事件模型包含以下组件：

<table>
  <caption>表 1. CADF 事件模型中可用的组件</caption>
  <tr>
    <th>组件</th>
	<th>描述</th>
  </tr>
  <tr>
    <td>操作</td>
	<td>操作是发起者执行、尝试执行或等待完成的行动或活动。</td>
  </tr>
  <tr>
    <td>发起者</td>
	<td>发起者是发起 API 调用并生成 CADF 事件的资源。触发的事件取决于 API 调用请求的操作。</td>
  </tr>
  <tr>
    <td>观察者</td>
	<td>观察者是通过 CADF 事件中可用的信息来创建和存储 CADF 记录的资源。</td>
  </tr>
  <tr>
    <td>结果</td>
	<td>结果是针对目标所执行的操作的状态。</td>
  </tr>
  <tr>
    <td>目标</td>
	<td>目标是对其执行操作、尝试执行操作或待完成操作的资源。</td>
  </tr>
</table>


在 {{site.data.keyword.IBM_notm}} 公共云中使用 {{site.data.keyword.cloudaccesstrailshort}} 日志时，请考虑以下信息：

* 只能存储对 {{site.data.keyword.IBM_notm}} 公共云中所运行资源发起的 API 调用的审计记录。
* 仅 {{site.data.keyword.IBM_notm}} 公共云存储器用于收集事件。
* 信息存储 3 天。在此时间后，将根据先入先出 (FIFO) 方法删除信息。
* {{site.data.keyword.cloudaccesstrailshort}} 服务支持类型为*活动*的 CADF 事件。


## 供应 Activity Tracker
{: #activity_tracker_ov_provision}

要查看通过帐户域提供的事件，您必须在监控 API 活动的区域的 Cloud Foundry 空间中供应 {{site.data.keyword.cloudaccesstrailshort}} 服务。只有**帐户所有者**可以看到帐户事件。

要查看通过空间域提供的事件，您必须在要监视 API 活动的空间中供应 {{site.data.keyword.cloudaccesstrailshort}} 服务。

要了解如何供应 {{site.data.keyword.cloudaccesstrailshort}} 服务，请参阅[供应 {{site.data.keyword.cloudaccesstrailshort}} 服务](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-provision#provision)。



## 分析活动日志
{: #activity_tracker_ov_analyze}

可以通过 {{site.data.keyword.cloud_notm}} 中的 {{site.data.keyword.cloudaccesstrailshort}} UI 或使用开放式源代码工具 Kibana 来分析活动日志。还可以监视特定空间中或帐户级别上可用的事件。

可以通过 {{site.data.keyword.cloud_notm}} 中的 {{site.data.keyword.cloudaccesstrailshort}} UI 来搜索、分析和监视最近 24 小时的活动日志。有关更多信息，请参阅[导航至 {{site.data.keyword.cloudaccesstrailshort}} UI](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-launch_at_ui#launch_at_ui)。

可以使用 {{site.data.keyword.cloudaccesstrailshort}} Kibana 仪表板或创建您自己的定制仪表板，通过 Kibana 搜索、分析和监视最近 3 天的活动日志。* **注：**此功能适用于**高端**套餐用户。

* 有关如何启动 Kibana 的更多信息，请参阅[导航至 Kibana 仪表板](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-launch_kibana#launch_kibana)。 
* 有关可用于在 Kibana 中分析事件的字段的列表，请参阅 [{{site.data.keyword.cloudaccesstrailshort}} 事件字段](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-at_event#at_event)



## 区域
{: #activity_tracker_ov_regions}

{{site.data.keyword.cloudaccesstrailshort}} 服务在以下区域中可用：

* 德国
* 悉尼
* 英国（仅提供轻量套餐）
* 美国南部


## 服务套餐
{: #activity_tracker_ov_plan}

{{site.data.keyword.cloudaccesstrailshort}} 服务提供有多种套餐。

可以通过 {{site.data.keyword.cloud_notm}} UI 或命令行来更改套餐。您可以随时将套餐升级或降级。有关服务套餐升级的更多信息，请参阅[更改套餐](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-change_plan#change_plan)。 

下表概括了可用的套餐：

<table>
    <caption>表 1. 用于事件获取、事件保留时间和导出事件的功能</caption>
      <tr>
        <th>套餐</th>
        <th>事件获取</th>
        <th>事件保留时间</th>
		<th>导出事件</th>
      </tr>
      <tr>
        <td>轻量（缺省）</td>
        <td>否</td>
        <td>最近 3 天</td>
		<td>否</td>
      </tr>
      <tr>
        <td>高端</td>
        <td>是</td>
        <td>可配置的天数。</td>
		<td>是</td>
      </tr>
</table>

<table>
    <caption>表 2. 用于管理和查看事件的功能</caption>
      <tr>
        <th>套餐</th>
		    <th>API</th>
		    <th>CLI</th>
        <th>Kibana</th>
      </tr>
      <tr>
        <td>轻量（缺省）</td>
		    <td>否</td>
		    <td>否</td>
        <td>否</td>
      </tr>
      <tr>
        <td>高端</td>
		    <td>是</td>
		    <td>是</td>
        <td>是</td>
      </tr>
</table>

**注：**事件存储器的每月成本按计费周期内的平均值进行计算。

## 安全性
{: #activity_tracker_ov_security}

使用 {{site.data.keyword.cloudaccesstrailshort}} 服务时，请考虑有关安全性的以下信息：

* 生成 {{site.data.keyword.cloudaccesstrailshort}} 事件的 IBM 服务遵循 {{site.data.keyword.IBM_notm}} 云安全策略。有关更多信息，请参阅 [Trust the security and privacy of IBM Cloud ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/cloud/security){: new_window}。
* {{site.data.keyword.cloudaccesstrailshort}} 服务捕获用户发起的用于更改云服务状态的操作。信息不提供对数据库或应用程序的直接访问。
* 只有授权用户才能查看和监视 {{site.data.keyword.cloudaccesstrailshort}} 事件日志。每个用户通过 {{site.data.keyword.cloud_notm}} 中的用户唯一标识进行确定。
