---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, news

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

# Novità
{: #whatsnew}

Descrizione delle funzioni e delle integrazioni più recenti per {{site.data.keyword.cloudaccesstrailshort}}.
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} è obsoleto. A partire dal 9 maggio 2019, non puoi eseguire il provisioning delle nuove istanze di {{site.data.keyword.cloudaccesstrailshort}}. Le istanze del piano Premium esistenti sono supportate fino al 30 settembre 2019. Per continuare a monitorare l'attività del tuo account {{site.data.keyword.cloud_notm}}, esegui il provisioning di un'istanza di [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}

Per l'ultimo elenco di servizi integrati con {{site.data.keyword.cloudaccesstrailshort}}, vedi [Servizi cloud](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-cloud_services#cloud_services).
{: important}


## Marzo 2019
{: #march2019}

* {{site.data.keyword.cloudaccesstrailshort}} CLI

Abbiamo identificato un problema con la CLI del programma di traccia dell'attività. Stiamo per rilasciare una nuova versione della CLI per risolvere il problema.

Se accedi a {{site.data.keyword.cloud_notm}} dalla riga di comando utilizzando `ibmcloud login` e poi esegui i comandi {{site.data.keyword.cloudaccesstrailshort}}, ricevi il seguente errore `Failed: Unauthorized` per ognuno dei comandi {{site.data.keyword.cloudaccesstrailshort}} che esegui. 

Nel frattempo, per continuare ad utilizzare la CLI, accedi a {{site.data.keyword.cloud_notm}} utilizzando i seguenti comandi:

| Regione | Comando |
|--------|---------|
| `US South` | `bx login -a api.ng.bluemix.net -o OrgName -s SpaceName` |
| `EU DE`    | `bx login -a api.eu-de.bluemix.net -o OrgName -s SpaceName` |
| `EU DE`    | `bx login -a api.au-syd.bluemix.net -o OrgName -s SpaceName` |
{: caption="Tabella 1. Comandi" caption-side="top"} 

## Febbraio 2019
{: #february2019}

* **Puoi monitorare il servizio {{site.data.keyword.GlobalizationPipeline_short}} con {{site.data.keyword.cloudaccesstrailshort}}.**

    {{site.data.keyword.GlobalizationPipeline_short}} consente agli sviluppatori dell'applicazione di rilasciare velocemente delle applicazioni tradotte ai clienti in tutto il mondo.

    Per ulteriori informazioni sugli eventi {{site.data.keyword.cloudaccesstrailshort}}, vedi [Eventi generati da {{site.data.keyword.GlobalizationPipeline_short}}](/docs/services/GlobalizationPipeline?topic=GlobalizationPipeline-gpat_events#gpat_events).








