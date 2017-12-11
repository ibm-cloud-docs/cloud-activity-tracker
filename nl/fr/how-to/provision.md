---

copyright:
  years: 2016, 2017

lastupdated: "2017-09-17"

---


{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# Mise à disposition du service Activity Tracker
{: #provision}

Vous pouvez mettre à disposition le service {{site.data.keyword.cloudaccesstraillong}} à partir de l'interface utilisateur {{site.data.keyword.Bluemix}} ou de la ligne de commande.
{:shortdesc}


## Mise à disposition à partir de l'interface utilisateur
{: #ui}

Pour mettre à disposition une instance du service {{site.data.keyword.cloudaccesstraillong_notm}} dans {{site.data.keyword.Bluemix_notm}} :

1. Connectez-vous à votre compte {{site.data.keyword.Bluemix_notm}}.

    Le tableau de bord {{site.data.keyword.Bluemix_notm}} se trouve à l'adresse suivante : [http://bluemix.net ![External link icon](../../../icons/launch-glyph.svg "External link icon")](http://bluemix.net){:new_window}.
    
	Après que vous vous êtes connecté avec votre ID utilisateur et votre mot de passe, l'interface utilisateur {{site.data.keyword.Bluemix_notm}} s'ouvre.

2. Cliquez sur **Catalogue**. La liste des services disponibles sur {{site.data.keyword.Bluemix_notm}} s'ouvre.

3. Sélectionnez la catégorie **Sécurité** pour filtrer la liste de services affichée.

    Le service est également disponible sous la catégorie **DevOps**.

4. Cliquez sur la vignette **Activity Tracker**.

5. Configurez les informations qui définissent où le service va être mis à disposition. 

    Entrez les données indiquées dans le tableau suivant : 

    <table>
	  <caption>Tableau 1. Zones obligatoires pour mise à disposition du service {{site.data.keyword.cloudaccesstrailshort}}</caption>
	  <tr>
	    <th>Zone</th>
		<th>Valeur</th>
	  </tr>
	  <tr>
	    <td>Sélectionnez une région dans laquelle effectuer le déploiement :</td>
		<td>Les valeurs admises sont : Sud des Etats-Unis, Royaume-Uni et Allemagne</td>
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

6. Sélectionnez un plan de service. 

    Le plan **free** est sélectionné par défaut.

    Pour plus d'information, voir [Plans de service](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#plans).
	
7. Cliquez sur **Créer** pour mettre à disposition le service {{site.data.keyword.cloudaccesstrailshort}} dans l'espace {{site.data.keyword.Bluemix_notm}} auquel vous êtes connecté.
  
 

## Mise à disposition à partir de l'interface de ligne de commande
{: #cli}

Procédez comme suit pour mettre à disposition une instance du service {{site.data.keyword.cloudaccesstraillong_notm}} dans {{site.data.keyword.Bluemix_notm}} via la ligne de commande :

1. Installez l'interface de ligne de commande Cloud Foundry (CF). Si l'interface de ligne de commande CF est installée, passez à l'étape suivante.

   Pour plus d'informations, voir [Installation de l'interface de ligne de commande cf ![External link icon](../../../icons/launch-glyph.svg "External link icon")](http://docs.cloudfoundry.org/cf-cli/install-go-cli.html){: new_window}. 
    
2. Connectez-vous à un espace, une organisation ou une région {{site.data.keyword.Bluemix_notm}}. 

    Par exemple, pour vous connecter à la région du sud des États-Unis, exécutez la commande suivante :

    ```
    cf login -a https://api.ng.bluemix.net
    ```
    {: codeblock}

    Suivez les instructions. Entrez vos données d'identification {{site.data.keyword.Bluemix_notm}} et sélectionnez une organisation et un espace.
	
3. Exécutez la commande `cf create-service` pour mettre à disposition une instance.

    ```
	cf create-service service_name service_plan service_instance_name
	```
	{: codeblock}
	
	Où
	
	* service_name est le nom du service, à savoir **activityTracker**.
	* service_plan est le nom du plan de service. Pour la liste des plans, voir [Service plans](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#plans).
	* service_instance_name est le nom que vous souhaitez utiliser pour la nouvelle instance de service que vous créez.
	
	Pour plus d'informations sur la commande cf, voir [cf create-service](/docs/cli/reference/cfcommands/index.html#cf_create-service).

	Par exemple, pour créer une instance de service {{site.data.keyword.cloudaccesstrailshort}} avec le plan Lite, exécutez la commande suivante :
	
	```
	cf create-service activityTracker free my_activity_tracker_svc
	```
	{: codeblock}
	
4. Vérifiez que le service a bel et bien été créé. Exécutez la commande suivante :

    ```	
	cf services
	```
	{: codeblock}
	
	Le résultat de l'exécution de la commande se présente comme suit :
	
	```
    Getting services in org MyOrg / space MySpace as xxx@yyy.com...
    OK
    
    name                           service                  plan                   bound apps              last operation
    my_activity_tracker_svc        activityTracker          free                                           create succeeded
	```
	{: screen}

	



