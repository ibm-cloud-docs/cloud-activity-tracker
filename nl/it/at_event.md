---

copyright:
  years: 2016, 2018
lastupdated: "2018-07-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}



# Campi evento del programma di traccia dell'attività
{: #at_event}

Gli eventi {{site.data.keyword.cloudaccesstrailshort}} si basano sugli standard CADF (Cloud Auditing Data Federation). 
{:shortdesc}

## Campi dell'iniziatore 
{: #initiator}

La seguente tabella elenca i campi comuni disponibili per un evento {{site.data.keyword.cloudaccesstrailshort}}:

<table>
  <caption>Campi dell'iniziatore comuni</caption>
  <tr>
    <th>Nome campo</th>
	  <th>Descrizione</th>
    <th>Valore</th>
  </tr>
  <tr>
    <td>initiator.id</td>
	  <td>ID dell'iniziatore dell'azione. </br>Esistono due tipi di iniziatori: IBMID e serviceID.</td>
    <td>Esempio di un IBMID: IBMid-000000XXX2 </br>Esempio di un ID servizio: iam-ServiceId-12345678-0165-4c89-847d-9660b1632e14</td>
  </tr>
  <tr>
    <td>initiator.name</td>
	  <td>Il nome dell'utente che ha avviato l'azione.</td>
    <td></td>
  </tr>
  <tr>
    <td>initiator.typeURI</td>
	  <td>Tipo di origine dell'evento.</td>
    <td>I valori validi sono: *service/security/account/user*, *service/security/clientid*, *service/security/account/serviceid*</td>
  </tr>
  <tr>
    <td>initiator.credential.type</td>
	  <td>Tipo di credenziali dell'ID iniziatore. </td>
    <td>I valori validi sono: *user*, *token*, *apikey*</td>
  </tr>
</table>

## Campi di destinazione
{: #target}

La seguente tabella elenca i campi di destinazione comuni disponibili per un evento {{site.data.keyword.cloudaccesstrailshort}}:

<table>
  <caption>Campi di destinazione comuni</caption>
  <tr>
    <th>Nome campo</th>
	  <th>Descrizione</th>
    <th>Valore</th>
  </tr>
  <tr>
    <td>target.id</td>
	  <td>CRN (Cloud Resource Name) della risorsa in cui viene eseguita l'azione. </br>Per ulteriori informazioni, vedi [Formato del CRN](/docs/overview/crn.html#format).</td>
    <td>Ad esempio: `crn:v1:bluemix:public:cloud-object-storage:global:a/12345678e6232019c6567c9123456789:fr56et47-befb-440a-a223c-12345678dae1:bucket:bucket1`</td>
  </tr>
  <tr>
    <td>target.name</td>
	  <td>Nome leggibile della risorsa cloud su cui viene eseguita l'azione.</td>
    <td></td>
  </tr>
  <tr>
    <td>target.typeURI</td>
    <td>Il tipo di risorsa cloud su cui viene eseguita l'azione. </br>Il formato di questo campo è **serviceName/objectType** dove servicename è il nome del servizio. </td>
	  <td>Ad esempio: `iam-am/policy` o `cloud-object-storage/bucket/acl`</td>
  </tr>
</table>
 
## Campi di azione
{: #action}

La seguente tabella elenca i campi di azione comuni disponibili per un evento {{site.data.keyword.cloudaccesstrailshort}}:

<table>
  <caption>Campi di azione comuni</caption>
  <tr>
    <th>Nome campo</th>
	  <th>Descrizione</th>
    <th>Valore</th>
  </tr>
  <tr>
    <td>azione</td>
	  <td>Azione che attiva l'evento. </br>Il formato di questo campo è **serviceName.objectType.action** dove servicename è il nome del servizio. </br>Per informazioni sugli eventi generati da un servizio, consulta <a href="/docs/services/cloud-activity-tracker/cloud_services.html#cloud_services">Servizi cloud</a></td>
    <td>Ad esempio: *iam-identity.serviceid-apikey.login*</td>
  </tr>
  <tr>
    <td>eventTime</td>
	  <td>Indica la data/ora in cui è stato creato l'evento. </br>La data è rappresentata come UTC (Universal Time Coordinated). </br>Il formato è conforme con ISO 8601.</td>
    <td>Ad esempio: 2017-10-19T19:07:50.32+0000<td>
  </tr>
</table>

## Campi del risultato
{: #outcomes}

La seguente tabella elenca i campi del risultato comuni disponibili per un evento {{site.data.keyword.cloudaccesstrailshort}}:

<table>
  <caption>Campi del risultato comuni</caption>
  <tr>
    <th>Nome campo</th>
	  <th>Descrizione</th>
    <th>Valore</th>
  </tr>
  <tr>
    <td>risultato</td>
	  <td>Risultato dell'azione. </td>
    <td>I valori validi sono: *success*, *failure*, *pending*</td>
  </tr>
  <tr>
    <td>reason.reasonCode</td>
	  <td>Campo numerico che include il codice di risposta HTTP. </td>
    <td>Ad esempio, *200* per un risultato corretto.</td>
  </tr>
  <tr>
    <td>severità</td>
	  <td>Definisce il livello di minaccia che un'azione può avere sul cloud.  </td>
    <td>I valori validi sono: *normal*, *warning* e *critical* </br></br>**Normal** è impostato per le azioni di routine nel cloud. Ad esempio: avvio di un'istanza o aggiornamento di un token. </br></br>**Warning** è impostato per le azioni in cui una risorsa cloud viene aggiornata o i relativi metadati vengono modificati. Ad esempio: l'aggiornamento della versione di un nodo di lavoro, la ridenominazione del certificato o dell'istanza del servizio. </br></br>**Critical** è impostato per le azioni che influiscono sulla sicurezza nel cloud. Ad esempio: la modifica delle credenziali di un utente, l'eliminazione dei dati, l'accesso non autorizzato all'utilizzo di una risorsa cloud. </td>
  </tr>
</table>
