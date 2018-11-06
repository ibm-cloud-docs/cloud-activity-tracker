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


# Configuración de la CLI de Activity Tracker
{: #config_cli}

El servicio {{site.data.keyword.cloudaccesstraillong}} incluye una interfaz de línea de mandatos (CLI) que puede utilizar para gestionar los sucesos en la nube. Puede utilizar el plugin de {{site.data.keyword.Bluemix_notm}} para ver el estado de los sucesos, para descargar sucesos y para configurar la política de retención de sucesos. La CLI ofrece distintos tipos de ayuda: ayuda general para obtener información sobre la CLI y los mandatos soportados, ayuda sobre mandatos para ver cómo se utiliza un mandato o ayuda sobre submandatos para aprender a utilizar un submandato de un mandato.
{:shortdesc}


## Instalación del plugin de {{site.data.keyword.cloudaccesstrailshort}} desde el repositorio de {{site.data.keyword.Bluemix_notm}}
{: #install_cli_repo}

Para instalar la CLI de {{site.data.keyword.cloudaccesstrailshort}},
siga estos pasos:

1. Instale la CLI de {{site.data.keyword.Bluemix_notm}}.

   Para obtener más información, consulte [Instalación de la CLI de {{site.data.keyword.Bluemix_notm}}](/docs/cli/reference/ibmcloud/download_cli.html#install_use).
   
2. Averigüe el nombre del plugin en el repositorio. Ejecute el mandato siguiente:

    ```
    ibmcloud plugin repo-plugins
    ```
    {: codeblock}
    
    El nombre del plugin es **activity-tracker**.

3. Instale el plugin de {{site.data.keyword.cloudaccesstrailshort}}. Ejecute el mandato siguiente:

    ```
    ibmcloud plugin install activity-tracker -r Bluemix
    ```
    {: codeblock}
 
4. Verifique que el plugin de {{site.data.keyword.cloudaccesstrailshort}} está instalado.
  
    Por ejemplo, ejecute el mandato siguiente para ver la lista de los plugins que están instalados:
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    
    El resultado se parecerá al siguiente:
   
    ```
    ibmcloud plugin list
    Listing installed plug-ins...

    Plugin Name               Version   
    activity-tracker          3.3.0   
    ```
    {: screen}


## Instalación del plugin de {{site.data.keyword.cloudaccesstrailshort}} desde un archivo
{: #install_cli}

Para instalar la CLI de {{site.data.keyword.cloudaccesstrailshort}},
siga estos pasos:

1. Instale la CLI de {{site.data.keyword.Bluemix_notm}}.

   Para obtener más información, consulte [Instalación de la CLI de {{site.data.keyword.Bluemix_notm}}](/docs/cli/reference/ibmcloud/download_cli.html#install_use).

2. Instale el plugin de {{site.data.keyword.cloudaccesstrailshort}}.

    * Para Linux, consulte [Instalación del plugin de {{site.data.keyword.cloudaccesstrailshort}} en Linux](/docs/services/cloud-activity-tracker/how-to/config_cli.html#install_cli_linux).
    * Para Windows, consulte [Instalación del plugin de {{site.data.keyword.cloudaccesstrailshort}} en Windows](/docs/services/cloud-activity-tracker/how-to/config_cli.html#install_cli_windows).
    * Para Mac OS X, consulte [Instalación del plugin de {{site.data.keyword.cloudaccesstrailshort}} en Mac OS X](/docs/services//cloud-activity-tracker/how-to/config_cli.html#install_cli_mac).
 
3. Verifique la instalación del plugin de la CLI.
  
    Por ejemplo, compruebe la versión del plugin. Ejecute el mandato siguiente:
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    
    El resultado se parecerá al siguiente:
   
    ```
    ibmcloud plugin list
    Listing installed plug-ins...

    Plugin Name               Version   
    activity-tracker          3.3.0   
    ```
    {: screen}
 


## Instalación del plugin de Log Analysis en Linux desde un archivo
{: #install_cli_linux}

Siga estos pasos para instalar el plugin de recopilación de registros en Linux:

1. Instale el plugin.

    Descargue el último release del plugin de la CLI del servicio {{site.data.keyword.cloudaccesstrailshort}} (activity-tracker) desde [la página de la CLI de {{site.data.keyword.Bluemix_notm}}](https://clis.ng.bluemix.net/ui/repository.html#bluemix-plugins). 
	
	* Seleccione el valor de la plataforma: **linux64**. 
	
	* Pulse **Guardar archivo**. 
    
2. Instale el plugin. Ejecute el mandato siguiente:
        
    ```
    ibmcloud plugin install -f activity-tracker-linux-amd64-3.3.0
    ```
    {: codeblock}




## Instalación del plugin de Log Analysis en Windows desde un archivo
{: #install_cli_windows}

Siga estos pasos para instalar el plugin de recopilación de registros en Windows:

1. Descargue el último release del plugin de la CLI del servicio {{site.data.keyword.cloudaccesstrailshort}} (activity-tracker) desde [la página de la CLI de {{site.data.keyword.Bluemix_notm}}](https://clis.ng.bluemix.net/ui/repository.html#bluemix-plugins). 
	
	1. Seleccione el valor de la plataforma: **win64**. 
	2. Pulse **Guardar archivo**.  
    
2. Instale el plugin. Ejecute el mandato siguiente:
        
    ```
    ibmcloud plugin install -f activity-tracker-windows-amd64-3.3.0.exe
    ```
    {: codeblock}

	

## Instalación del plugin de Log Analysis en Mac OS X desde un archivo
{: #install_cli_mac}

Siga estos pasos para instalar el plugin de recopilación de registros en Mac OS X:

1. Descargue el último release del plugin de la CLI del servicio {{site.data.keyword.cloudaccesstrailshort}} (activity-tracker) desde [la página de la CLI de {{site.data.keyword.Bluemix_notm}}](https://clis.ng.bluemix.net/ui/repository.html#bluemix-plugins). 
	
	1. Seleccione el valor de plataforma: **osx**. 
	2. Pulse **Guardar archivo**.  
    
2. Instale el plugin. Ejecute el mandato siguiente:
        
    ```
    ibmcloud plugin install -f activity-tracker-darwin-amd64-3.3.0
    ```
    {: codeblock}

	
	
## Desinstalación de la CLI de Log Analysis
{: #uninstall_cli}

Para desinstalar la CLI, suprima el plugin.
{:shortdesc}

Siga estos pasos para desinstalar la CLI del servicio {{site.data.keyword.cloudaccesstrailshort}}:

1. Verifique la versión del plugin de la CLI que está instalada.
  
    Por ejemplo, compruebe la versión del plugin. Ejecute el mandato siguiente:
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    
    El resultado se parecerá al siguiente:
   
    ```
    ibmcloud plugin list
    Listing installed plug-ins...

    Plugin Name          Version   
    activity-tracker      3.3.0   
    ```
    {: screen}
    
2. Si el plugin está instalado, ejecute `ibmcloud plugin uninstall` para desinstalar el plugin de la CLI.

    Ejecute el mandato siguiente:
        
    ```
    ibmcloud plugin uninstall activity-tracker
    ```
    {: codeblock}
  

## Actualización de la CLI de Log Analysis desde el repositorio
{: #update_cli}

Para actualizar la CLI, ejecute el mandato *ibmcloud plugin update*.
{:shortdesc}

Complete los pasos siguientes para actualizar la CLI de servicio de {{site.data.keyword.cloudaccesstrailshort}}:

1. Actualice el plugin de {{site.data.keyword.cloudaccesstrailshort}}. Ejecute el mandato siguiente:

    ```
    ibmcloud plugin update activity-tracker -r Bluemix
    ```
    {: codeblock}
 
2. Verifique la instalación del plugin de la CLI.
  
    Por ejemplo, verifique la versión del plugin. Ejecute el mandato siguiente:
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    
    El resultado se parecerá al siguiente:
   
    ```
    ibmcloud plugin list
    Listing installed plug-ins...

    Plugin Name             Version   
    activity-tracker         3.3.0   
    ```
    {: screen}





## Obtención de ayuda general
{: #general_cli_help}

Para obtener información general sobre la CLI y los mandatos soportados, siga los pasos siguientes:

1. Inicie la sesión en una región, organización y espacio en {{site.data.keyword.Bluemix_notm}}. 
    
2. Obtenga una lista de la información sobre los mandatos soportados y la CLI. Ejecute el mandato siguiente:

    ```
    ibmcloud at help 
    ```
    {: codeblock}
    
    

## Obtención de ayuda sobre un mandato
{: #command_cli_help}

Para obtener ayuda sobre cómo utilizar un mandato, siga los pasos siguientes:

1. Inicie la sesión en una región, organización y espacio en {{site.data.keyword.Bluemix_notm}}. 
    
2. Obtenga la lista de mandatos soportados e identifique el que necesita. Ejecute el mandato:

    ```
    ibmcloud at help 
    ```
    {: codeblock}

3. Obtenga ayuda sobre el mandato. Ejecute el mandato siguiente:

    ```
    ibmcloud at help *Command*
    ```
    {: codeblock}
    
    donde *Mandato* es el nombre de un mandato de CLI, por ejemplo *status*.



## Obtención de ayuda sobre un submandato
{: #subcommand_cli_help}

Un mandato puede tener submandatos. Para obtener ayuda sobre los submandatos, siga los pasos siguientes:

1. Inicie la sesión en una región, organización y espacio en {{site.data.keyword.Bluemix_notm}}. 
    
2. Obtenga la lista de mandatos soportados e identifique el que necesita. Ejecute el mandato:

    ```
    ibmcloud at help 
    ```
    {: codeblock}

3. Obtenga ayuda sobre el mandato e identifique los submandatos soportados. Ejecute el mandato siguiente:

    ```
    ibmcloud at help *Command*
    ```
    {: codeblock}
    
    donde *Mandato* es el nombre de un mandato de CLI, por ejemplo *session*.

4. Obtenga ayuda sobre el mandato e identifique los submandatos soportados. Ejecute el mandato siguiente:

    ```
    ibmcloud at *Command* help *Subcommand*
    ```
    {: codeblock}
    
    donde 
    
    * *Mandato* es el nombre de un mandato de CLI, por ejemplo *status*.
    * *Submandato* es el nombre de un submandato soportado, por ejemplo, para el mandato *session*, un submandato válido es *list*.


## Mostrar los detalles del plugin
{: #show}
  
Utilice el mandato 'ibmcloud plugin show activity-tracker' para mostrar los detalles del plugin. 

```
ibmcloud plugin show activity-tracker
```
{: codeblock}
    
El resultado se parecerá al siguiente:
   
```
ibmcloud plugin show activity-tracker
                                  
Plugin                         activity-tracker
Version                        3.3.0
SDK Version
Minimal CLI version required   N/A      
```
{: screen}



