---

copyright:
  years: 2016, 2017

lastupdated: "2017-09-19"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# Monitoraggio dell'attività di Key Protect 
{: #kp_at}

Utilizza il servizio {{site.data.keyword.cloudaccesstrailfull}} per tracciare come le applicazioni interagiscono con il servizio
{{site.data.keyword.keymanagementservicelong_notm}} in {{site.data.keyword.Bluemix}}.
{:shortdesc}

## Informazioni su Key Protect
{: #about}

{{site.data.keyword.keymanagementserviceshort}} è un servizio di gestione della chiave di crittografia. Puoi utilizzare il servizio {{site.data.keyword.keymanagementserviceshort}} per eseguire il provisioning delle chiavi crittografate per le applicazioni in {{site.data.keyword.Bluemix_notm}}. Per ulteriori informazioni, consulta [Introduzione a Key Protect](/docs/services/keymgmt/index.html#getting-started-with-key-protect).

Per gestire le chiavi di crittografia, puoi crearle ed eliminarle tramite la IU {{site.data.keyword.Bluemix_notm}}
o in modo programmatico utilizzando l'[API IBM Key Protect](https://docs-api-keyprotect.ng.bluemix.net/#/){: new_window}.


## Come funziona
{: #how}

In {{site.data.keyword.Bluemix_notm}}, per monitorare il tracciato di attività del servizio
{{site.data.keyword.keymanagementserviceshort}}, devi eseguire il provisioning del servizio
{{site.data.keyword.cloudaccesstrailshort}} nello stesso spazio in cui è stato eseguito il provisioning del servizio
{{site.data.keyword.keymanagementserviceshort}}. Dopo che è stato eseguito il provisioning di entrambi i servizi e che sono in esecuzione, gli eventi attività vengono generati e automaticamente raccolti nel log
{{site.data.keyword.cloudaccesstrailshort}} quando crei, leggi o elimini una chiave. 

A causa della riservatezza delle informazioni di una chiave crittografata,
quando viene generato un evento come risultato di una chiamata API al servizio
{{site.data.keyword.keymanagementserviceshort}}, l'evento generato non include le informazioni dettagliate sulla chiave. L'evento include un ID di correlazione che può essere utilizzato
per identificare la chiave internamente nel tuo ambiente cloud. L'ID di correlazione è un campo restituito come parte del campo **responseHeader.content**. Utilizza queste informazioni per collegare i dati sensibili della chiave di crittografia con le informazioni
dell'azione riportata tramite l'evento.

La seguente figura mostra i diversi componenti e azioni che si verificano quando un utente effettua una chiamata
API per creare una chiave:

![Componenti e azioni differenti che si verificano quando un utente effettua una chiamata API per creare un chiave](images/KP_AT_F1.png "Componenti e azioni differenti che si verificano quando un utente effettua una chiamata API per creare un chiave")

## Metodi API
{: #methods}

La seguente tabella elenca i metodi API {{site.data.keyword.keymanagementserviceshort}} che generano un evento quando vengono richiamati:

<table>
  <caption>Tabella 1. Metodi API</caption>
  <tr>
    <th>Metodo</th>
	<th>Descrizione</th>
  <tr>
  <tr>
    <td>GET /secrets </td>
	<td>Richiama i segreti</td>
  </tr>
  <tr>
    <td>POST /secrets </td>
	<td>Crea un segreto</td>
  </tr>
  <tr>
    <td>DELETE /secrets/{id}</td>
	<td>Elimina un segreto per ID</td>
  </tr>
  <tr>
    <td>GET /secrets/{id} </td>
	<td>Richiama un segreto per ID</td>
  </tr>  
</table>

**Nota:** un segreto è una chiave di crittografia.

 	
 	
## Esercitazione: Monitorare l'attività di IBM Key Protect nel cloud
{: #tutorial1}

Utilizza questa esercitazione per informazioni su come puoi monitorare un'interazione dell'utente con il servizio cloud {{site.data.keyword.keymanagementservicelong_notm}}. 

In questa esercitazione, crei una chiave di sicurezza in {{site.data.keyword.keymanagementserviceshort}} (KP). Il servizio KP Cloud è stato abilitato ad inviare gli eventi a {{site.data.keyword.cloudaccesstrailshort}} quando un utente crea una chiave tramite la IU, la CLI o l'API. Dopo aver creato la chiave, puoi monitorare gli eventi tramite la IU {{site.data.keyword.cloudaccesstrailshort}} e tramite Kibana.

Questa esercitazione ti mostrerà come: 

1. [Eseguire il provisioning del servizio {{site.data.keyword.keymanagementserviceshort}}](/docs/services/cloud-activity-tracker/tutorials/key_protect.html#step1)
2. [Creare una chiave di sicurezza in {{site.data.keyword.keymanagementserviceshort}} per generare i dati dell'evento {{site.data.keyword.cloudaccesstrailshort}} ](/docs/services/cloud-activity-tracker/tutorials/key_protect.html#step2)
3. [Verificare tramite la IU {{site.data.keyword.Bluemix_notm}} che gli eventi {{site.data.keyword.cloudaccesstrailshort}} siano stati generati ](/docs/services/cloud-activity-tracker/tutorials/key_protect.html#step3)

### Premesse
{: #assumptions}

Devi avere un ID utente {{site.data.keyword.Bluemix_notm}} con autorizzazioni da sviluppatore per utilizzare uno spazio di un account {{site.data.keyword.Bluemix_notm}} in cui viene eseguito il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}. 


### Passo 1: esegui il provisioning del programma di traccia dell'attività
{: #step1}

Devi eseguire il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}} negli stessi spazio e regione in cui viene eseguito il provisioning del servizio cloud di cui desideri monitorare l'attività. Dopo aver eseguito il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}, gli eventi vengono raccolti automaticamente dai servizi cloud selezionati di cui è stato eseguito il provisioning in tale spazio. Consulta [Servizi cloud supportati](/docs/services/cloud-activity-tracker/cloud_services.html#cloud_services) per un elenco di servizi di cui vuoi monitorare l'attività tramite {{site.data.keyword.cloudaccesstrailshort}}.

**Nota:** questa esercitazione mostra come utilizzare il servizio {{site.data.keyword.cloudaccesstrailshort}} per monitorare un'interazione dell'utente con il servizio cloud {{site.data.keyword.keymanagementservicelong_notm}}. Il servizio {{site.data.keyword.keymanagementserviceshort}} è disponibile in Stati Uniti Sud. Pertanto, devi eseguire il provisioning di {{site.data.keyword.cloudaccesstrailshort}} nella regione Stati Uniti Sud, nello stesso spazio in cui è disponibile il servizio {{site.data.keyword.keymanagementserviceshort}}. Per visualizzare le informazioni su quale regione è disponibile un servizio, consulta [Servizi per regione](/docs/services/services_region.html#services_region).

Completa la seguente procedura per eseguire il provisioning di un'istanza del servizio {{site.data.keyword.cloudaccesstraillong_notm}} in {{site.data.keyword.Bluemix_notm}}:

1. Accedi al tuo account {{site.data.keyword.Bluemix_notm}}.

    Il dashboard {{site.data.keyword.Bluemix_notm}} può essere trovato all'indirizzo: [http://bluemix.net ![Icona link esterno](../../../icons/launch-glyph.svg "Icona link esterno")](http://bluemix.net){:new_window}.
    
	Dopo aver eseguito l'accesso con i tuoi ID e password utente, viene aperta la IU {{site.data.keyword.Bluemix_notm}}.

2. Fai clic su **Catalogo**. Viene aperto l'elenco dei servizi disponibili in {{site.data.keyword.Bluemix_notm}}.

3. Seleziona la categoria **Sicurezza** per filtrare l'elenco dei servizi visualizzati.

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
		<td>Seleziona l'organizzazione in cui il tuo piano monitora l'attività.</td>
	  </tr>
	  <tr>
	    <td>Scegli uno spazio:</td>
		<td>Seleziona lo spazio nell'organizzazione selezionata in cui il tuo piano monitora l'attività.</td>
	  </tr>
	</table>

6. Fai clic su **Crea** per eseguire il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}} nello spazio
{{site.data.keyword.Bluemix_notm}} in cui hai eseguito l'accesso.
   

### Passo 2: Provisioning di Key Protect 
{: #step2}
	
Completa la seguente procedura per eseguire il provisioning di un'istanza del servizio {{site.data.keyword.keymanagementserviceshort}} nella regione Stati Uniti Sud di {{site.data.keyword.Bluemix_notm}}:

1. Accedi al tuo account {{site.data.keyword.Bluemix_notm}}.

    Il dashboard {{site.data.keyword.Bluemix_notm}} può essere trovato all'indirizzo: [http://bluemix.net ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://bluemix.net){:new_window}
	
	Dopo aver eseguito l'accesso con i tuoi ID e password utente, viene aperta la IU {{site.data.keyword.Bluemix_notm}}.

2. Fai clic su **Catalogo**. Viene aperto l'elenco dei servizi disponibili in {{site.data.keyword.Bluemix_notm}}.

    Seleziona la categoria **Sicurezza** per filtrare l'elenco dei servizi visualizzati.

3. Seleziona il tile **Key Protect**.

4. Configura le informazioni che definiscono dove viene eseguito il provisioning del servizio. 

    Immetti i dati come indicato nella seguente tabella: 

    <table>
	  <caption>Tabella 2. Campi obbligatori per eseguire il provisioning del servizio {{site.data.keyword.keymanagementserviceshort}}</caption>
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
		<td>Seleziona l'organizzazione in cui scegli di eseguire il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}.</td>
	  </tr>
	  <tr>
	    <td>Scegli uno spazio:</td>
		<td>Seleziona lo spazio in cui scegli di eseguire il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}.</td>
	  </tr>
	</table>

5. Fai clic su **Crea** per eseguire il provisioning del servizio {{site.data.keyword.keymanagementserviceshort}} nello spazio
{{site.data.keyword.Bluemix_notm}} in cui hai eseguito l'accesso.


### Passo 3: Crea una chiave di sicurezza in Key Protect per generare i dati dell'evento del programma di traccia dell'attività 
{: # step3}

Completa la seguente procedura per generare un evento {{site.data.keyword.cloudaccesstrailshort}}:

1. Dal dashboard {{site.data.keyword.Bluemix_notm}}, seleziona il servizio **Key Protect**,
Viene aperto il dashboard {{site.data.keyword.keymanagementserviceshort}}. Quindi, seleziona la scheda **Gestisci**.

2. Fai clic su **Aggiungi chiave**. Viene visualizzata una nuova finestra.

    Finestra ![{{site.data.keyword.keymanagementserviceshort}} per aggiungere le chiavi](images/KP_f2.gif)

3. Seleziona **Genera chiave** e completa le seguenti istruzioni:

    * Immetti un nome per la chiave, ad esempio, *MyFirstKey*.

    * Scegli un algoritmo per la chiave.

    * Fai clic su **Aggiungi chiave**. 

### Passo 4: Verifica tramite la IU Bluemix che gli eventi del programma di traccia dell'attività sono stati generati 
{: #step4}

Verifica che sia stato creato un evento:

1. Dal dashboard {{site.data.keyword.Bluemix_notm}}, seleziona il servizio {{site.data.keyword.cloudaccesstrailshort}}. Viene aperto il dashboard del servizio.

2. Configura la vista per ricercare gli eventi {{site.data.keyword.keymanagementserviceshort}} che sono stati generati quando hai eseguito il provisioning del servizio e aggiunto una chiave.

    * Seleziona **Space logs** per il campo *View logs*.
    * Seleziona **target.name** per il campo *Search field*.
    * Immetti **ibm-key-protect** nel campo *Filter*.
	
    I dati visualizzati corrispondo agli eventi {{site.data.keyword.keymanagementserviceshort}} disponibili per le ultime 24 ore.  

    Scheda gestione ![{{site.data.keyword.cloudaccesstrailshort}} ](images/KP_f3.gif)


 	
 	
 	
 	














