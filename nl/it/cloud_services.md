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



# Servizi cloud
{: #cloud_services}

Utilizza il servizio {{site.data.keyword.cloudaccesstraillong}} per monitorare le attività avviate dall'utente che modificano lo stato di uno dei seguenti servizi nel cloud {{site.data.keyword.IBM_notm}}:
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} è obsoleto. A partire dal 9 maggio 2019, non puoi eseguire il provisioning delle nuove istanze di {{site.data.keyword.cloudaccesstrailshort}}. Le istanze del piano Premium esistenti sono supportate fino al 30 settembre 2019. Per continuare a monitorare l'attività del tuo account {{site.data.keyword.cloud_notm}}, esegui il provisioning di un'istanza di [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}

**Nota:** per ottenere le informazioni sulle regioni in cui è disponibile un servizio in {{site.data.keyword.cloud_notm}}, consulta [Servizi per regione](/docs/resources?topic=resources-services_region#services_region).


## Calcolo dei servizi dell'infrastruttura
{: #infrastructure}

**Nota:** perché un utente generi degli eventi {{site.data.keyword.BluVirtServers_short}} e {{site.data.keyword.baremetal_short}} {{site.data.keyword.cloudaccesstrailshort}}, deve avere accesso alle risorse dell'infrastruttura nella console {{site.data.keyword.cloud_notm}}. Per ulteriori informazioni, vedi [Monitoraggio di {{site.data.keyword.BluVirtServers_short}} e dell'attività di {{site.data.keyword.baremetal_short}} con {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/tutorials?topic=cloud-activity-tracker-vsi#vsi).

La seguente tabella elenca i servizi dell'infrastruttura che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}:

| Servizio     | Descrizione | Eventi {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.BluVirtServers_short}} ](/docs/vsi?topic=virtual-servers-about-virtual-servers#about-virtual-servers)| {{site.data.keyword.BluVirtServers}} sono server virtuali scalabili che vengono acquistati con i core dedicati e le allocazioni di memoria. Sono una grande opzione se stai cercando risorse di calcolo, che possono essere aggiunte in pochi minuti, con l'accesso alle funzioni come i template dell'immagine.  | [Eventi generati da {{site.data.keyword.BluVirtServers_short}}](/docs/vsi?topic=virtual-servers-at_events#at_events) |  
| [{{site.data.keyword.baremetal_long}} ](/docs/bare-metal?topic=bare-metal-about-bm#about-bm) | {{site.data.keyword.baremetal_short}} sono server fisici a singolo tenant che ti forniscono prestazioni e controllo con un accesso di basso livello alle risorse hardware. | [Eventi generati da {{site.data.keyword.baremetal_short}}](/docs/bare-metal?topic=bare-metal-bm-at-events#bm-at-events) | 
{: caption="Elenco dei servizi dell'infrastruttura che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 




## Calcolo dei servizi senza server
{: #serverless}

La seguente tabella elenca i servizi di calcolo senza server che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}:

| Servizio     | Descrizione | Eventi {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.openwhisk_short}}](/docs/openwhisk?topic=cloud-functions-index#index) | {{site.data.keyword.openwhisk_short}} è una piattaforma di programmazione FaaS (Functions-as-a-Service) poliglotta basata su Apache OpenWhisk che puoi utilizzare per scrivere semplici `code called actions`. | [Eventi generati da {{site.data.keyword.openwhisk_short}}](/docs/openwhisk?topic=cloud-functions-activity_tracker#activity_tracker) |
{: caption="Elenco dei servizi di calcolo senza server che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Servizi di contenitore della piattaforma
{: #ikcs}

{{site.data.keyword.containershort_notm}} genera due tipi di eventi {{site.data.keyword.cloudaccesstrailshort}}:

* **Eventi di gestione del cluster**
    
    * Questi eventi sono generati automaticamente.
    * Questi eventi sono inoltrati automaticamente a {{site.data.keyword.cloudaccesstrailshort}}.
    * Puoi visualizzare questi eventi tramite il **dominio dell'account** {{site.data.keyword.cloudaccesstrailshort}}. 

* **Eventi di controllo del server API Kubernetes**

    * Questi eventi sono generati automaticamente.
    * Devi configurare il tuo cluster per inoltrare questi eventi al servizio {{site.data.keyword.cloudaccesstrailshort}}.
    * Puoi configurare il tuo cluster per inoltrare gli eventi al **dominio dell'account** o al **dominio dello spazio** {{site.data.keyword.cloudaccesstrailshort}}. Per ulteriori informazioni, vedi [Invio dei log di controllo](/docs/containers?topic=containers-health#api_forward).

La seguente tabella elenca i servizi della piattaforma del contenitore che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}:

| Servizio     | Descrizione | Eventi {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.containerlong_notm}}: eventi di gestione del cluster](/docs/containers?topic=containers-container_index#container_index)| Questi eventi si riferiscono ad azioni come la creazione, l'eliminazione o l'aggiornamento del cluster. | [Eventi di gestione del cluster ](/docs/containers?topic=containers-at_events#cluster-events) |  
| [{{site.data.keyword.containerlong_notm}}: eventi di controllo del server API](/docs/containers?topic=containers-container_index#container_index)| Gli eventi di controllo del server API Kubernetes forniscono le informazioni cronologiche sulla sequenza delle attività che influenza un cluster. Ogni azione genera un evento | [Eventi di controllo del server API Kubernetes](/docs/containers?topic=containers-at_events#kube-events) |
| [{{site.data.keyword.registrylong_notm}}](/docs/services/Registry?topic=registry-registry_overview#registry_overview) | Puoi utilizzare il servizio {{site.data.keyword.registrylong_notm}} per archiviare e accedere alle immagini Docker private in un'architettura altamente disponibile e scalabile. | [Eventi generati quando interagisci con {{site.data.keyword.registrylong_notm}}](/docs/services/Registry?topic=registry-at_events#at_events) | 
{: caption="Eventi del contenitore" caption-side="top"} 



## Applicazioni Cloud Foundry della piattaforma
{: #platform_cfapps}

Gli eventi che vengono inviati dalle applicazioni Cloud Foundry a {{site.data.keyword.cloudaccesstrailshort}} sono elencati nell'area di risposta `GET /v2/events`, sotto la sezione del corpo. Il campo *Type* elenca tutte le azioni che generano un evento. Per ulteriori informazioni, vedi [Events API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://apidocs.cloudfoundry.org/270/events/list_all_events.html){:new_window}.


## Servizi integrati principali della piattaforma
{: #platform_core_integrated}

I servizi della piattaforma principali generano gli eventi {{site.data.keyword.cloudaccesstrailshort}} che puoi visualizzare attraverso il **dominio dell'account** {{site.data.keyword.cloudaccesstrailshort}}.

La seguente tabella elenca i servizi della piattaforma principali che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}:

| Servizio     | Descrizione | Eventi {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [Provisioning e gestione dei servizi del catalogo per le risorse gestite da {{site.data.keyword.iamshort}} (IAM)](/docs/overview?topic=overview-ui#catalogcreate) | Puoi eseguire il provisioning, ridenominare, modificare il piano e rimuovere un'istanza del servizio. | [Eventi generati quando interagisci con i servizi del catalogo ](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_rc#at_events_rc) |  
| [Provisioning e gestione dei servizi del catalogo associati a uno spazio Cloud Foundry](/docs/overview?topic=overview-ui#catalogcreate)| Puoi eseguire il provisioning, ridenominare, modificare il piano e rimuovere un'istanza del servizio. </br>Questi eventi vengono generati per i servizi di cui viene eseguito il provisioning in uno spazio CF. | [Eventi generati quando interagisci con i servizi del catalogo ](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-cf#cf_catalog) |  
| [Gestione di un account](/docs/account?topic=account-accounts#accounts) | Puoi registrati a un account {{site.data.keyword.IBM_notm}} utilizzando un ID IBM esistente, creandone uno nuovo o utilizzando un ID federato. | [Eventi generati quando gestisci un account](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_acc_mgt#at_events_acc_mgt_account) |
| [Gestione di utenti](/docs/iam?topic=iam-iamuserinv#iamusermanage) | Puoi visualizzare e gestire gli utenti nell'account o nelle organizzazioni di cui sei proprietario o che gestisci.  | [Eventi generati quando gestisci gli utenti ](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_acc_mgt#at_events_acc_mgt_users) |
| [Gestione di organizzazioni](/docs/account?topic=account-orgsspacesusers#orgsspacesusers) | Come proprietario di un account, puoi aggiungere e gestire le organizzazioni all'account. | [Eventi generati quando gestisci le organizzazioni ](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_acc_mgt#at_events_acc_mgt_org) |
{: caption="Elenco delle azioni della piattaforma principali" caption-side="top"} 


## Servizi di database della piattaforma
{: #database}

La seguente tabella elenca i servizi di database che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}:

| Servizio     | Descrizione | Eventi {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|----------------------------------------------------|
| [{{site.data.keyword.databases-for-postgresql_full_notm}}](/docs/services/databases-for-postgresql?topic=databases-for-postgresql-about#about) | {{site.data.keyword.databases-for-postgresql_full_notm}} è un servizio PostgreSQL gestito ospitato in {{site.data.keyword.cloud_notm}} e integrato con altri servizi {{site.data.keyword.cloud_notm}}. | [Eventi generati da {{site.data.keyword.databases-for-postgresql_full_notm}}](/docs/services/databases-for-postgresql?topic=databases-for-postgresql-activity-tracker#activity-tracker) |
| [{{site.data.keyword.databases-for-redis_full_notm}}](/docs/services/databases-for-redis?topic=databases-for-redis-about#about-databases-for-redis) | {{site.data.keyword.databases-for-redis_full_notm}} è un servizio gestito ospitato in {{site.data.keyword.cloud_notm}} e integrato con altri servizi {{site.data.keyword.cloud_notm}}. | [Eventi generati da {{site.data.keyword.databases-for-redis_full_notm}} ](/docs/services/databases-for-redis?topic=databases-for-redis-activity-tracker-integration#activity-tracker-integration) |
| [{{site.data.keyword.sqlquery_short}}](/docs/services/sql-query?topic=sql-query-overview#overview) | Puoi utilizzare il servizio {{site.data.keyword.sqlquery_short}} per eseguire le query SQL (cioè, le istruzioni SELECT) per analizzare, trasformare o ripulire i dati rettangolari. | [Eventi generati da {{site.data.keyword.sqlquery_short}} ](/docs/services/sql-query?topic=sql-query-activitytracker#activity-tracker-events) |  
| [{{site.data.keyword.databases-for-etcd_full_notm}}](/docs/services/databases-for-etcd?topic=databases-for-etcd-about#about-databases-for-etcd) | {{site.data.keyword.databases-for-etcd_full_notm}} è un servizio etcd gestito ospitato in {{site.data.keyword.cloud_notm}} e integrato con altri servizi {{site.data.keyword.cloud_notm}}. | [Eventi generati da {{site.data.keyword.databases-for-etcd_full_notm}}](/docs/services/databases-for-etcd?topic=databases-for-etcd-activity-tracker#activity-tracker-integration) |
| [{{site.data.keyword.databases-for-elasticsearch_full_notm}}](/docs/services/databases-for-elasticsearch?topic=databases-for-elasticsearch-about#about-databases-for-elasticsearch) | {{site.data.keyword.databases-for-elasticsearch_full_notm}} è un servizio Elasticsearch gestito ospitato in {{site.data.keyword.cloud_notm}} e integrato con altri servizi {{site.data.keyword.cloud_notm}}. | [Eventi generati da {{site.data.keyword.databases-for-elasticsearch_full_notm}}](/docs/services/databases-for-elasticsearch?topic=databases-for-elasticsearch-activity-tracker#activity-tracker-integration) |
| [{{site.data.keyword.messages-for-rabbitmq_full_notm}}](/docs/services/messages-for-rabbitmq?topic=messages-for-rabbitmq-about#about-messages-for-rabbitmq)  | {{site.data.keyword.messages-for-rabbitmq_full_notm}} è un servizio RabbitMQ gestito ospitato in {{site.data.keyword.cloud_notm}} e integrato con altri servizi {{site.data.keyword.cloud_notm}}.   | [Eventi generati da {{site.data.keyword.messages-for-rabbitmq_full_notm}}](/docs/services/messages-for-rabbitmq?topic=messages-for-rabbitmq-activity-tracker#activity-tracker-integration) |
{: caption="Elenco dei servizi di database che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 




## Strumenti per gli sviluppatori della piattaforma
{: #devops}

La seguente tabella elenca i servizi DevOps che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}:

| Servizio     | Descrizione | Eventi {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.DRA_short}}](/docs/apps?topic=creating-apps-insights-overview) | {{site.data.keyword.DRA_short}} è un'integrazione nel catalogo delle toolchain aperte {{site.data.keyword.cloud_notm}}. | [Eventi generati da {{site.data.keyword.DRA_short}}](/docs/apps?topic=creating-apps-at_events) |
| [{{site.data.keyword.contdelivery_short}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-cd_overview#cd_overview) | Con {{site.data.keyword.contdelivery_short}}, puoi creare, testare e fornire applicazioni utilizzando le procedure e gli strumenti leader nel settore DevOps. | [Eventi generati da {{site.data.keyword.contdelivery_short}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-at_events#at_events) |
| [{{site.data.keyword.GlobalizationPipeline_short}}](/docs/services/GlobalizationPipeline?topic=GlobalizationPipeline-globalizationpipeline#globalizationpipeline) | Consente agli sviluppatori dell'applicazione di rilasciare velocemente delle applicazioni tradotte ai clienti in tutto il mondo. | [Eventi generati da {{site.data.keyword.GlobalizationPipeline_short}}](/docs/services/GlobalizationPipeline?topic=GlobalizationPipeline-gpat_events#gpat_events)|
{: caption="Elenco degli strumenti per gli sviluppatori che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Servizi per gli sviluppatori integrati della piattaforma
{: #integrated_dev_svcs}

La seguente tabella elenca i servizi cloud che puoi utilizzare per sviluppare le applicazioni e inviare gli eventi a {{site.data.keyword.cloudaccesstrailshort}}:

| Servizio     | Descrizione | Eventi {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.dev_console}}](/docs/apps?topic=creating-apps-tutorial-getting-started#create) | In {{site.data.keyword.cloud_notm}}, puoi creare applicazioni mobili e web a livello aziendale e trarre vantaggio dalle estensioni cloud ospitate da {{site.data.keyword.cloud_notm}}. Puoi utilizzare la console {{site.data.keyword.cloud_notm}} e gli strumenti della riga di comando per creare, eseguire e distribuire le tue applicazioni. Puoi utilizzare la {{site.data.keyword.dev_console}} per creare un'applicazione utilizzando un kit starter. | [Eventi generati da {{site.data.keyword.dev_console}}](/docs/apps?topic=creating-apps-at_events#at_events) |
| [{{site.data.keyword.mobilepushshort}}](/docs/services/mobilepush?topic=mobile-pushnotification-overview-push#overview-push)| Puoi utilizzare il servizio {{site.data.keyword.mobilepushshort}} per inviare le notifiche ai dispositivi mobili e ai browser. Le notifiche possono essere destinate a tutti gli utenti dell'applicazione oppure a uno specifico insieme di utenti e dispositivi facendo uso delle tag. Per ogni messaggio che invii al servizio, i destinatari previsti ricevono una notifica. | [Eventi generati da {{site.data.keyword.mobilepushshort}}](/docs/services/mobilepush?topic=mobile-pushnotification-push_activity_tracker#push_activity_tracker) |  
{: caption="Elenco dei servizi cloud mobili e web che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Servizi di sicurezza integrati della piattaforma
{: #platform_integrated_security}

I servizi di sicurezza integrati generano gli eventi {{site.data.keyword.cloudaccesstrailshort}} che puoi visualizzare attraverso il **dominio dell'account** {{site.data.keyword.cloudaccesstrailshort}}.


La seguente tabella elenca i servizi della piattaforma di sicurezza principali che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}:

| Servizio     | Descrizione | Eventi {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [Accedi a {{site.data.keyword.cloud_notm}}](/docs/iam?topic=iam-iamoverview#iamoverview)| Puoi accedere a {{site.data.keyword.cloud_notm}} utilizzando una password, una chiave API, un codice di autorizzazione o un passcode. Come utente federato, puoi accedere all'interfaccia della riga di comando (CLI) utilizzando un passcode monouso o una chiave API. | [Eventi generati quando un utente o un'applicazione accede a {{site.data.keyword.cloud_notm}}](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_login) |
| [Gestione dell'accesso Cloud Foundry dell'utente dell'account](/docs/iam?topic=iam-mngcf#mngcf) | Puoi concedere, revocare e aggiornare le autorizzazioni Cloud Foundry (CF) agli utenti nell'account. | [Eventi generati quando gestisci i ruoli CF nell'account](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-cf#cf_cfroles) |
| [{{site.data.keyword.iamlong}} (IAM)](/docs/iam?topic=iam-userroles#userroles) | Puoi utilizzare IAM per gestire gli utenti e i ruoli nei servizi infrastruttura e piattaforma {{site.data.keyword.cloud_notm}}. | [Eventi generati quando gestisci le politiche IAM](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_policies) |
| [Gestione delle chiavi API della piattaforma](/docs/iam?topic=iam-manapikey#platform-api-keys) | Puoi definire le chiavi API in {{site.data.keyword.IBM_notm}} Cloud che sono associate a un utente o a un ID servizio. | [Eventi generati quando gestisci le chiavi API della piattaforma](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_apikeys) |
| [Gestione degli ID servizio](/docs/iam?topic=iam-serviceids#serviceids) | Puoi definire gli ID servizio a livello dell'account in {{site.data.keyword.IBM_notm}} Cloud. | [Eventi generati quando gestisci gli ID del servizio](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_serviceids) |
| [Gestione dei gruppi di accesso](/docs/iam?topic=iam-groups#groups) | Puoi definire i gruppi di accesso per organizzare una serie di utenti e ID servizio in una sola entità che ti rende facile assegnare le autorizzazioni. | [Eventi generati quando gestisci i gruppi di accesso](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_access) |
{: caption="Elenco dei servizi della piattaforma di sicurezza principali" caption-side="top"} 


## Servizi di integrazione della piattaforma
{: #integration}

La seguente tabella elenca i servizi di integrazione che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}:

| Servizio     | Descrizione | Eventi {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.messagehub}}](/docs/services/EventStreams?topic=eventstreams-about#about)| {{site.data.keyword.messagehub}} è un bus di messaggi di velocità elevata creato con Apache Kafka. È ottimizzato per l'inserimento di eventi in {{site.data.keyword.IBM_notm}} e la distribuzione del flusso di eventi tra i tuoi servizi e le tue applicazioni. | [Eventi generati da {{site.data.keyword.messagehub}} ](/docs/services/EventStreams?topic=eventstreams-at_events#at_events) |  
{: caption="Elenco dei servizi cloud di integrazione che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Servizi di rete della piattaforma
{: #network}

La seguente tabella elenca i servizi di rete che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}:

| Servizio     | Descrizione | Eventi {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [IBM Cloud Internet Services (CIS)](/docs/infrastructure/cis?topic=cis-about-ibm-cloud-internet-services-cis#about-ibm-cloud-internet-services-cis)| IBM Cloud Internet Services (CIS) fornisce un servizio internet sicuro, affidabile, ad elevate prestazioni e veloce. | [Eventi generati da IBM Cloud Internet Services](/docs/infrastructure/cis?topic=cis-at_events#at_events) |  
{: caption="Elenco dei servizi cloud di rete che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Servizi di sicurezza della piattaforma
{: #security}

La seguente tabella elenca i servizi di sicurezza che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}:


| Servizio     | Descrizione | Eventi {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.cloudaccesstraillong_notm}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov)| Puoi utilizzare il servizio {{site.data.keyword.cloudaccesstrailshort}} per monitorare {{site.data.keyword.cloudaccesstraillong_notm}}. | [Eventi generati dal servizio {{site.data.keyword.cloudaccesstraillong_notm}}](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-downloading_events#events) |  
| [{{site.data.keyword.appid_full_notm}}](/docs/services/appid?topic=appid-about#about) | Puoi utilizzare {{site.data.keyword.appid_short}} per aggiungere l'autenticazione alle tue applicazioni mobili e web e per proteggere le risorse di backend. | [Eventi generati dal servizio {{site.data.keyword.appid_short}}](/docs/services/appid?topic=appid-at-events#at-events) |
| [{{site.data.keyword.cloudcerts_full_notm}}](/docs/services/certificate-manager?topic=certificate-manager-about-certificate-manager#about-certificate-manager) | Puoi utilizzare {{site.data.keyword.cloudcerts_short}} per gestire i certificati SSL per le tue applicazioni e i tuoi servizi basati su {{site.data.keyword.cloud_notm}}.  | [Eventi generati dal servizio {{site.data.keyword.cloudcerts_short}}](/docs/services/certificate-manager?topic=certificate-manager-at_events#at_events) |
| [{{site.data.keyword.keymanagementservicelong}}](/docs/services/key-protect?topic=key-protect-getting-started-tutorial#getting-started-with-key-protect) | Puoi utilizzare il servizio {{site.data.keyword.keymanagementserviceshort}} per eseguire il provisioning delle chiavi crittografate per le applicazioni in {{site.data.keyword.cloud_notm}}. | [Eventi generati dal servizio {{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect?topic=key-protect-activity-tracker-events#activity-tracker-events) |
| [{{site.data.keyword.security-advisor_short}}](/docs/services/security-advisor?topic=security-advisor-about#about) | Puoi utilizzare {{site.data.keyword.security-advisor_short}} per monitorare la sicurezza dei tuoi carichi di lavoro e delle tue applicazioni {{site.data.keyword.cloud_notm}}.   | [Eventi generati dal servizio {{site.data.keyword.security-advisor_short}}](/docs/services/security-advisor?topic=security-advisor-at_events#at_events) |
{: caption="Elenco dei servizi cloud di sicurezza che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 


## Servizi di archiviazione della piattaforma
{: #storage}

La seguente tabella elenca i servizi di archiviazione che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}:

| Servizio     | Descrizione | Eventi {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.cos_full_notm}}](/docs/services/cloud-object-storage?topic=cloud-object-storage-about#about-ibm-cloud-object-storage)| Puoi utilizzare {{site.data.keyword.cos_full_notm}} per archiviare i dati in {{site.data.keyword.cloud_notm}}. I dati vengono codificati e distribuiti in più ubicazioni geografiche e sono accessibili su HTTP utilizzando un'API REST.   | [Eventi generati da {{site.data.keyword.cos_full_notm}}](/docs/services/cloud-object-storage?topic=cloud-object-storage-at-events) |  
{: caption="Elenco dei servizi cloud di archiviazione che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Servizi di dati della piattaforma Watson
{: #watson_data}


| Servizio     | Descrizione | Eventi {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [Watson Studio](https://dataplatform.cloud.ibm.com/docs/content/wsj/getting-started/overview-ws.html) | Watson Studio fornisce l'ambiente e gli strumenti per risolvere i tuoi problemi di business in modo collaborativo utilizzando i dati. Puoi scegliere gli strumenti di cui hai bisogno per analizzare e visualizzare i dati, ripulire e modellare i dati, inserire i dati di streaming, o creare, preparare e distribuire i modelli di machine learning. | [Eventi generati da Watson Studio](https://dataplatform.cloud.ibm.com/docs/content/wsj/admin/at-events.html#ws) |  
| [Watson Machine Learning](https://dataplatform.cloud.ibm.com/docs/content/wsj/analyze-data/ml-overview.html)| Puoi utilizzare Watson Machine Learning per creare modelli analitici sofisticati, preparati con i tuoi dati, che puoi distribuire per l'utilizzo nelle applicazioni. | [Eventi generati da Watson Machine Learning](https://dataplatform.cloud.ibm.com/docs/content/wsj/admin/at-events.html#wml) | 
| [Watson Knowledge Catalog](https://dataplatform.cloud.ibm.com/docs/content/wsj/catalog/overview-wkc.html)| Watson Knowledge Catalog fornisce una piattaforma di gestione del catalogo aziendale sicura supportata da un framework della politica dei dati. Un catalogo collega i dati e le informazioni approfondite alle persone che hanno bisogno di utilizzarli. Il framework della politica dei dati garantisce che l'accesso ai dati sia conforme alle tue regole aziendali. | [Eventi generati da Watson Knowledge Catalog](https://dataplatform.cloud.ibm.com/docs/content/wsj/admin/at-events.html#wkc) |  
{: caption="Elenco dei servizi di dati cloud Watson che inviano gli eventi a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 

