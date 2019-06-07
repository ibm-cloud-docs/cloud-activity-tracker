---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, CLI

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
{:deprecated: .deprecated}


# Interface de ligne de commande d'Activity Tracker d'IBM Cloud
{: #at_cli_cloud}

Vous pouvez utiliser l'interface de ligne de commande {{site.data.keyword.cloudaccesstraillong}} pour gérer des événements {{site.data.keyword.cloudaccesstrailshort}}.
{: shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} est obsolète. A compter du 9 mai 2019, vous ne pourrez plus mettre à disposition de nouvelles instances {{site.data.keyword.cloudaccesstrailshort}}. Les instances de plan existantes sont prises en charge jusqu'au 30 septembre 2019. Pour continuer à surveiller l'activité de votre compte {{site.data.keyword.cloud_notm}}, mettez à disposition une instance du [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}


**Prérequis**
* Avant d'exécuter les commandes, connectez-vous à {{site.data.keyword.Bluemix}} avec la commande `ibmcloud login` pour générer un jeton d'accès et authentifier votre session.
* Pour gérer des événements à l'aide de l'interface de ligne de commande, vous devez disposer d'un plan payant.

Le plug-in de l'interface de ligne de commande d'{{site.data.keyword.cloudaccesstraillong}} prend en charge les plateformes Linux, Mac et Windows.

<table>
  <caption>Commandes de gestion d'{{site.data.keyword.cloudaccesstrailshort}}</caption>
  <tr>
    <th>Commande</th>
    <th>Quant l'utiliser</th>
  </tr>
  <tr>
    <td>[ibmcloud at](#base)</td>
    <td>Utilisez cette commande pour obtenir des informations sur l'interface de ligne de commande, comme la version ou la liste des commandes.</td>
  </tr>
  <tr>
    <td>[ibmcloud at delete](#delete)</td>
    <td>Utilisez cette commande pour supprimer des événements {{site.data.keyword.cloudaccesstrailshort}}.</td>
  </tr>
  <tr>
    <td>[ibmcloud at download](#download)</td>
    <td>Utilisez cette commande pour télécharger des journaux {{site.data.keyword.cloudaccesstrailshort}} dans un fichier local. </td>
  </tr>
  <tr>
    <td>[ibmcloud at help](#help)</td>
    <td>Utilisez cette commande pour obtenir de l'aide sur l'utilisation de l'interface de ligne de commande et une liste de toutes les commandes.</td>
  </tr>
  <tr>
    <td>[ibmcloud at option](#option)</td>
    <td>Utilisez cette commande pour afficher ou modifier des options d'événement {{site.data.keyword.cloudaccesstrailshort}}, telles que la conservation, disponibles dans un espace ou un compte.</td>
  </tr>
  <tr>
    <td>[ibmcloud at session create](#session_create)</td>
    <td>Utilisez cette commande pour créer une nouvelle session.</td>
  </tr>
  <tr>
    <td>[ibmcloud at session delete](#session_delete)</td>
    <td>Utilisez cette commande pour supprimer une session.</td>
  </tr>  
  <tr>
    <td>[ibmcloud at session list](#session_list)</td>
    <td>Utilisez cette commande pour afficher une liste des sessions actives et de leurs ID.</td>
  </tr>  
  <tr>
    <td>[ibmcloud at session show](#session_show)</td>
    <td>Utilisez cette commande pour afficher l'état d'une session unique.</td>
  </tr>   
  <tr>
    <td>[ibmcloud at status](#status)</td>
    <td>Utilisez cette commande pour afficher des informations sur le statut des événements stockés dans {{site.data.keyword.cloudaccesstrailshort}}.</td>
  </tr>
  </table>


## ibmcloud at
{: #base}

Fournit des informations sur la version de l'interface de ligne de commande et sur son mode d'utilisation.

```
ibmcloud at [parameters]
```
{: codeblock}

**Paramètres**

<dl>
<dt>--help, -h</dt>
<dd>Définissez ce paramètre pour afficher la liste des commandes ou pour obtenir de l'aide sur une commande.
</dd>

<dt>--version, -v</dt>
<dd>Définissez ce paramètre pour imprimer la version de l'interface de ligne de commande.</dd>
</dl>

**Exemples**

Pour obtenir la liste des commandes, exécutez la commande suivante :

```
ibmcloud at --help
```
{: codeblock}

Pour obtenir la version de l'interface de ligne de commande, exécutez la commande suivante :

```
ibmcloud at --version
```
{: codeblock}


## ibmcloud at delete
{: #delete}

Supprime des événements {{site.data.keyword.cloudaccesstrailshort}}.

```
ibmcloud at delete [parameters] [arguments..]
```
{: codeblock}

**Paramètres**

<dl>
  <dt>--start value, -s value</dt>
  <dd>(Facultatif) Définit la date de début en Temps Universel Coordonné (TUC) : *AAAA-MM-JJ*, par exemple, `2017-01-02`. <br>La valeur par défaut est définie sur les deux semaines précédant la date en cours. 
  </dd>
  
  <dt>--end value, -e value</dt>
  <dd>(Facultatif) Définit la date de fin en Temps Universel Coordonné (TUC) : *AAAA-MM-JJ* <br>Le format TUC de la date est **AAAA-MM-JJ**, par exemple, `2017-01-02`. <br>La valeur par défaut est définie sur la date en cours.
  </dd>
  
  <dt>--search-time value, -T value</dt>
  <dd>(Facultatif) Vous pouvez définir ce paramètre pour supprimer les événements qui sont stockés pendant un certain nombre d'heures, un jour spécifique. Le format de la zone est le suivant : 0-23
  </dd>

</dl>


**Exemple**

Pour supprimer les événements du 22 juin 2017, exécutez la commande suivante :
```
ibmcloud at delete -s 2017-06-22 -e 2017-06-22
```
{: codeblock}

Vous recevez des informations similaires à la sortie suivante :

`Deleted successfully`
`"6 logs were deleted, freeing 13737 bytes."`


## ibmcloud at download
{: #download}

Télécharge des événements {{site.data.keyword.cloudaccesstrailshort}} dans un fichier local ou les transfère en continu vers une fenêtre de terminal sous Windows et Mac OS X ou vers stdout sur un terminal Linux. 

**Note:** Pour télécharger des fichiers, vous devez d'abord créer une session. Une session définit les événements à télécharger selon une plage de dates. Vous téléchargez les événements dans le cadre du contexte d'une session. 

```
ibmcloud at download [parameters] [arguments...]
```
{: codeblock}

**Paramètres**

<dl>
<dt>--output value, -o value</dt>
<dd>(Facultatif) Définit le chemin d'accès et le nom du fichier de sortie local dans lequel les événements sont téléchargés. <br>La valeur par défaut est un trait d'union (-). <br>Définissez ce paramètre sur la valeur par défaut pour que les journaux soient générés dans la sortie standard.</dd>
</dl>

**Arguments**

<dl>
<dt>ID de session</dt>
<dd>Définissez la valeur d'ID de session obtenue lorsque vous avez exécuté la commande `ibmcloud at session create`. Cette valeur indique quelle session utiliser lors du téléchargement des événements. <br>**Remarque :** La commande `ibmcloud at session create` fournit les paramètres qui contrôlent quels événements sont téléchargés. </dd>
</dl>

**Remarque :** Une fois le téléchargement terminé, pour télécharger de nouveau les mêmes données, vous devez utiliser un autre fichier ou une autre session.

**Exemple**

Pour télécharger des événements dans un fichier nommé `events.log`, exécutez la commande suivante :

```
ibmcloud at download -o events.log 1db6ce16-824d-4d50-bd40-37f1d8fea9b7
```
{: screen}

Vous recevez des informations similaires à la sortie suivante : 

```
6.70 KiB / 3.06 KiB [========] 219.03% 8.60 MiB/s 0s
Download completed successfully
```
{: screen}


## ibmcloud at help
{: #help}

Fournit des informations sur l'utilisation d'une commande.

```
ibmcloud at help [parameters]
```
{: codeblock}

**Paramètres**

<dl>
<dt>Commande</dt>
<dd>Définissez le nom de la commande pour laquelle vous souhaitez obtenir de l'aide.
</dd>
</dl>


**Exemple**

Pour obtenir de l'aide sur l'exécution de la commande pour afficher le statut d'{{site.data.keyword.cloudaccesstrailshort}}, exécutez la commande suivante :

```
ibmcloud at help status
```
{: codeblock}


## ibmcloud at option
{: #option}

Affiche ou modifie la durée de conservation des événements disponibles dans un espace. Lorsque vous définissez une règle de conservation, les événements sont automatiquement supprimés lorsque le nombre de jours de conservation est atteint.

* La durée est définie en nombre de jours.
* La valeur par défaut est **-1**, c'est-à-dire que les événements sont stockés et ne sont pas supprimés.

**Remarque :** Par défaut, tous les événements sont stockés. Si vous ne définissez pas de durée de conservation, vous devez supprimer les événements manuellement à l'aide de la commande `ibmcloud at delete`. 

```
ibmcloud at option [parameters] [arguments...]
```
{: codeblock}

**Paramètres**

<dl>
<dt>--retention value, -r value</dt>
<dd>(Facultatif) Définit le nombre de jours de conservation. <br> La valeur par défaut est *-1* jour.</dd>

<dt>--at-account-level, -a</dt>
<dd>(Facultatif) Définissez ce paramètre pour répertorier les informations relatives à la durée de conservation pour les événements stockés dans chaque domaine d'espace et dans le domaine de compte.

</dl>

**Exemple**

Pour afficher la durée de conservation en cours pour l'espace où vous êtes connecté, exécutez la commande suivante :

```
ibmcloud at option
```
{: codeblock}

La sortie obtenue est similaire à la suivante :

```
+--------------------------------------+-----------+
|               SPACEID                | RETENTION |
+--------------------------------------+-----------+
| 2af890ce-fb4f-4e41-a975-901a56ed1f11 |        30 |
+--------------------------------------+-----------+
```
{: screen}


Pour modifier la durée de conservation à 25 jours pour l'espace où vous êtes connecté, exécutez la commande suivante :

```
ibmcloud at option -r 25
```
{: codeblock}

La sortie obtenue est similaire à la suivante :

```
+--------------------------------------+-----------+
|               SPACEID                | RETENTION |
+--------------------------------------+-----------+
| 2af890ce-fb4f-4e41-a975-901a56ed1f11 |        25 |
+--------------------------------------+-----------+
```
{: screen}



## ibmcloud at session create
{: #session_create}

Crée une nouvelle session.

**Remarque :** vous pouvez avoir jusqu'à 30 sessions simultanées dans un espace. La session est créée pour un utilisateur. Les sessions ne peuvent pas être partagées
entre les utilisateurs dans un espace.

```
ibmcloud at session create [parameters] [arguments...]
```
{: codeblock}

**Paramètres**

<dl>
  <dt>--at-account-level, -a </dt>
  <dd>(Facultatif) Définit l'étendue du niveau de compte. </br>Définissez cette valeur pour obtenir des informations relatives à un compte. <br>Si ce paramètre n'est pas spécifié, la valeur par défaut est l'espace en cours uniquement, c'est-à-dire l'espace auquel vous vous êtes connecté avec la commande `ibmcloud cf login`.
  </dd>

  <dt>--start value, -s value</dt>
  <dd>(Facultatif) Définit la date de début en Temps Universel Coordonné (TUC) : *AAAA-MM-JJ*, par exemple, `2017-01-02`. <br>La valeur par défaut est définie sur les deux semaines précédant la date en cours. 
  </dd>
  
  <dt>--end value, -e value</dt>
  <dd>(Facultatif) Définit la date de fin en Temps Universel Coordonné (TUC) : *AAAA-MM-JJ*, par exemple, `2017-01-02`. <br>La valeur par défaut est définie sur la date en cours. 
  </dd>

  <dt>--search-time value, -T value</dt>
  <dd>(Facultatif) Vous pouvez définir ce paramètre pour supprimer les événements qui sont stockés pendant un certain nombre d'heures, un jour spécifique. Le format de la zone est le suivant : 0-23
  </dd>


 </dl>

**Valeurs renvoyées**

<dl>
<dt>Access-Time</dt>
<dd>Horodatage indiquant quand la session a été utilisée pour la dernière fois.</dd>

<dt>Create-Time</dt>
<dd>Horodatage correspondant à la date et à l'heure de création de la session.</dd>

<dt>Date-Range</dt>
<dd>Indique les jours utilisés pour filtrer les événements. Les événements identifiés dans cette plage de dates sont disponibles pour être gérés dans la session.</dd>

<dt>ID</dt>
<dd>ID de session.</dd>

<dt>Space</dt>
<dd>ID de l'espace où la session est active.</dd>

<dt>Type-Account</dt>
<dd>Cette valeur est définie sur **ActivityTracker**.</dd>

<dt>Username</dt>
<dd>{{site.data.keyword.IBM_notm}}ID de l'utilisateur qui a créé la session.</dd>
</dl>


**Exemple**

Pour créer une session pour le 10 juillet 2017, exécutez la commande suivante :

```
ibmcloud at session create -s 2017-07-10 -e 2017-07-10
```
{: screen}

La sortie obtenue est similaire à la suivante :

```
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| id           | 9b8c4db8-5841-4993-a449-305815a53a8e      |
| space        | xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx      |
| username     | xxx@yyy.com                               |
| create-time  | 2017-07-25T11:54:00.20042645Z             |
| access-time  | 2017-07-25T11:54:00.20042645Z             |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
+--------------+-------------------------------------------+
```
{: screen}



## ibmcloud at session delete
{: #session_delete}

Supprime la session indiquée par l'ID de session.

```
ibmcloud at session delete [arguments...]
```
{: codeblock}


**Arguments**

<dl>
<dt>ID de session</dt>
<dd>ID de la session que vous souhaitez supprimer. <br>Vous pouvez utiliser la commande `ibmcloud at session list` pour obtenir tous les ID de session active.</dd>
</dl>

**Exemple**

Pour supprimer une session dont l'ID est *9b8c4db8-5841-4993-a449-305815a53a8e*, exécutez la commande suivante :

```
ibmcloud at session delete 9b8c4db8-5841-4993-a449-305815a53a8e
```
{: screen}

La sortie obtenue est similaire à la suivante :

```
+---------------+--------------------------+
|    NAME       |     VALUE                |
+---------------+--------------------------+
|  message      | Delete session success   |
+---------------+--------------------------+
```
{: screen}


## ibmcloud at session list
{: #session_list}

Affiche une liste des sessions actives et de leurs ID.

```
ibmcloud at session list 
```
{: codeblock}

**Valeurs renvoyées**

<dl>
<dt>ID</dt>
<dd>ID de session.</dd>

<dt>SPACE</dt>
<dd>ID de l'espace où la session est active.</dd>

<dt>USERNAME</dt>
<dd>{{site.data.keyword.IBM_notm}}ID de l'utilisateur qui a créé la session.</dd>

<dt>CREATE-TIME</dt>
<dd>Horodatage correspondant à la date et à l'heure de création de la session.</dd>

<dt>ACCESS-TIME</dt>
<dd>Horodatage indiquant quand la session a été utilisée pour la dernière fois.</dd>
</dl>
 
**Exemple**

Pour obtenir la liste des sessions, exécutez la commande suivante :

```
ibmcloud at session list
```
{: screen}

La sortie obtenue est similaire à la suivante :

```
+--------------------------------------+--------------------------------------+-----------------------------------+--------------------------------+--------------------------------+
| ID                                   | SPACE                                | USERNAME                          | CREATE-TIME                    | ACCESS-TIME                    |
+--------------------------------------+--------------------------------------+-----------------------------------+--------------------------------+--------------------------------+
| fa3f1970-21f3-4e32-b480-1ffb41badc16 | 12345678-fb4f-acdf-a975-11335678r3fg | xxx@yyy.com                       | 2017-07-10T09:04:07.916788069Z | 2017-07-10T09:04:07.916788069Z |
| 9b8c4db8-5841-4993-a449-305815a53a8e | 12345678-fb4f-acdf-a975-11335678r3fg | xxx@yyy.com                       | 2017-07-11T09:19:14.666532796Z | 2017-07-12T09:19:14.666532796Z |
+--------------------------------------+--------------------------------------+-----------------------------------+--------------------------------+--------------------------------+
```
{: screen}


## ibmcloud at session show
{: #session_show}

Affiche l'état d'une session unique.

```
ibmcloud at session show [arguments...]
```
{: codeblock}

**Arguments**

<dl>
<dt>ID de session</dt>
<dd>ID de la session active sur laquelle vous souhaitez obtenir des informations.</dd>
</dl>

**Valeurs renvoyées**

<dl>
<dt>Access-Time</dt>
<dd>Horodatage indiquant quand la session a été utilisée pour la dernière fois.</dd>

<dt>Create-Time</dt>
<dd>Horodatage correspondant à la date et à l'heure de création de la session.</dd>

<dt>Date-Range</dt>
<dd>Indique les jours utilisés pour filtrer les événements. Les événements identifiés dans cette plage de dates sont disponibles pour être gérés dans la session.</dd>

<dt>id</dt>
<dd>ID de session.</dd>

<dt>Space</dt>
<dd>ID de l'espace où la session est active.</dd>

<dt>Type-Account</dt>
<dd>Cette valeur est définie sur **ActivityTracker**.</dd>

<dt>Username</dt>
<dd>{{site.data.keyword.IBM_notm}}ID de l'utilisateur qui a créé la session.</dd>
</dl>

**Exemple**

Pour afficher les détails d'une session dont l'ID est *9b8c4db8-5841-4993-a449-305815a53a8e*, exécutez la commande suivante :

```
ibmcloud at session show 9b8c4db8-5841-4993-a449-305815a53a8e
```
{: screen}

La sortie obtenue est similaire à la suivante :

```
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| create-time  | 2017-07-25T11:54:00.20042645Z             |
| access-time  | 2017-07-25T11:54:00.20042645Z             |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
| id           | 9b8c4db8-5841-4993-a449-305815a53a8e      |
| space        | xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx      |
| username     | xxx@yyy.com                               |
+--------------+-------------------------------------------+
```
{: screen}


## ibmcloud at status
{: #status}

Renvoie des informations sur le statut des événements {{site.data.keyword.cloudaccesstrailshort}}.

```
ibmcloud at status [parameters] [arguments...]
```
{: codeblock}

**Paramètres**

<dl>
  <dt>--start value, -s value</dt>
  <dd>(Facultatif) Définit la date de début en Temps Universel Coordonné (TUC) : *AAAA-MM-JJ*, par exemple, `2017-01-02`. <br>La valeur par défaut est définie sur les deux semaines précédant la date en cours.
  </dd>
  
  <dt>--end value, -e value</dt>
  <dd>(Facultatif) Définit la date de fin en Temps Universel Coordonné (TUC) : *AAAA-MM-JJ*, par exemple, `2017-01-02`. <br>La valeur par défaut est définie sur la date en cours.
  </dd>
  
  <dt>--at-account-level, -a </dt>
  <dd>(Facultatif) Définit l'étendue du niveau de compte. <br> **Remarque :** Définissez cette valeur pour obtenir des informations relatives à un compte. <br>Si ce paramètre n'est pas spécifié, la valeur par défaut est l'espace en cours uniquement, c'est-à-dire l'espace auquel vous vous êtes connecté avec la commande `ibmcloud cf login`.
  </dd>
  
</dl>


**Remarque :** La commande `ibmcloud at status` ne renvoie que les deux dernières semaines d'événements stockés dans {{site.data.keyword.cloudaccesstrailshort}} lorsqu'aucune date de début et de fin n'est spécifiée. 

**Valeurs renvoyées**   

<dl>
  <dt>DATE</dt>
  <dd>Date de fin en Temps Universel Coordonné (TUC) : *AAAA-MM-JJ*, par exemple, `2017-01-02`. 
  </dd>
  
  <dt>COUNT</dt>
  <dd>Nombre total d'événements.
  </dd>
  
  <dt>SIZE</dt>
  <dd>Taille totale des événements en mégaoctets.
  </dd>

  <dt>TYPES</dt>
  <dd>Cette valeur est définie sur **ActivityTracker**.
  </dd>
  
  <dt>SEARCHABLE</dt>
  <dd>Cette zone indique si les événements peuvent être soumis à une opération de recherche dans Kibana. <br>Lorsque la valeur de la zone **SEARCHABLE** est définie sur *None*, les événements sont disponibles pour téléchargement, mais vous ne pouvez pas les analyser dans Kibana.
  </dd>
  
</dl>

**Exemple**

Pour afficher les détails des événements du 20 juillet 2017, exécutez la commande suivante :

```
ibmcloud at status -s 2017-07-20 -e 2017-07-20
```
{: codeblock}


Vous recevez des informations similaires à la sortie suivante :

```
+------------+-----------+-------+------------------+--------------+
|   Date     |  Count    | Size  | Types            |  Searchable  | 
+------------+-----------+-------+------------------+--------------+
| 2017-07-20 |    1      | 2531  | ActivityTracker  | All          | 
+------------+-----------+-------+------------------+--------------+
```
{: screen}


