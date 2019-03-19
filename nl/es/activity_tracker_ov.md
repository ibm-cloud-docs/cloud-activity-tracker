---

copyright:
  years: 2016, 2019
lastupdated: "2019-02-18"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}



# Acerca de
{: #activity_tracker_ov}

Utilice el servicio de {{site.data.keyword.cloudaccesstrailfull}} para hacer un seguimiento de cómo interactúan las aplicaciones con los servicios de {{site.data.keyword.Bluemix}}. Utilice {{site.data.keyword.cloudaccesstrailshort}} para supervisar actividad anormal y cumplir con los requisitos de auditoría normativos. Los eventos que se han recopilado cumplen con la normativa de Cloud Auditing Data Federation (CADF).
{:shortdesc}

* {{site.data.keyword.cloudaccesstrailshort}} ofrece control de seguridad de alto nivel para los recursos de TI de la nube.
* {{site.data.keyword.cloudaccesstrailshort}} ofrece una solución para los administradores para capturar, almacenar, visualizar, buscar y controlar actividad de API en un mismo lugar.
* {{site.data.keyword.cloudaccesstrailshort}} proporciona capacidades para descargar eventos que puede utilizar para generar un informe de seguimiento de auditoría. Es posible que necesite estos informes para que la organización pueda cumplir con las normativas internas y con las normativas externas del sector y del país.

El cumplimiento de las políticas internas y de las normativas del sector es un requisito clave en la estrategia de cualquier organización, independientemente de dónde se ejecuten las aplicaciones: de forma local, en una nube híbrida o en una nube pública. El servicio {{site.data.keyword.cloudaccesstrailshort}} proporciona la infraestructura y la funcionalidad para supervisar llamadas API y generar un informe que demuestre el cumplimiento de las políticas corporativas y las normativas específicas del sector de mercado.

Cuando se trabaja en un entorno de nube, como {{site.data.keyword.cloud_notm}}, se debe planificar la estrategia de nube para auditar y supervisar las cargas de trabajo y los datos de acuerdo con las políticas internas y con los requisitos de cumplimiento de cada país. Puede utilizar la información que se registra a través del servicio {{site.data.keyword.cloudaccesstrailshort}} para identificar incidencias de seguridad, detectar accesos no autorizados y cumplir con la normativa y con los requisitos de auditoría.

Por ejemplo, puede utilizar los registros de actividad de {{site.data.keyword.cloudaccesstrailshort}} para identificar la siguiente información:

* Los usuarios que han realizado llamadas de API a servicios en la nube.
* La dirección IP de origen desde la que se han realizado las llamadas de API.
* La indicación de fecha y hora de realización de las llamadas de API.
* El estado de la llamada de API.


## Recopilación de sucesos
{: #activity_tracker_ov_collect}

El servicio de {{site.data.keyword.cloudaccesstrailshort}} solo captura los datos de actividad que están relacionados con las llamadas
API y otras acciones que se realizan en servicios en la nube seleccionados de {{site.data.keyword.cloud_notm}}. 

* Los sucesos se recopilan automáticamente. 
* Los sucesos que se recopilan en {{site.data.keyword.cloudaccesstrailshort}} cumplen con el estándar de Cloud Auditing Data Federation (CADF). El estándar CADF define un modelo de sucesos completo que incluye información necesaria para clarificar, gestionar y auditar la seguridad de las aplicaciones en entornos de nube.
* {{site.data.keyword.cloudaccesstrailshort}} almacena y agrupa sucesos por dominio. Hay un dominio de cuenta por región y un dominio de espacio por espacio de Cloud Foundry. 

El modelo de sucesos CADF incluye los siguientes componentes:

<table>
  <caption>Tabla 1. Componentes que están disponibles en el modelo de eventos CADF</caption>
  <tr>
    <th>Componente</th>
	<th>Descripción</th>
  </tr>
  <tr>
    <td>Acción</td>
	<td>La acción es la operación o la actividad que realiza el iniciador, que intenta realizar, o espera completar.</td>
  </tr>
  <tr>
    <td>Iniciador</td>
	<td>El iniciador es el recurso que realiza una llamada API y genera un suceso CADF. El suceso que se desencadena depende de la acción solicitada por la llamada de API.</td>
  </tr>
  <tr>
    <td>Observador</td>
	<td>El observador es el recurso que crea y almacena un registro CADF a partir de información disponible en un suceso CADF.</td>
  </tr>
  <tr>
    <td>Resultado</td>
	<td>El resultado es el estado de la acción frente al destino.</td>
  </tr>
  <tr>
    <td>Destino</td>
	<td>El destino es el recurso en el que se realiza o se intenta realizar la acción, o en el que está pendiente de completarse la acción.</td>
  </tr>
</table>


Considere la siguiente información cuando trabaje con el registro de {{site.data.keyword.cloudaccesstrailshort}} en la nube pública {{site.data.keyword.IBM_notm}}:

* Sólo puede almacenar registros de auditoría para llamadas de API realizadas a recursos que se ejecutan en la nube pública de {{site.data.keyword.IBM_notm}}.
* Sólo se utiliza la nube pública de almacenamiento {{site.data.keyword.IBM_notm}} para recopilar sucesos.
* La información se almacena durante 3 días. Una vez que ha transcurrido este tiempo, la información se elimina sobre la base de su antigüedad.
* Los eventos CADF del tipo *Actividad* están admitidos por el servicio {{site.data.keyword.cloudaccesstrailshort}}.


## Suministro de Activity Tracker
{: #activity_tracker_ov_provision}

Para ver los sucesos que están disponibles a través de un dominio de cuenta, debe suministrar el servicio {{site.data.keyword.cloudaccesstrailshort}} en un espacio de Cloud Foundry en la región en la que desea supervisar la actividad de la API. Solo el **propietario de la cuenta** puede ver los sucesos de la cuenta.

Para ver los sucesos que están disponibles a través de un dominio de espacio, debe suministrar el servicio {{site.data.keyword.cloudaccesstrailshort}} en el espacio en el que desea supervisar la actividad de la API.

Para aprender a suministrar el servicio {{site.data.keyword.cloudaccesstrailshort}}, consulte [Suministro del servicio {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/how-to/provision.html#provision).



## Análisis de registros de actividad
{: #activity_tracker_ov_analyze}

Puede analizar registros de actividad a través de la IU de {{site.data.keyword.cloudaccesstrailshort}} en {{site.data.keyword.cloud_notm}}, o utilizando Kibana, una herramienta de código abierto. Puede supervisar sucesos que están disponibles en un espacio específico o en el nivel de cuentas.

Puede buscar, analizar, y supervisar registros de actividad de las últimas 24 horas a través de la IU de {{site.data.keyword.cloudaccesstrailshort}} en {{site.data.keyword.cloud_notm}}. Para obtener más información, consulte [Navegación a la IU de {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_at_ui.html#launch_at_ui).

Puede buscar, analizar y supervisar los registros de actividad de los últimos 3 días a través de Kibana mediante el {{site.data.keyword.cloudaccesstrailshort}} panel de control de Kibana, o creando sus propios paneles de control personalizados. * **Nota:** Esta característica está disponible para los usuarios del plan **Premium**.

* Para obtener más información sobre cómo iniciar Kibana, consulte [Navegar al panel de control de Kibana](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_kibana.html#launch_kibana). 
* Para obtener una lista de campos que puede utilizar para analizar sucesos en Kibana, consulte [Campos de sucesos de {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/at_event.html#at_event)



## Regiones
{: #activity_tracker_ov_regions}

El servicio de {{site.data.keyword.cloudaccesstrailshort}} está disponible en las siguientes regiones:

* Alemania
* Sídney
* Reino Unido (solo está disponible el plan Lite)
* EE. UU. sur


## Plan de servicios
{: #activity_tracker_ov_plan}

El servicio {{site.data.keyword.cloudaccesstrailshort}} ofrece varios planes.

Puede cambiar un plan mediante la IU de {{site.data.keyword.cloud_notm}} o la línea de mandatos. Puede actualizar o reducir el plan en cualquier momento. Para obtener más información sobre actualizaciones del plan de servicio, consulte [Cambio del plan](/docs/services/cloud-activity-tracker/how-to/change_plan.html#change_plan). 

En la tabla siguiente se describen los planes disponibles:

<table>
    <caption>Tabla 1. Posibilidades para la ingestión, retención y exportación de sucesos</caption>
      <tr>
        <th>Plan</th>
        <th>Ingestión de sucesos</th>
        <th>Retención de sucesos</th>
		<th>Exportar sucesos</th>
      </tr>
      <tr>
        <td>Lite (predeterminado)</td>
        <td>No</td>
        <td>Últimos 3 días</td>
		<td>No</td>
      </tr>
      <tr>
        <td>Premium</td>
        <td>Sí</td>
        <td>Número de días que se puede configurar.</td>
		<td>Sí</td>
      </tr>
</table>

<table>
    <caption>Tabla 2. Posibilidades para gestionar y visualizar sucesos</caption>
      <tr>
        <th>Plan</th>
		    <th>API</th>
		    <th>CLI</th>
        <th>Kibana</th>
      </tr>
      <tr>
        <td>Lite (predeterminado)</td>
		    <td>No</td>
		    <td>No</td>
        <td>No</td>
      </tr>
      <tr>
        <td>Premium</td>
		    <td>Sí</td>
		    <td>Sí</td>
        <td>Sí</td>
      </tr>
</table>

**Nota:** El coste mensual del almacenamiento del suceso se calcula como un promedio del ciclo de facturación.

## Seguridad
{: #activity_tracker_ov_security}

Considere la siguiente información acerca de la seguridad cuando trabaje con el servicio {{site.data.keyword.cloudaccesstrailshort}}:

* Los servicios de IBM que generan sucesos de {{site.data.keyword.cloudaccesstrailshort}} siguen la política de seguridad {{site.data.keyword.IBM_notm}} Cloud. Para obtener más información, consulte [Confíe en la seguridad y privacidad de IBM Cloud ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/cloud-computing/learn-more/why-ibm-cloud/security/){: new_window}.
* El servicio {{site.data.keyword.cloudaccesstrailshort}} captura acciones iniciadas por el usuario que cambian el estado de los servicios en la nube. La información no ofrece acceso directo a las bases de datos ni a las aplicaciones.
* Sólo los usuarios autorizados pueden visualizar y supervisar los registros de sucesos de {{site.data.keyword.cloudaccesstrailshort}}. Cada usuario se identifica mediante un ID exclusivo en {{site.data.keyword.cloud_notm}}.
