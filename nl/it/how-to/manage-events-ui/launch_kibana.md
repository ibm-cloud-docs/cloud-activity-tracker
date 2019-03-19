---

copyright:
  years: 2016, 2019
lastupdated: "2019-01-23"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}



# Passaggio al dashboard Kibana
{: #launch_kibana}

Puoi avviare Kibana dall'IU {{site.data.keyword.cloudaccesstrailshort}} in {{site.data.keyword.Bluemix}} o direttamente da un browser web.
{:shortdesc}
   

##  Passaggio a Kibana dal dashboard del servizio del programma di traccia dell'attività
{: #launch_Kibana_from_at}

I log attività che visualizza Kibana includono gli eventi di tutte le risorse distribuite nello spazio dell'organizzazione {{site.data.keyword.cloud_notm}} a cui hai eseguito l'accesso e in cui è stato eseguito il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}.

Completa la seguente procedura per avviare Kibana dal dashboard del servizio {{site.data.keyword.cloudaccesstrailshort}}:

1. Accedi al tuo account {{site.data.keyword.cloud_notm}}.

    Il dashboard {{site.data.keyword.cloud_notm}} può essere trovato all'indirizzo: [https://cloud.ibm.com/login ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://cloud.ibm.com/login){:new_window}.
    
	Dopo aver eseguito l'accesso con i tuoi ID e password utente, viene aperta la IU {{site.data.keyword.cloud_notm}}.

2. Seleziona il servizio {{site.data.keyword.cloudaccesstrailshort}} dal dashboard {{site.data.keyword.cloud_notm}}. 
    
3. Seleziona la scheda **Managed**.

4. Per visualizzare gli eventi dello spazio, seleziona **Space logs** per il campo *View Logs*. **Nota:** questa è la vista predefinita. Fai quindi clic su **View in Kibana**. 

    Viene aperto il dashboard Kibana. Viene caricato il dashboard **ActivityTracker_Space_Dashboard_in_24h** con un filtro temporale impostato sulle ultime 24 ore.

5. Per visualizzare gli eventi dell'account, seleziona **Account logs** per il campo *View Logs*. Fai quindi clic su **View in Kibana**. 

    Viene caricato il dashboard **ActivityTracker_Account_Dashboard_in_24h** con un filtro temporale impostato sulle ultime 24 ore.
	
	
##  Passaggio a Kibana da un browser web
{: #launch_Kibana_from_browser}

Completa la seguente procedura per avviare Kibana da un browser:

1. Apri un browser web e avvia Kibana nella regione in cui vuoi monitorare gli eventi. Quindi, accedi all'interfaccia utente Kibana.
    
    Ad esempio, la seguente tabella elenca l'URL che devi utilizzare per avviare Kibana per regione:
      
    <table>
          <caption>Tabella 1. URL per avviare Kibana per regione</caption>
           <tr>
            <th>Regione</th>
            <th>URL</th>
          </tr>
          <tr>
            <td>Germania</td>
            <td>[https://logging.eu-fra.bluemix.net](https://logging.eu-fra.bluemix.net) </td>
          </tr>
          <tr>
            <td>Sydney</td>
            <td>[https://logging.au-syd.bluemix.net](https://logging.au-syd.bluemix.net) </td>
          </tr>
		  <tr>
            <td>Regno Unito</td>
            <td>[https://logging.eu-gb.bluemix.net](https://logging.eu-gb.bluemix.net)</td>
          </tr>
		  <tr>
            <td>Stati Uniti Sud</td>
            <td>[https://logging.ng.bluemix.net](https://logging.ng.bluemix.net) </td>
          </tr>
    </table>
	
	Viene aperta la pagina Rileva in Kibana.
	
2. Verifica di aver eseguito l'accesso all'account {{site.data.keyword.cloud_notm}} in cui desideri visualizzare e analizzare gli eventi attività.

3. Seleziona un dominio (**Domain**).

    Seleziona **Account** per visualizzare gli eventi del dominio dell'account.
    Seleziona **Space** per visualizzare gli eventi in un dominio dello spazio.

Gli eventi che visualizzi in Kibana corrispondono a quelli ospitati nel dominio selezionato nella regione in cui hai avviato Kibana.


## Limitazioni
{: #launch_kibana_limitations}

 A causa di limitazioni in Kibana, non puoi avere più schede browser Kibana aperte contemporaneamente nella stessa sessione per visualizzare account e spazi differenti. Pertanto, se hai due o più sessioni aperte contemporaneamente e modifichi il dominio dallo spazio all'account o viceversa, potresti riscontrare dei problemi.
	



