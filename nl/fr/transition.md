---

copyright:
  years: 2016, 2019
lastupdated: "2019-06-06"

keywords: IBM Cloud, Activity Tracker, migration

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


# Transition vers {{site.data.keyword.at_full_notm}}
{: #transition}

{{site.data.keyword.cloudaccesstrailfull}} est obsolète depuis le 9 mai 2019. [En savoir plus](https://www.ibm.com/blogs/cloud-archive/2019/04/deprecating-ibm-cloud-activity-tracker/). Le service est remplacé par {{site.data.keyword.at_full_notm}}. [En savoir plus](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started).
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} est obsolète. A compter du 9 mai 2019, vous ne pourrez plus mettre à disposition de nouvelles instances {{site.data.keyword.cloudaccesstrailshort}}. Les instances de plan existantes sont prises en charge jusqu'au 30 septembre 2019. Pour continuer à surveiller l'activité de votre compte {{site.data.keyword.cloud_notm}}, mettez à disposition une instance du [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}


Procédez comme suit pour migrer vers {{site.data.keyword.at_full_notm}} : 

1. Sauvegardez une copie des événements stockés dans {{site.data.keyword.cloudaccesstrailfull}} pour les recherches ultérieures. Vous pouvez utiliser l'interface de ligne de commande {{site.data.keyword.cloudaccesstrailshort}} ou l'API. 

    Assurez-vous de sauvegarder les événements d'espace pour chaque espace Cloud Foundry dans lequel il existe une instance {{site.data.keyword.cloudaccesstrailshort}} et pour chaque domaine de compte dans chaque région que vous surveillez actuellement.

    * [Téléchargement d'événements à l'aide de l'interface de ligne de commande](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-downloading_events).

    * [Téléchargement d'événements à l'aide de l'API](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-downloading_events_api).

2. Mettez à disposition [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-provision).

    Vous ne pouvez mettre à disposition qu'une seule instance par région. 
    
3. Créez et configurez des groupes d'accès pour gérer les droits dans {{site.data.keyword.cloud_notm}}. 

    * [Octroi de droits d'administration à un utilisateur ou à un ID de service](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-iam_manage_events).

    * [Octroi de droits utilisateur à un utilisateur ou à un ID de service](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-iam_view_events).

4. Définissez des vues et des tableaux de bord dans {{site.data.keyword.at_full_notm}} pour analyser et gérer les événements. [En savoir plus](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-views).

    La migration des tableaux de bord Kibana vers des tableaux de bord LogDNA n'est pas automatisée. Vous devez implémenter manuellement les nouveaux tableaux de bord. 

    Notez que dans LogDNA, les histogrammes et les graphiques circulaires sont les seules visualisations que vous pouvez implémenter.

5. [Facultatif] Configurez l'archivage pour votre instance {{site.data.keyword.at_full_notm}}. 

    Vous pouvez archiver des événements dans {{site.data.keyword.cos_full_notm}} (COS). [En savoir plus](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-archiving).

    **Remarque :** Vous êtes responsable de la mise à disposition d'une instance COS utilisées pour archiver les événements et pour la conservation des événements archivés. 

    Cette étape est requise uniquement pour les instances {{site.data.keyword.at_full_notm}} comportant un plan payant.

6. Explorez les autres fonctions, telles que la [création d'alertes](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-alerts).


Lorsque vous êtes prêt à arrêter la surveillance de votre activité cloud par le biais de vos instances {{site.data.keyword.cloudaccesstrailshort}} existantes, procédez comme suit :

1. Supprimez les instances {{site.data.keyword.cloudaccesstrailshort}} existantes depuis la console {{site.data.keyword.cloud_notm}}.
2. Retirez aux utilisateurs tous les droits leur permettant d'utiliser ces instances existantes. 


