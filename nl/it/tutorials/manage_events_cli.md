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



# Gestione degli eventi utilizzando la CLI del programma di traccia dell'attività
{: #tutorial2}

Utilizza questa esercitazione per informazioni su come utilizzare la CLI {{site.data.keyword.cloudaccesstrailshort}} per gestire gli eventi tramite la riga di comando. Impara come ottenere le informazioni sugli eventi archiviati, su come scaricare gli eventi archiviati nel cloud {{site.data.keyword.IBM_notm}} o su come eliminare gli eventi.
{:shortdesc}

Completa la seguente
procedura:

1. [Esegui il provisioning di {{site.data.keyword.keymanagementservicelong_notm}} e genera gli eventi](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#tutorial2_step1)
2. [Ottieni le informazioni sugli eventi archiviati (ibmcloud at status)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#tutorial2_step2)
2. [Specifica quale log scaricare creando una sessione (ibmcloud at session create)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#tutorial2_step3)
3. [Ottieni i dati di log correnti (ibmcloud at download)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#tutorial2_step4)
4. [Elimina la sessione dopo il completamento del download (ibmcloud at session delete)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#tutorial2_step5)
5. [Elimina manualmente i log non necessari (ibmcloud at delete)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#tutorial2_step6)


## Premesse
{: #tutorial2_assumptions}

1. Devi avere un ID utente {{site.data.keyword.cloud_notm}} con autorizzazioni da sviluppatore per utilizzare uno spazio di un account {{site.data.keyword.cloud_notm}} in cui viene eseguito il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}. 

    Per ulteriori informazioni su come eseguire il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}, consulta
[Provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/how-to/provision.html#provision).

2. Hai eseguito il provisioning di un'istanza del servizio {{site.data.keyword.cloudaccesstrailshort}} con un piano premium.

    **Nota:** la CLI {{site.data.keyword.cloudaccesstrailshort}} non è disponibile con il piano Lite.

3. Hai installato la CLI {{site.data.keyword.cloudaccesstrailshort}} nel tuo sistema locale. È necessario per poter utilizzare la CLI {{site.data.keyword.cloudaccesstrailshort}} per gestire gli eventi tramite la riga di comando. 

    Per ulteriori informazioni sull'installazione della CLI {{site.data.keyword.cloudaccesstrailshort}}, consulta [Configurazione della CLI {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/how-to/config_cli.html#config_cli).

4. Hai eseguito l'accesso a {{site.data.keyword.cloud_notm}} tramite la riga di comando. Per questa esercitazione, esegui i seguenti comandi da un terminale: 

    `ibmcloud login -a api.ng.bluemix.net` per accedere alla regione Stati Uniti Sud. Per ulteriori informazioni, vedi [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login).
    
    `ibmcloud target -o OrgName -s SpaceName` per impostare l'organizzazione di destinazione e lo spazio in cui è stato eseguito il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}. Per ulteriori informazioni, vedi [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target).


## Passo 1: Esegui provisioning del servizio IBM Key Protect e genera gli eventi 
{: #tutorial2_step1}
	
Completa la seguente procedura per eseguire il provisioning di {{site.data.keyword.keymanagementserviceshort}} in {{site.data.keyword.cloud_notm}} e generare gli eventi:

1. Esegui il provisioning di un'istanza del servizio {{site.data.keyword.keymanagementserviceshort}} nella regione Stati Uniti Sud. Per ulteriori informazioni, vedi [Provisioning dalla console IBM Cloud](/docs/services/key-protect/provision.html#provision).

2. Definisci le autorizzazioni {{site.data.keyword.cloud_notm}} per l'utente che stai pianificando di utilizzare con le chiavi. 

    * Un utente ha bisogno di una politica IAM con un ruolo del servizio impostato su *gestore* o *scrittore* per poter creare le chiavi.
	* Un utente ha bisogno di una politica IAM con un ruolo del servizio impostato su *gestore* per poter eliminare le chiavi.
	* Un utente ha bisogno di una politica IAM con un ruolo del servizio impostato su *lettore* per poter visualizzare le chiavi. 

3. Crea una chiave di sicurezza utilizzando il servizio {{site.data.keyword.keymanagementserviceshort}} per generare i dati dell'evento {{site.data.keyword.cloudaccesstrailshort}}. Per ulteriori informazioni, consulta [Creazione di nuove chiavi](/docs/services/key-protect/create-standard-keys.html#create-standard-keys).

Gli eventi {{site.data.keyword.cloudaccesstrailshort}} vengono generati come risultato della creazione di una chiave.

## Passo 2: Ottieni le informazioni sugli eventi archiviati.
{: #tutorial2_step2}

Gli eventi {{site.data.keyword.keymanagementserviceshort}} sono disponibili nel dominio dell'account {{site.data.keyword.cloudaccesstrailshort}}.

In questa esercitazione, gli eventi {{site.data.keyword.keymanagementserviceshort}} sono disponibili nel dominio dell'account Stati Uniti Sud che si trova nella regione in cui è stato eseguito il provisioning del servizio {{site.data.keyword.keymanagementserviceshort}}. 

Immetti il seguente comando per ottenere le informazioni sugli eventi raccolti in una data specifica:

```
ibmcloud at status -s startDate -e endDate -a
```
{: codeblock}

dove 

* `-s` viene utilizzato per impostare il giorno di inizio. 
* `startDate` rappresenta la data di inizio. Il formato è *YYYY-MM-DD*.
* `-e` viene utilizzato per impostare la data di fine.
* `endDate` rappresenta la data di fine. Il formato è *YYYY-MM-DD*.
* `-a` viene utilizzato per indicare di includere gli eventi nel dominio dell'account.

Ad esempio:

```
ibmcloud at status -s 2017-07-25 -e 2017-07-25 -a
+------------+-------+-------+------------+
| Date       | Count | Size  | Searchable |
+------------+-------+-------+------------+
| 2017-07-25 | 12    | 34994 | All        |
+------------+-------+-------+------------+
```
{: screen}

Questo comando calcolerà gli eventi del 25 giugno 2017.  {{site.data.keyword.cloudaccesstrailshort}} è un servizio globale, tuttavia, i giorni sono Universal Time. Per ottenere un giorno con ora locale completo, potresti dover scaricare più giorni UTC.




## Passo 3: Specifica quali eventi scaricare
{: #tutorial2_step3}

Prima di scaricare gli eventi, crea una sessione. La sessione specifica quali eventi saranno scaricati.


Utilizza il seguente comando per creare una sessione:

```
ibmcloud at session create -s startDate -e endDate -a
```
{: codeblock}

dove 

* `-s` viene utilizzato per impostare il giorno di inizio. 
* `startDate` rappresenta la data di inizio. Il formato è *YYYY-MM-DD*.
* `-e` viene utilizzato per impostare la data di fine.
* `endDate` rappresenta la data di fine. Il formato è *YYYY-MM-DD*.
* `-a` viene utilizzato per indicare di includere gli eventi nel dominio dell'account.

Ad esempio:

```
ibmcloud at session create -s 2017-07-25 -e 2017-07-25 -a
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
{: screen}

dove 

* `-s` viene utilizzato per impostare il giorno di inizio.
* `-e` viene utilizzato per impostare la data di fine.
* `-a` viene utilizzato per indicare di includere gli eventi nel dominio dell'account.

Sono presenti una data di inizio e di fine associate a una sessione. Il comando download includerà gli eventi compresi tra queste date.

La parte importante dell'output del comando è la sessione `Id`. Vi si fa riferimento nel comando download.

Per ottenere le informazioni sulle sessioni esistenti, immetti `ibmcloud at session list`.

Per ulteriori informazioni sulle sessioni e sul comando `ibmcloud at session create`, fai riferimento a [Guida di riferimento alla CLI](/docs/services/cloud-activity-tracker/reference/at_cli_cloud.html#session_create).

Utilizza `ibmcloud at session help create` per ottenere supporto dalla riga di comando.

## Passo 4: Scarica gli eventi identificati per l'ambito definito per la sessione
{: #tutorial2_step4}

Per scaricare gli eventi specificati dai parametri della sessione, immetti il seguente comando:

```
ibmcloud at events download -o outputFile sessionID
```
{: codeblock}

* Il parametro `-o` specifica un file di output.
* `outputFile` è il nome del file locale.
* `sessionID` viene specificato per ultimo. Ottieni il valore dell'ID sessione dall'output del comando `ibmcloud at session create`.

Il formato dei dati scaricati è un JSON compresso. 

Ad esempio:

```
$ ibmcloud at events download -o events.log 21b19aeb-3d32-4c60-b912-517609c62db2
 6.70 KiB / 3.06 KiB [================================================================================================================================================================] 219.03% 8.60 MiB/s 0s
Download Successful
```
{: screen} 

L'indicatore di avanzamento si muove da 0 a 100% come vengono scaricati gli eventi.

Per ulteriori informazioni sul comando `ibmcloud at download`, fai riferimento a [Guida di riferimento alla CLI](/docs/services/cloud-activity-tracker/reference/at_cli_cloud.html#download).

Utilizza `ibmcloud at help download` per ottenere supporto dalla riga di comando.

## Passo 5: Elimina la sessione
{: #tutorial2_step5}

Al termine del download, elimina la sessione. Esegui il seguente comando:

```
ibmcloud at session delete sessionID
```
{: codeblock}

dove 

* `sessionID` è l'ID della sessione che desideri eliminare.

Il numero di sessioni è limitato. Una sessione non viene eliminata automaticamente. Devi eliminare manualmente le sessioni che non sono necessarie. 

Ad esempio: 

```
$ ibmcloud at session delete 21b19aeb-3d32-4c60-b912-517609c62db2
+---------+------------------------+
| name    | value                  |
+---------+------------------------+
| message | Delete session success |
+---------+------------------------+
```
{: screen}

Per ulteriori informazioni sul comando `ibmcloud at session delete`, fai riferimento a [Guida di riferimento alla CLI](/docs/services/cloud-activity-tracker/reference/at_cli_cloud.html#session_delete).

Utilizza `ibmcloud at session help delete` per ottenere supporto dalla riga di comando.

## Passo 6: Elimina gli eventi dal programma di traccia dell'attività automaticamente
{: #tutorial2_step6}

Hai il controllo della tua propria conservazione dell'evento in {{site.data.keyword.cloudaccesstrailshort}}. Puoi eliminare gli eventi manualmente o puoi automatizzare l'eliminazione di eventi.

Per eliminare gli eventi manualmente da uno spazio, esegui il comando `ibmcloud at delete`. Ad esempio,

```
$ ibmcloud at delete -s 2017-07-25 -e 2017-07-25
Deleted successfully
"6 logs were deleted,freeing 13737 bytes."
```
{: screen}

Per ulteriori informazioni sul comando `ibmcloud at delete`, fai riferimento a [Guida di riferimento alla CLI](/docs/services/cloud-activity-tracker/reference/at_cli_cloud.html#delete).

Utilizza `ibmcloud at help delete` per ottenere supporto dalla riga di comando.

**Nota:** per eliminare gli eventi automaticamente, puoi impostare una politica di conservazione utilizzando il comando della CLI `ibmcloud at option`. Per ulteriori informazioni, vedi [Guida di riferimento alla CLI](/docs/services/cloud-activity-tracker/reference/at_cli_cloud.html#option)


