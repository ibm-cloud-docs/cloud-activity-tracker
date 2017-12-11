---

copyright:
  years: 2016, 2017

lastupdated: "2017-09-18"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# Zones d'événement Activity Tracker
{: #at_event}

Les événements {{site.data.keyword.cloudaccesstrailshort}} sont conformes à la norme CADF (Cloud Auditing Data Federation).
{:shortdesc}

## Zones d'événement
{: #fields}

Le tableau suivant répertorie les zones disponibles pour analyse d'un événement {{site.data.keyword.cloudaccesstrailshort}} :

<table>
  <caption>Tableau 1. Zones disponibles pour une surveillance par événement.</caption>
  <tr>
    <th>Nom de zone</th>
	<th>Statut</th>
	<th>Description</th>
  </tr>
  <tr>
    <td>outcome</td>
	<td>Obligatoire</td>
	<td>Les valeurs admises sont : *success* et *failure*</td>
  </tr>
  <tr>
    <td>typeURI</td>
	<td>Obligatoire</td>
	<td>Cette zone est définie sur *http://schemas.dmtf.org/cloud/audit/1.0/event*</td>
  </tr>
  <tr>
    <td>eventType</td>
	<td>Obligatoire</td>
	<td>Cette zone est définie sur *activity*.</td>
  </tr>
  <tr>
    <td>eventTime</td>
	<td>Obligatoire</td>
	<td>(La date est représentée sous forme de chaîne ISO, par exemple : *2017-09-17 15:15:32.396 +0000 UTC*.</td>
  </tr>
  <tr>
    <td>action</td>
	<td>Obligatoire</td>
	<td>Cette zone indique l'action qui a déclenché l'événement, par exemple, *read.ibm-key-protect.secrets*.</td>
  </tr>
  <tr>
    <td>id</td>
	<td>Facultatif</td>
	<td>Cette zone contient l'identificateur unique universel (UUID) de l'événement.</td>
  </tr>
  <tr>
    <td>initiator.id</td>
	<td>Obligatoire</td>
	<td>Cette zone contient l'ID de la source de l'événement, par exemple un ID d'instance.</td>
  </tr>
  <tr>
    <td>initiator.name</td>
	<td>Facultatif</td>
	<td>Cette zone fournit un nom lisible de la source de l'événement, tel un ID utilisateur.</td>
  </tr>
  <tr>
    <td>initiator.typeURI</td>
	<td>Obligatoire</td>
	<td>Cette zone indique le type de la source de l'événement, par exemple, *service/security/account/user*</td>
  </tr>
  <tr>
    <td>initiator.host.agent</td>
	<td>Facultatif</td>
	<td>Cette zone désigne le client utilisé pour envoyer la demande, par exemple, *python-neutronclient* ou contient des informations de navigateur.</td>
  </tr>
  <tr>
    <td>initiator.host.address</td>
	<td>Facultatif</td>
	<td>Cette zone contient l'adresse IP de l'initiateur.</td>
  </tr>
  <tr>
    <td>target.id</td>
	<td>Obligatoire</td>
	<td>Cette zone contient l'ID du service cible.</td>
  </tr>
  <tr>
    <td>target.name</td>
	<td>Obligatoire</td>
	<td>Cette zone contient le nom lisible du service cible, par exemple, *ibm-key-protect*.</td>
  </tr>
  <tr>
    <td>target.typeURI</td>
	<td>Obligatoire</td>
	<td>Cette zone indique le type de la cible de l'événement, par exemple, *service/ibm-key-protect/secrets*.</td>
  </tr>
  <tr>
    <td>target.host.address</td>
	<td>Facultatif</td>
	<td>Cette zone contient l'adresse IP ou l'URL du service cible, par exemple, *xxx.bluemix.net*.</td>
  </tr>
  <tr>
    <td>observer.name</td>
	<td>Obligatoire</td>
	<td>Cette zone est définie sur *ActivityTracker*</td>
  </tr>
  <tr>
    <td>observer.id</td>
	<td>Obligatoire</td>
	<td>Cette zone contient des informations sur la ressource qui crée et stocke l'événement CADF, par exemple, *activitytracker.ng.bluemix.net*.</td>
  </tr>
  <tr>
    <td>observer.typeURI</td>
	<td>Obligatoire</td>
	<td>Cette zone est définie sur *service/security/edge/activity-tracker*</td>
  </tr>
  <tr>
    <td>reason.reasonCode</td>
	<td>Facultatif</td>
	<td>Cette zone contient le code de réponse HTTP, par exemple, *200* for success.</td>
  </tr>
  <tr>
    <td>reason.reasonType</td>
	<td>Obligatoire</td>
	<td>Cette zone contient des informations sur le code anomalie si celui-ci est fourni dans la zone *reason.reasonCode*.</td>
  </tr>
</table>

 

