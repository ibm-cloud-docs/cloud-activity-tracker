---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, view events, UI

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


# Visualizzazione degli eventi
{: #view_acc_events}

Puoi visualizzare gli eventi tramite l'IU {{site.data.keyword.cloudaccesstrailshort}} nella console {{site.data.keyword.cloud_notm}} o tramite Kibana.
{:shortdesc}
   

## Visualizzazione degli eventi dell'account
{: #view_acc_events_account_events}

Puoi visualizzare gli eventi in un dominio dell'account {{site.data.keyword.cloudaccesstrailshort}} tramite l'IU {{site.data.keyword.cloudaccesstrailshort}} o Kibana.

Un **proprietario dell'account** dispone delle autorizzazioni per visualizzare gli eventi in un dominio dell'account {{site.data.keyword.cloudaccesstrailshort}} tramite l'IU {{site.data.keyword.cloudaccesstrailshort}} o Kibana.

Come **membro in un account**, considera le seguenti informazioni per visualizzare gli eventi dell'account in una regione:

* Devi avere il ruolo di *sviluppatore* nello spazio in cui viene eseguito il provisioning di {{site.data.keyword.cloudaccesstrailshort}}. Per ulteriori informazioni, vedi [Concessione di un ruolo CF](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-grant_permissions#grant_cf_role).

* Devi avere una politica IAM per il servizio {{site.data.keyword.loganalysisshort}} con il ruolo *visualizzatore* in tale regione. Il ruolo di visualizzatore è il ruolo minimo IAM richiesto. Per ulteriori informazioni, vedi [Concessione delle autorizzazioni IAM](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-grant_permissions#grant_iam_policy).

* Puoi visualizzare gli eventi tramite Kibana. Per ulteriori informazioni su come avviare Kibana, consulta [Passaggio a Kibana da un browser web](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-launch_kibana#launch_Kibana_from_browser).



## Visualizzazione degli eventi dello spazio
{: #view_acc_events_space_events}

Puoi visualizzare gli eventi in un dominio dello spazio {{site.data.keyword.cloudaccesstrailshort}} tramite l'IU {{site.data.keyword.cloudaccesstrailshort}}. Se hai un piano premium, puoi visualizzare gli eventi anche tramite Kibana.

Un **proprietario dell'account** dispone delle autorizzazioni per visualizzare gli eventi di tutti i domini dello spazio {{site.data.keyword.cloudaccesstrailshort}}.

Come **membro in un account**, devi avere un ruolo di *sviluppatore* nello spazio in cui viene eseguito il provisioning di {{site.data.keyword.cloudaccesstrailshort}}.


