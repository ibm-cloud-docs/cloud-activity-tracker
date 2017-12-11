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

# Activity Tracker-CLI konfigurieren
{: #config_at_cli}

Der {{site.data.keyword.cloudaccesstraillong}}-Service enthält eine Befehlszeilenschnittstelle (Command Line Interface, CLI), mit der Sie Ihre Ereignisse in der Cloud verwalten können. Diese CLI ist ein Cloud Foundry-Plug-in (CF-Plug-in). Mit den Befehlen der CLI können Sie den Status der Ereignisse anzeigen, Ereignisse herunterladen, Ereignisse wiederherstellen, Ereignisse löschen und die Richtlinie für Ereignisaufbewahrung konfigurieren.
{:shortdesc}


## Activity Tracker-CLI installieren
{: #install_cli}

Führen Sie die folgenden Schritte aus, um die {{site.data.keyword.cloudaccesstrailshort}}-CLI zu installieren:

1. Installieren Sie die {{site.data.keyword.Bluemix_notm}}-CLI.

    Weitere Informationen finden Sie in [Über die Shell installieren](/docs/cli/reference/bluemix_cli/download_cli.html#shell_install).
	
	Führen Sie zum Beispiel den folgenden Befehl aus, um die {{site.data.keyword.Bluemix_notm}}-CLI unter Linux zu installieren:
	
	```
	curl -fsSL https://clis.ng.bluemix.net/install/linux | sh
	```
	{: codeblock}

2. Installieren Sie das CF-Plug-in für {{site.data.keyword.cloudaccesstrailshort}}.

    * Informationen für die Installation unter Linux finden Sie in [{{site.data.keyword.cloudaccesstrailshort}}-CLI unter Linux installieren](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#install_cli_linux).
    * Informationen für die Installation unter Windows finden Sie in [{{site.data.keyword.cloudaccesstrailshort}}-CLI unter Windows installieren](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#install_cli_windows).
    * Informationen für die Installation unter Mac OS X finden Sie in [{{site.data.keyword.cloudaccesstrailshort}}-CLI unter Mac OS X installieren](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#install_cli_mac).
 
3. Überprüfen Sie die Installation des CLI-Plug-ins.
  
    Überprüfen Sie beispielsweise die Version des Plug-ins. Führen Sie dazu den folgenden Befehl aus:
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    Die Ausgabe sieht wie folgt aus:
   
    ```
    Invoking 'cf plugins'...

    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}

	
## Activity Tracker-CLI unter Linux installieren
{: #install_cli_linux}

Führen Sie die folgenden Schritte aus, um das CF-Plug-in für {{site.data.keyword.cloudaccesstrailshort}} unter Linux zu installieren:

1. Installieren Sie das CLI-Plug-in für {{site.data.keyword.cloudaccesstrailshort}}.

    1. Laden Sie die aktuelle Version des CLI-Plug-ins für den {{site.data.keyword.cloudaccesstrailshort}}-Service
von der [Bluemix-CLI-Seite](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins) herunter. 
	
		Wählen Sie den folgenden Wert für die Plattform aus: **linux64**.
		Klicken Sie auf **Datei speichern**. 
    
    2. Dekomprimieren Sie das Plug-in.
    
        Führen Sie zum Beispiel den folgenden Befehl aus, um die Plug-in-Datei `activitytracker-cli-linux_x64_v3.0.2.gz` in Ubuntu zu dekomprimieren:
        
        ```
        gunzip activitytracker-cli-linux_x64_v3.0.2.gz
        ```
        {: codeblock}

    3. Machen Sie die Datei ausführbar.
    
        Führen Sie zum Beispiel den folgenden Befehl aus, um die Datei `activitytracker-cli-linux_x64_v3.0.2` ausführbar zu machen:
        
        ```
        chmod a+x activitytracker-cli-linux_x64_v3.0.2
        ```
        {: codeblock}

    4. Installieren Sie das CF-Plug-in für die Protokollierung.
    
        Führen Sie zum Beispiel den folgenden Befehl aus, um die Datei `activitytracker-cli-linux_x64_v3.0.2` ausführbar zu machen:
        
        ```
        bx cf install-plugin -f activitytracker-cli-linux_x64_v3.0.2
        ```
        {: codeblock}

2. Überprüfen Sie die Installation des CLI-Plug-ins.
  
    Überprüfen Sie beispielsweise die Version des Plug-ins. Führen Sie dazu den folgenden Befehl aus:
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    Die Ausgabe sieht wie folgt aus:
   
    ```
    Invoking 'cf plugins'...

    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}


## Activity Tracker-CLI unter Windows installieren
{: #install_cli_windows}

Führen Sie die folgenden Schritte au, um das CF-Plug-in für {{site.data.keyword.cloudaccesstrailshort}} unter Windows zu installieren:

1. Laden Sie die aktuelle Version des CLI-Plug-ins für den {{site.data.keyword.cloudaccesstrailshort}}-Service
von der [Bluemix-CLI-Seite](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins) herunter. 
	
	1. Wählen Sie den folgenden Wert für die Plattform aus: **win64**. 
	2. Klicken Sie auf **Datei speichern**.  
    
2. Führen Sie den Befehl **cf install-plugins** aus, um das {{site.data.keyword.cloudaccesstrailshort}}-Plug-in unter Windows zu installieren. 

    ```
	bx cf install-plugin PluginName
	```
	{: codeblock}
	
	Dabei ist *PluginName* der Name der Datei, die Sie heruntergeladen haben.
	
    Führen Sie zum Beispiel den folgenden Befehl in einem Terminalfenster aus, um das Plug-in unter Windows zu installieren:
	
	```
	bx cf install-plugin activitytracker-cli-windows_x64_v3.0.2.exe
	```
	{: codeblock}
	
    Nach dem Installieren des Plug-ins wird die folgende Nachricht ausgegeben: `Plugin IBM-ActivityTracker successfully installed.`

3. Überprüfen Sie die Installation des CLI-Plug-ins.

    Überprüfen Sie beispielsweise die Version des Plug-ins. Führen Sie dazu den folgenden Befehl aus:

    ```
    bx cf plugins
    ```
    {: codeblock}

    Die Ausgabe sieht wie folgt aus:

    ```
    Invoking 'cf plugins'...

    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}



## Activity Tracker-CLI unter Mac OS X installieren
{: #install_cli_mac}

Führen Sie die folgenden Schritte aus, um das CF-Plug-in für {{site.data.keyword.cloudaccesstrailshort}} unter Mac OS X auszuführen:

1. Laden Sie das neueste Release des CLI-Plug-ins für den {{site.data.keyword.cloudaccesstrailshort}}-Service von der [Bluemix-CLI-Seite] (https://clis.ng.bluemix.net/ui/repository.html#cf-plugins) herunter.
	
	1. Wählen Sie den folgenden Wert für die Plattform aus: **osx**.
	2. Klicken Sie auf **Datei speichern**.

2. Führen Sie den Befehl **cf install-plugin** aus, um das {{site.data.keyword.cloudaccesstrailshort}}-Plug-in unter Mac OS X zu installieren.

    ```
	bx cf install-plugin PluginName
	```
	{: codeblock}
	
	Dabei ist *PluginName* der Name der Datei, die Sie heruntergeladen haben.
	
    Führen Sie zum Beispiel den folgenden Befehl in einem Terminal aus, um das Plug-in unter Mac OS X zu installieren:
	
	```
	bx cf install-plugin activitytracker-cli-mac_x64_v3.0.2
	```
	{: codeblock}
	
    Nach dem Installieren des Plug-ins wird die folgende Nachricht ausgegeben: `Plugin IBM-ActivityTracker successfully installed.`

3. Überprüfen Sie die Installation des CLI-Plug-ins.

    Überprüfen Sie beispielsweise die Version des Plug-ins. Führen Sie dazu den folgenden Befehl aus:

    ```
    bx cf plugins
    ```
    {: codeblock}

    Die Ausgabe sieht wie folgt aus:

    ```
    Invoking 'cf plugins'...

    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}

	

## Activity Tracker-CLI aktualisieren
{: #update_cli}

Führen Sie die folgenden Schritte aus, um das CF-Plug-in für {{site.data.keyword.cloudaccesstrailshort}} zu aktualisieren:

1. Laden Sie das neueste Release des CLI-Plug-ins für den {{site.data.keyword.cloudaccesstrailshort}}-Service von der [Bluemix-CLI-Seite] (https://clis.ng.bluemix.net/ui/repository.html#cf-plugins) herunter.
	
	1. Wählen Sie den folgenden Wert für die Plattform aus: **win64** für Windows, **osx** für Mac OS X oder **linux64** für Linux.
	2. Klicken Sie auf **Datei speichern**.

2. Führen Sie den Befehl **cf install-plugin** aus, um das {{site.data.keyword.cloudaccesstrailshort}}-Plug-in unter Windows zu aktualisieren.

    ```
	bx cf install-plugin PluginName -f
	```
	{: codeblock}
	
	Dabei gilt Folgendes:
	
	* *PluginName* ist der Name der Datei, die Sie heruntergeladen haben.
	* *-f* ist die Option, die angibt, dass die alte Version des Plug-ins deinstalliert und die neue installiert werden soll.
	
    Führen Sie zum Beispiel den folgenden Befehl in einem Terminalfenster aus, um das Plug-in unter Windows zu aktualisieren:
	
	```
	bx cf install-plugin activitytracker-cli-windows_x64_v3.0.2.exe
	```
	{: codeblock}
	
    Nach dem Installieren des Plug-ins wird die folgende Nachricht ausgegeben: `Plugin IBM-ActivityTracker successfully installed.`

3. Überprüfen Sie die Installation des CLI-Plug-ins.

    Überprüfen Sie beispielsweise die Version des Plug-ins. Führen Sie dazu den folgenden Befehl aus:

    ```
    bx cf plugins
    ```
    {: codeblock}

    Die Ausgabe sieht wie folgt aus:

    ```
    Invoking 'cf plugins'...

    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}

	
	
## Activity Tracker-CLI deinstallieren
{: #uninstall_cli}

Löschen Sie das Plug-in, um die {{site.data.keyword.cloudaccesstrailshort}}-CLI zu deinstallieren.
{:shortdesc}

Führen Sie die folgenden Schritte aus, um das CLI-Plug-in für den {{site.data.keyword.cloudaccesstrailshort}}-Service zu deinstallieren:

1. Überprüfen Sie, welche Version des CLI-Plug-ins für {{site.data.keyword.cloudaccesstrailshort}} installiert ist.

    Überprüfen Sie beispielsweise die Version des Plug-ins. Führen Sie dazu den folgenden Befehl aus:

    ```
    bx cf plugins
    ```
    {: codeblock}

    Die Ausgabe sieht wie folgt aus:

    ```
    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2           at       IBM Activity Tracker plug-in
    ```
    {: screen}

2. Wenn das Plug-in installiert ist, führen Sie den Befehl `cf uninstall-plugin` aus, um das CLI-Plug-in für die Protokollierung zu deinstallieren.

    Führen Sie den folgenden Befehl aus:

    ```
    bx cf uninstall-plugin IBM-ActivityTracker
    ```
    {: codeblock}
