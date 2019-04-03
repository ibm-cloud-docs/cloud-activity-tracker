---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, provision instance

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



# Mise à disposition d'Activity Tracker
{: #provision}

Vous pouvez mettre à disposition le service {{site.data.keyword.cloudaccesstraillong}} à partir de l'interface utilisateur {{site.data.keyword.cloud_notm}} ou de la ligne de commande.
{:shortdesc}


## Mise à disposition à partir de l'interface utilisateur
{: #provision_ui}

Pour mettre à disposition une instance du service {{site.data.keyword.cloudaccesstraillong_notm}} dans {{site.data.keyword.cloud_notm}} :

1. [Connectez-vous à votre compte {{site.data.keyword.cloud_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://cloud.ibm.com/login){:new_window}.
    
	Après que vous vous êtes connecté avec votre ID utilisateur et votre mot de passe, l'interface utilisateur {{site.data.keyword.cloud_notm}} s'ouvre.

2. Cliquez sur **Catalogue**. La liste des services disponibles sur {{site.data.keyword.cloud_notm}} s'ouvre.

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
		<td>Les valeurs admises sont : Sud des Etats-Unis, Royaume-Uni, Allemagne et Sydney.</td>
	  </tr>
	  <tr>
	    <td>Choisissez une organisation :</td>
		<td>Sélectionnez l'organisation dont vous prévoyez de surveiller l'activité.</td>
	  </tr>
	  <tr>
	    <td>Choisissez un espace :</td>
		<td>Sélectionnez un espace dans l'organisation sélectionnée dans lequel vous prévoyez de surveiller l'activité.</td>
	  </tr>
	</table>

6. Sélectionnez un plan de service. 

    Le plan **free** est sélectionné par défaut.

    Pour plus d'informations, voir [Plans de service](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-change_plan#change_plan).
	
7. Cliquez sur **Créer** pour mettre à disposition le service {{site.data.keyword.cloudaccesstrailshort}} dans l'espace {{site.data.keyword.cloud_notm}} auquel vous êtes connecté.
  
 

## Mise à disposition à partir de l'interface de ligne de commande
{: #provision_cli}

Procédez comme suit pour mettre à disposition une instance du service {{site.data.keyword.cloudaccesstrailshort}} dans {{site.data.keyword.cloud_notm}} via la ligne de commande :

1. [Prérequis] Installez l'interface de ligne de commande {{site.data.keyword.cloud_notm}}.

   Pour plus d'informations, voir [Installation de l'interface de ligne de commande {{site.data.keyword.cloud_notm}}.](/docs/cli?topic=cloud-cli-ibmcloud-cli#ibmcloud-cli)
   
   Si l'interface de ligne de commande est installée, passez à l'étape suivante.
    
2. Connectez-vous à {{site.data.keyword.cloud_notm}}. 

    Exécutez la commande [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) pour vous connecter à {{site.data.keyword.cloud_notm}}, puis exécutez la commande [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) pour définir l'organisation et l'espace où mettre le service {{site.data.keyword.cloudaccesstrailshort}} à disposition.
	
3. Exécutez la commande `ibmcloud service create` pour mettre à disposition une instance.

    ```
	  ibmcloud service create service_name service_plan service_instance_name
    ```
	  {: codeblock}
	
	  Où
	
	  * service_name est le nom du service, en l'occurrence **accessTrail**.

	  * service_plan est le nom du plan de service. Pour la liste des plans, voir [Plans de service](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-change_plan#change_plan).

	  * service_instance_name est le nom que vous souhaitez utiliser pour la nouvelle instance de service que vous créez.

	  Par exemple, pour créer une instance du service {{site.data.keyword.cloudaccesstrailshort}} avec le plan standard, exécutez la commande suivante :
	
	  ```
	  ibmcloud service create accessTrail free my_activitytracker_svc
	  ```
	  {: codeblock}
	
4. Vérifiez que le service a été créé. Exécutez la commande suivante :

  ```	
	ibmcloud service list
	```
	{: codeblock}
	
	Le résultat de l'exécution de la commande se présente comme suit :
	
	```
    Getting services in org MyOrg / space MySpace as xxx@yyy.com...
    OK
    
    name                           service                  plan                   bound apps              last operation
    my_activitytracker_svc         accessTrail             free                                            create succeeded
	```
	{: screen}

	




