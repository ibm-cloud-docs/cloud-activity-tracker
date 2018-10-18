---

copyright:
  years: 2016, 2018
lastupdated: "2018-07-09"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# CLI del programma di traccia dell'attività IBM Cloud
{: #at_cli_cloud}

Puoi utilizzare la CLI {{site.data.keyword.cloudaccesstraillong}} per gestire gli eventi {{site.data.keyword.cloudaccesstrailshort}}.
{: shortdesc}

**Prerequisiti**
* Prima di eseguire i comandi, accedi a {{site.data.keyword.Bluemix}} con il comando `ibmcloud login` per generare un token di accesso e per autenticare la tua sessione. 
* Per gestire gli eventi utilizzando la CLI, devi disporre di un piano a pagamento.

Il plugin CLI {{site.data.keyword.cloudaccesstraillong}} supporta le piattaforme Linux, Mac e Windows.

<table>
  <caption>Comandi per la gestione di {{site.data.keyword.cloudaccesstrailshort}}</caption>
  <tr>
    <th>Comando</th>
    <th>Quando utilizzarlo</th>
  </tr>
  <tr>
    <td>[ibmcloud at](#base)</td>
    <td>Utilizza questo comando per ottenere informazioni sulla CLI, come la versione o l'elenco dei comandi.</td>
  </tr>
  <tr>
    <td>[ibmcloud at delete](#delete)</td>
    <td>Utilizza questo comando per eliminare gli eventi {{site.data.keyword.cloudaccesstrailshort}}.</td>
  </tr>
  <tr>
    <td>[ibmcloud at download](#download)</td>
    <td>Utilizza questo comando per scaricare i log {{site.data.keyword.cloudaccesstrailshort}} in un file locale. </td>
  </tr>
  <tr>
    <td>[ibmcloud at help](#help)</td>
    <td>Utilizza questo comando per ottenere assistenza su come utilizzare la CLI e un elenco di tutti i comandi.</td>
  </tr>
  <tr>
    <td>[ibmcloud at option](#option)</td>
    <td>Utilizza questo comando per visualizzare o modificare le opzioni dell'evento {{site.data.keyword.cloudaccesstrailshort}}, come la conservazione, disponibili in uno spazio o un account.</td>
  </tr>
  <tr>
    <td>[ibmcloud at session create](#session_create)</td>
    <td>Utilizza questo comando per creare una nuova sessione.</td>
  </tr>
  <tr>
    <td>[ibmcloud at session delete](#session_delete)</td>
    <td>Utilizza questo comando per eliminare una sessione.</td>
  </tr>  
  <tr>
    <td>[ibmcloud at session list](#session_list)</td>
    <td>Utilizza questo comando per elencare le sessioni attive e i rispettivi ID.</td>
  </tr>  
  <tr>
    <td>[ibmcloud at session show](#session_show)</td>
    <td>Utilizza questo comando per visualizzare lo stato di una sola sessione.</td>
  </tr>   
  <tr>
    <td>[ibmcloud at status](#status)</td>
    <td>Utilizza questo comando per visualizzare le informazioni sullo stato degli eventi archiviati in {{site.data.keyword.cloudaccesstrailshort}}.</td>
  </tr>
  </table>


## ibmcloud at
{: #base}

Fornisce informazioni sulla versione della CLI e su come utilizzarla.

```
ibmcloud at [parameters]
```
{: codeblock}

**Parametri**

<dl>
<dt>--help, -h</dt>
<dd>Imposta questo parametro per visualizzare l'elenco dei comandi o per ottenere assistenza su un comando.
</dd>

<dt>--version, -v</dt>
<dd>Imposta questo parametro per stampare la versione della CLI.</dd>
</dl>

**Esempi**

Per ottenere l'elenco di comandi, immetti il seguente
comando:

```
ibmcloud at --help
```
{: codeblock}

Per ottenere la versione della CLI, immetti il seguente comando:

```
ibmcloud at --version
```
{: codeblock}


## ibmcloud at delete
{: #delete}

Elimina gli eventi {{site.data.keyword.cloudaccesstrailshort}}.

```
ibmcloud at delete [parameters] [arguments..]
```
{: codeblock}

**Parametri**

<dl>
  <dt>--start value, -s value</dt>
  <dd>(Facoltativo) Imposta la data di inizio in UTC (Universal Coordinated Time): *YYYY-MM-DD*, ad esempio, `2017-01-02`. <br>Il valore predefinito è impostato su 2 settimane fa. 
  </dd>
  
  <dt>--end value, -e value</dt>
  <dd>(Facoltativo) Imposta la data di fine in UTC (Universal Coordinated Time): *YYYY-MM-DD* <br>Il formato UTC della data è **YYYY-MM-DD**, ad esempio, `2017-01-02`. <br>Il valore predefinito è impostato sulla data corrente.
  </dd>
  
  <dt>--search-time value, -T value</dt>
  <dd>(Facoltativo) Puoi impostare questo parametro per eliminare gli eventi archiviati per un numero di ore in un giorno specifico. Il formato del campo è: 0-23
  </dd>

</dl>


**Esempio**

Per eliminare gli eventi del 22 giugno 2017, esegui il seguente comando:
```
ibmcloud at delete -s 2017-06-22 -e 2017-06-22
```
{: codeblock}

Riceverai delle informazioni simili alle seguenti:

`Deleted successfully`
`"6 logs were deleted, freeing 13737 bytes."`


## ibmcloud at download
{: #download}

Scarica gli eventi {{site.data.keyword.cloudaccesstrailshort}} in un file locale o li trasmette alla finestra del terminale in Windows e Mac OS X o in stdout in un terminale Linux. 

**Nota:** per scaricare i file è prima necessario creare una sessione. Una sessione definisce quali eventi scaricare in base all'intervallo di date. Scarichi gli eventi nel contesto di una sessione. 

```
ibmcloud at download [parameters] [arguments...]
```
{: codeblock}

**Parametri**

<dl>
<dt>--output value, -o value</dt>
<dd>(Facoltativo) Imposta il percorso e il nome file del file di output locale in cui gli eventi sono stati scaricati. <br>Il valore predefinito è un trattino (-). <br>Imposta questo parametro sul valore predefinito per i log di output e l'output standard.</dd>
</dl>

**Argomenti**

<dl>
<dt>ID sessione</dt>
<dd>Imposta il valore ID sessione che ottieni quando esegui il comando `ibmcloud at session create`. Questo valore indica quale sessione utilizzare quando scarichi gli eventi. <br>**Nota:** il comando `ibmcloud at session create` fornisce i parametri che controllano quali eventi vengono scaricati. </dd>
</dl>

**Nota:** dopo il termine del download, per riscaricare nuovamente gli stessi dati, devi utilizzare un file o una sessione differenti.

**Esempio**

Per scaricare gli eventi in un file denominato `events.log`, esegui il seguente comando:

```
ibmcloud at download -o events.log 1db6ce16-824d-4d50-bd40-37f1d8fea9b7
```
{: screen}

Riceverai delle informazioni simili alle seguenti: 

```
6.70 KiB / 3.06 KiB [========] 219.03% 8.60 MiB/s 0s
Download completed successfully
```
{: screen}


## ibmcloud at help
{: #help}

Fornisce le informazioni su come utilizzare un comando.

```
ibmcloud at help [parameters]
```
{: codeblock}

**Parametri**

<dl>
<dt>Comando</dt>
<dd>Imposta il nome del comando per cui desideri ottenere assistenza.
</dd>
</dl>


**Esempio**

Per ottenere assistenza su come eseguire il comando per visualizzare lo stato di {{site.data.keyword.cloudaccesstrailshort}}, esegui il seguente comando:

```
ibmcloud at help status
```
{: codeblock}


## ibmcloud at option
{: #option}

Visualizza o modifica il periodo di conservazione degli eventi disponibili in uno spazio. Quando imposti una politica di conservazione, gli eventi vengono eliminati automaticamente quando viene raggiunto il numero di giorni di conservazione.

* Il periodo viene impostato nel numero di giorni.
* Il valore predefinito è **-1**, ossia, gli eventi vengono archiviati e non eliminati.

**Nota:** per impostazione predefinita, tutti gli eventi vengono archiviati. Se non si imposta un periodo di conservazione, è necessario eliminarli manualmente utilizzando il comando `ibmcloud at delete`. 

```
ibmcloud at option [parameters] [arguments...]
```
{: codeblock}

**Parametri**

<dl>
<dt>--retention value, -r value</dt>
<dd>(Facoltativo) Imposta il numero di giorni di conservazione. <br> Il valore predefinito è *-1* giorni.</dd>

<dt>--at-account-level, -a</dt>
<dd>(Facoltativo) Imposta questo parametro per elencare le informazioni relative al periodo di conservazione per gli eventi archiviati in ogni dominio dello spazio e dell'account.

</dl>

**Esempio**

Per visualizzare il periodo di conservazione corrente per lo spazio in cui hai eseguito l'accesso, esegui il seguente comando:

```
ibmcloud at option
```
{: codeblock}

L'output è simile al seguente:

```
+--------------------------------------+-----------+
|               SPACEID                | RETENTION |
+--------------------------------------+-----------+
| 2af890ce-fb4f-4e41-a975-901a56ed1f11 |        30 |
+--------------------------------------+-----------+
```
{: screen}


Per modificare il periodo di conservazione in 25 giorni per lo spazio in cui hai eseguito l'accesso, esegui il seguente comando:

```
ibmcloud at option -r 25
```
{: codeblock}

L'output è simile al seguente:

```
+--------------------------------------+-----------+
|               SPACEID                | RETENTION |
+--------------------------------------+-----------+
| 2af890ce-fb4f-4e41-a975-901a56ed1f11 |        25 |
+--------------------------------------+-----------+
```
{: screen}



## ibmcloud at session create
{: #session_create}

Crea una nuova sessione.

**Nota:** puoi avere fino a 30 sessioni simultanee in uno spazio. La sessione viene creata per un utente. Le sessioni non possono essere condivise tra gli utenti in uno spazio.

```
ibmcloud at session create [parameters] [arguments...]
```
{: codeblock}

**Parametri**

<dl>
  <dt>--at-account-level, -a </dt>
  <dd>(Facoltativo) imposta l'ambito al livello dell'account. </br>Imposta questo valore per ottenere le informazioni sull'account. <br>Se questo parametro non viene specificato, viene impostato il valore solo per lo spazio corrente, che è lo spazio in cui hai eseguito l'accesso utilizzato il comando `ibmcloud cf login`.
  </dd>

  <dt>--start value, -s value</dt>
  <dd>(Facoltativo) Imposta la data di inizio in UTC (Universal Coordinated Time): *YYYY-MM-DD*, ad esempio, `2017-01-02`. <br>Il valore predefinito è impostato su 2 settimane fa. 
  </dd>
  
  <dt>--end value, -e value</dt>
  <dd>(Facoltativo) Imposta la data di fine in UTC (Universal Coordinated Time): *YYYY-MM-DD*, ad esempio, `2017-01-02`. <br>Il valore predefinito è impostato sulla data corrente. 
  </dd>

  <dt>--search-time value, -T value</dt>
  <dd>(Facoltativo) Puoi impostare questo parametro per eliminare gli eventi archiviati per un numero di ore in un giorno specifico. Il formato del campo è: 0-23
  </dd>


 </dl>

**Valori restituiti**

<dl>
<dt>Ora-Accesso</dt>
<dd>La data/ora che indica quando la sessione è stata utilizzata l'ultima volta.</dd>

<dt>Ora-Creazione</dt>
<dd>La data/ora che corrisponde alla data e all'ora in cui è stata creata la sessione.</dd>

<dt>Intervallo-Date</dt>
<dd>Indica i giorni utilizzati per filtrare gli eventi. Gli eventi identificati in questo intervallo di date sono disponibili per la gestione attraverso la sessione.</dd>

<dt>ID</dt>
<dd>ID sessione.</dd>

<dt>Spazio</dt>
<dd>L'ID spazio in cui la sessione è attiva.</dd>

<dt>Account-Tipo</dt>
<dd>Questo valore è impostato su **ActivityTracker**.</dd>

<dt>Nome utente</dt>
<dd>{{site.data.keyword.IBM_notm}}L'ID dell'utente che ha creato la sessione.</dd>
</dl>


**Esempio**

Per creare una sessione per il 10 luglio 2017, esegui il seguente comando:

```
ibmcloud at session create -s 2017-07-10 -e 2017-07-10
```
{: screen}

L'output è simile al seguente:

```
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| id           | 9b8c4db8-5841-4993-a449-305815a53a8e      |
| space        | xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx      |
| username     | xxx@yyy.com                               |
| create-time  | 2017-07-25T11:54:00.20042645Z             |
| access-time  | 2017-07-25T11:54:00.20042645Z             |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
+--------------+-------------------------------------------+
```
{: screen}



## ibmcloud at session delete
{: #session_delete}

Elimina una sessione specificata dall'ID sessione.

```
ibmcloud at session delete [arguments...]
```
{: codeblock}


**Argomenti**

<dl>
<dt>ID sessione</dt>
<dd>L'ID della sessione che desideri eliminare. <br>Puoi utilizzare il comando `ibmcloud at session list` per ottenere tutti gli ID sessione attivi.</dd>
</dl>

**Esempio**

Per eliminare una sessione con ID sessione *9b8c4db8-5841-4993-a449-305815a53a8e*, esegui il seguente comando:

```
ibmcloud at session delete 9b8c4db8-5841-4993-a449-305815a53a8e
```
{: screen}

L'output è simile al seguente:

```
+---------------+--------------------------+
|    NAME       |     VALUE                |
+---------------+--------------------------+
|  message      | Delete session success   |
+---------------+--------------------------+
```
{: screen}


## ibmcloud at session list
{: #session_list}

Elenca le sessioni attive e i rispettivi ID.

```
ibmcloud at session list 
```
{: codeblock}

**Valori restituiti**

<dl>
<dt>ID</dt>
<dd>ID sessione.</dd>

<dt>SPAZIO</dt>
<dd>L'ID spazio in cui la sessione è attiva.</dd>

<dt>NOME UTENTE</dt>
<dd>{{site.data.keyword.IBM_notm}}L'ID dell'utente che ha creato la sessione.</dd>

<dt>ORA-CREAZIONE</dt>
<dd>La data/ora che corrisponde alla data e all'ora in cui è stata creata la sessione.</dd>

<dt>ORA-ACCESSO</dt>
<dd>La data/ora che indica quando la sessione è stata utilizzata l'ultima volta.</dd>
</dl>
 
**Esempio**

Per elencare le sessioni, esegui questo comando:

```
ibmcloud at session list
```
{: screen}

L'output è simile al seguente:

```
+--------------------------------------+--------------------------------------+-----------------------------------+--------------------------------+--------------------------------+
| ID                                   | SPACE                                | USERNAME                          | CREATE-TIME                    | ACCESS-TIME                    |
+--------------------------------------+--------------------------------------+-----------------------------------+--------------------------------+--------------------------------+
| fa3f1970-21f3-4e32-b480-1ffb41badc16 | 12345678-fb4f-acdf-a975-11335678r3fg | xxx@yyy.com                       | 2017-07-10T09:04:07.916788069Z | 2017-07-10T09:04:07.916788069Z |
| 9b8c4db8-5841-4993-a449-305815a53a8e | 12345678-fb4f-acdf-a975-11335678r3fg | xxx@yyy.com                       | 2017-07-11T09:19:14.666532796Z | 2017-07-12T09:19:14.666532796Z |
+--------------------------------------+--------------------------------------+-----------------------------------+--------------------------------+--------------------------------+
```
{: screen}


## ibmcloud at session show
{: #session_show}

Mostra lo stato di una singola sessione.

```
ibmcloud at session show [arguments...]
```
{: codeblock}

**Argomenti**

<dl>
<dt>ID sessione</dt>
<dd>L'ID della sessione attiva per cui desideri ottenere le informazioni.</dd>
</dl>

**Valori restituiti**

<dl>
<dt>Ora-Accesso</dt>
<dd>La data/ora che indica quando la sessione è stata utilizzata l'ultima volta.</dd>

<dt>Ora-Creazione</dt>
<dd>La data/ora che corrisponde alla data e all'ora in cui è stata creata la sessione.</dd>

<dt>Intervallo-Date</dt>
<dd>Indica i giorni utilizzati per filtrare gli eventi. Gli eventi identificati in questo intervallo di date sono disponibili per la gestione attraverso la sessione.</dd>

<dt>id</dt>
<dd>ID sessione.</dd>

<dt>Spazio</dt>
<dd>L'ID spazio in cui la sessione è attiva.</dd>

<dt>Account-Tipo</dt>
<dd>Questo valore è impostato su **ActivityTracker**.</dd>

<dt>Nome utente</dt>
<dd>{{site.data.keyword.IBM_notm}}L'ID dell'utente che ha creato la sessione.</dd>
</dl>

**Esempio**

Per visualizzare i dettagli di una sessione con ID sessione *9b8c4db8-5841-4993-a449-305815a53a8e*, esegui il seguente comando:

```
ibmcloud at session show 9b8c4db8-5841-4993-a449-305815a53a8e
```
{: screen}

L'output è simile al seguente:

```
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| create-time  | 2017-07-25T11:54:00.20042645Z             |
| access-time  | 2017-07-25T11:54:00.20042645Z             |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
| id           | 9b8c4db8-5841-4993-a449-305815a53a8e      |
| space        | xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx      |
| username     | xxx@yyy.com                               |
+--------------+-------------------------------------------+
```
{: screen}


## ibmcloud at status
{: #status}

Restituisce le informazioni sullo stato degli eventi {{site.data.keyword.cloudaccesstrailshort}}.

```
ibmcloud at status [parameters] [arguments...]
```
{: codeblock}

**Parametri**

<dl>
  <dt>--start value, -s value</dt>
  <dd>(Facoltativo) Imposta la data di inizio in UTC (Universal Coordinated Time): *YYYY-MM-DD*, ad esempio, `2017-01-02`. <br>Il valore predefinito è impostato su 2 settimane fa.
  </dd>
  
  <dt>--end value, -e value</dt>
  <dd>(Facoltativo) Imposta la data di fine in UTC (Universal Coordinated Time): *YYYY-MM-DD*, ad esempio, `2017-01-02`. <br>Il valore predefinito è impostato sulla data corrente.
  </dd>
  
  <dt>--at-account-level, -a </dt>
  <dd>(Facoltativo) imposta l'ambito al livello dell'account. <br> **Nota:** imposta questo valore per ottenere le informazioni sull'account. <br>Se questo parametro non viene specificato, viene impostato il valore solo per lo spazio corrente, che è lo spazio in cui hai eseguito l'accesso utilizzato il comando `ibmcloud cf login`.
  </dd>
  
</dl>


**Nota:** il comando `ibmcloud at status` restituisce solo le ultime due settimane di eventi archiviati in {{site.data.keyword.cloudaccesstrailshort}} quando non vengono specificate date di inizio e di fine. 

**Valori restituiti**   

<dl>
  <dt>DATA</dt>
  <dd>La data in UTC (Universal Coordinated Time): *YYYY-MM-DD*, ad esempio, `2017-01-02`. 
  </dd>
  
  <dt>CONTEGGIO</dt>
  <dd>Numero totale di eventi.
  </dd>
  
  <dt>DIMENSIONE</dt>
  <dd>La dimensione totale degli eventi in megabyte.
  </dd>

  <dt>TIPI</dt>
  <dd>Questo valore è impostato su **ActivityTracker**.
  </dd>
  
  <dt>RICERCABILE</dt>
  <dd>Questo campo indica se gli eventi sono disponibili per la ricerca in Kibana. <br>Quando il valore del campo **RICERCABILE** è impostato su *Nessuno*, gli eventi sono disponibili per il download ma non puoi analizzarli in Kibana.
  </dd>
  
</dl>

**Esempio**

Per visualizzare i dettagli degli eventi del 20 luglio 2017, esegui il seguente comando:

```
ibmcloud at status -s 2017-07-20 -e 2017-07-20
```
{: codeblock}


Riceverai delle informazioni simili alle seguenti:

```
+------------+-----------+-------+------------------+--------------+
|   Date     |  Count    | Size  | Types            |  Searchable  | 
+------------+-----------+-------+------------------+--------------+
| 2017-07-20 |    1      | 2531  | ActivityTracker  | All          | 
+------------+-----------+-------+------------------+--------------+
```
{: screen}


