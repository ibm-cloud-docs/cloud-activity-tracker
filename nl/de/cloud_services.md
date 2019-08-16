---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

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
{:deprecated: .deprecated}



# Cloud-Services
{: #cloud_services}

Verwenden Sie den {{site.data.keyword.cloudaccesstraillong}}-Service, um die vom Benutzer eingeleiteten Aktivitäten zu überwachen, die den Status eines der folgenden Services in der {{site.data.keyword.IBM_notm}} Cloud ändern:
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} wird nicht mehr verwendet. Ab 09. Mai 2019 können keine neuen {{site.data.keyword.cloudaccesstrailshort}}-Instanzen mehr bereitgestellt werden. Vorhandene Instanzen des Premium-Plans werden bis 30. September 2019 unterstützt. Wenn Sie die Aktivitäten Ihres {{site.data.keyword.cloud_notm}}-Kontos weiterhin verfolgen möchten, stellen Sie eine Instanz von [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) bereit.
{: deprecated}

**Hinweis:** Informationen zu den {{site.data.keyword.cloud_notm}}-Regionen, in denen ein Service in verfügbar ist, finden Sie in [Services nach Region](/docs/resources?topic=resources-services_region#services_region).


## Infrastrukturservices für Datenverarbeitung
{: #infrastructure}

**Hinweis:** Damit ein Benutzer {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse für {{site.data.keyword.BluVirtServers_short}} und {{site.data.keyword.baremetal_short}} generieren kann, benötigt er Zugriff auf Infrastrukturressourcen in der {{site.data.keyword.cloud_notm}}-Konsole. Weitere Informationen finden Sie in [{{site.data.keyword.BluVirtServers_short}}- und {{site.data.keyword.baremetal_short}}-Aktivität mit {{site.data.keyword.cloudaccesstrailshort}} überwachen](/docs/services/cloud-activity-tracker/tutorials?topic=cloud-activity-tracker-vsi#vsi).

Die folgende Tabelle enthält eine Auflistung von Infrastrukturservices, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden:

| Service     | Beschreibung | {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse |
|-------------|-------------|-------------|
| [{{site.data.keyword.BluVirtServers_short}} ](/docs/vsi?topic=virtual-servers-about-virtual-servers#about-virtual-servers)| {{site.data.keyword.BluVirtServers}} sind skalierbare virtuelle Server, die mit dedizierten Kernen (Cores) und Speicherzuordnungen erworben werden. Sie stellen eine großartige Option dar, wenn Sie nach Rechenressourcen suchen, die in wenigen Minuten hinzugefügt werden können und Zugriff auf Features wie Imagevorlagen bieten.  | [Von {{site.data.keyword.BluVirtServers_short}} generierte Ereignisse](/docs/vsi?topic=virtual-servers-at_events#at_events) |  
| [{{site.data.keyword.baremetal_long}} ](/docs/bare-metal?topic=bare-metal-about-bm#about-bm) | {{site.data.keyword.baremetal_short}} sind physische Single-Tenant-Server, die Ihnen Leistung und Kontrolle mit maschinennahem Zugriff auf die Hardwareressourcen bereitstellen. | [Von {{site.data.keyword.baremetal_short}} generierte Ereignisse](/docs/bare-metal?topic=bare-metal-bm-at-events#bm-at-events) | 
{: caption="Liste der Infrastrukturservices, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden" caption-side="top"} 




## Serverunabhängige Services für Datenverarbeitung
{: #serverless}

Die folgende Tabelle enthält eine Auflistung von serverunabhängigen Datenverarbeitungsservices, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden:

| Service     | Beschreibung | {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse |
|-------------|-------------|-------------|
| [{{site.data.keyword.openwhisk_short}}](/docs/openwhisk?topic=cloud-functions-getting_started) | {{site.data.keyword.openwhisk_short}} ist eine auf Apache OpenWhisk basierende mehrsprachige FaaS-Programmierplattform (Functions as a Service), mit der Sie schlanken `Code, sogenannte Aktionen`, erstellen können. | [Von {{site.data.keyword.openwhisk_short}} generierte Ereignisse](/docs/openwhisk?topic=cloud-functions-activity_tracker#activity_tracker) |
{: caption="Liste der serverunabhängigen Datenverarbeitungsservices, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden" caption-side="top"} 



## Plattform-Container-Services
{: #ikcs}

Der {{site.data.keyword.containershort_notm}} generiert zwei Typen von {{site.data.keyword.cloudaccesstrailshort}}-Ereignissen:

* **Clusterverwaltungsereignisse**
    
    * Diese Ereignisse werden automatisch generiert.
    * Diese Ereignisse werden automatisch an {{site.data.keyword.cloudaccesstrailshort}} weitergeleitet.
    * Sie können diese Ereignisse über die {{site.data.keyword.cloudaccesstrailshort}}-**Kontodomäne** anzeigen. 

* **Prüfereignisse des Kubernetes-API-Servers**

    * Diese Ereignisse werden automatisch generiert.
    * Sie müssen Ihren Cluster so konfigurieren, dass er diese Ereignisse an den {{site.data.keyword.cloudaccesstrailshort}}-Service weiterleitet.
    * Sie können Ihren Cluster so konfigurieren, dass er Ereignisse an die {{site.data.keyword.cloudaccesstrailshort}}-**Kontodomäne** oder an eine **Bereichsdomäne** (Spacedomäne) sendet. Weitere Informationen finden Sie in [Prüfprotokolle senden](/docs/containers?topic=containers-health#api_forward).

Die folgende Tabelle enthält eine Auflistung von Services der Containerplattform, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden:

| Service     | Beschreibung | {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse |
|-------------|-------------|-------------|
| [{{site.data.keyword.containerlong_notm}}: Clusterverwaltungsereignisse](/docs/containers?topic=containers-getting-started#getting-started)| Diese Ereignisse liefern Meldungen zu Aktionen wie Erstellen, Löschen oder Aktualisieren von Clustern. | [Clusterverwaltungsereignisse ](/docs/containers?topic=containers-at_events#cluster-events) |  
| [{{site.data.keyword.containerlong_notm}}: API-Server-Prüfereignisse](/docs/containers?topic=containers-getting-started#getting-started)| Prüfereignisse des Kubernetes-API-Servers liefern chronologische Informationen zu der Abfolge von Aktivitäten, die einen Cluster betreffen. Jede Aktion generiert ein Ereignis. | [Prüfereignisse des Kubernetes-API-Servers](/docs/containers?topic=containers-at_events#kube-events) |
| [{{site.data.keyword.registrylong_notm}}](/docs/services/Registry?topic=registry-registry_overview#registry_overview) | Mit dem {{site.data.keyword.registrylong_notm}}-Service können Sie private Docker-Images in einer hoch verfügbaren und skalierbaren Architektur speichern und auf diese zugreifen. | [Bei der Interaktion mit {{site.data.keyword.registrylong_notm}} generierte Ereignisse](/docs/services/Registry?topic=registry-at_events#at_events) | 
{: caption="Containerereignisse" caption-side="top"} 



## Cloud Foundry-Anwendungen für die Plattform
{: #platform_cfapps}

Die Ereignisse, die von Cloud Foundry-Anwendungen an {{site.data.keyword.cloudaccesstrailshort}} gesendet werden, werden im Antwortbereich von `GET /v2/events` unter dem Hauptteil aufgelistet. Im Feld *Type* werden alle Aktionen aufgeführt, bei denen ein Ereignis generiert wird. Weitere Informationen finden Sie in [API für Ereignisse![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://apidocs.cloudfoundry.org/270/events/list_all_events.html){:new_window}.


## Zentrale integrierte Services für die Plattform
{: #platform_core_integrated}

Die zentralen Services der Plattform generieren {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse, die Sie über die **Kontodomäne** von {{site.data.keyword.cloudaccesstrailshort}} anzeigen können.

Die folgende Tabelle enthält eine Auflistung von zentralen Services der Plattform, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden:

| Service     | Beschreibung | {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse |
|-------------|-------------|-------------|
| [Bereitstellen und Verwalten von Katalogservices für Ressourcen, die von {{site.data.keyword.iamshort}} (IAM) verwaltet werden](/docs/overview?topic=overview-ui#catalogcreate) | Sie können eine Serviceinstanz bereitstellen, eine Serviceinstanz umbenennen, den Plan für eine Serviceinstanz ändern und eine Serviceinstanz entfernen. | [Bei der Interaktion mit den Katalogservices generierte Ereignisse](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_rc#at_events_rc) |  
| [Bereitstellen und Verwalten von Katalogservices, die an einen Cloud Foundry-Bereich (Space) gebunden sind](/docs/overview?topic=overview-ui#catalogcreate)| Sie können eine Serviceinstanz bereitstellen, eine Serviceinstanz umbenennen, den Plan für eine Serviceinstanz ändern und eine Serviceinstanz entfernen. </br>Diese Ereignisse werden für Services generiert, die in einem CF-Bereich bereitgestellt werden. | [Bei der Interaktion mit den Katalogservices generierte Ereignisse](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-cf#cf_catalog) |  
| [Verwalten eines Kontos](/docs/account?topic=account-accounts#accounts) | Sie können sich für ein {{site.data.keyword.IBM_notm}} Konto anmelden, indem Sie eine vorhandene IBMid verwenden, eine neue IBMid erstellen oder eine föderierte ID benutzen. | [Bei der Verwaltung eines Kontos generierte Ereignisse](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_acc_mgt#at_events_acc_mgt_account) |
| [Verwalten von Benutzern](/docs/iam?topic=iam-iamuserinv#iamusermanage) | Sie können Benutzer übergreifend über die Konten oder Organisationen, deren Eigner Sie sind oder die Sie verwalten, anzeigen und verwalten.  | [Bei der Verwaltung von Benutzern generierte Ereignisse](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_acc_mgt#at_events_acc_mgt_users) |
| [Verwalten von Organisationen](/docs/account?topic=account-orgsspacesusers#orgsspacesusers) | Als Kontoeigner können Sie Organisationen zum Account hinzufügen und verwalten. | [Bei der Verwaltung von Organisationen generierte Ereignisse](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_acc_mgt#at_events_acc_mgt_org) |
{: caption="Liste der zentralen Aktionen für die Plattform" caption-side="top"} 


## Plattformdatenbankservices
{: #database}

Die folgende Tabelle enthält eine Auflistung von Datenbankservices, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden:

| Service     | Beschreibung | {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse |
|-------------|-------------|----------------------------------------------------|
| [{{site.data.keyword.databases-for-postgresql_full_notm}}](/docs/services/databases-for-postgresql?topic=databases-for-postgresql-about#about) | {{site.data.keyword.databases-for-postgresql_full_notm}} ist ein verwalteter PostgreSQL-Service, der in der {{site.data.keyword.cloud_notm}} gehostet wird und mit anderen {{site.data.keyword.cloud_notm}}-Services integriert ist. | [Von {{site.data.keyword.databases-for-postgresql_full_notm}} generierte Ereignisse](/docs/services/databases-for-postgresql?topic=databases-for-postgresql-activity-tracker#activity-tracker) |
| [{{site.data.keyword.databases-for-redis_full_notm}}](/docs/services/databases-for-redis?topic=databases-for-redis-about#about-databases-for-redis) | {{site.data.keyword.databases-for-redis_full_notm}} ist ein verwalteter Service, der in der {{site.data.keyword.cloud_notm}} gehostet wird und mit anderen {{site.data.keyword.cloud_notm}}-Services integriert ist.  | [Von {{site.data.keyword.databases-for-redis_full_notm}} generierte Ereignisse](/docs/services/databases-for-redis?topic=databases-for-redis-activity-tracker-integration#activity-tracker-integration) |
| [{{site.data.keyword.sqlquery_short}}](/docs/services/sql-query?topic=sql-query-overview#overview) | Mit dem {{site.data.keyword.sqlquery_short}}-Service können Sie SQL-Abfragen (d. h. Anweisungen vom Typ SELECT) zum Analysieren, Transformieren oder Bereinigen rechteckiger Daten ausführen. | [Von {{site.data.keyword.sqlquery_short}} generierte Ereignisse](/docs/services/sql-query?topic=sql-query-activitytracker#activity-tracker-events) |  
| [{{site.data.keyword.databases-for-etcd_full_notm}}](/docs/services/databases-for-etcd?topic=databases-for-etcd-about#about-databases-for-etcd) | {{site.data.keyword.databases-for-etcd_full_notm}} ist ein verwalteter etcd-Service, der in der {{site.data.keyword.cloud_notm}} gehostet wird und mit anderen {{site.data.keyword.cloud_notm}}-Services integriert ist. | [Von {{site.data.keyword.databases-for-etcd_full_notm}} generierte Ereignisse](/docs/services/databases-for-etcd?topic=databases-for-etcd-activity-tracker#activity-tracker-integration) |
| [{{site.data.keyword.databases-for-elasticsearch_full_notm}}](/docs/services/databases-for-elasticsearch?topic=databases-for-elasticsearch-about#about-databases-for-elasticsearch) | {{site.data.keyword.databases-for-elasticsearch_full_notm}} ist ein verwalteter Elasticsearch-Service, der in der {{site.data.keyword.cloud_notm}} gehostet wird und mit anderen {{site.data.keyword.cloud_notm}}-Services integriert ist. | [Von {{site.data.keyword.databases-for-elasticsearch_full_notm}} generierte Ereignisse](/docs/services/databases-for-elasticsearch?topic=databases-for-elasticsearch-activity-tracker#activity-tracker-integration) |
| [{{site.data.keyword.messages-for-rabbitmq_full_notm}}](/docs/services/messages-for-rabbitmq?topic=messages-for-rabbitmq-about#about-messages-for-rabbitmq)  | {{site.data.keyword.messages-for-rabbitmq_full_notm}} ist ein verwalteter RabbitMQ-Service, der in der {{site.data.keyword.cloud_notm}} gehostet wird und mit anderen {{site.data.keyword.cloud_notm}}-Services integriert ist.   | [Von {{site.data.keyword.messages-for-rabbitmq_full_notm}} generierte Ereignisse](/docs/services/messages-for-rabbitmq?topic=messages-for-rabbitmq-activity-tracker#activity-tracker-integration) |
{: caption="Liste der Datenbankservices, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden" caption-side="top"} 




## Plattformentwicklertools
{: #devops}

Die folgende Tabelle enthält eine Auflistung von DevOps-Services, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden:

| Service     | Beschreibung | {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse |
|-------------|-------------|-------------|
| [{{site.data.keyword.DRA_short}}](/docs/apps?topic=creating-apps-insights-overview) | {{site.data.keyword.DRA_short}} ist eine Integration in den offenen Toolchainkatalog von {{site.data.keyword.cloud_notm}}. | [Von {{site.data.keyword.DRA_short}} generierte Ereignisse](/docs/apps?topic=creating-apps-at_events) |
| [{{site.data.keyword.contdelivery_short}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-getting-started) | Mit {{site.data.keyword.contdelivery_short}} können Sie Anwendungen mithilfe von DevOps-Verfahren und branchenführenden Tools erstellen, testen und bereitstellen. | [Von {{site.data.keyword.contdelivery_short}} generierte Ereignisse](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-at_events) |
| [{{site.data.keyword.GlobalizationPipeline_short}}](/docs/services/GlobalizationPipeline?topic=GlobalizationPipeline-globalizationpipeline#globalizationpipeline) | Ermöglicht es App-Entwicklern, übersetzte Anwendungen schnell für globale Kunden freizugeben. | [Von {{site.data.keyword.GlobalizationPipeline_short}} generierte Ereignisse](/docs/services/GlobalizationPipeline?topic=GlobalizationPipeline-gpat_events#gpat_events)|
{: caption="Liste der Entwicklertools, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden" caption-side="top"} 



## Integrierte Entwicklerservices für die Plattform
{: #integrated_dev_svcs}

In der folgenden Tabelle sind Cloud-Services aufgelistet, die Sie zum Entwickeln von Apps und Senden von Ereignissen an {{site.data.keyword.cloudaccesstrailshort}} verwenden können:

| Service     | Beschreibung | {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse |
|-------------|-------------|-------------|
| [{{site.data.keyword.dev_console}}](/docs/apps?topic=creating-apps-getting-started) | In {{site.data.keyword.cloud_notm}} können Sie auf Unternehmen abgestimmte Mobile- und Webanwendungen erstellen und die Vorteile von Clouderweiterungen nutzen, die {{site.data.keyword.cloud_notm}} per Hosting bereitstellt. Mit der Konsole und den Befehlszeilentools von {{site.data.keyword.cloud_notm}} können Sie Ihre Apps erstellen, ausführen und bereitstellen. Danach können Sie mit dem {{site.data.keyword.dev_console}} unter Verwendung eines Starter-Kits eine App erstellen. | [Von {{site.data.keyword.dev_console}} generierte Ereignisse](/docs/apps?topic=creating-apps-at_events#at_events) |
| [{{site.data.keyword.mobilepushshort}}](/docs/services/mobilepush?topic=mobile-pushnotification-overview-push#overview-push)| Sie können den {{site.data.keyword.mobilepushshort}}-Service verwenden, um Benachrichtigungen an mobile Geräte und Browser zu senden. Benachrichtigungen können an alle Anwendungsbenutzer gerichtet werden oder bei Verwendung von Tags eine bestimmte Gruppe von Benutzern und Geräten zum Ziel haben. Für jede Nachricht, die Sie an den Service übergeben, erhält die Zielgruppe eine Benachrichtigung. | [Von {{site.data.keyword.mobilepushshort}} generierte Ereignisse](/docs/services/mobilepush?topic=mobile-pushnotification-push_activity_tracker#push_activity_tracker) |  
{: caption="Liste der Web- und Mobile Cloud-Services, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden" caption-side="top"} 



## Integrierte Sicherheitsservices für die Plattform
{: #platform_integrated_security}

Die integrierten Sicherheitsservices generieren {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse, die Sie über die **Kontodomäne** von {{site.data.keyword.cloudaccesstrailshort}} anzeigen können.


Die folgende Tabelle enthält eine Auflistung von Services der zentralen Sicherheitsplattform, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden:

| Service     | Beschreibung | {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse |
|-------------|-------------|-------------|
| [Anmelden bei {{site.data.keyword.cloud_notm}}](/docs/iam?topic=iam-iamoverview#iamoverview)| Zum Anmelden bei {{site.data.keyword.cloud_notm}} können Sie ein Kennwort, einen API-Schlüssel, einen Berechtigungscode oder einen Kenncode verwenden. Als föderierter Benutzer können Sie sich über die Befehlszeilenschnittstelle (CLI) mit einem einmaligen Kenncode oder einem API-Schlüssel anmelden. | [Bei der Anmeldung eines Benutzers oder einer App bei {{site.data.keyword.cloud_notm}} generierte Ereignisse](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_login) |
| [Verwalten des Cloud Foundry-Zugriffs für einen Kontobenutzer](/docs/iam?topic=iam-mngcf#mngcf) | Sie können Benutzern im Konto Cloud Foundry-Berechtigungen (CF) erteilen, solche Berechtigungen widerrufen und entsprechende Berechtigungen aktualisieren. | [Bei der Verwaltung von CF-Rollen im Konto generierte Ereignisse](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-cf#cf_cfroles) |
| [{{site.data.keyword.iamlong}} (IAM)](/docs/iam?topic=iam-userroles#userroles) | Mit IAM können Sie Benutzer und Rollen für alle Plattform- und Infrastrukturservices von {{site.data.keyword.cloud_notm}} verwalten. | [Bei der Verwaltung von IAM-Richtlinien generierte Ereignisse](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_policies) |
| [Verwalten von Plattform-API-Schlüsseln](/docs/iam?topic=iam-manapikey#platform-api-keys) | In {{site.data.keyword.IBM_notm}} können Sie Plattform-API-Schlüssel definieren, die einem Benutzer oder einer Service-ID zugeordnet sind. | [Bei der Verwaltung von Plattform-API-Schlüsseln generierte Ereignisse](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_apikeys) |
| [Verwalten von Service-IDs](/docs/iam?topic=iam-serviceids#serviceids) | Sie können Service-IDs auf Kontoebene in {{site.data.keyword.IBM_notm}} Cloud definieren. | [Bei der Verwaltung von Service-IDs generierte Ereignisse](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_serviceids) |
| [Verwalten von Zugriffsgruppen](/docs/iam?topic=iam-groups#groups) | Sie können Zugriffsgruppen definieren, um eine Gruppe von Benutzern und Service-IDs in einer einzigen Entität zu organisieren, die Ihnen das Zuweisen von Berechtigungen erleichtert. | [Bei der Verwaltung von Zugriffsgruppen generierte Ereignisse](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_access) |
{: caption="Liste der zentralen Services für die Sicherheitsplattform" caption-side="top"} 


## Plattformintegrationsservices
{: #integration}

Die folgende Tabelle enthält eine Auflistung von Integrationsservices, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden:

| Service     | Beschreibung | {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse |
|-------------|-------------|-------------|
| [{{site.data.keyword.messagehub}}](/docs/services/EventStreams?topic=eventstreams-about#about)| {{site.data.keyword.messagehub}} ist ein Nachrichtenbus mit hohem Durchsatz, der mit Apache Kafka erstellt wurde. Er ist für die Aufnahme von Ereignissen in {{site.data.keyword.IBM_notm}} und die Verteilung des Ereignisstroms zwischen Ihren Services und Anwendungen optimiert. | [Von {{site.data.keyword.messagehub}} generierte Ereignisse](/docs/services/EventStreams?topic=eventstreams-at_events#at_events) |  
{: caption="Liste der Integrations-Cloud-Services, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden" caption-side="top"} 



## Plattformnetzservices
{: #network}

Die folgende Tabelle enthält eine Auflistung von Cloud-Netzservices, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden:

| Service     | Beschreibung | {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse |
|-------------|-------------|-------------|
| [IBM Cloud Internet Services (CIS)](/docs/infrastructure/cis?topic=cis-about-ibm-cloud-internet-services-cis#about-ibm-cloud-internet-services-cis)| IBM Cloud Internet Services (CIS) bietet einen schnellen, hochleistungsfähigen, zuverlässigen und sicheren Internet-Service. | [Von IBM Cloud Internet Services generierte Ereignisse](/docs/infrastructure/cis?topic=cis-at_events#at_events) |  
{: caption="Liste der Cloud-Netzservices, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden" caption-side="top"} 



## Plattformsicherheitsservices
{: #security}

Die folgende Tabelle enthält eine Auflistung von Cloud-Services für Sicherheit, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden:


| Service     | Beschreibung | {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse |
|-------------|-------------|-------------|
| [{{site.data.keyword.cloudaccesstraillong_notm}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov)| Mit dem {{site.data.keyword.cloudaccesstrailshort}}-Service können Sie {{site.data.keyword.cloudaccesstraillong_notm}} überwachen. | [Vom {{site.data.keyword.cloudaccesstraillong_notm}}-Service generierte Ereignisse](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-downloading_events#events) |  
| [{{site.data.keyword.appid_full_notm}}](/docs/services/appid?topic=appid-about#about) | Mit {{site.data.keyword.appid_short}} können Sie Authentifizierung zu Ihren mobilen Apps und Web-Apps hinzufügen und Ihre Back-End-Ressourcen schützen. | [Vom {{site.data.keyword.appid_short}}-Service generierte Ereignisse](/docs/services/appid?topic=appid-at-events#at-events) |
| [{{site.data.keyword.cloudcerts_full_notm}}](/docs/services/certificate-manager?topic=certificate-manager-about-certificate-manager#about-certificate-manager) | Mit {{site.data.keyword.cloudcerts_short}} können Sie die SSL-Zertifikate für Ihre {{site.data.keyword.cloud_notm}}-basierten Apps und Services verwalten.  | [Vom {{site.data.keyword.cloudcerts_short}}-Service generierte Ereignisse](/docs/services/certificate-manager?topic=certificate-manager-at_events#at_events) |
| [{{site.data.keyword.keymanagementservicelong}}](/docs/services/key-protect?topic=key-protect-getting-started-tutorial#getting-started-with-key-protect) | Mit dem {{site.data.keyword.keymanagementserviceshort}}-Service können Sie verschlüsselte Schlüssel für Apps in der gesamten {{site.data.keyword.cloud_notm}} bereitstellen. | [Vom {{site.data.keyword.keymanagementserviceshort}}-Service generierte Ereignisse](/docs/services/key-protect?topic=key-protect-activity-tracker-events#activity-tracker-events) |
| [{{site.data.keyword.security-advisor_short}}](/docs/services/security-advisor?topic=security-advisor-about#about) | Mit {{site.data.keyword.security-advisor_short}} können Sie die Sicherheit Ihrer {{site.data.keyword.cloud_notm}}-Apps und -Workloads überwachen.   | [Vom {{site.data.keyword.security-advisor_short}}-Service generierte Ereignisse](/docs/services/security-advisor?topic=security-advisor-at_events#at_events) |
{: caption="Liste der Cloud-Services für Sicherheit, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden" caption-side="top"} 


## Plattformspeicherservices
{: #storage}

Die folgende Tabelle enthält eine Auflistung von Cloud-Speicherservices, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden:

| Service     | Beschreibung | {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse |
|-------------|-------------|-------------|
| [{{site.data.keyword.cos_full_notm}}](/docs/services/cloud-object-storage?topic=cloud-object-storage-about#about-ibm-cloud-object-storage)| Mit {{site.data.keyword.cos_full_notm}} können Sie Daten in {{site.data.keyword.cloud_notm}} speichern. Daten werden verschlüsselt und über mehrere geografische Standorte hinweg verteilt gespeichert. Der Zugriff auf die Daten erfolgt mit einer REST-API über HTTP.   | [Von {{site.data.keyword.cos_full_notm}} generierte Ereignisse](/docs/services/cloud-object-storage?topic=cloud-object-storage-at-events) |  
{: caption="Liste der Cloud-Speicherservices, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden" caption-side="top"} 



## Watson-Datenservices für die Plattform
{: #watson_data}


| Service     | Beschreibung | {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse |
|-------------|-------------|-------------|
| [Watson Studio](https://dataplatform.cloud.ibm.com/docs/content/wsj/getting-started/overview-ws.html) | Watson Studio stellt die Umgebung und Tools bereit, um Ihre Geschäftsprobleme durch kollaboratives Arbeiten mit Daten zu lösen. Sie können die Tools auswählen, die Sie benötigen, um Daten zu analysieren und zu visualisieren, um Daten zu bereinigen und zu modellieren, um Streaming-Daten einzupflegen oder um Modelle für maschinelles Lernen zu erstellen, zu trainieren und bereitzustellen. | [Von Watson Studio generierte Ereignisse](https://dataplatform.cloud.ibm.com/docs/content/wsj/admin/at-events.html#ws) |  
| [Watson Machine Learning](https://dataplatform.cloud.ibm.com/docs/content/wsj/analyze-data/ml-overview.html)| Mit Watson Machine Learning können Sie fortgeschrittene Analysemodelle erstellen, die Sie mit Ihren eigenen Daten trainieren und für die Verwendung in Anwendungen bereitstellen können. | [Von Watson Machine Learning generierte Ereignisse](https://dataplatform.cloud.ibm.com/docs/content/wsj/admin/at-events.html#wml) | 
| [Watson Knowledge Catalog](https://dataplatform.cloud.ibm.com/docs/content/wsj/catalog/overview-wkc.html)| Watson Knowledge Catalog stellt eine sichere Plattform für die Unternehmenskatalogverwaltung bereit, die durch ein Framework für Datenrichtlinien gestützt wird. Ein Katalog verbindet Daten und Wissen mit den Personen, die sie verwenden müssen. Das Framework für Datenrichtlinien stellt sicher, dass der Datenzugriff mit Ihren Geschäftsregeln konform ist. | [Von Watson Knowledge Catalog generierte Ereignisse](https://dataplatform.cloud.ibm.com/docs/content/wsj/admin/at-events.html#wkc) |  
{: caption="Liste der Watson-Cloud-Datenservices, die Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden" caption-side="top"} 

