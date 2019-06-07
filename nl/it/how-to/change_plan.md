---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, change plan

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


# Modifica del piano
{: #change_plan}

Puoi modificare il tuo piano di servizio {{site.data.keyword.cloudaccesstraillong}} tramite l'IU {{site.data.keyword.cloud_notm}} o immettendo il comando `ibmcloud service update`. Puoi aggiornare o ridurre il tuo piano in qualsiasi momento.
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} è obsoleto. A partire dal 9 maggio 2019, non puoi eseguire il provisioning delle nuove istanze di {{site.data.keyword.cloudaccesstrailshort}}. Le istanze del piano Premium esistenti sono supportate fino al 30 settembre 2019. Per continuare a monitorare l'attività del tuo account {{site.data.keyword.cloud_notm}}, esegui il provisioning di un'istanza di [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}

## Modifica del piano di servizio tramite la IU
{: #change_plan_ui}

Per modificare il tuo piano di servizio tramite l'IU {{site.data.keyword.cloud_notm}}, completa la seguente procedura:

1. Accedi a {{site.data.keyword.cloud_notm}} e fai clic sul servizio {{site.data.keyword.cloudaccesstraillong_notm}} dal *Dashboard*. 
    
2. Seleziona la scheda **Plan**.

    Vengono visualizzate le informazioni sul tuo piano corrente.
	
3. Seleziona un nuovo piano per aggiornare o ridurre il tuo piano. 

4. Fai clic su **Salva**.



## Modifica del piano di servizio tramite la CLI
{: #change_plan_cli}

Per modificare il tuo piano di servizio tramite la CLI, completa la seguente procedura:

1. Accedi a {{site.data.keyword.cloud_notm}}. 

    Esegui il comando [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) per accedere a {{site.data.keyword.cloud_notm}} e poi esegui il comando [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) per configurare l'organizzazione e lo spazio in cui vuoi eseguire il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}.
	
2. Esegui il comando `ibmcloud service` per controllare il tuo piano corrente e per ottenere il nome del servizio {{site.data.keyword.cloudaccesstrailshort}} dall'elenco dei servizi disponibili nello spazio. 

    Il valore del campo **name** deve essere utilizzato per modificare il piano. 

    Ad esempio,
	
	```
	$ ibmcloud service list
    Invoking 'cf services'...

    Getting services in org MyOrg / space dev as xxx@ibm.com...
    OK

    name                       service                  plan                 bound apps                               last operation
    Activity Tracker-zt          OK                     accessTrail             premium                                update succeeded
    ```
	{: screen}
    
3. Aggiorna o riduci il tuo piano. Esegui il comando `ibmcloud service update`.
    
	```
	ibmcloud service update service_name [-p new_plan]
	```
	{: codeblock}
	
	dove 
	
	* *service_name* è il nome del tuo servizio. Puoi eseguire il comando `ibmcloud service list` per ottenere il valore.
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
	    <td>gratuito</td>
	  </tr>
	  <tr>
	    <td>Premium</td>
	    <td>premium</td>
	  </tr>
	</table>
	
	Ad esempio, per ridurre il tuo piano al piano *Lite*, immetti il seguente comando:
	
	```
	ibmcloud service update "Activity Tracker-zt" -p free
    Updating service instance Activity Tracker-zt as xxx@ibm.com...
    OK
	```
	{: screen}



