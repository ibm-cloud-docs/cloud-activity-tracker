---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, cloud services

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



# 云服务
{: #cloud_services}

使用 {{site.data.keyword.cloudaccesstraillong}} 服务可监视用户发起的用于更改 {{site.data.keyword.IBM_notm}} 云中以下任一服务状态的活动：
{:shortdesc}

**注：**要获取有关服务在 {{site.data.keyword.cloud_notm}} 中的哪些区域可用的信息，请参阅[按区域列出的服务](/docs/resources?topic=resources-services_region#services_region)。


## 计算基础架构服务
{: #infrastructure}

**注：**要使用户能够生成 {{site.data.keyword.BluVirtServers_short}} 和 {{site.data.keyword.baremetal_short}} {{site.data.keyword.cloudaccesstrailshort}} 事件，该用户必须有权访问 IBM Cloud 控制台中的基础架构资源。有关更多信息，请参阅[使用 {{site.data.keyword.cloudaccesstrailshort}} 来监视 {{site.data.keyword.BluVirtServers_short}} 和 {{site.data.keyword.baremetal_short}} 活动](/docs/services/cloud-activity-tracker/tutorials?topic=cloud-activity-tracker-vsi#vsi)。

下表列出了将事件发送到 {{site.data.keyword.cloudaccesstrailshort}} 的基础架构服务：

|服务|描述|{{site.data.keyword.cloudaccesstrailshort}} 事件|
|-------------|-------------|-------------|
| [{{site.data.keyword.BluVirtServers_short}} ](/docs/vsi?topic=virtual-servers-about-virtual-servers#about-virtual-servers)|{{site.data.keyword.BluVirtServers}} 是可扩展的虚拟服务器。要获取专用的核心和内存分配，需要付费购买。如果您在寻找能在几分钟内完成添加且有权访问映像模板等功能的计算资源，那么这是不错的选择。| [{{site.data.keyword.BluVirtServers_short}} 生成的事件](/docs/vsi?topic=virtual-servers-at_events#at_events) |  
| [{{site.data.keyword.baremetal_long}} ](/docs/bare-metal?topic=bare-metal-about#about) | {{site.data.keyword.baremetal_short}} 是单租户物理服务器，通过对硬件资源的低级别访问来为您提供性能和控制。| [{{site.data.keyword.baremetal_short}} 生成的事件](/docs/bare-metal?topic=bare-metal-at_events#at_events) | 
{: caption="将事件发送到 {{site.data.keyword.cloudaccesstrailshort}} 的基础架构服务的列表" caption-side="top"} 




## 计算无服务器服务
{: #serverless}

下表列出了将事件发送到 {{site.data.keyword.cloudaccesstrailshort}} 的无服务器计算服务：

|服务|描述|{{site.data.keyword.cloudaccesstrailshort}} 事件|
|-------------|-------------|-------------|
| [{{site.data.keyword.openwhisk_short}}](/docs/openwhisk?topic=cloud-functions-index#index) | {{site.data.keyword.openwhisk_short}} 是一种基于 Apache OpenWhisk 的多语言功能即服务 (FaaaS) 编程平台，可用于编写轻量级`代码（称为操作）`。| [{{site.data.keyword.openwhisk_short}} 生成的事件](/docs/openwhisk?topic=cloud-functions-activity_tracker#activity_tracker) |
{: caption="将事件发送到 {{site.data.keyword.cloudaccesstrailshort}} 的无服务器计算服务的列表" caption-side="top"} 



## 平台容器服务
{: #ikcs}

{{site.data.keyword.containershort_notm}} 会生成两种类型的 {{site.data.keyword.cloudaccesstrailshort}} 事件：

* **集群管理事件**
    
    * 这些事件会自动生成。
    * 这些事件会自动转发到 {{site.data.keyword.cloudaccesstrailshort}}。
    * 您可以通过 {{site.data.keyword.cloudaccesstrailshort}} **帐户域**来查看这些事件。 

* **Kubernetes API 服务器审计事件**

    * 这些事件会自动生成。
    * 您必须配置集群，才能将这些事件转发到 {{site.data.keyword.cloudaccesstrailshort}} 服务。
    * 您可以配置集群，以便将事件发送到 {{site.data.keyword.cloudaccesstrailshort}} **帐户域**或**空间域**。有关更多信息，请参阅[发送审计日志](/docs/containers?topic=containers-health#api_forward)。

下表列出了将事件发送到 {{site.data.keyword.cloudaccesstrailshort}} 的容器平台服务：

|服务|描述|{{site.data.keyword.cloudaccesstrailshort}} 事件|
|-------------|-------------|-------------|
|[{{site.data.keyword.containerlong_notm}}：集群管理事件](/docs/containers?topic=containers-container_index#container_index)|这些事件会报告集群创建、删除或更新等操作。|[集群管理事件](/docs/containers?topic=containers-at_events#cluster-events)|  
|[{{site.data.keyword.containerlong_notm}}：API 服务器审计事件](/docs/containers?topic=containers-container_index#container_index)|Kubernetes API 服务器审计事件会提供有关影响集群的一系列活动的时间顺序信息。每个操作都会生成一个事件|[Kubernetes API 服务器审计事件](/docs/containers?topic=containers-at_events#kube-events)|
| [{{site.data.keyword.registrylong_notm}}](/docs/services/Registry?topic=registry-registry_overview#registry_overview) |您可以使用 {{site.data.keyword.registrylong_notm}} 服务在高度可用且可扩展的体系结构中存储和访问专用 Docker 映像。| [与 {{site.data.keyword.registrylong_notm}} 交互时生成的事件](/docs/services/Registry?topic=registry-at_events#at_events) | 
{: caption="容器事件" caption-side="top"} 



## 平台 Cloud Foundry 应用程序
{: #platform_cfapps}

由 Cloud Foundry 应用程序发送到 {{site.data.keyword.cloudaccesstrailshort}} 的事件会列示在 `GET /v2/events` 的响应区域中（位于主体部分之下）。*类型*字段会列出生成事件的所有操作。有关更多信息，请参阅 [Events API ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://apidocs.cloudfoundry.org/270/events/list_all_events.html){:new_window}。


## 平台核心集成服务
{: #platform_core_integrated}

核心平台服务会生成 {{site.data.keyword.cloudaccesstrailshort}} 事件。您可以通过 {{site.data.keyword.cloudaccesstrailshort}} **帐户域**来查看这些事件。

下表列出了将事件发送到 {{site.data.keyword.cloudaccesstrailshort}} 的核心平台服务：

|服务|描述|{{site.data.keyword.cloudaccesstrailshort}} 事件|
|-------------|-------------|-------------|
|[供应和管理 {{site.data.keyword.iamshort}} (IAM) 所管理的资源的目录服务](/docs/overview?topic=overview-ui#catalogcreate)|您可以供应服务实例，重命名服务实例，更改服务实例的套餐以及除去服务实例。| [与目录服务交互时生成的事件](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_rc#at_events_rc) |  
|[供应和管理绑定到 Cloud Foundry 空间的目录服务](/docs/overview?topic=overview-ui#catalogcreate)|您可以供应服务实例，重命名服务实例，更改服务实例的套餐以及除去服务实例。</br>这些事件是针对 CF 空间中供应的服务所生成的。| [与目录服务交互时生成的事件](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-cf#cf_catalog) |  
|[管理帐户](/docs/account?topic=account-accounts#accounts)|您可以通过使用现有 IBM 标识、创建新 IBM 标识或使用联合标识来注册 {{site.data.keyword.IBM_notm}} 帐户。| [管理帐户时生成的事件](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_acc_mgt#at_events_acc_mgt_account) |
|[管理用户](/docs/iam?topic=iam-iamuserinv#iamusermanage)|您可以查看和管理自己所拥有或管理的帐户或组织中的用户。| [管理用户时生成的事件](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_acc_mgt#at_events_acc_mgt_users) |
|[管理组织](/docs/account?topic=account-orgsspacesusers#orgsspacesusers)|如果您是帐户所有者，那么可以向帐户中添加组织，还可以管理组织。| [管理组织时生成的事件](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_acc_mgt#at_events_acc_mgt_org) |
{: caption="核心平台操作的列表" caption-side="top"} 


## 平台数据库服务
{: #database}

下表列出了将事件发送到 {{site.data.keyword.cloudaccesstrailshort}} 的数据库服务：

|服务|描述|{{site.data.keyword.cloudaccesstrailshort}} 事件|
|-------------|-------------|----------------------------------------------------|
| [{{site.data.keyword.databases-for-postgresql_full_notm}}](/docs/services/databases-for-postgresql?topic=databases-for-postgresql-about#about) | {{site.data.keyword.databases-for-postgresql_full_notm}} 是受管的 PostgreSQL 服务，该服务在 {{site.data.keyword.cloud_notm}} 中托管，并与其他 {{site.data.keyword.cloud_notm}} 服务集成。| [{{site.data.keyword.databases-for-postgresql_full_notm}} 生成的事件](/docs/services/databases-for-postgresql?topic=databases-for-postgresql-activity-tracker#activity-tracker) |
| [{{site.data.keyword.databases-for-redis_full_notm}}](/docs/services/databases-for-redis?topic=databases-for-redis-about#about-databases-for-redis) | {{site.data.keyword.databases-for-redis_full_notm}} 是受管的 Redis 服务，该服务在 {{site.data.keyword.cloud_notm}} 中托管，并与其他 {{site.data.keyword.cloud_notm}} 服务集成。| [{{site.data.keyword.databases-for-redis_full_notm}} 生成的事件](/docs/services/databases-for-redis?topic=databases-for-redis-activity-tracker-integration#activity-tracker-integration) |
| [{{site.data.keyword.sqlquery_short}}](/docs/services/sql-query?topic=sql-query-overview#overview) |您可以使用 {{site.data.keyword.sqlquery_short}} 服务来运行 SQL 查询（即 SELECT 语句），以分析、变换或清除矩形数据。| [{{site.data.keyword.sqlquery_short}} 生成的事件](/docs/services/sql-query?topic=sql-query-activitytracker#activity-tracker-events) |  
| [{{site.data.keyword.databases-for-etcd_full_notm}}](/docs/services/databases-for-etcd?topic=databases-for-etcd-about#about-databases-for-etcd) | {{site.data.keyword.databases-for-etcd_full_notm}} 是受管的 etcd 服务，该服务在 {{site.data.keyword.cloud_notm}} 中托管，并与其他 {{site.data.keyword.cloud_notm}} 服务集成。| [{{site.data.keyword.databases-for-etcd_full_notm}} 生成的事件](/docs/services/databases-for-etcd?topic=databases-for-etcd-activity-tracker#activity-tracker-integration) |
| [{{site.data.keyword.databases-for-elasticsearch_full_notm}}](/docs/services/databases-for-elasticsearch?topic=databases-for-elasticsearch-about#about-databases-for-elasticsearch) | {{site.data.keyword.databases-for-elasticsearch_full_notm}} 是受管的 Elasticsearch 服务，该服务在 {{site.data.keyword.cloud_notm}} 中托管，并与其他 {{site.data.keyword.cloud_notm}} 服务集成。| [{{site.data.keyword.databases-for-elasticsearch_full_notm}} 生成的事件](/docs/services/databases-for-elasticsearch?topic=databases-for-elasticsearch-activity-tracker#activity-tracker-integration) |
| [{{site.data.keyword.messages-for-rabbitmq_full_notm}}](/docs/services/messages-for-rabbitmq?topic=messages-for-rabbitmq-about#about-messages-for-rabbitmq)  | {{site.data.keyword.messages-for-rabbitmq_full_notm}} 是受管的 RabbitMQ 服务，该服务在 {{site.data.keyword.cloud_notm}} 中托管，并与其他 {{site.data.keyword.cloud_notm}} 服务集成。| [{{site.data.keyword.messages-for-rabbitmq_full_notm}} 生成的事件](/docs/services/messages-for-rabbitmq?topic=messages-for-rabbitmq-activity-tracker#activity-tracker-integration) |
{: caption="将事件发送到 {{site.data.keyword.cloudaccesstrailshort}} 的数据库服务的列表" caption-side="top"} 




## 平台开发者工具
{: #devops}

下表列出了将事件发送到 {{site.data.keyword.cloudaccesstrailshort}} 的 DevOps 服务：

|服务|描述|{{site.data.keyword.cloudaccesstrailshort}} 事件|
|-------------|-------------|-------------|
| [{{site.data.keyword.DRA_short}}](/docs/services/DevOpsInsights?topic=DevOpsInsights-insights_about#insights_about) | {{site.data.keyword.DRA_short}} 是 {{site.data.keyword.cloud_notm}} 开放工具链目录中的一个集成。| [{{site.data.keyword.DRA_short}} 生成的事件](/docs/services/DevOpsInsights?topic=DevOpsInsights-at_events#at_events) |
| [{{site.data.keyword.contdelivery_short}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-cd_overview#cd_overview) |通过 {{site.data.keyword.contdelivery_short}}，您可以使用 DevOps 实践和业界领先的工具来构建、测试和交付应用程序。| [{{site.data.keyword.contdelivery_short}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-at_events#at_events) 生成的事件 |
| [{{site.data.keyword.GlobalizationPipeline_short}}](/docs/services/GlobalizationPipeline?topic=GlobalizationPipeline-globalizationpipeline#globalizationpipeline) |支持应用程序开发者快速将翻译的应用程序发布到全球客户。| [{{site.data.keyword.GlobalizationPipeline_short}} 生成的事件](/docs/services/GlobalizationPipeline?topic=GlobalizationPipeline-gpat_events#gpat_events)|
{: caption="将事件发送到 {{site.data.keyword.cloudaccesstrailshort}} 的开发者工具的列表" caption-side="top"} 



## 平台集成的开发者服务
{: #integrated_dev_svcs}

下表列出了可用于开发应用程序和将事件发送到 {{site.data.keyword.cloudaccesstrailshort}} 的云服务：

|服务|描述|{{site.data.keyword.cloudaccesstrailshort}} 事件|
|-------------|-------------|-------------|
| [{{site.data.keyword.dev_console}}](/docs/apps?topic=creating-apps-tutorial-getting-started#create) |在 {{site.data.keyword.cloud_notm}} 中，您可以构建企业级移动和 Web 应用程序，还可以利用由 {{site.data.keyword.cloud_notm}} 托管的云扩展。使用 {{site.data.keyword.cloud_notm}} 控制台和命令行工具，可构建、运行和部署应用程序。您可以使用入门模板工具包通过 {{site.data.keyword.dev_console}} 来创建应用程序。| [{{site.data.keyword.dev_console}} 生成的事件](/docs/apps?topic=creating-apps-at_events#at_events) |
| [{{site.data.keyword.mobilepushshort}}](/docs/services/mobilepush?topic=mobile-pushnotification-overview-push#overview-push)|您可以使用 {{site.data.keyword.mobilepushshort}} 服务向移动设备和浏览器发送通知。通知可以定向发送到所有应用程序用户，也可以通过添加标记定向发送到一组特定的用户和设备。每向服务提交一条消息，目标受众就会收到一个通知。| [{{site.data.keyword.mobilepushshort}} 生成的事件](/docs/services/mobilepush?topic=mobile-pushnotification-push_activity_tracker#push_activity_tracker) |  
{: caption="将事件发送到 {{site.data.keyword.cloudaccesstrailshort}} 的 Web 和移动云服务的列表" caption-side="top"} 



## 平台集成的安全服务
{: #platform_integrated_security}

集成的安全服务会生成 {{site.data.keyword.cloudaccesstrailshort}} 事件。您可以通过 {{site.data.keyword.cloudaccesstrailshort}} **帐户域**来查看这些事件。


下表列出了将事件发送到 {{site.data.keyword.cloudaccesstrailshort}} 的核心安全平台服务：

|服务|描述|{{site.data.keyword.cloudaccesstrailshort}} 事件|
|-------------|-------------|-------------|
|[登录到 {{site.data.keyword.cloud_notm}}](/docs/iam?topic=iam-features#features)|您可以使用密码、API 密钥、授权代码或通行码来登录到 {{site.data.keyword.cloud_notm}}。如果您是联合用户，那么可以使用一次性密码或 API 密钥从命令行界面 (CLI) 进行登录。| [用户或应用程序登录到 {{site.data.keyword.cloud_notm}} 时生成的事件](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_login) |
|[管理帐户用户的 Cloud Foundry 访问权](/docs/iam?topic=iam-mngcf#mngcf)|您可以授予、撤销和更新帐户中用户的 Cloud Foundry (CF) 许可权。| [管理帐户中的 CF 角色时生成的事件](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-cf#cf_cfroles) |
|[{{site.data.keyword.iamlong}} (IAM)](/docs/iam?topic=iam-userroles#userroles)|您可以使用 IAM 来管理 {{site.data.keyword.cloud_notm}} 平台和基础架构服务中的用户和角色。| [管理 IAM 策略时生成的事件](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_policies) |
|[管理平台 API 密钥](/docs/iam?topic=iam-manapikey#platform-api-keys)|您可以在 {{site.data.keyword.IBM_notm}} Cloud 中定义与用户或服务标识相关联的平台 API 密钥。| [管理平台 API 密钥时生成的事件](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_apikeys) |
|[管理服务标识](/docs/iam?topic=iam-serviceids#serviceids)|在 {{site.data.keyword.IBM_notm}} Cloud 中，您可以在帐户级别定义服务标识。| [管理服务标识时生成的事件](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_serviceids) |
|[管理访问组](/docs/iam?topic=iam-groups#groups)|您可以定义访问组，以便将一组用户和服务标识组织到单个实体中，从而轻松地分配许可权。| [管理访问组时生成的事件](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_access) |
{: caption="核心安全平台服务的列表" caption-side="top"} 


## 平台集成服务
{: #integration}

下表列出了将事件发送到 {{site.data.keyword.cloudaccesstrailshort}} 的集成服务：

|服务|描述|{{site.data.keyword.cloudaccesstrailshort}} 事件|
|-------------|-------------|-------------|
| [{{site.data.keyword.messagehub}}](/docs/services/EventStreams?topic=eventstreams-about#about)|{{site.data.keyword.messagehub}} 是使用 Apache Kafka 构建的高吞吐量消息传递总线。它已针对将事件获取到 {{site.data.keyword.IBM_notm}} 中以及在服务和应用程序之间进行事件流分发进行了优化。| [{{site.data.keyword.messagehub}} 生成的事件](/docs/services/EventStreams?topic=eventstreams-at_events#at_events) |  
{: caption="将事件发送到 {{site.data.keyword.cloudaccesstrailshort}} 的集成云服务的列表" caption-side="top"} 



## 平台网络服务
{: #network}

下表列出了将事件发送到 {{site.data.keyword.cloudaccesstrailshort}} 的网络云服务：

|服务|描述|{{site.data.keyword.cloudaccesstrailshort}} 事件|
|-------------|-------------|-------------|
|[IBM Cloud Internet Services (CIS)](/docs/infrastructure/cis?topic=cis-about-ibm-cloud-internet-services-cis-#about-ibm-cloud-internet-services-cis-)|IBM Cloud Internet Services (CIS) 提供了一个快速、高性能、可靠且安全的因特网服务。|[IBM Cloud Internet Services 生成的事件](/docs/infrastructure/cis?topic=cis-at_events#at_events)|  
{: caption="将事件发送到 {{site.data.keyword.cloudaccesstrailshort}} 的网络云服务的列表" caption-side="top"} 



## 平台安全服务
{: #security}

下表列出了将事件发送到 {{site.data.keyword.cloudaccesstrailshort}} 的安全云服务：


|服务|描述|{{site.data.keyword.cloudaccesstrailshort}} 事件|
|-------------|-------------|-------------|
| [{{site.data.keyword.cloudaccesstraillong_notm}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov)|您可以使用 {{site.data.keyword.cloudaccesstrailshort}} 服务来监视 {{site.data.keyword.cloudaccesstraillong_notm}}。| [{{site.data.keyword.cloudaccesstraillong_notm}} 服务生成的事件](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-downloading_events#events) |  
| [{{site.data.keyword.appid_full_notm}}](/docs/services/appid?topic=appid-about#about) |您可以使用 {{site.data.keyword.appid_short}} 向移动和 Web 应用程序添加身份验证，以保护后端资源。| [{{site.data.keyword.appid_short}} 服务生成的事件](/docs/services/appid?topic=appid-at-events#at-events) |
| [{{site.data.keyword.cloudcerts_full_notm}}](/docs/services/certificate-manager?topic=certificate-manager-about-certificate-manager#about-certificate-manager) |您可以使用 {{site.data.keyword.cloudcerts_short}} 来管理基于 {{site.data.keyword.cloud_notm}} 的应用程序和服务的 SSL 证书。| [{{site.data.keyword.cloudcerts_short}} 服务生成的事件](/docs/services/certificate-manager?topic=certificate-manager-at_events#at_events) |
| [{{site.data.keyword.keymanagementservicelong}}](/docs/services/key-protect?topic=key-protect-getting-started-tutorial#getting-started-with-key-protect) |您可以使用 {{site.data.keyword.keymanagementserviceshort}} 服务来为 {{site.data.keyword.cloud_notm}} 中的应用程序供应加密密钥。| [{{site.data.keyword.keymanagementserviceshort}} 服务生成的事件](/docs/services/key-protect?topic=key-protect-at-events#at-events) |
| [{{site.data.keyword.security-advisor_short}}](/docs/services/security-advisor?topic=security-advisor-about#about) |您可以使用 {{site.data.keyword.security-advisor_short}} 来帮助监视 {{site.data.keyword.cloud_notm}} 应用程序和工作负载的安全性。| [{{site.data.keyword.security-advisor_short}} 服务生成的事件](/docs/services/security-advisor?topic=security-advisor-at_events#at_events) |
{: caption="将事件发送到 {{site.data.keyword.cloudaccesstrailshort}} 的安全云服务的列表" caption-side="top"} 


## 平台存储服务
{: #storage}

下表列出了将事件发送到 {{site.data.keyword.cloudaccesstrailshort}} 的存储云服务：

|服务|描述|{{site.data.keyword.cloudaccesstrailshort}} 事件|
|-------------|-------------|-------------|
| [{{site.data.keyword.cos_full_notm}}](/docs/services/cloud-object-storage?topic=cloud-object-storage-about-ibm-cloud-object-storage#about-ibm-cloud-object-storage)|您可以使用 {{site.data.keyword.cos_full_notm}} 来存储 {{site.data.keyword.cloud_notm}} 中的数据。数据是经过加密的，分散在多个地理位置，可使用 REST API 通过 HTTP 进行访问。| [{{site.data.keyword.cos_full_notm}} 生成的事件](/docs/services/cloud-object-storage/basics?topic=cloud-object-storage-at_events#at_events) |  
{: caption="将事件发送到 {{site.data.keyword.cloudaccesstrailshort}} 的存储云服务的列表" caption-side="top"} 



## Watson 平台数据服务
{: #watson_data}


|服务|描述|{{site.data.keyword.cloudaccesstrailshort}} 事件|
|-------------|-------------|-------------|
| [Watson Studio](https://dataplatform.cloud.ibm.com/docs/content/getting-started/overview-ws.html?context=analytics&linkInPage=true) |Watson Studio 通过协作处理数据，提供了用于解决业务问题的环境和工具。您可以选择所需的工具来分析和可视化数据，对数据进行清理和建模，摄入流数据，或者创建、训练和部署机器学习模型。| [Watson Studio 生成的事件](https://dataplatform.cloud.ibm.com/docs/content/admin/at-events.html#ws) |  
|[Watson Machine Learning](https://dataplatform.cloud.ibm.com/docs/content/analyze-data/ml-overview.html?audience=dr&context=refinery)|您可以使用 Watson Machine Learning 来构建复杂的分析模型，利用自己的数据对模型进行训练。您可以部署这些模型，以在应用程序中使用。| [Watson Machine Learning 生成的事件](https://dataplatform.cloud.ibm.com/docs/content/admin/at-events.html#wml) | 
|[Watson Knowledge Catalog](https://dataplatform.cloud.ibm.com/docs/content/catalog/overview-wkc.html?audience=dr&context=refinery&linkInPage=true)|Watson Knowledge Catalog 提供了由数据策略框架支持的安全企业目录管理平台。目录可将数据和知识与需要使用它们的人员关联起来。数据策略框架可确保数据访问符合您的业务规则。| [Watson Knowledge Catalog 生成的事件](https://dataplatform.cloud.ibm.com/docs/content/admin/at-events.html#wkc) |  
{: caption="将事件发送到 {{site.data.keyword.cloudaccesstrailshort}} 的 Watson Cloud 数据服务的列表" caption-side="top"} 

