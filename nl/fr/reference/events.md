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


# Evénements {{site.data.keyword.cloudaccesstrailshort}}
{: #events}

Utilisez le service {{site.data.keyword.cloudaccesstrailfull}} pour suivre {{site.data.keyword.cloudaccesstrailshort}} dans {{site.data.keyword.Bluemix}}. 
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} est obsolète. A compter du 9 mai 2019, vous ne pourrez plus mettre à disposition de nouvelles instances {{site.data.keyword.cloudaccesstrailshort}}. Les instances de plan existantes sont prises en charge jusqu'au 30 septembre 2019. Pour continuer à surveiller l'activité de votre compte {{site.data.keyword.cloud_notm}}, mettez à disposition une instance du [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}


## Liste des événements
{: #actions}

Le tableau suivant répertorie les actions qui génèrent un événement :

<table>
  <caption>Tableau 1. Liste des actions qui génèrent un événement</caption>
  <tr>
    <th>Action</th>
	  <th>Description</th>
  <tr>
  <tr>
    <td>read.events</td>
	  <td>Permet d'obtenir des informations sur les événements qui sont stockés.</td>
  </tr>
  <tr>
    <td>create.sessions</td>
	  <td>Permet de créer une session qui peut être utilisée pour télécharger des événements.</td>
  </tr>
  <tr>
    <td>delete.session</td>
	  <td>Permet de supprimer une session.</td>
  </tr>
  <tr>
    <td>read.sessions</td>
	  <td>Permet de répertorier les sessions.</td>
  </tr>
  <tr>
    <td>download.events</td>
	  <td>Permet de télécharger des événements.</td>
  </tr>
  <tr>
    <td>delete.events</td>
	  <td>Permet de supprimer des événements.</td>
  </tr>
</table>


## Où rechercher les événements ?
{: #ui}
 	
Les événements {{site.data.keyword.cloudaccesstrailshort}} sont disponibles dans l'espace Cloud Foundry où le service {{site.data.keyword.cloudaccesstrailshort}} est mis à disposition.
