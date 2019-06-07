---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, view events

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

# Visualizzazione di informazioni sull'evento
{: #viewing_event_status}

Utilizza il comando `ibmcloud at status` per ottenere le informazioni sugli eventi raccolti e archiviati in {{site.data.keyword.cloudaccesstrailshort}} per uno spazio {{site.data.keyword.Bluemix}}.
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} è obsoleto. A partire dal 9 maggio 2019, non puoi eseguire il provisioning delle nuove istanze di {{site.data.keyword.cloudaccesstrailshort}}. Le istanze del piano Premium esistenti sono supportate fino al 30 settembre 2019. Per continuare a monitorare l'attività del tuo account {{site.data.keyword.cloud_notm}}, esegui il provisioning di un'istanza di [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}


Puoi ottenere le informazioni sulla dimensione del log di eventi teh, il numero di record e se gli eventi sono disponibili o meno per l'analisi in Kibana. 

Completa la seguente procedura per visualizzare le informazioni sul log degli eventi:

## Passo 1: Accedi a {{site.data.keyword.cloud_notm}}
{: #viewing_event_status_step1}

Accedi a {{site.data.keyword.cloud_notm}}. Completa la seguente
procedura:

1. Esegui il comando [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) per accedere a {{site.data.keyword.cloud_notm}}.
2. Esegui il comando [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) per impostare l'organizzazione e lo spazio in cui vuoi eseguire il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}.

**Nota:** imposta l'organizzazione e lo spazio in cui viene eseguito il provisioning di {{site.data.keyword.cloudaccesstrailshort}}.

## Passo 2: Identifica quali eventi sono disponibili
{: #viewing_event_status_step2}

Utilizza il comando `ibmcloud at status` per visualizzare le informazioni sugli eventi disponibili in un dominio dello spazio.

* Per ottenere le informazioni sugli eventi in un dominio dello spazio, esegui il comando `ibmcloud at status`.
* Per ottenere le informazioni sugli eventi nel dominio dell'account, esegui il comando `ibmcloud at status` con l'opzione `-a`.

```
$ ibmcloud at status -a -s YYYY-MM-DD -e YYYY-MM-DD 
```
{: codeblock}
    
dove
    
* *-a* viene utilizzato per specificare che la richiesta venga applicata al dominio dell'account.
* *-s* viene utilizzato per impostare la data di inizio in UTC (Universal Coordinated Time): *YYYY-MM-DD*.
* *-e* viene utilizzato per impostare la data di fine in UTC (Universal Coordinated Time): *YYYY-MM-DD*.

Ad esempio, per visualizzare quali eventi sono disponibili per le ultime 2 settimane in un dominio dello spazio, immetti il seguente comando:

```
$ ibmcloud at status
```
{: codeblock}
    
Ad esempio, l'output di esecuzione di questo comando è:
    
```
+------------+--------+------------+
|    DATE    |  COUNT | SEARCHABLE |
+------------+--------+------------+
| 2017-07-24 |    16  |    None    |
+------------+--------+------------+
| 2017-07-25 |   1224 |    All     |
+------------+--------+------------+
```
{: screen}

**Nota:** il servizio {{site.data.keyword.cloudaccesstrailshort}} è un servizio globale che utilizza UTC (Coordinated Universal Time). I giorni sono definiti come giorni UTC. Per ottenere gli eventi per un giorno con ora locale specifico, potresti dover scaricare più giorni UTC.
	














