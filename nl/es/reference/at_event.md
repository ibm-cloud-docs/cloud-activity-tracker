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


# Cambios de sucesos de Activity Tracker
{: #at_event}

Los sucesos de {{site.data.keyword.cloudaccesstrailshort}} se basan en el estándar Cloud Auditing Data Federation (CADF).
{:shortdesc}

## Campos de un suceso
{: #fields}

La tabla siguiente contiene los campos que están disponibles para el análisis de un suceso de {{site.data.keyword.cloudaccesstrailshort}}: 

<table>
  <caption>Tabla 1. Campos que están disponibles para la supervisión por suceso. </caption>
  <tr>
    <th>Nombre de campo</th>
	<th>Estado</th>
	<th>Descripción</th>
  </tr>
  <tr>
    <td>outcome</td>
	<td>Obligatorio</td>
	<td>Los valores válidos son: *success*, *failure*</td>
  </tr>
  <tr>
    <td>typeURI</td>
	<td>Obligatorio</td>
	<td>Este campo está establecido en: *http://schemas.dmtf.org/cloud/audit/1.0/event*</td>
  </tr>
  <tr>
    <td>eventType</td>
	<td>Obligatorio</td>
	<td>Este campo está establecido en *activity*.</td>
  </tr>
  <tr>
    <td>eventTime </td>
	<td>Obligatorio</td>
	<td>(La fecha se representa como una serie ISO, por ejemplo: *2017-09-17 15:15:32.396 +0000 UTC*.</td>
  </tr>
  <tr>
    <td>action</td>
	<td>Obligatorio</td>
	<td>Este campo indica la acción que ha activado el suceso, por ejemplo *read.ibm-key-protect.secrets*.</td>
  </tr>
  <tr>
    <td>id</td>
	<td>Opcional</td>
	<td>Este campo contiene el UUID del suceso.</td>
  </tr>
  <tr>
    <td>initiator.id</td>
	<td>Obligatorio</td>
	<td>Este campo contiene el ID del origen del suceso, como por ejemplo un ID de instancia.</td>
  </tr>
  <tr>
    <td>initiator.name</td>
	<td>Opcional</td>
	<td>Este campo proporciona un nombre legible para el origen del suceso, como por ejemplo un ID de usuario.</td>
  </tr>
  <tr>
    <td>initiator.typeURI</td>
	<td>Obligatorio</td>
	<td>Este campo informa sobre el tipo de origen del suceso, por ejemplo *service/security/account/user*</td>
  </tr>
  <tr>
    <td>initiator.host.agent</td>
	<td>Opcional</td>
	<td>Este campo indica el cliente que se ha utilizado para enviar la solicitud, por ejemplo *python-neutronclient* o información del navegador.</td>
  </tr>
  <tr>
    <td>initiator.host.address</td>
	<td>Opcional</td>
	<td>Este campo incluye la dirección IP del iniciador.</td>
  </tr>
  <tr>
    <td>target.id</td>
	<td>Obligatorio</td>
	<td>Este campo incluye el ID del servicio de destino.</td>
  </tr>
  <tr>
    <td>target.name</td>
	<td>Obligatorio</td>
	<td>Este campo incluye el nombre legible del servicio de destino, por ejemplo *ibm-key-protect*.</td>
  </tr>
  <tr>
    <td>target.typeURI</td>
	<td>Obligatorio</td>
	<td>Este campo incluye el tipo de destino del suceso, por ejemplo *service/ibm-key-protect/secrets*.</td>
  </tr>
  <tr>
    <td>target.host.address</td>
	<td>Opcional</td>
	<td>Este campo incluye la dirección IP o URL del servicio de destino, por ejemplo *xxx.bluemix.net*.</td>
  </tr>
  <tr>
    <td>observer.name</td>
	<td>Obligatorio</td>
	<td>Este campo está establecido en el valor siguiente: *ActivityTracker*</td>
  </tr>
  <tr>
    <td>observer.id</td>
	<td>Obligatorio</td>
	<td>Este campo incluye información sobre el recurso que crea y almacena el suceso CADF, por ejemplo *activitytracker.ng.bluemix.net*.</td>
  </tr>
  <tr>
    <td>observer.typeURI</td>
	<td>Obligatorio</td>
	<td>Este campo está establecido en el valor siguiente: *service/security/edge/activity-tracker*</td>
  </tr>
  <tr>
    <td>reason.reasonCode</td>
	<td>Opcional</td>
	<td>Este campo incluye el código de razón de HTTP, por ejemplo *200* indica éxito. </td>
  </tr>
  <tr>
    <td>reason.reasonType</td>
	<td>Obligatorio</td>
	<td>Este campo incluye información sobre el código de razón cuando se proporciona uno mediante el campo *reason.reasonCode*. </td>
  </tr>
</table>

 

