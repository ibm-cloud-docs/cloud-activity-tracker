---

copyright:
  years: 2016, 2017

lastupdated: "2017-09-07"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# Gestion des événements à l'aide de l'interface de ligne de commande d'Activity Tracker
{: #tutorial2}

Utilisez ce tutoriel pour apprendre à utiliser l'interface de ligne de commande d'{{site.data.keyword.cloudaccesstrailshort}} pour gérer des événements via la ligne de commande. Apprenez à obtenir des informations sur des événements stockés, à télécharger des événements stockés dans {{site.data.keyword.IBM_notm}} Cloud ou à supprimer des événements.
{:shortdesc}

Effectuez les opérations suivantes :

1. [Mise à disposition du service {{site.data.keyword.IBM_notm}} Key Protect et génération d'événements](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step1)
2. [Obtention d'informations sur des événements stockés (cf at status)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step2)
2. [Spécification des journaux à télécharger par la création d'une session (cf at session create)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step3)
3. [Obtention de données de journal réelles (cf at download)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step4)
4. [Suppression de la session une fois le téléchargement terminé (cf at session delete)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step5)
5. [Suppression manuelle des journaux non nécessaires (cf at delete)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step6)


## Hypothèses
{: #assumptions}

1. Vous disposez d'un ID utilisateur {{site.data.keyword.Bluemix_notm}} doté des droits d'accès de développeur vous permettant de travailler dans un espace d'un compte {{site.data.keyword.Bluemix_notm}} où le service {{site.data.keyword.IBM_notm}} Cloud {{site.data.keyword.cloudaccesstrailshort}} est à disposition. 

    Pour plus d'informations sur la mise à disposition du service {{site.data.keyword.cloudaccesstrailshort}}, voir [Mise à disposition du service {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/how-to/provision.html#provision).

2. Vous avez installé le plug-in CF d'{{site.data.keyword.cloudaccesstrailshort}} sur votre système local. Ce plug-in est nécessaire pour que vous puissiez utiliser l'interface de ligne de commande d'{{site.data.keyword.cloudaccesstrailshort}} afin de gérer des événements via la ligne de commande. 

    Pour plus d'informations sur l'installation du plug-in CF d'{{site.data.keyword.cloudaccesstrailshort}}, voir [Configuration de l'interface de ligne de commande d'{{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#config_at_cli).

3. Vous vous êtes connecté à {{site.data.keyword.Bluemix_notm}} via la ligne de commande à l'aide de la commande suivante :

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

    Par exemple, pour vous connecter à la région du sud des Etats-Unis, exécutez la commande suivante :
	
	```
	bx cf login -a api.ng.bluemix.net
	```
	{: codeblock}

	**Remarque :** Vous devez vous connecter à la région, à l'organisation et à l'espace de {{site.data.keyword.Bluemix_notm}} où le service {{site.data.keyword.cloudaccesstrailshort}} est à disposition pour pouvoir exécuter des commandes {{site.data.keyword.cloudaccesstrailshort}} et gérer vos événements via la ligne de commande.
	
	Définissez ensuite l'organisation et l'espace. Exécutez la commande suivante :

    ```
    bx target -o OrgName -s SpaceName
    ```
    {: codeblock}

    où

    * OrgName est le nom de l'organisation.
    * SpaceName est le nom de l'espace.


## Etape 1 : Mise à disposition du service IBM Key Protect et génération d'événements 
{: #step1}
	
1. Pour mettre à disposition une instance du service {{site.data.keyword.keymanagementserviceshort}} dans {{site.data.keyword.Bluemix_notm}} :

    1. Connectez-vous à votre compte {{site.data.keyword.Bluemix_notm}}.

        Le tableau de bord {{site.data.keyword.Bluemix_notm}} se trouve à l'adresse suivante : [http://bluemix.net](http://bluemix.net)

        Après que vous vous êtes connecté avec votre ID utilisateur et votre mot de passe, l'interface utilisateur {{site.data.keyword.Bluemix_notm}} s'ouvre.

    2. Cliquez sur **Catalogue**. La liste des services disponibles sur {{site.data.keyword.Bluemix_notm}} s'ouvre.

        Sélectionnez la catégorie **Sécurité** pour filtrer la liste de services affichée.

    3. Sélectionnez la vignette **Key Protect**.

    4. Cliquez sur **Créer** pour mettre à disposition le service {{site.data.keyword.keymanagementserviceshort}} dans l'espace {{site.data.keyword.Bluemix_notm}} auquel vous êtes connecté.

2. Pour générer un événement {{site.data.keyword.cloudaccesstrailshort}}, procédez comme suit :

    1. Dans le tableau de bord {{site.data.keyword.Bluemix_notm}}, sélectionnez le service {{site.data.keyword.keymanagementserviceshort}}. Le tableau de bord {{site.data.keyword.keymanagementserviceshort}} s'ouvre. Ensuite, sélectionnez l'onglet **Gérer**.

    2. Cliquez sur **Add Key**. Une nouvelle fenêtre s'ouvre.

        Fenêtre d'ajout de clés de ![{{site.data.keyword.keymanagementserviceshort}}](images/KP_f2.gif)

    3. Sélectionnez **Generate key**, puis effectuez les opérations suivantes :

        * Entrez un nom pour la clé, par exemple, *MaPremièreClé*.

        * Choisissez un algorithme pour la clé.

        * Cliquez sur **Add key**. 

3. Vérifiez comme suit qu'un événement a été créé :

    1. Dans le tableau de bord {{site.data.keyword.Bluemix_notm}}, sélectionnez le service {{site.data.keyword.cloudaccesstrailshort}}. Le tableau de bord du service s'ouvre.

    2. Configurez la vue de recherche des événements {{site.data.keyword.keymanagementserviceshort}} générés lorsque vous avez mis le service a disposition et ajouté une clé.

        * Sélectionnez **Space logs** pour la zone *Afficher les journaux*.
	    * Sélectionnez **target.name** pour la zone *Zone de Recherche*.
	    * Entrez **ibm-key-protect** dans la zone *Filtrer*.
	
	    Les données affichées correspondent aux événement {{site.data.keyword.keymanagementserviceshort}} disponibles pour les dernières 24 heure. 

	    Onglet Gérer d'![{{site.data.keyword.cloudaccesstrailshort}}](images/KP_f3.gif)

## Etape 2 : Obtention d'informations sur des événements stockés
{: #step2}

Vérifiez quels événements sont disponibles pour téléchargement. Par exemple, si vous mettez à disposition et ajoutez une clé à la date du jour, exécutez la commande suivante pour obtenir des informations sur les événements collectés aujourd'hui :

```
bx cf at status -s 2017-07-25 -e 2017-07-25
+------------+-------+-------+------------+
| Date       | Count | Size  | Searchable |
+------------+-------+-------+------------+
| 2017-07-25 | 12    | 34994 | All        |
+------------+-------+-------+------------+
```
{: screen}

Cette commande compte les événements du 25 juin 2017. {{site.data.keyword.cloudaccesstrailshort}} étant un service global, les jours sont exprimés en temps universel. Pour obtenir un jour complet en heure locale, vous devrez probablement télécharger plusieurs jours TUC.

Pour afficher les informations relatives à plusieurs jours, utilisez `-s` pour définir la date de début et `-e` pour définir la date de fin. 

Pour en savoir plus sur la commande `cf at status`, voir le [Guide de référence de l'interface de ligne de commande](/docs/services/cloud-activity-tracker/cli/at_cli.html#status).

Utilisez `bx cf at help status` pour obtenir de l'aide depuis la ligne de commande.

## Etape 3 : Spécification des événements à télécharger
{: #step3}

Avant de télécharger de événements, créez une session :

* La session indique quels événements seront téléchargés.
* Si le téléchargement des événements est interrompu, la session active la reprise à partir du point d'interruption du téléchargement.

Pour créer une session, exécutez la commande suivante :

```
bx cf at session create -s 2017-07-25 -e 2017-07-25
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

Une date de début et une date de fin sont associées à une session. La commande de téléchargement inclura les événements qui se sont produits entre ces deux dates inclusives. La plage de dates par défaut est la date du jour uniquement. 

La partie importante du résultat de la commande est l'`Id` de session. Il est référencé dans la commande de téléchargement.

Pour obtenir des informations sur les sessions existantes, entrez `cf at session list`.

Pour en savoir plus sur les sessions et sur la commande `cf at session create`, voir le [Guide de référence de l'interface de ligne de commande](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_create).

Utilisez `cf at session help create` pour obtenir de l'aide depuis la ligne de commande.

## Etape 4 : Téléchargement des événements identifiés pour la portée définie pour la session
{: #step4}

Pour télécharger les événements spécifiés par les paramètres de session, exécutez la commande suivante :

```
$ bx cf at events download -o events.log 21b19aeb-3d32-4c60-b912-517609c62db2
 6.70 KiB / 3.06 KiB [================================================================================================================================================================] 219.03% 8.60 MiB/s 0s
Download Successful
```

* Le paramètre `-o` indique un fichier de sortie.
* L'ID de session est spécifié en dernier. L'ID de session ID est indiqué dans le résultat de la commande `cf at session create`.
* L'indicateur de progression va de 0 à 100% à mesure du téléchargement des événements.

Le format des données téléchargées est compressé JSON. 

Pour en savoir plus sur la commande `cf at download`, voir le [Guide de référence de l'interface de ligne de commande](/docs/services/cloud-activity-tracker/cli/at_cli.html#download).

Utilisez `bx cf at help download` pour obtenir de l'aide depuis la ligne de commande.

## Etape 5 : Suppression de la session
{: #step5}

Une fois le téléchargement terminé, supprimez la session. 

Le nombre de sessions est limité. Une session n'es pas automatiquement supprimée. Vous devez supprimer manuellement les sessions devenues inutiles. 

```
$ bx cf at session delete 21b19aeb-3d32-4c60-b912-517609c62db2
+---------+------------------------+
| name    | value                  |
+---------+------------------------+
| message | Delete session success |
+---------+------------------------+
```

Pour en savoir plus sur la commande `cf at session delete`, voir le [Guide de référence de l'interface de ligne de commande](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_delete).

Utilisez `bx cf at session help delete` pour obtenir de l'aide depuis la ligne de commande.

## Etape 6 : Suppression manuelle d'événements d'Activity Tracker
{: #step6}

Vous contrôlez la durée de conservation de vos événements dans {{site.data.keyword.cloudaccesstrailshort}}. Vous pouvez supprimer les événements manuellement ou automatiser leur suppression.

Pour supprimer des événements manuellement, exécutez la commande `cf at delete`. Par exemple,

```
$ bx cf at delete -s 2017-07-25 -e 2017-07-25
Deleted successfully
"6 logs were deleted,freeing 13737 bytes."
```

Pour en savoir plus sur la commande `cf at delete`, voir le [Guide de référence de l'interface de ligne de commande](/docs/services/cloud-activity-tracker/cli/at_cli.html#delete).

Utilisez `bx cf at help delete` pour obtenir de l'aide depuis la ligne de commande.

**Remarque :** Pour supprimer automatiquement les événements, vous pouvez définir une règle de conservation à l'aide de la commande d'interface de ligne de commande `cf at option`. Pour plus d'information, voir le [Guide de référence de l'interface de ligne de commande](/docs/services/cloud-activity-tracker/cli/at_cli.html#option)


