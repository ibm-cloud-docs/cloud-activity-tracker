---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, event fields

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



# Campi evento
{: #at_event}

Gli eventi {{site.data.keyword.cloudaccesstrailshort}} si basano sugli standard CADF (Cloud Auditing Data Federation). 
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} è obsoleto. A partire dal 9 maggio 2019, non puoi eseguire il provisioning delle nuove istanze di {{site.data.keyword.cloudaccesstrailshort}}. Le istanze del piano Premium esistenti sono supportate fino al 30 settembre 2019. Per continuare a monitorare l'attività del tuo account {{site.data.keyword.cloud_notm}}, esegui il provisioning di un'istanza di [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}

## Campi dell'iniziatore
{: #initiator}

La seguente tabella elenca i campi comuni disponibili per un evento {{site.data.keyword.cloudaccesstrailshort}}:

| Nome campo | Descrizione | Valore |
|------------|-------------|-------|
| `initiator.id` | ID dell'iniziatore dell'azione. </br></br>I tipi validi di iniziatori sono `IBMID`, `serviceID` e `Cloud Foundry (CF) user ID`. | Un esempio di un ID IBM è `IBMid-000000XXX2` </br>Un esempio di un ID servizio è `iam-ServiceId-12345678-0165-4c89-847d-9660b1632e14` </br>Un esempio di un ID utente CF è `7666666b-23ae-4a34-8569-cu75tgdr4da3` |
| `initiator.name` | Il nome dell'utente che ha avviato l'azione. | Ad esempio, un indirizzo email. |
| `initiator.typeURI` | Tipo di origine dell'evento. | I valori validi sono *service/security/account/user*, *service/security/clientid* e *service/security/account/serviceid*. |
| `initiator.credential.type` | Tipo di credenziali dell'ID iniziatore. | I valori validi sono *user*, *token* e *apikey*. |
{: caption="Tabella 1. Campi dell'iniziatore comuni" caption-side="top"} 

  

## Campi di destinazione
{: #target}

La seguente tabella elenca i campi di destinazione comuni disponibili per un evento {{site.data.keyword.cloudaccesstrailshort}}:

| Nome campo | Descrizione | Valore |
|------------|-------------|-------|
| `target.id` | CRN (Cloud Resource Name) della risorsa in cui viene eseguita l'azione. </br>Per ulteriori informazioni, vedi [Formato del CRN](/docs/overview?topic=overview-crn#format-crn). | Ad esempio, `crn:v1:bluemix:public:cloud-object-storage:global:a/12345678e6232019c6567c9123456789:fr56et47-befb-440a-a223c-12345678dae1:bucket:bucket1` |
| `target.name` | Nome leggibile della risorsa cloud su cui viene eseguita l'azione. |  |
| `target.typeURI` | Il tipo di risorsa cloud su cui viene eseguita l'azione. </br>Il formato di questo campo è **serviceName/objectType** dove `servicename` è il nome del servizio. | Ad esempio, `iam-am/policy` o `cloud-object-storage/bucket/acl` |
{: caption="Tabella 2. Campi di destinazione comuni" caption-side="top"} 


 
## Campi di azione
{: #action}

La seguente tabella elenca i campi di azione comuni disponibili per un evento {{site.data.keyword.cloudaccesstrailshort}}:

| Nome campo | Descrizione | Valore |
|------------|-------------|-------|
| `action` | Azione che attiva l'evento. </br>Il formato di questo campo è **serviceName.objectType.action** dove `servicename` è il nome del servizio. </br>Per ulteriori informazioni sui i valori dell'azione per gli eventi generati da un servizio, consulta <a href="/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-cloud_services#cloud_services">Servizi cloud</a> | Ad esempio, `iam-identity.serviceid-apikey.login` |
| `eventTime` | Indica la data/ora in cui è stato creato l'evento. </br>La data è rappresentata come UTC (Coordinated Universal Time). </br>Il formato è conforme con ISO 8601. | Ad esempio, `2017-10-19T19:07:50.32+0000` |
{: caption="Tabella 3. Campi di azione comuni" caption-side="top"} 



## Campi del risultato
{: #outcomes}

La seguente tabella elenca i campi del risultato comuni disponibili per un evento {{site.data.keyword.cloudaccesstrailshort}}:

| Nome campo | Descrizione | Valore |
|------------|-------------|-------|
| `outcome` | Risultato dell'azione. | I valori validi sono *success*, *failure* e *pending*. |
| `reason.reasonCode` | Campo numerico che include il codice di risposta HTTP. | Ad esempio, *200* per un risultato corretto. |
| `severity` | Definisce il livello di minaccia che un'azione può avere sul cloud. | I valori validi sono *normal*, *warning* e *critical*. </br></br>**Normal** è impostato per le azioni di routine nel cloud. Ad esempio, avvio di un'istanza o aggiornamento di un token. </br></br>**Warning** è impostato per le azioni in cui una risorsa cloud viene aggiornata o i relativi metadati vengono modificati. Ad esempio, l'aggiornamento della versione di un nodo di lavoro, la ridenominazione di un certificato o di un'istanza del servizio. </br></br>**Critical** è impostato per le azioni che influiscono sulla sicurezza nel cloud. Ad esempio, la modifica delle credenziali di un utente, l'eliminazione dei dati, l'accesso non autorizzato all'utilizzo di una risorsa cloud. |
{: caption="Tabella 4. Campi del risultato comuni" caption-side="top"} 


