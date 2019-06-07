---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, download events

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

# Descarga de sucesos
{: #downloading_events}

Puede descargar sucesos en un archivo local. Puede descargar sucesos dentro del contexto de una sesión. Una sesión especifica los sucesos que se descargarán. Una vez finalizada la descarga, debe suprimir la sesión.
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} está en desuso. A partir del 9 de mayo de 2019, no se pueden suministrar nuevas instancias de {{site.data.keyword.cloudaccesstrailshort}}. Las instancias existentes del plan premium recibirán soporte hasta el 30 de septiembre de 2019. Para seguir supervisando la actividad de la cuenta de {{site.data.keyword.cloud_notm}} suministre una instancia de [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}


Siga los pasos siguientes para descargar los sucesos en un archivo local:

## Paso 1: Iniciar sesión en {{site.data.keyword.cloud_notm}}
{: #prereq}

Inicie una sesión en {{site.data.keyword.cloud_notm}}. Siga estos pasos:

1. Ejecute el mandato [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) para iniciar una sesión en {{site.data.keyword.cloud_notm}}.
2. Ejecute el mandato [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) para definir la organización y el espacio donde desea suministrar el servicio {{site.data.keyword.cloudaccesstrailshort}}.

**Nota:** establezca la organización y el espacio donde se suministra {{site.data.keyword.cloudaccesstrailshort}}.

## Paso 2: Identificar los sucesos que están disponibles
{: #step2}

Utilice el mandato `ibmcloud at status` para ver información sobre los sucesos que están disponibles en un dominio del espacio.

* Para obtener información sobre los sucesos de un dominio del espacio, ejecute el mandato `ibmcloud at status`.
* Para obtener información sobre los sucesos en el dominio de la cuenta, ejecute el mandato `ibmcloud at status` con la opción `-a`.

Para obtener más información, consulte [Visualización de la información de sucesos](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-viewing_event_status#viewing_event_status).
  


## Paso 3: Crear una sesión
{: #step3}

Se necesita una sesión para definir el ámbito de los datos de sucesos que se pueden descargar y para mantener el estado de la descarga. 

Utilice el mandato `ibmcloud at session create` para crear una sesión. De forma predeterminada, una sesión incluye datos correspondientes a las 2 últimas semanas.  Si lo desea, puede especificar la fecha de inicio y la fecha final cuando cree una sesión para especificar un rango de tiempo, una hora del día específica y el ámbito de los sucesos. 

**Nota:** 

* Si especifica la fecha de inicio y la fecha final, la sesión proporciona acceso a los sucesos comprendidos entre ambas fechas inclusive. 
* No se pueden descargar más de 2 semanas de datos por sesión. Por lo tanto, el intervalo de tiempo debe ser inferior a 2 semanas.
* Puede descargar sucesos para un dominio del espacio o para el dominio de la cuenta en una región.

Para crear una sesión que se utiliza para descargar los sucesos correspondientes a una fecha actual específica, ejecute el mandato siguiente:

```
ibmcloud at session create -s 2017-07-25 -e 2017-07-25
```
{: codeblock}

La sesión devuelve la siguiente información:

* El rango de fechas que se van a descargar.
* Información sobre si se deben incluir los sucesos disponibles para toda la cuenta o solo para el espacio actual. De forma predeterminada se obtienen los sucesos correspondientes al espacio en el que se ha iniciado la sesión.
* El ID de sesión necesario para descargar los sucesos.
* El ID de usuario que crea la sesión.

Por ejemplo,

```
$ ibmcloud at session create
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

**Sugerencia:** para ver la lista de sesiones activas, ejecute el mandato `ibmcloud at session list`.

Por ejemplo,

```
ibmcloud at session list
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
ibmcloud at download -o Events_File_Name Session_ID
```
{: codeblock}

donde

* Events_File_Name es el nombre del archivo de salida.
* Session_ID es el GUID de la sesión. Este valor se obtiene en el paso anterior. Utilice el valor para el campo **ID**.

Por ejemplo,

```
ibmcloud at download -o Events_File_Name.log 32c657c5-31c0-4a3c-a139-b380871c737a
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

Una vez finalizada la descarga, debe suprimir la sesión con el mandato `ibmcloud at session delete`. 

Ejecute el siguiente mandato para suprimir una sesión:

```
ibmcloud at session delete Session_ID
```
{: codeblock}

Donde Session_ID es el GUID de la sesión que ha creado en un paso anterior. Utilice el valor para el campo **ID**.

Por ejemplo,

```
ibmcloud at session delete 32c657c5-31c0-4a3c-a139-b380871c737a
+---------+------------------------+
| Name    | Value                  |
+---------+------------------------+
| message | Delete session success |
+---------+------------------------+
```
{: screen}




