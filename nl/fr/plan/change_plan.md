---

copyright:
  years: 2017
lastupdated: "2017-09-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# Changement de plan
{: #change_plan}

Votre pouvez changer de plan de service {{site.data.keyword.cloudaccesstraillong}} dans {{site.data.keyword.Bluemix_notm}} dans le tableau de bord du service ou en exécutant la commande `cf update-service`. Vous pouvez mettre à niveau ou rétrograder votre plan à tout moment.
{:shortdesc}

## Changement de plan de service via l'interface utilisateur
{: #change_plan_ui}

Pour changer de plan de service dans {{site.data.keyword.Bluemix_notm}} depuis le tableau de bord du service, procédez comme suit :

1. Connectez-vous à {{site.data.keyword.Bluemix_notm}}, puis cliquez sur le service {{site.data.keyword.cloudaccesstraillong_notm}} dans le tableau de bord {{site.data.keyword.Bluemix_notm}}. 
    
2. Sélectionnez l'onglet **Plan** dans l'interface utilisateur {{site.data.keyword.Bluemix_notm}}.

    Les informations relatives à votre plan en cours s'affichent.
	
3. Sélectionnez un nouveau plan pour mettre à niveau votre plan ou le rétrograder. 

4. Cliquez sur **Save**.



## Changement de plan de service via l'interface de ligne de commande
{: #change_plan_cli}

Pour changer de plan de service dans Bluemix via l'interface de ligne de commande, procédez comme suit :

1. Connectez-vous à un espace, une organisation ou une région {{site.data.keyword.Bluemix_notm}}. 

    ```
    cf login -a Endpoint
    ```
    {: codeblock}
	
	Où *Endpoint* est l'adresse URL de connexion à {{site.data.keyword.Bluemix_notm}}. Cette adresse URL varie selon les régions.
	
	<table>
	    <caption>Liste des noeuds finaux d'accès à {{site.data.keyword.Bluemix_notm}}</caption>
		<tr>
		  <th>Région</th>
		  <th>URL</th>
		</tr>
		<tr>
		  <td>Sud des Etats-Unis</td>
		  <td>api.ng.bluemix.net</td>
		</tr>
		<tr>
		  <td>Royaume-Uni</td>
		  <td>api.eu-gb.bluemix.net</td>
		</tr>
		<tr>
		  <td>Allemagne</td>
		  <td>api.eu-de.bluemix.net</td>
		</tr>
	</table>

    Suivez les instructions. Entrez vos données d'identification {{site.data.keyword.Bluemix_notm}} et sélectionnez une organisation et un espace. 

    Par exemple, pour vous connecter à la région du sud des Etats-Unis, exécutez la commande suivante :
	
	```
	cf login -a api.ng.bluemix.net
	```
	{: codeblock}
	
2. Exécutez la commande `cf services` pour vérifier votre plan en cours et pour obtenir le nom de service {{site.data.keyword.cloudaccesstrailshort}} dans la liste des services disponibles dans l'espace. 

    La valeur de la zone **name** est celle que vous devez utiliser pour changer de plan. 

    Par exemple,
	
	```
	$ cf services
    Getting services in org MyOrg / space dev as xxx@yyy.com...
    OK
    
    name                            service              plan          bound apps      last operation
    Activity Tracker-oj            activityTracker       premium                       create succeeded
    ```
	{: screen}
    
3. Mettez à niveau votre plan ou rétrogradez-le. Exécutez la commande `cf update-service`.
    
	```
	cf update-service service_name [-p new_plan]
	```
	{: codeblock}
	
	où 
	
	* *service_name* est le nom de votre service. Vous pouvez exécuter la commande `cf services` pour obtenir cette valeur.
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
	    <td>lite</td>
	  </tr>
	  <tr>
	    <td>Premium</td>
	    <td>premium</td>
	  </tr>
	</table>
	
	Par exemple, pour rétrograder votre plan et passer au plan *Lite*, exécutez la commande suivante :
	
	```
	cf update-service "Activity Tracker-oj" -p lite
    Updating service instance Activity Tracker-oj as xxx@yyy.com...
    OK
	```
	{: screen}

4. Vérifiez que le plan a été changé. Exécutez la commande `cf services`.

    ```
	cf services
    Getting services in org MyOrg / space dev as xxx@yyy.com...
    OK

    name                   service            plan      bound apps   last operation
    Activity Tracker-oj    activityTracker    lite                   update succeeded
	```
	{: screen}






