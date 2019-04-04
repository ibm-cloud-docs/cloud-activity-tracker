---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, Cloud Foundry events, CF

subcollection: cloud-activity-tracker

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}
{:important: .important}
{:note: .note}


# Eventi Cloud Foundry
{: #cf}

Utilizza il servizio {{site.data.keyword.cloudaccesstrailfull}} per tenere traccia dell'interazione con i servizi della piattaforma principali in {{site.data.keyword.Bluemix}}. 
{:shortdesc}


Il seguente elenco illustra le diverse attività della piattaforma principale che inviano gli eventi al servizio {{site.data.keyword.cloudaccesstrailshort}}: 

* Provisioning di un servizio, rimozione di un servizio e modifica del nome di un servizio.
* Concessione, aggiornamento e revoca dei ruoli dello spazio Cloud Foundry agli utenti nell'account.
* Creazione di una chiave API della piattaforma, ridenominazione ed eliminazione di una chiave della piattaforma.


## Eventi generati quando interagiscono con i servizi del catalogo
{: #cf_catalog}

Quando esegui il provisioning di un servizio, lo rimuovi e ne modifichi il nome, un evento viene generato e inviato al dominio dello spazio in {{site.data.keyword.cloudaccesstrailshort}} associato allo spazio Cloud Foundry in cui il servizio è disponibile nell'account. 

Ad esempio, esegui il provisioning del servizio A nello spazio B nella regione Stai Uniti Sud. Viene generato un evento. Per visualizzare l'evento, devi eseguire il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}} in Stati Uniti Sud, nello stesso spazio in cui è stato eseguito il provisioning del servizio. Quindi, puoi visualizzare l'evento tramite l'IU del servizio {{site.data.keyword.cloudaccesstrailshort}}.

La seguente tabella elenca le azioni del catalogo che generano gli eventi:

<table>
  <caption>Azioni del catalogo</caption>
  <tr>
    <th>Azione</th>
	  <th>Descrizione</th>
  <tr>
  <tr>
    <td>`audit.service_instance.create`</td>
	<td>Un evento viene creato quando esegui il provisioning di un servizio in uno spazio Cloud Foundry.</td>
  </tr>
  <tr>
    <td>`audit.service_instance.update`</td>
	<td>Un evento viene creato quando modifichi il nome di un servizio che è disponibile in uno spazio Cloud Foundry.</td>
  </tr>
  <tr>
    <td>`audit.service_instance.delete`</td>
	<td>Un evento viene creato quando rimuovi un servizio da uno spazio Cloud Foundry nell'account.</td>
  </tr>
</table>


 	

## Eventi generati durante la gestione dei ruoli Cloud Foundry nell'account
{: #cf_cfroles} 

Quando concedi o revochi (elimini) un ruolo Cloud Foundry a un utente nell'account, un evento viene generato e inviato al dominio dello spazio in {{site.data.keyword.cloudaccesstrailshort}} associato allo spazio Cloud Foundry in cui il ruolo viene concesso o revocato. 

Ad esempio, concedi all'utente A nello spazio B nella regione Stati Uniti Sud un ruolo di *gestore dello spazio*. Viene generato un evento. Per visualizzare l'evento, devi eseguire il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}} in Stati Uniti Sud, nello stesso spazio in cui stai gestendo le autorizzazioni CF dell'utente. Quindi, puoi visualizzare l'evento tramite l'IU del servizio {{site.data.keyword.cloudaccesstrailshort}}.


La seguente tabella elenca le azioni che generano gli eventi {{site.data.keyword.cloudaccesstrailshort}} quando gestisci i ruoli Cloud Foundry di un utente:

<table>
  <caption>Gestione delle azioni dei ruoli Cloud Foundry</caption>
  <tr>
    <th>Azione</th>
	<th>Descrizione</th>
  <tr>
  <tr>
    <td>`audit.user.space_manager_add`</td>
	<td>Concedi a un utente il ruolo di *gestore* in uno spazio Cloud Foundry.</td>
  </tr>
  <tr>
    <td>`audit.user.space_developer_add`</td>
	<td>Concedi a un utente il ruolo di *sviluppatore* in uno spazio Cloud Foundry.</td>
  </tr>
  <tr>
    <td>`audit.user.space_auditor_add`</td>
	<td>Concedi a un utente il ruolo di *revisore* in uno spazio Cloud Foundry.</td>
  </tr>
  <tr>
    <td>`audit.user.space_manager_remove`</td>
	<td>Elimina il ruolo di *gestore* di un utente in uno spazio Cloud Foundry.</td>
  </tr>
  <tr>
    <td>`audit.user.space_developer_remove`</td>
	<td>Elimina il ruolo di *sviluppatore* di un utente in uno spazio Cloud Foundry.</td>
  </tr>
  <tr>
    <td>`audit.user.space_auditor_remove`</td>
	<td>Elimina il ruolo di *revisore* di un utente in uno spazio Cloud Foundry.</td>
  </tr>
</table>






	
 	
 	
