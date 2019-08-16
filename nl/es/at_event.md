---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

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
{:deprecated: .deprecated}



# Campos de un suceso
{: #at_event}

Los sucesos de {{site.data.keyword.cloudaccesstrailshort}} se basan en el estándar Cloud Auditing Data Federation (CADF). 
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} está en desuso. A partir del 9 de mayo de 2019, no se pueden suministrar nuevas instancias de {{site.data.keyword.cloudaccesstrailshort}}. Las instancias existentes del plan premium recibirán soporte hasta el 30 de septiembre de 2019. Para seguir supervisando la actividad de la cuenta de {{site.data.keyword.cloud_notm}} suministre una instancia de [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}

## Campos del iniciador
{: #initiator}

La tabla siguiente contiene los campos comunes que están disponibles para un suceso de {{site.data.keyword.cloudaccesstrailshort}}:

| Nombre de campo | Descripción | Valor |
|------------|-------------|-------|
| `initiator.id` | ID del iniciador de la acción. </br></br>Los tipos válidos de iniciadores son `IBMID`, `serviceID` y `Cloud Foundry (CF) user ID`. | Un ejemplo de IBMID es `IBMid-000000XXX2` </br>Un ejemplo de ID de servicio es `iam-ServiceId-12345678-0165-4c89-847d-9660b1632e14` </br>Un ejemplo de ID de usuario de CF es `7666666b-23ae-4a34-8569-cu75tgdr4da3` |
| `initiator.name` | Nombre de usuario del usuario que ha iniciado la acción. | Por ejemplo, una dirección de correo electrónico. |
| `initiator.typeURI` | Tipo de origen del suceso. | Los valores válidos son *service/security/account/user*, *service/security/clientid* y *service/security/account/serviceid*. |
| `initiator.credential.type` | Tipo de credencial del ID de iniciador. | Los valores válidos son *user*, *token* y *apikey*. |
{: caption="Tabla 1. Campos comunes de iniciador" caption-side="top"} 

  

## Campos de destino
{: #target}

La tabla siguiente contiene los campos de destino comunes que están disponibles para un suceso de {{site.data.keyword.cloudaccesstrailshort}}:

| Nombre de campo | Descripción | Valor |
|------------|-------------|-------|
| `target.id` | Nombre del recurso de nube (CRN) del recurso en el que se ejecuta la acción. </br>Para obtener más información, consulte [Formato de CRN](/docs/overview?topic=overview-crn#format-crn). | Por ejemplo, `crn:v1:bluemix:public:cloud-object-storage:global:a/12345678e6232019c6567c9123456789:fr56et47-befb-440a-a223c-12345678dae1:bucket:bucket1` |
| `target.name` | Nombre legible por el usuario del recurso de nube en el que se ejecuta la acción. |  |
| `target.typeURI` | Tipo de recurso de nube en el que se ejecuta la acción. </br>El formato de este campo es **serviceName/objectType**, donde `servicename` es el nombre del servicio. | Por ejemplo, `iam-am/policy` o `cloud-object-storage/bucket/acl` |
{: caption="Tabla 2. Campos de destino comunes" caption-side="top"} 


 
## Campos de acción
{: #action}

La tabla siguiente contiene los campos de acción comunes que están disponibles para un suceso de {{site.data.keyword.cloudaccesstrailshort}}:

| Nombre de campo | Descripción | Valor |
|------------|-------------|-------|
| `action` | Acción que desencadena el suceso. </br>El formato de este campo es **serviceName.objectType.action**, donde `servicename` es el nombre del servicio. </br>Para obtener más información sobre los valores de acción para sucesos generados por un servicio, consulte <a href="/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-cloud_services#cloud_services">Servicios de nube</a> | Por ejemplo, `iam-identity.serviceid-apikey.login` |
| `eventTime` | Indicación de fecha y hora en que se ha creado el suceso. </br>La fecha se representa como Hora Universal Coordinada (UTC). </br>El formato cumple con ISO 8601. | Por ejemplo, `2017-10-19T19:07:50.32+0000` |
{: caption="Tabla 3. Campos de acción comunes" caption-side="top"} 



## Campos de resultados
{: #outcomes}

La tabla siguiente contiene los campos de resultado comunes que están disponibles para un suceso de {{site.data.keyword.cloudaccesstrailshort}}:

| Nombre de campo | Descripción | Valor |
|------------|-------------|-------|
| `outcome` | Resultado de la acción. | Los valores válidos son *success*, *failure* y *pending*. |
| `reason.reasonCode` | Campo numérico que incluye el código de respuesta de HTTP. | Por ejemplo, *200* para un resultado correcto. |
| `severity` | Define el nivel de amenaza que puede tener una acción en la nube. | Los valores válidos son *normal*, *warning* y *critical*. </br></br>**Normal** está definido para las acciones rutinarias en la nube. Por ejemplo, iniciar una instancia o renovar una señal. </br></br>**Warning** está definido para las acciones en las que se actualiza un recurso de la nube o se modifican sus metadatos. Por ejemplo, actualizar la versión de un nodo trabajador, cambiar el nombre de un certificado o cambiar el nombre de una instancia de servicio. </br></br>**Critical** está definido para las acciones que afectan a la seguridad en la nube. Por ejemplo, cambiar las credenciales de un usuario, suprimir datos o acceso no autorizado para trabajar con un recurso en la nube. |
{: caption="Tabla 4. Campos de resultados comunes" caption-side="top"} 


