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

# Evénements d'instance de service  
{: #at_events_rc}

En tant que responsable de la sécurité, auditeur ou responsable, vous pouvez utiliser le service {{site.data.keyword.cloudaccesstrailfull}} pour suivre comment les utilisateurs et les applications interagissent avec les services {{site.data.keyword.Bluemix}}. 
{:shortdesc}

Le service {{site.data.keyword.cloudaccesstrailfull_notm}} enregistre les activités initiées par l'utilisateur qui changent l'état d'un service dans {{site.data.keyword.cloud_notm}}. Pour plus d'informations, voir [A propos d'{{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov).

Pour commencer à surveiller les actions utilisateur, voir [{{site.data.keyword.cloudaccesstrailfull_notm}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started-with-cla#getting-started-with-cla). 


## Evénements liés à la mise à disposition et à la gestion des instances de service
{: #at_events_rc_provision}

Le tableau suivant répertorie les méthodes d'API générant un événement lorsqu'elles sont appelées :

<table>
  <caption>Actions qui génèrent des événements</caption>
  <tr>
    <th>Action</th>
	  <th>Description</th>
  </tr>
  <tr>
    <td><i>nom_service</i>.instance.create</td>
	  <td>Un événement est généré lorsque vous mettez à disposition une instance de service.</td>
  </tr>
  <tr>
    <td><i>nom_service</i>.instance.update</td>
	  <td>Un événement est généré lorsque vous renommez une instance de service ou lorsque vous modifiez le plan de service.</td>
  </tr>
  <tr>
    <td><i>nom_service</i>.instance.delete</td>
	  <td>Un événement est généré lorsqu'une instance de service est supprimée.</td>
  </tr>
</table>


##  Evénements liés à la gestion des clés d'API associées à une instance de service
{: #at_events_rc_keys}

Le tableau suivant répertorie les méthodes d'API générant un événement lorsqu'elles sont appelées :

<table>
  <caption>Actions qui génèrent des événements</caption>
  <tr>
    <th>Action</th>
	  <th>Description</th>
  </tr>
  <tr>
    <td><i>nom_service</i>.key.create</td>
	  <td>Un événement est généré lorsqu'une clé d'API est créée pour une instance de service via la section *Données d'identification pour le service* de l'interface utilisateur de l'instance de service.</td>
  </tr>
  <tr>
    <td><i>nom_service</i>.key.delete</td>
	  <td>Un événement est généré lorsqu'une clé d'API qui est associée à une instance de service est supprimée de la section *Données d'identification pour le service* de l'interface utilisateur de l'instance de service.</td>
  </tr>
</table>

##  Evénements liés à la liaison d'une instance de service à une application
{: #at_events_rc_bind}

Le tableau suivant répertorie les méthodes d'API générant un événement lorsqu'elles sont appelées :

<table>
  <caption>Actions qui génèrent des événements</caption>
  <tr>
    <th>Action</th>
	  <th>Description</th>
  </tr>
  <tr>
    <td><i>nom_service</i>.binding.create</td>
	  <td>Un événement est généré lorsque vous liez une instance de service à une application.</td>
  </tr>
  <tr>
    <td><i>nom_service</i>.binding.delete</td>
	  <td>Un événement est généré lorsque vous annulez la liaison d'une instance de service à une application.</td>
  </tr>
</table>




## Où rechercher les événements ?
{: #at_events_rc_ui}

Les événements {{site.data.keyword.cloudaccesstrailshort}} sont disponibles dans le **domaine de compte** de la région **Sud des Etats-Unis**.

Pour afficher ces événements, vous devez mettre à disposition une instance du service {{site.data.keyword.cloudaccesstrailshort}} dans la région **Sud des Etats-Unis**. Ensuite, vous devez ouvrir l'interface utilisateur d'{{site.data.keyword.cloudaccesstrailshort}}, puis accéder au domaine de compte pour afficher les événements. 

Pour plus d'informations, voir [Affichage d'événements de compte](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-view_acc_events#view_acc_events_account_events).



