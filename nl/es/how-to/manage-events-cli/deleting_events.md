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

# Supresión de sucesos
{: #deleting_events}

Utilice el mandato *cf at delete* para suprimir manualmente los sucesos almacenados en {{site.data.keyword.cloudaccesstrailshort}} para un espacio de {{site.data.keyword.Bluemix}}.{:shortdesc}

## Supresión de sucesos
{: #viewing_events}

Utilice el mandato `cf at status` para ver el tamaño y el recuento, y si los sucesos están disponibles o no para el análisis en Kibana. Para obtener más información, consulte [cf at status](/docs/services/cloud-activity-tracker/cli/at_cli.html#status).

1. Inicie una sesión en una región, organización y espacio de {{site.data.keyword.Bluemix_notm}}.  

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

2. Ejecute el mandato *cf at status*. 

    ```
    $ bx cf at status -a -s YYYY-MM-DD -e YYYY-MM-DD
    ```
    {: codeblock}
    
    donde 
    
    * *-a* se utiliza para especificar que la solicitud se aplica a todos los espacios en la cuenta.
    * *-s* se utiliza para establecer la fecha de inicio en Hora Universal Coordinada (UTC): *AAAA-MM-DD*.
    * *-e* se utiliza para establecer la fecha final en Hora Universal Coordinada (UTC): *AAAA-MM-DD*.
    	
	Utilice el mandato `cf at status` con las opciones **-s** para establecer el día de inicio y **-e** para establecer la fecha final. Por ejemplo: 

    * `bx cf at status` proporciona información correspondiente a las 2 últimas semanas.
    * `bx cf at status -s 2017-05-03` proporciona información desde el 3 de mayo de 2017 hasta la fecha actual. 
    * `bx cf at status -s 2017-05-03 -e 2017-05-08` proporciona información entre el 3 de mayo de 2017 y el 8 de mayo de 2017. 
 
    Utilice el mandato `cf at status` con la opción **-a** para establecer el dominio en la cuenta. 
	
    Por ejemplo, para obtener información sobre los sucesos disponibles correspondiente al 10 de junio de 2017, ejecute el siguiente mandato: 
    
    ```
    $ bx cf at status -s 2017-06-10 -e 2017-06-10
    +------------+-------+------+------------+
    | Date       | Count | Size | Searchable |
    +------------+-------+------+------------+
    | 2017-07-10 | 1     | 2531 | All        |
    +------------+-------+------+------------+
    ```
    {: screen}
	














