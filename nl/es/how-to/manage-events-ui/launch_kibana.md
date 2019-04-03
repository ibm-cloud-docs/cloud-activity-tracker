---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, launch Kibana

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



# Apertura del panel de control de Kibana
{: #launch_kibana}

Puede lanzar Kibana desde la IU de {{site.data.keyword.cloudaccesstrailshort}} en {{site.data.keyword.cloud_notm}}, o directamente desde un navegador web.
{:shortdesc}
   

##  Apertura de Kibana desde el panel de control del servicio Activity Tracker
{: #launch_Kibana_from_at}

Los registros de actividad que muestra Kibana incluye sucesos para todos los recursos que se despliegan en el espacio de la organización de {{site.data.keyword.cloud_notm}} en la que ha iniciado sesión y en la que se ha suministrado el servicio de {{site.data.keyword.cloudaccesstrailshort}}.

Siga los siguientes pasos para iniciar Kibana desde el panel de control del servicio de {{site.data.keyword.cloudaccesstrailshort}}:

1. Inicie sesión en su cuenta de {{site.data.keyword.cloud_notm}}.

    Encontrará el panel de control de {{site.data.keyword.cloud_notm}} en: [https://cloud.ibm.com/login ![Icono de enlace externo](../../../icons/launch-glyph.svg "Icono de enlace externo")](https://cloud.ibm.com/login){:new_window}.
    
	Después de iniciar la sesión con su ID de usuario y contraseña, se abre la interfaz de usuario de {{site.data.keyword.cloud_notm}}.

2. Seleccione el servicio {{site.data.keyword.cloudaccesstrailshort}} en el panel de control de {{site.data.keyword.cloud_notm}}. 
    
3. Seleccione el separador **Gestionado**.

4. Para ver los sucesos del espacio, seleccione **Registros de espacio** en el campo *Ver registros*. **Nota:** esta es la vista predeterminada. A continuación, pulse **Ver en Kibana**. 

    Se abre el panel de control de Kibana. El panel de control **ActivityTracker_Space_Dashboard_in_24h** se carga con un filtro de tiempo establecido en las últimas 24 horas.

5. Para ver los sucesos de la cuenta, seleccione **Registros de cuenta** en el campo *Ver registros*. A continuación, pulse **Ver en Kibana**. 

    El panel de control **ActivityTracker_Account_Dashboard_in_24h** se carga con un filtro de tiempo establecido en las últimas 24 horas.
	
	
##  Apertura de Kibana desde un navegador web
{: #launch_Kibana_from_browser}

Siga los siguientes pasos para iniciar Kibana desde el navegador:

1. Abra un navegador web e inicie Kibana en la región en la que desea supervisar los sucesos. A continuación, inicie sesión en la interfaz de usuario de Kibana.
    
    Por ejemplo, la siguiente tabla enumera las URL que debe utilizar para iniciar Kibana por región:
      
    <table>
          <caption>Tabla 1. Las URL para iniciar Kibana por región</caption>
           <tr>
            <th>Región</th>
            <th>URL</th>
          </tr>
          <tr>
            <td>Alemania</td>
            <td>[https://logging.eu-fra.bluemix.net](https://logging.eu-fra.bluemix.net) </td>
          </tr>
          <tr>
            <td>Sídney</td>
            <td>[https://logging.au-syd.bluemix.net](https://logging.au-syd.bluemix.net) </td>
          </tr>
		  <tr>
            <td>Reino Unido</td>
            <td>[https://logging.eu-gb.bluemix.net](https://logging.eu-gb.bluemix.net)</td>
          </tr>
		  <tr>
            <td>EE. UU. sur</td>
            <td>[https://logging.ng.bluemix.net](https://logging.ng.bluemix.net) </td>
          </tr>
    </table>
	
	Se abre la página Descubrir en Kibana.
	
2. Compruebe que ha iniciado una sesión en la cuenta de {{site.data.keyword.cloud_notm}} donde quiere visualizar y analizar sucesos de actividad.

3. Visualizar sucesos de cuenta o espacio

* Pulse sobre la parte superior derecha de la ventana de Kibana donde aparezca su información de inicio de sesión.
* En **Dominio**, seleccione espacio o cuenta en el menú desplegable
* Para sucesos de espacio, seleccione el **espacio** de interés en el menú desplegable Espacio
* Para sucesos de cuenta, seleccione la **cuenta** correcta en el menú desplegable Cuenta

4. Ajustar tiempo de búsqueda

* El tiempo de búsqueda predeterminado de Kibana está establecido en los últimos 15 minutos.
* Pulse `Últimos 15 minutos` en la barra gris de la parte superior derecha
* Seleccione hasta cuánto tiempo hacia atrás desea poder ver los sucesos. Es posible buscar en los sucesos de los últimos 3 días. Elija un marco de tiempo de 3 días o menos.

5. Filtrar para mostrar solamente sucesos de Activity Tracker
* Puede que encuentre sucesos tanto de registros como de Activity Tracker cuando los visualice directamente en Kibana.
* En la barra de búsqueda, especifique `type:ActivityTracker` para mostrar únicamente los sucesos de Activity Tracker.

Los sucesos que se pueden ver en Kibana corresponden a los sucesos que están alojados en el dominio seleccionado en la región donde se ha iniciado Kibana.

## Limitaciones
{: #launch_kibana_limitations}

* Debido a limitaciones en Kibana, no puede tener varios separadores de Kibana abiertos al mismo tiempo en la misma sesión para ver distintos espacios o cuentas. Por lo tanto, si tienen dos o más sesiones abiertas a la vez, y cambia el dominio desde el espacio a la cuenta o viceversa, podría surgir algún problema.
* De forma predeterminada, únicamente el propietario de la cuenta puede visualizar sucesos de cuenta. Para permitir que otros puedan ver sucesos de cuenta, siga las instrucciones de
[Visualización de sucesos de cuenta](https://cloud.ibm.com/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-view_acc_events#view_acc_events).



