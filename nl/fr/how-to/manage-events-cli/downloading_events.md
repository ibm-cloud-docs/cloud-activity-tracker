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

# Téléchargement d'événements
{: #downloading_events}

Vous pouvez télécharger des événements dans un fichier local ou diriger des données vers un autre programme. Les événements sont téléchargés dans le contexte d'une session. Une session indique quels événements seront téléchargé. Si le téléchargement des événements est interrompu, la session active la reprise à partir du point d'interruption du téléchargement.Une fois le téléchargement terminé, vous
devez supprimer la session.
{:shortdesc}

Pour télécharger les événements disponibles d'un espace {{site.data.keyword.Bluemix_notm}} dans un fichier local, procédez comme suit :

## Etape 1 : Connexion à Bluemix
{: #prereq}

Avant de commencez, connectez-vous à une région, une organisation et un espace {{site.data.keyword.Bluemix_notm}} où le service {{site.data.keyword.cloudaccesstrailshort}} est à disposition. 

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

## Etape 2 : Identification des événements disponibles
{: #step2}

1. Utilisez la commande `cf at status` pour afficher les événements disponibles.

    Par exemple, pour afficher les événements disponibles pour les 2 dernières semaines, exécutez la commande suivante :

    ```
    $ bx cf at status
    ```
    {: codeblock}
    
    Par exemple, l'exécution de cette commande génère la sortie suivante :
    
    ```
    +------------+--------+-------+--------------------+------------+
    |    DATE    |  COUNT | SIZE  |       TYPES        | SEARCHABLE |
    +------------+--------+-------+--------------------+------------+
    | 2017-07-24 |    16  | 3020  | ActivityTracker    |   None     |
    +------------+--------+-------+--------------------+------------+
    | 2017-07-25 |   1224 | 76115 | ActivityTracker    |    All     |
    +------------+--------+-------+--------------------+------------+
    ```
    {: screen}

    **Remarque :** le service {{site.data.keyword.cloudaccesstrailshort}} est un service global qui utilise UTC (Coordinated Universal Time). Les jours sont définis
en tant que jours UTC. Pour obtenir les événements d'un jour spécifique en heure locale, vous devez télécharger plusieurs jours TUC.
	
	Pour plus d'informations, voir [cf at status](/docs/services/cloud-activity-tracker/cli/at_cli.html#status).


## Etape 3 : Création d'une session
{: #step3}

Une session est nécessaire pour définir la portée des données d'événement disponibles pour téléchargement et pour conserver le statut du téléchargement. 

Utilisez la commande [cf at session create](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_create) pour créer une session. Vous pouvez également spécifier une date de début et une date de fin lorsque vous créez une session. 

**Remarque :** Lorsque vous spécifiez une date de début et une date de fin, la session donne accès aux événements situés entre ces dates inclusives. 

Pour créer une session utilisée pour télécharger les événements de la date en cours, exécutez la commande suivante :

```
bx cf at session create 
```
{: codeblock}

La session renvoie les informations suivantes :

* La plage de dates à télécharger. La valeur par défaut est la date UTC en cours.
* Des informations indiquant si les événements disponibles de l'intégralité du compte doivent être inclus ou uniquement ceux de l'espace en cours. Par défaut, vous obtenez les événements de l'espace auquel vous êtes connecté.
* L'ID de session nécessaire pour télécharger des événements.
* L'ID de l'utilisateur qui crée la session.

Par exemple,

```
$ bx cf at session create 
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| username     | xxx@yyy.com                               |
| create-time  | 2017-07-25T10:29:28.541092735Z            |
| access-time  | 2017-07-25T10:29:28.541092735Z            |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
| id           | 32c657c5-31c0-4a3c-a139-b380871c737a      |
| space        | 66fe4565-abab-46c9-cdcd-qf4565342345      |
+--------------+-------------------------------------------+
```
{: screen}

**Conseil :** Pour afficher la liste des sessions actives, exécutez la commande [cf at session list](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_list).

Par exemple,

```
bx cf at session list
+--------------------------------------+--------------------------------------+---------------------+--------------------------------+--------------------------------+
| Id                                   | Space                                |Username             | Create-time                    | Access-time                    |
+--------------------------------------+--------------------------------------+---------------------+--------------------------------+--------------------------------+
| 32c657c5-31c0-4a3c-a139-b380871c737a | 66fe4565-abab-46c9-cdcd-qf4565342345 |xxx@yyy.com          | 2017-07-25T10:29:28.541092735Z | 2017-07-25T10:29:28.541092735Z |
+--------------------------------------+--------------------------------------+---------------------+--------------------------------+--------------------------------+
```
{: screen} 


## Etape 4 : Téléchargement d'événements dans un fichier
{: #step4}

Pour télécharger les événements spécifiés par les paramètres de session, exécutez la commande suivante :

```
bx cf at download -o Events_File_Name Session_ID
```
{: codeblock}

où

* Events_File_Name est le nom du fichier de sortie.
* Session_ID est l'identificateur global unique de la session. Cette valeur est obtenue à l'étape précédente. Utilisez cette valeur pour la zone **Id**.

Par exemple,

```
bx cf at download -o Events_File_Name.log 32c657c5-31c0-4a3c-a139-b380871c737a
 29.89 KiB / 12.19 KiB [================================] 245.14% 9.73 MiB/s 0s
Download completed successfully
```
{: screen}

L'indicateur de progression va de 0 à 100% à mesure du téléchargement des événements.

**Remarque :** 

* Le format des données téléchargées est compressé JSON. Par exemple, lorsque vous téléchargez des événements dans un système Linux, décompressez le fichier .gz et ouvrez-le pour voir les données au format JSON. 
* Le format JSON compressé est approprié pour l'ingestion par ElasticSearch ou Logstash. Par exemple, si -o n'est pas indiqué et que vous travaillez sur un système Linux, les données seront transmises en continu vers stdout, de sorte que vous pouvez les diriger directement dans votre propre pile élastique.
* Vous pouvez également traiter les données avec un programme pouvant analyser JSON. 

## Etape 4 : Suppression de la session

Une fois le téléchargement terminé, vous devez supprimer la session à l'aide de la commande [cf at session delete](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_delete). 

Exécutez la commande suivante pour supprimer une session :

```
bx cf at session delete Session_ID
```
{: codeblock}

où Session_ID est l'identificateur global unique de la session créée à l'étape précédente. Utilisez cette valeur pour la zone **Id**.

Par exemple,

```
bx cf at session delete 32c657c5-31c0-4a3c-a139-b380871c737a
+---------+------------------------+
| Name    | Value                  |
+---------+------------------------+
| message | Delete session success |
+---------+------------------------+
```
{: screen}




