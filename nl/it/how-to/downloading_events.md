---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, download events

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

# Scaricamento degli eventi
{: #downloading_events}

Puoi scaricare gli eventi in un file locale. Scarichi gli eventi nel contesto di una sessione. Una sessione specifica quali eventi saranno scaricati. Dopo il completamento del download, devi eliminare la sessione.
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} è obsoleto. A partire dal 9 maggio 2019, non puoi eseguire il provisioning delle nuove istanze di {{site.data.keyword.cloudaccesstrailshort}}. Le istanze del piano Premium esistenti sono supportate fino al 30 settembre 2019. Per continuare a monitorare l'attività del tuo account {{site.data.keyword.cloud_notm}}, esegui il provisioning di un'istanza di [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}


Completa le seguenti istruzioni per scaricare gli eventi in un file locale:

## Passo 1: Accedi a {{site.data.keyword.cloud_notm}}
{: #prereq}

Accedi a {{site.data.keyword.cloud_notm}}. Completa la seguente
procedura:

1. Esegui il comando [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) per accedere a {{site.data.keyword.cloud_notm}}.
2. Esegui il comando [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) per impostare l'organizzazione e lo spazio in cui vuoi eseguire il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}.

**Nota:** imposta l'organizzazione e lo spazio in cui viene eseguito il provisioning di {{site.data.keyword.cloudaccesstrailshort}}.

## Passo 2: Identifica quali eventi sono disponibili
{: #step2}

Utilizza il comando `ibmcloud at status` per visualizzare le informazioni sugli eventi disponibili in un dominio dello spazio.

* Per ottenere le informazioni sugli eventi in un dominio dello spazio, esegui il comando `ibmcloud at status`.
* Per ottenere le informazioni sugli eventi nel dominio dell'account, esegui il comando `ibmcloud at status` con l'opzione `-a`.

Per ulteriori informazioni, vedi [Visualizzazione di informazioni sull'evento](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-viewing_event_status#viewing_event_status).
  


## Passo 3: Crea una sessione
{: #step3}

Una sessione è obbligatoria per definire l'ambito dei dati dell'evento disponibili per un download e per conservare lo stato del download. 

Utilizza il comando `ibmcloud at session create` per creare una sessione. Per impostazione predefinita, una sessione include i dati delle ultime 2 settimane.  Facoltativamente, puoi specificare le date di inizio e di fine quando crei una sessione per specificare un intervallo di tempo, un'ora specifica del giorno e l'ambito degli eventi. 

**Nota:** 

* Quando specifichi le date di inizio e di fine, la sessione fornisce l'accesso agli eventi compresi tra queste date. 
* Non puoi scaricare più di 2 settimane di dati per sessione. Pertanto, l'intervallo di tempo deve essere inferiore a 2 settimane.
* Puoi scaricare gli eventi di un dominio dello spazio o dell'account in una regione.

Per creare una sessione utilizzata per scaricare gli eventi per una data specifica, immetti il seguente comando:

```
ibmcloud at session create -s 2017-07-25 -e 2017-07-25
```
{: codeblock}

La sessione restituisce le seguenti informazioni:

* L'intervallo di date che deve essere scaricato.
* Le informazioni su quali eventi includere disponibili per l'account completo o soltanto per lo spazio corrente. Per impostazione predefinita, ottieni gli eventi per lo spazio a cui hai eseguito l'accesso
* L'ID sessione necessario per scaricare gli eventi.
* L'ID utente che crea la sessione.

Ad esempio,

```
$ ibmcloud at session create 
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| username     | xxx@yyy.com                               |
| create-time  | 2017-07-25T10:29:28.541092735Z            |
| access-time  | 2017-07-25T10:29:28.541092735Z            |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
| id           | 32c657c5-31c0-4a3c-a139-b380871c737a      |
| space        | 66fe4565-abab-46c9-cdcd-qf4565342345      |
+--------------+-------------------------------------------+
```
{: screen}

**Suggerimento:** per visualizzare l'elenco delle sessioni attive, esegui il comando `ibmcloud at session list`.

Ad esempio,

```
ibmcloud at session list
+--------------------------------------+--------------------------------------+---------------------+--------------------------------+--------------------------------+
| Id                                   | Space                                |Username             | Create-time                    | Access-time                    |
+--------------------------------------+--------------------------------------+---------------------+--------------------------------+--------------------------------+
| 32c657c5-31c0-4a3c-a139-b380871c737a | 66fe4565-abab-46c9-cdcd-qf4565342345 |xxx@yyy.com          | 2017-07-25T10:29:28.541092735Z | 2017-07-25T10:29:28.541092735Z |
+--------------------------------------+--------------------------------------+---------------------+--------------------------------+--------------------------------+
```
{: screen} 


## Passo 4: Scarica gli eventi in un file
{: #step4}

Per scaricare gli eventi specificati dai parametri della sessione, immetti il seguente comando:

```
ibmcloud at download -o Events_File_Name Session_ID
```
{: codeblock}

dove

* Events_File_Name è il nome del file di output.
* Session_ID è il GUID della sessione. Ottieni questi valori nel passo precedente. Utilizza il valore per il campo **Id**.

Ad esempio,

```
ibmcloud at download -o Events_File_Name.log 32c657c5-31c0-4a3c-a139-b380871c737a
 29.89 KiB / 12.19 KiB [================================] 245.14% 9.73 MiB/s 0s
Download completed successfully
```
{: screen}

L'indicatore di avanzamento passa da 0 a 100% man mano che vengono scaricati gli eventi.

**Nota:** 

* Il formato dei dati scaricati è un JSON compresso. Ad esempio, quando scarichi gli eventi in un sistema Linux, decomprimi il file .gz e aprilo per visualizzare i dati nel formato JSON. 
* Il JSON compresso è adatto all'inserimento per ElasticSearch o Logstash. Ad esempio, se non viene fornito -o e stai utilizzando un sistema Linux, i dati saranno trasmessi a stdout, in modo che puoi passarli direttamente nel tuo proprio stack Elastic.
* Puoi anche elaborare i dati con qualsiasi programma che possa analizzare JSON. 

## Passo 4: Elimina la sessione

Dopo il completamento del download, devi eliminare la sessione utilizzando il comando `ibmcloud at session delete`. 

Immetti il seguente comando per eliminare una sessione:

```
ibmcloud at session delete Session_ID
```
{: codeblock}

Dove Session_ID è il GUID della sessione che hai creato nel passo precedente. Utilizza il valore per il campo **Id**.

Ad esempio,

```
ibmcloud at session delete 32c657c5-31c0-4a3c-a139-b380871c737a
+---------+------------------------+
| Name    | Value                  |
+---------+------------------------+
| message | Delete session success |
+---------+------------------------+
```
{: screen}




