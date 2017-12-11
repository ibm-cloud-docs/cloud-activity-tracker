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


# Suministro del servicio Activity Tracker
{: #provision}

Puede suministrar el servicio {{site.data.keyword.cloudaccesstraillong}} desde la interfaz de usuario de {{site.data.keyword.Bluemix}} o desde la línea de mandatos.{:shortdesc}


## Suministro desde la interfaz de usuario
{: #ui}

Siga los pasos siguientes para suministrar una instancia del servicio {{site.data.keyword.cloudaccesstraillong_notm}} en {{site.data.keyword.Bluemix_notm}}:

1. Inicie sesión en su cuenta de {{site.data.keyword.Bluemix_notm}}.

    El panel de control de {{site.data.keyword.Bluemix_notm}} se encuentra en: [http://bluemix.net ![Icono de enlace externo](../../../icons/launch-glyph.svg "Icono de enlace externo")](http://bluemix.net){:new_window}.
    
	Después de iniciar la sesión con su ID de usuario y contraseña, se abre la interfaz de usuario de {{site.data.keyword.Bluemix_notm}}.

2. Pulse **Catálogo**. Se abre la lista de los servicios que están disponibles en {{site.data.keyword.Bluemix_notm}}.  

3. Seleccione la categoría **Seguridad** para filtrar la lista de servicios que se muestran.

    El servicio también está disponible en la categoría **DevOps**. 

4. Pulse el mosaico **Acivity Tracker**.

5. Configure la información que define dónde se va a suministrar el servicio.  

    Especifique los datos como se indica en la tabla siguiente: 

    <table>
	  <caption>Tabla 1. Campos obligatorios para suministrar el servicio {{site.data.keyword.cloudaccesstrailshort}}</caption>
	  <tr>
	    <th>Campo</th>
		<th>Valor</th>
	  </tr>
	  <tr>
	    <td>Seleccione la región de despliegue:</td>
		<td>Los valores válidos son: EE.UU. sur, Reino Unido, Alemania</td>
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

6. Seleccione un plan de servicio. 

    De forma predeterminada, está definido el plan **gratuito**. 

    Para obtener más información, consulte [Planes de servicio](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#plans).
	
7. Pulse **Crear** para suministrar el servicio {{site.data.keyword.cloudaccesstrailshort}} en el espacio de {{site.data.keyword.Bluemix_notm}} en el que ha iniciado la sesión.
  
 

## Suministro desde la CLI
{: #cli}

Siga los pasos siguientes para suministrar una instancia del servicio {{site.data.keyword.cloudaccesstraillong_notm}} en {{site.data.keyword.Bluemix_notm}} mediante la línea de mandatos:

1. Instale la CLI de Cloud Foundry (CF). Si la CLI de CF ya está instalada, continúe con el siguiente paso.

   Para obtener más información, consulte [Instalación de la CLI de cf ![Icono de enlace externo](../../../icons/launch-glyph.svg "Icono de enlace externo")](http://docs.cloudfoundry.org/cf-cli/install-go-cli.html){: new_window}. 
    
2. Inicie una sesión en una región, organización y espacio de {{site.data.keyword.Bluemix_notm}}.  

    Por ejemplo, para iniciar una sesión en la región EE.UU. sur, ejecute el mandato siguiente:

    ```
    cf login -a https://api.ng.bluemix.net
    ```
    {: codeblock}

    Siga las instrucciones. Escriba sus credenciales de {{site.data.keyword.Bluemix_notm}} y seleccione una organización y un espacio.
	
3. Ejecute el mandato `cf create-service` para suministrar una instancia. 

    ```
	cf create-service service_name service_plan service_instance_name
	```
	{: codeblock}
	
	Donde
	
	* service_name es el nombre del servicio, es decir, **activityTracker**.
	* service_plan es el nombre del plan de servicio. Para ver una lista de planes, consulte [Planes de servicio](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#plans).
	* service_instance_name es el nombre que desea utilizar para la nueva instancia de servicio que cree.
Para obtener más información sobre el mandato, consulte [cf create-service](/docs/cli/reference/cfcommands/index.html#cf_create-service).

	Por ejemplo, para crear una instancia del servicio {{site.data.keyword.cloudaccesstrailshort}} con el plan Lite, ejecute este mandato:
```
	cf create-service activityTracker free my_activity_tracker_svc
	```
	{: codeblock}
	
4. Verifique que el servicio se ha creado correctamente. Ejecute el mandato siguiente:

    ```	
	cf services
	```
	{: codeblock}
	
	El resultado de ejecutar el mandato se parece al siguiente:
	
	```
    Getting services in org MyOrg / space MySpace as xxx@yyy.com...
    OK
    
    name                           service                  plan                   bound apps              last operation
    my_activity_tracker_svc        activityTracker          free                                           create succeeded
	```
	{: screen}

	



