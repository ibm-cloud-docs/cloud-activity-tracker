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

# Visualizzazione di informazioni sull'evento
{: #viewing_event_status}

Utilizza il comando *cf at status* per ottenere le informazioni sugli eventi raccolti e archiviati in
{{site.data.keyword.cloudaccesstrailshort}} per uno spazio {{site.data.keyword.Bluemix}}.
{:shortdesc}

## Ottenimento delle informazioni sugli eventi
{: #viewing_event_information}

Utilizza il comando `cf at status` per visualizzare la dimensione, il numero e se gli eventi sono disponibili o meno per l'analisi in Kibana. Per ulteriori informazioni, consulta [cf at status](/docs/services/cloud-activity-tracker/cli/at_cli.html#status).

1. Accedi a uno spazio, organizzazione, regione {{site.data.keyword.Bluemix_notm}}. 

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
	
	Quindi, imposta l'organizzazione e lo spazio. Esegui il seguente comando:

    ```
    bx target -o OrgName -s SpaceName
    ```
   {: codeblock}

    dove

    * OrgName è il nome dell'organizzazione.
    * SpaceName è il nome dello spazio.
    
2. Esegui il comando *cf at status* per visualizzare i dettagli degli eventi raccolti in {{site.data.keyword.cloudaccesstrailshort}}.

    ```
    $ bx cf at status -a -s YYYY-MM-DD -e YYYY-MM-DD 
    ```
    {: codeblock}
    
    dove
    
    * *-a* viene utilizzato per specificare le informazioni a livello dell'account
    * *-s* viene utilizzato per impostare la data di inizio in UTC (Universal Coordinated Time): *YYYY-MM-DD*
    * *-e* viene utilizzato per impostare la data di fine in UTC (Universal Coordinated Time): *YYYY-MM-DD*
    	
	Utilizza il comando `cf at status` con le opzioni **-s** per impostare il giorno di inizio e **-e** per la data di fine. Ad esempio:

    * `bx cf at status` fornisce informazioni per le ultime 2 settimane..
    * `bx cf at status -s 2017-05-03` fornisce le informazioni dal 3 maggio 2017 fino alla data corrente.
    * `bx cf at status -s 2017-05-03 -e 2017-05-08` fornisce le informazioni tra il 3 e l'8 maggio 2017. 
 
    Utilizza il comando `cf at status` con l'opzione **-a** per impostare il dominio su account.
	
    Ad esempio, per ottenere le informazioni sugli eventi disponibili per il 10 giugno 2017, immetti il seguente comando:
    
    ```
    $ bx cf at status -s 2017-06-10 -e 2017-06-10
    +------------+-------+------+-----------------+------------+
    | Date       | Count | Size | Types           | Searchable |
    +------------+-------+------+-----------------+------------+
    | 2017-07-10 | 1     | 2531 | ActivityTracker | All        |
    +------------+-------+------+-----------------+------------+
    ```
    {: screen}
	














