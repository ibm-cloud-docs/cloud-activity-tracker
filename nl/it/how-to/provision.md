---

copyright:
  years: 2016, 2018
lastupdated: "2018-09-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}



# Provisioning del programma di traccia dell'attività
{: #provision}

Puoi eseguire il provisioning del servizio {{site.data.keyword.cloudaccesstraillong}} dall'IU {{site.data.keyword.Bluemix}} o dalla riga di comando.
{:shortdesc}


## Provisioning dalla IU
{: #ui}

Completa la seguente procedura per eseguire il provisioning di un'istanza del servizio {{site.data.keyword.cloudaccesstraillong_notm}} in {{site.data.keyword.Bluemix_notm}}:

1. Accedi al tuo account {{site.data.keyword.Bluemix_notm}}.

    L'IU {{site.data.keyword.Bluemix_notm}} può essere trovata all'indirizzo: [http://bluemix.net ![Icona link esterno](../../../icons/launch-glyph.svg "Icona link esterno")](http://bluemix.net){:new_window}.
    
	Dopo aver eseguito l'accesso con i tuoi ID e password utente, viene aperta la IU {{site.data.keyword.Bluemix_notm}}.

2. Fai clic su **Catalogo**. Viene aperto l'elenco dei servizi disponibili in {{site.data.keyword.Bluemix_notm}}.

3. Seleziona la categoria **Sicurezza** per filtrare l'elenco dei servizi visualizzati.

    Il servizio è disponibile anche nella categoria **DevOps**.

4. Fai clic sul tile **Programma di traccia dell'attività**.

5. Configura le informazioni che definiscono dove viene eseguito il provisioning del servizio. 

    Immetti i dati come indicato nella seguente tabella: 

    <table>
	  <caption>Tabella 1. Campi obbligatori per eseguire il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}</caption>
	  <tr>
	    <th>Campo</th>
		<th>Valore</th>
	  </tr>
	  <tr>
	    <td>Seleziona la regione a cui distribuire:</td>
		<td>I valori validi sono: Stati Uniti Sud, Regno Unito, Germania, Sydney</td>
	  </tr>
	  <tr>
	    <td>Scegli un'organizzazione:</td>
		<td>Seleziona l'organizzazione in cui il tuo piano monitora l'attività.</td>
	  </tr>
	  <tr>
	    <td>Scegli uno spazio:</td>
		<td>Seleziona uno spazio nell'organizzazione selezionata in cui il tuo piano monitora l'attività. </td>
	  </tr>
	</table>

6. Seleziona un piano di servizio. 

    Per impostazione predefinita, viene impostato il piano **free**.

    Per ulteriori informazioni, vedi [Piani di servizio](/docs/services/cloud-activity-tracker/how-to/change_plan.html#change_plan).
	
7. Fai clic su **Crea** per eseguire il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}} nello spazio
{{site.data.keyword.Bluemix_notm}} in cui hai eseguito l'accesso.
  
 

## Provisioning dalla CLI
{: #cli}

Completa la seguente procedura per eseguire il provisioning di un'istanza del servizio {{site.data.keyword.cloudaccesstrailshort}}
in {{site.data.keyword.Bluemix_notm}} tramite la riga di comando:

1. [Pre-requisito] Installa la CLI {{site.data.keyword.Bluemix_notm}}.

   Per ulteriori informazioni, consulta [Installazione della CLI {{site.data.keyword.Bluemix_notm}}](/docs/cli/reference/ibmcloud/download_cli.html#install_use).
   
   Se la CLI è installata, continua con il prossimo passo.
    
2. Accedi a {{site.data.keyword.Bluemix_notm}}. 

    Esegui il comando [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) per accedere a {{site.data.keyword.Bluemix_notm}} e poi esegui il comando [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) per configurare l'organizzazione e lo spazio in cui vuoi eseguire il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}.
	
3. Immetti il comando `ibmcloud service create` per eseguire il provisioning di un'istanza.

    ```
	ibmcloud service create service_name service_plan service_instance_name
	```
	{: codeblock}
	
	Dove 
	
	* service_name è il nome del servizio, ossia, **accessTrail**.
	* service_plan è il nome del piano di servizio. Per un elenco dei piani, consulta [Piani di servizio](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#plan).
	* service_instance_name è il nome che vuoi utilizzare per la nuova istanza del servizio da te creata.

	Ad esempio, per creare un'istanza del servizio {{site.data.keyword.cloudaccesstrailshort}} con il piano standard, immetti il seguente comando:
	
	```
	ibmcloud service create accessTrail free my_activitytracker_svc
	```
	{: codeblock}
	
4. Verifica che il servizio sia stato creato correttamente. Esegui il seguente comando:

    ```	
	ibmcloud service list
	```
	{: codeblock}
	
	L'output dell'esecuzione del comando è simile al seguente:
	
	```
    Getting services in org MyOrg / space MySpace as xxx@yyy.com...
    OK
    
    name                           service                  plan                   bound apps              last operation
    my_activitytracker_svc         accessTrail             free                                            create succeeded
	```
	{: screen}

	




