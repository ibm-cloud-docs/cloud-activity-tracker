---

copyright:
  years: 2016, 2019
lastupdated: "2019-02-18"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}



# Cloud-Services
{: #cloud_services}

Verwenden Sie den {{site.data.keyword.cloudaccesstraillong}}-Service, um die vom Benutzer eingeleiteten Aktivitäten zu überwachen, die den Status eines der folgenden Services in der {{site.data.keyword.IBM_notm}} Cloud ändern:
{:shortdesc}

**Hinweis:** Informationen zu den {{site.data.keyword.cloud_notm}}-Regionen, in denen ein Service in verfügbar ist, finden Sie in [Services nach Region](/docs/resources/services_region.html#services_region).


## Datenverarbeitung: Infrastrukturservices
{: #infrastructure}

**Hinweis:** Damit ein Benutzer {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse für {{site.data.keyword.BluVirtServers_short}} und {{site.data.keyword.baremetal_short}} generieren kann, benötigt er Zugriff auf Infrastrukturressourcen in der IBM Cloud-Konsole. Weitere Informationen finden Sie in [{{site.data.keyword.BluVirtServers_short}}- und  {{site.data.keyword.baremetal_short}}-Aktivität mit {{site.data.keyword.cloudaccesstrailshort}} überwachen](/docs/services/cloud-activity-tracker/tutorials/vsi.html#vsi). 

Die folgende Tabelle enthält eine Auflistung von Infrastrukturservices, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden: 

| Service     | Beschreibung | {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse |
|-------------|-------------|-------------|
| [{{site.data.keyword.BluVirtServers_short}} ](/docs/vsi/vsi_about.html#about-virtual-servers)| {{site.data.keyword.BluVirtServers}} sind skalierbare virtuelle Server, die mit dedizierten Kernen (Cores) und Speicherzuordnungen erworben werden. Sie stellen eine großartige Option dar, wenn Sie nach Rechenressourcen suchen, die in wenigen Minuten hinzugefügt werden können und Zugriff auf Features wie Imagevorlagen bieten.  | [Von {{site.data.keyword.BluVirtServers_short}} generierte Ereignisse](/docs/vsi/vsi_activity_tracker_events.html#at_events) |  
| [{{site.data.keyword.baremetal_long}} ](/docs/bare-metal/about.html#about) | {{site.data.keyword.baremetal_short}} sind physische Single-Tenant-Server, die Ihnen Leistung und Kontrolle mit maschinennahem Zugriff auf die Hardwareressourcen bereitstellen. | [Von {{site.data.keyword.baremetal_short}} generierte Ereignisse](/docs/bare-metal/bm-activity-tracker-events.html#at_events) | 
{: caption="Liste der Infrastrukturservices, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden" caption-side="top"} 




## Datenverarbeitung: Serverunabhängige Datenverarbeitungsservices
{: #serverless}

Die folgende Tabelle enthält eine Auflistung von serverunabhängigen Datenverarbeitungsservices, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden: 

| Service     | Beschreibung | {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse |
|-------------|-------------|-------------|
| [{{site.data.keyword.openwhisk_short}}](/docs/openwhisk/index.html#index) | {{site.data.keyword.openwhisk_short}} ist eine auf Apache OpenWhisk basierende mehrsprachige FaaS-Programmierplattform (Functions as a Service). Mit {{site.data.keyword.openwhisk_short}} können Entwickler schlanken Code erstellen, sogenannte Aktionen, mit denen die Anwendungslogik skalierbar ausführt wird. | [Von {{site.data.keyword.openwhisk_short}} generierte Ereignisse](/docs/openwhisk/at-events.html#activity_tracker) |
{: caption="Liste der serverunabhängigen Datenverarbeitungsservices, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden" caption-side="top"} 

## Plattform: Analytics-Services
{: #analytics}

Die folgende Tabelle enthält eine Auflistung von Analytics-Services, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden:

| Service     | Beschreibung | {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse |
|-------------|-------------|-------------|
| [{{site.data.keyword.streaminganalyticsfull}} ](/docs/services/StreamingAnalytics/index.html#gettingstarted)| {{site.data.keyword.streaminganalyticsfull}} basiert auf {{site.data.keyword.streamsshort}}, einer hochentwickelten Analyseplattform, mit der Sie Informationen aus verschiedenen Arten von Datenquellen in Echtzeit erfassen, analysieren und korrelieren können. | [Von {{site.data.keyword.streaminganalyticsshort}} generierte Ereignisse]() |  
{: caption="Liste der Analytics Cloud-Services, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden" caption-side="top"} 


## Plattform: Container-Services
{: #ikcs}

Der {{site.data.keyword.containershort_notm}} generiert zwei Typen von {{site.data.keyword.cloudaccesstrailshort}}-Ereignissen:

* **Clusterverwaltungsereignisse**: 
    
    * Diese Ereignisse werden automatisch generiert.
    * Diese Ereignisse werden automatisch an {{site.data.keyword.cloudaccesstrailshort}} weitergeleitet.
    * Sie können diese Ereignisse über die {{site.data.keyword.cloudaccesstrailshort}}-**Kontodomäne** anzeigen. 

* **Prüfereignisse des Kubernetes-API-Servers**: 

    * Diese Ereignisse werden automatisch generiert.
    * Sie müssen Ihren Cluster so konfigurieren, dass er diese Ereignisse an den {{site.data.keyword.cloudaccesstrailshort}}-Service weiterleitet.
    * Sie können Ihren Cluster so konfigurieren, dass er Ereignisse an die {{site.data.keyword.cloudaccesstrailshort}}-**Kontodomäne** oder an eine **Bereichsdomäne** (Spacedomäne) sendet. Weitere Informationen finden Sie in [Prüfprotokolle senden](/docs/containers/cs_health.html#api_forward).

Die folgende Tabelle enthält eine Auflistung von Services der Containerplattform, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden:

| Service     | Beschreibung | {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse |
|-------------|-------------|-------------|
| [{{site.data.keyword.containerlong_notm}}: Clusterverwaltungsereignisse](/docs/containers/container_index.html#container_index)| Diese Ereignisse liefern Meldungen zu Aktionen wie Erstellen, Löschen oder Aktualisieren von Clustern. | [Clusterverwaltungsereignisse ](/docs/containers/cs_at_events.html#cluster-events) |  
| [{{site.data.keyword.containerlong_notm}}: API-Server-Prüfereignisse](/docs/containers/container_index.html#container_index)| Prüfereignisse des Kubernetes-API-Servers liefern chronologische Informationen zu der Abfolge von Aktivitäten, die einen Cluster betreffen. Jede Aktion generiert ein Ereignis. | [Prüfereignisse des Kubernetes-API-Servers](/docs/containers/cs_at_events.html#kube-events) |
| [{{site.data.keyword.registrylong_notm}}](/docs/services/Registry/registry_overview.html#registry_overview) | Mit dem {{site.data.keyword.registrylong_notm}}-Service können Sie private Docker-Images in einer hoch verfügbaren und skalierbaren Architektur speichern und auf diese zugreifen. | [Bei der Interaktion mit der {{site.data.keyword.registrylong_notm}} generierte Ereignisse](/docs/services/Registry/registry_at_events.html#at_events) | 
{: caption="Containerereignisse" caption-side="top"} 



## Plattform: Cloud Foundry-Anwendungen
{: #platform_cfapps}

Die Ereignisse, die von Cloud Foundry-Anwendungen an {{site.data.keyword.cloudaccesstrailshort}} gesendet werden, werden im Antwortbereich von `GET /v2/events` unter dem Hauptteil aufgelistet. Im Feld *Type* werden alle Aktionen aufgeführt, bei denen ein Ereignis generiert wird. Weitere Informationen finden Sie in [API für Ereignisse![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://apidocs.cloudfoundry.org/270/events/list_all_events.html){:new_window}. 


## Plattform: Zentrale integrierte Services
{: #platform_core_integrated}

Die zentralen Services der Plattform generieren {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse, die Sie über die **Kontodomäne** von {{site.data.keyword.cloudaccesstrailshort}} anzeigen können.

Die folgende Tabelle enthält eine Auflistung von zentralen Services der Plattform, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden:

| Service     | Beschreibung | {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse |
|-------------|-------------|-------------|
| [Bereitstellen und Verwalten von Katalogservices für Ressourcen, die von {{site.data.keyword.iamshort}} (IAM) verwaltet werden](/docs/overview/ui.html#catalogcreate) | Sie können eine Serviceinstanz bereitstellen, eine Serviceinstanz umbenennen, den Plan für eine Serviceinstanz ändern und eine Serviceinstanz entfernen. | [Bei der Interaktion mit Katalogservices generierte Ereignisse](/docs/services/cloud-activity-tracker/services/at_events_rc.html#at_events_rc) |  
| [Bereitstellen und Verwalten von Katalogservices, die an einen Cloud Foundry-Bereich (Space) gebunden sind](/docs/overview/ui.html#catalogcreate)| Sie können eine Serviceinstanz bereitstellen, eine Serviceinstanz umbenennen, den Plan für eine Serviceinstanz ändern und eine Serviceinstanz entfernen. </br>Diese Ereignisse werden für Services generiert, die in einem CF-Bereich bereitgestellt werden. | [Bei der Interaktion mit Katalogservices generierte Ereignisse](/docs/services/cloud-activity-tracker/services/at_events_cf.html#cf_catalog) |  
| [Verwalten eines Kontos](/docs/account/index.html#accounts) | Sie können sich für ein {{site.data.keyword.IBM_notm}}-Konto anmelden, indem Sie eine vorhandene IBMid verwenden, eine neue IBMid erstellen oder eine föderierte ID benutzen. | [Beim Verwalten eines Kontos generierte Ereignisse](/docs/services/cloud-activity-tracker/services/at_events_acc_mgt.html#at_events_acc_mgt_account) |
| [Verwalten von Benutzern](/docs/iam/iamusermanage.html#iamusermanage) | Sie können Benutzer übergreifend über die Konten oder Organisationen, deren Eigner Sie sind oder die Sie verwalten, anzeigen und verwalten.  | [Beim Verwalten von Benutzern generierte Ereignisse](/docs/services/cloud-activity-tracker/services/at_events_acc_mgt.html#at_events_acc_mgt_users) |
| [Verwalten von Organisationen](/docs/account/orgs_spaces.html#orgsspacesusers) | Als Kontoeigner können Sie Organisationen zum Account hinzufügen und verwalten. | [Beim Verwalten von Organisationen generierte Ereignisse](/docs/services/cloud-activity-tracker/services/at_events_acc_mgt.html#at_events_acc_mgt_org) |
{: caption="Liste der zentralen Aktionen für die Plattform" caption-side="top"} 


## Plattform: Datenbankservices
{: #database}

Die folgende Tabelle enthält eine Auflistung von Datenbankservices, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden:

| Service     | Beschreibung | {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse |
|-------------|-------------|-------------|
| [{{site.data.keyword.databases-for-postgresql_full_notm}}](/docs/services/databases-for-postgresql?topic=databases-for-postgresql-about#about) | {{site.data.keyword.databases-for-postgresql_full_notm}} ist ein verwalteter PostgreSQL-Service, der in der {{site.data.keyword.cloud_notm}} gehostet wird und mit anderen {{site.data.keyword.cloud_notm}}-Services integriert ist. | [Von {{site.data.keyword.databases-for-postgresql_full_notm}} generierte Ereignisse](/docs/services/databases-for-postgresql?topic=databases-for-postgresql-activity-tracker#activity-tracker) |
| [{{site.data.keyword.databases-for-redis_full_notm}}](/docs/services/databases-for-redis/index.html#about-databases-for-redis) | {{site.data.keyword.databases-for-redis_full_notm}} ist ein verwalteter Redis-Service, der in der {{site.data.keyword.cloud_notm}} gehostet wird und mit anderen {{site.data.keyword.cloud_notm}}-Services integriert ist. | [Von {{site.data.keyword.databases-for-redis_full_notm}} generierte Ereignisse](/docs/services/databases-for-redis/reference-activity-tracker.html#activity-tracker-integration) |
| [{{site.data.keyword.sqlquery_short}}](/docs/services/sql-query/sql-query.html#overview)| Mit dem {{site.data.keyword.sqlquery_short}}-Service können Sie SQL-Abfragen (d. h. Anweisungen vom Typ SELECT) zum Analysieren, Transformieren oder Bereinigen rechteckiger Daten ausführen. | [Von {{site.data.keyword.sqlquery_short}} generierte Ereignisse](/docs/services/sql-query/activity.html#activity-tracker-events) |  
| [{{site.data.keyword.databases-for-etcd_full_notm}}](/docs/services/databases-for-etcd/index.html#about-databases-for-etcd) | {{site.data.keyword.databases-for-etcd_full_notm}} ist ein verwalteter etcd-Service, der in der {{site.data.keyword.cloud_notm}} gehostet wird und mit anderen {{site.data.keyword.cloud_notm}}-Services integriert ist. | [Von {{site.data.keyword.databases-for-etcd_full_notm}} generierte Ereignisse](/docs/services/databases-for-etcd/reference-activity-tracker.html#activity-tracker-integration) |
| [{{site.data.keyword.databases-for-elasticsearch_full_notm}}](/docs/services/databases-for-elasticsearch/index.html#about-databases-for-elasticsearch) | {{site.data.keyword.databases-for-elasticsearch_full_notm}} ist ein verwalteter Elasticsearch-Service, der in der {{site.data.keyword.cloud_notm}} gehostet wird und mit anderen {{site.data.keyword.cloud_notm}}-Services integriert ist. | [Von [{{site.data.keyword.databases-for-elasticsearch_full_notm}}](/docs/services/databases-for-elasticsearch/reference-activity-tracker.html#activity-tracker-integration) generierte Ereignisse |
| [{{site.data.keyword.messages-for-rabbitmq_full_notm}}](/docs/services/messages-for-rabbitmq/index.html#about-messages-for-rabbitmq)  | {{site.data.keyword.messages-for-rabbitmq_full_notm}} ist ein verwalteter RabbitMQ-Service, der in der {{site.data.keyword.cloud_notm}} gehostet wird und mit anderen {{site.data.keyword.cloud_notm}}-Services integriert ist. | [Von [{{site.data.keyword.messages-for-rabbitmq_full_notm}](/docs/services/messages-for-rabbitmq/reference-activity-tracker.html#activity-tracker-integration) generierte Ereignisse |
{: caption="Liste der Datenbank-Cloud-Services, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden" caption-side="top"}

## Plattform: Entwicklertools
{: #devops}

Die folgende Tabelle enthält eine Auflistung von DevOps-Services, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden: 

| Service     | Beschreibung | {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse |
|-------------|-------------|-------------|
| [{{site.data.keyword.DRA_short}}](/docs/services/DevOpsInsights/insights_about.html#insights_about) | {{site.data.keyword.DRA_short}} ist eine Integration in den offenen Toolchainkatalog von {{site.data.keyword.cloud_notm}}. | [Von {{site.data.keyword.DRA_short}} generierte Ereignisse](/docs/services/DevOpsInsights/at-events.html#at_events) |
| [{{site.data.keyword.contdelivery_short}}](/docs/services/ContinuousDelivery/cd_overview.html#cd_overview) | Mit {{site.data.keyword.contdelivery_short}} können Sie Anwendungen mithilfe von DevOps-Verfahren und branchenführenden Tools erstellen, testen und bereitstellen. | [Von {{site.data.keyword.contdelivery_short}} generierte Ereignisse](/docs/services/ContinuousDelivery/at-events.html#at_events) |
{: caption="Liste der Entwicklertools, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden" caption-side="top"}



## Plattform: Integrierte Entwicklerservices
{: #integrated_dev_svcs}

Die folgende Tabelle enthält eine Auflistung von Cloud-Services, die Sie verwenden können, um Apps zu entwickeln und Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} zu senden: 

| Service     | Beschreibung | {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse |
|-------------|-------------|-------------|
| [{{site.data.keyword.dev_console}}](/docs/apps/index.html#create) | In {{site.data.keyword.cloud_notm}} können Sie auf Unternehmen abgestimmte mobile und Webanwendungen erstellen und die Vorteile von Clouderweiterungen nutzen, die in der {{site.data.keyword.cloud_notm}} gehostet werden. Mit der Konsole und den Befehlszeilentools von {{site.data.keyword.cloud_notm}} können Sie Ihre Apps erstellen, ausführen und bereitstellen. Danach können Sie mit dem {{site.data.keyword.dev_console}} unter Verwendung eines Starter-Kits eine App erstellen. | [Von {{site.data.keyword.dev_console}} generierte Ereignisse](/docs/apps/at_events_devx.html#at_events) |
| [{{site.data.keyword.mobilepushshort}}](/docs/services/mobilepush/c_overview_push.html#overview-push)| Mit dem {{site.data.keyword.mobilepushshort}}-Service können Sie Benachrichtigungen an mobile Geräte und Browser senden. Benachrichtigungen können an alle Anwendungsbenutzer gerichtet werden oder bei Verwendung entsprechender Tags eine bestimmte Gruppe von Benutzern und Geräten zum Ziel haben. Für jede Nachricht, die Sie an den Service übergeben, erhält die Zielgruppe eine Benachrichtigung. | [Von {{site.data.keyword.mobilepushshort}} generierte Ereignisse](/docs/services/mobilepush/push_activity_tracker.html#push_activity_tracker) |  
{: caption="Liste der Web- und mobilen Cloud-Services, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden" caption-side="top"}



## Plattform: Integrierte Sicherheitsservices
{: #platform_integrated_security}

Integrierte Sicherheitsservices generieren {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse, die Sie über die {{site.data.keyword.cloudaccesstrailshort}}-**Kontodomäne** anzeigen können. 

Die folgende Tabelle enthält eine Auflistung von zentralen Sicherheitsplattformservices, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden: 

| Service     | Beschreibung | {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse |
|-------------|-------------|-------------|
| [Anmeldung bei {{site.data.keyword.cloud_notm}}](/docs/iam/quickstart.html#getstarted)| Sie können sich mit einem Kennwort, einem API-Schlüssel, einem Berechtigungscode oder einem Kenncode bei {{site.data.keyword.cloud_notm}} anmelden. Als föderierter Benutzer können Sie sich über die Befehlszeilenschnittstelle (CLI) mit einem einmaligen Kenncode oder einem API-Schlüssel anmelden. | [Bei der Anmeldung eines Benutzers oder einer App bei {{site.data.keyword.cloud_notm}} generierte Ereignisse](/docs/services/cloud-activity-tracker/services/at_events_iam.html#at_events_iam_login) |
| [Verwaltung des Cloud Foundry-Zugriffs des Kontobenutzers](/docs/iam/mngcf.html#mngcf) | Sie können für Benutzer im Konto CF-Berechtigungen (CF - Cloud Foundry) erteilen, widerrufen und aktualisieren. | [Bei der Verwaltung von CF-Rollen im Konto generierte Ereignisse](/docs/services/cloud-activity-tracker/services/at_events_cf.html#cf_cfroles) |
| [{{site.data.keyword.iamlong}} (IAM)](/docs/iam/users_roles.html#userroles) | Mit IAM können Sie Benutzer und Rollen für alle Services der {{site.data.keyword.cloud_notm}}-Plattform und -Infrastruktur verwalten. | [Bei der Verwaltung von IAM-Richtlinien generierte Ereignisse](/docs/services/cloud-activity-tracker/services/at_events_iam.html#at_events_iam_policies) |
| [Verwaltung der Plattform-API-Schlüssel](/docs/iam/apikeys.html#platform-api-keys) | In der {{site.data.keyword.IBM_notm}} Cloud können Sie Plattform-API-Schlüssel definieren, die einem Benutzer oder einer Service-ID zugeordnet sind. | [Bei der Verwaltung von Plattform-API-Schlüsseln generierte Ereignisse](/docs/services/cloud-activity-tracker/services/at_events_iam.html#at_events_iam_apikeys) |
| [Verwaltung von Service-IDs](/docs/iam/serviceid.html#serviceids) | Sie können Service-IDs auf der Kontoebene in der {{site.data.keyword.IBM_notm}} Cloud definieren. | [Bei der Verwaltung von Service-IDs generierte Ereignisse](/docs/services/cloud-activity-tracker/services/at_events_iam.html#at_events_iam_serviceids) |
| [Verwaltung von Zugriffsgruppen](/docs/iam/groups.html#groups) | Sie können Zugriffsgruppen definieren, um eine Reihe von Benutzern und Service-IDs in einer einzigen Entität zusammenzufassen, die Ihnen das Zuweisen von Berechtigungen erleichtert. | [Bei der Verwaltung von Zugriffsgruppen generierte Ereignisse](/docs/services/cloud-activity-tracker/services/at_events_iam.html#at_events_iam_access) |
{: caption="Liste der zentralen Sicherheitsplattformservices" caption-side="top"}


## Plattform: Integrationsservices
{: #integration}

Die folgende Tabelle enthält eine Auflistung von Integrationsservices, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden:  
| Service     | Beschreibung | {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse |
|-------------|-------------|-------------|
| [{{site.data.keyword.messagehub}}](/docs/services/MessageHub/messagehub010.html#about)| {{site.data.keyword.messagehub}} ist ein Nachrichtenbus mit hohem Durchsatz, der mit Apache Kafka erstellt wurde. Er ist für die Aufnahme von Ereignissen in {{site.data.keyword.IBM_notm}} und die Verteilung des Ereignisstroms zwischen Ihren Services und Anwendungen optimiert. | [Von {{site.data.keyword.messagehub}} generierte Ereignisse](/docs/services/MessageHub/at-events.html#at_events) |  
{: caption="Liste der Integrations-Cloud-Services, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden" caption-side="top"}



## Plattform: Netzservices
{: #network}

Die folgende Tabelle enthält eine Auflistung von Netz-Cloud-Services, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden: 
| Service     | Beschreibung | {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse |
|-------------|-------------|-------------|
| [IBM Cloud Internet Services (CIS)](/docs/infrastructure/cis/about.html#about-ibm-cloud-internet-services-cis-)| IBM Cloud Internet Services (CIS) stellt einen schnellen, zuverlässigen und sicheren Internet-Service mit hoher Leistung zur Verfügung. | [Von IBM Cloud Internet Services generierte Ereignisse](/docs/infrastructure/cis/at_events.html#at_events) |  
{: caption="Liste der Netz-Cloud-Services, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden" caption-side="top"}



## Plattform: Sicherheitsservices
{: #security}

Die folgende Tabelle enthält eine Auflistung von Sicherheits-Cloud-Services, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden: 

| Service     | Beschreibung | {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse |
|-------------|-------------|-------------|
| [{{site.data.keyword.cloudaccesstraillong_notm}}](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#activity_tracker_ov)| Mit dem {{site.data.keyword.cloudaccesstrailshort}}-Service können Sie {{site.data.keyword.cloudaccesstraillong_notm}} überwachen. | [Vom {{site.data.keyword.cloudaccesstraillong_notm}}-Service generierte Ereignisse](/docs/services/cloud-activity-tracker/reference/events.html#events) |  
| [{{site.data.keyword.appid_full_notm}}](/docs/services/appid/about.html#about) | Mit {{site.data.keyword.appid_short}} können Sie Ihren mobilen und Web-Apps Authentifizierung hinzufügen und Ihre Back-End-Ressourcen schützen. | [Vom {{site.data.keyword.appid_short}}-Service generierte Ereignisse](/docs/services/appid/iam.html#tracking) |
| [{{site.data.keyword.cloudcerts_full_notm}}](/docs/services/certificate-manager/about.html#about-certificate-manager) | Mit {{site.data.keyword.cloudcerts_short}} können Sie die SSL-Zertifikate für Ihre {{site.data.keyword.cloud_notm}}-basierten Apps und Services verwalten. | [Vom {{site.data.keyword.cloudcerts_short}}-Service generierte Ereignisse](/docs/services/certificate-manager/at_events.html#at_events) |
| [{{site.data.keyword.keymanagementservicelong}}](/docs/services/key-protect/index.html#getting-started-with-key-protect) | Mit dem {{site.data.keyword.keymanagementserviceshort}}-Service können Sie verschlüsselte Schlüssel für Apps in der gesamten {{site.data.keyword.cloud_notm}} bereitstellen. | [Vom {{site.data.keyword.keymanagementserviceshort}}-Service generierte Ereignisse](/docs/services/key-protect/at-events.html#at-events) |
| [{{site.data.keyword.security-advisor_short}}](/docs/services/security-advisor/about.html#about) | Mit {{site.data.keyword.security-advisor_short}} können Sie die Sicherheit Ihrer {{site.data.keyword.cloud_notm}}-Apps und -Workloads überwachen. | [Vom {{site.data.keyword.security-advisor_short}}-Service generierte Ereignisse](/docs/services/security-advisor/at-events.html#at_events) |
{: caption="Liste  der Sicherheits-Cloud-Services, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden" caption-side="top"}


## Plattform: Speicherservices
{: #storage}

Die folgende Tabelle enthält eine Auflistung von Speicher-Cloud-Services, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden: 

| Service     | Beschreibung | {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse |
|-------------|-------------|-------------|
| [{{site.data.keyword.cos_full_notm}}](/docs/services/cloud-object-storage/about-cos.html#about-ibm-cloud-object-storage)| Mit {{site.data.keyword.cos_full_notm}} können Sie Daten in der {{site.data.keyword.cloud_notm}} speichern. Daten werden verschlüsselt und über mehrere geografische Standorte hinweg verteilt gespeichert, wo mit einer REST-API über HTTP auf sie zugegriffen werden kann.   | [Von {{site.data.keyword.cos_full_notm}} generierte Ereignisse](/docs/services/cloud-object-storage/basics/at.html#at_events) |  
{: caption="Liste der Speicher-Cloud-Services, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden" caption-side="top"}



## Watson-Plattform: Datenservices
{: #watson_data}


| Service     | Beschreibung | {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse |
|-------------|-------------|-------------|
| [Watson Studio](https://dataplatform.cloud.ibm.com/docs/content/getting-started/overview-ws.html?context=analytics&linkInPage=true) | Watson Studio stellt die Umgebung und Tools bereit, die Ihnen helfen, Ihre Geschäftsprobleme durch gemeinsames Arbeiten mit Daten zu lösen. Sie können auswählen, welche Tools Sie zum Analysieren und Darstellen von Daten, zum Bereinigen und Formen von Daten, zum Einpflegen von Streamingdaten oder zum Erstellen, Trainieren und Bereitstellen von Maschinenlernmodellen benötigen. | [Von Watson Studio generierte Ereignisse](https://dataplatform.cloud.ibm.com/docs/content/admin/at-events.html#ws) |  
| [Watson Machine Learning](https://dataplatform.cloud.ibm.com/docs/content/analyze-data/ml-overview.html?audience=dr&context=refinery)| Mit Watson Machine Learning können Sie anspruchsvolle Analysemodelle erstellen, die Sie mit Ihren eigenen Daten trainieren und zur Verwendung in Anwendungen bereitstellen können. | [Von Watson Machine Learning generierte Ereignisse](https://dataplatform.cloud.ibm.com/docs/content/admin/at-events.html#wml) | 
| [Watson Knowledge Catalog](https://dataplatform.cloud.ibm.com/docs/content/catalog/overview-wkc.html?audience=dr&context=refinery&linkInPage=true)| Watson Knowledge Catalog stellt eine sichere Plattform für die Unternehmenskatalogverwaltung bereit, die durch ein Framework für Datenrichtlinien gestützt wird. Ein Katalog verbindet Daten und Wissen mit den Personen, die sie verwenden müssen. Das Framework für Datenrichtlinien stellt sicher, dass der Datenzugriff mit Ihren Geschäftsregeln konform ist. | [von Watson Knowledge Catalog generierte Ereignisse](https://dataplatform.cloud.ibm.com/docs/content/admin/at-events.html#wkc) |  
{: caption="Liste der Watson-Cloud-Datenservices, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden" caption-side="top"} 


