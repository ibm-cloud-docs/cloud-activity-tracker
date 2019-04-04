---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, resource controller events

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

# Eventi dell'istanza del servizio  
{: #at_events_rc}

In qualità di responsabile della sicurezza, revisore o gestore, puoi utilizzare il servizio {{site.data.keyword.cloudaccesstrailfull}} per tracciare come gli utenti e le applicazioni interagiscono con i servizi {{site.data.keyword.Bluemix}}. 
{:shortdesc}

Il servizio {{site.data.keyword.cloudaccesstrailfull_notm}} registra le attività avviate dall'utente che modificano lo stato di un servizio in {{site.data.keyword.cloud_notm}}. Per ulteriori informazioni, vedi [Informazioni su {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov).

Per iniziare a monitorare le azioni del tuo utente, vedi [{{site.data.keyword.cloudaccesstrailfull_notm}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started-with-cla#getting-started-with-cla). 


## Eventi per il provisioning e la gestione delle istanze del servizio
{: #at_events_rc_provision}

La seguente tabella elenca i metodi API che generano un evento quando vengono richiamati:

<table>
  <caption>Azioni che generano gli eventi</caption>
  <tr>
    <th>Azione</th>
	  <th>Descrizione</th>
  </tr>
  <tr>
    <td><i>service_name</i>.instance.create</td>
	  <td>Un evento viene generato quando esegui il provisioning di un'istanza del servizio.</td>
  </tr>
  <tr>
    <td><i>service_name</i>.instance.update</td>
	  <td>Un evento viene generato quando ridenomini un'istanza del servizio o modifichi il piano di servizio.</td>
  </tr>
  <tr>
    <td><i>service_name</i>.instance.delete</td>
	  <td>Un evento viene generato quando un'istanza del servizio viene eliminata.</td>
  </tr>
</table>


##  Eventi per la gestione delle chiavi API associate a un'istanza del servizio
{: #at_events_rc_keys}

La seguente tabella elenca i metodi API che generano un evento quando vengono richiamati:

<table>
  <caption>Azioni che generano gli eventi</caption>
  <tr>
    <th>Azione</th>
	  <th>Descrizione</th>
  </tr>
  <tr>
    <td><i>service_name</i>.key.create</td>
	  <td>Un evento viene generato quando crei una chiave API per un'istanza del servizio tramite la sezione *Service credentials* dell'IU dell'istanza del servizio.</td>
  </tr>
  <tr>
    <td><i>service_name</i>.key.delete</td>
	  <td>Un evento viene generato quando una chiave API associata a un'istanza del servizio viene eliminata dalla sezione *Service credentials* dell'IU dell'istanza del servizio.</td>
  </tr>
</table>

##  Eventi per l'associazione di un'istanza del servizio a un'applicazione
{: #at_events_rc_bind}

La seguente tabella elenca i metodi API che generano un evento quando vengono richiamati:

<table>
  <caption>Azioni che generano gli eventi</caption>
  <tr>
    <th>Azione</th>
	  <th>Descrizione</th>
  </tr>
  <tr>
    <td><i>service_name</i>.binding.create</td>
	  <td>Un evento viene generato quando associ un'istanza del servizio a un'applicazione.</td>
  </tr>
  <tr>
    <td><i>service_name</i>.binding.delete</td>
	  <td>Un evento viene generato quando annulli l'associazione a un'istanza del servizio da un'applicazione.</td>
  </tr>
</table>




## Dove cercare gli eventi
{: #at_events_rc_ui}

Gli eventi {{site.data.keyword.cloudaccesstrailshort}} sono disponibili nella regione **Stati Uniti Sud** del **dominio dell'account**.

Per visualizzare questi eventi, devi eseguire il provisioning di un'istanza del servizio {{site.data.keyword.cloudaccesstrailshort}} nella regione **Stati Uniti Sud**. Quindi, devi aprire l'IU {{site.data.keyword.cloudaccesstrailshort}} e passare al dominio dell'account per visualizzare gli eventi. 

Per ulteriori informazioni, vedi [Visualizzazione degli eventi dell'account](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-view_acc_events#view_acc_events_account_events).



