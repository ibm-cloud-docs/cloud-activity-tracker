---

copyright:
  years: 2016, 2017
lastupdated: "2017-09-17"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Tutoriel de prise en main
{: #getting-started-with-cla}

Le service {{site.data.keyword.cloudaccesstrailfull}} enregistre les activités initiées par des utilisateurs, qui modifient l'état d'un service dans le cloud {{site.data.keyword.IBM}}. Utilisez ce tutoriel pour apprendre comment utiliser le service {{site.data.keyword.cloudaccesstrailfull}} pour surveiller l'interaction d'un utilisateur avec un service Cloud.
{:shortdesc}

Les objectifs de ce tutoriel de prise en main sont les suivants :

1. Montrer comment mettre à disposition le service {{site.data.keyword.cloudaccesstrailshort}}.
2. Montrer comment utiliser un service Cloud pour générer des événements d'activité automatiquement collectés par le service {{site.data.keyword.cloudaccesstrailshort}}. Les événements sont conformes à la norme CADF (Cloud Auditing Data Federation).
3. Montrer comment surveiller l'activité Cloud d'un service à l'aide des tableaux de bord {{site.data.keyword.cloudaccesstrailshort}} prédéfinis.

La figure suivante représente les différents composants et les actions impliqués lorsqu'une activité initiée par un utilisateur modifie l'état d'un service :

![Composants et actions impliqués lorsqu'une activité initiée par un utilisateur modifie l'état d'un service](images/AT_f1.png "Composants et actions impliqués lorsqu'une activité initiée par un utilisateur modifie l'état d'un service")



## Avant de commencer
{: #prereqs}

Créez un compte [{{site.data.keyword.Bluemix_notm}}](https://console.bluemix.net/registration/). Votre ID utilisateur doit être membre ou propriétaire d'un compte {{site.data.keyword.Bluemix_notm}} doté des droits d'accès de développeur sur l'espace où vous prévoyez d'utiliser le service {{site.data.keyword.cloudaccesstrailshort}}.


## Etape 1 : Mise à disposition d'Activity Tracker
{: #step1}

Vous devez mettre le service {{site.data.keyword.cloudaccesstrailshort}} à disposition dans la région et l'espace où le service Cloud que vous voulez surveiller est à disposition. Une fois le service {{site.data.keyword.cloudaccesstrailshort}} mis à disposition, les événements sont collectés automatiquement à partir des services Cloud sélectionnés mis à disposition dans cet espace. Pour la liste des service dont vous pouvez surveiller l'activité à l'aide d'{{site.data.keyword.cloudaccesstrailshort}}, voir [Services cloud pris en charge](/docs/services/cloud-activity-tracker/cloud_services.html#cloud_services).

**Remarque :** Ce tutoriel montre comment utiliser le service {{site.data.keyword.cloudaccesstrailshort}} pour surveiller l'interaction d'un utilisateur avec le service Cloud {{site.data.keyword.keymanagementservicelong_notm}}. Le service {{site.data.keyword.keymanagementserviceshort}} est disponible dans le sud des États-Unis. Par conséquent, vous devez mettre {{site.data.keyword.cloudaccesstrailshort}} à disposition dans la région du sud des Etats-Unis, dans l'espace où le service {{site.data.keyword.keymanagementserviceshort}} est disponible. Pour afficher les informations relatives à la région où un service est à disposition, voir [Services par région](/docs/services/services_region.html#services_region).

Pour mettre à disposition une instance du service {{site.data.keyword.cloudaccesstraillong_notm}} dans {{site.data.keyword.Bluemix_notm}} :

1. Connectez-vous à votre compte {{site.data.keyword.Bluemix_notm}}.

    Le tableau de bord {{site.data.keyword.Bluemix_notm}} se trouve à l'adresse suivante : [http://bluemix.net ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://bluemix.net){:new_window}.
    
	Après que vous vous êtes connecté avec votre ID utilisateur et votre mot de passe, l'interface utilisateur {{site.data.keyword.Bluemix_notm}} s'ouvre.

2. Cliquez sur **Catalogue**. La liste des services disponibles sur {{site.data.keyword.Bluemix_notm}} s'ouvre.

3. Sélectionnez la catégorie **Sécurité** pour filtrer la liste de services affichée.

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
		<td>Sélectionnez l'organisation dont vous prévoyez de surveiller l'activité.</td>
	  </tr>
	  <tr>
	    <td>Choisissez un espace :</td>
		<td>Sélectionnez l'espace de l'organisation sélectionnée dans lequel vous prévoyez de surveiller l'activité.</td>
	  </tr>
	</table>

6. Cliquez sur **Créer** pour mettre à disposition le service {{site.data.keyword.cloudaccesstrailshort}} dans l'espace {{site.data.keyword.Bluemix_notm}} auquel vous êtes connecté.
   

## Etape 2 :  Mise à disposition d'un service cloud 
{: #step2}
	
Pour mettre à disposition une instance du service {{site.data.keyword.keymanagementserviceshort}} dans {{site.data.keyword.Bluemix_notm}}, procédez comme suit :

1. Connectez-vous à votre compte {{site.data.keyword.Bluemix_notm}}.

    Le tableau de bord {{site.data.keyword.Bluemix_notm}} se trouve à l'adresse suivante : [http://bluemix.net ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://bluemix.net){:new_window}
	
	Après que vous vous êtes connecté avec votre ID utilisateur et votre mot de passe, l'interface utilisateur {{site.data.keyword.Bluemix_notm}} s'ouvre.

2. Cliquez sur **Catalogue**. La liste des services disponibles sur {{site.data.keyword.Bluemix_notm}} s'ouvre.

    Sélectionnez la catégorie **Sécurité** pour filtrer la liste de services affichée.

3. Sélectionnez la vignette **Key Protect**.

4. Configurez les informations qui définissent où le service va être mis à disposition. 

    Entrez les données indiquées dans le tableau suivant : 

    <table>
	  <caption>Tableau 2. Zones obligatoires pour mise à disposition du service {{site.data.keyword.keymanagementserviceshort}}</caption>
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
		<td>Sélectionnez l'organisation pour laquelle vous voulez mettre le service {{site.data.keyword.cloudaccesstrailshort}} à disposition.</td>
	  </tr>
	  <tr>
	    <td>Choisissez un espace :</td>
		<td>Sélectionnez l'espace dans lequel vous voulez mettre le service {{site.data.keyword.cloudaccesstrailshort}} à disposition.</td>
	  </tr>
	</table>

5. Cliquez sur **Créer** pour mettre à disposition le service {{site.data.keyword.keymanagementserviceshort}} dans l'espace {{site.data.keyword.Bluemix_notm}} auquel vous êtes connecté.


## Etape 3 : Génération d'un événement de suivi d'activité
{: # step3}

Dans cette étape, créez une clé de sécurité à l'aide du service {{site.data.keyword.keymanagementserviceshort}} afin de générer des données d'événement {{site.data.keyword.cloudaccesstrailshort}}. 

Pour générer un événement {{site.data.keyword.cloudaccesstrailshort}}, procédez comme suit :

1. Dans le tableau de bord {{site.data.keyword.Bluemix_notm}}, sélectionnez le service **Key Protect**. Le tableau de bord {{site.data.keyword.keymanagementserviceshort}} s'ouvre. Ensuite, sélectionnez l'onglet **Gérer**.

2. Cliquez sur **Add Key**. Une nouvelle fenêtre s'ouvre.

3. Sélectionnez **Generate key**, puis effectuez les opérations suivantes :

    * Entrez un nom pour la clé, par exemple, *MaPremièreClé*.

    * Choisissez un algorithme pour la clé.

    * Cliquez sur **Add key**. 
	
La création d'une clé a pour résultat la génération d'événements {{site.data.keyword.cloudaccesstrailshort}}.

## Etape 4 : Surveillance d'un événement de suivi d'activité
{: #step4}

Dans cette étape, vérifiez à l'aide de l'interface utilisateur {{site.data.keyword.Bluemix_notm}} des événements {{site.data.keyword.cloudaccesstrailshort}} sont générés.

Vérifiez comme suit qu'un événement a été créé :

1. Dans le tableau de bord {{site.data.keyword.Bluemix_notm}}, sélectionnez le service {{site.data.keyword.cloudaccesstrailshort}}. Le tableau de bord du service s'ouvre.

2. Configurez la vue de recherche des événements {{site.data.keyword.keymanagementserviceshort}} générés lorsque vous avez mis le service a disposition et ajouté une clé.

    * Sélectionnez **Space logs** pour la zone *Afficher les journaux*.
    * Sélectionnez **target.name** pour la zone *Zone de Recherche*.
    * Entrez **ibm-key-protect** dans la zone *Filtrer*.
	
    Les données affichées correspondent aux événements {{site.data.keyword.keymanagementserviceshort}} disponibles pour les dernières 24 heures. 
	
	![Vue des événements de l'interface utilisateur](images/bmx_ui_space_view.png "Vue des événements de l'interface utilisateur")


## Etapes suivantes
{: #next_steps}

Ensuite, utilisez le tableau de bord Kibana prédéfini d'{{site.data.keyword.cloudaccesstrailshort}} pour surveiller et analyser les journaux des événements. Pour lancer Kibana, voir [Accès au tableau de bord Kibana](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_kibana.html#launch_kibana). 

Dans Kibana, les journaux d'activité des espaces sont, par défaut, affichés à l'aide du tableau de bord **ActivityTracker_Space_Search_in_24h** :

![Vue Kibana des événements](images/kibana_space_view.png "Vue Kibana des événements")

Vous pouvez également utiliser l'interface de ligne de commande d'{{site.data.keyword.cloudaccesstrailshort}} pour gérer vos événements depuis la ligne de commande. Pour plus d'information, voir [Affichage d'informations sur les événements](/docs/services/cloud-activity-tracker/how-to/manage-events-cli/viewing_event_information.html#viewing_event_status).

                                                                                                                      

