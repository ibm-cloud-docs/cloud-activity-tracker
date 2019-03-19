---

copyright:
  years: 2016, 2019
lastupdated: "2019-01-23"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# Téléchargement d'événements
{: #downloading_events}

Vous pouvez télécharger des événements dans un fichier local. Vous téléchargez les événements dans le cadre du contexte d'une session. Une session indique quels événements seront téléchargé. Une fois le téléchargement terminé, vous
devez supprimer la session.
{:shortdesc}

Pour télécharger des événements dans un fichier local, procédez comme suit :

## Etape 1 : Connexion à {{site.data.keyword.cloud_notm}}
{: #prereq}

Connectez-vous à {{site.data.keyword.cloud_notm}}. Effectuez les opérations suivantes :

1. Exécutez la commande [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) pour vous connecter à {{site.data.keyword.cloud_notm}}.
2. Exécutez la commande [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) pour définir l'organisation et l'espace où mettre le service {{site.data.keyword.cloudaccesstrailshort}} à disposition.

**Remarque :** définissez l'organisation et l'espace où {{site.data.keyword.cloudaccesstrailshort}} est mis à disposition.

## Etape 2 : Identification des événements disponibles
{: #step2}

Utilisez la commande `ibmcloud at status` pour afficher les informations relatives aux événements disponibles dans un domaine d'espace.

* Pour obtenir des informations sur les événements d'un domaine d'espace, exécutez la commande `ibmcloud at status`.
* Pour obtenir des informations sur les événements d'un domaine de compte, exécutez la commande `ibmcloud at status` avec l'option `-a`.

Pour plus d'information, voir [Affichage d'informations sur les événements](/docs/services/cloud-activity-tracker/how-to/viewing_event_information.html#viewing_event_status).
  


## Etape 3 : Création d'une session
{: #step3}

Une session est nécessaire pour définir la portée des données d'événement disponibles pour téléchargement et pour conserver le statut du téléchargement. 

Utilisez la commande `ibmcloud at session create` pour créer une session. Par défaut, une session inclut des données pour les deux dernières semaines.  Vous pouvez éventuellement spécifier une date de début et une date de fin lorsque vous créez une session afin d'indiquer une plage de temps, une heure spécifique de la journée et la portée des événements. 

**Remarque :** 

* Lorsque vous spécifiez une date de début et une date de fin, la session donne accès aux événements situés entre ces dates inclusives. 
* Vous ne pouvez pas télécharger plus de 2 semaines de données par session. Par conséquent, la plage de temps doit être inférieure à 2 semaines.
* Vous pouvez télécharger des événements pour un domaine d'espace ou pour le domaine de compte dans une région.

Pour créer une session utilisée pour télécharger les événements d'une date spécifique, exécutez la commande suivante :

```
ibmcloud at session create -s 2017-07-25 -e 2017-07-25
```
{: codeblock}

La session renvoie les informations suivantes :

* La plage de dates à télécharger.
* Des informations indiquant si les événements disponibles de l'intégralité du compte doivent être inclus ou uniquement ceux de l'espace en cours. Par défaut, vous obtenez les événements de l'espace auquel vous êtes connecté.
* L'ID de session nécessaire pour télécharger des événements.
* L'ID de l'utilisateur qui crée la session.

Par exemple,

```
$ ibmcloud at session create 
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

**Conseil :** Pour afficher la liste des sessions actives, exécutez la commande `ibmcloud at session list`.

Par exemple,

```
ibmcloud at session list
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
ibmcloud at download -o Events_File_Name Session_ID
```
{: codeblock}

où

* Events_File_Name est le nom du fichier de sortie.
* Session_ID est l'identificateur global unique de la session. Cette valeur est obtenue à l'étape précédente. Utilisez cette valeur pour la zone **Id**.

Par exemple,

```
ibmcloud at download -o Events_File_Name.log 32c657c5-31c0-4a3c-a139-b380871c737a
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

Une fois le téléchargement terminé, vous devez supprimer la session à l'aide de la commande `ibmcloud at session delete`. 

Exécutez la commande suivante pour supprimer une session :

```
ibmcloud at session delete Session_ID
```
{: codeblock}

où Session_ID est l'identificateur global unique de la session créée à l'étape précédente. Utilisez cette valeur pour la zone **Id**.

Par exemple,

```
ibmcloud at session delete 32c657c5-31c0-4a3c-a139-b380871c737a
+---------+------------------------+
| Name    | Value                  |
+---------+------------------------+
| message | Delete session success |
+---------+------------------------+
```
{: screen}




