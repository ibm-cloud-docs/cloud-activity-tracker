---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, VSI events, tutorial

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


# Monitoraggio di {{site.data.keyword.BluVirtServers_short}} e {{site.data.keyword.baremetal_short}} con {{site.data.keyword.cloudaccesstrailshort}}
{: #vsi}

Utilizza questa esercitazione per imparare a configurare gli utenti in un account {{site.data.keyword.cloud_notm}} in modo da poter monitorare gli eventi {{site.data.keyword.cloudaccesstrailshort}} generati da tali utenti quando utilizzano {{site.data.keyword.BluVirtServers_short}} e {{site.data.keyword.baremetal_short}}.
{:shortdesc}

{{site.data.keyword.BluVirtServers}} sono server virtuali scalabili che vengono acquistati con i core dedicati e le allocazioni di memoria. Sono una grande opzione se stai cercando risorse di calcolo, che possono essere aggiunte in pochi minuti, con l'accesso alle funzioni come i template dell'immagine. 
* Per ulteriori informazioni, consulta [{{site.data.keyword.BluVirtServers_short}}](/docs/vsi?topic=virtual-servers-about-virtual-servers#about-virtual-servers). 
* Per l'elenco delle azioni che generano un evento {{site.data.keyword.cloudaccesstrailshort}}, consulta [Eventi generati da {{site.data.keyword.BluVirtServers_short}}](/docs/vsi?topic=virtual-servers-at_events#at_events).

{{site.data.keyword.baremetal_short}} sono server fisici a singolo tenant che ti forniscono prestazioni e controllo con un accesso di basso livello alle risorse hardware. 
* Per ulteriori informazioni, consulta [{{site.data.keyword.baremetal_long}}](/docs/bare-metal?topic=bare-metal-about#about).
* Per l'elenco delle azioni che generano un evento {{site.data.keyword.cloudaccesstrailshort}}, consulta [Eventi generati da {{site.data.keyword.baremetal_short}}](/docs/bare-metal?topic=bare-metal-at_events#at_events).

**Perché un utente generi degli eventi {{site.data.keyword.BluVirtServers_short}} e {{site.data.keyword.baremetal_short}} {{site.data.keyword.cloudaccesstrailshort}}, deve avere accesso alle risorse dell'infrastruttura nella console IBM Cloud.**
{: tip}

## Passo 1. Collega l'account Softlayer a un account {{site.data.keyword.cloud_notm}} 
{: #vsi_step1}

** Per generare gli eventi {{site.data.keyword.cloudaccesstrailshort}}, l'account Softlayer deve essere collegato a un account {{site.data.keyword.cloud_notm}}. Per ulteriori informazioni, consulta [Passaggio all'ID IBM e collegamento degli account](/docs/account?topic=account-unifyingaccounts#link_accounts).

Prendi in considerazione le seguenti informazioni quando colleghi il tuo account Softlayer a un account {{site.data.keyword.cloud_notm}}:
* Tutti i nuovi account ricevono automaticamente un ID IBM e gli account SoftLayer esistenti, con l'eccezione degli account federati SAML, sono abilitati per passare all'autenticazione ID IBM.
* Ogni account SoftLayer che prevedi di collegare a un account {{site.data.keyword.cloud_notm}} deve appartenere a un unico ID IBM con un indirizzo e-mail univoco.
* Per passare il tuo account SoftLayer esistente a un ID IBM, crea un ID IBM e quindi utilizza il tuo codice di registrazione per confermarlo.
* Dopo aver passato un account a uno ID IBM, puoi collegare l'account SoftLayer a quello {{site.data.keyword.cloud_notm}} per utilizzare le risorse IaaS (infrastructure as a service) e PaaS (platform as a service) combinate. 

Completa la seguente procedura per collegare un account:
1. [Richiedi un ID IBM e un codice di registrazione](/docs/account?topic=account-unifyingaccounts#reqIBMidandregcode)
2. [Conferma il tuo ID IBM con il codice di registrazione](/docs/account?topic=account-unifyingaccounts#confIBMiduseregcode)
3. [Collega il tuo account ID IBM](/docs/account?topic=account-unifyingaccounts#link_user_account)


## Passo 2. Concedi agli utenti le autorizzazioni dell'infrastruttura
{: #vsi_step2}

**Nota:** se concedi le autorizzazioni dal *portale dell'infrastruttura {{site.data.keyword.cloud_notm}}*, l'utente non ha accesso dal dashboard dell'*Infrastruttura {{site.data.keyword.cloud_notm}}* per gestire i dispositivi e gli eventi {{site.data.keyword.cloudaccesstrailshort}} non vengono generati. **Devi concedere a un utente le autorizzazioni dell'infrastruttura tramite l'account {{site.data.keyword.cloud_notm}} per gestire i dispositivi. Queste azioni generano gli eventi {{site.data.keyword.cloudaccesstrailshort}}.**
{: tip}

Completa la seguente procedura per concedere a un utente le autorizzazioni dell'infrastruttura: 

1. [Accedi a {{site.data.keyword.cloud_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://cloud.ibm.com/login){:new_window}.
    
	Dopo aver eseguito l'accesso con i tuoi ID e password utente, viene aperta la IU {{site.data.keyword.cloud_notm}}.

2. Dalla barra dei menu, fai clic su **Gestisci** &gt; **Account** e seleziona **Utenti**. 

3. Scegli un utente a cui vuoi concedere le autorizzazioni per utilizzare i dispositivi.

4. Seleziona **Assegna l'accesso**.

5. Seleziona **Assegna l'accesso al tuo account SoftLayer**. Viene aperto il portale dell'infrastruttura {{site.data.keyword.cloud_notm}} all'interno del contesto di {{site.data.keyword.cloud_notm}}.

6. Configura le autorizzazioni che vuoi concedere all'utente per gestire i dispositivi. Seleziona **Autorizzazioni portale**. Successivamente, nella sezione **Dispositivi**, concedi all'utente le autorizzazioni di cui ha bisogno per gestire i dispositivi. Ad esempio, puoi modificare le autorizzazioni per le azioni `View Virtual Server Details`, `Reboot server and view IPMI system information`, `Upgrade Server` o `Issue OS Reloads and Initiate Rescue Kernel`.

7. Salva le autorizzazioni del portale. Quando selezioni **Accesso al dispositivo**, ti viene richiesto di salvare le modifiche. Fai clic su **Salva**.

8. Configura i dispositivi che l'utente può gestire. Nella sezione **Accesso al dispositivo**, seleziona i dispositivi fisici. Fai quindi clic su **Aggiorna accesso dispositivo**.






