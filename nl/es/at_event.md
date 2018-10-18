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



# Cambios de sucesos de Activity Tracker
{: #at_event}

Los sucesos de {{site.data.keyword.cloudaccesstrailshort}} se basan en el estándar Cloud Auditing Data Federation (CADF). 
{:shortdesc}

## Campos del iniciador
{: #initiator}

La tabla siguiente contiene los campos comunes que están disponibles para un suceso de {{site.data.keyword.cloudaccesstrailshort}}:

<table>
  <caption>Campos comunes del iniciador</caption>
  <tr>
    <th>Nombre de campo</th>
	  <th>Descripción</th>
    <th>Valor</th>
  </tr>
  <tr>
    <td>initiator.id</td>
	  <td>ID del iniciador de la acción. </br>Hay dos tipos de iniciadores: IBMID y serviceID (ID de servicio).</td>
    <td>Ejemplo de un IBMID: IBMid-000000XXX2 </br>Ejemplo de un ID de servicio: iam-ServiceId-12345678-0165-4c89-847d-9660b1632e14</td>
  </tr>
  <tr>
    <td>initiator.name</td>
	  <td>Nombre de usuario del usuario que ha iniciado la acción.</td>
    <td></td>
  </tr>
  <tr>
    <td>initiator.typeURI</td>
	  <td>Tipo de origen del suceso.</td>
    <td>Los valores válidos son: *service/security/account/user*, *service/security/clientid*, *service/security/account/serviceid*</td>
  </tr>
  <tr>
    <td>initiator.credential.type</td>
	  <td>Tipo de credencial del ID de iniciador. </td>
    <td>Los valores válidos son: *user*, *token*, *apikey*</td>
  </tr>
</table>

## Campos de destino
{: #target}

La tabla siguiente contiene los campos de destino comunes que están disponibles para un suceso de {{site.data.keyword.cloudaccesstrailshort}}:

<table>
  <caption>Campos de destino comunes</caption>
  <tr>
    <th>Nombre de campo</th>
	  <th>Descripción</th>
    <th>Valor</th>
  </tr>
  <tr>
    <td>target.id</td>
	  <td>Nombre del recurso de nube (CRN) del recurso en el que se ejecuta la acción. </br>Para obtener más información, consulte [Formato de CRN](/docs/overview/crn.html#format).</td>
    <td>Por ejemplo: `crn:v1:bluemix:public:cloud-object-storage:global:a/12345678e6232019c6567c9123456789:fr56et47-befb-440a-a223c-12345678dae1:bucket:bucket1`</td>
  </tr>
  <tr>
    <td>target.name</td>
	  <td>Nombre legible por el usuario del nombre del recurso de nube en el que se ejecuta la acción.</td>
    <td></td>
  </tr>
  <tr>
    <td>target.typeURI</td>
    <td>Tipo de recurso de nube en el que se ejecuta la acción. </br>El formato del campo es **serviceName/objectType**, donde servicename es el nombre del servicio. </td>
	  <td>Por ejemplo: `iam-am/policy` o `cloud-object-storage/bucket/acl`</td>
  </tr>
</table>
 
## Campos de acción
{: #action}

La tabla siguiente contiene los campos de acción comunes que están disponibles para un suceso de {{site.data.keyword.cloudaccesstrailshort}}:

<table>
  <caption>Campos de acción comunes</caption>
  <tr>
    <th>Nombre de campo</th>
	  <th>Descripción</th>
    <th>Valor</th>
  </tr>
  <tr>
    <td>action</td>
	  <td>Acción que desencadena el suceso. </br>El formato del campo es **serviceName.objectType.action**, donde servicename es el nombre del servicio. </br>Para obtener información sobre los sucesos generados por un servicio, consulte <a href="/docs/services/cloud-activity-tracker/cloud_services.html#cloud_services">Servicios de nube</a></td>
    <td>Por ejemplo: *iam-identity.serviceid-apikey.login*</td>
  </tr>
  <tr>
    <td>eventTime</td>
	  <td>Indicación de fecha y hora en que se ha creado el suceso. </br>La fecha se representa como Hora Universal Coordinada (UTC). </br>El formato cumple con ISO 8601.</td>
    <td>Por ejemplo: 2017-10-19T19:07:50.32+0000<td>
  </tr>
</table>

## Campos de resultados
{: #outcomes}

La tabla siguiente contiene los campos de resultados comunes que están disponibles para un suceso de {{site.data.keyword.cloudaccesstrailshort}}:

<table>
  <caption>Campos de resultados comunes</caption>
  <tr>
    <th>Nombre de campo</th>
	  <th>Descripción</th>
    <th>Valor</th>
  </tr>
  <tr>
    <td>outcome</td>
	  <td>Resultado de la acción. </td>
    <td>Los valores válidos son: *success*, *failure*, *pending*</td>
  </tr>
  <tr>
    <td>reason.reasonCode</td>
	  <td>Campo numérico que incluye el código de respuesta de HTTP. </td>
    <td>Por ejemplo, *200* para un resultado correcto.</td>
  </tr>
  <tr>
    <td>severity</td>
	  <td>Define el nivel de amenaza que puede tener una acción en la nube.  </td>
    <td>Los valores válidos son: *normal*, *warning* y *critical* </br></br>**Normal** está definido para las acciones rutinarias en la nube. Por ejemplo, iniciar una instancia o renovar una señal. </br></br>**Warning** está definido para las acciones en las que se actualiza un recurso de la nube o se modifican sus metadatos. Por ejemplo, actualizar la versión de un nodo trabajador, cambiar el nombre de un certificado o cambiar el nombre de una instancia de servicio. </br></br>**Critical** está definido para las acciones que afectan a la seguridad en la nube. Por ejemplo, cambiar las credenciales de un usuario, suprimir datos o acceso no autorizado para trabajar con un recurso en la nube. </td>
  </tr>
</table>
