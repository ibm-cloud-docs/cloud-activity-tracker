---

copyright:
  years: 2016, 2017

lastupdated: "2017-09-25"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# Programma di traccia dell'attività 
{: #activity_tracker_ov}

Utilizza il servizio {{site.data.keyword.cloudaccesstrailfull}} per tracciare come le applicazioni interagiscono con i servizi {{site.data.keyword.Bluemix}}. Utilizza {{site.data.keyword.cloudaccesstrailshort}} per monitorare attività anomala e rispettare i requisiti di controllo normativi. Gli eventi vengono raccolti conformi agli standard CADF (Cloud Auditing Data Federation).
{:shortdesc}

* {{site.data.keyword.cloudaccesstrailshort}} offre governance di sicurezza di alto livello
per le tue risorse IT nel cloud.
* {{site.data.keyword.cloudaccesstrailshort}} fornisce una soluzione per gli amministratori
di rete per acquisire, memorizzare, visualizzare, cercare e monitorare l'attività API
in un solo posto. 
* {{site.data.keyword.cloudaccesstrailshort}} fornisce capacità per scaricare gli eventi che possono venire utilizzati per generare un report audit trail. Puoi richiedere
questi report in modo che la tua organizzazione sia conforme con i regolamenti interni, le normative di settore esterne
e i regolamenti nazionali.

La conformità con le politiche interne e le normative di settore sono un requisito chiave nella
strategia aziendale, indipendentemente da dove vengono eseguite le applicazioni: in locale, in un cloud ibrido
o in un cloud pubblico. Il servizio {{site.data.keyword.cloudaccesstrailshort}}
fornisce il framework e la funzionalità per monitorare le chiamate API ed esegue il controllo di conformità
con le politiche aziendali e le normative specifiche per il settore di marketing.  

Quando lavori in un ambiente cloud, come ad esempio {{site.data.keyword.Bluemix_notm}},
devi pianificare la strategia cloud per il controllo e il monitoraggio dei carichi di lavoro e dei dati in conformità alle tue politiche interne
e ai requisiti di conformità su base nazionale e di settore. Puoi utilizzare le informazioni registrate tramite il servizio
{{site.data.keyword.cloudaccesstrailshort}} per identificare
gli incidenti di sicurezza, individuare un accesso non autorizzato ed essere conforme con le normative
e i requisiti di controllo interni.

Ad esempio, puoi utilizzare i log di attività {{site.data.keyword.cloudaccesstrailshort}} per identificare le seguenti informazioni: 

* Gli utenti che hanno effettuato le chiamate API ai servizi cloud. 
* L'indirizzo IP di origine da dove le chiamate API sono state effettuate.
* La data/ora in cui le chiamate API sono state effettuate.
* Lo stato della chiamata API.


## Provisioning del programma di traccia dell'attività in Bluemix
{: #provision}

È necessario eseguire il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}} in ogni spazio del tuo account
{{site.data.keyword.Bluemix_notm}} se desideri monitorare l'attività API ai servizi cloud in esecuzione in tale spazio.

Per informazioni su come eseguire il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}, consulta
[Provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/how-to/provision.html#provision).



## Raccolta dei log di attività
{: #collect}

Il servizio {{site.data.keyword.cloudaccesstrailshort}}
acquisisce solo i dati di attività relativi alle chiamate API e ad altre azioni effettuate nei servizi cloud selezionati in {{site.data.keyword.Bluemix_notm}}. Consulta [Servizi cloud supportati](/docs/services/cloud-activity-tracker/cloud_services.html#cloud_services) per un elenco di servizi.

* Gli eventi vengono raccolti automaticamente. 
* Gli eventi vengono raccolti in {{site.data.keyword.cloudaccesstrailshort}} conformi agli standard CADF (Cloud Auditing Data Federation). Lo standard CADF definisce un modello evento completo che include le informazioni necessarie per
certificare, gestire e controllare la sicurezza delle applicazioni negli ambienti cloud.

Il modello evento CADF include i seguenti componenti: 

<table>
  <caption>Tabella 1. Componenti disponibili in un modello dell'evento CADF</caption>
  <tr>
    <th>Componente </th>
	<th>Descrizione</th>
  </tr>
  <tr>
    <td>Azione</td>
	<td>L'azione è l'operazione o l'attività eseguita, tentata o in attesa di completamento da un iniziatore. </td>
  </tr>
  <tr>
    <td>Iniziatore </td>
	<td>L'iniziatore è la risorsa che esegue una chiamata API e genera un evento
CADF. L'evento che viene attivato dipende dall'azione che è stata richiesta dalla chiamata
API.</td>
  </tr>
  <tr>
    <td>Osservatore</td>
	<td>L'osservatore è la risorsa che crea e archivia un record CADF
dalle informazioni disponibili in un evento CADF. </td>
  </tr>
  <tr>
    <td>Risultato </td>
	<td>Il risultato è lo stato dell'azione per la destinazione. </td>
  </tr>
  <tr>
    <td>Destinazione</td>
	<td>La destinazione è la risorsa su cui viene eseguita, tentata o è in attesa di completamento
l'azione. </td>
  </tr>
</table>


Considera le seguenti informazioni quando utilizzi il log {{site.data.keyword.cloudaccesstrailshort}} nel cloud pubblico {{site.data.keyword.IBM_notm}}:

* Puoi solo memorizzare i record di controllo delle chiamate API effettuate alle risorse eseguite nel cloud pubblico {{site.data.keyword.IBM_notm}}.
* Viene utilizzata solo l'archiviazione cloud pubblica {{site.data.keyword.IBM_notm}} per raccogliere gli eventi.
* Le informazioni vengono memorizzate per 3 giorni. Dopo tale intervallo, le informazioni vengono eliminate su base
primo arrivato primo eliminato.
* Gli eventi CADF del tipo *Activity* sono supportati dal servizio {{site.data.keyword.cloudaccesstrailshort}}.



## Analisi dei log attività
{: #analyze}

Puoi analizzare i log attività tramite l'IU {{site.data.keyword.cloudaccesstrailshort}}
in {{site.data.keyword.Bluemix_notm}} o utilizzando Kibana, uno strumento open source. Puoi monitorare gli eventi disponibili in uno spazio specifico o al livello dell'account.

Puoi ricercare, analizzare e monitorare i log attività per le ultime 24 ore tramite l'IU
{{site.data.keyword.cloudaccesstrailshort}} in {{site.data.keyword.Bluemix_notm}}. Per ulteriori informazioni, consulta
[Passaggio all'IU {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_at_ui.html#launch_at_ui).

Puoi ricercare, analizzare e monitorare i log attività per gli ultimi 3 giorni tramite Kibana utilizzando il dashboard Kibana
{{site.data.keyword.cloudaccesstrailshort}} o creando i tuoi propri dashboard personalizzati. * **Nota:** questa funzione è disponibile per gli utenti del piano **Premium**.

* Per ulteriori informazioni su come avviare Kibana, consulta
[Passaggio al dashboard Kibana](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_kibana.html#launch_kibana). 
* Per un elenco di campi che puoi utilizzare per analizzare gli eventi in Kibana, consulta
[Campi evento {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/reference/at_event.html#at_event)



## Regioni
{: #regions}

Il servizio {{site.data.keyword.cloudaccesstrailshort}} è disponibile nelle seguenti regioni: 

* Stati Uniti Sud
* Regno Unito (Beta) 


## Piano di servizio
{: #plan}

Il servizio {{site.data.keyword.cloudaccesstrailshort}} fornisce più piani.

Puoi modificare un piano tramite l'IU {{site.data.keyword.Bluemix_notm}} o con la riga di comando. Puoi aggiornare o ridurre il tuo piano in qualsiasi momento. Per ulteriori informazioni sugli aggiornamenti del piano di servizio in {{site.data.keyword.Bluemix_notm}}, consulta [Modifica del piano](/docs/services/cloud-activity-tracker/plan/change_plan.html#change_plan). 

Le seguenti tabelle illustrano le funzioni che sono disponibili in ogni piano di servizio: 

<table>
    <caption>Tabella 1. Funzionalità per l'inserimento, la conservazione e l'esportazione degli eventi.</caption>
      <tr>
        <th>Piano</th>
        <th>Inserimento evento</th>
        <th>Conservazione evento</th>
		<th>Esporta eventi </th>
      </tr>
      <tr>
        <td>Lite (predefinito)</td>
        <td>No</td>
        <td>Ultimi 3 giorni</td>
		<td>No</td>
      </tr>
      <tr>
        <td>Premium</td>
        <td>Sì</td>
        <td>Numero di giorni configurabile.</td>
		<td>Sì</td>
      </tr>
</table>

<table>
    <caption>Tabella 2. Funzionalità per la gestione e la visualizzazione degli eventi.</caption>
      <tr>
        <th>Piano</th>
		<th>API</th>
		<th>CLI</th>
        <th>Kibana</th>
      </tr>
      <tr>
        <td>Lite (predefinito)</td>
		<td>No</td>
		<td>No</td>
        <td>No</td>
      </tr>
      <tr>
        <td>Premium</td>
		<td>Sì</td>
		<td>Sì</td>
        <td>Sì</td>
      </tr>
</table>

**Nota:** il costo mensile dell'archiviazione degli eventi viene calcolato come una media del ciclo di fatturazione.

## Sicurezza
{: #security}

Considera le seguenti informazioni sulla sicurezza quando utilizzi il servizio {{site.data.keyword.cloudaccesstrailshort}}:

* I servizi IBM che generano gli eventi {{site.data.keyword.cloudaccesstrailshort}} seguono la politica di sicurezza cloud {{site.data.keyword.IBM_notm}}. Per ulteriori informazioni, consulta [Trust the security and privacy of IBM Cloud ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud-computing/learn-more/why-ibm-cloud/security/){: new_window}.
* Il servizio {{site.data.keyword.cloudaccesstrailshort}} acquisisce le azioni avviate dall'utente che modificano lo stato dei servizi cloud. Le informazioni non forniscono l'accesso diretto al database o alle applicazioni.
* Soltanto gli utenti autorizzati possono visualizzare e monitorare i log evento {{site.data.keyword.cloudaccesstrailshort}}. Ogni utente viene identificato
tramite il proprio ID univoco {{site.data.keyword.Bluemix_notm}}.
