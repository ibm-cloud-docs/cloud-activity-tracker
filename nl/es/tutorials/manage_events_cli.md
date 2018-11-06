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



# Gestión de sucesos mediante la CLI de Activity Tracker
{: #tutorial2}

Utilice esta guía de aprendizaje para aprender a utilizar la CLI de {{site.data.keyword.cloudaccesstrailshort}} para gestionar sucesos a través de la línea de mandatos. Aprenda a obtener información sobre sucesos almacenados, cómo descargar los sucesos almacenados en {{site.data.keyword.IBM_notm}} Cloud o cómo suprimir sucesos.
{:shortdesc}

Siga estos pasos:

1. [Suministre {{site.data.keyword.keymanagementservicelong_notm}} y genere sucesos](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step1)
2. [Obtenga información sobre sucesos almacenados (ibmcloud at status)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step2)
2. [Especifique los registros que desea descargar mediante la creación de una sesión (ibmcloud at session create)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step3)
3. [Obtenga los datos de registro real (ibmcloud at download)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step4)
4. [Suprima la sesión después de que finalice la descarga (ibmcloud at session delete)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step5)
5. [Suprima manualmente los registros que no se necesiten (ibmcloud at delete)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step6)


## Supuestos
{: #assumptions}

1. Tiene un ID de usuario de {{site.data.keyword.Bluemix_notm}} con permisos de desarrollador para trabajar en un espacio de una cuenta de {{site.data.keyword.Bluemix_notm}} en la que se suministra el servicio {{site.data.keyword.cloudaccesstrailshort}}. 

    Para obtener más información sobre cómo suministrar el servicio {{site.data.keyword.cloudaccesstrailshort}}, consulte [Suministro del servicio {{site.data.keyword.cloudaccesstrailshort}} ](/docs/services/cloud-activity-tracker/how-to/provision.html#provision).

2. Ha suministrado una instancia del servicio {{site.data.keyword.cloudaccesstrailshort}} con un plan premium.

    **Nota:** la CLI de {{site.data.keyword.cloudaccesstrailshort}} no está disponible con el plan Lite.

3. Ha instalado la CLI de {{site.data.keyword.cloudaccesstrailshort}} en el sistema local. Esto es necesario para poder utilizar la CLI de {{site.data.keyword.cloudaccesstrailshort}} para gestionar sucesos a través de la línea de mandatos. 

    Para obtener más información sobre cómo instalar la CLI de {{site.data.keyword.cloudaccesstrailshort}}, consulte [Configuración de la CLI de {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/how-to/config_cli.html#config_cli).

4. Ha iniciado una sesión en {{site.data.keyword.Bluemix_notm}} mediante la línea de mandatos. En esta guía de aprendizaje, ejecute los siguientes mandatos desde un terminal: 

    `ibmcloud login -a api.ng.bluemix.net` para iniciar una sesión en la región EE.UU. sur. Para obtener más información, consulte [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login).
    
    `ibmcloud target -o OrgName -s SpaceName` para definir la organización y el espacio de destino donde se suministrará el servicio {{site.data.keyword.cloudaccesstrailshort}}. Para obtener más información, consulte [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target).


## Paso 1: Suministrar el servicio IBM Key Protect y generar sucesos 
{: #step1}
	
Siga estos pasos para suministrar el servicio {{site.data.keyword.keymanagementserviceshort}} en {{site.data.keyword.Bluemix_notm}} y generar sucesos:

1. Suministre una instancia del servicio {{site.data.keyword.keymanagementserviceshort}} en la región EE.UU. sur. Para obtener más información, consulte [Suministro desde la consola de IBM Cloud](/docs/services/key-protect/provision.html#provision).

2. Defina los permisos de {{site.data.keyword.Bluemix_notm}} para el usuario que va a utilizar para trabajar con claves. 

    * Un usuario necesita una política de IAM con el rol de servicio *gestor (manager)* o *escritor (writer)* para poder crear claves.
	* Un usuario necesita una política de IAM con el rol de servicio *gestor (manager)* para poder suprimir claves.
	* Un usuario necesita una política de IAM con el rol de servicio *lector (reader)* para poder ver claves. 

3. Cree una clave de seguridad utilizando el servicio {{site.data.keyword.keymanagementserviceshort}} para generar datos de sucesos de {{site.data.keyword.cloudaccesstrailshort}}. Para obtener más información, consulte [Creación de claves nuevas](/docs/services/key-protect/create-standard-keys.html#create-standard-keys).

Como resultado de crear una clave se generan sucesos de {{site.data.keyword.cloudaccesstrailshort}}.

## Paso 2: Obtener información sobre sucesos almacenados
{: #step2}

Los sucesos de {{site.data.keyword.keymanagementserviceshort}} están disponibles en el dominio de la cuenta de {{site.data.keyword.cloudaccesstrailshort}}.

En esta guía de aprendizaje, los sucesos de {{site.data.keyword.keymanagementserviceshort}} están disponibles en el dominio de cuenta de EE.UU. sur, que es la región en la que se ha suministrado el servicio {{site.data.keyword.keymanagementserviceshort}}. 

Ejecute el mandato siguiente para obtener información sobre los sucesos recopilados en una fecha específica:

```
ibmcloud at status -s startDate -e endDate -a
```
{: codeblock}

donde 

* `-s` se utiliza para definir el día inicial. 
* `startDate` representa la fecha inicial. El formato es *AAAA-MM-DD*.
* `-e` especifica la fecha final.
* `endDate` representa la fecha final. El formato es *AAAA-MM-DD*.
* `-a` indica que se deben incluir sucesos en el dominio de la cuenta.

Por ejemplo:

```
ibmcloud at status -s 2017-07-25 -e 2017-07-25 -a
+------------+-------+-------+------------+
| Date       | Count | Size  | Searchable |
+------------+-------+-------+------------+
| 2017-07-25 | 12    | 34994 | All        |
+------------+-------+-------+------------+
```
{: screen}

Este mandato contará los sucesos correspondientes al 25 de junio de 2017.  {{site.data.keyword.cloudaccesstrailshort}} es un servicio global, por lo tanto, los días están en Hora Universal. Para obtener un día en hora local, probablemente tendrá que descargar varios días UTC.




## Paso 3: Especificar los sucesos que se van a descargar
{: #step3}

Antes de descargar sucesos, cree una sesión. La sesión especifica los sucesos que se descargarán.


Utilice el mandato siguiente para crear una sesión:

```
ibmcloud at session create -s startDate -e endDate -a
```
{: codeblock}

donde 

* `-s` se utiliza para definir el día inicial. 
* `startDate` representa la fecha inicial. El formato es *AAAA-MM-DD*.
* `-e` especifica la fecha final.
* `endDate` representa la fecha final. El formato es *AAAA-MM-DD*.
* `-a` indica que se deben incluir sucesos en el dominio de la cuenta.

Por ejemplo:

```
ibmcloud at session create -s 2017-07-25 -e 2017-07-25 -a
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
{: screen}

donde 

* `-s` se utiliza para definir el día inicial.
* `-e` especifica la fecha final.
* `-a` indica que se deben incluir sucesos en el dominio de la cuenta.

Hay una fecha de inicio y una fecha final asociadas a una sesión. El mandato de descarga incluirá los sucesos comprendidos entre ambas fechas inclusive.

La parte importante de la salida del mandato es el `ID` de sesión. Se hace referencia al mismo en el mandato de descarga.

Para obtener información sobre las sesiones existentes, escriba `ibmcloud at session list`.

Para obtener más información sobre las sesiones y el mandato `ibmcloud at session create`, consulte la [Referencia de CLI](/docs/services/cloud-activity-tracker/reference/at_cli_cloud.html#session_create).

Utilice `ibmcloud at session help create` para obtener ayuda desde la línea de mandatos.

## Paso 4: Descargue los sucesos identificados para el ámbito definido para la sesión
{: #step4}

Para descargar los sucesos especificados por los parámetros de la sesión, ejecute el siguiente mandato:

```
ibmcloud at events download -o outputFile sessionID
```
{: codeblock}

* El parámetro `-o` especifica un archivo de salida.
* `outputFile` es el nombre del archivo local.
* `sessionID` se especifica en último lugar. El valor de ID de sesión se obtiene de la salida del mandato `ibmcloud at session create` mandato.

El formato de los datos descargados es JSON comprimido. 

Por ejemplo:

```
$ ibmcloud at events download -o events.log 21b19aeb-3d32-4c60-b912-517609c62db2
 6.70 KiB / 3.06 KiB [================================================================================================================================================================] 219.03% 8.60 MiB/s 0s
Download Successful
```
{: screen} 

El indicador de progreso pasa de 0 a 100% a medida que los sucesos se descargan.

Para obtener más información sobre el mandato `ibmcloud at download`, consulte la [Referencia de CLI](/docs/services/cloud-activity-tracker/reference/at_cli_cloud.html#download).

Utilice `ibmcloud at help download` para obtener ayuda desde la línea de mandatos.

## Paso 5: Suprimir la sesión
{: #step5}

Una vez finalizada la descarga, suprima la sesión. Ejecute el mandato siguiente:

```
ibmcloud at session delete sessionID
```
{: codeblock}

donde 

* `sessionID` es el ID de la sesión que desea suprimir.

El número de sesiones es limitado. Una sesión no se suprime automáticamente. Debe suprimir manualmente las sesiones que no necesite. 

Por ejemplo: 

```
$ ibmcloud at session delete 21b19aeb-3d32-4c60-b912-517609c62db2
+---------+------------------------+
| name    | value                  |
+---------+------------------------+
| message | Delete session success |
+---------+------------------------+
```
{: screen}

Para obtener más información sobre el mandato `ibmcloud at session delete`, consulte la [Referencia de CLI](/docs/services/cloud-activity-tracker/reference/at_cli_cloud.html#session_delete).

Utilice `ibmcloud at session help delete` para obtener ayuda desde la línea de mandatos.

## Paso 6: Suprimir sucesos de Activity Tracker automáticamente
{: #step6}

El usuario tiene el control de su propia retención de sucesos en {{site.data.keyword.cloudaccesstrailshort}}. Puede suprimir sucesos manualmente, o puede automatizar la supresión de sucesos.

Para suprimir sucesos manualmente de un espacio, ejecute el mandato `ibmcloud at delete`. Por ejemplo,

```
$ ibmcloud at delete -s 2017-07-25 -e 2017-07-25
Deleted successfully
"6 logs were deleted,freeing 13737 bytes."
```

Para obtener más información sobre el mandato `ibmcloud at delete`, consulte la [Referencia de CLI](/docs/services/cloud-activity-tracker/reference/at_cli_cloud.html#delete).

Utilice `ibmcloud at help delete` para obtener ayuda desde la línea de mandatos.

**Nota:** Para suprimir sucesos automáticamente, puede definir una política de retención mediante el mandato de CLI `ibmcloud at option`. Para obtener más información, consulte la [Referencia de CLI](/docs/services/cloud-activity-tracker/reference/at_cli_cloud.html#option)


