---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, events

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
{:deprecated: .deprecated}


# Eventi {{site.data.keyword.cloudaccesstrailshort}}
{: #events}

Utilizza il servizio {{site.data.keyword.cloudaccesstrailfull}} per tenere traccia di {{site.data.keyword.cloudaccesstrailshort}} in {{site.data.keyword.Bluemix}}. 
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} è obsoleto. A partire dal 9 maggio 2019, non puoi eseguire il provisioning delle nuove istanze di {{site.data.keyword.cloudaccesstrailshort}}. Le istanze del piano Premium esistenti sono supportate fino al 30 settembre 2019. Per continuare a monitorare l'attività del tuo account {{site.data.keyword.cloud_notm}}, esegui il provisioning di un'istanza di [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}


## Elenco degli eventi
{: #actions}

La seguente tabella elenca le azioni che generano un evento:

<table>
  <caption>Tabella 1. Elenco di azioni che generano un evento</caption>
  <tr>
    <th>Azione</th>
	  <th>Descrizione</th>
  <tr>
  <tr>
    <td>read.events</td>
	  <td>Ottieni le informazioni sugli eventi che sono archiviati.</td>
  </tr>
  <tr>
    <td>create.sessions</td>
	  <td>Crea una sessione che può essere utilizzata per scaricare gli eventi.</td>
  </tr>
  <tr>
    <td>delete.session</td>
	  <td>Elimina una sessione.</td>
  </tr>
  <tr>
    <td>read.sessions</td>
	  <td>Elenca le sessioni.</td>
  </tr>
  <tr>
    <td>download.events</td>
	  <td>Scarica gli eventi.</td>
  </tr>
  <tr>
    <td>delete.events</td>
	  <td>Elimina gli eventi.</td>
  </tr>
</table>


## Dove cercare gli eventi
{: #ui}
 	
Gli eventi {{site.data.keyword.cloudaccesstrailshort}} sono disponibili nello spazio Cloud Foundry in cui viene eseguito il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}.
