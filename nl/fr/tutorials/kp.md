---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, monitoring activity, tutorial

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


# Surveillance de l'activité de {{site.data.keyword.keymanagementserviceshort}} avec {{site.data.keyword.cloudaccesstrailshort}}
{: #kp}

Utilisez ce tutoriel pour apprendre à utiliser le service {{site.data.keyword.cloudaccesstrailfull}} pour surveiller l'interaction d'un utilisateur avec le service {{site.data.keyword.keymanagementserviceshort}}. 
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} est obsolète. A compter du 9 mai 2019, vous ne pourrez plus mettre à disposition de nouvelles instances {{site.data.keyword.cloudaccesstrailshort}}. Les instances de plan existantes sont prises en charge jusqu'au 30 septembre 2019. Pour continuer à surveiller l'activité de votre compte {{site.data.keyword.cloud_notm}}, mettez à disposition une instance du [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}

1. Découvrez comment mettre à disposition le service {{site.data.keyword.cloudaccesstrailshort}}.
2. Découvrez comment utiliser un service Cloud pour générer des événements d'activité qui sont automatiquement collectés par le service {{site.data.keyword.cloudaccesstrailshort}}.
3. Découvrez comment surveiller l'activité Cloud d'un service en utilisant les tableaux de bord prédéfinis d'{{site.data.keyword.cloudaccesstrailshort}}.

La figure suivante représente les différents composants et les actions impliqués lorsqu'une activité initiée par un utilisateur modifie l'état d'un service :

![Composants et actions impliqués lorsqu'une activité initiée par un utilisateur modifie l'état d'un service](../images/AT_f1.png "Composants et actions impliqués lorsqu'une activité initiée par un utilisateur modifie l'état d'un service")



## Avant de commencer
{: #kp_prereqs}

Créez un compte [{{site.data.keyword.cloud_notm}}](https://cloud.ibm.com/login). Votre ID utilisateur doit être membre ou propriétaire d'un compte {{site.data.keyword.cloud_notm}} doté des droits d'accès de développeur sur l'espace où vous prévoyez d'utiliser le service {{site.data.keyword.cloudaccesstrailshort}}.


## Etape 1. Mise à disposition du service Activity Tracker
{: #kp_step1}

Vous devez mettre à disposition le service {{site.data.keyword.cloudaccesstrailshort}} dans la région où le service Cloud dont vous voulez surveiller l'activité est à disposition. Une fois le service {{site.data.keyword.cloudaccesstrailshort}} mis à disposition, les événements sont collectés automatiquement à partir des services Cloud sélectionnés. 

**Remarque :** Ce tutoriel montre comment utiliser le service {{site.data.keyword.cloudaccesstrailshort}} pour surveiller l'interaction d'un utilisateur avec le service Cloud {{site.data.keyword.keymanagementservicelong_notm}} dans la région Sud des Etats-Unis. Par conséquent, vous devez mettre {{site.data.keyword.cloudaccesstrailshort}} à disposition dans la région Sud des Etats-Unis. Pour afficher les informations relatives à la région où un service est à disposition, voir [Services par région](/docs/resources?topic=resources-services_region#services_region).

Procédez comme suit pour mettre à disposition une instance du service {{site.data.keyword.cloudaccesstraillong_notm}} dans {{site.data.keyword.cloud_notm}} :

1. [Connectez-vous à {{site.data.keyword.cloud_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://cloud.ibm.com/login){:new_window}.
    
	Après que vous vous êtes connecté avec votre ID utilisateur et votre mot de passe, l'interface utilisateur {{site.data.keyword.cloud_notm}} s'ouvre.

2. Cliquez sur **Catalogue**. La liste des services disponibles dans {{site.data.keyword.cloud_notm}} s'affiche.

3. Sélectionnez la catégorie **Sécurité et identité** pour filtrer la liste de services affichée.

    **Remarque :** Le service est également disponible via la catégorie **Developer Tools**.

4. Cliquez sur la vignette **Activity Tracker**. 

5. Configurez les informations qui définissent où le service va être mis à disposition. 

    Entrez les données indiquées dans le tableau suivant : 

    <table>
	  <caption>Tableau 1. Zones obligatoires pour mise à disposition du service {{site.data.keyword.cloudaccesstrailshort}}</caption>
	  <tr>
	    <th width="50%">Zone</th>
		<th width="50%">Valeur</th>
	  </tr>
	  <tr>
	    <td>Sélectionnez une région dans laquelle effectuer le déploiement :</td>
		<td>Sud des Etats-Unis</td>
	  </tr>
	  <tr>
	    <td>Choisissez une organisation :</td>
		<td>Sélectionnez l'organisation dans laquelle vous prévoyez de mettre le service {{site.data.keyword.cloudaccesstrailshort}} à disposition.</td>
	  </tr>
	  <tr>
	    <td>Choisissez un espace :</td>
		<td>Sélectionnez l'espace dans l'organisation dans laquelle vous prévoyez de mettre à disposition le service {{site.data.keyword.cloudaccesstrailshort}}.</td>
	  </tr>
	</table>

6. Cliquez sur **Créer** pour mettre à disposition le service {{site.data.keyword.cloudaccesstrailshort}} dans l'espace auquel vous êtes connecté.
   

## Etape 2.  Configuration du service Cloud  
{: #kp_step2}

Ce tutoriel montre comment surveiller l'activité des API pour le service {{site.data.keyword.keymanagementserviceshort}} dans {{site.data.keyword.cloud_notm}}.

Procédez comme suit pour configurer le service {{site.data.keyword.keymanagementserviceshort}} dans {{site.data.keyword.cloud_notm}} :

1. Mettez à disposition une instance du service {{site.data.keyword.keymanagementserviceshort}} dans la région Sud des Etats-Unis. Pour plus d'informations, voir [Mise à disposition à partir de la console IBM Cloud](/docs/services/key-protect?topic=key-protect-provision#provision).

2. Définissez les droits {{site.data.keyword.cloud_notm}} pour l'utilisateur à l'aide duquel vous prévoyez de gérer des clés. 

    Un utilisateur a besoin d'une règle IAM avec un rôle de service défini sur *Responsable* ou *Auteur* pour pouvoir créer des clés.

    Un utilisateur a besoin d'une règle IAM avec un rôle de service défini sur *Responsable* pour pouvoir supprimer des clés.

    Un utilisateur a besoin d'une règle IAM avec un rôle de service défini sur *Lecteur* pour pouvoir afficher des clés. 


## Etape 3. Génération d'un événement Activity Tracker
{: #kp_step3}

Dans cette étape, créez une clé de sécurité à l'aide du service {{site.data.keyword.keymanagementserviceshort}} afin de générer des données d'événement {{site.data.keyword.cloudaccesstrailshort}}. Pour plus d'informations, voir [Création de nouvelles clés](/docs/services/key-protect?topic=key-protect-create-standard-keys#create-standard-keys).

* La création d'une clé a pour résultat la génération d'événements {{site.data.keyword.cloudaccesstrailshort}}.
* Les événements {{site.data.keyword.cloudaccesstrailshort}} sont disponibles dans le **domaine de compte** {{site.data.keyword.cloudaccesstrailshort}}, lui-même disponible dans la région {{site.data.keyword.cloud_notm}} où les événements sont générés. 

## Etape 4. Surveillance d'un événement Activity Tracker
{: #kp_step4}

Dans cette étape, vérifiez à l'aide de l'interface utilisateur {{site.data.keyword.cloud_notm}} si des événements {{site.data.keyword.cloudaccesstrailshort}} sont générés.

Pour vérifier qu'un événement a été créé, procédez comme suit :

1. Accordez à l'utilisateur des droits lui permettant d'afficher des événements de compte. Pour plus d'informations, voir [Affichage d'événements de compte](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-view_acc_events#view_acc_events_account_events) et [Octroi de droits pour la consultation des événements de compte](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-grant_permissions#grant_acc_events).

2. Dans le tableau de bord {{site.data.keyword.cloud_notm}}, sélectionnez le service {{site.data.keyword.cloudaccesstrailshort}}. Le tableau de bord du service s'ouvre.

3. Configurez la vue de recherche des événements {{site.data.keyword.keymanagementserviceshort}} générés lorsque vous avez mis à disposition le service et ajouté une clé.

    * Sélectionnez **Journaux de compte** pour la zone *Afficher les journaux*.
    * Sélectionnez ** target.typeURI_str** pour la zone *Recherche* et saisissez `kms/secrets` dans la zone *Filtre*.
	
    Les données affichées correspondent aux événements {{site.data.keyword.keymanagementserviceshort}} disponibles pour les dernières 24 heures. 
	


## Etapes suivantes
{: #kp_next_steps}

Ensuite, utilisez le tableau de bord Kibana prédéfini d'{{site.data.keyword.cloudaccesstrailshort}} pour surveiller et analyser les journaux des événements. Pour lancer Kibana, voir [Accès au tableau de bord Kibana](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-launch_kibana#launch_kibana). Dans Kibana, les journaux d'activité des espaces sont, par défaut, affichés à l'aide du tableau de bord **ActivityTracker_Space_Dashboard_in_24h** :

Vous pouvez également utiliser l'interface de ligne de commande d'{{site.data.keyword.cloudaccesstrailshort}} pour gérer vos événements depuis la ligne de commande. Pour plus d'informations, voir [Affichage des informations sur les événements](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-viewing_event_status#viewing_event_status).



