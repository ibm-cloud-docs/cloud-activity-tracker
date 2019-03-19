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


# Eventi IAM
{: #at_events_iam}

In qualità di responsabile della sicurezza, revisore o gestore, puoi utilizzare il servizio {{site.data.keyword.cloudaccesstrailfull}} per tracciare come gli utenti e le applicazioni interagiscono con il servizio {{site.data.keyword.iamlong}} (IAM) in {{site.data.keyword.Bluemix}}. 
{:shortdesc}

Il servizio {{site.data.keyword.cloudaccesstrailshort}} registra le attività avviate dall'utente che modificano lo stato di un servizio in {{site.data.keyword.cloud_notm}}. Per ulteriori informazioni, vedi [Informazioni su {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#activity_tracker_ov ).

Per iniziare a monitorare le azioni del tuo utente, vedi [{{site.data.keyword.cloudaccesstrailfull_notm}}](/docs/services/cloud-activity-tracker/index.html#getting-started-with-cla). 

Un iniziatore può essere un utente, un servizio o un'applicazione.
{: tip}

## Gestione dei gruppi di accesso
{: #at_events_iam_access}

La seguente tabella elenca le azioni che generano un evento:

| Azione | Descrizione |
|----------|---------|
| `iam-groups.group.create`   | Un evento viene generato quando un iniziatore crea un gruppo di accesso. | 
| `iam-groups.group.read`     | Un evento viene generato quando un iniziatore ricerca le informazioni correlate ai gruppi di accesso. |
| `iam-groups.group.update`   | Un evento viene generato quando un iniziatore aggiorna un nome o una descrizione del gruppo. |
| `iam-groups.group.delete`   | Un evento viene generato quando un iniziatore elimina un gruppo di accesso. |
| `iam-groups.member.add`     | Un evento viene generato quando un iniziatore aggiunge un membro a un gruppo di accesso. |
| `iam-groups.member.delete`  | Un evento viene generato quando un iniziatore rimuove un membro da un gruppo di accesso. |
| `iam-groups.member.read`    | Un evento viene generato quando un iniziatore controlla l'appartenenza di un membro. |
| `iam-groups.rule.read`      | Un evento viene generato quando un iniziatore visualizza una regola di un gruppo di accesso. |
| `iam-groups.rule.create`    | Un evento viene generato quando un iniziatore aggiunge una regola a un gruppo di accesso. |
| `iam-groups.rule.update`    | Un evento viene generato quando un iniziatore modifica il nome della regola. |
| `iam-groups.rule.delete`    | Un evento viene generato quando un iniziatore elimina una regola da un gruppo di accesso. |
{: caption="Tabella 1. Gestisci le azioni dei gruppi di accesso" caption-side="top"} 



## Gestione degli eventi degli ID servizio
{: #at_events_iam_serviceids}

La seguente tabella elenca le azioni che generano un evento:

| Azione | Descrizione |
|----------|---------|
| `iam-identity.account-serviceid.create` | Un evento viene generato quando un iniziatore crea un ID servizio.  | 
| `iam-identity.account-serviceid.update` | Un evento viene generato quando un iniziatore ridenomina un ID servizio o ne modifica la descrizione. | 
| `iam-identity.account-serviceid.delete` | Un evento viene generato quando un iniziatore elimina un ID servizio. | 
{: caption="Tabella 2. Utilizzo delle azioni degli ID servizio" caption-side="top"} 


## Gestione degli eventi delle chiavi API
{: #at_events_iam_apikeys}

La seguente tabella elenca le azioni che generano un evento:

| Azione | Descrizione |
|----------|---------|
| `iam-identity.user-apikey.create`      | Un evento viene generato quando un iniziatore crea una chiave API. | 
| `iam-identity.user-apikey.update`      | Un evento viene generato quando un iniziatore ridenomina una chiave API o ne modifica la descrizione. |  
| `iam-identity.user-apikey.delete`      | Un evento viene generato quando un iniziatore elimina una chiave API. |  
| `iam-identity.serviceid-apikey.create` | Un evento viene generato quando un iniziatore crea una chiave API di un ID servizio. |  
| `iam-identity.serviceid-apikey.delete` | Un evento viene generato quando un iniziatore elimina una chiave API di un ID servizio. |  
{: caption="Tabella 3. Utilizzo delle azioni delle chiavi API" caption-side="top"} 


## Accesso agli eventi
{: #at_events_iam_login}

La seguente tabella elenca le azioni che generano un evento:

| Azione | Descrizione |
|----------|---------|
| `iam-identity.user-apikey.login`         | Un evento viene generato quando un utente accede a {{site.data.keyword.cloud_notm}} utilizzando una chiave API. |  
| `iam-identity.serviceid-apikey.login`    | Un evento viene generato quando un iniziatore accede a {{site.data.keyword.cloud_notm}} utilizzando una chiave API associata a un ID servizio. |  
| `iam-identity.user-identitycookie.login` | Questo è un evento generato quando un iniziatore richiede un nuovo cookie di identità per eseguire un'azione. |
| `iam-identity.user-refreshtoken.login`   | Questo è un evento generato quando l'iniziatore accede a IBM Cloud o quando un iniziatore che ha già eseguito l'accesso a IBM Cloud richiede un nuovo token di aggiornamento per eseguire un'azione. |
{: caption="Tabella 4. Azioni di accesso dell'utente" caption-side="top"} 


## Gestione degli eventi delle politiche
{: #at_events_iam_policies}

La seguente tabella elenca le azioni che generano un evento:

| Azione | Descrizione |
|----------|---------|
| `iam-am.policy.create` | Un evento viene generato quando un iniziatore aggiunge una politica a un utente o a un gruppo di accesso. |
| `iam-am.policy.delete` | Un evento viene generato quando un iniziatore modifica le autorizzazioni di una politica di un utente o di un gruppo di accesso.|
| `iam-am.policy.update` | Un evento viene generato quando un iniziatore elimina una politica assegnata a un utente o a un gruppo di accesso. |
{: caption="Tabella 5. Gestione delle azioni della politica" caption-side="top"} 


## Visualizzazione degli eventi
{: #at_events_iam_ui}

Gli eventi {{site.data.keyword.cloudaccesstrailshort}} sono disponibili nella regione **Stati Uniti Sud** del **dominio dell'account**.

Per visualizzare questi eventi, devi eseguire il provisioning di un'istanza del servizio {{site.data.keyword.cloudaccesstrailshort}} nella regione **Stati Uniti Sud**. Quindi, devi aprire l'IU {{site.data.keyword.cloudaccesstrailshort}} e passare al dominio dell'account per visualizzare gli eventi. Per ulteriori informazioni, vedi [Visualizzazione degli eventi dell'account](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/viewing_events.html#account_events).

