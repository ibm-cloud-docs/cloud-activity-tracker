---

copyright:
  years: 2016, 2017
lastupdated: "2017-09-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Scaricamento degli eventi
{: #downloading_events}

Puoi scaricare gli eventi in un file locale o passare i dati a un altro programma. Scarichi gli eventi nel contesto di una sessione. Una sessione specifica quali eventi saranno scaricati. Se il download degli eventi viene interrotto, la sessione abilita la ripresa del download da dove era stato interrotto. Dopo il completamento del download, devi eliminare la sessione.
{:shortdesc}

Completa le seguenti istruzioni per scaricare gli eventi disponibili in uno spazio {{site.data.keyword.Bluemix_notm}} in un file locale:

## Passo 1: Accedi a Bluemix
{: #prereq}

rima di iniziare, accedi a uno spazio, organizzazione, regione {{site.data.keyword.Bluemix_notm}} in cui è stato eseguito il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}. 

```
bx login -a Endpoint
```
{: codeblock}
	
Dove *Endpoint* è l'URL per accedere a {{site.data.keyword.Bluemix_notm}}. Questo URL è differente per regione.
	
<table>
    <caption>Elenco degli endpoint per accedere a {{site.data.keyword.Bluemix_notm}}</caption>
	<tr>
	  <th>Regione</th>
	  <th>URL</th>
	</tr>
	<tr>
	  <td>Stati Uniti Sud</td>
	  <td>api.ng.bluemix.net</td>
	</tr>
</table>

Segui le istruzioni. 

Ad esempio, immetti il seguente comando per accedere dalla regione Stati Uniti Sud: 
	
```
bx login -a api.ng.bluemix.net
```
{: codeblock}

Quindi, imposta l'organizzazione e lo spazio. Immetti il seguente comando:

```
bx target -o OrgName -s SpaceName
```
{: codeblock}

dove

* OrgName è il nome dell'organizzazione. 
* SpaceName è il nome dello spazio.

## Passo 2: Identifica quali eventi sono disponibili
{: #step2}

1. Utilizza il comando `cf at status` per visualizzare quali eventi sono disponibili.

    Ad esempio, per visualizzare quali eventi sono disponibili per le ultime 2 settimane, immetti il seguente comando:

    ```
    $ bx cf at status
    ```
    {: codeblock}
    
    Ad esempio, l'output di esecuzione di questo comando è:
    
    ```
    +------------+--------+-------+--------------------+------------+
    |    DATE    |  COUNT | SIZE  |       TYPES        | SEARCHABLE |
    +------------+--------+-------+--------------------+------------+
    | 2017-07-24 |    16  | 3020  | ActivityTracker    |   None     |
    +------------+--------+-------+--------------------+------------+
    | 2017-07-25 |   1224 | 76115 | ActivityTracker    |    All     |
    +------------+--------+-------+--------------------+------------+
    ```
    {: screen}

    **Nota:** il servizio {{site.data.keyword.cloudaccesstrailshort}} è un servizio globale che utilizza UTC (Coordinated Universal Time). I giorni sono definiti come giorni UTC. Per ottenere gli eventi per un giorno con ora locale specifico, potresti dover scaricare più giorni UTC.
	
	Per ulteriori informazioni, consulta [cf at status](/docs/services/cloud-activity-tracker/cli/at_cli.html#status).


## Passo 3: Crea una sessione
{: #step3}

Una sessione è obbligatoria per definire l'ambito dei dati dell'evento disponibili per un download e per conservare lo stato del download. 

Utilizza il comando [cf at session create](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_create) per creare una sessione. Facoltativamente, puoi specificare le date di inizio e di fine quando crei una sessione. 

**Nota:** quando specifichi le date di inizio e di fine, la sessione fornisce l'accesso agli eventi compresi tra queste date. 

Per creare una sessione utilizzata per scaricare gli eventi per la data corrente, immetti il seguente comando:

```
bx cf at session create 
```
{: codeblock}

La sessione restituisce le seguenti informazioni: 

* L'intervallo di date che deve essere scaricato. Il valore predefinito è la data UTC corrente. 
* Le informazioni su quali eventi includere disponibili per l'account completo o soltanto per lo spazio corrente. Per impostazione predefinita, ottieni gli eventi per lo spazio a cui hai eseguito l'accesso
* L'ID sessione necessario per scaricare gli eventi. 
* L'ID utente che crea la sessione.

Ad esempio,

```
$ bx cf at session create 
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

**Suggerimento:** per visualizzare l'elenco delle sessioni attive, esegui il comando [cf at session list](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_list).

Ad esempio,

```
bx cf at session list
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
bx cf at download -o Events_File_Name Session_ID
```
{: codeblock}

dove

* Events_File_Name è il nome del file di output.
* Session_ID è il GUID della sessione. Ottieni questi valori nel passo precedente. Utilizza il valore per il campo **Id**.

Ad esempio,

```
bx cf at download -o Events_File_Name.log 32c657c5-31c0-4a3c-a139-b380871c737a
 29.89 KiB / 12.19 KiB [================================] 245.14% 9.73 MiB/s 0s
Download completed successfully
```
{: screen}

L'indicatore di avanzamento si muove da 0 a 100% come vengono scaricati gli eventi.

**Nota:** 

* Il formato dei dati scaricati è un JSON compresso. Ad esempio, quando scarichi gli eventi in un sistema Linux, decomprimi il file .gz e aprilo per visualizzare i dati nel formato JSON. 
* Il JSON compresso è adatto all'inserimento per ElasticSearch o Logstash. Ad esempio, se non viene fornito -o e stai utilizzando un sistema Linux, i dati saranno trasmessi a stdout, in modo che puoi passarli direttamente nel tuo proprio stack Elastic.
* Puoi anche elaborare i dati con qualsiasi programma che possa analizzare JSON.  

## Passo 4: Elimina la sessione

Dopo il completamento del download, devi eliminare la sessione utilizzando il comando [cf at session delete](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_delete). 

Immetti il seguente comando per eliminare una sessione:

```
bx cf at session delete Session_ID
```
{: codeblock}

Dove Session_ID è il GUID della sessione che hai creato nel passo precedente. Utilizza il valore per il campo **Id**.

Ad esempio,

```
bx cf at session delete 32c657c5-31c0-4a3c-a139-b380871c737a
+---------+------------------------+
| Name    | Value                  |
+---------+------------------------+
| message | Delete session success |
+---------+------------------------+
```
{: screen}




