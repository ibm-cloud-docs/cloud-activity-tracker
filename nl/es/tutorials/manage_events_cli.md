---

copyright:
  years: 2016, 2017

lastupdated: "2017-09-07"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# Gestión de sucesos mediante la CLI de Activity Tracker
{: #tutorial2}

Utilice esta guía de aprendizaje para aprender a utilizar la CLI de {{site.data.keyword.cloudaccesstrailshort}} para gestionar sucesos a través de la línea de mandatos. Aprenda a obtener información sobre sucesos almacenados, cómo descargar los sucesos almacenados en {{site.data.keyword.IBM_notm}} Cloud o cómo suprimir sucesos.{:shortdesc}

Siga estos pasos:

1. [Suministre el servicio {{site.data.keyword.IBM_notm}} Key Protect y genere sucesos](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step1)
2. [Obtenga información sobre sucesos almacenados (cf at status)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step2)
2. [Especifique los registros que desea descargar mediante la creación de una sesión (cf at session create)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step3)
3. [Obtenga los datos de registro real (cf at download)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step4)
4. [Suprima la sesión después de que finalice la descarga (cf at session delete)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step5)
5. [Suprima manualmente los registros que no se necesiten (cf at delete)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step6)


## Supuestos
{: #assumptions}

1. Tiene un ID de usuario de {{site.data.keyword.Bluemix_notm}} con permisos de desarrollador para trabajar en un espacio de una cuenta de {{site.data.keyword.Bluemix_notm}} en la que se suministra el servicio {{site.data.keyword.IBM_notm}} Cloud {{site.data.keyword.cloudaccesstrailshort}}.  

    Para obtener más información sobre cómo suministrar el servicio {{site.data.keyword.cloudaccesstrailshort}}, consulte [Suministro del servicio {{site.data.keyword.cloudaccesstrailshort}} ](/docs/services/cloud-activity-tracker/how-to/provision.html#provision).

2. Ha instalado el plugin {{site.data.keyword.cloudaccesstrailshort}} CF en el sistema local. Esto es necesario para poder utilizar la CLI de {{site.data.keyword.cloudaccesstrailshort}} para gestionar sucesos a través de la línea de mandatos.  

    Para obtener más información sobre cómo instalar el plugin {{site.data.keyword.cloudaccesstrailshort}} CF, consulte [Configuración de la CLI de {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#config_at_cli).

3. Ha iniciado una sesión en {{site.data.keyword.Bluemix_notm}} mediante la línea de mandatos con este mandato: 

    ```
    bx login -a Endpoint
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
	</table>

    Por ejemplo, ejecute el siguiente mandato para iniciar la sesión en la región EE.UU. sur: 
	
	```
	bx cf login -a api.ng.bluemix.net
	```
	{: codeblock}

	**Nota:** Debe iniciar sesión en la región, organización y espacio de {{site.data.keyword.Bluemix_notm}} donde se suministra el servicio {{site.data.keyword.cloudaccesstrailshort}} para poder ejecutar mandatos de {{site.data.keyword.cloudaccesstrailshort}} y gestionar sucesos mediante la línea de mandatos.
	
	A continuación, defina la organización y el espacio. Ejecute el mandato siguiente:

    ```
    bx target -o OrgName -s SpaceName
    ```
    {: codeblock}

    donde 

    * OrgName es el nombre de la organización.
    * SpaceName es el nombre del espacio.


## Paso 1: Suministrar el servicio IBM Key Protect y generar sucesos 
{: #step1}
	
1. Siga los pasos siguientes para suministrar una instancia del servicio {{site.data.keyword.keymanagementserviceshort}} en {{site.data.keyword.Bluemix_notm}}:

    1. Inicie sesión en su cuenta de {{site.data.keyword.Bluemix_notm}}.

        El panel de control de {{site.data.keyword.Bluemix_notm}} se encuentra en: [http://bluemix.net](http://bluemix.net).

        Después de iniciar la sesión con su ID de usuario y contraseña, se abre la interfaz de usuario de {{site.data.keyword.Bluemix_notm}}.

    2. Pulse **Catálogo**. Se abre la lista de los servicios que están disponibles en {{site.data.keyword.Bluemix_notm}}.  

        Seleccione la categoría **Seguridad** para filtrar la lista de servicios que se muestran.

    3. Seleccione el mosaico **Key Protect**.

    4. Pulse **Crear** para suministrar el servicio {{site.data.keyword.keymanagementserviceshort}} en el espacio de {{site.data.keyword.Bluemix_notm}} en el que ha iniciado la sesión.

2. Siga los pasos siguientes para generar un suceso de {{site.data.keyword.cloudaccesstrailshort}}: 

    1. En el panel de control de {{site.data.keyword.Bluemix_notm}}, seleccione el servicio {{site.data.keyword.keymanagementserviceshort}}; se abrirá el panel de control de {{site.data.keyword.keymanagementserviceshort}}. A continuación, seleccione el separador **Gestionar**. 

    2. Pulse **Añadir clave**. Se abrirá una nueva ventana.

        ![{{site.data.keyword.keymanagementserviceshort}} ventana para añadir claves](images/KP_f2.gif)

    3. Seleccione **Generar clave** y siga los pasos siguientes:

        * Escriba un nombre para la clave, por ejemplo *MyFirstKey*.

        * Elija un algoritmo para la clave.

        * Pulse **Añadir clave**. 

3. Verifique que se ha creado un suceso: 

    1. En el panel de control de {{site.data.keyword.Bluemix_notm}}, seleccione el servicio {{site.data.keyword.cloudaccesstrailshort}}. Se abre el panel de control del servicio.

    2. Configure la vista para buscar los sucesos de {{site.data.keyword.keymanagementserviceshort}} que se han generado cuando se ha suministrado el servicio y se ha añadido una clave.

        * Seleccione **Registros de espacio** para el campo *Ver registros*.
	    * Seleccione **target.name** para el campo *Campo de búsqueda*.
	    * Escriba **ibm-key-protect** en el campo *Filtro*. 
	
	    Los datos que se muestran corresponden a los sucesos de {{site.data.keyword.keymanagementserviceshort}} que están disponibles durante las últimas 24 horas. 

	    ![{{site.data.keyword.cloudaccesstrailshort}} separador gestionar](images/KP_f3.gif)

## Paso 2: Obtener información sobre sucesos almacenados
{: #step2}

Compruebe que hay sucesos disponibles que se pueden descargar. Por ejemplo, si suministra y añade una clave sobre la fecha actual, ejecute el siguiente mandato para obtener información sobre los sucesos recopilados hoy:

```
bx cf at status -s 2017-07-25 -e 2017-07-25
+------------+-------+-------+------------+
| Date       | Count | Size  | Searchable |
+------------+-------+-------+------------+
| 2017-07-25 | 12    | 34994 | All        |
+------------+-------+-------+------------+
```
{: screen}

Este mandato contará los sucesos correspondientes al 25 de junio de 2017.  {{site.data.keyword.cloudaccesstrailshort}} es un servicio global, por lo tanto, los días están en Hora Universal. Para obtener un día en hora local, probablemente tendrá que descargar varios días UTC.

Para ver información correspondiente a varios días, utilice `-s` para definir el día inicial y `-e` para definir el día final.  

Para obtener más información sobre el mandato `cf at status`, consulte la [Referencia de CLI](/docs/services/cloud-activity-tracker/cli/at_cli.html#status).

Utilice `bx cf at help status` para obtener ayuda desde la línea de mandatos. 

## Paso 3: Especificar los sucesos que se van a descargar
{: #step3}

Antes de descargar sucesos, cree una sesión:

* La sesión especifica los sucesos que se descargarán. 
* Si la descarga de sucesos se interrumpe, la sesión permite reanudar la descarga desde donde se detuvo.

Utilice el mandato siguiente crear una sesión:

```
bx cf at session create -s 2017-07-25 -e 2017-07-25
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| id           | 21b19aeb-3d32-4c60-b912-517609c62db2      |
| space        | 667fb895-b5f5-46c9-9f0e-cf4587341095      |
| username     | xxx@yyy.com                               |
| create-time  | 2017-07-25T18:33:22.678350874Z            |
| access-time  | 2017-07-25T18:33:22.678350874Z            |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
+--------------+-------------------------------------------+
```

Hay una fecha de inicio y una fecha final asociadas a una sesión. El mandato de descarga incluirá los sucesos comprendidos entre ambas fechas inclusive. El rango de fechas predeterminado es solo el día actual.  

La parte importante de la salida del mandato es el `ID` de sesión. Se hace referencia al mismo en el mandato de descarga.

Para obtener información sobre las sesiones existentes, escriba `cf at session list`.

Para obtener más información sobre las sesiones y el mandato `cf at session create`, consulte la [Referencia de CLI](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_create).

Utilice `cf at session help create` para obtener ayuda desde la línea de mandatos.

## Paso 4: Descargue los sucesos identificados para el ámbito definido para la sesión
{: #step4}

Para descargar los sucesos especificados por los parámetros de la sesión, ejecute el siguiente mandato: 

```
$ bx cf at events download -o events.log 21b19aeb-3d32-4c60-b912-517609c62db2
 6.70 KiB / 3.06 KiB [================================================================================================================================================================] 219.03% 8.60 MiB/s 0s
Download Successful
```

* El parámetro `-o` especifica un archivo de salida. 
* El ID de sesión se especifica en último logar. El valor de ID de sesión se obtiene de la salida del mandato `cf at session create` mandato.
* El indicador de progreso pasa de 0 a 100% a medida que los sucesos se descargan. 

El formato de los datos descargados es JSON comprimido. 

Para obtener más información sobre el mandato `cf at download`, consulte la [Referencia de CLI](/docs/services/cloud-activity-tracker/cli/at_cli.html#download).

Utilice `bx cf at help download` para obtener ayuda desde la línea de mandatos. 

## Paso 5: Suprimir la sesión
{: #step5}

Una vez finalizada la descarga, suprima la sesión. 

El número de sesiones es limitado. Una sesión no se suprime automáticamente. Debe suprimir manualmente las sesiones que no necesite. 

```
$ bx cf at session delete 21b19aeb-3d32-4c60-b912-517609c62db2
+---------+------------------------+
| name    | value                  |
+---------+------------------------+
| message | Delete session success |
+---------+------------------------+
```

Para obtener más información sobre el mandato `cf at session delete`, consulte la [Referencia de CLI](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_delete).

Utilice `bx cf at session help delete` para obtener ayuda desde la línea de mandatos.

## Paso 6: Suprimir sucesos manualmente de Activity Tracker
{: #step6}

El usuario tiene el control de su propia retención de sucesos en {{site.data.keyword.cloudaccesstrailshort}}. Puede suprimir sucesos manualmente, o puede automatizar la supresión de sucesos.

Para suprimir sucesos manualmente, ejecute el mandato `cf at delete`. Por ejemplo, 

```
$ bx cf at delete -s 2017-07-25 -e 2017-07-25
Deleted successfully
"6 logs were deleted,freeing 13737 bytes."
```

Para obtener más información sobre el mandato `cf at delete`, consulte la [Referencia de CLI](/docs/services/cloud-activity-tracker/cli/at_cli.html#delete).

Utilice `bx cf at help delete` para obtener ayuda desde la línea de mandatos.

**Nota:** Para suprimir sucesos automáticamente, puede definir una política de retención mediante el mandato de CLI `cf at option`. Para obtener más información, consulte la [Referencia de CLI](/docs/services/cloud-activity-tracker/cli/at_cli.html#option)


