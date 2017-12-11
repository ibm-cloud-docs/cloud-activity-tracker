---

copyright:
  years: 2016, 2017

lastupdated: "2017-09-07"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# Gestione degli eventi utilizzando la CLI del programma di traccia dell'attività
{: #tutorial2}

Utilizza questa esercitazione per informazioni su come utilizzare la CLI {{site.data.keyword.cloudaccesstrailshort}} per gestire gli eventi tramite la riga di comando. Impara come ottenere le informazioni sugli eventi archiviati, su come scaricare gli eventi archiviati nel cloud {{site.data.keyword.IBM_notm}} o su come eliminare gli eventi.
{:shortdesc}

Completa la seguente
procedura:

1. [Esegui il provisioning del servizio {{site.data.keyword.IBM_notm}} Key Protect e genera gli eventi](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step1)
2. [Ottieni le informazioni sugli eventi archiviati (cf at status)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step2)
2. [Specifica quale log scaricare creando una sessione (cf at session create)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step3)
3. [Ottieni i dati di log correnti (cf at download)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step4)
4. [Elimina la sessione dopo il completamento del download (cf at session delete)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step5)
5. [Elimina manualmente i log non necessari (cf at delete)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step6)


## Premesse
{: #assumptions}

1. Devi avere un ID utente {{site.data.keyword.Bluemix_notm}} con autorizzazioni da sviluppatore per utilizzare uno spazio di un account {{site.data.keyword.Bluemix_notm}} dove è stato eseguito il provisioning del servizio {{site.data.keyword.IBM_notm}} Cloud {{site.data.keyword.cloudaccesstrailshort}}. 

    Per ulteriori informazioni su come eseguire il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}, consulta
[Provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/how-to/provision.html#provision).

2. Hai installato il plugin CF {{site.data.keyword.cloudaccesstrailshort}} nel tuo sistema locale. È necessario per poter utilizzare la CLI {{site.data.keyword.cloudaccesstrailshort}} per gestire gli eventi tramite la riga di comando. 

    Per ulteriori informazioni sull'installazione del plugin CF {{site.data.keyword.cloudaccesstrailshort}}, consulta
[Configurazione della CLI {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#config_at_cli).

3. Hai eseguito l'accesso a {{site.data.keyword.Bluemix_notm}} tramite la riga di comando utilizzando il seguente comando:

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

    Ad esempio, immetti il seguente comando per accedere dalla regione Stati Uniti Sud:
	
	```
	bx cf login -a api.ng.bluemix.net
	```
	{: codeblock}

	**Nota:** devi accedere alla regione, organizzazione e spazio in {{site.data.keyword.Bluemix_notm}} in cui è stato eseguito il provisioning del servizio
{{site.data.keyword.cloudaccesstrailshort}} per poter eseguire i comandi {{site.data.keyword.cloudaccesstrailshort}} e gestire i tuoi eventi tramite la riga di comando.
	
	Quindi, imposta l'organizzazione e lo spazio. Esegui il seguente comando:

    ```
    bx target -o OrgName -s SpaceName
    ```
    {: codeblock}

    dove

    * OrgName è il nome dell'organizzazione.
    * SpaceName è il nome dello spazio.


## Passo 1: Esegui provisioning del servizio IBM Key Protect e genera gli eventi 
{: #step1}
	
1. Completa la seguente procedura per eseguire il provisioning di un'istanza del servizio {{site.data.keyword.keymanagementserviceshort}} in {{site.data.keyword.Bluemix_notm}}:

    1. Accedi al tuo account {{site.data.keyword.Bluemix_notm}}.

        Il dashboard {{site.data.keyword.Bluemix_notm}} può essere trovato all'indirizzo: [http://bluemix.net](http://bluemix.net)

        Dopo aver eseguito l'accesso con i tuoi ID e password utente, viene aperta la IU {{site.data.keyword.Bluemix_notm}}.

    2. Fai clic su **Catalogo**. Viene aperto l'elenco dei servizi disponibili in {{site.data.keyword.Bluemix_notm}}.

        Seleziona la categoria **Sicurezza** per filtrare l'elenco dei servizi visualizzati.

    3. Seleziona il tile **Key Protect**.

    4. Fai clic su **Crea** per eseguire il provisioning del servizio {{site.data.keyword.keymanagementserviceshort}} nello spazio
{{site.data.keyword.Bluemix_notm}} in cui hai eseguito l'accesso.

2. Completa la seguente procedura per generare un evento {{site.data.keyword.cloudaccesstrailshort}}:

    1. Dal dashboard {{site.data.keyword.Bluemix_notm}}, seleziona il servizio {{site.data.keyword.keymanagementserviceshort}},
Viene aperto il dashboard {{site.data.keyword.keymanagementserviceshort}}. Quindi, seleziona la scheda **Gestisci**.

    2. Fai clic su **Aggiungi chiave**. Viene visualizzata una nuova finestra.

        Finestra ![{{site.data.keyword.keymanagementserviceshort}} per aggiungere le chiavi](images/KP_f2.gif)

    3. Seleziona **Genera chiave** e completa le seguenti istruzioni:

        * Immetti un nome per la chiave, ad esempio, *MyFirstKey*.

        * Scegli un algoritmo per la chiave.

        * Fai clic su **Aggiungi chiave**. 

3. Verifica che sia stato creato un evento:

    1. Dal dashboard {{site.data.keyword.Bluemix_notm}}, seleziona il servizio {{site.data.keyword.cloudaccesstrailshort}}. Viene aperto il dashboard del servizio.

    2. Configura la vista per ricercare gli eventi {{site.data.keyword.keymanagementserviceshort}} che sono stati generati quando hai eseguito il provisioning del servizio e aggiunto una chiave.

        * Seleziona **Space logs** per il campo *View logs*.
	    * Seleziona **target.name** per il campo *Search field*.
	    * Immetti **ibm-key-protect** nel campo *Filter*.
	
	    I dati visualizzati corrispondo agli eventi {{site.data.keyword.keymanagementserviceshort}} disponibili per le ultime 24 ore.  

	    Scheda gestione ![{{site.data.keyword.cloudaccesstrailshort}} ](images/KP_f3.gif)

## Passo 2: Ottieni le informazioni sugli eventi archiviati.
{: #step2}

Verifica quali eventi sono disponibili per il download. Ad esempio, se esegui il provisioning e aggiungi una chiave nella data corrente, immetti il seguente comando per ottenere le informazioni sugli eventi raccolti oggi:

```
bx cf at status -s 2017-07-25 -e 2017-07-25
+------------+-------+-------+------------+
| Date       | Count | Size  | Searchable |
+------------+-------+-------+------------+
| 2017-07-25 | 12    | 34994 | All        |
+------------+-------+-------+------------+
```
{: screen}

Questo comando calcolerà gli eventi del 25 giugno 2017.  {{site.data.keyword.cloudaccesstrailshort}} è un servizio globale, tuttavia, i giorni sono Universal Time. Per ottenere un giorno con ora locale completo, potresti dover scaricare più giorni UTC.

Per visualizzare le informazioni per più giorni, utilizza `-s` per impostare il giorno di inizio e `-e` per la data di fine. 

Per ulteriori informazioni sul comando `cf at status`, fai riferimento a
[Guida di riferimento alla CLI](/docs/services/cloud-activity-tracker/cli/at_cli.html#status).

Utilizza `bx cf at help status` per ottenere supporto dalla riga di comando.

## Passo 3: Specifica quali eventi scaricare
{: #step3}

Prima di scaricare gli eventi, crea una sessione:

* La sessione specifica quali eventi saranno scaricati. 
* Se il download degli eventi viene interrotto, la sessione abilita la ripresa del download da dove era stato interrotto.

Utilizzare il seguente comando per creare una sessione: 

```
bx cf at session create -s 2017-07-25 -e 2017-07-25
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| id           | 21b19aeb-3d32-4c60-b912-517609c62db2      |
| space        | 667fb895-b5f5-46c9-9f0e-cf4587341095      |
| username     | xxx@yyy.com                               |
| create-time  | 2017-07-25T18:33:22.678350874Z            |
| access-time  | 2017-07-25T18:33:22.678350874Z            |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
+--------------+-------------------------------------------+
```

Sono presenti una data di inizio e di fine associate a una sessione. Il comando download includerà gli eventi compresi tra queste date. L'intervallo di date predefinito è solo il giorno corrente. 

La parte importante dell'output del comando è la sessione `Id`. Vi si fa riferimento nel comando download.

Per ottenere le informazioni sulle sessioni esistenti, immetti `cf at session list`.

Per ulteriori informazioni sulle sessioni e sul comando `cf at session create`, fai riferimento a
[Guida di riferimento alla CLI](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_create).

Utilizza `cf at session help create` per ottenere supporto dalla riga di comando.

## Passo 4: Scarica gli eventi identificati per l'ambito definito per la sessione
{: #step4}

Per scaricare gli eventi specificati dai parametri della sessione, immetti il seguente comando: 

```
$ bx cf at events download -o events.log 21b19aeb-3d32-4c60-b912-517609c62db2
 6.70 KiB / 3.06 KiB [================================================================================================================================================================] 219.03% 8.60 MiB/s 0s
Download Successful
```

* Il parametro `-o` specifica un file di output.
* L'ID sessione viene specificato per ultimo. Ottieni il valore dell'ID sessione dall'output del comando `cf at session create`.
* L'indicatore di avanzamento si muove da 0 a 100% come vengono scaricati gli eventi.

Il formato dei dati scaricati è un JSON compresso. 

Per ulteriori informazioni sul comando `cf at download`, fai riferimento a
[Guida di riferimento alla CLI](/docs/services/cloud-activity-tracker/cli/at_cli.html#download).

Utilizza `bx cf at help download` per ottenere supporto dalla riga di comando.

## Passo 5: Elimina la sessione
{: #step5}

Al termine del download, elimina la sessione.  

Il numero di sessioni è limitato. Una sessione non viene eliminata automaticamente. Devi eliminare manualmente le sessioni che non sono necessarie.  

```
$ bx cf at session delete 21b19aeb-3d32-4c60-b912-517609c62db2
+---------+------------------------+
| name    | value                  |
+---------+------------------------+
| message | Delete session success |
+---------+------------------------+
```

Per ulteriori informazioni sul comando `cf at session delete`, fai riferimento a
[Guida di riferimento alla CLI](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_delete).

Utilizza `bx cf at session help delete` per ottenere supporto dalla riga di comando.

## Passo 6: Elimina gli eventi dal programma di traccia dell'attività manualmente
{: #step6}

Hai il controllo della tua propria conservazione dell'evento in {{site.data.keyword.cloudaccesstrailshort}}. Puoi eliminare gli eventi manualmente  o puoi automatizzare l'eliminazione di eventi. 

Per eliminare gli eventi manualmente, esegui il comando `cf at delete`. Ad esempio,

```
$ bx cf at delete -s 2017-07-25 -e 2017-07-25
Deleted successfully
"6 logs were deleted,freeing 13737 bytes."
```

Per ulteriori informazioni sul comando `cf at delete`, fai riferimento a
[Guida di riferimento alla CLI](/docs/services/cloud-activity-tracker/cli/at_cli.html#delete).

Utilizza `bx cf at help delete` per ottenere supporto dalla riga di comando.

**Nota:** per eliminare gli eventi automaticamente, puoi impostare una politica di conservazione utilizzando il comando della CLI `cf at option`. Per ulteriori informazioni, vedi [Guida di riferimento alla CLI](/docs/services/cloud-activity-tracker/cli/at_cli.html#option)


