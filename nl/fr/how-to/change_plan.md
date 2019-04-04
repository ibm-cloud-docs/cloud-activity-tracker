---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, change plan

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



# Changement de plan
{: #change_plan}

Vous pouvez changer de plan de service {{site.data.keyword.cloudaccesstraillong}} dans l'interface utilisateur {{site.data.keyword.cloud_notm}} ou en exécutant la commande `ibmcloud service update`. Vous pouvez mettre à niveau ou rétrograder votre plan à tout moment.
{:shortdesc}

## Changement de plan de service via l'interface utilisateur
{: #change_plan_ui}

Pour changer votre plan de service dans l'interface utilisateur {{site.data.keyword.cloud_notm}}, procédez comme suit :

1. Connectez-vous à {{site.data.keyword.cloud_notm}}, puis cliquez sur le service {{site.data.keyword.cloudaccesstraillong_notm}} dans le *Tableau de bord*. 
    
2. Sélectionnez l'onglet **Plan**.

    Les informations relatives à votre plan en cours s'affichent.
	
3. Sélectionnez un nouveau plan pour mettre à niveau votre plan ou le rétrograder. 

4. Cliquez sur **Sauvegarder**.



## Changement de plan de service via l'interface de ligne de commande
{: #change_plan_cli}

Pour modifier votre plan de service via l'interface de ligne de commande, procédez comme suit :

1. Connectez-vous à {{site.data.keyword.cloud_notm}}. 

    Exécutez la commande [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) pour vous connecter à {{site.data.keyword.cloud_notm}}, puis exécutez la commande [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) pour définir l'organisation et l'espace où mettre le service {{site.data.keyword.cloudaccesstrailshort}} à disposition.
	
2. Exécutez la commande `ibmcloud service list` pour identifier le plan en cours et obtenir le nom du service {{site.data.keyword.cloudaccesstrailshort}} depuis la liste des services qui est disponible dans l'espace. 

    La valeur de la zone **name** est celle que vous devez utiliser pour changer de plan. 

    Par exemple,
	
	```
	$ ibmcloud service list
    Appel de 'cf services'...

    Obtention des services dans l'organisation MyOrg / l'espace dev en tant que xxx@ibm.com...
    OK

    name                       service                  plan                 bound apps                               last operation
    Activity Tracker-zt          OK                     accessTrail             premium                                update succeeded
    ```
	{: screen}
    
3. Mettez à niveau votre plan ou rétrogradez-le. Exécutez la commande `ibmcloud service update`.
    
	```
	ibmcloud service update service_name [-p new_plan]
	```
	{: codeblock}
	
	où 
	
	* *service_name* est le nom de votre service. Vous pouvez exécuter la commande `ibmcloud service list` pour obtenir la valeur.
	* *new_plan* est le nom du plan.
	
	
	Le tableau suivant répertorie les différents plans et les valeurs prises en charge :
	
	<table>
	  <caption>Tableau 1. Liste des plans.</caption>
	  <tr>
	    <th>Plan</th>
	    <th>Nom</th>
	  </tr>
	  <tr>
	    <td>Lite</td>
	    <td>free</td>
	  </tr>
	  <tr>
	    <td>Premium</td>
	    <td>premium</td>
	  </tr>
	</table>
	
	Par exemple, pour rétrograder votre plan et passer au plan *Lite*, exécutez la commande suivante :
	
	```
	ibmcloud service update "Activity Tracker-zt" -p free
    Mise à jour de l'instance de service Activity Tracker-zt en tant que xxx@ibm.com...
    OK
	```
	{: screen}



