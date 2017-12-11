---

copyright:
  years: 2016, 2017

lastupdated: "2017-09-17"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# Navegación al panel de control de Kibana 
{: #launch_kibana}

Puede lanzar Kibana desde la IU de {{site.data.keyword.cloudaccesstrailshort}} en {{site.data.keyword.Bluemix}}, o directamente desde un navegador web.
{:shortdesc}
   

##  Navegación a Kibana desde el panel de control del servicio de Activity Tracker 
{: #launch_Kibana_from_at}

Los registros de actividad que muestra Kibana incluye eventos para todos los recursos que se despliegan en el espacio de la organización de {{site.data.keyword.Bluemix_notm}} en la que ha iniciado sesión y en la que se ha suministrado el servicio de {{site.data.keyword.cloudaccesstrailshort}}.

Siga los siguientes pasos para iniciar Kibana desde el panel de control del servicio de {{site.data.keyword.cloudaccesstrailshort}}:

1. Inicie sesión en su cuenta de {{site.data.keyword.Bluemix_notm}}.

    El panel de control de {{site.data.keyword.Bluemix_notm}} se encuentra en: [http://bluemix.net ![Icono de enlace externo](../../../../icons/launch-glyph.svg "Icono de enlace externo")](http://bluemix.net){:new_window}.
    
	Después de iniciar la sesión con su ID de usuario y contraseña, se abre la interfaz de usuario de {{site.data.keyword.Bluemix_notm}}.

2. Seleccione el servicio {{site.data.keyword.cloudaccesstrailshort}} en el panel de control de {{site.data.keyword.Bluemix_notm}}. 
    
3. Seleccione el separador **Gestionado**.

4. Pulse **Vista avanzada**. 

    Se abre el panel de control de Kibana.

De forma predeterminada se carga un panel de control de **ActivityTracker_Space_Dashboard_in_24h**, y un filtro de tiempo se define en las últimas 24 horas. 


	
	
##  Navegación a Kibana desde un navegador web 
{: #launch_Kibana_from_browser}

La información de registro que muestra Kibana incluye eventos para todos los recursos que se muestran dentro del espacio de la organización de {{site.data.keyword.Bluemix_notm}} en la que ha iniciado sesión.

Siga los siguientes pasos para iniciar Kibana desde el navegador:

1. Abra un nuevo navegador web e inicie Kibana. A continuación, inicie sesión en la interfaz de usuario de Kibana.
    
    Por ejemplo, la siguiente tabla enumera las URL que debe utilizar para iniciar Kibana por región:
      
    <table>
          <caption>Tabla 1. Las URL para iniciar Kibana por región</caption>
           <tr>
            <th>Región</th>
            <th>URL</th>
          </tr>
          <tr>
            <td>EE.UU. sur</td>
            <td>[https://logging.ng.bluemix.net](https://logging.ng.bluemix.net) </td>
          </tr>
		  <tr>
            <td>Reino Unido</td>
            <td>[https://logmet.eu-gb.bluemix.net](https://logmet.eu-gb.bluemix.net)</td>
          </tr>
    </table>
	
	Se abre la página Descubrir en Kibana opens.
	
2. Compruebe que ha iniciado sesión en la cuenta, organización y espacio de {{site.data.keyword.Bluemix_notm}}, donde quiere visualizar y analizar registros de actividad.

    Puede visualizar sucesos y registros que están disponibles en el espacio donde está conectado.

3. Para filtrar por sucesos, seleccione **Abrir** desde la barra del menú.

    Se muestra la lista de paneles de control guardados.
	
4. Para visualizar los eventos para el espacio en el que ha iniciado sesión, seleccione **ActivityTracker_Space_Dashboard_in_24h**.


## Limitaciones
{: #limitations}

 Debido a limitaciones en Kibana, no puede tener varios separadores de Kibana abiertos al mismo tiempo en la misma sesión para ver distintos espacios o cuentas. Por lo tanto, si tienen dos o más sesiones abiertas a la vez, y cambia el dominio desde el espacio a la cuenta o viceversa, podría surgir algún problema.
	



