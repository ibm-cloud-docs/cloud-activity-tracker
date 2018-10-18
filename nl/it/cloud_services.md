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



# Servizi cloud
{: #cloud_services}

Utilizza il servizio {{site.data.keyword.cloudaccesstraillong}} per monitorare le attività avviate dall'utente che modificano lo stato di uno dei seguenti servizi nel cloud {{site.data.keyword.IBM_notm}}:
{:shortdesc}

**Nota:** per ottenere le informazioni sulle regioni in cui è disponibile un servizio in {{site.data.keyword.Bluemix_notm}}, consulta [Servizi per regione](/docs/resources/services_region.html#services_region).


## Infrastruttura: servizi Virtual Server
{: #vs}

La seguente tabella elenca i servizi Virtual Server che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}:

| Servizio     | Descrizione |Eventi {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.BluVirtServers_short}} ](/docs/vsi/vsi_about.html#about-virtual-servers)|{{site.data.keyword.BluVirtServers}} sono server virtuali scalabili che vengono acquistati con i core dedicati e le allocazioni di memoria. Sono una grande opzione se stai cercando risorse di calcolo, che possono essere aggiunte in pochi minuti, con l'accesso alle funzioni come i template dell'immagine. | [Eventi generati da {{site.data.keyword.BluVirtServers_short}}](/docs/vsi/vsi_activity_tracker_events.html#at_events) |  
{: caption="Elenco dei servizi Virtual Server che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 


## Piattaforma: Servizi di analisi
{: #analytics}

La seguente tabella elenca i servizi di analisi che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}:

| Servizio     | Descrizione |Eventi {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.streaminganalyticsfull}} ](/docs/services/StreamingAnalytics/index.html#gettingstarted)|{{site.data.keyword.streaminganalyticsfull}} è fornito da {{site.data.keyword.streamsshort}}, una piattaforma di analisi avanzata che puoi utilizzare per inserire, analizzare e correlare le informazioni come arrivano da diversi tipi di origini dati in tempo reale. | [Eventi generati da {{site.data.keyword.streaminganalyticsshort}} ]() |  
{: caption="Elenco dei servizi cloud di analisi che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 


## Piattaforma: Servizi del contenitore
{: #ikcs}

{{site.data.keyword.containershort_notm}} genera due tipi di eventi {{site.data.keyword.cloudaccesstrailshort}}:

* **Eventi di gestione del cluster**: 
    
    * Questi eventi sono generati automaticamente. 
    * Questi eventi sono inoltrati automaticamente a {{site.data.keyword.cloudaccesstrailshort}}.
    * Puoi visualizzare questi eventi tramite il **dominio dell'account** {{site.data.keyword.cloudaccesstrailshort}}. 

* **Eventi di controllo del server API Kubernetes**: 

    * Questi eventi sono generati automaticamente. 
    * Devi configurare il tuo cluster per inoltrare questi eventi al servizio {{site.data.keyword.cloudaccesstrailshort}}.
    * Puoi configurare il tuo cluster per inoltrare gli eventi al **dominio dell'account** o al **dominio dello spazio** {{site.data.keyword.cloudaccesstrailshort}}. Per ulteriori informazioni, vedi [Invio dei log di controllo](/docs/containers/cs_health.html#api_forward).

La seguente tabella elenca i servizi della piattaforma del contenitore che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}:

| Servizio     | Descrizione |Eventi {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.containerlong_notm}}: eventi di gestione del cluster](/docs/containers/container_index.html#container_index)| Questi eventi si riferiscono ad azioni come la creazione, l'eliminazione o l'aggiornamento del cluster. | [Eventi di gestione del cluster ]() |  
| [{{site.data.keyword.containerlong_notm}}: eventi di controllo del server API](/docs/containers/container_index.html#container_index)| Gli eventi di controllo del server API Kubernetes forniscono le informazioni cronologiche sulla sequenza delle attività che influenza un cluster. Ogni azione genera un evento | [Eventi di controllo del server API Kubernetes](/docs/containers/cs_at_events.html#at_events) |
| [{{site.data.keyword.registrylong_notm}}](/docs/services/Registry/registry_overview.html#registry_overview) | Puoi utilizzare il servizio {{site.data.keyword.registrylong_notm}} per archiviare e accedere alle immagini Docker private in un'architettura altamente disponibile e scalabile. | [Eventi generati quando interagiscono con {{site.data.keyword.registrylong_notm}}](/docs/services/Registry/registry_at_events.html#at_events) | 
{: caption="Eventi del contenitore" caption-side="top"} 



## Piattaforma: applicazioni Cloud Foundry
{: #platform_cfapps}

Gli eventi che vengono inviati dalle applicazioni Cloud Foundry a {{site.data.keyword.cloudaccesstrailshort}} sono elencati nell'area di risposta `GET /v2/events`, sotto la sezione del corpo. Il campo *Type* elenca tutte le azioni che generano un evento. Per ulteriori informazioni, vedi [Events API](https://apidocs.cloudfoundry.org/270/events/list_all_events.html).


## Piattaforma: servizi integrati principali
{: #platform_core_integrated}

I servizi della piattaforma principali generano gli eventi {{site.data.keyword.cloudaccesstrailshort}} che puoi visualizzare attraverso il **dominio dell'account** {{site.data.keyword.cloudaccesstrailshort}}.

La seguente tabella elenca i servizi della piattaforma principali che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}:

| Servizio     | Descrizione |Eventi {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [Provisioning e gestione dei servizi del catalogo per le risorse gestite da {{site.data.keyword.iamshort}} (IAM)](/docs/overview/ui.html#catalogcreate) | Puoi eseguire il provisioning, ridenominare, modificare il piano e rimuovere un'istanza del servizio. | [Eventi generati quando interagiscono con i servizi del catalogo ](/docs/services/cloud-activity-tracker/services/at_events_rc.html#at_events) |  
| [Provisioning e gestione dei servizi del catalogo associati a uno spazio Cloud Foundry](/docs/overview/ui.html#catalogcreate)| Puoi eseguire il provisioning, ridenominare, modificare il piano e rimuovere un'istanza del servizio. </br>Questi eventi vengono generati per i servizi di cui viene eseguito il provisioning in uno spazio CF. | [Eventi generati quando interagiscono con i servizi del catalogo ](/docs/services/cloud-activity-tracker/services/at_events_cf.html#catalog) |  
| [Gestione di un account](/docs/account/index.html#accounts) | Puoi registrati a un account {{site.data.keyword.IBM_notm}} utilizzando un ID IBM esistente, creandone uno nuovo o utilizzando un ID federato. | [Eventi generati quando gestisci un account](/docs/services/cloud-activity-tracker/services/at_events_acc_mgt.html#account) |
| [Gestione di utenti](/docs/iam/iamusermanage.html#iamusermanage) |Puoi visualizzare e gestire gli utenti nell'account o nelle organizzazioni di cui sei proprietario o che gestisci.  | [Eventi generati quando gestisci gli utenti ](/docs/services/cloud-activity-tracker/services/at_events_acc_mgt.html#users) |
| [Gestione di organizzazioni](/docs/account/orgs_spaces.html#orgsspacesusers) | Come proprietario di un account, puoi aggiungere e gestire le organizzazioni all'account. | [Eventi generati quando gestisci le organizzazioni ](/docs/services/cloud-activity-tracker/services/at_events_acc_mgt.html#org) |
{: caption="Elenco delle azioni della piattaforma principali" caption-side="top"} 


## Piattaforma: servizi del database
{: #database}

La seguente tabella elenca i servizi del database che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}:

| Servizio     | Descrizione |Eventi {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.sqlquery_short}}](/docs/services/sql-query/sql-query.html#overview)| Puoi utilizzare il servizio {{site.data.keyword.sqlquery_short}} per eseguire le query SQL (cioè, le istruzioni SELECT) per analizzare, trasformare o ripulire i dati rettangolari. | [Eventi generati da {{site.data.keyword.sqlquery_short}} ](/docs/services/sql-query/activity.html#activity-tracker-events) |  
{: caption="Elenco dei servizi cloud del database che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 


## Piattaforma: servizi dello sviluppatore integrati
{: #integrated_dev_svcs}

La seguente tabella elenca i servizi cloud che puoi utilizzare per sviluppare le applicazioni e inviare gli eventi a {{site.data.keyword.cloudaccesstrailshort}}:

| Servizio     | Descrizione |Eventi {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.dev_console}}](/docs/apps/index.html#create) | In {{site.data.keyword.Bluemix_notm}}, puoi creare applicazioni mobili e web a livello aziendale e trarre vantaggio dalle estensioni cloud ospitate da {{site.data.keyword.Bluemix_notm}}. Puoi utilizzare la console {{site.data.keyword.Bluemix_notm}} e gli strumenti della riga di comando per creare, eseguire e distribuire le tue applicazioni. Puoi utilizzare la {{site.data.keyword.dev_console}} per creare un'applicazione utilizzando un kit starter. | [Eventi generati dalla {{site.data.keyword.dev_console}}](/docs/apps/at_events_devx.html#at_events) |
| [{{site.data.keyword.mobilepushshort}}](/docs/services/mobilepush/c_overview_push.html#overview-push)| Puoi utilizzare il servizio {{site.data.keyword.mobilepushshort}} per inviare le notifiche ai dispositivi mobili e ai browser. Le notifiche possono essere destinate a tutti gli utenti dell'applicazione oppure a uno specifico insieme di utenti e dispositivi facendo uso delle tag. Per ogni messaggio che invii al servizio, i destinatari previsti ricevono una notifica. | [Eventi generati da {{site.data.keyword.mobilepushshort}}](/docs/services/mobilepush/push_activity_tracker.html#push_activity_tracker) |  
{: caption="Elenco dei servizi cloud mobili e web che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Piattaforma: servizi di sicurezza integrati
{: #platform_integrated_security}

I servizi di sicurezza integrati generano gli eventi {{site.data.keyword.cloudaccesstrailshort}} che puoi visualizzare attraverso il **dominio dell'account** {{site.data.keyword.cloudaccesstrailshort}}.


La seguente tabella elenca i servizi della piattaforma di sicurezza principali che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}:

| Servizio     | Descrizione |Eventi {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [Accedi a {{site.data.keyword.Bluemix_notm}}](/docs/iam/quickstart.html#getstarted)| Puoi accedere a {{site.data.keyword.Bluemix_notm}} utilizzando una password, una chiave API, un codice di autorizzazione o un passcode. Come utente federato, puoi accedere all'interfaccia della riga di comando (CLI) utilizzando un passcode monouso o una chiave API. | [Eventi generati quando un utente o un'applicazione accede a {{site.data.keyword.Bluemix_notm}}](/docs/services/cloud-activity-tracker/services/at_events_iam.html#login) |
| [Gestione dell'accesso Cloud Foundry dell'utente dell'account](/docs/iam/mngcf.html#mngcf) | Puoi concedere, revocare e aggiornare le autorizzazioni Cloud Foundry (CF) agli utenti nell'account. | [Eventi generati durante la gestione dei ruoli CF nell'account](/docs/services/cloud-activity-tracker/services/at_events_cf.html#cfroles) |
| [{{site.data.keyword.iamlong}} (IAM)](/docs/iam/users_roles.html#userroles) |Puoi utilizzare IAM per gestire gli utenti e i ruoli nei servizi infrastruttura e piattaforma {{site.data.keyword.Bluemix_notm}}. | [Eventi generati quando gestisci le politiche IAM](/docs/services/cloud-activity-tracker/services/at_events_iam.html#policies) |
| [Gestione delle chiavi API della piattaforma](/docs/iam/apikeys.html#platform-api-keys) | Puoi definire le chiavi API in {{site.data.keyword.IBM_notm}} Cloud che sono associate a un utente o a un ID servizio. | [Eventi generati durante la gestione delle chiavi API della piattaforma](/docs/services/cloud-activity-tracker/services/at_events_iam.html#apikeys) |
| [Gestione degli ID servizio](/docs/iam/serviceid.html#serviceids) | Puoi definire gli ID servizio a livello dell'account in {{site.data.keyword.IBM_notm}} Cloud. | [Eventi generati durante la gestione degli ID servizio](/docs/services/cloud-activity-tracker/services/at_events_iam.html#serviceids) |
| [Gestione dei gruppi di accesso](/docs/iam/groups.html#groups) | Puoi definire i gruppi di accesso per organizzare una serie di utenti e ID servizio in una sola entità che ti rende facile assegnare le autorizzazioni. | [Eventi generati durante la gestione dei gruppi di accesso](/docs/services/cloud-activity-tracker/services/at_events_iam.html#access) |
{: caption="Elenco dei servizi della piattaforma di sicurezza principali" caption-side="top"} 


## Piattaforma: servizi di integrazione
{: #integration}

La seguente tabella elenca i servizi di integrazione che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}:

| Servizio     | Descrizione |Eventi {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.messagehub}}](/docs/services/MessageHub/messagehub010.html#about)| {{site.data.keyword.messagehub}} è un bus di messaggi di velocità elevata creato con Apache Kafka. È ottimizzato per l'inserimento di eventi in {{site.data.keyword.IBM_notm}} e la distribuzione del flusso di eventi tra i tuoi servizi e le tue applicazioni. | [Eventi generati da {{site.data.keyword.messagehub}} ](/docs/services/MessageHub/at-events.html#at_events) |  
{: caption="Elenco dei servizi cloud di integrazione che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Piattaforma: servizi di rete
{: #network}

La seguente tabella elenca i servizi di rete che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}:

| Servizio    | Descrizione | Eventi {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [IBM Cloud Internet Services (CIS)](/docs/infrastructure/cis/about.html#about-ibm-cloud-internet-services-cis-)| IBM Cloud Internet Services (CIS) fornisce un servizio internet sicuro, affidabile, ad elevate prestazioni e veloce. | [Eventi generati da IBM Cloud Internet Services](/docs/infrastructure/cis/at_events.html#at_events) |  
{: caption="Elenco dei servizi cloud di rete che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Piattaforma: servizi di sicurezza
{: #security}

La seguente tabella elenca i servizi di sicurezza che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}:


| Servizio     | Descrizione |Eventi {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.cloudaccesstraillong_notm}}](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#activity_tracker_ov)| Puoi utilizzare il servizio {{site.data.keyword.cloudaccesstrailshort}} per monitorare {{site.data.keyword.cloudaccesstraillong_notm}}. | [Eventi generati dal servizio {{site.data.keyword.cloudaccesstraillong_notm}}](/docs/services/cloud-activity-tracker/reference/events.html#events) |  
| [{{site.data.keyword.appid_full_notm}}](/docs/services/appid/about.html#about) | Puoi utilizzare {{site.data.keyword.appid_short}} per aggiungere l'autenticazione alle tue applicazioni mobili e web e per proteggere le risorse di backend. | [Eventi generati dal servizio {{site.data.keyword.appid_short}}](/docs/services/appid/iam.html#tracking) |
| [{{site.data.keyword.cloudcerts_full_notm}}](/docs/services/certificate-manager/about.html#about-certificate-manager) | Puoi utilizzare {{site.data.keyword.cloudcerts_short}} per gestire i certificati SSL per le tue applicazioni e i tuoi servizi basati su {{site.data.keyword.Bluemix_notm}}.  | [Eventi generati dal servizio {{site.data.keyword.cloudcerts_short}}](/docs/services/certificate-manager/at_events.html#at_events) |
| [{{site.data.keyword.keymanagementservicelong}}](/docs/services/key-protect/index.html#getting-started-with-key-protect) |Puoi utilizzare il servizio {{site.data.keyword.keymanagementserviceshort}} per eseguire il provisioning delle chiavi crittografate per le applicazioni in {{site.data.keyword.Bluemix_notm}}.| [Eventi generati dal servizio {{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect/at-events.html#at-events) |
{: caption="Elenco dei servizi cloud di sicurezza che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 


## Piattaforma: servizi di archiviazione
{: #storage}

La seguente tabella elenca i servizi di archiviazione che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}:

| Servizio     | Descrizione |Eventi {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.cos_full_notm}}](/docs/services/cloud-object-storage/about-cos.html#about-ibm-cloud-object-storage)| Puoi utilizzare {{site.data.keyword.cos_full_notm}} per archiviare i dati in {{site.data.keyword.Bluemix_notm}}. I dati vengono codificati e distribuiti in più ubicazioni geografiche e sono accessibili su HTTP utilizzando un'API REST.   | [Eventi generati da {{site.data.keyword.cos_full_notm}}](/docs/services/cloud-object-storage/basics/at.html#at_events) |  
{: caption="Elenco dei servizi cloud di archiviazione che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Piattaforma Watson: servizi di dati
{: #watson_data}


| Servizio     | Descrizione |Eventi {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [Watson Studio](https://dataplatform.cloud.ibm.com/docs/content/getting-started/overview-ws.html?context=analytics&linkInPage=true) | Watson Studio fornisce l'ambiente e gli strumenti per risolvere i tuoi problemi di business in modo collaborativo utilizzando i dati. Puoi scegliere gli strumenti di cui hai bisogno per analizzare e visualizzare i dati, per ripulire e modellare i dati, per inserire i dati di streaming, o per creare, preparare e distribuire i modelli di machine learning. | [Eventi generati da Watson Studio](https://dataplatform.cloud.ibm.com/docs/content/admin/at-events.html#ws) |  
| [Watson Machine Learning](https://dataplatform.cloud.ibm.com/docs/content/analyze-data/ml-overview.html?audience=dr&context=refinery)| Puoi utilizzare Watson Machine Learning per creare modelli analitici sofisticati, preparati con i tuoi dati, che puoi distribuire per l'utilizzo nelle applicazioni. | [Eventi generati da Watson Machine Learning](https://dataplatform.cloud.ibm.com/docs/content/admin/at-events.html#wml) | 
| [Watson Knowledge Catalog](https://dataplatform.cloud.ibm.com/docs/content/catalog/overview-wkc.html?audience=dr&context=refinery&linkInPage=true)| Watson Knowledge Catalog fornisce una piattaforma di gestione del catalogo aziendale sicura supportata da un framework della politica dei dati. Un catalogo collega i dati e le informazioni approfondite alle persone che hanno bisogno di utilizzarli. Il framework della politica dei dati garantisce che l'accesso ai dati sia conforme alle tue regole aziendali. | [Eventi generati da Watson Knowledge Catalog](https://dataplatform.cloud.ibm.com/docs/content/admin/at-events.html#wkc) |  
{: caption="Elenco dei servizi di dati cloud Watson che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 


