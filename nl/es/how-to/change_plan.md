---

copyright:
  years: 2016, 2018
lastupdated: "2018-09-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}



# Modificación del plan
{: #change_plan}

Puede cambiar su plan de servicio de {{site.data.keyword.cloudaccesstraillong}} en la interfaz de usuario de {{site.data.keyword.Bluemix_notm}} o ejecutando el mandato `ibmcloud service update`. Puede actualizar o reducir el plan en cualquier momento.
{:shortdesc}

## Modificación del plan de servicio mediante la interfaz de usuario
{: #change_plan_ui}

Para cambiar el plan de servicio a través de la interfaz de usuario de {{site.data.keyword.Bluemix_notm}}, lleve a cabo los siguientes pasos:

1. Inicie una sesión en {{site.data.keyword.Bluemix_notm}} y luego pulse el servicio {{site.data.keyword.cloudaccesstraillong_notm}} en el *Panel de control*. 
    
2. Seleccione el separador **Plan**.

    Se muestra información sobre su plan actual.
	
3. Seleccione un nuevo plan para actualizar o reducir su plan. 

4. Pulse **Guardar**.



## Modificación del plan de servicio mediante la CLI
{: #change_plan_cli}

Para cambiar su plan de servicio mediante la CLI, siga los pasos siguientes:

1. Inicie una sesión en {{site.data.keyword.Bluemix_notm}}. 

    Ejecute el mandato [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) para iniciar una sesión en {{site.data.keyword.Bluemix_notm}} y luego ejecute el mandato [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) para definir la organización y el espacio donde desea suministrar el servicio {{site.data.keyword.cloudaccesstrailshort}}.
	
2. Ejecute el mandato `ibmcloud service list` para comprobar su plan actual y para obtener el nombre del servicio {{site.data.keyword.cloudaccesstrailshort}} de la lista de servicios disponibles en el espacio. 

    El valor del campo **name** es el que debe utilizar para modificar el plan. 

    Por ejemplo,
	
	```
	$ ibmcloud service list
    Invoking 'cf services'...

    Getting services in org MyOrg / space dev as xxx@ibm.com...
    OK

    name                       service                  plan                 bound apps                               last operation
    Activity Tracker-zt          OK                     accessTrail             premium                                update succeeded
    ```
	{: screen}
    
3. Actualice o reduzca su plan. Ejecute el mandato `ibmcloud service update`.
    
	```
	ibmcloud service update service_name [-p new_plan]
	```
	{: codeblock}
	
	donde 
	
	* *service_name* es el nombre del servicio. Puede ejecutar el mandato `ibmcloud service list` para obtener el valor.
	* *new_plan* es el nombre del plan.
	
	En la tabla siguiente se muestran los diferentes planes y sus valores soportados:
	
	<table>
	  <caption>Tabla 1. Lista de planes.</caption>
	  <tr>
	    <th>Plan</th>
	    <th>Nombre</th>
	  </tr>
	  <tr>
	    <td>Lite</td>
	    <td>free</td>
	  </tr>
	  <tr>
	    <td>Premium</td>
	    <td>premium</td>
	  </tr>
	</table>
	
	Por ejemplo, para reducir el plan al plan *Lite*, ejecute el siguiente mandato:
	
	```
	ibmcloud service update "Activity Tracker-zt" -p free
    Updating service instance Activity Tracker-zt as xxx@ibm.com...
    OK
	```
	{: screen}



