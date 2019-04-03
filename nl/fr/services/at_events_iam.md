---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, IAM events

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


# Evénements IAM
{: #at_events_iam}

En tant que responsable de la sécurité, auditeur ou responsable, vous pouvez utiliser le service {{site.data.keyword.cloudaccesstrailfull}} pour suivre comment les utilisateurs et les applications interagissent avec le service {{site.data.keyword.iamlong}} (IAM) dans {{site.data.keyword.Bluemix}}. 
{:shortdesc}

Le service {{site.data.keyword.cloudaccesstrailfull_notm}} enregistre les activités initiées par l'utilisateur qui changent l'état d'un service dans {{site.data.keyword.cloud_notm}}. Pour plus d'informations, voir [A propos d'{{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov).

Pour commencer à surveiller les actions utilisateur, voir [{{site.data.keyword.cloudaccesstrailfull_notm}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started-with-cla#getting-started-with-cla). 

L'initiateur peut être un utilisateur, un service ou une application.
{: tip}

## Evénements de gestion des groupes d'accès
{: #at_events_iam_access}

Le tableau suivant répertorie les actions qui génèrent un événement :

| Action | Description |
|----------|---------|
| `iam-groups.group.create`   | Un événement est généré lorsqu'un initiateur crée un groupe d'accès. | 
| `iam-groups.group.read`     | Un événement est généré lorsqu'un initiateur examine les informations qui sont associées à des groupes d'accès. |
| `iam-groups.group.update`   | Un événement est généré lorsqu'un initiateur met à jour un nom de groupe ou une description. |
| `iam-groups.group.delete`   | Un événement est généré lorsqu'un initiateur supprime un groupe d'accès. |
| `iam-groups.member.add`     | Un événement est généré lorsqu'un initiateur ajoute un membre à un groupe d'accès. |
| `iam-groups.member.delete`  | Un événement est généré lorsqu'un initiateur supprime un membre d'un groupe d'accès. |
| `iam-groups.member.read`    | Un événement est généré lorsqu'un initiateur vérifie l'appartenance d'un membre. |
| `iam-groups.rule.read`      | Un événement est généré lorsqu'un initiateur affiche une règle dans un groupe d'accès. |
| `iam-groups.rule.create`    | Un événement est généré lorsqu'un initiateur ajoute une règle à un groupe d'accès. |
| `iam-groups.rule.update`    | Un événement est généré lorsqu'un initiateur modifie le nom de la règle. |
| `iam-groups.rule.delete`    | Un événement est généré lorsqu'un initiateur supprime une règle d'un groupe d'accès. |
{: caption="Tableau 1. Gestion des actions des groupes d'accès" caption-side="top"} 



## Evénements de gestion des ID de service
{: #at_events_iam_serviceids}

Le tableau suivant répertorie les actions qui génèrent un événement :

| Action | Description |
|----------|---------|
| `iam-identity.account-serviceid.create` | Un événement est généré lorsqu'un initiateur crée un ID de service.  | 
| `iam-identity.account-serviceid.update` | Un événement est généré lorsqu'un initiateur renomme un ID de service ou modifie sa description. | 
| `iam-identity.account-serviceid.delete` | Un événement est généré lorsqu'un initiateur supprime un ID de service. | 
{: caption="Tableau 2. Utilisation des actions d'ID de service" caption-side="top"} 


## Evénements de gestion des clés d'API
{: #at_events_iam_apikeys}

Le tableau suivant répertorie les actions qui génèrent un événement :

| Action | Description |
|----------|---------|
| `iam-identity.user-apikey.create`      | Un événement est généré lorsqu'un initiateur crée une clé d'API. | 
| `iam-identity.user-apikey.update`      | Un événement est généré lorsqu'un initiateur renomme une clé d'API ou modifie sa description. |  
| `iam-identity.user-apikey.delete`      | Un événement est généré lorsqu'un initiateur supprime une clé d'API. |  
| `iam-identity.serviceid-apikey.create` | Un événement est généré lorsqu'un initiateur crée une clé d'API pour un ID de service. |  
| `iam-identity.serviceid-apikey.delete` | Un événement est généré lorsqu'un initiateur supprime une clé d'API pour un ID de service. |  
{: caption="Tableau 3. Utilisation des actions des clés d'API" caption-side="top"} 


## Evénements de connexion
{: #at_events_iam_login}

Le tableau suivant répertorie les actions qui génèrent un événement :

| Action | Description |
|----------|---------|
| `iam-identity.user-apikey.login`         | Un événement est généré lorsqu'un initiateur se connecte à {{site.data.keyword.cloud_notm}} à l'aide d'une clé d'API. |  
| `iam-identity.serviceid-apikey.login`    | Un événement est généré lorsqu'un initiateur se connecte à {{site.data.keyword.cloud_notm}} à l'aide d'une clé d'API qui est associée à un ID de service. |  
| `iam-identity.user-identitycookie.login` | Il s'agit d'un événement qui est généré lorsqu'un initiateur demande un nouveau cookie d'identité pour exécuter une action. |
| `iam-identity.user-refreshtoken.login`   | Il s'agit d'un événement qui est généré lorsque l'initiateur se connecte à IBM Cloud, ou lorsqu'un initiateur qui s'est déjà connecté à IBM Cloud demande un nouveau jeton d'actualisation pour exécuter une action. |
{: caption="Tableau 4. Actions de connexion utilisateur" caption-side="top"} 


## Evénements de gestion des règles
{: #at_events_iam_policies}

Le tableau suivant répertorie les actions qui génèrent un événement :

| Action | Description |
|----------|---------|
| `iam-am.policy.create` | Un événement est généré lorsqu'un initiateur ajoute une règle à un utilisateur ou un groupe d'accès. |
| `iam-am.policy.delete` | Un événement est généré lorsqu'un initiateur modifie les droits d'accès à une règle d'un utilisateur ou d'un groupe d'accès.|
| `iam-am.policy.update` | Un événement est généré lorsqu'un initiateur supprime une règle qui est affectée à un utilisateur ou un groupe d'accès. |
{: caption="Tableau 5. Gestion des actions de règle" caption-side="top"} 


## Affichage d'événements
{: #at_events_iam_ui}

Les événements {{site.data.keyword.cloudaccesstrailshort}} sont disponibles dans le **domaine de compte** de la région **Sud des Etats-Unis**.

Pour afficher ces événements, vous devez mettre à disposition une instance du service {{site.data.keyword.cloudaccesstrailshort}} dans la région **Sud des Etats-Unis**. Ensuite, vous devez ouvrir l'interface utilisateur d'{{site.data.keyword.cloudaccesstrailshort}}, puis accéder au domaine de compte pour afficher les événements. 

Pour plus d'informations, voir [Affichage d'événements de compte](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-view_acc_events#view_acc_events_account_events).



