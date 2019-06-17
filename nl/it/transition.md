---

copyright:
  years: 2016, 2019
lastupdated: "2019-06-06"

keywords: IBM Cloud, Activity Tracker, migration

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


# Transizione a {{site.data.keyword.at_full_notm}}
{: #transition}

{{site.data.keyword.cloudaccesstrailfull}} è obsoleto dal 9 maggio 2019. [Ulteriori informazioni](https://www.ibm.com/blogs/cloud-archive/2019/04/deprecating-ibm-cloud-activity-tracker/). Il servizio viene sostituito con {{site.data.keyword.at_full_notm}}. [Ulteriori informazioni](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started).
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} è obsoleto. A partire dal 9 maggio 2019, non puoi eseguire il provisioning delle nuove istanze di {{site.data.keyword.cloudaccesstrailshort}}. Le istanze del piano Premium esistenti sono supportate fino al 30 settembre 2019. Per continuare a monitorare l'attività del tuo account {{site.data.keyword.cloud_notm}}, esegui il provisioning di un'istanza di [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}


Completa la seguente procedura per migrare a {{site.data.keyword.at_full_notm}}: 

1. Salva una copia degli eventi archiviati in {{site.data.keyword.cloudaccesstrailfull}} per una ricerca a lungo termine. Puoi utilizzare la CLI o l'API {{site.data.keyword.cloudaccesstrailshort}}. 

    Assicurati di salvare i log dello spazio per ogni spazio Cloud Foundry in cui hai un'istanza {{site.data.keyword.cloudaccesstrailshort}} legacy e per ogni dominio dell'account in ciascuna regione che stai attualmente monitorando.

    * [Download degli eventi utilizzando la CLI](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-downloading_events).

    * [Download degli eventi utilizzando l'API](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-downloading_events_api).

2. Esegui il provisioning di [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-provision).

    Puoi eseguire il provisioning di solo 1 istanza per ogni regione. 
    
3. Crea e configura i gruppi di accesso per gestire le autorizzazioni in {{site.data.keyword.cloud_notm}}. 

    * [Concessione delle autorizzazioni di amministrazione a un utente o ID servizio](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-iam_manage_events).

    * [Concessione delle autorizzazioni utente a un utente o ID servizio](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-iam_view_events).

4. Definisci le viste e i dashboard in {{site.data.keyword.at_full_notm}} per analizzare e gestire gli eventi. [Ulteriori informazioni](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-views).

    La migrazione dei dashboard Kibana ai dashboard LogDNA non è automatizzata. Devi implementare manualmente i nuovi dashboard. 

    Tieni presente che in LogDNA gli istogrammi e i grafici a torta sono le uniche visualizzazioni che puoi implementare.

5. [Facoltativo] Configura l'archiviazione per la tua istanza {{site.data.keyword.at_full_notm}}. 

    Puoi archiviare gli eventi in {{site.data.keyword.cos_full_notm}} (COS). [Ulteriori informazioni](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-archiving).

    **Nota:** sei responsabile del provisioning di un'istanza COS che viene utilizzata per archiviare gli eventi e della conservazione degli eventi archiviati. 

    Questo passo è richiesto solo per le istanze {{site.data.keyword.at_full_notm}} con un piano a pagamento.

6. Esplora altre funzioni come ad esempio la [gestione degli avvisi](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-alerts).


Quando sei pronto a interrompere il monitoraggio dell'attività cloud tramite le tue istanze{{site.data.keyword.cloudaccesstrailshort}} legacy, completa la seguente procedura:

1. Elimina le istanze {{site.data.keyword.cloudaccesstrailshort}} legacy dalla console {{site.data.keyword.cloud_notm}}.
2. Rimuovi tutte le autorizzazioni agli utenti che utilizzano queste istanze legacy. 


