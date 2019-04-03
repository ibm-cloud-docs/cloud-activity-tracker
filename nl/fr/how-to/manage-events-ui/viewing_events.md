---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, view events, UI

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


# Affichage d'événements
{: #view_acc_events}

Vous pouvez afficher des événements via l'interface utilisateur d'{{site.data.keyword.cloudaccesstrailshort}} dans la console {{site.data.keyword.cloud_notm}} ou via Kibana.
{:shortdesc}
   

## Affichage d'événements de compte
{: #view_acc_events_account_events}

Vous pouvez afficher des événements dans un domaine de compte {{site.data.keyword.cloudaccesstrailshort}} via l'interface utilisateur d'{{site.data.keyword.cloudaccesstrailshort}} ou via Kibana.

Un **propriétaire de compte** dispose des droits nécessaires pour afficher des événements dans un domaine de compte {{site.data.keyword.cloudaccesstrailshort}} via l'interface utilisateur d'{{site.data.keyword.cloudaccesstrailshort}} ou via Kibana.

En tant que **membre d'un compte**, tenez compte des informations suivantes pour afficher des événements de compte dans une région :

* Vous devez disposer du rôle *Développeur* dans l'espace où {{site.data.keyword.cloudaccesstrailshort}} est mis à disposition. Pour plus d'informations, voir [Octroi d'un rôle CF](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-grant_permissions#grant_cf_role).

* Vous devez disposer d'une règle IAM pour le service {{site.data.keyword.loganalysisshort}} avec le rôle *Afficheur* dans cette région. Le rôle d'afficheur est le rôle IAM minimal requis. Pour plus d'informations, voir [Octroi de droits IAM](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-grant_permissions#grant_iam_policy).

* Vous pouvez afficher des événements via Kibana. Pour plus d'informations sur le lancement de Kibana, voir [Accès à Kibana depuis un navigateur Web](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-launch_kibana#launch_Kibana_from_browser).



## Affichage d'événements d'espace
{: #view_acc_events_space_events}

Vous pouvez afficher des événements dans un domaine d'espace {{site.data.keyword.cloudaccesstrailshort}} via l'interface utilisateur d'{{site.data.keyword.cloudaccesstrailshort}}. Si vous disposez d'un plan Premium, vous pouvez également afficher les événements via Kibana.

Un **propriétaire de compte** dispose des droits nécessaires pour afficher les événements d'un domaine d'espace {{site.data.keyword.cloudaccesstrailshort}}.

En tant que **membre d'un compte**, vous devez disposer du rôle *Développeur* dans l'espace où {{site.data.keyword.cloudaccesstrailshort}} est mis à disposition.


