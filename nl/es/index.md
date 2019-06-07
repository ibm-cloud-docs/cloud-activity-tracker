---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-25"

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

# Iniciación
{: #getting-started-with-cla}

El servicio {{site.data.keyword.cloudaccesstrailfull}} registra las actividades iniciadas por el usuario que cambian el estado de un servicio en {{site.data.keyword.Bluemix}}. Obtenga más información sobre cómo utilizar el servicio {{site.data.keyword.cloudaccesstrailfull}} para supervisar la interacción de un usuario con el servicio de nube. 
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} está en desuso. A partir del 9 de mayo de 2019, no se pueden suministrar nuevas instancias de {{site.data.keyword.cloudaccesstrailshort}} y se eliminará el acceso a las instancias del plan *Lite*. Las instancias existentes del plan premium recibirán soporte hasta el 30 de septiembre de 2019. Para seguir supervisando la actividad de la cuenta de {{site.data.keyword.cloud_notm}} suministre una instancia de [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}

En la figura siguiente se muestran los distintos componentes y acciones que se producen cuando una actividad iniciada por el usuario cambia el estado de un servicio:

![Componentes y acciones que se producen cuando una actividad iniciada por el usuario cambia el estado de un servicio](images/AT_f1.png "Componentes y acciones que se producen cuando una actividad iniciada por el usuario cambia el estado de un servicio")

**Nota:** esta guía de iniciación le mostrará cómo empezar a trabajar para supervisar la actividad de la nube en la región EE. UU. sur.

## Antes de empezar
{: #index_prereqs}

* Obtenga información sobre el servicio {{site.data.keyword.cloudaccesstrailshort}}. Para obtener más información, consulte [Acerca de {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#activity_tracker_ov).
* Compruebe las regiones en las que está disponible el servicio. Para obtener más información, consulte [Regiones](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#activity_tracker_ov_regions).
* Obtenga un ID de usuario que sea miembro o propietario de una cuenta de {{site.data.keyword.cloud_notm}}. 

    Para obtener un ID de usuario de {{site.data.keyword.cloud_notm}}, vaya a: [Registro ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://cloud.ibm.com/login){:new_window}.



## Paso 1: Suministrar {{site.data.keyword.cloudaccesstrailshort}}
{: #index_step1}

Tenga en cuenta la información siguiente al elegir dónde suministrar una instancia del servicio {{site.data.keyword.cloudaccesstrailshort}}:

* {{site.data.keyword.cloudaccesstrailshort}} recopila los sucesos en dominios. Hay un dominio de cuenta por región y un dominio de espacio por espacio de Cloud Foundry (CF). 

* **Para supervisar las acciones de cuentas globales**, debe suministrar una instancia del servicio {{site.data.keyword.cloudaccesstrailshort}} en un espacio en la región EE. UU. sur. Estos son algunos ejemplos de acciones globales: suministro de una instancia, cambio de la política IAM de un usuario o invitación a un usuario a la cuenta.

* **Para supervisar sucesos generados por un servicio que se suministra en el contexto de una organización y un espacio de CF**, debe suministrar una instancia del servicio {{site.data.keyword.cloudaccesstrailshort}} en la misma región y espacio donde se ha suministrado el servicio cuya actividad desea supervisar. 

* **Para supervisar los sucesos generados por un servicio suministrado en el contexto de un grupo de recursos**, debe suministrar una instancia del servicio {{site.data.keyword.cloudaccesstrailshort}} en un espacio en la misma región en la que se ha suministrado el servicio cuya actividad desea supervisar. 

* Para suministrar una instancia, el ID de usuario debe tener el **rol de desarrollador** en el espacio en el que tiene previsto suministrar el servicio {{site.data.keyword.cloudaccesstrailshort}}.

Siga estos pasos para suministrar una instancia del servicio {{site.data.keyword.cloudaccesstraillong_notm}} en {{site.data.keyword.cloud_notm}}:

1. [Inicie sesión en {{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://cloud.ibm.com/login){:new_window}.
    
	Después de iniciar la sesión con su ID de usuario y contraseña, se abre la interfaz de usuario de {{site.data.keyword.cloud_notm}}.

2. Pulse **Catálogo**. Se abre la lista de los servicios que están disponibles en {{site.data.keyword.cloud_notm}}.

3. Seleccione la categoría **Seguridad e identidad** para filtrar la lista de servicios que se muestran.

    **Nota:** el servicio también está disponible a través de la categoría **Herramientas del desarrollador**.

4. Pulse el mosaico **Acivity Tracker**. 

5. Configure la información que define dónde se va a suministrar el servicio.

    Por ejemplo, para suministrar el servicio en la región EE. UU. sur, especifique los datos tal como se indica en la tabla siguiente: 

    <table>
	  <caption>Tabla 1. Campos obligatorios para suministrar el servicio {{site.data.keyword.cloudaccesstrailshort}}</caption>
	  <tr>
	    <th width="50%">Campo</th>
		<th width="50%">Valor</th>
	  </tr>
	  <tr>
	    <td>Seleccione la región de despliegue:</td>
		<td>EE. UU. sur</td>
	  </tr>
	  <tr>
	    <td>Elija una organización:</td>
		<td>Seleccione la organización en la que va a suministrar el servicio {{site.data.keyword.cloudaccesstrailshort}}.</td>
	  </tr>
	  <tr>
	    <td>Elija un espacio:</td>
		<td>Seleccione el espacio de la organización que ha seleccionado donde tiene previsto suministrar el servicio {{site.data.keyword.cloudaccesstrailshort}}.</td>
	  </tr>
	</table>

6. Seleccione un plan. 

    De forma predeterminada, se selecciona el plan **Lite**.

	Para obtener más información, consulte [Planes de servicio](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#activity_tracker_ov_plan).

7. Pulse **Crear** para suministrar una instancia del servicio {{site.data.keyword.cloudaccesstrailshort}} en el espacio en el que ha iniciado la sesión.
   


## Paso 2: Otorgar a los usuarios acceso a los sucesos de supervisión
{: #index_step2}

Para ver los sucesos, debe tener permisos de acceso en {{site.data.keyword.cloud_notm}}. Los permisos varían en función de si desea ver sucesos globales de la cuenta, sucesos correspondientes a un servicio suministrado en el contexto de un grupo de servicios o sucesos correspondientes a un servicio suministrado en el contexto de una organización y un espacio de CF. 

**Para supervisar las acciones globales de una cuenta** y **para supervisar un servicio que se ha suministrado en el contexto de un grupo de recursos**, tenga en cuenta la información siguiente:

* Debe tener una política IAM para el servicio {{site.data.keyword.loganalysisshort}} con el rol de **lector** sobre el servicio {{site.data.keyword.loganalysisshort}}. 
* El propietario de la cuenta o un administrador del servicio {{site.data.keyword.loganalysisshort}} pueden otorgar esta política.

**Para supervisar un servicio suministrado en el contexto de una organización y un espacio de CF**, tenga en cuenta la siguiente información:

* Debe tener el rol de **desarrollador** para el espacio en el que ha suministrado una instancia del servicio {{site.data.keyword.cloudaccesstrailshort}}.
* El propietario de la cuenta, el gestor de la organización o el gestor del espacio pueden otorgarle el rol de **desarrollador**
para el espacio.

**Nota: para otorgar a un usuario una política IAM, debe ser el propietario de la cuenta o un administrador del servicio {{site.data.keyword.loganalysisshort}}.**

### Cómo otorgar a los usuarios acceso para supervisar sucesos de dominio de cuenta
{: #index_acc}

Siga los pasos siguientes para otorgar a un usuario una política IAM desde la interfaz de usuario de {{site.data.keyword.cloud_notm}}:

1. [Inicie sesión en la consola de {{site.data.keyword.cloud_notm}}
![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://cloud.ibm.com/login){:new_window}.

2. Desde la barra de menús, pulse **Gestionar** &gt; **Seguridad** &gt; **Identidad y acceso** y luego seleccione **Usuarios**.
3. En la fila del usuario al que desea asignar acceso, seleccione el menú **Acciones** y luego pulse **Asignar acceso**.
4. Seleccione **Asignar acceso a recursos**.
5. Seleccione **Análisis de registros**.
6. Seleccione **Todas las regiones**.
7. Seleccione **Todas las instancias de servicio**.
8. Seleccione el rol de servicio **Lector**.
9. Pulse Asignar.

### Cómo otorgar a los usuarios acceso para supervisar sucesos de dominio de espacio
{: #index_space}

Para otorgar a un usuario un rol de desarrollador en un espacio desde la interfaz de usuario de {{site.data.keyword.cloud_notm}}, siga estos pasos:

1. [Inicie sesión en la consola de {{site.data.keyword.cloud_notm}}
![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://cloud.ibm.com/login){:new_window}.
	
	Después de iniciar la sesión con su ID de usuario y contraseña, se abre la interfaz de usuario de {{site.data.keyword.cloud_notm}}.

2. Desde la barra de menús, pulse **Gestionar** &gt; **Seguridad** &gt; **Identidad y acceso** y luego seleccione **Usuarios**.

3. Seleccione el usuario.

4. Seleccione **Acceso a Cloud Foundry**.

5. Amplíe una organización.

    Aparece la lista de espacios disponibles en dicha organización.

6. En el menú de acciones, seleccione **Editar rol de organización**. Seleccione el rol **Auditor** para el campo *Roles de organización*. A continuación, pulse **Guardar rol**.

7. Seleccione un espacio. 

8. En el menú de acciones, seleccione **Editar rol de espacio**. Seleccione el rol **Desarrollador** para el campo *Roles de espacio*. A continuación, pulse **Guardar rol**.
	
7. Pulse **Asignar**.




## Paso 3: Generar sucesos de {{site.data.keyword.cloudaccesstrailshort}}
{: #index_step3}

Una vez suministrado el servicio {{site.data.keyword.cloudaccesstrailshort}}, los sucesos se recopilan automáticamente de los servicios de la nube seleccionados. Para obtener más información sobre los servicios que puede supervisar con {{site.data.keyword.cloudaccesstrailshort}}, incluida la información sobre las acciones que generan un suceso de {{site.data.keyword.cloudaccesstrailshort}}, consulte el apartado sobre [Servicios de nube](/docs/services/cloud-activity-tracker/cloud_services.html#cloud_services).

**Nota:** para que un usuario genere sucesos de {{site.data.keyword.BluVirtServers_short}} y de {{site.data.keyword.baremetal_short}} {{site.data.keyword.cloudaccesstrailshort}}, el usuario debe tener acceso a recursos de infraestructura en la consola de IBM Cloud. Para obtener más información, consulte [Supervisión de la actividad de {{site.data.keyword.BluVirtServers_short}} y de {{site.data.keyword.baremetal_short}} con {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/tutorials/vsi.html#vsi).

Para obtener más información sobre cómo generar sucesos, consulte la guía de aprendizaje sobre [Supervisión de la actividad de {{site.data.keyword.keymanagementserviceshort}} con {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/tutorials/kp.html#kp).

## Paso 4: Visualizar sucesos
{: #index_step4}

Puede supervisar los sucesos de {{site.data.keyword.cloudaccesstrailshort}} en la interfaz de usuario de {{site.data.keyword.cloud_notm}}. También puede actualizar su plan al plan premium para supervisar los sucesos a través de Kibana. 

**Para supervisar las acciones globales de una cuenta** y **para supervisar un servicio que se ha suministrado en el contexto de un grupo de recursos**, tenga en cuenta la información siguiente:

* Los sucesos se recopilan en un dominio de cuenta.

    Hay un dominio de cuenta por región.

    Las acciones de cuentas globales se recopilan en el dominio de la cuenta EE. UU. sur.

    Los sucesos de un servicio se recopilan en el dominio de cuenta de la región en la que se suministra una instancia de este servicio.

* El propietario de la cuenta puede ver los sucesos a través de la interfaz de usuario de {{site.data.keyword.cloud_notm}} o en Kibana.
* Otros usuarios solo pueden ver los sucesos de dominio de cuenta a través de Kibana. 


**Para supervisar un servicio suministrado en el contexto de una organización y un espacio de CF**, tenga en cuenta la siguiente información:

* Los sucesos se recopilan en un dominio de espacio. 
* Cada espacio de CF tiene un dominio de espacio de {{site.data.keyword.cloudaccesstrailshort}} asociado. 
* Puede ver los sucesos a través de la interfaz de usuario de {{site.data.keyword.cloud_notm}} o en Kibana.

En la tabla siguiente se define el dominio de {{site.data.keyword.cloudaccesstrailshort}} en el que debe supervisar los sucesos:

| Supervisión                                                           | Dominio de {{site.data.keyword.cloudaccesstrailshort}} |  
|----------------------------------------------------------------------|----------------------------------------------------| 
| `Acciones globales de cuenta`                                             | Dominio de cuenta de EE.UU. sur                            |  
| `Servicios que se suministran en el contexto de un grupo de recursos`   | dominio de cuenta                                     | 
| `Servicios que se suministran en el contexto de una organización y un espacio de CF` | dominio de espacio                                       | 
{: caption="Tabla 1. Dominios de {{site.data.keyword.cloudaccesstrailshort}} por origen de sucesos" caption-side="top"} 

Para ver sucesos, puede elegir una de las opciones siguientes:

* [Navegación al panel de control de Activity Tracker para supervisar la actividad de nube en la cuenta](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_at_ui.html#launch_at_ui_account_view_account) 
* [Navegación en el panel de control de Activity Tracker para supervisar la actividad de nube en un espacio](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_at_ui.html#launch_at_ui_account_view_space) 
* [Navegación a Kibana desde un navegador web](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_kibana.html#launch_kibana).

Para ver los sucesos que genera con los pasos de esta guía de aprendizaje, seleccione [Navegación al panel de control de Activity Tracker para supervisar la actividad de nube en la cuenta](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_at_ui.html#launch_at_ui_account_view_account). Si no es el propietario de la cuenta, actualice el plan de servicio y compruebe que dispone de los permisos de acceso correctos para ver sucesos. 


## Siguientes pasos
{: #index_next_steps}

Utilice la CLI de {{site.data.keyword.cloudaccesstrailshort}} para gestionar los sucesos desde la línea de mandatos. Para obtener más información, consulte [Gestión de sucesos mediante la CLI de Activity Tracker](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#tutorial2).



