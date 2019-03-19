---

copyright:
  years: 2016, 2019
lastupdated: "2019-01-23"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# Configuración de la política de retención de sucesos
{: #configuring_retention_policy}

Utilice el mandato **ibmcloud at option** para ver y configurar la política de retención que define el número máximo de días que se conservan los sucesos en {{site.data.keyword.cloudaccesstrailshort}}. De forma predeterminada, la política de retención está inhabilitada y los sucesos se conservan indefinidamente. Una vez transcurrido el periodo de retención, los sucesos se suprimen automáticamente. 
{:shortdesc}

Puede establecer la misma política de retención para todos los espacios de la cuenta o puede personalizar el periodo de retención para un espacio. 


## Inhabilitación de la política de retención de sucesos para un espacio
{: #disable_retention_policy_space}

Siga los siguientes pasos para inhabilitar una política de retención:

1. Inicie una sesión en {{site.data.keyword.cloud_notm}}. 

    Ejecute el mandato [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) para iniciar una sesión en {{site.data.keyword.cloud_notm}} y luego ejecute el mandato [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) para definir la organización y el espacio donde desea suministrar el servicio {{site.data.keyword.cloudaccesstrailshort}}.
	
2. Establezca el periodo de retención en **-1** para inhabilitar el periodo de retención. Ejecute el mandato:

    ```
    ibmcloud at option -r -1
    ```
    {: codeblock}
    
**Ejemplo**
    
Por ejemplo, para inhabilitar el periodo de retención para un espacio con el ID *d35da1e3-b345-475f-8502-bx cfgh436902a3*, ejecute el mandato siguiente:

```
ibmcloud at option -r -1
```
{: codeblock}

La salida es:

```
+-----------------------------------------+-----------+
|               SPACEID                   | RETENTION |
+-----------------------------------------+-----------+
| d35da1e3-b345-475f-8502-bx cfgh436902a3 |        -1 |
+-----------------------------------------+-----------+
```
{: screen} 



## Comprobación de la política de retención de registros para un espacio
{: #check_retention_policy_space}

Para obtener el periodo de retención establecido para un espacio de {{site.data.keyword.cloud_notm}}, siga los pasos siguientes:

1. Inicie una sesión en {{site.data.keyword.cloud_notm}}. 

    Ejecute el mandato [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) para iniciar una sesión en {{site.data.keyword.cloud_notm}} y luego ejecute el mandato [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) para definir la organización y el espacio donde desea suministrar el servicio {{site.data.keyword.cloudaccesstrailshort}}.
	
2. Obtenga el periodo de retención. Ejecute el mandato:

    ```
    ibmcloud at option
    ```
    {: codeblock}

    La salida para el ID de espacio *d35da1e3-b345-475f-8502-bx cfgh436902a3* es 30 días:

    ```
    +-----------------------------------------+-----------+
    |               SPACEID                   | RETENTION |
    +-----------------------------------------+-----------+
    | d35da1e3-b345-475f-8502-bx cfgh436902a3 |        30 |
    +-----------------------------------------+-----------+
    ```
    {: screen}
    

## Comprobación de la política de retención de registros para todos los espacios de una cuenta
{: #check_retention_policy_account}

Para obtener el periodo de retención establecido para cada espacio de {{site.data.keyword.cloud_notm}} de una cuenta, lleve a cabo los siguientes pasos:

1. Inicie una sesión en {{site.data.keyword.cloud_notm}}. 

    Ejecute el mandato [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) para iniciar una sesión en {{site.data.keyword.cloud_notm}} y luego ejecute el mandato [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) para definir la organización y el espacio donde desea suministrar el servicio {{site.data.keyword.cloudaccesstrailshort}}.
    
2. Obtenga el periodo de retención para cada espacio de la cuenta. Ejecute el mandato:

    ```
    ibmcloud at option -a
    ```
    {: codeblock}
	
	donde *-a* indica que la información incluye todos los espacios de la cuenta.

    Por ejemplo, el resultado de ejecutar el mandato es:

    ```
    +-----------------------------------------+-----------+
    |               SPACEID                   | RETENTION |
    +-----------------------------------------+-----------+
    | d35da1e3-b345-475f-8502-bx cfgh436902a3 |        30 |
    +-----------------------------------------+-----------+
    | fdew45e3-b345-4365-8502-bx cfghrfthy5a3 |        30 |
    +-----------------------------------------+-----------+
    ```
    {: screen}
    

## Establecimiento de la política de retención de registros en la cuenta
{: #set_retention_policy_space}

Para establecer el periodo de retención para una cuenta de {{site.data.keyword.cloud_notm}}, siga los pasos siguientes:

1. Inicie una sesión en {{site.data.keyword.cloud_notm}}. 

    Ejecute el mandato [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) para iniciar una sesión en {{site.data.keyword.cloud_notm}} y luego ejecute el mandato [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) para definir la organización y el espacio donde desea suministrar el servicio {{site.data.keyword.cloudaccesstrailshort}}.
	
2. Establezca el periodo de retención. Ejecute el mandato:

    ```
    ibmcloud at option -r Number_of_days - a
    ```
    {: codeblock}
    
    donde 
	* *-r* es la opción que se debe especificar para definir un periodo de retención.
	* *Number_of_days* es un entero que define el número de días que desea conservar los sucesos. 
	* *-a* indica que la solicitud se aplica a todos los espacios de la cuenta.
    
    
**Ejemplo**
    
Por ejemplo, para conservar cualquier tipo de registro en su cuenta durante solo 15 días, ejecute el mandato siguiente:

```
ibmcloud at option -r 15 -a
```
{: codeblock}

El resultado muestra una entrada para cada espacio de la cuenta e incluye información sobre el periodo de retención:

```
+-----------------------------------------+-----------+
|               SPACEID                   | RETENTION |
+-----------------------------------------+-----------+
| d35da1e3-b345-475f-8502-bx cfgh436902a3 |        15 |
+-----------------------------------------+-----------+
| fdew45e3-b345-4365-8502-bx cfghrfthy5a3 |        15 |
+-----------------------------------------+-----------+
```
{: screen}

## Establecimiento de la política de retención de registros para un espacio
{: #set_retention_policy_account}

Para establecer el periodo de retención para un espacio de {{site.data.keyword.cloud_notm}}, siga los pasos siguientes:

1. Inicie una sesión en {{site.data.keyword.cloud_notm}}. 

    Ejecute el mandato [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) para iniciar una sesión en {{site.data.keyword.cloud_notm}} y luego ejecute el mandato [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) para definir la organización y el espacio donde desea suministrar el servicio {{site.data.keyword.cloudaccesstrailshort}}.
    
2. Establezca el periodo de retención. Ejecute el mandato:

    ```
    ibmcloud at option -r Number_of_days
    ```
    {: codeblock}
    
    donde 
	* *-r* es la opción que se debe especificar para definir un periodo de retención.
	* *Number_of_days* es un entero que define el número de días que desea conservar los sucesos.
    
    
**Ejemplo**
    
Por ejemplo, para conservar los sucesos que están disponibles en un espacio durante un año, ejecute el mandato siguiente:

```
ibmcloud at option -r 365
```
{: codeblock}

La salida es:

```
+-----------------------------------------+-----------+
|               SPACEID                   | RETENTION |
+-----------------------------------------+-----------+
| d35da1e3-b345-475f-8502-bx cfgh436902a3 |       365 |
+-----------------------------------------+-----------+
```
{: screen}


