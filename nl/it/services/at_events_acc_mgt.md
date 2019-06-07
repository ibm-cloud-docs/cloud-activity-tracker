---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, account events

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
{:deprecated: .deprecated}

# Eventi di gestione dell'account  
{: #at_events_acc_mgt}

In qualità di responsabile della sicurezza, revisore o gestore, puoi utilizzare il servizio {{site.data.keyword.cloudaccesstrailfull}} per tracciare come gli utenti e le applicazioni interagiscono con l'account {{site.data.keyword.Bluemix}}. 
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} è obsoleto. A partire dal 9 maggio 2019, non puoi eseguire il provisioning delle nuove istanze di {{site.data.keyword.cloudaccesstrailshort}}. Le istanze del piano Premium esistenti sono supportate fino al 30 settembre 2019. Per continuare a monitorare l'attività del tuo account {{site.data.keyword.cloud_notm}}, esegui il provisioning di un'istanza di [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}

Il servizio {{site.data.keyword.cloudaccesstrailfull_notm}} registra le attività avviate dall'utente che modificano lo stato di un servizio in {{site.data.keyword.cloud_notm}}. Per ulteriori informazioni, vedi [Informazioni su {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov).

Per iniziare a monitorare le azioni del tuo utente, vedi [{{site.data.keyword.cloudaccesstrailfull_notm}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started). 



## Eventi per la gestione degli account
{: #at_events_acc_mgt_account}

La seguente tabella elenca i metodi API che generano un evento quando vengono richiamati:

<table>
  <caption>Azioni che generano gli eventi</caption>
  <tr>
    <th>Azione</th>
	  <th>Descrizione</th>
  </tr>
  <tr>
    <td>billing.account.create</td>
	  <td>Un evento viene generato quando esegui il provisioning di un account, dopo che l'ID account viene assegnato all'account.</td>
  </tr>
  <tr>
    <td>billing.account.update</td>
	  <td>Un evento viene generato quando aggiorni le informazioni sull'account.</td>
  </tr>
  <tr>
    <td>billing.account.active</td>
	  <td>Un evento viene generato quando verifichi l'account, cioè, un evento viene generato quando l'account diventa attivo.</td>
  </tr>
  <tr>
    <td>billing.account.subscription.create</td>
	  <td>Un evento viene generato quando crei un <a href="/docs/account?topic=account-accounts#subscription-account">Account di sottoscrizione </a>.</td>
  </tr>
</table>



## Eventi per la gestione degli utenti
{: #at_events_acc_mgt_users}

La seguente tabella elenca i metodi API che generano un evento quando vengono richiamati:

<table>
  <caption>Azioni che generano gli eventi</caption>
  <tr>
    <th>Azione</th>
	  <th>Descrizione</th>
  </tr>
  <tr>
    <td>user-management.user.create</td>
	  <td>Un evento viene generato quando invii un invito a un utente per unirsi a un account. </br>Il proprietario dell'account è l'unico utente nell'account che può eseguire questa azione.</td>
  </tr>
  <tr>
    <td>user-management.user.active</td>
	  <td>Un evento viene generato quando attivi l'utente nell'account. </br>Quando l'utente verifica il suo indirizzo email, l'evento viene generato.</td>
  </tr>
  <tr>
    <td>user-management.user.delete</td>
	  <td>Un evento viene generato quando rimuovi un utente dall'account. </br>Il proprietario dell'account è l'unico utente nell'account che può eseguire questa azione.</td>
  </tr>
</table>

## Eventi per la gestione delle organizzazioni
{: #at_events_acc_mgt_org}

La seguente tabella elenca i metodi API che generano un evento quando vengono richiamati:

<table>
  <caption>Azione che genera gli eventi</caption>
  <tr>
    <th>Azione</th>
	  <th>Descrizione</th>
  </tr>
  <tr>
    <td>billing.account.org.create</td>
	  <td>Un evento viene generato quando aggiungi un'organizzazione all'account.</td>
  </tr>
</table>

## Dove cercare gli eventi
{: #at_events_acc_mgt_ui}

Gli eventi {{site.data.keyword.cloudaccesstrailshort}} sono disponibili nella regione **Stati Uniti Sud** del **dominio dell'account**. 

Per visualizzare questi eventi, devi eseguire il provisioning di un'istanza del servizio {{site.data.keyword.cloudaccesstrailshort}} nella regione **Stati Uniti Sud**. Quindi, devi aprire l'IU {{site.data.keyword.cloudaccesstrailshort}} e passare al dominio dell'account per visualizzare gli eventi. 

Per ulteriori informazioni, vedi [Visualizzazione degli eventi dell'account](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-view_acc_events#view_acc_events_account_events).








