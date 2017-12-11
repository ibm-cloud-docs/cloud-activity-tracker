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

# Interface de ligne de commande d'Activity Tracker d'IBM Cloud
{: #at_cli}

L'interface de ligne de commande d'{{site.data.keyword.cloudaccesstraillong}} est un plug-in CF que vous pouvez utiliser pour gérer des événements {{site.data.keyword.cloudaccesstrailshort}}.
{: shortdesc}

**Prérequis**
* Avant d'exécuter les commandes, connectez-vous à {{site.data.keyword.Bluemix}} avec la commande `cf login` afin de générer un jeton d'accès {{site.data.keyword.Bluemix_short}} et d'authentifier votre session.

Pour savoir comment utiliser l'interface de ligne de commande d'{{site.data.keyword.cloudaccesstrailshort}}, voir [Gestion des événements {{site.data.keyword.cloudaccesstrailshort}} via l'interface de ligne de commande](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#managing_events). 

Le plug-in de l'interface de ligne de commande d'{{site.data.keyword.cloudaccesstraillong}} prend en charge les plateformes Linux, Mac et Windows.

<table>
  <caption>Commandes de gestion d'{{site.data.keyword.cloudaccesstrailshort}}</caption>
  <tr>
    <th>Commande</th>
    <th>Quant l'utiliser</th>
  </tr>
  <tr>
    <td>[cf at](#base)</td>
    <td>Utilisez cette commande pour obtenir des informations sur l'interface de ligne de commande, comme la version ou la liste des commandes.</td>
  </tr>
  <tr>
    <td>[cf at delete](#delete)</td>
    <td>Utilisez cette commande pour supprimer des événements {{site.data.keyword.cloudaccesstrailshort}}.</td>
  </tr>
  <tr>
    <td>[cf at download](#download)</td>
    <td>Utilisez cette commande pour télécharger des journaux {{site.data.keyword.cloudaccesstrailshort}} dans un fichier local. </td>
  </tr>
  <tr>
    <td>[cf at help](#help)</td>
    <td>Utilisez cette commande pour obtenir de l'aide sur l'utilisation de l'interface de ligne de commande et une liste de toutes les commandes.</td>
  </tr>
  <tr>
    <td>[cf at option](#option)</td>
    <td>Utilisez cette commande pour afficher ou modifier des options d'événement {{site.data.keyword.cloudaccesstrailshort}}, telles que la conservation, disponibles dans un compte ou un espace {{site.data.keyword.Bluemix_notm}}.</td>
  </tr>
  <tr>
    <td>[cf at session create](#session_create)</td>
    <td>Utilisez cette commande pour créer une nouvelle session.</td>
  </tr>
  <tr>
    <td>[cf at session delete](#session_delete)</td>
    <td>Utilisez cette commande pour supprimer une session.</td>
  </tr>  
  <tr>
    <td>[cf at session list](#session_list)</td>
    <td>Utilisez cette commande pour afficher une liste des sessions actives et de leurs ID.</td>
  </tr>  
  <tr>
    <td>[cf at session show](#session_show)</td>
    <td>Utilisez cette commande pour afficher l'état d'une session unique.</td>
  </tr>   
  <tr>
    <td>[cf at status](#status)</td>
    <td>Utilisez cette commande pour afficher des informations sur le statut des événements stockés dans {{site.data.keyword.cloudaccesstrailshort}}.</td>
  </tr>
  <tr>
    <td>[cf at trail](#trail)</td>
    <td>Utilisez cette commande pour envoyer des événements à {{site.data.keyword.cloudaccesstrailshort}}.</td>
  </tr>
  </table>


## cf at
{: #base}

Fournit des informations sur la version de l'interface de ligne de commande et sur son mode d'utilisation.

```
cf at [parameters]
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
cf at --help
```
{: codeblock}

Pour obtenir la version de l'interface de ligne de commande, exécutez la commande suivante :

```
cf at --version
```
{: codeblock}


## cf at delete
{: #delete}

Supprime des événements {{site.data.keyword.cloudaccesstrailshort}}.

```
cf at delete [parameters] [arguments..]
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
  
</dl>

**Exemple**

Pour supprimer les événements du 22 juin 2017, exécutez la commande suivante :
```
cf at delete -s 2017-06-22 -e 2017-06-22
```
{: codeblock}

Vous recevez des informations similaires à la sortie suivante :

`Deleted successfully`
`"6 logs were deleted, freeing 13737 bytes."`


## cf at download
{: #download}

Télécharge des événements {{site.data.keyword.cloudaccesstrailshort}} dans un fichier local ou les transfère en continu vers une fenêtre de terminal sous Windows et Mac OS X ou vers stdout sur un terminal Linux. 

**Note:** Pour télécharger des fichiers, vous devez d'abord créer une session. Une session définit les événements à télécharger selon une plage de dates. Vous téléchargez les événements dans le cadre du contexte d'une session. Pour plus d'informations, voir [cf at session create](/docs/services/CloudActivityTracker/reference/at_cli.html#session_create).

```
cf at download [parameters] [arguments...]
```
{: codeblock}

**Paramètres**

<dl>
<dt>--output value, -o value</dt>
<dd>(Facultatif) Définit le chemin d'accès et le nom de fichier du fichier de sortie local dans lequel les événement sont téléchargés. <br>La valeur par défaut est un trait d'union (-). <br>Définissez ce
paramètre sur la valeur par défaut pour que les journaux soient générés dans la sortie standard.</dd>
</dl>

**Arguments**

<dl>
<dt>ID de session</dt>
<dd>Définissez la valeur d'ID de session obtenue lorsque vous avez exécuté la commande `cf at session create`. Cette valeur indique quelle session utiliser lors du téléchargement des événements. <br>**Remarque :** Le commande `cf at session create` fournit les paramètres qui contrôlent quels événements sont téléchargés. </dd>
</dl>

**Remarque :** Une fois le téléchargement terminé, pour télécharger de nouveau les mêmes données, vous devez utiliser un autre fichier ou une autre session.

**Exemple**

Pour télécharger des événements dans un fichier nommé `events.log`, exécutez la commande suivante :

```
cf at download -o events.log 1db6ce16-824d-4d50-bd40-37f1d8fea9b7
```
{: screen}

Vous recevez des informations similaires à la sortie suivante : 

```
6.70 KiB / 3.06 KiB [========] 219.03% 8.60 MiB/s 0s
Download completed successfully
```
{: screen}


## cf at help
{: #help}

Fournit des informations sur l'utilisation d'une commande.

```
cf at help [parameters]
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
cf at help status
```
{: codeblock}


## cf at option
{: #option}

Affiche ou modifie la durée de conservation des événements disponibles dans un espace {{site.data.keyword.Bluemix_notm}}. Lorsque vous définissez une règle de conservation, les événements sont automatiquement supprimés lorsque le nombre de jours de conservation est atteint.

* La durée est définie en nombre de jours.
* La valeur par défaut est **-1**, c'est-à-dire que les événements sont stockés et ne sont pas supprimés.

**Remarque :** Par défaut, tous les événements sont stockés. Si vous ne définissez pas de durée de conservation, vous devez supprimer les événements manuellement à l'aide de la commande `cf at delete`. 

```
cf at option [parameters] [arguments...]
```
{: codeblock}

**Paramètres**

<dl>
<dt>--retention value, -r value</dt>
<dd>(Facultatif) Définit le nombre de jours de conservation. <br> La valeur par défaut est *-1* jour.</dd>

</dl>

**Exemple**

Pour afficher la durée de conservation en cours pour l'espace où vous êtes connecté, exécutez la commande suivante :

```
cf at option
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
cf at option -r 25
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



## cf at session create
{: #session_create}

Crée une nouvelle session.

**Remarque :** vous pouvez avoir jusqu'à 30 sessions simultanées dans un espace. La session est créée pour un utilisateur. Les sessions ne peuvent pas être partagées
entre les utilisateurs dans un espace.

```
cf at session create [parameters] [arguments...]
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
cf at session create -s 2017-07-10 -e 2017-07-10
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



## cf at session delete
{: #session_delete}

Supprime la session indiquée par l'ID de session.

```
cf at session delete [arguments...]
```
{: codeblock}


**Arguments**

<dl>
<dt>ID de session</dt>
<dd>ID de la session que vous souhaitez supprimer. <br>Vous pouvez utiliser la commande `cf at session list` pour obtenir tous les ID de session active.</dd>
</dl>

**Exemple**

Pour supprimer une session dont l'ID est *9b8c4db8-5841-4993-a449-305815a53a8e*, exécutez la commande suivante :

```
cf at session delete 9b8c4db8-5841-4993-a449-305815a53a8e
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


## cf at session list
{: #session_list}

Affiche une liste des sessions actives et de leurs ID.

```
cf at session list 
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
cf at session list
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


## cf at session show
{: #session_show}

Affiche l'état d'une session unique.

```
cf at session show [arguments...]
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
cf at session show 9b8c4db8-5841-4993-a449-305815a53a8e
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


## cf at status
{: #status}

Renvoie des informations sur le statut des événements {{site.data.keyword.cloudaccesstrailshort}}.

```
cf at status [parameters] [arguments...]
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
  <dd>(Facultatif) Définit l'étendue du niveau de compte. <br> **Remarque :** Définissez cette valeur pour obtenir des informations relatives à un compte. <br>Si ce paramètre
n'est pas spécifié, la valeur par défaut est uniquement définie sur l'espace en cours, à savoir l'espace sur lequel vous vous êtes connecté à l'aide de la commande `cf login`.
  </dd>
  
</dl>


**Remarque :** La commande `cf at status` ne renvoie que les deux dernières semaines d'événements stockés dans {{site.data.keyword.cloudaccesstrailshort}} lorsqu'aucune date de début et de fin n'est spécifiée. 

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
  <dd>Cette zone indique si les événements peuvent être soumis à une opération de recherche dans Kibana. <br>Lorsque la zone **SEARCHABLE** est définie sur *None*, les événements sont disponibles pour téléchargement, mais vous ne pouvez pas les analyser dans Kibana.
  </dd>
  
</dl>

**Exemple**

Pour afficher les détails des événements du 20 juillet 2017, exécutez la commande suivante :

```
cf at status -s 2017-07-20 -e 2017-07-20
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



## cf at trail
{: #trail}

Envoie des événements sérialisés à {{site.data.keyword.cloudaccesstrailshort}}.

```
cf at trail [parameters] [arguments...]
```
{: codeblock}

**Paramètres**

<dl>
  <dt>--file FILE, -f FILE</dt>
  <dd>(Facultatif) Indiquez le fichier d'événements au format : `PATH/filename`
  </dd>
  
  <dt>--type FORMAT, -t FORMAT</dt>
  <dd>(Facultatif) Indiquez le format des événements inclus dans le fichier. Les valeurs admises sont : *cadf* et *kong*. <br> Utilisez *CADF* pour envoyer des événements conformes au format CADF. Utilisez *KONG* pour envoyer des événements conformes au format Kong. <br> **Remarque :** Vous ne pouvez envoyer dans un fichier que des événements de même type.
  </dd>
 </dl>
 
**Exemple**

Pour envoyer à {{site.data.keyword.cloudaccesstrailshort}} des événements CADF sérialisés, exécutez la commande suivante :

```
cf at trail -t cadf -f events.log
```
{: codeblock}

où *events.log* correspond au fichier qui contient les événements à envoyer à {{site.data.keyword.cloudaccesstrailshort}}. Ce fichier inclut des événements conformes au format CADF.

Vous recevez des informations similaires à la sortie suivante :

```
+--------------------------------------+---------------------------+
|            ID                        |          Value            |
+--------------------------------------+---------------------------+
| bbb170dc-2b0a-42d4-b560-b416f3308869 | B0UtwP1FhemsZIr4rTJVKA==  |
+--------------------------------------+---------------------------+
| 688f1194-2305-4367-8ece-f468e67c19fb | KLCG9f++usNolgvutRCR1Q==  |
+--------------------------------------+---------------------------+
```
{: screen}
