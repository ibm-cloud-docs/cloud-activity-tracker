---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, provision instance

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
{:deprecated: .deprecated}


# Suministro de Activity Tracker
{: #provision}

Puede suministrar el servicio {{site.data.keyword.cloudaccesstraillong}} desde la interfaz de usuario de {{site.data.keyword.cloud_notm}} o desde la línea de mandatos.
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} está en desuso. A partir del 9 de mayo de 2019, no se pueden suministrar nuevas instancias de {{site.data.keyword.cloudaccesstrailshort}}. Las instancias existentes del plan premium recibirán soporte hasta el 30 de septiembre de 2019. Para seguir supervisando la actividad de la cuenta de {{site.data.keyword.cloud_notm}} suministre una instancia de [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}

## Suministro desde la interfaz de usuario
{: #provision_ui}

Siga los pasos siguientes para suministrar una instancia del servicio {{site.data.keyword.cloudaccesstraillong_notm}} en {{site.data.keyword.cloud_notm}}:

1. [Inicie sesión en su cuenta de {{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://cloud.ibm.com/login){:new_window}.
    
	Después de iniciar la sesión con su ID de usuario y contraseña, se abre la interfaz de usuario de {{site.data.keyword.cloud_notm}}.

2. Pulse **Catálogo**. Se abre la lista de los servicios que están disponibles en {{site.data.keyword.cloud_notm}}.

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
		<td>Los valores válidos son: EE. UU. sur, Reino Unido, Alemania, Sídney</td>
	  </tr>
	  <tr>
	    <td>Elija una organización:</td>
		<td>Seleccione la organización donde piensa supervisar la actividad.</td>
	  </tr>
	  <tr>
	    <td>Elija un espacio:</td>
		<td>Seleccione un espacio de la organización que ha seleccionado donde piensa supervisar la actividad.</td>
	  </tr>
	</table>

6. Seleccione un plan de servicio. 

    De forma predeterminada, está definido el plan **gratuito**.

    Para obtener más información, consulte [Planes de servicio](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-change_plan#change_plan).
	
7. Pulse **Crear** para suministrar el servicio {{site.data.keyword.cloudaccesstrailshort}} en el espacio de {{site.data.keyword.cloud_notm}} en el que ha iniciado la sesión.
  
 

## Suministro desde la CLI
{: #provision_cli}

Siga los pasos siguientes para suministrar una instancia del servicio {{site.data.keyword.cloudaccesstrailshort}} en {{site.data.keyword.cloud_notm}} mediante la línea de mandatos:

1. [Requisito previo] Instale la CLI de {{site.data.keyword.cloud_notm}}.

   Para obtener más información, consulte [Instalación de la CLI de {{site.data.keyword.cloud_notm}}](/docs/cli?topic=cloud-cli-ibmcloud-cli#ibmcloud-cli).
   
   Si la CLI está instalada, continúe en el paso siguiente.
    
2. Inicie una sesión en {{site.data.keyword.cloud_notm}}. 

    Ejecute el mandato [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) para iniciar una sesión en {{site.data.keyword.cloud_notm}} y luego ejecute el mandato [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) para definir la organización y el espacio donde desea suministrar el servicio {{site.data.keyword.cloudaccesstrailshort}}.
	
3. Ejecute el mandato `ibmcloud service create` para suministrar una instancia.

    ```
	  ibmcloud service create service_name service_plan service_instance_name
    ```
	  {: codeblock}
	
	  Donde
	
	  * service_name es el nombre del servicio, es decir **accessTrail**.

	  * service_plan es el nombre del plan de servicio. Para ver una lista de planes, consulte [Planes de servicio](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-change_plan#change_plan).

	  * service_instance_name es el nombre que desea utilizar para la nueva instancia de servicio que cree.

	  Por ejemplo, para crear una instancia del servicio {{site.data.keyword.cloudaccesstrailshort}} con el plan estándar, ejecute este mandato:
	
	  ```
	  ibmcloud service create accessTrail free my_activitytracker_svc
	  ```
	  {: codeblock}
	
4. Verifique que el servicio se ha creado correctamente. Ejecute el mandato siguiente:

  ```	
	ibmcloud service list
	```
	{: codeblock}
	
	El resultado de ejecutar el mandato se parece al siguiente:
	
	```
    Getting services in org MyOrg / space MySpace as xxx@yyy.com...
    OK
    
    name                           service                  plan                   bound apps              last operation
    my_activitytracker_svc         accessTrail             free                                            create succeeded
	```
	{: screen}

	




