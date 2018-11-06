---

copyright:
  years: 2016, 2018
lastupdated: "2018-07-09"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# CLI de IBM Cloud Activity Tracker
{: #at_cli_cloud}

Puede utilizar la CLI de {{site.data.keyword.cloudaccesstraillong}} para gestionar los sucesos de {{site.data.keyword.cloudaccesstrailshort}}.
{: shortdesc}

**Requisitos previos**
* Antes de ejecutar los mandatos, inicie una sesión en {{site.data.keyword.Bluemix}} con el mandato `ibmcloud login` para generar una señal de acceso y autenticar la sesión.
* Para gestionar sucesos con la CLI, debe tener un plan de pago.

El plugin de la CLI de {{site.data.keyword.cloudaccesstraillong}} admite plataformas Linux, Mac, y Windows.

<table>
  <caption>Mandatos para gestionar {{site.data.keyword.cloudaccesstrailshort}}</caption>
  <tr>
    <th>Mandato</th>
    <th>Cuándo utilizarlo</th>
  </tr>
  <tr>
    <td>[ibmcloud at](#base)</td>
    <td>Utilice este mandato para obtener información sobre la CLI, como la versión o la lista de mandatos.</td>
  </tr>
  <tr>
    <td>[ibmcloud at delete](#delete)</td>
    <td>Utilice este mandato para suprimir sucesos de {{site.data.keyword.cloudaccesstrailshort}}.</td>
  </tr>
  <tr>
    <td>[ibmcloud at download](#download)</td>
    <td>Utilice este mandato para descargar los registros {{site.data.keyword.cloudaccesstrailshort}} a un archivo local. </td>
  </tr>
  <tr>
    <td>[ibmcloud at help](#help)</td>
    <td>Utilice este mandato para obtener ayuda sobre cómo utilizar la CLI, y una lista de todos los mandatos.</td>
  </tr>
  <tr>
    <td>[ibmcloud at option](#option)</td>
    <td>Utilice este mandato para ver o cambiar las opciones de sucesos de {{site.data.keyword.cloudaccesstrailshort}}, como la retención, que están disponibles en un espacio o en una cuenta.</td>
  </tr>
  <tr>
    <td>[ibmcloud at session create](#session_create)</td>
    <td>Utilice este mandato para crear una sesión nueva.</td>
  </tr>
  <tr>
    <td>[ibmcloud at session delete](#session_delete)</td>
    <td>Utilice este mandato para suprimir una sesión.</td>
  </tr>  
  <tr>
    <td>[ibmcloud at session list](#session_list)</td>
    <td>Utilice este mandato para poner en lista sesiones activas en su ID.</td>
  </tr>  
  <tr>
    <td>[ibmcloud at session show](#session_show)</td>
    <td>Utilice este mandato para mostrar el estado de una sola sesión.</td>
  </tr>   
  <tr>
    <td>[ibmcloud at status](#status)</td>
    <td>Utilice este mandato para visualizar la información acerca del estado de sucesos que son almacenes en {{site.data.keyword.cloudaccesstrailshort}}.</td>
  </tr>
  </table>


## ibmcloud at
{: #base}

Proporciona información acerca de la versión de la CLI y cómo utilizar la CLI.

```
ibmcloud at [parámetros]
```
{: codeblock}

**Parámetros**

<dl>
<dt>--help, -h</dt>
<dd>Establezca este parámetro para mostrar la lista de mandatos o para obtener ayuda para un mandato.
</dd>

<dt>--version, -v</dt>
<dd>Establezca este parámetro para imprimir la versión de la CLI.</dd>
</dl>

**Ejemplos**

Para obtener la lista de mandatos, ejecute el siguiente mandato:

```
ibmcloud at --help
```
{: codeblock}

Para obtener la versión de la CLI, ejecute el mandato siguiente:

```
ibmcloud at --version
```
{: codeblock}


## ibmcloud at delete
{: #delete}

Suprime sucesos {{site.data.keyword.cloudaccesstrailshort}}.

```
ibmcloud at delete [parámetros] [argumentos..]
```
{: codeblock}

**Parámetros**

<dl>
  <dt>--start value, -s value</dt>
  <dd>(Opcional) Establece la fecha de inicio en hora universal coordinada (UTC): *AAAA-MM-DD*, por ejemplo, `2017-01-02`. <br>El valor predeterminado está establecido en hace 2 semanas. 
  </dd>
  
  <dt>--end value, -e value</dt>
  <dd>(Opcional) Establece la fecha de finalización en la hora universal coordinada (UTC): *AAAA-MM-DD* <br>El formato de la UTC de la fecha es **AAAA-MM-DD**, por ejemplo, `2017-01-02`. <br>El valor predeterminado se establece en la fecha actual.
  </dd>
  
  <dt>--search-time value, -T value</dt>
  <dd>(Opcional) Puede establecer este parámetro para suprimir los sucesos almacenados durante un número de horas un día específico. El formato del campo es: 0-23
  </dd>

</dl>


**Ejemplo**

Para suprimir eventos del 22 de junio de 2017, ejecute el siguiente mandato:
```
ibmcloud at delete -s 2017-06-22 -e 2017-06-22
```
{: codeblock}

Recibe información parecida a la del siguiente resultado:

`Deleted successfully`
`"6 logs were deleted, freeing 13737 bytes."`


## ibmcloud at download
{: #download}

Descarga sucesos de {{site.data.keyword.cloudaccesstrailshort}} a un archivo local o a una ventana del terminal en Windows y Mac OS X, o stdout en un terminal de Linux. 

**Nota:** Para descargar archivos debe crear primero una sesión. Una sesión define qué sucesos descargar en función del intervalo de fechas. Puede descargar sucesos dentro del contexto de una sesión. 

```
ibmcloud at download [parámetros] [argumentos...]
```
{: codeblock}

**Parámetros**

<dl>
<dt>--output value, -o value</dt>
<dd>(Opcional) Establece la vía de acceso y nombre de archivo de salida, en la que se han descargado los sucesos. <br>El valor predeterminado es un guión (-). <br>Establezca este parámetro en el valor predeterminado para dirigir los registros a la salida estándar.</dd>
</dl>

**Argumentos**

<dl>
<dt>ID de sesión</dt>
<dd>Establezca el valor de ID de sesión que obtiene al ejecutar el mandato `ibmcloud at session create`. Este valor indica qué sesión utilizar cuando se descargan sucesos. <br>**Nota:** el mandato `ibmcloud at session create` proporciona los parámetros que controlan qué sucesos se descargan. </dd>
</dl>

**Nota:** Después de completarse la descarga, para descargar de nuevo la misma fecha, debe utilizar un archivo diferente o iniciar una sesión distinta.

**Ejemplo**

Para descargar sucesos en un archivo denominado `events.log`, ejecute el siguiente mandato:

```
ibmcloud at download -o events.log 1db6ce16-824d-4d50-bd40-37f1d8fea9b7
```
{: screen}

Recibe información parecida a la del siguiente resultado: 

```
6.70 KiB / 3.06 KiB [========] 219.03% 8.60 MiB/s 0s
Download completed successfully
```
{: screen}


## ibmcloud at help
{: #help}

Proporciona información acerca de cómo utilizar un mandato.

```
ibmcloud at help [parámetros]
```
{: codeblock}

**Parámetros**

<dl>
<dt>Mandato</dt>
<dd>Establecer el nombre del mandato para el cual quiere obtener ayuda.
</dd>
</dl>


**Ejemplo**

Para obtener ayuda sobre cómo ejecutar el mandato para ver el estado de {{site.data.keyword.cloudaccesstrailshort}}, ejecute el mandato siguiente:

```
ibmcloud at help status
```
{: codeblock}


## ibmcloud at option
{: #option}

Muestra o cambia el periodo de retención para los sucesos que están disponibles en un espacio. Cuando se establece una política de retención, los sucesos se suprimen automáticamente cuando se alcanza el número de días de retención.

* El periodo se establece en el número de días.
* El valor predeterminado es **-1**, es decir, los sucesos se almacenan y no se suprimen.

**Nota:** De forma predeterminada, se almacenan todos los sucesos. Si no establece un periodo de retención, debe suprimirlos manualmente utilizando el mandato `ibmcloud at delete`. 

```
ibmcloud at option [parámetros] [argumentos...]
```
{: codeblock}

**Parámetros**

<dl>
<dt>--retention value, -r value</dt>
<dd>(Opcional) Establece el número de días de retención. <br> El valor predeterminado es *-1* días.</dd>

<dt>--at-account-level, -a</dt>
<dd>(Opcional) Establezca este parámetro para ver una lista con la información sobre el periodo de retención para los sucesos almacenados en cada dominio de espacio y en el dominio de la cuenta.

</dl>

**Ejemplo**

Para visualizar el período de retención actual para el espacio donde está iniciado, ejecute el mandato siguiente:

```
ibmcloud at option
```
{: codeblock}

El resultado es similar al siguiente:

```
+--------------------------------------+-----------+
|               SPACEID                | RETENTION |
+--------------------------------------+-----------+
| 2af890ce-fb4f-4e41-a975-901a56ed1f11 |        30 |
+--------------------------------------+-----------+
```
{: screen}


Para cambiar el periodo de retención a 25 días del espacio donde ha iniciado sesión, ejecute el mandato siguiente:

```
ibmcloud at option -r 25
```
{: codeblock}

El resultado es similar al siguiente:

```
+--------------------------------------+-----------+
|               SPACEID                | RETENTION |
+--------------------------------------+-----------+
| 2af890ce-fb4f-4e41-a975-901a56ed1f11 |        25 |
+--------------------------------------+-----------+
```
{: screen}



## ibmcloud at session create
{: #session_create}

Crea una nueva sesión.

**Nota:** Puede tener hasta 30 sesiones simultáneas en un espacio. La sesión se crea para un usuario. Sesiones puede compartirse entre usuarios en un espacio.

```
ibmcloud at session create [parámetros] [argumentos...]
```
{: codeblock}

**Parámetros**

<dl>
  <dt>--at-account-level, -a </dt>
  <dd>(Opcional) Establece el ámbito de nivel de cuenta. </br>Establezca este valor para obtener información de la cuenta. <br>Si no se especifica este parámetro, el valor predeterminado se establece solo en el espacio actual, es decir, el espacio donde ha iniciado la sesión mediante el mandato `ibmcloud cf login`.
  </dd>

  <dt>--start value, -s value</dt>
  <dd>(Opcional) Establece la fecha de inicio en hora universal coordinada (UTC): *AAAA-MM-DD*, por ejemplo, `2017-01-02`. <br>El valor predeterminado está establecido en hace 2 semanas. 
  </dd>
  
  <dt>--end value, -e value</dt>
  <dd>(Opcional) Establece el fin de la fecha en hora universal coordinada (UTC): *AAAA-MM-DD*, por ejemplo, `2017-01-02`. <br>El valor predeterminado se establece en la fecha actual. 
  </dd>

  <dt>--search-time value, -T value</dt>
  <dd>(Opcional) Puede establecer este parámetro para suprimir los sucesos almacenados durante un número de horas un día específico. El formato del campo es: 0-23
  </dd>


 </dl>

**Valores devueltos**

<dl>
<dt>Access-Time</dt>
<dd>Indicación de fecha y hora que muestra cuándo se ha utilizado la sesión por última vez.</dd>

<dt>Create-Time</dt>
<dd>Indicación de fecha y hora correspondiente a la fecha y hora en que se ha creado la sesión.</dd>

<dt>Date-Range</dt>
<dd>Indica los días que se utilizan para filtrar sucesos. Los sucesos que se identifican en este rango de fechas están disponibles para la gestión mediante la sesión.</dd>

<dt>ID</dt>
<dd>ID de sesión.</dd>

<dt>Espacio</dt>
<dd>ID de espacio en el que la sesión está activa.</dd>

<dt>Type-Account</dt>
<dd>Este valor está establecido en **ActivityTracker**.</dd>

<dt>Nombre de usuario</dt>
<dd>{{site.data.keyword.IBM_notm}}El ID del usuario que ha creado la sesión.</dd>
</dl>


**Ejemplo**

Para crear una sesión para el 10 de julio de 2017, ejecute el siguiente mandato:

```
ibmcloud at session create -s 2017-07-10 -e 2017-07-10
```
{: screen}

El resultado es similar al siguiente:

```
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| id           | 9b8c4db8-5841-4993-a449-305815a53a8e      |
| space        | xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx      |
| username     | xxx@yyy.com                               |
| create-time  | 2017-07-25T11:54:00.20042645Z             |
| access-time  | 2017-07-25T11:54:00.20042645Z             |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
+--------------+-------------------------------------------+
```
{: screen}



## ibmcloud at session delete
{: #session_delete}

Suprime una sesión que está especificada por un ID de sesión.

```
ibmcloud at session delete [argumentos...]
```
{: codeblock}


**Argumentos**

<dl>
<dt>ID de sesión</dt>
<dd>ID de la sesión que desea suprimir. <br>Puede utilizar el mandato `ibmcloud at session list` para obtener todos los ID de sesión activos.</dd>
</dl>

**Ejemplo**

Para suprimir una sesión con ID de sesión *9b8c4db8-5841-4993-a449-305815a53a8e*, ejecute el siguiente mandato:

```
ibmcloud at session delete 9b8c4db8-5841-4993-a449-305815a53a8e
```
{: screen}

El resultado es similar al siguiente:

```
+---------------+--------------------------+
|    NAME       |     VALUE                |
+---------------+--------------------------+
|  message      | Delete session success   |
+---------------+--------------------------+
```
{: screen}


## ibmcloud at session list
{: #session_list}

Muestra una lista de las sesiones activas y sus ID.

```
ibmcloud at session list 
```
{: codeblock}

**Valores devueltos**

<dl>
<dt>ID</dt>
<dd>ID de sesión.</dd>

<dt>ESPACIO</dt>
<dd>ID de espacio en el que la sesión está activa.</dd>

<dt>USERNAME</dt>
<dd>{{site.data.keyword.IBM_notm}}El ID del usuario que ha creado la sesión.</dd>

<dt>CREATE-TIME</dt>
<dd>Indicación de fecha y hora correspondiente a la fecha y hora en que se ha creado la sesión.</dd>

<dt>ACCESS-TIME</dt>
<dd>Indicación de fecha y hora que indica cuando se ha utilizado la última sesión.</dd>
</dl>
 
**Ejemplo**

Para listar las sesiones, ejecute el siguiente mandato:

```
ibmcloud at session list
```
{: screen}

El resultado es similar al siguiente:

```
+--------------------------------------+--------------------------------------+-----------------------------------+--------------------------------+--------------------------------+
| ID                                   | SPACE                                | USERNAME                          | CREATE-TIME                    | ACCESS-TIME                    |
+--------------------------------------+--------------------------------------+-----------------------------------+--------------------------------+--------------------------------+
| fa3f1970-21f3-4e32-b480-1ffb41badc16 | 12345678-fb4f-acdf-a975-11335678r3fg | xxx@yyy.com                       | 2017-07-10T09:04:07.916788069Z | 2017-07-10T09:04:07.916788069Z |
| 9b8c4db8-5841-4993-a449-305815a53a8e | 12345678-fb4f-acdf-a975-11335678r3fg | xxx@yyy.com                       | 2017-07-11T09:19:14.666532796Z | 2017-07-12T09:19:14.666532796Z |
+--------------------------------------+--------------------------------------+-----------------------------------+--------------------------------+--------------------------------+
```
{: screen}


## ibmcloud at session show
{: #session_show}

Muestra el estado de una sola sesión.

```
ibmcloud at session show [argumentos...]
```
{: codeblock}

**Argumentos**

<dl>
<dt>ID de sesión</dt>
<dd>ID de la sesión activa para la que desea obtener información.</dd>
</dl>

**Valores devueltos**

<dl>
<dt>Access-Time</dt>
<dd>Indicación de fecha y hora que indica cuando se ha utilizado la última sesión.</dd>

<dt>Create-Time</dt>
<dd>Indicación de fecha y hora correspondiente a la fecha y hora en que se ha creado la sesión.</dd>

<dt>Date-Range</dt>
<dd>Indica los días que se utilizan para filtrar sucesos. Los sucesos que se identifican en este rango de fechas están disponibles para la gestión mediante la sesión.</dd>

<dt>id</dt>
<dd>ID de sesión.</dd>

<dt>Espacio</dt>
<dd>ID de espacio en el que la sesión está activa.</dd>

<dt>Type-Account</dt>
<dd>Este valor está establecido en **ActivityTracker**.</dd>

<dt>Nombre de usuario</dt>
<dd>{{site.data.keyword.IBM_notm}}El ID del usuario que ha creado la sesión.</dd>
</dl>

**Ejemplo**

Para mostrar detalles de una sesión con ID de sesión *9b8c4db8-5841-4993-a449-305815a53a8e*, ejecute el siguiente mandato:

```
ibmcloud at session show 9b8c4db8-5841-4993-a449-305815a53a8e
```
{: screen}

El resultado es similar al siguiente:

```
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| create-time  | 2017-07-25T11:54:00.20042645Z             |
| access-time  | 2017-07-25T11:54:00.20042645Z             |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
| id           | 9b8c4db8-5841-4993-a449-305815a53a8e      |
| space        | xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx      |
| username     | xxx@yyy.com                               |
+--------------+-------------------------------------------+
```
{: screen}


## ibmcloud at status
{: #status}

Devuelve información sobre el estado de los sucesos de {{site.data.keyword.cloudaccesstrailshort}}.

```
ibmcloud at status [parámetros] [argumentos...]
```
{: codeblock}

**Parámetros**

<dl>
  <dt>--start value, -s value</dt>
  <dd>(Opcional) Establece la fecha de inicio en hora universal coordinada (UTC): *AAAA-MM-DD*, por ejemplo, `2017-01-02`. <br>El valor predeterminado está establecido en hace 2 semanas.
  </dd>
  
  <dt>--end value, -e value</dt>
  <dd>(Opcional) Establece la fecha final en hora universal coordinada (UTC): *AAAA-MM-DD*, por ejemplo, `2017-01-02`. <br>El valor predeterminado se establece en la fecha actual.
  </dd>
  
  <dt>--at-account-level, -a </dt>
  <dd>(Opcional) Establece el ámbito de nivel de cuenta. <br> **Nota:** Establezca este valor para obtener información de la cuenta. <br>Si no se especifica este parámetro, el valor predeterminado se establece solo en el espacio actual, es decir, el espacio donde ha iniciado la sesión mediante el mandato `ibmcloud cf login`.
  </dd>
  
</dl>


**Nota:** El mandato `ibmcloud at status` solo muestra las dos últimas semanas de sucesos que se han almacenado en {{site.data.keyword.cloudaccesstrailshort}} si no se especifican fechas de inicio y final. 

**Valores devueltos**   

<dl>
  <dt>DATE</dt>
  <dd>Fecha en Universal Coordinated Time (UTC): *AAAA-MM-DD*, por ejemplo, `2017-01-02`. 
  </dd>
  
  <dt>COUNT</dt>
  <dd>Número total de sucesos.
  </dd>
  
  <dt>SIZE</dt>
  <dd>El tamaño total de los sucesos en megabytes.
  </dd>

  <dt>TYPES</dt>
  <dd>Este valor está establecido en **ActivityTracker**.
  </dd>
  
  <dt>SEARCHABLE</dt>
  <dd>Este campo indica si hay sucesos disponibles para la búsqueda en Kibana. <br>Si el valor del campo **SEARCHABLE** está establecido en *None*, los sucesos están disponibles para su descarga, pero no los puede analizar en Kibana.
  </dd>
  
</dl>

**Ejemplo**

Para mostrar detalles de los sucesos del 20 de julio de 2017, ejecute el mandato siguiente:

```
ibmcloud at status -s 2017-07-20 -e 2017-07-20
```
{: codeblock}


Recibe información parecida a la del siguiente resultado:

```
+------------+-----------+-------+------------------+--------------+
|   Date     |  Count    | Size  | Types            |  Searchable  |
+------------+-----------+-------+------------------+--------------+
| 2017-07-20 |    1      | 2531  | ActivityTracker  | All          |
+------------+-----------+-------+------------------+--------------+
```
{: screen}


