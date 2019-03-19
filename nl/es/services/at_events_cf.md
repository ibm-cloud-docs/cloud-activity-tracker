---

copyright:
  years: 2016, 2019
lastupdated: "2019-01-23"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# Sucesos de Cloud Foundry
{: #cf}

Utilice el servicio {{site.data.keyword.cloudaccesstrailfull}} para realizar un seguimiento de la interacción con los servicios básicos de la plataforma en {{site.data.keyword.Bluemix}}. 
{:shortdesc}


En la siguiente lista se describen las distintas tareas básicas de la plataforma que envían sucesos al servicio {{site.data.keyword.cloudaccesstrailshort}}: 

* Suministro de un servicio, eliminación de un servicio y cambio del nombre de un servicio.
* Concesión, actualización y revocación de roles de espacio de Cloud Foundry a los usuarios de la cuenta.
* Creación de una clave de API de la plataforma, cambio de nombre de una clave de la plataforma y supresión de una clave de la plataforma.


## Sucesos generados cuando se interactúa con los servicios de catálogo
{: #cf_catalog}

Cuando suministra un servicio, elimina un servicio o cambia el nombre de un servicio, se genera un suceso y se envía al dominio del espacio en {{site.data.keyword.cloudaccesstrailshort}} que está asociado al espacio de Cloud Foundry en el que está disponible el servicio en la cuenta. 

Por ejemplo, supongamos que suministra el servicio A en el espacio B en la región EE. UU. sur. Se genera un suceso. Para ver el suceso, debe suministrar el servicio {{site.data.keyword.cloudaccesstrailshort}} en la región EE. UU. sur, en el mismo espacio en el que ha suministrado el servicio. A continuación, puede ver el suceso a través de la interfaz de usuario del servicio {{site.data.keyword.cloudaccesstrailshort}}.

En la tabla siguiente se muestran las acciones de catálogo que generan sucesos:

<table>
  <caption>Acciones de catálogo</caption>
  <tr>
    <th>Acción</th>
	  <th>Descripción</th>
  <tr>
  <tr>
    <td>`audit.service_instance.create`</td>
	<td>Se crea un suceso cuando se suministra un servicio en un espacio de Cloud Foundry.</td>
  </tr>
  <tr>
    <td>`audit.service_instance.update`</td>
	<td>Se crea un suceso cuando se cambia el nombre de un servicio que está disponible en un espacio de Cloud Foundry.</td>
  </tr>
  <tr>
    <td>`audit.service_instance.delete`</td>
	<td>Se crea un suceso cuando se elimina un servicio de un espacio de Cloud Foundry de la cuenta.</td>
  </tr>
</table>


 	

## Sucesos generados al gestionar roles de Cloud Foundry en la cuenta
{: #cf_cfroles} 

Cuando otorga o revoca (suprime) un rol de Cloud Foundry a un usuario de la cuenta, se genera un suceso y se envía al dominio de espacio en {{site.data.keyword.cloudaccesstrailshort}} que está asociado con el espacio de Cloud Foundry en el que se otorga o se revoca el rol. 

Por ejemplo, supongamos que otorga a un usuario A en el espacio B en la región EE. UU. sur un rol de *gestor de espacio*. Se genera un suceso. Para ver el suceso, debe suministrar el servicio {{site.data.keyword.cloudaccesstrailshort}} en la región EE. UU. sur, en el mismo espacio en el que está gestionando los permisos de CF del usuario. A continuación, puede ver el suceso a través de la interfaz de usuario del servicio {{site.data.keyword.cloudaccesstrailshort}}.


En la tabla siguiente se muestran las acciones que generan sucesos de {{site.data.keyword.cloudaccesstrailshort}} cuando se gestionan los roles de Cloud Foundry de un usuario:

<table>
  <caption>Acciones de gestión de roles de Cloud Foundry</caption>
  <tr>
    <th>Acción</th>
	<th>Descripción</th>
  <tr>
  <tr>
    <td>`audit.user.space_manager_add`</td>
	<td>Otorgar a un usuario el rol de *gestor* en un espacio de Cloud Foundry.</td>
  </tr>
  <tr>
    <td>`audit.user.space_developer_add`</td>
	<td>Otorgar a un usuario el rol de *desarrollador* en un espacio de Cloud Foundry.</td>
  </tr>
  <tr>
    <td>`audit.user.space_auditor_add`</td>
	<td>Otorgar a un usuario el rol de *auditor* en un espacio de Cloud Foundry.</td>
  </tr>
  <tr>
    <td>`audit.user.space_manager_remove`</td>
	<td>Suprimir el rol de *gestor* del usuario en un espacio de Cloud Foundry.</td>
  </tr>
  <tr>
    <td>`audit.user.space_developer_remove`</td>
	<td>Suprimir el rol de *desarrollador* del usuario en un espacio de Cloud Foundry.</td>
  </tr>
  <tr>
    <td>`audit.user.space_auditor_remove`</td>
	<td>Suprimir el rol de *auditor* del usuario en un espacio de Cloud Foundry.</td>
  </tr>
</table>






	
 	
 	
