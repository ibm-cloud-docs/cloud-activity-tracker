---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

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


# Sucesos de {{site.data.keyword.cloudaccesstrailshort}}
{: #events}

Utilice el servicio {{site.data.keyword.cloudaccesstrailfull}} para realizar el seguimiento de {{site.data.keyword.cloudaccesstrailshort}} en {{site.data.keyword.Bluemix}}. 
{:shortdesc}



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
