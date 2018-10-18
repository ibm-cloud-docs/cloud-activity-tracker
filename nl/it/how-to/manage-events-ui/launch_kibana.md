---

copyright:
  years: 2016, 2018
lastupdated: "2018-04-27"

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

I log attività che visualizza Kibana includono gli eventi di tutte le risorse distribuite nello spazio dell'organizzazione {{site.data.keyword.Bluemix_notm}} a cui hai eseguito l'accesso e in cui è stato eseguito il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}.

Completa la seguente procedura per avviare Kibana dal dashboard del servizio {{site.data.keyword.cloudaccesstrailshort}}:

1. Accedi al tuo account {{site.data.keyword.Bluemix_notm}}.

    Il dashboard {{site.data.keyword.Bluemix_notm}} può essere trovato all'indirizzo: [http://bluemix.net ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://bluemix.net){:new_window}.
    
	Dopo aver eseguito l'accesso con i tuoi ID e password utente, viene aperta la IU {{site.data.keyword.Bluemix_notm}}.

2. Seleziona il servizio {{site.data.keyword.cloudaccesstrailshort}} dal dashboard {{site.data.keyword.Bluemix_notm}}. 
    
3. Seleziona la scheda **Managed**.

4. Fai clic su **Advanced view**. 

    Viene aperto il dashboard Kibana.

Per impostazione predefinita, viene caricato il dashboard **ActivityTracker_Space_Dashboard_in_24h** e impostato un filtro temporale sulle ultime 24 ore. 


	
	
##  Passaggio a Kibana da un browser web
{: #launch_Kibana_from_browser}

Le informazioni di log che visualizza Kibana includono gli eventi di tutte le risorse distribuite nello spazio dell'organizzazione {{site.data.keyword.Bluemix_notm}} a cui hai eseguito l'accesso

Completa la seguente procedura per avviare Kibana da un browser:

1. Apri un browser web e avvia Kibana. Quindi, accedi all'interfaccia utente Kibana.
    
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
	
2. Verifica di aver eseguito l'accesso allo spazio, organizzazione e account {{site.data.keyword.Bluemix_notm}} in cui desideri visualizzare e analizzare i log attività.

    Puoi visualizzare gli eventi e i log disponibili nello spazio in cui hai eseguito l'accesso.

3. Per filtrare gli eventi, selezionare **Open** dalla barra del menu.

    Viene visualizzato l'elenco dei dashboard salvati.
	
4. Per visualizzare gli eventi per lo spazio a cui hai eseguito l'accesso, seleziona **ActivityTracker_Space_Dashboard_in_24h**.


## Limitazioni
{: #limitations}

 A causa di limitazioni in Kibana, non puoi avere più schede browser Kibana aperte contemporaneamente nella stessa sessione per visualizzare account e spazi differenti. Pertanto, se hai due o più sessioni aperte contemporaneamente e modifichi il dominio dallo spazio all'account o viceversa, potresti riscontrare dei problemi.
	



