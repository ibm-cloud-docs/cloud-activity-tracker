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



# Gestion des événements à l'aide de l'interface de ligne de commande d'Activity Tracker
{: #tutorial2}

Utilisez ce tutoriel pour apprendre à utiliser l'interface de ligne de commande d'{{site.data.keyword.cloudaccesstrailshort}} pour gérer des événements via la ligne de commande. Apprenez à obtenir des informations sur des événements stockés, à télécharger des événements stockés dans {{site.data.keyword.IBM_notm}} Cloud ou à supprimer des événements.
{:shortdesc}

Effectuez les opérations suivantes :

1. [Mise à disposition d'{{site.data.keyword.keymanagementservicelong_notm}} et génération d'événements](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#tutorial2_step1)
2. [Obtention d'informations sur des événements stockés (ibmcloud at status)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#tutorial2_step2)
2. [Spécification des journaux à télécharger par la création d'une session (ibmcloud at session create)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#tutorial2_step3)
3. [Obtention de données de journal réelles (ibmcloud at download)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#tutorial2_step4)
4. [Suppression de la session une fois le téléchargement terminé (ibmcloud at session delete)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#tutorial2_step5)
5. [Suppression manuelle des journaux non nécessaires (ibmcloud at delete)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#tutorial2_step6)


## Hypothèses
{: #tutorial2_assumptions}

1. Vous disposez d'un ID utilisateur {{site.data.keyword.cloud_notm}} doté des droits d'accès de développeur vous permettant de travailler dans un espace d'un compte {{site.data.keyword.cloud_notm}} où le service {{site.data.keyword.cloudaccesstrailshort}} est à disposition. 

    Pour plus d'informations sur la mise à disposition du service {{site.data.keyword.cloudaccesstrailshort}}, voir [Mise à disposition du service {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/how-to/provision.html#provision).

2. Vous avez mis à disposition une instance du service {{site.data.keyword.cloudaccesstrailshort}} avec un plan premium.

    **Remarque :** L'interface de ligne de commande d'{{site.data.keyword.cloudaccesstrailshort}} n'est pas disponible avec le plan Lite.

3. Vous avez installé l'interface de ligne de commande d'{{site.data.keyword.cloudaccesstrailshort}} sur votre système local. Ce plug-in est nécessaire pour que vous puissiez utiliser l'interface de ligne de commande d'{{site.data.keyword.cloudaccesstrailshort}} afin de gérer des événements via la ligne de commande. 

    Pour plus d'informations sur l'installation de l'interface de ligne de commande d'{{site.data.keyword.cloudaccesstrailshort}}, voir [Configuration de l'interface de ligne de commande d'{{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/how-to/config_cli.html#config_cli).

4. Vous vous êtes connecté à {{site.data.keyword.cloud_notm}} via la ligne de commande. Pour ce tutoriel, exécutez les commandes suivantes à partir d'un terminal : 

    `ibmcloud login -a api.ng.bluemix.net` pour se connecter à la région us-south. Pour plus d'informations, voir [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login).
    
    `ibmcloud target -o OrgName -s SpaceName` pour définir l'organisation cible et l'espace où le service {{site.data.keyword.cloudaccesstrailshort}} est mis à disposition. Pour plus d'informations, voir [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target).


## Etape 1 : Mise à disposition du service IBM Key Protect et génération d'événements 
{: #tutorial2_step1}
	
Procédez comme suit pour mettre à disposition le service {{site.data.keyword.keymanagementserviceshort}} dans {{site.data.keyword.cloud_notm}} et générer des événements :

1. Mettez à disposition une instance du service {{site.data.keyword.keymanagementserviceshort}} dans la région Sud des Etats-Unis. Pour plus d'informations, voir [Mise à disposition à partir de la console IBM Cloud](/docs/services/key-protect/provision.html#provision).

2. Définissez les droits {{site.data.keyword.cloud_notm}} pour l'utilisateur à l'aide duquel vous prévoyez de gérer des clés. 

    * Un utilisateur a besoin d'une règle IAM avec un rôle de service défini sur *Responsable* ou *Auteur* pour pouvoir créer des clés.
	* Un utilisateur a besoin d'une règle IAM avec un rôle de service défini sur *Responsable* pour pouvoir supprimer des clés.
	* Un utilisateur a besoin d'une règle IAM avec un rôle de service défini sur *Lecteur* pour pouvoir afficher des clés. 

3. Créez une clé de sécurité à l'aide du service {{site.data.keyword.keymanagementserviceshort}} afin de générer des données d'événement {{site.data.keyword.cloudaccesstrailshort}}. Pour plus d'informations, voir [Création de clés](/docs/services/key-protect/create-standard-keys.html#create-standard-keys).

La création d'une clé a pour résultat la génération d'événements {{site.data.keyword.cloudaccesstrailshort}}.

## Etape 2 : Obtention d'informations sur des événements stockés
{: #tutorial2_step2}

Les événements {{site.data.keyword.keymanagementserviceshort}} sont disponibles dans le domaine de compte {{site.data.keyword.cloudaccesstrailshort}}.

Dans ce tutoriel, des événements {{site.data.keyword.keymanagementserviceshort}} sont disponibles dans le domaine de compte Sud des Etats-Unis, qui est la région où vous avez à disposition le service {{site.data.keyword.keymanagementserviceshort}}. 

Exécutez la commande suivante pour obtenir des informations sur les événements collectés à une date spécifique :

```
ibmcloud at status -s startDate -e endDate -a
```
{: codeblock}

où 

* `-s` est utilisé pour définir le jour de début. 
* `startDate` représente la date de début. Le format est *AAAA-MM-JJ*.
* `-e` est utilisé pour définir la date de fin.
* `endDate` représente la date de fin. Le format est *AAAA-MM-JJ*.
* `-a` est utilisé pour indiquer d'inclure des événements dans le domaine de compte.

Par exemple :

```
ibmcloud at status -s 2017-07-25 -e 2017-07-25 -a
+------------+-------+-------+------------+
| Date       | Count | Size  | Searchable |
+------------+-------+-------+------------+
| 2017-07-25 | 12    | 34994 | All        |
+------------+-------+-------+------------+
```
{: screen}

Cette commande compte les événements du 25 juin 2017.  {{site.data.keyword.cloudaccesstrailshort}} étant un service global, les jours sont exprimés en temps universel. Pour obtenir un jour complet en heure locale, vous devrez probablement télécharger plusieurs jours TUC.




## Etape 3 : Spécification des événements à télécharger
{: #tutorial2_step3}

Avant de télécharger des événements, créez une session. La session indique quels événements seront téléchargés.


Utilisez la commande suivante pour créer une session :

```
ibmcloud at session create -s startDate -e endDate -a
```
{: codeblock}

où 

* `-s` est utilisé pour définir le jour de début. 
* `startDate` représente la date de début. Le format est *AAAA-MM-JJ*.
* `-e` est utilisé pour définir la date de fin.
* `endDate` représente la date de fin. Le format est *AAAA-MM-JJ*.
* `-a` est utilisé pour indiquer d'inclure des événements dans le domaine de compte.

Par exemple :

```
ibmcloud at session create -s 2017-07-25 -e 2017-07-25 -a
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| id           | 21b19aeb-3d32-4c60-b912-517609c62db2      |
| space        | 667fb895-b5f5-46c9-9f0e-cf4587341095      |
| username     | xxx@yyy.com                               |
| create-time  | 2017-07-25T18:33:22.678350874Z            |
| access-time  | 2017-07-25T18:33:22.678350874Z            |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
+--------------+-------------------------------------------+
```
{: screen}

où 

* `-s` est utilisé pour définir le jour de début.
* `-e` est utilisé pour définir la date de fin.
* `-a` est utilisé pour indiquer d'inclure des événements dans le domaine de compte.

Une date de début et une date de fin sont associées à une session. La commande de téléchargement inclura les événements qui se sont produits entre ces deux dates inclusives.

La partie importante du résultat de la commande est l'`Id` de session. Il est référencé dans la commande de téléchargement.

Pour obtenir des informations sur les sessions existantes, entrez `ibmcloud at session list`.

Pour en savoir plus sur les sessions et sur la commande `ibmcloud at session create`, voir le [Guide de référence de l'interface de ligne de commande](/docs/services/cloud-activity-tracker/reference/at_cli_cloud.html#session_create).

Utilisez `ibmcloud at session help create` pour obtenir de l'aide depuis la ligne de commande.

## Etape 4 : Téléchargement des événements identifiés pour la portée définie pour la session
{: #tutorial2_step4}

Pour télécharger les événements spécifiés par les paramètres de session, exécutez la commande suivante :

```
ibmcloud at events download -o outputFile sessionID
```
{: codeblock}

* Le paramètre `-o` indique un fichier de sortie.
* `outputFile` est le nom du fichier local.
* L'`ID session` est spécifié en dernier. L'ID de session est indiqué dans le résultat de la commande `ibmcloud at session create`.

Le format des données téléchargées est compressé JSON. 

Par exemple :

```
$ ibmcloud at events download -o events.log 21b19aeb-3d32-4c60-b912-517609c62db2
 6.70 KiB / 3.06 KiB [================================================================================================================================================================] 219.03% 8.60 MiB/s 0s
Download Successful
```
{: screen} 

L'indicateur de progression va de 0 à 100% à mesure du téléchargement des événements.

Pour en savoir plus sur la commande `ibmcloud at download`, voir le [Guide de référence de l'interface de ligne de commande](/docs/services/cloud-activity-tracker/reference/at_cli_cloud.html#download).

Utilisez `ibmcloud at help download` pour obtenir de l'aide depuis la ligne de commande.

## Etape 5 : Suppression de la session
{: #tutorial2_step5}

Une fois le téléchargement terminé, supprimez la session. Exécutez la commande suivante :

```
ibmcloud at session delete sessionID
```
{: codeblock}

où 

* `sessionID` est l'ID de la session que vous souhaitez supprimer.

Le nombre de sessions est limité. Une session n'es pas automatiquement supprimée. Vous devez supprimer manuellement les sessions devenues inutiles. 

Par exemple : 

```
$ ibmcloud at session delete 21b19aeb-3d32-4c60-b912-517609c62db2
+---------+------------------------+
| name    | value                  |
+---------+------------------------+
| message | Delete session success |
+---------+------------------------+
```
{: screen}

Pour en savoir plus sur la commande `ibmcloud at session delete`, voir le [Guide de référence de l'interface de ligne de commande](/docs/services/cloud-activity-tracker/reference/at_cli_cloud.html#session_delete).

Utilisez `ibmcloud at session help delete` pour obtenir de l'aide depuis la ligne de commande.

## Etape 6 : Suppression automatique d'événements d'Activity Tracker
{: #tutorial2_step6}

Vous contrôlez la durée de conservation de vos événements dans {{site.data.keyword.cloudaccesstrailshort}}. Vous pouvez supprimer les événements manuellement ou automatiser leur suppression.

Pour supprimer manuellement des événements dans un espace, exécutez la commande `ibmcloud at delete`. Par exemple,

```
$ ibmcloud at delete -s 2017-07-25 -e 2017-07-25
Deleted successfully
"6 logs were deleted,freeing 13737 bytes."
```
{: screen}

Pour en savoir plus sur la commande `ibmcloud at delete`, voir le [Guide de référence de l'interface de ligne de commande](/docs/services/cloud-activity-tracker/reference/at_cli_cloud.html#delete).

Utilisez `ibmcloud at help delete` pour obtenir de l'aide depuis la ligne de commande.

**Remarque :** Pour supprimer automatiquement les événements, vous pouvez définir une règle de conservation à l'aide de la commande d'interface de ligne de commande `ibmcloud at option`. Pour plus d'information, voir le [Guide de référence de l'interface de ligne de commande](/docs/services/cloud-activity-tracker/reference/at_cli_cloud.html#option)


