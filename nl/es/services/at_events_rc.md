---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, resource controller events

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

# Sucesos de instancia de servicio  
{: #at_events_rc}

Como agente de seguridad, auditor o gestor, puede utilizar el servicio {{site.data.keyword.cloudaccesstrailfull}} para realizar un seguimiento de cómo interactúan los usuarios y las aplicaciones con los servicios de {{site.data.keyword.Bluemix}}. 
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} está en desuso. A partir del 9 de mayo de 2019, no se pueden suministrar nuevas instancias de {{site.data.keyword.cloudaccesstrailshort}}. Las instancias existentes del plan premium recibirán soporte hasta el 30 de septiembre de 2019. Para seguir supervisando la actividad de la cuenta de {{site.data.keyword.cloud_notm}} suministre una instancia de [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}

El servicio {{site.data.keyword.cloudaccesstrailfull_notm}} registra las actividades iniciadas por el usuario que cambian el estado de un servicio en {{site.data.keyword.cloud_notm}}. Para obtener más información, consulte [Acerca de {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov).

Para empezar a supervisar las acciones del usuario, consulte [{{site.data.keyword.cloudaccesstrailfull_notm}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started-with-cla#getting-started-with-cla). 


## Sucesos para el suministro y la gestión de instancias de servicio
{: #at_events_rc_provision}

En la tabla siguiente se muestran los métodos de API que generan un suceso cuando se le llama:

<table>
  <caption>Acciones que generan sucesos</caption>
  <tr>
    <th>Acción</th>
	  <th>Descripción</th>
  </tr>
  <tr>
    <td><i>service_name</i>.instance.create</td>
	  <td>Se genera un suceso cuando se suministra una instancia de servicio.</td>
  </tr>
  <tr>
    <td><i>service_name</i>.instance.update</td>
	  <td>Se genera un suceso cuando se cambia el nombre de una instancia de servicio o cuando se cambia el plan de servicio.</td>
  </tr>
  <tr>
    <td><i>service_name</i>.instance.delete</td>
	  <td>Se genera un suceso cuando se suprime una instancia de servicio.</td>
  </tr>
</table>


##  Sucesos para gestionar las claves de API que están asociadas a una instancia de servicio
{: #at_events_rc_keys}

En la tabla siguiente se muestran los métodos de API que generan un suceso cuando se le llama:

<table>
  <caption>Acciones que generan sucesos</caption>
  <tr>
    <th>Acción</th>
	  <th>Descripción</th>
  </tr>
  <tr>
    <td><i>service_name</i>.key.create</td>
	  <td>Se genera un suceso cuando se crea una clave de API para una instancia de servicio a través de la sección *Credenciales de servicio* de la interfaz de usuario de la instancia de servicio.</td>
  </tr>
  <tr>
    <td><i>service_name</i>.key.delete</td>
	  <td>Se genera un suceso cuando una clave de API asociada con una instancia de servicio se suprime desde la sección *Credenciales de servicio* de la interfaz de usuario de la instancia de servicio.</td>
  </tr>
</table>

##  Sucesos para enlazar una instancia de servicio con una app
{: #at_events_rc_bind}

En la tabla siguiente se muestran los métodos de API que generan un suceso cuando se le llama:

<table>
  <caption>Acciones que generan sucesos</caption>
  <tr>
    <th>Acción</th>
	  <th>Descripción</th>
  </tr>
  <tr>
    <td><i>service_name</i>.binding.create</td>
	  <td>Se genera un suceso cuando se enlaza una instancia de servicio a una aplicación.</td>
  </tr>
  <tr>
    <td><i>service_name</i>.binding.delete</td>
	  <td>Se genera un suceso cuando se elimina el enlace de una instancia de servicio de una aplicación.</td>
  </tr>
</table>




## Dónde buscar los sucesos
{: #at_events_rc_ui}

Los sucesos de {{site.data.keyword.cloudaccesstrailshort}} están disponibles en el **dominio de cuenta** de la región **EE. UU. sur**.

Para ver estos sucesos, debe suministrar una instancia del servicio {{site.data.keyword.cloudaccesstrailshort}} en la región **EE. UU. sur**. A continuación, debe abrir la interfaz de usuario de {{site.data.keyword.cloudaccesstrailshort}} y cambiar al dominio de cuenta para ver los sucesos. 

Para obtener más información, consulte [Visualización de sucesos de cuenta](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-view_acc_events#view_acc_events_account_events).



