---

copyright:
  years: 2016, 2018
lastupdated: "2018-07-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}



# Zones d'événement Activity Tracker
{: #at_event}

Les événements {{site.data.keyword.cloudaccesstrailshort}} sont conformes à la norme CADF (Cloud Auditing Data Federation). 
{:shortdesc}

## Zones de l'initiateur
{: #initiator}

Le tableau suivant répertorie les zones communes disponibles pour un événement {{site.data.keyword.cloudaccesstrailshort}} :

<table>
  <caption>Zones communes de l'initiateur</caption>
  <tr>
    <th>Nom de zone</th>
	  <th>Description</th>
    <th>Valeur</th>
  </tr>
  <tr>
    <td>initiator.id</td>
	  <td>ID de l'initiateur de l'action. </br>Il existe deux types d'initiateurs : IBMID et serviceID.</td>
    <td>Exemple d'IBMID : IBMid-000000XXX2 </br>Exemple d'ID de service : iam-ServiceId-12345678-0165-4c89-847d-9660b1632e14</td>
  </tr>
  <tr>
    <td>initiator.name</td>
	  <td>Nom de l'utilisateur qui a initié l'action.</td>
    <td></td>
  </tr>
  <tr>
    <td>initiator.typeURI</td>
	  <td>Type de la source de l'événement.</td>
    <td>Les valeurs admises sont : *service/security/account/user*, *service/security/clientid*, *service/security/account/serviceid*</td>
  </tr>
  <tr>
    <td>initiator.credential.type</td>
	  <td>Type de données d'identification de l'ID initiateur. </td>
    <td>Les valeurs admises sont : *user*, *token*, *apikey*</td>
  </tr>
</table>

## Zones cible
{: #target}

Le tableau suivant répertorie les zones cible communes disponibles pour un événement {{site.data.keyword.cloudaccesstrailshort}} :

<table>
  <caption>Zones cible communes</caption>
  <tr>
    <th>Nom de zone</th>
	  <th>Description</th>
    <th>Valeur</th>
  </tr>
  <tr>
    <td>target.id</td>
	  <td>Nom de ressource de cloud (CRN) sur laquelle l'action est exécutée. </br>Pour plus d'informations, voir [Format CRN](/docs/overview/crn.html#format).</td>
    <td>Par exemple : `crn:v1:bluemix:public:cloud-object-storage:global:a/12345678e6232019c6567c9123456789:fr56et47-befb-440a-a223c-12345678dae1:bucket:bucket1`</td>
  </tr>
  <tr>
    <td>target.name</td>
	  <td>Nom lisible de la ressource de cloud sur laquelle l'action est exécutée. </td>
    <td></td>
  </tr>
  <tr>
    <td>target.typeURI</td>
    <td>Type de la ressource de cloud sur laquelle l'action est exécutée. </br>Le format de cette zone est **serviceName/objectType** où serviceName correspond au nom du service. </td>
	  <td>Par exemple : `iam-am/policy` ou `cloud-object-storage/bucket/acl`</td>
  </tr>
</table>
 
## Zones d'action
{: #action}

Le tableau suivant répertorie les zones d'action communes disponibles pour un événement {{site.data.keyword.cloudaccesstrailshort}} :

<table>
  <caption>Zones d'action communes</caption>
  <tr>
    <th>Nom de zone</th>
	  <th>Description</th>
    <th>Valeur</th>
  </tr>
  <tr>
    <td>action</td>
	  <td>Action qui déclenche l'événement. </br>Le format de cette zone est **serviceName.objectType.action** où serviceName correspond au nom du service. </br>Pour plus d'informations sur les événements générés par un service, voir <a href="/docs/services/cloud-activity-tracker/cloud_services.html#cloud_services">Services cloud</a>.</td>
    <td>Par exemple : *iam-identity.serviceid-apikey.login*</td>
  </tr>
  <tr>
    <td>eventTime</td>
	  <td>Indique la date et l'heure de création de l'événement. </br>La date est représentée en temps universel coordonné (UTC). </br>Le format respecte la norme ISO 8601.</td>
    <td>Par exemple : 2017-10-19T19:07:50.32+0000<td>
  </tr>
</table>

## Zones de résultat
{: #outcomes}

Le tableau suivant répertorie les zones de résultat communes disponibles pour un événement {{site.data.keyword.cloudaccesstrailshort}} :

<table>
  <caption>Zones de résultat communes</caption>
  <tr>
    <th>Nom de zone</th>
	  <th>Description</th>
    <th>Valeur</th>
  </tr>
  <tr>
    <td>outcome</td>
	  <td>Résultat de l'action. </td>
    <td>Les valeurs admises sont : *success*, *failure*, *pending*</td>
  </tr>
  <tr>
    <td>reason.reasonCode</td>
	  <td>Zone numérique qui inclut le code de réponse HTTP. </td>
    <td>Par exemple, *200* pour un succès.</td>
  </tr>
  <tr>
    <td>severity</td>
	  <td>Définit le niveau de menace qu'une action peut présenter sur le cloud. </td>
    <td>Les valeurs admises sont : *normal*, *warning* et *critical* </br></br>**Normal** est défini pour les actions de routine dans le cloud. Par exemple : démarrage d'une instance ou actualisation d'un jeton. </br></br>**Warning** est défini pour les actions où une ressource de cloud est mise à jour ou dont les métadonnées sont modifiées. Par exemple : mise à jour de la version d'un noeud worker, changement de nom d'un certificat ou d'une instance de service. </br></br>**Critical** est défini pour les actions qui affectent la sécurité du cloud. Par exemple : modification des données d'identification d'un utilisateur, suppression de données, accès non autorisé pour travailler avec une ressource de cloud. </td>
  </tr>
</table>
