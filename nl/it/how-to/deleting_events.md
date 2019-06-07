---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, delete events

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

# Eliminazione di eventi
{: #deleting_events}

Utilizza il comando *ibmcloud at delete* per eliminare manualmente gli eventi archiviati in {{site.data.keyword.cloudaccesstrailshort}}.
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} è obsoleto. A partire dal 9 maggio 2019, non puoi eseguire il provisioning delle nuove istanze di {{site.data.keyword.cloudaccesstrailshort}}. Le istanze del piano Premium esistenti sono supportate fino al 30 settembre 2019. Per continuare a monitorare l'attività del tuo account {{site.data.keyword.cloud_notm}}, esegui il provisioning di un'istanza di [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}


Completa la seguente
procedura:

## Passo 1: Accedi a {{site.data.keyword.cloud_notm}}
{: #deleting_events_prereq}

Accedi a {{site.data.keyword.cloud_notm}}. Completa la seguente
procedura:

1. Esegui il comando [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) per accedere a {{site.data.keyword.cloud_notm}}.
2. Esegui il comando [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) per impostare l'organizzazione e lo spazio in cui vuoi eseguire il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}.

**Nota:** imposta l'organizzazione e lo spazio in cui viene eseguito il provisioning di {{site.data.keyword.cloudaccesstrailshort}}.

## Passo 2: Identifica quali eventi sono disponibili
{: #deleting_events_step2}

Utilizza il comando `ibmcloud at status` per visualizzare le informazioni sugli eventi disponibili in un dominio dello spazio.

* Per ottenere le informazioni sugli eventi in un dominio dello spazio, esegui il comando `ibmcloud at status`.
* Per ottenere le informazioni sugli eventi nel dominio dell'account, esegui il comando `ibmcloud at status` con l'opzione `-a`.

Per ulteriori informazioni, vedi [Visualizzazione di informazioni sull'evento](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-viewing_event_status#viewing_event_status).
	
  
## Passo 3: Elimina gli eventi
{: #deleting_events_step3}
	
Per eliminare gli eventi, esegui il comando `ibmcloud at delete`.

```
ibmcloud at delete -s YYYY-MM-DD -e YYYY-MM-DD 
```
{: codeblock}
    
dove

* *-s* viene utilizzato per impostare la data di inizio in UTC (Universal Coordinated Time): *YYYY-MM-DD*.
* *-e* viene utilizzato per impostare la data di fine in UTC (Universal Coordinated Time): *YYYY-MM-DD*.

Ad esempio, per eliminare gli eventi del 10 giugno 2017, esegui il seguente comando:

```
ibmcloud at delete -s 2017-06-10 -e 2017-06-10
```
{: screen}

Ricevi le informazioni sui record degli eventi che sono stati eliminati.










