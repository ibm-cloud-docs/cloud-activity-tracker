---

copyright:
  years: 2017
lastupdated: "2017-09-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# Modificación del plan
{: #change_plan}

Puede cambiar su plan de servicio de {{site.data.keyword.cloudaccesstraillong}} en {{site.data.keyword.Bluemix_notm}} en el panel de control del servicio o ejecutando el mandato `cf update-service`. Puede actualizar o reducir el plan en cualquier momento. {:shortdesc}

## Modificación del plan de servicio mediante la interfaz de usuario
{: #change_plan_ui}

Para cambiar su plan de servicios en {{site.data.keyword.Bluemix_notm}} en el panel de control del servicio, siga estos pasos:

1. Inicie una sesión en {{site.data.keyword.Bluemix_notm}} y pulse el servicio {{site.data.keyword.cloudaccesstraillong_notm}} en el panel de control de {{site.data.keyword.Bluemix_notm}}. 
    
2. Seleccione el separador **Plan** en la interfaz de usuario de {{site.data.keyword.Bluemix_notm}}.

    Se muestra información sobre su plan actual. 
	
3. Seleccione un nuevo plan para actualizar o reducir su plan. 

4. Pulse **Guardar**.



## Modificación del plan de servicio mediante la CLI
{: #change_plan_cli}

Para cambiar su plan de servicio en Bluemix mediante la CLI, siga los pasos siguientes:

1. Inicie una sesión en una región, organización y espacio de {{site.data.keyword.Bluemix_notm}}.  

    ```
    cf login -a Endpoint
    ```
    {: codeblock}
	
	Donde *Endpoint* es el URL para iniciar una sesión en {{site.data.keyword.Bluemix_notm}}. Este URL varía según la región. 
	
	<table>
	    <caption>Obtenga una lista de puntos finales para acceder a {{site.data.keyword.Bluemix_notm}}</caption>
		<tr>
		  <th>Región</th>
		  <th>URL</th>
		</tr>
		<tr>
		  <td>EE.UU. sur</td>
		  <td>api.ng.bluemix.net</td>
		</tr>
		<tr>
		  <td>Reino Unido</td>
		  <td>api.eu-gb.bluemix.net</td>
		</tr>
		<tr>
		  <td>Alemania</td>
		  <td>api.eu-de.bluemix.net</td>
		</tr>
	</table>

    Siga las instrucciones. Escriba sus credenciales de {{site.data.keyword.Bluemix_notm}} y seleccione una organización y un espacio. 

    Por ejemplo, ejecute el siguiente mandato para iniciar la sesión en la región EE.UU. sur: 
	
	```
	cf login -a api.ng.bluemix.net
	```
	{: codeblock}
	
2. Ejecute el mandato `cf services` para comprobar su plan actual y para obtener el nombre del servicio {{site.data.keyword.cloudaccesstrailshort}} de la lista de servicios disponibles en el espacio.  

    El valor del campo **name** es el que debe utilizar para modificar el plan. 

    Por ejemplo, 
	
	```
	$ cf services
    Getting services in org MyOrg / space dev as xxx@yyy.com...
    OK

    name                            service              plan          bound apps      last operation
    Activity Tracker-oj            activityTracker       premium                       create succeeded
    ```
	{: screen}
    
3. Actualice o reduzca su plan. Ejecute el mandato `cf update-service`. 
    
	```
	cf update-service service_name [-p new_plan]
	```
	{: codeblock}
	
	donde  
	
	* *service_name* es el nombre del servicio. Puede ejecutar el mandato `cf services` para obtener el valor.
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
	    <td>lite</td>
	  </tr>
	  <tr>
	    <td>Premium</td>
	    <td>premium</td>
	  </tr>
	</table>
	
	Por ejemplo, para reducir el plan al plan *Lite*, ejecute el siguiente mandato:
	
	```
	cf update-service "Activity Tracker-oj" -p lite
    Updating service instance Activity Tracker-oj as xxx@yyy.com...
    OK
	```
	{: screen}

4. Verifique que el nuevo plan se ha cambiado. Ejecute el mandato `cf services`. 

    ```
	cf services
    Getting services in org MyOrg / space dev as xxx@yyy.com...
    OK

    name                   service            plan      bound apps   last operation
    Activity Tracker-oj    activityTracker    lite                   update succeeded
	```
	{: screen}






