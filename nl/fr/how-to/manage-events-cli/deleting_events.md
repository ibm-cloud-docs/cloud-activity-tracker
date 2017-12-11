---

copyright:
  years: 2016, 2017
lastupdated: "2017-09-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Suppression d'événements
{: #deleting_events}

Utilisez la commande *cf at delete* pour supprimer manuellement des événements stockés dans {{site.data.keyword.cloudaccesstrailshort}} pour un espace {{site.data.keyword.Bluemix}}.
{:shortdesc}

## Suppression d'événements
{: #viewing_events}

Utilisez la commande `cf at status` pour afficher la taille et le nombre d'événements et si ceux-ci sont disponibles pour analyse dans Kibana. Pour plus d'informations, voir [cf at status](/docs/services/cloud-activity-tracker/cli/at_cli.html#status).

1. Connectez-vous à un espace, une organisation ou une région {{site.data.keyword.Bluemix_notm}}. 

    ```
    bx login -a Endpoint
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
	</table>

    Suivez les instructions. 

    Par exemple, pour vous connecter à la région du sud des Etats-Unis, exécutez la commande suivante :
	
	```
	bx login -a api.ng.bluemix.net
	```
	{: codeblock}
	
	Définissez ensuite l'organisation et l'espace. Exécutez la commande suivante :

    ```
    bx target -o OrgName -s SpaceName
    ```
   {: codeblock}

    où

    * OrgName est le nom de l'organisation.
    * SpaceName est le nom de l'espace.

2. Exécutez la commande *cf at status*.

    ```
    $ bx cf at status -a -s YYYY-MM-DD -e YYYY-MM-DD 
    ```
    {: codeblock}
    
    où
    
    * *-a* est utilisé pour indiquer que la demande s'applique à tous les espaces du compte.
    * *-s* est utilisé pour définir la date de début en UTC (Universal Coordinated Time) : *AAAA-MM-JJ*.
    * *-e* est utilisé pour définir la date de fin en UTC (Universal Coordinated Time) : *AAAA-MM-JJ*.
    	
	Utilisez la commande `cf at status` avec les options **-s** pour définir la date de début et **-e** pour définir la date de fin. Par exemple :

    * `bx cf at status` fournit les informations relatives aux 2 dernières semaines.
    * `bx cf at status -s 2017-05-03` fournit les informations depuis le 3 mai 2017 jusqu'à la date en cours.
    * `bx cf at status -s 2017-05-03 -e 2017-05-08` fournit les informations situées entre le 3 et le 8 mai 2017. 
 
    Utilisez la commande `cf at status` avec l'option **-a** pour définir le domaine à prendre en compte.
	
    Par exemple, pour obtenir les informations relatives aux événements disponibles pour le 10 juin 2017, exécutez la commande suivante :
    
    ```
    $ bx cf at status -s 2017-06-10 -e 2017-06-10
    +------------+-------+------+------------+
    | Date       | Count | Size | Searchable |
    +------------+-------+------+------------+
    | 2017-07-10 | 1     | 2531 | All        |
    +------------+-------+------+------------+
    ```
    {: screen}
	














