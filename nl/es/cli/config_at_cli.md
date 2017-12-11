---

copyright:
  years: 2016, 2017
lastupdated: "2017-09-17"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Configuración de la CLI de Activity Tracker
{: #config_at_cli}

El servicio {{site.data.keyword.cloudaccesstraillong}} incluye una interfaz de línea de mandatos (CLI) que puede utilizar para gestionar los sucesos en la nube. La CLI es un plugin de Cloud Foundry (CF). Puede utilizar mandatos para ver el estado de los sucesos, para descargar sucesos, para restaurar sucesos, para descartar sucesos y para configurar la política de retención de sucesos. {:shortdesc}


## Instalación de la CLI de Activity Tracker
{: #install_cli}

Para instalar la CLI de {{site.data.keyword.cloudaccesstrailshort}},
siga estos pasos: 

1. Instale la CLI de {{site.data.keyword.Bluemix_notm}}. 

    Para obtener más información, consulte [Instalación desde shell](/docs/cli/reference/bluemix_cli/download_cli.html#shell_install).
	
	Por ejemplo, para instalar la CLI de {{site.data.keyword.Bluemix_notm}} en Linux, ejecute el mandato siguiente:
	
	```
	curl -fsSL https://clis.ng.bluemix.net/install/linux | sh
	```
	{: codeblock}

2. Instale el plugin de {{site.data.keyword.cloudaccesstrailshort}} CF. 

    * Para Linux, consulte [Instalación de la CLI de {{site.data.keyword.cloudaccesstrailshort}} en Linux](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#install_cli_linux).
    * Para Windows, consulte [Instalación de la CLI de {{site.data.keyword.cloudaccesstrailshort}} en Windows](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#install_cli_windows).
    * Para Mac OS X, consulte [Instalación de la CLI de {{site.data.keyword.cloudaccesstrailshort}} en Mac OS X](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#install_cli_mac).
 
3. Verifique la instalación del plugin de la CLI.
  
    Por ejemplo, compruebe la versión del plugin. Ejecute el mandato siguiente:
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    El resultado se parecerá al siguiente: 
   
    ```
    Invoking 'cf plugins'...

    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}

	
## Instalación de la CLI de Activity Tracker en Linux
{: #install_cli_linux}

Siga los pasos siguientes para instalar el plugin de {{site.data.keyword.cloudaccesstrailshort}} CF en Linux:

1. Instale el plugin de la CLI de {{site.data.keyword.cloudaccesstrailshort}}. 

    1. Descargue el último release del plugin de la CLI del servicio {{site.data.keyword.cloudaccesstrailshort}} desde [la página de la CLI de Bluemix](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins). 
	
		Seleccione el valor de la plataforma: **linux64**.
		Pulse **Guardar archivo**. 
    
    2. Descomprima el plugin.
    
        Por ejemplo, para descomprimir el plugin `activitytracker-cli-linux_x64_v3.0.2.gz` en Ubuntu, ejecute el siguiente mandato: 
        
        ```
        gunzip activitytracker-cli-linux_x64_v3.0.2.gz
        ```
        {: codeblock}

    3. Convierta el archivo en ejecutable. 
    
        Por ejemplo, para convertir el archivo `activitytracker-cli-linux_x64_v3.0.2` en ejecutable, ejecute el siguiente mandato: 
        
        ```
        chmod a+x activitytracker-cli-linux_x64_v3.0.2
        ```
        {: codeblock}

    4. Instale el plugin de CF de registro.
    
        Por ejemplo, para convertir el archivo `activitytracker-cli-linux_x64_v3.0.2` en ejecutable, ejecute el siguiente mandato: 
        
        ```
        bx cf install-plugin -f activitytracker-cli-linux_x64_v3.0.2
        ```
        {: codeblock}

2. Verifique la instalación del plugin de la CLI.
  
    Por ejemplo, compruebe la versión del plugin. Ejecute el mandato siguiente:
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    El resultado se parecerá al siguiente: 
   
    ```
    Invoking 'cf plugins'...

    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}


## Instalación de la CLI de Activity Tracker en Windows
{: #install_cli_windows}

Siga los pasos siguientes para instalar el plugin de {{site.data.keyword.cloudaccesstrailshort}} CF en Windows:

1. Descargue el último release del plugin de la CLI del servicio {{site.data.keyword.cloudaccesstrailshort}} desde [la página de la CLI de Bluemix](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins). 
	
	1. Seleccione el valor de la plataforma: **win64**.
		 
	2. Pulse **Guardar archivo**.  
    
2. Ejecute el mandato **cf install-plugins** para instalar el plugin de {{site.data.keyword.cloudaccesstrailshort}} en Windows. 

    ```
	bx cf install-plugin PluginName
	```
	{: codeblock}
	
	donde *PluginName* es el nombre del archivo que ha descargado.
	
    Por ejemplo, para instalar el plugin en Windows, ejecute el siguiente mandato desde una ventana de terminal:
	
	```
	bx cf install-plugin activitytracker-cli-windows_x64_v3.0.2.exe
	```
	{: codeblock}
	
    Cuando el plugin esté instalado, verá el siguiente mensaje: `El plugin IBM-ActivityTracker se ha instalado correctamente.`

3. Verifique la instalación del plugin de la CLI.

    Por ejemplo, compruebe la versión del plugin. Ejecute el mandato siguiente:

    ```
    bx cf plugins
    ```
    {: codeblock}
    
    El resultado se parecerá al siguiente:

```
    Invoking 'cf plugins'...

    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}



## Instalación de la CLI de Activity Tracker en Mac OS X
{: #install_cli_mac}

Siga los pasos siguientes para instalar el plugin de {{site.data.keyword.cloudaccesstrailshort}} en Mac OS X:
1. Descargue el último release del plugin de la CLI del servicio {{site.data.keyword.cloudaccesstrailshort}} desde [la página de la CLI de Bluemix](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins).
	
	1. Seleccione el valor de la plataforma: **osx**.
	2. Pulse **Guardar archivo**.

2. Ejecute el mandato **cf install-plugin** para instalar el plugin {{site.data.keyword.cloudaccesstrailshort}} en Mac OS X.
    ```
	bx cf install-plugin PluginName
	```
	{: codeblock}
	
	donde *PluginName* es el nombre del archivo que ha descargado.
	
    Por ejemplo, para instalar el plugin en Mac OS X, ejecute el siguiente mandato desde un terminal:
	
	```
	bx cf install-plugin activitytracker-cli-mac_x64_v3.0.2
	```
	{: codeblock}
	
    Cuando el plugin esté instalado, verá el siguiente mensaje: `El plugin IBM-ActivityTracker se ha instalado correctamente.`

3. Verifique la instalación del plugin de la CLI.

    Por ejemplo, compruebe la versión del plugin. Ejecute el mandato siguiente:

    ```
    bx cf plugins
    ```
    {: codeblock}

    El resultado se parecerá al siguiente:

```
    Invoking 'cf plugins'...

    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}

	

## Actualización de la CLI de Activity Tracker
{: #update_cli}

Siga los pasos siguientes para actualizar el plugin de {{site.data.keyword.cloudaccesstrailshort}} CF:

1. Descargue el último release del plugin de la CLI del servicio {{site.data.keyword.cloudaccesstrailshort}} desde [la página de la CLI de Bluemix](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins).
	
	1. Seleccione el valor de la plataforma: **win64** para Windows, **osx** para Mac OS X o **linux64** para Linux.
	2. Pulse **Guardar archivo**.

2. Ejecute el mandato **cf install-plugin** para actualizar el plugin {{site.data.keyword.cloudaccesstrailshort}} en Windows.

    ```
	bx cf install-plugin PluginName -f
	```
	{: codeblock}
	
	donde
	
	* *PluginName* es el nombre del archivo que ha descargado.
	* *-f* es la opción que indica que se debe desinstalar la versión antigua del plugin e instalar la nueva. Por ejemplo, para actualizar el plugin en Windows, ejecute el siguiente mandato desde una ventana de terminal:
	
	```
	bx cf install-plugin activitytracker-cli-windows_x64_v3.0.2.exe
	```
	{: codeblock}
	
    Cuando el plugin esté instalado, verá el siguiente mensaje: `El plugin IBM-ActivityTracker se ha instalado correctamente.`

3. Verifique la instalación del plugin de la CLI.

    Por ejemplo, compruebe la versión del plugin. Ejecute el mandato siguiente:

    ```
    bx cf plugins
    ```
    {: codeblock}

    El resultado se parecerá al siguiente:

```
    Invoking 'cf plugins'...

    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}

	
	
## Desinstalación de la CLI de Activity Tracker
{: #uninstall_cli}

Para desinstalar la CLI de {{site.data.keyword.cloudaccesstrailshort}}, suprima el plugin.
{:shortdesc}

Siga los pasos siguientes para desinstalar la CLI del servicio {{site.data.keyword.cloudaccesstrailshort}}:
1. Verifique la versión del plugin de la CLI de {{site.data.keyword.cloudaccesstrailshort}} que está instalada.

    Por ejemplo, compruebe la versión del plugin. Ejecute el mandato siguiente:

    ```
    bx cf plugins
    ```
    {: codeblock}

    El resultado se parecerá al siguiente:

```
    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2           at       IBM Activity Tracker plug-in
    ```
    {: screen}

2. Si el plugin está instalado, ejecute `cf uninstall-plugin` para desinstalar el plugin de la CLI de registro.

    Ejecute el mandato siguiente:

    ```
    bx cf uninstall-plugin IBM-ActivityTracker
    ```
    {: codeblock}
