---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, events

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
{:deprecated: .deprecated}


# Sucesos de {{site.data.keyword.cloudaccesstrailshort}}
{: #events}

Utilice el servicio {{site.data.keyword.cloudaccesstrailfull}} para realizar el seguimiento de {{site.data.keyword.cloudaccesstrailshort}} en {{site.data.keyword.Bluemix}}. 
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} está en desuso. A partir del 9 de mayo de 2019, no se pueden suministrar nuevas instancias de {{site.data.keyword.cloudaccesstrailshort}}. Las instancias existentes del plan premium recibirán soporte hasta el 30 de septiembre de 2019. Para seguir supervisando la actividad de la cuenta de {{site.data.keyword.cloud_notm}} suministre una instancia de [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}


## Lista de sucesos
{: #actions}

En la tabla siguiente se muestran las acciones que generan un suceso:

<table>
  <caption>Tabla 1. Lista de acciones que generan un suceso</caption>
  <tr>
    <th>Acción</th>
	  <th>Descripción</th>
  <tr>
  <tr>
    <td>read.events</td>
	  <td>Obtener información acerca de los sucesos que se almacenan.</td>
  </tr>
  <tr>
    <td>create.sessions</td>
	  <td>Crear una sesión que se puede utilizar para descargar sucesos.</td>
  </tr>
  <tr>
    <td>delete.session</td>
	  <td>Suprimir una sesión.</td>
  </tr>
  <tr>
    <td>read.sessions</td>
	  <td>Listar las sesiones.</td>
  </tr>
  <tr>
    <td>download.events</td>
	  <td>Descargar sucesos.</td>
  </tr>
  <tr>
    <td>delete.events</td>
	  <td>Suprimir sucesos.</td>
  </tr>
</table>


## Dónde buscar los sucesos
{: #ui}
 	
Los sucesos de {{site.data.keyword.cloudaccesstrailshort}} están disponibles en el espacio de Cloud Foundry en el que se suministra el servicio {{site.data.keyword.cloudaccesstrailshort}}.
