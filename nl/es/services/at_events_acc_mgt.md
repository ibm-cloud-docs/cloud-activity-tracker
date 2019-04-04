---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, account events

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

# Sucesos de gestión de cuentas  
{: #at_events_acc_mgt}

Como agente de seguridad, auditor o gestor, puede utilizar el servicio {{site.data.keyword.cloudaccesstrailfull}} para realizar un seguimiento de cómo interactúan los usuarios y las aplicaciones con la cuenta de {{site.data.keyword.Bluemix}}. 
{:shortdesc}

El servicio {{site.data.keyword.cloudaccesstrailfull_notm}} registra las actividades iniciadas por el usuario que cambian el estado de un servicio en {{site.data.keyword.cloud_notm}}. Para obtener más información, consulte [Acerca de {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov).

Para empezar a supervisar las acciones del usuario, consulte [{{site.data.keyword.cloudaccesstrailfull_notm}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started-with-cla#getting-started-with-cla). 



## Sucesos para gestionar cuentas
{: #at_events_acc_mgt_account}

En la tabla siguiente se muestran el método de API que genera un suceso cuando se le llama:

<table>
  <caption>Acciones que generan sucesos</caption>
  <tr>
    <th>Acción</th>
	  <th>Descripción</th>
  </tr>
  <tr>
    <td>billing.account.create</td>
	  <td>Se genera un suceso cuando se proporciona una cuenta, después de que el ID de cuenta se haya asignado a la cuenta.</td>
  </tr>
  <tr>
    <td>billing.account.update</td>
	  <td>Se genera un suceso cuando se actualiza la información sobre la cuenta.</td>
  </tr>
  <tr>
    <td>billing.account.active</td>
	  <td>Se genera un suceso cuando se verifica la cuenta, es decir, se genera un suceso cuando la cuenta pasa a estar activa.</td>
  </tr>
  <tr>
    <td>billing.account.subscription.create</td>
	  <td>Se genera un suceso cuando se crea una <a href="/docs/account?topic=account-accounts#subscription-account">cuenta de suscripción</a>.</td>
  </tr>
</table>



## Sucesos para gestionar usuarios
{: #at_events_acc_mgt_users}

En la tabla siguiente se muestran el método de API que genera un suceso cuando se le llama:

<table>
  <caption>Acciones que generan sucesos</caption>
  <tr>
    <th>Acción</th>
	  <th>Descripción</th>
  </tr>
  <tr>
    <td>user-management.user.create</td>
	  <td>Se genera un suceso cuando se envía una invitación a un usuario para que se una a una cuenta. </br>El propietario de la cuenta es el único usuario de la cuenta que puede realizar esta acción.</td>
  </tr>
  <tr>
    <td>user-management.user.active</td>
	  <td>Se genera un suceso cuando se activa el usuario en la cuenta. </br>Cuando el usuario verifica su dirección de correo electrónico, se genera el suceso.</td>
  </tr>
  <tr>
    <td>user-management.account.user.delete</td>
	  <td>Se genera un suceso cuando se elimina un usuario de la cuenta. </br>El propietario de la cuenta es el único usuario de la cuenta que puede realizar esta acción.</td>
  </tr>
</table>

## Sucesos para gestionar organizaciones
{: #at_events_acc_mgt_org}

En la tabla siguiente se muestran el método de API que genera un suceso cuando se le llama:

<table>
  <caption>Acción que genera sucesos</caption>
  <tr>
    <th>Acción</th>
	  <th>Descripción</th>
  </tr>
  <tr>
    <td>billing.account.org.create</td>
	  <td>Se genera un suceso cuando se añade una organización a la cuenta.</td>
  </tr>
</table>

## Dónde buscar los sucesos
{: #at_events_acc_mgt_ui}

Los sucesos de {{site.data.keyword.cloudaccesstrailshort}} están disponibles en el **dominio de cuenta** de la región **EE. UU. sur**. 

Para ver estos sucesos, debe suministrar una instancia del servicio {{site.data.keyword.cloudaccesstrailshort}} en la región **EE. UU. sur**. A continuación, debe abrir la interfaz de usuario de {{site.data.keyword.cloudaccesstrailshort}} y cambiar al dominio de cuenta para ver los sucesos. 

Para obtener más información, consulte [Visualización de sucesos de cuenta](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-view_acc_events#view_acc_events_account_events).








