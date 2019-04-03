---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, event fields

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



# Zones d'événement
{: #at_event}

Les événements {{site.data.keyword.cloudaccesstrailshort}} sont conformes à la norme CADF (Cloud Auditing Data Federation). 
{:shortdesc}

## Zones de l'initiateur
{: #initiator}

Le tableau suivant répertorie les zones communes disponibles pour un événement {{site.data.keyword.cloudaccesstrailshort}} :

| Nom de zone | Description | Valeur |
|------------|-------------|-------|
| `initiator.id` | ID de l'initiateur de l'action. </br></br>Les types d'initiateur valides sont `IBMID`, `serviceID` et `Cloud Foundry (CF) user ID`. | Exemple d'IBMID : `IBMid-000000XXX2` </br>Exemple d'ID de service : `iam-ServiceId-12345678-0165-4c89-847d-9660b1632e14` </br>Exemple d'ID utilisateur CF : `7666666b-23ae-4a34-8569-cu75tgdr4da3` |
| `initiator.name` | Nom de l'utilisateur qui a initié l'action. | Par exemple, une adresse e-mail. |
| `initiator.typeURI` | Type de la source de l'événement. | Les valeurs valides sont *service/security/account/user*, *service/security/clientid* et *service/security/account/serviceid*. |
| `initiator.credential.type` | Type de données d'identification de l'ID initiateur. | Les valeurs valides sont *user*, *token* et *apikey*. |
{: caption="Tableau 1. Zones communes de l'initiateur" caption-side="top"} 

  

## Zones cible
{: #target}

Le tableau suivant répertorie les zones cible communes disponibles pour un événement {{site.data.keyword.cloudaccesstrailshort}} :

| Nom de zone | Description | Valeur |
|------------|-------------|-------|
| `target.id` | Nom de ressource de cloud (CRN) sur laquelle l'action est exécutée. </br>Pour plus d'informations, voir [Format CRN](/docs/overview?topic=overview-format-crn#format). | Par exemple, `crn:v1:bluemix:public:cloud-object-storage:global:a/12345678e6232019c6567c9123456789:fr56et47-befb-440a-a223c-12345678dae1:bucket:bucket1` |
| `target.name` | Nom lisible de la ressource de cloud sur laquelle l'action est exécutée. |  |
| `target.typeURI` | Type de la ressource de cloud sur laquelle l'action est exécutée. </br>Le format de cette zone est **serviceName/objectType**, où `serviceName` correspond au nom du service. | Par exemple, `iam-am/policy` ou `cloud-object-storage/bucket/acl` |
{: caption="Tableau 2. Zones cible communes" caption-side="top"} 


 
## Zones d'action
{: #action}

Le tableau suivant répertorie les zones d'action communes disponibles pour un événement {{site.data.keyword.cloudaccesstrailshort}} :

| Nom de zone | Description | Valeur |
|------------|-------------|-------|
| `action` | Action qui déclenche l'événement. </br>Le format de cette zone est **serviceName.objectType.action**, où `serviceName` correspond au nom du service. </br>Pour plus d'informations sur les valeurs d'action d'événements générés par un service, voir <a href="/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-cloud_services#cloud_services">Services Cloud</a> | Par exemple, `iam-identity.serviceid-apikey.login` |
| `eventTime` | Indique la date et l'heure de création de l'événement. </br>La date est représentée en Temps Universel Coordonné (UTC). </br>Le format respecte la norme ISO 8601. | Par exemple, `2017-10-19T19:07:50.32+0000` |
{: caption="Tableau 3. Zones d'action communes" caption-side="top"} 



## Zones de résultat
{: #outcomes}

Le tableau suivant répertorie les zones de résultat communes disponibles pour un événement {{site.data.keyword.cloudaccesstrailshort}} :

| Nom de zone | Description | Valeur |
|------------|-------------|-------|
| `outcome` | Résultat de l'action. | Les valeurs valides sont *success*, *failure* et *pending*. |
| `reason.reasonCode` | Zone numérique qui inclut le code de réponse HTTP. | Par exemple, *200* pour un succès. |
| `severity` | Définit le niveau de menace qu'une action peut présenter sur le cloud. | Les valeurs valides sont *normal*, *warning* et *critical*. </br></br>**Normal** est défini pour les actions de routine dans le cloud. Par exemple, le démarrage d'une instance ou l'actualisation d'un jeton. </br></br>**Warning** est défini pour les actions où une ressource de cloud est mise à jour ou dont les métadonnées sont modifiées. Par exemple, la mise à jour de la version d'un noeud worker, le changement de nom d'un certificat ou d'une instance de service. </br></br>**Critical** est défini pour les actions qui affectent la sécurité du cloud. Par exemple, la modification des données d'identification d'un utilisateur, la suppression de données, l'accès non autorisé pour travailler avec une ressource de cloud. |
{: caption="Tableau 4. Zones de résultat communes" caption-side="top"} 


