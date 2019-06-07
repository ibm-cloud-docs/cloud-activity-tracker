---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, view events

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
{:deprecated: .deprecated}

# Affichage des informations sur les événements
{: #viewing_event_status}

Utilisez la commande `ibmcloud at status` pour obtenir des informations sur les événements collectés et stockés dans {{site.data.keyword.cloudaccesstrailshort}} pour un espace {{site.data.keyword.Bluemix}}.
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} est obsolète. A compter du 9 mai 2019, vous ne pourrez plus mettre à disposition de nouvelles instances {{site.data.keyword.cloudaccesstrailshort}}. Les instances de plan existantes sont prises en charge jusqu'au 30 septembre 2019. Pour continuer à surveiller l'activité de votre compte {{site.data.keyword.cloud_notm}}, mettez à disposition une instance du [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}


Vous pouvez obtenir des informations sur la taille du journal des événements, le nombre d'enregistrements, ainsi que sur la disponibilité des événements pour l'analyse dans Kibana. 

Procédez comme suit pour afficher des informations sur le journal des événements :

## Etape 1 : Connexion à {{site.data.keyword.cloud_notm}}
{: #viewing_event_status_step1}

Connectez-vous à {{site.data.keyword.cloud_notm}}. Effectuez les opérations suivantes :

1. Exécutez la commande [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) pour vous connecter à {{site.data.keyword.cloud_notm}}.
2. Exécutez la commande [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) pour définir l'organisation et l'espace où mettre le service {{site.data.keyword.cloudaccesstrailshort}} à disposition.

**Remarque :** définissez l'organisation et l'espace où {{site.data.keyword.cloudaccesstrailshort}} est mis à disposition.

## Etape 2 : Identification des événements disponibles
{: #viewing_event_status_step2}

Utilisez la commande `ibmcloud at status` pour afficher les informations relatives aux événements disponibles dans un domaine d'espace.

* Pour obtenir des informations sur les événements d'un domaine d'espace, exécutez la commande `ibmcloud at status`.
* Pour obtenir des informations sur les événements d'un domaine de compte, exécutez la commande `ibmcloud at status` avec l'option `-a`.

```
$ ibmcloud at status -a -s YYYY-MM-DD -e YYYY-MM-DD 
```
{: codeblock}
    
où
    
* *-a* est utilisé pour indiquer que la demande s'applique au domaine de compte.
* *-s* est utilisé pour définir la date de début en UTC (Universal Coordinated Time) : *AAAA-MM-JJ*.
* *-e* est utilisé pour définir la date de fin en UTC (Universal Coordinated Time) : *AAAA-MM-JJ*.

Par exemple, pour afficher les événements disponibles pour les deux dernières semaines dans un domaine d'espace, exécutez la commande suivante :

```
$ ibmcloud at status
```
{: codeblock}
    
Par exemple, l'exécution de cette commande génère la sortie suivante :
    
```
+------------+--------+------------+
|    DATE    |  COUNT | SEARCHABLE |
+------------+--------+------------+
| 2017-07-24 |    16  |    None    |
+------------+--------+------------+
| 2017-07-25 |   1224 |    All     |
+------------+--------+------------+
```
{: screen}

**Remarque :** le service {{site.data.keyword.cloudaccesstrailshort}} est un service global qui utilise UTC (Coordinated Universal Time). Les jours sont définis
en tant que jours UTC. Pour obtenir les événements d'un jour spécifique en heure locale, vous devez télécharger plusieurs jours TUC.
	














