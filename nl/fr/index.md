---

copyright:
  years: 2016, 2018
lastupdated: "2018-09-12"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# Tutoriel de prise en main
{: #getting-started-with-cla}

Le service {{site.data.keyword.cloudaccesstrailfull}} enregistre des activités initiées par l'utilisateur qui change l'état d'un service dans {{site.data.keyword.Bluemix}}. Utilisez ce tutoriel pour apprendre comment utiliser le service {{site.data.keyword.cloudaccesstrailfull}} pour surveiller l'interaction d'un utilisateur avec un service Cloud. 
{:shortdesc}

Les objectifs de ce tutoriel de prise en main sont les suivants :

1. Montrer comment mettre à disposition le service {{site.data.keyword.cloudaccesstrailshort}}.
2. Montrer comment utiliser un service Cloud pour générer des événements d'activité automatiquement collectés par le service {{site.data.keyword.cloudaccesstrailshort}}. Les événements sont conformes à la [norme CADF (Cloud Auditing Data Federation) ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.dmtf.org/sites/default/files/standards/documents/DSP0262_1.0.0.pdf){: new_window}. 
3. Montrer comment surveiller l'activité Cloud d'un service à l'aide des tableaux de bord {{site.data.keyword.cloudaccesstrailshort}} prédéfinis.

La figure suivante représente les différents composants et les actions impliqués lorsqu'une activité initiée par un utilisateur modifie l'état d'un service :

![Composants et actions impliqués lorsqu'une activité initiée par un utilisateur modifie l'état d'un service](images/AT_f1.png "Composants et actions impliqués lorsqu'une activité initiée par un utilisateur modifie l'état d'un service")



## Avant de commencer
{: #prereqs}

Créez un compte [{{site.data.keyword.Bluemix_notm}}](https://console.bluemix.net/registration/). Votre ID utilisateur doit être membre ou propriétaire d'un compte {{site.data.keyword.Bluemix_notm}} doté des droits d'accès de développeur sur l'espace où vous prévoyez d'utiliser le service {{site.data.keyword.cloudaccesstrailshort}}.


## Etape 1 : Mise à disposition d'Activity Tracker
{: #step1}

Vous devez mettre le service {{site.data.keyword.cloudaccesstrailshort}} à disposition dans la région où le service Cloud dont vous voulez surveiller l'activité est à disposition. Une fois le service {{site.data.keyword.cloudaccesstrailshort}} mis à disposition, les événements sont collectés automatiquement à partir des services Cloud sélectionnés.  

**Remarque :** Ce tutoriel montre comment utiliser le service {{site.data.keyword.cloudaccesstrailshort}} pour surveiller l'interaction d'un utilisateur avec le service Cloud {{site.data.keyword.keymanagementservicelong_notm}} dans la région Sud des Etats-Unis. Par conséquent, vous devez mettre {{site.data.keyword.cloudaccesstrailshort}} à disposition dans la région Sud des Etats-Unis. Pour afficher les informations relatives à la région où un service est à disposition, voir [Services par région](/docs/resources/services_region.html#services_region).

Procédez comme suit pour mettre à disposition une instance du service {{site.data.keyword.cloudaccesstraillong_notm}} dans {{site.data.keyword.Bluemix_notm}} :

1. Connectez-vous à {{site.data.keyword.Bluemix_notm}}.

    Le tableau de bord {{site.data.keyword.Bluemix_notm}} se trouve à l'adresse suivante : [http://bluemix.net ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://bluemix.net){:new_window}.
    
	Après que vous vous êtes connecté avec votre ID utilisateur et votre mot de passe, l'interface utilisateur {{site.data.keyword.Bluemix_notm}} s'ouvre.

2. Cliquez sur **Catalogue**. La liste des services disponibles dans {{site.data.keyword.Bluemix_notm}} s'affiche.

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
		<td>Sélectionnez l'organisation dans laquelle vous prévoyez de mettre le service {{site.data.keyword.cloudaccesstrailshort}} à disposition. </td>
	  </tr>
	  <tr>
	    <td>Choisissez un espace :</td>
		<td>Sélectionnez l'espace de l'organisation sélectionnée dans lequel vous prévoyez de mettre le service {{site.data.keyword.cloudaccesstrailshort}} à disposition. </td>
	  </tr>
	</table>

6. Cliquez sur **Créer** pour mettre à disposition le service {{site.data.keyword.cloudaccesstrailshort}} dans l'espace auquel vous êtes connecté. 
   

## Etape 2 : Configuration du service Cloud  
{: #step2}

Ce tutoriel montre comment surveiller l'activité des API pour le service {{site.data.keyword.keymanagementserviceshort}} dans {{site.data.keyword.Bluemix_notm}}. 

Procédez comme suit pour configurer le service {{site.data.keyword.keymanagementserviceshort}} dans {{site.data.keyword.Bluemix_notm}} :

1. Mettez à disposition une instance du service {{site.data.keyword.keymanagementserviceshort}} dans la région Sud des Etats-Unis. Pour plus d'informations, voir [Mise à disposition à partir de la console IBM Cloud](/docs/services/key-protect/provision.html#provision). 

2. Définissez les droits {{site.data.keyword.Bluemix_notm}} pour l'utilisateur à l'aide duquel vous prévoyez de gérer des clés.  

    * Un utilisateur a besoin d'une règle IAM avec un rôle de service défini sur *Responsable* ou *Auteur* pour pouvoir créer des clés. 
	* Un utilisateur a besoin d'une règle IAM avec un rôle de service défini sur *Responsable* pour pouvoir supprimer des clés. 
	* Un utilisateur a besoin d'une règle IAM avec un rôle de service défini sur *Lecteur* pour pouvoir afficher des clés.  


## Etape 3 : Génération d'un événement de suivi d'activité
{: # step3}

Dans cette étape, créez une clé de sécurité à l'aide du service {{site.data.keyword.keymanagementserviceshort}} afin de générer des données d'événement {{site.data.keyword.cloudaccesstrailshort}}. Pour plus d'informations, voir [Création de clés](/docs/services/key-protect/create-standard-keys.html#create-standard-keys). 

* La création d'une clé a pour résultat la génération d'événements {{site.data.keyword.cloudaccesstrailshort}}.
* Les événements {{site.data.keyword.cloudaccesstrailshort}} sont disponibles dans le **domaine de compte** {{site.data.keyword.cloudaccesstrailshort}} qui se trouve dans la région {{site.data.keyword.Bluemix_notm}} où les événements sont générés. 

## Etape 4 : Surveillance d'un événement de suivi d'activité
{: #step4}

Dans cette étape, vérifiez à l'aide de l'interface utilisateur {{site.data.keyword.Bluemix_notm}} des événements {{site.data.keyword.cloudaccesstrailshort}} sont générés.

Vérifiez comme suit qu'un événement a été créé :

1. Accordez à l'utilisateur des droits lui permettant d'afficher des événements de compte. Pour plus d'informations, voir [Affichage d'événements de compte](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/viewing_events.html#account_events) et
[Octroi de droits pour l'affichage d'événements de compte](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_acc_events).

2. Dans le tableau de bord {{site.data.keyword.Bluemix_notm}}, sélectionnez le service {{site.data.keyword.cloudaccesstrailshort}}. Le tableau de bord du service s'ouvre.

3. Configurez la vue de recherche des événements {{site.data.keyword.keymanagementserviceshort}} générés lorsque vous avez mis le service a disposition et ajouté une clé.

    * Sélectionnez **Journaux de compte** pour la zone *Afficher les journaux*.
    * Sélectionnez ** target.typeURI_str** pour la zone *Recherche* et saisissez **kms/secrets** dans la zone *Filtre*. 
	
    Les données affichées correspondent aux événements {{site.data.keyword.keymanagementserviceshort}} disponibles pour les dernières 24 heures. 
	


## Etapes suivantes
{: #next_steps}

Ensuite, utilisez le tableau de bord Kibana prédéfini d'{{site.data.keyword.cloudaccesstrailshort}} pour surveiller et analyser les journaux des événements. Pour lancer Kibana, voir [Accès au tableau de bord Kibana](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_kibana.html#launch_kibana). Dans Kibana, les journaux d'activité des espaces sont, par défaut, affichés à l'aide du tableau de bord **ActivityTracker_Space_Dashboard_in_24h** :

Vous pouvez également utiliser l'interface de ligne de commande d'{{site.data.keyword.cloudaccesstrailshort}} pour gérer vos événements depuis la ligne de commande. Pour plus d'information, voir [Affichage d'informations sur les événements](/docs/services/cloud-activity-tracker/how-to/viewing_event_information.html#viewing_event_status).



