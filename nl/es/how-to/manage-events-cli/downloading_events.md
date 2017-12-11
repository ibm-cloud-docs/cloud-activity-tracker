---

copyright:
  years: 2016, 2017
lastupdated: "2017-09-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Descarga de sucesos
{: #downloading_events}

Puede descargar sucesos en un archivo local o puede dirigir los datos a otro programa. Puede descargar sucesos dentro del contexto de una sesión. Una sesión especifica los sucesos que se descargarán. Si la descarga de sucesos se interrumpe, la sesión permite reanudar la descarga desde donde se detuvo. Una vez finalizada la descarga, debe suprimir la sesión.{:shortdesc}

Siga los pasos siguientes para descargar los sucesos que están disponibles en un espacio de {{site.data.keyword.Bluemix_notm}} en un archivo local:

## Paso 1: Iniciar sesión en Bluemix
{: #prereq}

Antes de empezar, inicie una sesión en una región, organización y espacio de {{site.data.keyword.Bluemix_notm}} donde se suministra el servicio. {{site.data.keyword.cloudaccesstrailshort}}. 

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

Siga las instrucciones.  

Por ejemplo, ejecute el siguiente mandato para iniciar la sesión en la región EE.UU. sur: 
	
```
bx login -a api.ng.bluemix.net
```
{: codeblock}

A continuación, defina la organización y el espacio. Ejecute el mandato siguiente:

```
bx target -o OrgName -s SpaceName
```
{: codeblock}

donde 

* OrgName es el nombre de la organización.
* SpaceName es el nombre del espacio.

## Paso 2: Identificar los sucesos que están disponibles
{: #step2}

1. Utilice el mandato `cf at status` para ver los sucesos que están disponibles.

    Por ejemplo, para ver los sucesos que están disponibles durante las 2 últimas semanas, ejecute el mandato siguiente:

    ```
    $ bx cf at status
    ```
    {: codeblock}
    
    Por ejemplo, el resultado de ejecutar este mandato es: 
    
    ```
    +------------+--------+-------+--------------------+------------+
    |    DATE    |  COUNT | SIZE  |       TYPES        | SEARCHABLE |
    +------------+--------+-------+--------------------+------------+
    | 2017-07-24 |    16  | 3020  | ActivityTracker    |   None     |
    +------------+--------+-------+--------------------+------------+
    | 2017-07-25 |   1224 | 76115 | ActivityTracker    |    All     |
    +------------+--------+-------+--------------------+------------+
    ```
    {: screen}

    **Nota:** El servicio {{site.data.keyword.cloudaccesstrailshort}} es un servicio global que utiliza la Hora Universal Coordinada (UTC). Los días se definen como días UTC. Para obtener sucesos correspondientes a un día en hora local, es posible que tenga que descargar varios días UTC. 
	
	Para obtener más información, consulte [cf at status](/docs/services/cloud-activity-tracker/cli/at_cli.html#status).


## Paso 3: Crear una sesión
{: #step3}

Se necesita una sesión para definir el ámbito de los datos de sucesos que se pueden descargar y para mantener el estado de la descarga. 

Utilice el mandato [cf at session create](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_create) para crear una sesión. Si lo desea, puede especificar la fecha de inicio y la fecha final cuando cree una sesión. 

**Nota:** Si especifica la fecha de inicio y la fecha final, la sesión proporciona acceso a los sucesos comprendidos entre ambas fechas inclusive. 

Para crear una sesión que se utiliza para descargar los sucesos correspondientes a la fecha actual, ejecute el mandato siguiente:

```
bx cf at session create
```
{: codeblock}

La sesión devuelve la siguiente información:

* El rango de fechas que se van a descargar. El valor predeterminado es la fecha UTC actual. 
* Información sobre si se deben incluir los sucesos disponibles para toda la cuenta o solo para el espacio actual. De forma predeterminada se obtienen los sucesos correspondientes al espacio en el que se ha iniciado la sesión. 
* El ID de sesión necesario para descargar los sucesos.
* El ID de usuario que crea la sesión.

Por ejemplo, 

```
$ bx cf at session create
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| username     | xxx@yyy.com                               |
| create-time  | 2017-07-25T10:29:28.541092735Z            |
| access-time  | 2017-07-25T10:29:28.541092735Z            |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
| id           | 32c657c5-31c0-4a3c-a139-b380871c737a      |
| space        | 66fe4565-abab-46c9-cdcd-qf4565342345      |
+--------------+-------------------------------------------+
```
{: screen}

**Sugerencia:** Para ver la lista de sesiones activas, ejecute el mandato [cf at session list](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_list).

Por ejemplo, 

```
bx cf at session list
+--------------------------------------+--------------------------------------+---------------------+--------------------------------+--------------------------------+
| Id                                   | Space                                |Username             | Create-time                    | Access-time                    |
+--------------------------------------+--------------------------------------+---------------------+--------------------------------+--------------------------------+
| 32c657c5-31c0-4a3c-a139-b380871c737a | 66fe4565-abab-46c9-cdcd-qf4565342345 |xxx@yyy.com          | 2017-07-25T10:29:28.541092735Z | 2017-07-25T10:29:28.541092735Z |
+--------------------------------------+--------------------------------------+---------------------+--------------------------------+--------------------------------+
```
{: screen} 


## Paso 4: Descargar los sucesos en un archivo
{: #step4}

Para descargar los sucesos especificados por los parámetros de la sesión, ejecute el siguiente mandato: 

```
bx cf at download -o Events_File_Name Session_ID
```
{: codeblock}

donde 

* Events_File_Name es el nombre del archivo de salida.
* Session_ID es el GUID de la sesión. Este valor se obtiene en el paso anterior. Utilice el valor para el campo **ID**.

Por ejemplo, 

```
bx cf at download -o Events_File_Name.log 32c657c5-31c0-4a3c-a139-b380871c737a
 29.89 KiB / 12.19 KiB [================================] 245.14% 9.73 MiB/s 0s
Download completed successfully
```
{: screen}

El indicador de progreso pasa de 0 a 100% a medida que los sucesos se descargan. 

**Nota:** 

* El formato de los datos descargados es JSON comprimido. Por ejemplo, cuando se descarga sucesos en un sistema Linux, descomprima el archivo .gz y ábralo para ver los datos en formato JSON. 
* El archivo JSON comprimido es adecuado para la ingestión por parte de ElasticSearch o Logstash. Por ejemplo, si no se especifica -o y está trabajando en un sistema Linux, los datos se dirigen a stdout, para que pueda dirigirlos directamente a su propia pila Elastic. 
* También puede procesar los datos con cualquier programa que pueda analizar JSON. 

## Paso 4: Suprimir la sesión

Una vez finalizada la descarga, debe suprimir la sesión con el mandato [cf at session delete](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_delete).  

Ejecute el siguiente mandato para suprimir una sesión:

```
bx cf at session delete Session_ID
```
{: codeblock}

Donde Session_ID es el GUID de la sesión que ha creado en un paso anterior. Utilice el valor para el campo **ID**.

Por ejemplo, 

```
bx cf at session delete 32c657c5-31c0-4a3c-a139-b380871c737a
+---------+------------------------+
| Name    | Value                  |
+---------+------------------------+
| message | Delete session success |
+---------+------------------------+
```
{: screen}




