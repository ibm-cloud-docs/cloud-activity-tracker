---

copyright:
  years: 2016, 2018
lastupdated: "2018-09-12"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}



# 雲端服務
{: #cloud_services}

使用 {{site.data.keyword.cloudaccesstraillong}} 服務來監視使用者起始的活動，這些活動會在 {{site.data.keyword.IBM_notm}} Cloud 中變更下列任何服務的狀態：
{:shortdesc}

**附註：**若要取得 {{site.data.keyword.Bluemix_notm}} 中提供服務之地區的相關資訊，請參閱[依地區列出的服務](/docs/resources/services_region.html#services_region)。


## 基礎架構：虛擬伺服器服務
{: #vs}

下表列出將事件傳送至 {{site.data.keyword.cloudaccesstrailshort}} 的虛擬伺服器服務：

|服務|說明| {{site.data.keyword.cloudaccesstrailshort}} 事件 |
|-------------|-------------|-------------|
| [{{site.data.keyword.BluVirtServers_short}} ](/docs/vsi/vsi_about.html#about-virtual-servers)|{{site.data.keyword.BluVirtServers}} 是與專用核心及記憶體配置一起購買的可擴充虛擬伺服器。如果您要尋找可立即新增的計算資源，並存取映像檔範本這類特性，則它們是不錯的選項。| [{{site.data.keyword.BluVirtServers_short}} 所產生的事件](/docs/vsi/vsi_activity_tracker_events.html#at_events) |  
{: caption="將事件傳送至 {{site.data.keyword.cloudaccesstrailshort}} 的虛擬伺服器服務清單" caption-side="top"} 


## 平台：分析服務
{: #analytics}

下表列出將事件傳送至 {{site.data.keyword.cloudaccesstrailshort}} 的分析服務：

|服務|說明| {{site.data.keyword.cloudaccesstrailshort}} 事件 |
|-------------|-------------|-------------|
| [{{site.data.keyword.streaminganalyticsfull}} ](/docs/services/StreamingAnalytics/index.html#gettingstarted)|{{site.data.keyword.streaminganalyticsfull}} 採用 {{site.data.keyword.streamsshort}} 技術，這是一種進階分析平台，可用來即時吸收及分析來自不同資料來源類型的資訊，並與之產生關聯。| [{{site.data.keyword.streaminganalyticsshort}} 所產生的事件]() |  
{: caption="將事件傳送至 {{site.data.keyword.cloudaccesstrailshort}} 的分析雲端服務清單" caption-side="top"} 


## 平台：容器服務
{: #ikcs}

{{site.data.keyword.containershort_notm}} 會產生兩種類型的 {{site.data.keyword.cloudaccesstrailshort}} 事件：

* **叢集管理事件**： 
    
    * 會自動產生這些事件。
    * 這些事件會自動轉遞至 {{site.data.keyword.cloudaccesstrailshort}}。
    * 您可以透過 {{site.data.keyword.cloudaccesstrailshort}} **帳戶網域**來檢視這些事件。 

* **Kubernetes API 伺服器審核事件**： 

    * 會自動產生這些事件。
    * 您必須配置您的叢集，以將這些事件轉遞至 {{site.data.keyword.cloudaccesstrailshort}} 服務。
    * 您可以配置您的叢集，以將事件傳送至 {{site.data.keyword.cloudaccesstrailshort}} **帳戶網域**或**空間網域**。如需相關資訊，請參閱[傳送審核日誌](/docs/containers/cs_health.html#api_forward)。

下表列出將事件傳送至 {{site.data.keyword.cloudaccesstrailshort}} 的容器平台服務：

|服務|說明| {{site.data.keyword.cloudaccesstrailshort}} 事件 |
|-------------|-------------|-------------|
| [{{site.data.keyword.containerlong_notm}}：叢集管理事件](/docs/containers/container_index.html#container_index)|這些事件會報告像是叢集建立、刪除或更新的動作。| [叢集管理事件 ]() |  
| [{{site.data.keyword.containerlong_notm}}：API 伺服器審核事件](/docs/containers/container_index.html#container_index)| Kubernetes API 伺服器審核事件可提供影響叢集之活動順序的時間順序相關資訊。每一個動作都會產生一個事件| [Kubernetes API 伺服器審核事件](/docs/containers/cs_at_events.html#at_events) |
| [{{site.data.keyword.registrylong_notm}}](/docs/services/Registry/registry_overview.html#registry_overview) |您可以使用 {{site.data.keyword.registrylong_notm}} 服務，以高可用性及可擴充的架構來儲存及存取專用 Docker 映像檔。| [與 {{site.data.keyword.registrylong_notm}} 互動時所產生的事件](/docs/services/Registry/registry_at_events.html#at_events) | 
{: caption="容器事件" caption-side="top"} 



## 平台：Cloud Foundry 應用程式
{: #platform_cfapps}

Cloud Foundry 應用程式傳送至 {{site.data.keyword.cloudaccesstrailshort}} 的事件會列在內文區段下 `GET /v2/events` 的回應區域中。*類型* 欄位會列出所有產生事件的動作。如需相關資訊，請參閱[事件 API](https://apidocs.cloudfoundry.org/270/events/list_all_events.html)。


## 平台：核心整合式服務
{: #platform_core_integrated}

核心平台服務會產生 {{site.data.keyword.cloudaccesstrailshort}} 事件，您可以透過 {{site.data.keyword.cloudaccesstrailshort}} **帳戶網域**來檢視這些事件。

下表列出將事件傳送至 {{site.data.keyword.cloudaccesstrailshort}} 的核心平台服務：

|服務|說明| {{site.data.keyword.cloudaccesstrailshort}} 事件 |
|-------------|-------------|-------------|
| [佈建及管理 {{site.data.keyword.iamshort}} (IAM) 管理之資源的型錄服務](/docs/overview/ui.html#catalogcreate) |您可以佈建服務實例、重新命名服務實例、變更服務實例的方案，以及移除服務實例。| [與型錄服務互動時所產生的事件](/docs/services/cloud-activity-tracker/services/at_events_rc.html#at_events) |  
| [佈建及管理連結至 Cloud Foundry 空間的型錄服務](/docs/overview/ui.html#catalogcreate)|您可以佈建服務實例、重新命名服務實例、變更服務實例的方案，以及移除服務實例。</br>這些事件是針對 CF 空間中所佈建的服務而產生的。| [與型錄服務互動時所產生的事件](/docs/services/cloud-activity-tracker/services/at_events_cf.html#catalog) |  
| [管理帳戶](/docs/account/index.html#accounts)|您可以使用現有 IBM ID、建立新的 IBM ID 或使用聯合 ID 來註冊 {{site.data.keyword.IBM_notm}} 帳戶。| [管理帳戶時所產生的事件](/docs/services/cloud-activity-tracker/services/at_events_acc_mgt.html#account)|
| [管理使用者](/docs/iam/iamusermanage.html#iamusermanage)|您可以透過您所擁有或管理的帳戶或組織來檢視及管理使用者。| [管理使用者時所產生的事件](/docs/services/cloud-activity-tracker/services/at_events_acc_mgt.html#users) |
| [管理組織](/docs/account/orgs_spaces.html#orgsspacesusers)| 身為帳戶擁有者，您可以對該帳戶新增及管理組織。| [管理組織時所產生的事件](/docs/services/cloud-activity-tracker/services/at_events_acc_mgt.html#org)|
{: caption="核心平台動作的清單" caption-side="top"} 


## 平台：資料庫服務
{: #database}

下表列出將事件傳送至 {{site.data.keyword.cloudaccesstrailshort}} 的資料庫服務：

|服務|說明| {{site.data.keyword.cloudaccesstrailshort}} 事件 |
|-------------|-------------|-------------|
| [{{site.data.keyword.sqlquery_short}}](/docs/services/sql-query/sql-query.html#overview)|您可以使用 {{site.data.keyword.sqlquery_short}} 服務來執行 SQL 查詢（亦即，SELECT 陳述式），以分析、轉換或清除矩形資料。| [{{site.data.keyword.sqlquery_short}} 所產生的事件](/docs/services/sql-query/activity.html#activity-tracker-events) |  
{: caption="將事件傳送至 {{site.data.keyword.cloudaccesstrailshort}} 的資料庫雲端服務清單" caption-side="top"} 


## 平台：整合開發人員服務
{: #integrated_dev_svcs}

下表列出您可以用來開發應用程式並將事件傳送至 {{site.data.keyword.cloudaccesstrailshort}} 的雲端服務：

|服務|說明| {{site.data.keyword.cloudaccesstrailshort}} 事件 |
|-------------|-------------|-------------|
| [{{site.data.keyword.dev_console}}](/docs/apps/index.html#create) |在 {{site.data.keyword.Bluemix_notm}} 中，您可以建置企業層級的行動式和 Web 應用程式，並利用 {{site.data.keyword.Bluemix_notm}} 所管理的雲端延伸。您可以使用 {{site.data.keyword.Bluemix_notm}} 主控台及指令行工具來建置、執行及部署應用程式。您可以使用 {{site.data.keyword.dev_console}}，以透過使用入門範本套件來建立應用程式。| [{{site.data.keyword.dev_console}} 所產生的事件](/docs/apps/at_events_devx.html#at_events) |
| [{{site.data.keyword.mobilepushshort}}](/docs/services/mobilepush/c_overview_push.html#overview-push)|您可以使用 {{site.data.keyword.mobilepushshort}} 服務，將通知傳送至行動式裝置及瀏覽器。可以使用標籤將通知目標設為傳送給所有應用程式使用者或特定的一組使用者和裝置。對於您提交給服務的每一則訊息，預期的對象都會收到通知。| [{{site.data.keyword.mobilepushshort}} 所產生的事件](/docs/services/mobilepush/push_activity_tracker.html#push_activity_tracker) |  
{: caption="將事件傳送至 {{site.data.keyword.cloudaccesstrailshort}} 的 Web 和行動式雲端服務清單" caption-side="top"} 



## 平台：整合安全服務
{: #platform_integrated_security}

整合安全服務會產生 {{site.data.keyword.cloudaccesstrailshort}} 事件，您可以透過 {{site.data.keyword.cloudaccesstrailshort}} **帳戶網域**來檢視這些事件。


下表列出將事件傳送至 {{site.data.keyword.cloudaccesstrailshort}} 的核心安全平台服務：

|服務|說明| {{site.data.keyword.cloudaccesstrailshort}} 事件 |
|-------------|-------------|-------------|
| [登入 {{site.data.keyword.Bluemix_notm}}](/docs/iam/quickstart.html#getstarted)|您可以使用密碼、API 金鑰、授權碼或通行碼來登入 {{site.data.keyword.Bluemix_notm}}。身為聯合使用者，您可以使用一次性密碼或 API 金鑰，從指令行介面 (CLI) 登入。| [使用者或應用程式登入 {{site.data.keyword.Bluemix_notm}} 時所產生的事件](/docs/services/cloud-activity-tracker/services/at_events_iam.html#login) |
| [管理帳戶使用者的 Cloud Foundry 存取權](/docs/iam/mngcf.html#mngcf) |您可以對帳戶中的使用者授與、撤銷及更新 Cloud Foundry (CF) 許可權。| [管理帳戶中的 CF 角色時所產生的事件](/docs/services/cloud-activity-tracker/services/at_events_cf.html#cfroles) |
| [{{site.data.keyword.iamlong}} (IAM)](/docs/iam/users_roles.html#userroles) |您可以使用 IAM，跨 {{site.data.keyword.Bluemix_notm}} 平台和基礎架構服務管理使用者和角色。| [管理 IAM 原則時所產生的事件](/docs/services/cloud-activity-tracker/services/at_events_iam.html#policies) |
| [管理平台 API 金鑰](/docs/iam/apikeys.html#platform-api-keys) |您可以在 {{site.data.keyword.IBM_notm}} Cloud 中定義與使用者或服務 ID 相關聯的平台 API 金鑰。| [管理平台 API 金鑰時所產生的事件](/docs/services/cloud-activity-tracker/services/at_events_iam.html#apikeys) |
| [管理服務 ID](/docs/iam/serviceid.html#serviceids) |您可以在 {{site.data.keyword.IBM_notm}} Cloud 的帳戶層次上定義服務 ID。| [管理服務 ID 時所產生的事件](/docs/services/cloud-activity-tracker/services/at_events_iam.html#serviceids) |
| [管理存取群組](/docs/iam/groups.html#groups) |您可以定義存取群組，以將一組使用者和服務 ID 組織成一個實體中，以便您能輕易指派許可權。| [管理存取群組時所產生的事件](/docs/services/cloud-activity-tracker/services/at_events_iam.html#access) |
{: caption="核心安全平台服務的清單" caption-side="top"} 


## 平台：整合服務
{: #integration}

下表列出將事件傳送至 {{site.data.keyword.cloudaccesstrailshort}} 的整合服務：

|服務|說明| {{site.data.keyword.cloudaccesstrailshort}} 事件 |
|-------------|-------------|-------------|
| [{{site.data.keyword.messagehub}}](/docs/services/MessageHub/messagehub010.html#about)|{{site.data.keyword.messagehub}} 是以 Apache Kafka 建置的高傳輸量訊息匯流排。它經過最佳化，可將事件吸收至 {{site.data.keyword.IBM_notm}} 並在服務與應用程式之間進行事件串流配送。| [{{site.data.keyword.messagehub}} 所產生的事件](/docs/services/MessageHub/at-events.html#at_events) |  
{: caption="將事件傳送至 {{site.data.keyword.cloudaccesstrailshort}} 的整合雲端服務清單" caption-side="top"} 



## 平台：網路服務
{: #network}

下表列出將事件傳送至 {{site.data.keyword.cloudaccesstrailshort}} 的網路雲端服務：

|服務|說明| {{site.data.keyword.cloudaccesstrailshort}} 事件 |
|-------------|-------------|-------------|
| [IBM Cloud Internet Services (CIS)](/docs/infrastructure/cis/about.html#about-ibm-cloud-internet-services-cis-)|IBM Cloud Internet Services (CIS) 可提供快速、高效能、可靠且安全的網際網路服務。| [IBM Cloud Internet Services 所產生的事件](/docs/infrastructure/cis/at_events.html#at_events) |  
{: caption="將事件傳送至 {{site.data.keyword.cloudaccesstrailshort}} 的網路雲端服務清單" caption-side="top"} 



## 平台：安全服務
{: #security}

下表列出將事件傳送至 {{site.data.keyword.cloudaccesstrailshort}} 的安全雲端服務：


|服務|說明| {{site.data.keyword.cloudaccesstrailshort}} 事件 |
|-------------|-------------|-------------|
| [{{site.data.keyword.cloudaccesstraillong_notm}}](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#activity_tracker_ov)|您可以使用 {{site.data.keyword.cloudaccesstrailshort}} 服務來監視 {{site.data.keyword.cloudaccesstraillong_notm}}。| [{{site.data.keyword.cloudaccesstraillong_notm}} 服務所產生的事件](/docs/services/cloud-activity-tracker/reference/events.html#events) |  
| [{{site.data.keyword.appid_full_notm}}](/docs/services/appid/about.html#about) |您可以使用 {{site.data.keyword.appid_short}} 將鑑別新增至您的行動式和 Web 應用程式，以及保護後端資源。| [{{site.data.keyword.appid_short}} 服務所產生的事件](/docs/services/appid/iam.html#tracking) |
| [{{site.data.keyword.cloudcerts_full_notm}}](/docs/services/certificate-manager/about.html#about-certificate-manager) |您可以使用 {{site.data.keyword.cloudcerts_short}} 來管理 {{site.data.keyword.Bluemix_notm}} 型應用程式和服務的 SSL 憑證。| [{{site.data.keyword.cloudcerts_short}} 服務所產生的事件](/docs/services/certificate-manager/at_events.html#at_events) |
| [{{site.data.keyword.keymanagementservicelong}}](/docs/services/key-protect/index.html#getting-started-with-key-protect) |您可以使用 {{site.data.keyword.keymanagementserviceshort}} 服務，在 {{site.data.keyword.Bluemix_notm}} 之間佈建應用程式的加密金鑰。| [{{site.data.keyword.keymanagementserviceshort}} 服務所產生的事件](/docs/services/key-protect/at-events.html#at-events) |
{: caption="將事件傳送至 {{site.data.keyword.cloudaccesstrailshort}} 的安全雲端服務清單" caption-side="top"} 


## 平台：儲存空間服務
{: #storage}

下表列出將事件傳送至 {{site.data.keyword.cloudaccesstrailshort}} 的儲存空間雲端服務：

|服務|說明| {{site.data.keyword.cloudaccesstrailshort}} 事件 |
|-------------|-------------|-------------|
| [{{site.data.keyword.cos_full_notm}}](/docs/services/cloud-object-storage/about-cos.html#about-ibm-cloud-object-storage)|您可以使用 {{site.data.keyword.cos_full_notm}}，將資料儲存在 {{site.data.keyword.Bluemix_notm}} 中。會在多個地理位置之間對資料進行加密及傳播，並透過 HTTP 使用 REST API 來存取資料。| [{{site.data.keyword.cos_full_notm}} 所產生的事件](/docs/services/cloud-object-storage/basics/at.html#at_events) |  
{: caption="將事件傳送至 {{site.data.keyword.cloudaccesstrailshort}} 的儲存空間雲端服務清單" caption-side="top"} 



## Watson 平台：資料服務
{: #watson_data}


|服務|說明| {{site.data.keyword.cloudaccesstrailshort}} 事件 |
|-------------|-------------|-------------|
| [Watson Studio](https://dataplatform.cloud.ibm.com/docs/content/getting-started/overview-ws.html?context=analytics&linkInPage=true) |Watson Studio 可提供環境及工具，以透過分工合作的方式處理資料來解決您的商業問題。您可以選擇分析及視覺化資料、清理及整理資料、吸收串流資料，或建立、訓練及部署機器學習模型所需的工具。| [Watson Studio 所產生的事件](https://dataplatform.cloud.ibm.com/docs/content/admin/at-events.html#ws) |  
| [Watson Machine Learning](https://dataplatform.cloud.ibm.com/docs/content/analyze-data/ml-overview.html?audience=dr&context=refinery)|您可以使用 Watson Machine Learning 來建置更準確的分析模型，並使用您自己的資料來進行訓練，以便您能夠部署以用於應用程式中。| [Watson Machine Learning 所產生的事件](https://dataplatform.cloud.ibm.com/docs/content/admin/at-events.html#wml) | 
| [Watson Knowledge Catalog](https://dataplatform.cloud.ibm.com/docs/content/catalog/overview-wkc.html?audience=dr&context=refinery&linkInPage=true)|Watson Knowledge Catalog 可提供資料原則架構支援的安全企業型錄管理平台。型錄會將資料和知識與需要使用它的人連接起來。資料原則架構可確保資料存取符合您的商業規則。| [Watson Knowledge Catalog 所產生的事件](https://dataplatform.cloud.ibm.com/docs/content/admin/at-events.html#wkc) |  
{: caption="將事件傳送至 {{site.data.keyword.cloudaccesstrailshort}} 的 Watson 雲端資料服務清單" caption-side="top"} 


