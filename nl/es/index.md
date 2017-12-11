---

copyright:
  years: 2016, 2017
lastupdated: "2017-09-17"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Guía de aprendizaje de iniciación
{: #getting-started-with-cla}

El servicio {{site.data.keyword.cloudaccesstrailfull}} registra las actividades iniciadas por el usuario que cambian el estado de un servicio en la nube de {{site.data.keyword.IBM}}. Utilice esta guía de aprendizaje para aprender a utilizar el servicio {{site.data.keyword.cloudaccesstrailfull}} para supervisar la interacción de un usuario con un servicio en la nube. {:shortdesc}

Los objetivos de esta guía de iniciación son los siguientes:

1. Mostrar cómo se suministra el servicio {{site.data.keyword.cloudaccesstrailshort}}.
2. Mostrar cómo se utiliza un servicio en la nube para generar sucesos de actividad que el servicio {{site.data.keyword.cloudaccesstrailshort}} recopila automáticamente. Los sucesos cumplen con el estándar de Cloud Auditing Data Federation (CADF). 
3. Mostrar cómo se supervisa la actividad en la nube de un servicio mediante los paneles de control predefinidos de {{site.data.keyword.cloudaccesstrailshort}}. 

En la figura siguiente se muestran los distintos componentes y acciones que se producen cuando una actividad iniciada por el usuario cambia el estado de un servicio:

![Componentes y acciones que se producen cuando una actividad iniciada por el usuario cambia el estado de un servicio](images/AT_f1.png "Componentes y acciones que se producen cuando una actividad iniciada por el usuario cambia el estado de un servicio")



## Antes de empezar
{: #prereqs}

Cree una cuenta de [{{site.data.keyword.Bluemix_notm}}](https://console.bluemix.net/registration/). El ID de usuario debe ser miembro o propietario de una cuenta de {{site.data.keyword.Bluemix_notm}}, con permisos de desarrollador en el espacio donde piensa utilizar el servicio {{site.data.keyword.cloudaccesstrailshort}}.


## Paso 1: Suministrar Activity Tracker
{: #step1}

Debe suministrar el servicio {{site.data.keyword.cloudaccesstrailshort}} en la misma región y espacio donde se suministra el servicio de nube cuya actividad desea supervisar. Una vez suministrado el servicio {{site.data.keyword.cloudaccesstrailshort}}, los sucesos se recopilan automáticamente de los servicios de la nube seleccionados que se suministran en ese espacio. Consulte [Servicios de nube soportados](/docs/services/cloud-activity-tracker/cloud_services.html#cloud_services) para ver una lista de servicios cuya actividad puede supervisar mediante {{site.data.keyword.cloudaccesstrailshort}}.

**Nota:** En esta guía de aprendizaje se muestra cómo utilizar el servicio {{site.data.keyword.cloudaccesstrailshort}} para supervisar la interacción de un usuario con el servicio de nube {{site.data.keyword.keymanagementservicelong_notm}}. El servicio {{site.data.keyword.keymanagementserviceshort}} está disponible en EE.UU. sur. Por lo tanto, debe suministrar {{site.data.keyword.cloudaccesstrailshort}} en la región EE.UU. sur, en el mismo espacio donde está disponible el servicio {{site.data.keyword.keymanagementserviceshort}}. Para ver información sobre la región en que un servicio está disponible, consulte [Servicios por región](/docs/services/services_region.html#services_region).

Siga los pasos siguientes para suministrar una instancia del servicio {{site.data.keyword.cloudaccesstraillong_notm}} en {{site.data.keyword.Bluemix_notm}}:

1. Inicie sesión en su cuenta de {{site.data.keyword.Bluemix_notm}}.

    El panel de control de {{site.data.keyword.Bluemix_notm}} se encuentra en: [http://bluemix.net ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://bluemix.net){:new_window}.
    
	Después de iniciar la sesión con su ID de usuario y contraseña, se abre la interfaz de usuario de {{site.data.keyword.Bluemix_notm}}.

2. Pulse **Catálogo**. Se abre la lista de los servicios que están disponibles en {{site.data.keyword.Bluemix_notm}}.  

3. Seleccione la categoría **Seguridad** para filtrar la lista de servicios que se muestran.

4. Pulse el mosaico **Acivity Tracker**. 

5. Configure la información que define dónde se va a suministrar el servicio.  

    Especifique los datos como se indica en la tabla siguiente: 

    <table>
	  <caption>Tabla 1. Campos obligatorios para suministrar el servicio {{site.data.keyword.cloudaccesstrailshort}}</caption>
	  <tr>
	    <th width="50%">Campo</th>
		<th width="50%">Valor</th>
	  </tr>
	  <tr>
	    <td>Seleccione la región de despliegue:</td>
		<td>EE.UU. sur</td>
	  </tr>
	  <tr>
	    <td>Elija una organización:</td>
		<td>Seleccione la organización donde piensa supervisar la actividad.</td>
	  </tr>
	  <tr>
	    <td>Elija un espacio:</td>
		<td>Seleccione el espacio de la organización que ha seleccionado donde piensa supervisar la actividad.</td>
	  </tr>
	</table>

6. Pulse **Crear** para suministrar el servicio {{site.data.keyword.cloudaccesstrailshort}} en el espacio de {{site.data.keyword.Bluemix_notm}} en el que ha iniciado la sesión.
   

## Paso 2: Suministrar un servicio en la nube 
{: #step2}
	
Siga los pasos siguientes para suministrar una instancia del servicio {{site.data.keyword.keymanagementserviceshort}} en la región EE.UU. sur de {{site.data.keyword.Bluemix_notm}}:

1. Inicie sesión en su cuenta de {{site.data.keyword.Bluemix_notm}}.

    El panel de control de {{site.data.keyword.Bluemix_notm}} se encuentra en: [http://bluemix.net ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://bluemix.net){:new_window}.
	
	Después de iniciar la sesión con su ID de usuario y contraseña, se abre la interfaz de usuario de {{site.data.keyword.Bluemix_notm}}.

2. Pulse **Catálogo**. Se abre la lista de los servicios que están disponibles en {{site.data.keyword.Bluemix_notm}}.  

    Seleccione la categoría **Seguridad** para filtrar la lista de servicios que se muestran.

3. Seleccione el mosaico **Key Protect**.

4. Configure la información que define dónde se va a suministrar el servicio.  

    Especifique los datos como se indica en la tabla siguiente: 

    <table>
	  <caption>Tabla 2. Campos obligatorios para suministrar el servicio {{site.data.keyword.keymanagementserviceshort}}</caption>
	  <tr>
	    <th width="50%">Campo</th>
		<th width="50%">Valor</th>
	  </tr>
	  <tr>
	    <td>Seleccione la región de despliegue:</td>
		<td>EE.UU. sur</td>
	  </tr>
	  <tr>
	    <td>Elija una organización:</td>
		<td>Seleccione la organización que ha elegido para suministrar el servicio {{site.data.keyword.cloudaccesstrailshort}}.</td>
	  </tr>
	  <tr>
	    <td>Elija un espacio:</td>
		<td>Seleccione el espacio que ha elegido para suministrar el servicio {{site.data.keyword.cloudaccesstrailshort}}.</td>
	  </tr>
	</table>

5. Pulse **Crear** para suministrar el servicio {{site.data.keyword.keymanagementserviceshort}} en el espacio de {{site.data.keyword.Bluemix_notm}} en el que ha iniciado la sesión.


## Paso 3: Generar un suceso de Activity Tracker
{: # step3}

En este paso creará una clave de seguridad utilizando el servicio {{site.data.keyword.keymanagementserviceshort}} para generar datos de sucesos de {{site.data.keyword.cloudaccesstrailshort}}. 

Siga los pasos siguientes para generar un suceso de {{site.data.keyword.cloudaccesstrailshort}}: 

1. En el panel de control de {{site.data.keyword.Bluemix_notm}}, seleccione el servicio **Key Protect**; se abrirá el panel de control de {{site.data.keyword.keymanagementserviceshort}}. A continuación, seleccione el separador **Gestionar**. 

2. Pulse **Añadir clave**. Se abrirá una nueva ventana.

3. Seleccione **Generar clave** y siga los pasos siguientes:

    * Escriba un nombre para la clave, por ejemplo *MyFirstKey*.

    * Elija un algoritmo para la clave.

    * Pulse **Añadir clave**. 
	
Como resultado de crear una clave se generan sucesos de {{site.data.keyword.cloudaccesstrailshort}}. 

## Paso 4: Supervisar un suceso de Activity Tracker
{: #step4}

En este paso verificará mediante la interfaz de usuario de {{site.data.keyword.Bluemix_notm}} que se generan sucesos de {{site.data.keyword.cloudaccesstrailshort}}. 

Siga los siguientes pasos para verificar que se ha creado un suceso: 

1. En el panel de control de {{site.data.keyword.Bluemix_notm}}, seleccione el servicio {{site.data.keyword.cloudaccesstrailshort}}. Se abre el panel de control del servicio.

2. Configure la vista para buscar los sucesos de {{site.data.keyword.keymanagementserviceshort}} que se han generado cuando se ha suministrado el servicio y se ha añadido una clave.

    * Seleccione **Registros de espacio** para el campo *Ver registros*.
    * Seleccione **target.name** para el campo *Campo de búsqueda*.
    * Escriba **ibm-key-protect** en el campo *Filtro*. 
	
    Los datos que se visualizan muestran los sucesos de {{site.data.keyword.keymanagementserviceshort}} que están disponibles durante las últimas 24 horas. 
	
	![Vista de la interfaz de usuario de los sucesos](images/bmx_ui_space_view.png "Vista de la interfaz de usuario de los sucesos")


## Siguientes pasos
{: #next_steps}

A continuación, utilice el panel de control de Kibana predefinido de {{site.data.keyword.cloudaccesstrailshort}} para supervisar y analizar registros de sucesos. Para iniciar Kibana, consulte [Navegación al panel de control de Kibana](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_kibana.html#launch_kibana). 

De forma predeterminada, en Kibana los registros de actividad de un espacio se muestran mediante el panel de control **ActivityTracker_Space_Search_in_24h**: 

![Vista de Kibana de los sucesos](images/kibana_space_view.png "Vista de Kibana de los sucesos")

También puede utilizar la CLI de {{site.data.keyword.cloudaccesstrailshort}} para gestionar los sucesos desde la línea de mandatos. Para obtener más información, consulte [Visualización de la información de sucesos](/docs/services/cloud-activity-tracker/how-to/manage-events-cli/viewing_event_information.html#viewing_event_status).

                                                                                                                      

