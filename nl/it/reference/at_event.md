---

copyright:
  years: 2016, 2017

lastupdated: "2017-09-18"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# Campi evento del programma di traccia dell'attività
{: #at_event}

Gli eventi {{site.data.keyword.cloudaccesstrailshort}} si basano sugli standard CADF (Cloud Auditing Data Federation). 
{:shortdesc}

## Campi evento
{: #fields}

La seguente tabella elenca i campi disponibili per l'analisi di un evento {{site.data.keyword.cloudaccesstrailshort}}:

<table>
  <caption>Tabella 1. Campi disponibili per il monitoraggio per evento.</caption>
  <tr>
    <th>Nome campo</th>
	<th>Stato</th>
	<th>Descrizione</th>
  </tr>
  <tr>
    <td>risultato</td>
	<td>Obbligatorio</td>
	<td>I valori validi sono: *success*, *failure*</td>
  </tr>
  <tr>
    <td>typeURI</td>
	<td>Obbligatorio</td>
	<td>Questo campo è impostato su: *http://schemas.dmtf.org/cloud/audit/1.0/event*</td>
  </tr>
  <tr>
    <td>eventType</td>
	<td>Obbligatorio</td>
	<td>Questo campo è impostato su *activity*.</td>
  </tr>
  <tr>
    <td>eventTime</td>
	<td>Obbligatorio</td>
	<td>(La data viene rappresentata come una stringa ISO, ad esempio: *2017-09-17 15:15:32.396 +0000 UTC*.</td>
  </tr>
  <tr>
    <td>azione</td>
	<td>Obbligatorio</td>
	<td>Questo campo indica l'azione che ha attivato l'evento, ad esempio, *read.ibm-key-protect.secrets*.</td>
  </tr>
  <tr>
    <td>id</td>
	<td>Facoltativo</td>
	<td>Questo campo contiene l'UUID dell'evento.</td>
  </tr>
  <tr>
    <td>initiator.id</td>
	<td>Obbligatorio</td>
	<td>Questo campo contiene l'ID per l'origine dell'evento, ad esempio un ID istanza.</td>
  </tr>
  <tr>
    <td>initiator.name</td>
	<td>Facoltativo</td>
	<td>Questo campo fornisce un nome leggibile dall'utente per l'origine dell'evento, ad esempio un ID utente. </td>
  </tr>
  <tr>
    <td>initiator.typeURI</td>
	<td>Obbligatorio</td>
	<td>Questo campo fornisce informazioni sul tipo di origine dell'evento, ad esempio, *service/security/account/user*</td>
  </tr>
  <tr>
    <td>initiator.host.agent</td>
	<td>Facoltativo</td>
	<td>Questo campo indica il client che è stato utilizzato per inviare la richiesta, ad esempio, *python-neutronclient* o le informazioni sul browser.</td>
  </tr>
  <tr>
    <td>initiator.host.address</td>
	<td>Facoltativo</td>
	<td>Questo campo include l'indirizzo IP dell'iniziatore. </td>
  </tr>
  <tr>
    <td>target.id</td>
	<td>Obbligatorio</td>
	<td>Questo campo include l'ID del servizio di destinazione. </td>
  </tr>
  <tr>
    <td>target.name</td>
	<td>Obbligatorio</td>
	<td>Questo campo include il nome leggibile dall'utente del servizio di destinazione, ad esempio, *ibm-key-protect*.</td>
  </tr>
  <tr>
    <td>target.typeURI</td>
	<td>Obbligatorio</td>
	<td>Questo campo include il tipo di destinazione dell'evento, ad esempio, *service/ibm-key-protect/secrets*.</td>
  </tr>
  <tr>
    <td>target.host.address</td>
	<td>Facoltativo</td>
	<td>Questo campo include l'indirizzo IP o l'URL del servizio di destinazione, ad esempio, *xxx.bluemix.net*.</td>
  </tr>
  <tr>
    <td>observer.name</td>
	<td>Obbligatorio</td>
	<td>Questo campo è impostato sul seguente valore: *ActivityTracker*</td>
  </tr>
  <tr>
    <td>observer.id</td>
	<td>Obbligatorio</td>
	<td>Questo campo include le informazioni sulla risorsa che crea e archivia l'evento CADF, ad esempio, *activitytracker.ng.bluemix.net*.</td>
  </tr>
  <tr>
    <td>observer.typeURI</td>
	<td>Obbligatorio</td>
	<td>Questo campo è impostato sul seguente valore: *service/security/edge/activity-tracker*</td>
  </tr>
  <tr>
    <td>reason.reasonCode</td>
	<td>Facoltativo</td>
	<td>Questo campo include il codice di risposta HTTP, ad esempio, *200* per l'esito positivo.</td>
  </tr>
  <tr>
    <td>reason.reasonType</td>
	<td>Obbligatorio</td>
	<td>Questo campo include le informazioni sul reasonCode quando ne viene eseguito il provisioning tramite il campo *reason.reasonCode*.</td>
  </tr>
</table>

 

