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


# Monitoraggio dell'attività di {{site.data.keyword.keymanagementserviceshort}} con {{site.data.keyword.cloudaccesstrailshort}}
{: #kp}

Utilizza questa esercitazione per imparare ad utilizzare il servizio {{site.data.keyword.cloudaccesstrailfull}} per monitorare l'interazione di un'utente con il servizio {{site.data.keyword.keymanagementserviceshort}}.
{:shortdesc}

Gli obiettivi di questa esercitazione sono i seguenti:

1. Mostrare come eseguire il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}.
2. Mostrare come utilizzare un servizio cloud per generare gli eventi attività raccolti automaticamente dal servizio {{site.data.keyword.cloudaccesstrailshort}}. Gli eventi sono conformi agli standard [Cloud Auditing Data Federation (CADF) ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.dmtf.org/sites/default/files/standards/documents/DSP0262_1.0.0.pdf){: new_window}.
3. Mostrare come monitorare l'attività cloud di un servizio utilizzando i dashboard {{site.data.keyword.cloudaccesstrailshort}} predefiniti.

La seguente figura mostra i diversi componenti e azioni che si verificano quando un'attività avviata dall'utente modifica lo stato di un servizio:

![Componenti e azioni che si verificano quando un'attività avviata dall'utente modifica lo stato di un servizio](../images/AT_f1.png "Componenti e azioni che si verificano quando un'attività avviata dall'utente modifica lo stato di un servizio")



## Prima di iniziare
{: #kp_prereqs}

Crea un [account {{site.data.keyword.cloud_notm}}](https://cloud.ibm.com/registration/). Il tuo ID utente deve essere un membro o un proprietario di un account {{site.data.keyword.cloud_notm}}, con autorizzazioni da sviluppatore nello spazio in cui pianifichi di utilizzare il servizio {{site.data.keyword.cloudaccesstrailshort}}.


## Passo 1: esegui il provisioning del programma di traccia dell'attività
{: #kp_step1}

Devi eseguire il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}} nella stessa regione in cui viene eseguito il provisioning del servizio cloud di cui desideri monitorare l'attività. Dopo aver eseguito il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}, gli eventi vengono raccolti automaticamente dai servizi cloud selezionati. 

**Nota:** questa esercitazione mostra come utilizzare il servizio {{site.data.keyword.cloudaccesstrailshort}} per monitorare un'interazione dell'utente con il servizio cloud {{site.data.keyword.keymanagementservicelong_notm}} nella regione Stati Uniti Sud. Pertanto, devi eseguire il provisioning di {{site.data.keyword.cloudaccesstrailshort}} nella regione Stati Uniti Sud. Per visualizzare le informazioni su quale regione è disponibile un servizio, consulta [Servizi per regione](/docs/resources/services_region.html#services_region).

Completa la seguente procedura per eseguire il provisioning di un'istanza del servizio {{site.data.keyword.cloudaccesstraillong_notm}} in {{site.data.keyword.cloud_notm}}:

1. Accedi a {{site.data.keyword.cloud_notm}}.

    Il dashboard {{site.data.keyword.cloud_notm}} può essere trovato all'indirizzo: [http://cloud.ibm.com ![Icona link esterno](../../../icons/launch-glyph.svg "Icona link esterno")](http://cloud.ibm.com){:new_window}.
    
	Dopo aver eseguito l'accesso con i tuoi ID e password utente, viene aperta la IU {{site.data.keyword.cloud_notm}}.

2. Fai clic su **Catalogo**. Viene aperto l'elenco dei servizi disponibili in {{site.data.keyword.cloud_notm}}.

3. Seleziona la categoria **Sicurezza e identità** per filtrare l'elenco dei servizi visualizzati.

    **Nota:** il servizio è anche disponibile tramite la categoria **Strumenti di sviluppo**.

4. Fai clic sul tile **Programma di traccia dell'attività**. 

5. Configura le informazioni che definiscono dove viene eseguito il provisioning del servizio. 

    Immetti i dati come indicato nella seguente tabella: 

    <table>
	  <caption>Tabella 1. Campi obbligatori per eseguire il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}</caption>
	  <tr>
	    <th width="50%">Campo</th>
		<th width="50%">Valore</th>
	  </tr>
	  <tr>
	    <td>Seleziona la regione a cui distribuire:</td>
		<td>Stati Uniti Sud</td>
	  </tr>
	  <tr>
	    <td>Scegli un'organizzazione:</td>
		<td>Seleziona l'organizzazione in cui scegli di eseguire il provisioning del tuo piano {{site.data.keyword.cloudaccesstrailshort}}.</td>
	  </tr>
	  <tr>
	    <td>Scegli uno spazio:</td>
		<td>Seleziona lo spazio nell'organizzazione selezionata in cui vuoi eseguire il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}.</td>
	  </tr>
	</table>

6. Fai clic su **Crea** per eseguire il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}} nello spazio in cui hai eseguito l'accesso.
   

## Passo 2:  Configura il servizio cloud  
{: #kp_step2}

Questa esercitazione illustra come monitorare l'attività dell'API per il servizio {{site.data.keyword.keymanagementserviceshort}} in {{site.data.keyword.cloud_notm}}.

Completa la seguente procedura per configurare il servizio {{site.data.keyword.keymanagementserviceshort}} in {{site.data.keyword.cloud_notm}}:

1. Esegui il provisioning di un'istanza del servizio {{site.data.keyword.keymanagementserviceshort}} nella regione Stati Uniti Sud. Per ulteriori informazioni, vedi [Provisioning dalla console IBM Cloud](/docs/services/key-protect/provision.html#provision).

2. Definisci le autorizzazioni {{site.data.keyword.cloud_notm}} per l'utente che stai pianificando di utilizzare con le chiavi. 

    * Un utente ha bisogno di una politica IAM con un ruolo del servizio impostato su *gestore* o *scrittore* per poter creare le chiavi.
	* Un utente ha bisogno di una politica IAM con un ruolo del servizio impostato su *gestore* per poter eliminare le chiavi.
	* Un utente ha bisogno di una politica IAM con un ruolo del servizio impostato su *lettore* per poter visualizzare le chiavi. 


## Passo 3: Genera un evento del programma di traccia dell'attività
{: #kp_step3}

In questo passo, crea una chiave di sicurezza utilizzando il servizio {{site.data.keyword.keymanagementserviceshort}} per generare i dati dell'evento
{{site.data.keyword.cloudaccesstrailshort}}. Per ulteriori informazioni, consulta [Creazione di nuove chiavi](/docs/services/key-protect/create-standard-keys.html#create-standard-keys).

* Gli eventi {{site.data.keyword.cloudaccesstrailshort}} vengono generati come risultato della creazione di una chiave.
* Gli eventi {{site.data.keyword.cloudaccesstrailshort}} sono disponibili nel **dominio dell'account** {{site.data.keyword.cloudaccesstrailshort}}disponibile nella regione {{site.data.keyword.cloud_notm}} in cui vengono generati gli eventi. 

## Passo 4: Monitora un evento del programma di traccia dell'attività
{: #kp_step4}

In questo passo, verifica tramite la IU {{site.data.keyword.cloud_notm}} che gli eventi {{site.data.keyword.cloudaccesstrailshort}} siano stati generati.

Completa la seguente procedura per verificare che un evento è stato creato:

1. Concedi le autorizzazioni all'utente per visualizzare gli eventi dell'account. Per ulteriori informazioni, vedi [Visualizzazione degli eventi dell'account](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/viewing_events.html#view_acc_events_account_events) e [Concessione delle autorizzazioni per visualizzare gli eventi dell'account](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_acc_events).

2. Dal dashboard {{site.data.keyword.cloud_notm}}, seleziona il servizio {{site.data.keyword.cloudaccesstrailshort}}. Viene aperto il dashboard del servizio.

3. Configura la vista per ricercare gli eventi {{site.data.keyword.keymanagementserviceshort}} che sono stati generati quando hai eseguito il provisioning del servizio e aggiunto una chiave.

    * Seleziona **Account logs** per il campo *View logs*.
    * Seleziona ** target.typeURI_str** per il campo *Search field* e immetti **kms/secrets** nel campo *Filter*.
	
    I dati visualizzati mostrano gli eventi {{site.data.keyword.keymanagementserviceshort}} disponibili per le ultime 24 ore. 
	


## Passo successivo
{: #kp_next_steps}

Successivamente, utilizza il dashboard Kibana predefinito {{site.data.keyword.cloudaccesstrailshort}} per monitorare e analizzare i log evento. Per avviare Kibana, consulta [Passaggio al dashboard Kibana](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_kibana.html#launch_kibana). Per impostazione predefinita, in Kibana, i log di attività dello spazio vengono visualizzati tramite il dashboard **ActivityTracker_Space_Dashboard_in_24h**:

Puoi anche utilizzare la CLI {{site.data.keyword.cloudaccesstrailshort}} per gestire i tuoi eventi dalla riga di comando. Per ulteriori informazioni, vedi [Visualizzazione di informazioni sull'evento](/docs/services/cloud-activity-tracker/how-to/viewing_event_information.html#viewing_event_status).



