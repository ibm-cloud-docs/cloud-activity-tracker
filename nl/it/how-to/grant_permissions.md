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


# Concessione delle autorizzazioni per visualizzare gli eventi
{: #grant_permissions}

In {{site.data.keyword.Bluemix}}, puoi assegnare i ruoli Cloud Foundry, i ruoli IAM o entrambi a un utente. Questi ruoli definiscono le attività che un utente può eseguire quando utilizza il servizio {{site.data.keyword.cloudaccesstrailshort}}.  
{:shortdesc}

## Concessione delle autorizzazioni per visualizzare gli eventi dell'account
{: #grant_acc_events}

Concedi a un utente le seguenti autorizzazioni per visualizzare gli eventi dell'account in una regione:

1. Ruolo di *Sviluppatore* in uno spazio della regione in cui è stato eseguito il provisioning di {{site.data.keyword.cloudaccesstrailshort}}. 

    Per ulteriori informazioni, vedi [Concessione di un ruolo CF](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_cf_role).

2. La politica IAM per il servizio {{site.data.keyword.loganalysisshort}} con il ruolo *visualizzatore* nella regione. 

    Il ruolo di visualizzatore è il ruolo minimo IAM richiesto. 
	
	Per ulteriori informazioni, vedi [Concessione delle autorizzazioni IAM](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_iam_policy).


## Concessione delle autorizzazioni per visualizzare gli eventi dello spazio
{: #grant_space_events}

Concedi a un utente la seguente autorizzazione per visualizzare gli eventi dello spazio in una regione:

* Ruolo di *Sviluppatore* nello spazio della regione in cui è stato eseguito il provisioning di {{site.data.keyword.cloudaccesstrailshort}}. 

    Per ulteriori informazioni, vedi [Concessione di un ruolo CF](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_cf_role).


## Concessione delle autorizzazioni IAM
{: #grant_iam_policy}

Per concedere a un utente un ruolo IAM, considera le seguenti informazioni:

* Devi disporre delle autorizzazioni per assegnare le politiche ad altri utenti nell'account, oppure devi essere il proprietario dell'account. Se non sei il proprietario dell'account, devi disporre di una politica IAM con il ruolo di **amministratore** per il servizio {{site.data.keyword.loganalysisshort}}.

* Quando definisci una politica, le regioni che specifichi definiscono quelle in cui viene concesso l'accesso all'utente per visualizzare gli eventi del dominio dell'account.

Completa la seguente procedura per concedere le autorizzazioni utente per visualizzare gli eventi da un dominio dell'account:

1. Accedi alla console {{site.data.keyword.cloud_notm}}.

    Apri un browser web e avvia il dashboard {{site.data.keyword.cloud_notm}}: [http://bluemix.net ![Icona link esterno](../../../icons/launch-glyph.svg "Icona link esterno")](http://bluemix.net){:new_window}
	
	Dopo aver eseguito l'accesso con i tuoi ID e password utente, viene aperta la IU {{site.data.keyword.cloud_notm}}.

2. Dalla barra dei menu, fai clic su **Gestisci > Account > Utenti**. 

    La finestra *Utenti* visualizza un elenco di utenti con i relativi indirizzi email per l'account selezionato al momento.
	
3. Se l'utente è un membro dell'account, seleziona il nome utente dall'elenco o fai clic su **Gestisci utente** dal menu *Azioni* .

    Se l'utente non è un membro dell'account, vedi [Invito di utenti](/docs/iam/iamuserinv.html#iamuserinv).

4. Nella sezione **Politiche di accesso**, fai clic su **Assegna accesso** e seleziona quindi **Assegna l'accesso alle risorse**. 

    Viene visualizzata la finestra *Assegna l'accesso alla risorsa all'utente**. 

5. Immetti le informazioni sulla politica. La seguente tabella elenca i campi necessari per definire una politica: 

    <table>
	  <caption>Elenco dei campi per configurare una politica IAM.</caption>
	  <tr>
	    <th>Campo</th>
		<th>Valore</th>
	  </tr>
	  <tr>
	    <td>Servizi</td>
		<td>*IBM Cloud Log Analysis*</td>
	  </tr>	  
	  <tr>
	    <td>Regioni</td>
		<td>Puoi specificare le regioni in cui sta venendo concesso l'accesso all'utente per utilizzare gli eventi. Seleziona una o più regioni singolarmente o **All current regions** per concedere l'accesso a tutte le regioni.</td>
	  </tr>
	  <tr>
	    <td>Istanza del servizio</td>
		<td>Seleziona *All service instances*.</td>
	  </tr>
	  <tr>
	    <td>Ruoli</td>
		<td>Seleziona uno o più ruoli IAM. <br>I ruoli validi sono: *amministratore*, *operatore*, *editor* e *visualizzatore*.</td>
	  </tr>
     </table>
	
6. Fai clic su **Assegna**.
	
La politica che configuri si applica alle regioni selezionate. 


## Concessione di un ruolo CF
{: #grant_cf_role}

Per concedere a un utente un ruolo CF, considera le seguenti informazioni:

* Devi disporre delle autorizzazioni nell'organizzazione e nello spazio per assegnare un ruolo Cloud Foundry a un utente. 

* Solo il ruolo di **sviluppatore** consente a un utente di visualizzare gli eventi.

Completa la seguente procedura per concedere a un utente l'accesso per visualizzare gli eventi dello spazio:

1. Accedi alla console {{site.data.keyword.cloud_notm}}.

    Apri un browser web e avvia il dashboard {{site.data.keyword.cloud_notm}}: [http://bluemix.net ![Icona link esterno](../../../icons/launch-glyph.svg "Icona link esterno")](http://bluemix.net){:new_window}
	
	Dopo aver eseguito l'accesso con i tuoi ID e password utente, viene aperta la IU {{site.data.keyword.cloud_notm}}.

2. Dalla barra dei menu, fai clic su **Gestisci > Account > Utenti**.  

    La finestra *Utenti* visualizza un elenco di utenti con i relativi indirizzi email per l'account selezionato al momento.
	
3. Se l'utente è un membro dell'account, seleziona il nome utente dall'elenco o fai clic su **Gestisci utente** dal menu *Azioni* .

    Se l'utente non è un membro dell'account, vedi [Invito di utenti](/docs/iam/iamuserinv.html#iamuserinv).

4. Seleziona **Accesso Cloud Foundry** e poi l'organizzazione.

    Viene visualizzato l'elenco degli spazi disponibili in tale organizzazione.

5. Scegli uno spazio. Quindi, dal menu delle azioni, seleziona **Modifica ruolo spazio**. 

6. Seleziona **Sviluppatore**.
	
7. Fai clic su **Salva ruolo**.




