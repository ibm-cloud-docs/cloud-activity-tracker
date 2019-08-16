---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, news

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

# Nouveautés
{: #whatsnew}

Découvrez les fonctions et intégrations les plus récentes d'{{site.data.keyword.cloudaccesstrailshort}}.
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} est obsolète. A compter du 9 mai 2019, vous ne pourrez plus mettre à disposition de nouvelles instances {{site.data.keyword.cloudaccesstrailshort}}. Les instances de plan existantes sont prises en charge jusqu'au 30 septembre 2019. Pour continuer à surveiller l'activité de votre compte {{site.data.keyword.cloud_notm}}, mettez à disposition une instance du [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}

Pour obtenir la liste à jour des services intégrés avec {{site.data.keyword.cloudaccesstrailshort}}, voir [Services Cloud](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-cloud_services#cloud_services).
{: important}


## Mars 2019
{: #march2019}

* {{site.data.keyword.cloudaccesstrailshort}} Interface de ligne de commande

Nous avons identifié un problème lié à l'interface CLI de suivi d'activité (Activity Tracker). Une nouvelle version de l'interface CLI sera publiée afin de résoudre ce problème.

Si vous vous connectez à {{site.data.keyword.cloud_notm}} depuis la ligne de commande en utilisant `ibmcloud login` puis exécutez des commandes {{site.data.keyword.cloudaccesstrailshort}}, vous obtenez l'erreur `Failed: Unauthorized` pour toute commande {{site.data.keyword.cloudaccesstrailshort}} que vous exécutez. 

Pour continuer à utiliser l'interface CLI, vous pouvez néanmoins vous connecter à {{site.data.keyword.cloud_notm}} en utilisant les commandes suivantes :

| Région | Commande |
|--------|---------|
| `Sud des Etats-Uni` | `bx login -a api.ng.bluemix.net -o OrgName -s SpaceName` |
| `EU DE`    | `bx login -a api.eu-de.bluemix.net -o OrgName -s SpaceName` |
| `EU DE`    | `bx login -a api.au-syd.bluemix.net -o OrgName -s SpaceName` |
{: caption="Tableau 1. Commandes" caption-side="top"} 

## Février 2019
{: #february2019}

* **Vous pouvez surveiller le service {{site.data.keyword.GlobalizationPipeline_short}} avec {{site.data.keyword.cloudaccesstrailshort}}.**

    Le service {{site.data.keyword.GlobalizationPipeline_short}} permet aux développeurs d'application de publier rapidement des applications traduites aux clients dans le monde entier.

    Pour plus d'informations sur les événements {{site.data.keyword.cloudaccesstrailshort}}, voir [Evénements générés par {{site.data.keyword.GlobalizationPipeline_short}}](/docs/services/GlobalizationPipeline?topic=GlobalizationPipeline-gpat_events#gpat_events).








