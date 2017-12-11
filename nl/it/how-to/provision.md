---

copyright:
  years: 2016, 2017

lastupdated: "2017-09-17"

---


{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# Provisioning del servizio del programma di traccia dell'attività 
{: #provision}

Puoi eseguire il provisioning del servizio {{site.data.keyword.cloudaccesstraillong}} dalla IU {{site.data.keyword.Bluemix}} o dalla riga di comando.
{:shortdesc}


## Provisioning dalla IU
{: #ui}

Completa la seguente procedura per eseguire il provisioning di un'istanza del servizio {{site.data.keyword.cloudaccesstraillong_notm}} in {{site.data.keyword.Bluemix_notm}}:

1. Accedi al tuo account {{site.data.keyword.Bluemix_notm}}.

    Il dashboard {{site.data.keyword.Bluemix_notm}} può essere trovato all'indirizzo: [http://bluemix.net ![Icona link esterno](../../../icons/launch-glyph.svg "Icona link esterno")](http://bluemix.net){:new_window}.
    
	Dopo aver eseguito l'accesso con i tuoi ID e password utente, viene aperta la IU {{site.data.keyword.Bluemix_notm}}.

2. Fai clic su **Catalogo**.Viene aperto l'elenco dei servizi disponibili in {{site.data.keyword.Bluemix_notm}}.

3. Seleziona la categoria **Sicurezza** per filtrare l'elenco dei servizi visualizzati.

    Il servizio è disponibile anche nella categoria **DevOps**.

4. Fai clic sul tile **Programma di traccia dell'attività**.

5. Configura le informazioni che definiscono dove viene eseguito il provisioning del servizio. 

    Immetti i dati come indicato nella seguente tabella: 

    <table>
	  <caption>Tabella 1. Campi obbligatori per eseguire il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}</caption>
	  <tr>
	    <th>Campo</th>
		<th>Valore </th>
	  </tr>
	  <tr>
	    <td>Seleziona la regione a cui distribuire:</td>
		<td>I valori validi sono: Stati Uniti Sud, Regno Unito, Germania</td>
	  </tr>
	  <tr>
	    <td>Scegli un'organizzazione: </td>
		<td>Seleziona l'organizzazione in cui il tuo piano monitora l'attività.</td>
	  </tr>
	  <tr>
	    <td>Scegli uno spazio:</td>
		<td>Seleziona lo spazio nell'organizzazione selezionata in cui il tuo piano monitora l'attività. </td>
	  </tr>
	</table>

6. Seleziona un piano di servizio. 

    Per impostazione predefinita, viene impostato il piano **free**.

    Per ulteriori informazioni, vedi [Piani di servizio](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#plans).
	
7. Fai clic su **Crea** per eseguire il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}} nello spazio
{{site.data.keyword.Bluemix_notm}} in cui hai eseguito l'accesso.
  
 

## Provisioning dalla CLI
{: #cli}

Completa la seguente procedura per eseguire il provisioning di un'istanza del servizio {{site.data.keyword.cloudaccesstraillong_notm}}
in {{site.data.keyword.Bluemix_notm}} tramite la riga di comando:

1. Installa la CLI Cloud Foundry (CF). Se la CLI CF è installata, continua con il prossimo passo.

   Per ulteriori informazioni, vedi [Installing the cf CLI ![Icona link esterno](../../../icons/launch-glyph.svg "Icona link esterno")](http://docs.cloudfoundry.org/cf-cli/install-go-cli.html){: new_window}. 
    
2. Accedi a uno spazio, organizzazione, regione {{site.data.keyword.Bluemix_notm}}. 

    Ad esempio, per accedere alla regione Stai Uniti Sud, immetti il seguente comando:

    ```
    cf login -a https://api.ng.bluemix.net
    ```
    {: codeblock}

    Segui le istruzioni. Immetti le tue credenziali {{site.data.keyword.Bluemix_notm}}, seleziona un'organizzazione e uno spazio.
	
3. Esegui il comando `cf create-service` per eseguire il provisioning di un'istanza.

    ```
	cf create-service service_name service_plan service_instance_name
	```
	{: codeblock}
	
	Dove
	
	* service_name è il nome del servizio, ossia, **activityTracker**.
	* service_plan è il nome del piano di servizio. Per un elenco dei piani, consulta [Piani di servizio](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#plans).
	* service_instance_name è il nome che vuoi utilizzare per la nuova istanza del servizio da te creata.
	
	Per ulteriori informazioni sul comando cf, consulta [cf create-service](/docs/cli/reference/cfcommands/index.html#cf_create-service).

	Ad esempio, per creare un'istanza del servizio {{site.data.keyword.cloudaccesstrailshort}} con il piano Lite, immetti il seguente comando:
	
	```
	cf create-service activityTracker free my_activity_tracker_svc
	```
	{: codeblock}
	
4. Verifica che il servizio sia stato creato correttamente. Esegui il seguente comando:

    ```	
	cf services
	```
	{: codeblock}
	
	L'output dell'esecuzione del comando è simile al seguente:
	
	```
    Getting services in org MyOrg / space MySpace as xxx@yyy.com...
    OK
    
    name                           service                  plan                   bound apps              last operation
    my_activity_tracker_svc        activityTracker          free                                           create succeeded
	```
	{: screen}

	



