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


# Evénements de gestion des comptes  
{: #at_events_acc_mgt}

En tant que responsable de la sécurité, auditeur ou responsable, vous pouvez utiliser le service {{site.data.keyword.cloudaccesstrailfull}} pour suivre comment les utilisateurs et les applications interagissent avec le compte {{site.data.keyword.Bluemix}}. 
{:shortdesc}

Le service {{site.data.keyword.cloudaccesstrailfull_notm}} enregistre les activités initiées par l'utilisateur qui changent l'état d'un service dans {{site.data.keyword.cloud_notm}}. Pour plus d'informations, voir [A propos d'{{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#activity_tracker_ov ).

Pour commencer à surveiller les actions utilisateur, voir [{{site.data.keyword.cloudaccesstrailfull_notm}}](/docs/services/cloud-activity-tracker/index.html#getting-started-with-cla). 



## Evénements liés à la gestion des comptes
{: #at_events_acc_mgt_account}

Le tableau suivant répertorie les méthodes d'API générant un événement lorsqu'elles sont appelées :

<table>
  <caption>Actions qui génèrent des événements</caption>
  <tr>
    <th>Action</th>
	  <th>Description</th>
  </tr>
  <tr>
    <td>billing.account.create</td>
	  <td>Un événement est généré lorsque vous mettez un compte à disposition, une fois que l'ID de compte est affecté au compte.</td>
  </tr>
  <tr>
    <td>billing.account.update</td>
	  <td>Un événement est généré lorsque vous mettez à jour les informations relatives au compte.</td>
  </tr>
  <tr>
    <td>billing.account.active</td>
	  <td>Un événement est généré lorsque vous vérifiez le compte, c'est-à-dire quand le compte devient actif.</td>
  </tr>
  <tr>
    <td>billing.account.subscription.create</td>
	  <td>Un événement est généré lorsque vous créez un <a href="/docs/account/index.html#subscription-account">compte d'abonnement</a>.</td>
  </tr>
</table>



## Evénements liés à la gestion des utilisateurs
{: #at_events_acc_mgt_users}

Le tableau suivant répertorie les méthodes d'API générant un événement lorsqu'elles sont appelées :

<table>
  <caption>Actions qui génèrent des événements</caption>
  <tr>
    <th>Action</th>
	  <th>Description</th>
  </tr>
  <tr>
    <td>user-management.user.create</td>
	  <td>Un événement est généré lorsque vous envoyez une invitation à un utilisateur pour qu'il rejoigne un compte. </br>Le propriétaire du compte est le seul utilisateur du compte qui peut effectuer cette action.</td>
  </tr>
  <tr>
    <td>user-management.user.active</td>
	  <td>Un événement est généré lorsque vous activez l'utilisateur dans le compte. </br>L'événement est généré lorsque l'utilisateur confirme son adresse électronique.</td>
  </tr>
  <tr>
    <td>user-management.account.user.delete</td>
	  <td>Un événement est généré lorsque vous supprimez un utilisateur du compte. </br>Le propriétaire du compte est le seul utilisateur du compte qui peut effectuer cette action.</td>
  </tr>
</table>

## Evénements liés à la gestion des organisations
{: #at_events_acc_mgt_org}

Le tableau suivant répertorie les méthodes d'API générant un événement lorsqu'elles sont appelées :

<table>
  <caption>Action qui génère des événements</caption>
  <tr>
    <th>Action</th>
	  <th>Description</th>
  </tr>
  <tr>
    <td>billing.account.org.create</td>
	  <td>Un événement est généré lorsque vous ajoutez une organisation au compte.</td>
  </tr>
</table>

## Où rechercher les événements ?
{: #at_events_acc_mgt_ui}

Les événements {{site.data.keyword.cloudaccesstrailshort}} sont disponibles dans le **domaine de compte** de la région **Sud des Etats-Unis**. Pour plus d'information, voir [Affichage des événements de compte](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/viewing_events.html#view_acc_events_account_events).

Pour afficher ces événements, vous devez mettre à disposition une instance du service {{site.data.keyword.cloudaccesstrailshort}} dans la région **Sud des Etats-Unis**. Ensuite, vous devez ouvrir l'interface utilisateur d'{{site.data.keyword.cloudaccesstrailshort}}, puis accéder au domaine de compte pour afficher les événements. Pour plus d'information, voir [Affichage des événements de compte](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/viewing_events.html#view_acc_events_account_events). 








