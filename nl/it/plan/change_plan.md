---

copyright:
  years: 2017
lastupdated: "2017-09-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# Modifica del piano
{: #change_plan}

Puoi modificare il tuo piano di servizio {{site.data.keyword.cloudaccesstraillong}}
in {{site.data.keyword.Bluemix_notm}} nel dashboard del servizio o eseguendo il comando `cf update-service`. Puoi aggiornare o ridurre il tuo piano in qualsiasi momento.
{:shortdesc}

## Modifica del piano di servizio tramite la IU
{: #change_plan_ui}

Per modificare il tuo piano di servizio in {{site.data.keyword.Bluemix_notm}} nel Dashboard del servizio, completa le seguenti istruzioni:

1. Accedi a {{site.data.keyword.Bluemix_notm}} e fai clic sul servizio {{site.data.keyword.cloudaccesstraillong_notm}} dal dashboard
{{site.data.keyword.Bluemix_notm}}. 
    
2. Seleziona la scheda **Piano** nella IU {{site.data.keyword.Bluemix_notm}}.

    Vengono visualizzate le informazioni sul tuo piano corrente.
	
3. Seleziona un nuovo piano per aggiornare o ridurre il tuo piano. 

4. Fai clic su **Salva**.



## Modifica del piano di servizio tramite la CLI 
{: #change_plan_cli}

Per modificare il tuo piano di servizio in Bluemix tramite la CLI, completa la seguente procedura:

1. Accedi a uno spazio, organizzazione, regione {{site.data.keyword.Bluemix_notm}}. 

    ```
    cf login -a Endpoint
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
		<tr>
		  <td>Regno Unito</td>
		  <td>api.eu-gb.bluemix.net</td>
		</tr>
		<tr>
		  <td>Germania</td>
		  <td>api.eu-de.bluemix.net</td>
		</tr>
	</table>

    Segui le istruzioni. Immetti le tue credenziali {{site.data.keyword.Bluemix_notm}}, seleziona un'organizzazione e uno spazio. 

    Ad esempio, immetti il seguente comando per accedere dalla regione Stati Uniti Sud:
	
	```
	cf login -a api.ng.bluemix.net
	```
	{: codeblock}
	
2. Esegui il comando `cf services` per controllare il tuo piano corrente e per ottenere il nome del servizio {{site.data.keyword.cloudaccesstrailshort}}
dall'elenco dei servizi disponibili nello spazio. 

    Il valore del campo **name** deve essere utilizzato per modificare il piano. 

    Ad esempio,
	
	```
	$ cf services
    Getting services in org MyOrg / space dev as xxx@yyy.com...
    OK
    
    name                            service              plan          bound apps      last operation
    Activity Tracker-oj            activityTracker       premium                       create succeeded
    ```
	{: screen}
    
3. Aggiorna o riduci il tuo piano. Esegui il comando `cf update-service`.
    
	```
	cf update-service service_name [-p new_plan]
	```
	{: codeblock}
	
	dove 
	
	* *service_name* è il nome del tuo servizio. Puoi eseguire il comando `cf services` per ottenere il valore.
	* *new_plan* è il nome del piano.
	
	La seguente tabella elenca i diversi piani e i rispettivi valori supportati: 
	
	<table>
	  <caption>Tabella 1. Elenco dei piani</caption>
	  <tr>
	    <th>Piano</th>
	    <th>Nome</th>
	  </tr>
	  <tr>
	    <td>Lite</td>
	    <td>lite</td>
	  </tr>
	  <tr>
	    <td>Premium</td>
	    <td>premium</td>
	  </tr>
	</table>
	
	Ad esempio, per ridurre il tuo piano al piano *Lite*, immetti il seguente comando:
	
	```
	cf update-service "Activity Tracker-oj" -p lite
    Updating service instance Activity Tracker-oj as xxx@yyy.com...
    OK
	```
	{: screen}

4. Verifica che il nuovo piano è stato modificato. Esegui il comando `cf services`.

    ```
	cf services
    Getting services in org MyOrg / space dev as xxx@yyy.com...
    OK

    name                   service            plan      bound apps   last operation
    Activity Tracker-oj    activityTracker    lite                   update succeeded
	```
	{: screen}






