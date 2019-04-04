---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, overview

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



# A propos d'{{site.data.keyword.cloudaccesstrailshort}}
{: #activity_tracker_ov}

Utilisez le service {{site.data.keyword.cloudaccesstrailfull}} pour suivre comment les applications interagissent avec les services {{site.data.keyword.cloud_notm}}. Utilisez {{site.data.keyword.cloudaccesstrailshort}} pour identifier une activité anormale et pour vérifier votre conformité avec les exigences d'audit réglementaires. Les événements collectés sont conformes à la norme CADF (Cloud Auditing Data Federation).
{:shortdesc}

* {{site.data.keyword.cloudaccesstrailshort}} offre une
gouvernance de haut niveau de la sécurité de vos ressources informatiques dans le cloud.
* {{site.data.keyword.cloudaccesstrailshort}} fournit aux administrateurs une solution pour la capture, le stockage, l'affichage, la recherche et la surveillance de l'activité d'API depuis un seul endroit.
* {{site.data.keyword.cloudaccesstrailshort}} fournit des fonctions de téléchargement d'événements que vous pouvez utiliser pour générer un rapport de piste d'audit. Vous pouvez avoir besoin de ces rapports pour vérifier que votre organisation se conforme
à vos règlements internes et aux réglementations externes du secteur et du pays.

La conformité avec les règlements internes et les réglementations du secteur est une exigence cruciale dans la stratégie
d'une organisation, quel que soit l'endroit où les applications s'exécutent : sur site, dans un cloud hybride ou dans un cloud public. Le service {{site.data.keyword.cloudaccesstrailshort}} fournit l'infrastructure et les fonctions de surveillance des appels d'API et permet de s'assurer de la conformité avec les règles de l'entreprise et avec les réglementations spécifiques au secteur d'activité.

Lorsque vous travaillez dans un environnement de cloud, tel qu'{{site.data.keyword.cloud_notm}}, vous devez planifier la stratégie de cloud pour l'audit
et la surveillance des contenus et des données en conformité avec vos règlements internes et avec les exigences de conformité du secteur et du pays. Vous pouvez
utiliser les informations enregistrées via le service {{site.data.keyword.cloudaccesstrailshort}}
pour identifier des incidents de sécurité, détecter des accès non autorisés et vous conformer aux exigences d'audit réglementaires et internes.

Par exemple, vous pouvez utiliser les journaux d'activité {{site.data.keyword.cloudaccesstrailshort}} pour identifier les informations suivantes :

* Utilisateurs ayant effectué des appels d'API à des services cloud.
* Adresse IP source depuis laquelle les appels d'API ont été effectués.
* Horodatage des appels d'API.
* Statut de l'appel d'API.


## Collecte d'événements
{: #activity_tracker_ov_collect}

Le service {{site.data.keyword.cloudaccesstrailshort}} capture les données d'activité associées à des appels d'API et à d'autres actions effectuées pour sélectionner des services cloud dans {{site.data.keyword.cloud_notm}}. 

* Les événements sont collectés automatiquement. 
* Les événements collectés dans {{site.data.keyword.cloudaccesstrailshort}} sont conformes à la norme CADF (Cloud Auditing Data Federation). La norme CADF définit un modèle d'événement complet incluant les informations nécessaires pour certifier, gérer et auditer
la sécurité des applications dans les environnements de cloud.
* {{site.data.keyword.cloudaccesstrailshort}} stocke et groupe les événements par domaine. Il existe un domaine de compte par région et un domaine d'espace par espace Cloud Foundry. 

Le modèle d'événement CADF inclut les composants suivants :

<table>
  <caption>Tableau 1. Composants disponibles dans un modèle d'événement CADF</caption>
  <tr>
    <th>Composant</th>
	<th>Description</th>
  </tr>
  <tr>
    <td>Action</td>
	<td>L'action est l'opération ou l'activité qu'effectue l'initiateur, qu'il tente d'effectuer, ou dont il attend l'achèvement.</td>
  </tr>
  <tr>
    <td>Initiateur</td>
	<td>L'initiateur est la ressource effectuant un appel d'API et générant un événement CADF. L'événement déclenché dépend de l'action demandée par l'appel d'API.</td>
  </tr>
  <tr>
    <td>Observateur</td>
	<td>L'observateur est la ressource qui crée et sauvegarde un enregistrement CADF à partir des informations disponibles dans un événement CADF.</td>
  </tr>
  <tr>
    <td>Résultat</td>
	<td>Le résultat est le statut de l'action par rapport à la cible.</td>
  </tr>
  <tr>
    <td>Cible</td>
	<td>La cible est la ressource sur laquelle l'action est réalisée, tentée ou dont l'achèvement est attendu</td>
  </tr>
</table>


Prenez en compte les informations suivantes lorsque vous travaillez avec le journal {{site.data.keyword.cloudaccesstrailshort}} dans le cloud {{site.data.keyword.IBM_notm}} public :

* Vous ne pouvez stocker que des enregistrements d'audit pour des appels d'API à des ressources s'exécutant dans le cloud {{site.data.keyword.IBM_notm}} public.
* Seul le stockage en cloud {{site.data.keyword.IBM_notm}} public est utilisé pour collecter des événements.
* Les informations sont conservées pendant 3 jours. Passé ce délai, les informations sont supprimées selon la méthode Premier entré, premier sorti (FIFO).
* Les événements CADF de type *Activity* sont pris en charge par le service {{site.data.keyword.cloudaccesstrailshort}}.


## Mise à disposition d'Activity Tracker
{: #activity_tracker_ov_provision}

Pour afficher les événements disponibles via un domaine de compte, vous devez mettre le service {{site.data.keyword.cloudaccesstrailshort}} à disposition dans un espace Cloud Foundry dans la région où vous voulez surveiller l'activité d'API. Seul le **propriétaire de compte** peut voir les événements de compte.

Pour afficher les événements disponibles via un domaine d'espace, vous devez mettre le service {{site.data.keyword.cloudaccesstrailshort}} à disposition dans l'espace où vous voulez surveiller l'activité d'API.

Pour savoir comment mettre à disposition le service {{site.data.keyword.cloudaccesstrailshort}}, voir [Mise à disposition du service {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-provision#provision).



## Analyse des journaux d'activité
{: #activity_tracker_ov_analyze}

Vous pouvez analyser les journaux d'activité via l'interface utilisateur d'{{site.data.keyword.cloudaccesstrailshort}} dans {{site.data.keyword.cloud_notm}} ou à l'aide de Kibana, un outil open source. Vous pouvez surveiller les événements disponibles dans un espace spécifique ou au niveau du compte.

Vous pouvez rechercher, analyser et surveiller les journaux d'activité des dernières 24 heures via l'interface utilisateur d'{{site.data.keyword.cloudaccesstrailshort}} dans {{site.data.keyword.cloud_notm}}. Pour plus d'informations, voir [Accès à l'interface utilisateur d'{{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-launch_at_ui#launch_at_ui).

Vous pouvez rechercher, analyser et surveiller les journaux d'activité des 3 derniers jours via Kibana à l'aide du tableau de bord Kibana d'{{site.data.keyword.cloudaccesstrailshort}} ou en créant vos propres tableaux de bord personnalisés. * **Remarque :** Cette fonction est disponible pour les utilisateurs du plan **Premium**.

* Pour plus d'informations sur le lancement de Kibana, voir [Accès au tableau de bord Kibana](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-launch_kibana#launch_kibana). 
* Pour obtenir une liste de zones que vous pouvez utiliser pour analyser des événements dans Kibana, voir [Zones d'événement {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-at_event#at_event)



## Régions
{: #activity_tracker_ov_regions}

Le service {{site.data.keyword.cloudaccesstrailshort}} est disponible dans les régions suivantes :

* Allemagne
* Sydney
* Royaume-Uni (seul le plan Lite est disponible)
* Sud des Etats-Unis


## Plan de service
{: #activity_tracker_ov_plan}

Le service {{site.data.keyword.cloudaccesstrailshort}} propose plusieurs plans.

Vous pouvez modifier un plan via l'interface utilisateur {{site.data.keyword.cloud_notm}} ou via la ligne de commande. Vous pouvez mettre à niveau ou rétrograder votre plan à tout moment. Pour plus d'informations sur la sélection d'un plan de service de niveau supérieur, voir [Changement de plan](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-change_plan#change_plan). 

Le tableau suivant présente les plans disponibles :

<table>
    <caption>Tableau 1. Fonctions d'ingestion d'événement, de conservation d'événement et d'exportation des événements</caption>
      <tr>
        <th>Plan</th>
        <th>Ingestion d'événement</th>
        <th>Conservation d'événement</th>
		<th>Exportation des événements</th>
      </tr>
      <tr>
        <td>Lite (par défaut)</td>
        <td>Non</td>
        <td>3 derniers jours</td>
		<td>Non</td>
      </tr>
      <tr>
        <td>Premium</td>
        <td>Oui</td>
        <td>Nombre de jours configurable.</td>
		<td>Oui</td>
      </tr>
</table>

<table>
    <caption>Tableau 2. Fonctions de gestion et d'affichage des événements</caption>
      <tr>
        <th>Plan</th>
		    <th>API</th>
		    <th>Interface de ligne de commande</th>
        <th>Kibana</th>
      </tr>
      <tr>
        <td>Lite (par défaut)</td>
		    <td>Non</td>
		    <td>Non</td>
        <td>Non</td>
      </tr>
      <tr>
        <td>Premium</td>
		    <td>Oui</td>
		    <td>Oui</td>
        <td>Oui</td>
      </tr>
</table>

**Remarque :** Le coût mensuel de stockage des événements est calculé sous forme de moyenne du cycle de facturation.

## Sécurité
{: #activity_tracker_ov_security}

Prenez en compte les informations suivantes concernant la sécurité lorsque vous travaillez avec le service {{site.data.keyword.cloudaccesstrailshort}} :

* Les services IBM qui génèrent des événements {{site.data.keyword.cloudaccesstrailshort}} respectent la politique de sécurité {{site.data.keyword.IBM_notm}} Cloud. Pour plus d'informations, voir [Faites confiance à la sécurité et à la confidentialité d'IBM Cloud ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/cloud-computing/learn-more/why-ibm-cloud/security/){: new_window}.
* Le service {{site.data.keyword.cloudaccesstrailshort}} capture les actions initiées par des utilisateurs, qui modifient l'état de services Cloud. Les informations ne permettent pas un accès direct à des bases de données ou des applications.
* Seuls les utilisateurs autorisés peuvent afficher et surveiller les journaux d'événements {{site.data.keyword.cloudaccesstrailshort}}. Chaque utilisateur est identifié par son ID unique dans {{site.data.keyword.cloud_notm}}.
