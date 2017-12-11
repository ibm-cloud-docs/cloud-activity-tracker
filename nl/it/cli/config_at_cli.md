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

# Configurazione della CLI del programma di traccia dell'attività 
{: #config_at_cli}

Il servizio {{site.data.keyword.cloudaccesstraillong}} include una CLI (command line interface) che puoi utilizzare per gestire i tuo eventi nel cloud. La CLI è un plugin Cloud Foundry (CF). Puoi utilizzare i comandi per visualizzare lo stato degli eventi, per scaricarli, ripristinarli, scartarli o per configurare la politica di conservazione degli eventi.
{:shortdesc}


## Installazione della CLI del programma di traccia dell'attività 
{: #install_cli}

Per installare la CLI di {{site.data.keyword.cloudaccesstrailshort}}, completa la seguente procedura: 

1. Installa la CLI {{site.data.keyword.Bluemix_notm}}. 

    Per ulteriori informazioni, vedi [Installa dalla shell](/docs/cli/reference/bluemix_cli/download_cli.html#shell_install).
	
	Ad esempio, per installare la CLI {{site.data.keyword.Bluemix_notm}} su Linux, immetti il seguente comando:
	
	```
	curl -fsSL https://clis.ng.bluemix.net/install/linux | sh
	```
	{: codeblock}

2. Installa il plugin CF {{site.data.keyword.cloudaccesstrailshort}}.

    * Per Linux, consulta [Installazione della CLI {{site.data.keyword.cloudaccesstrailshort}} su Linux](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#install_cli_linux).
    * Per Windows, consulta [Installazione della CLI {{site.data.keyword.cloudaccesstrailshort}} su Windows](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#install_cli_windows).
    * Per Mac OS X, consulta [Installazione della CLI {{site.data.keyword.cloudaccesstrailshort}} su Mac OS X ](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#install_cli_mac).
 
3. Verifica l'installazione del plugin CLI.
  
    Ad esempio, controlla la versione del plugin. Immetti il seguente comando:
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    L'output è simile al seguente:
   
    ```
    Invoking 'cf plugins'...

    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}

	
## Installazione della CLI del programma di traccia dell'attività su Linux
{: #install_cli_linux}

Completa le seguenti istruzioni per installare il plugin CLI {{site.data.keyword.cloudaccesstrailshort}} su Linux:

1. Installa il plugin CLI {{site.data.keyword.cloudaccesstrailshort}}. 

    1. Scarica l'ultima release del plugin CLI del servizio {{site.data.keyword.cloudaccesstrailshort}} dalla [pagina Bluemix CLI](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins). 
	
		Seleziona il valore della piattaforma: **linux64**.
		Fai clic su **Salva file**. 
    
    2. Decomprimi il plugin.
    
        Ad esempio, per decomprimere il plugin `activitytracker-cli-linux_x64_v3.0.2.gz` in Ubuntu, immetti il seguente comando:
        
        ```
        gunzip activitytracker-cli-linux_x64_v3.0.2.gz
        ```
        {: codeblock}

    3. Rendi il file eseguibile.
    
        Ad esempio, per rendere il file `activitytracker-cli-linux_x64_v3.0.2` eseguibile, immetti il seguente comando:
        
        ```
        chmod a+x activitytracker-cli-linux_x64_v3.0.2
        ```
        {: codeblock}

    4. Installa il plugin CLI di registrazione.
    
        Ad esempio, per rendere il file `activitytracker-cli-linux_x64_v3.0.2` eseguibile, immetti il seguente comando:
        
        ```
        bx cf install-plugin -f activitytracker-cli-linux_x64_v3.0.2
        ```
        {: codeblock}

2. Verifica l'installazione del plugin CLI.
  
    Ad esempio, controlla la versione del plugin. Immetti il seguente comando:
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    L'output è simile al seguente:
   
    ```
    Invoking 'cf plugins'...

    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}


## Installazione della CLI del programma di traccia dell'attività su Windows
{: #install_cli_windows}

Completa le seguenti istruzioni per installare il plugin CLI {{site.data.keyword.cloudaccesstrailshort}} su Windows:

1. Scarica l'ultima release del plugin CLI del servizio {{site.data.keyword.cloudaccesstrailshort}} dalla [pagina Bluemix CLI](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins). 
	
	1. Seleziona il valore della piattaforma: **win64**. 		 
	2. Fai clic su **Salva file**.  
    
2. Esegui il comando **cf install-plugins** per installare il plugin {{site.data.keyword.cloudaccesstrailshort}} su Windows. 

    ```
	bx cf install-plugin PluginName
	```
	{: codeblock}
	
	dove *PluginName* è il nome del file che hai scaricato.
	
    Ad esempio, per installare il plugin su Windows, immetti il seguente comando da una finestra del terminale:
	
	```
	bx cf install-plugin activitytracker-cli-windows_x64_v3.0.2.exe
	```
	{: codeblock}
	
    Quando il plugin è stato installato, ricevi il seguente messaggio: `Plugin IBM-ActivityTracker successfully installed.`

3. Verifica l'installazione del plugin CLI.

    Ad esempio, controlla la versione del plugin. Esegui il seguente comando:
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    L'output è simile al seguente:

    ```
    Invoking 'cf plugins'...

    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}



## Installazione della CLI del programma di traccia dell'attività su Mac OS X
{: #install_cli_mac}

Completa le seguenti istruzioni per installare il plugin CF {{site.data.keyword.cloudaccesstrailshort}} su Mac OS X:

1. Scarica l'ultima release del plugin CLI del servizio {{site.data.keyword.cloudaccesstrailshort}} dalla [pagina Bluemix CLI](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins).
	
	1. Seleziona il valore della piattaforma: **osx**.
	2. Fai clic su **Salva file**.

2. Esegui il comando **cf install-plugin** per installare il plugin {{site.data.keyword.cloudaccesstrailshort}} su Mac OS X.

    ```
	bx cf install-plugin PluginName
	```
	{: codeblock}
	
	dove *PluginName* è il nome del file che hai scaricato.
	
    Ad esempio, per installare il plugin su Mac OS X, immetti il seguente comando da una finestra del terminale:
	
	```
	bx cf install-plugin activitytracker-cli-mac_x64_v3.0.2
	```
	{: codeblock}
	
    Quando il plugin è stato installato, ricevi il seguente messaggio: `Plugin IBM-ActivityTracker successfully installed.`

3. Verifica l'installazione del plugin CLI.

    Ad esempio, controlla la versione del plugin. Esegui il seguente comando:
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    L'output è simile al seguente:

    ```
    Invoking 'cf plugins'...

    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}

	

## Aggiornamento della CLI del programma di traccia dell'attività
{: #update_cli}

Completa le seguenti istruzioni per aggiornare il plugin CF {{site.data.keyword.cloudaccesstrailshort}}:

1. Scarica l'ultima release del plugin CLI del servizio {{site.data.keyword.cloudaccesstrailshort}} dalla [pagina Bluemix CLI](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins).
	
	1. Seleziona il valore della piattaforma: **win64** per Windows, **osx** per Mac OS X o **linux64** per Linux.
	2. Fai clic su **Salva file**.

2. Esegui il comando **cf install-plugin** per aggiornare il plugin {{site.data.keyword.cloudaccesstrailshort}} su Windows.

    ```
	bx cf install-plugin PluginName -f
	```
	{: codeblock}
	
	dove
	
	* *PluginName* è il nome del file che hai scaricato.
	* *-f* è l'opzione che indica di disinstallare la versione precedente del plugin e installare la nuova versione.
	
    Ad esempio, per aggiornare il plugin su Windows, immetti il seguente comando da una finestra del terminale:
	
	```
	bx cf install-plugin activitytracker-cli-windows_x64_v3.0.2.exe
	```
	{: codeblock}
	
    Quando il plugin è stato installato, ricevi il seguente messaggio: `Plugin IBM-ActivityTracker successfully installed.`

3. Verifica l'installazione del plugin CLI.

    Ad esempio, controlla la versione del plugin. Esegui il seguente comando:
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    L'output è simile al seguente:

    ```
    Invoking 'cf plugins'...

    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}

	
	
## Disinstallazione della CLI del programma di traccia dell'attività
{: #uninstall_cli}

Per disinstallare la CLI {{site.data.keyword.cloudaccesstrailshort}}, elimina il plugin.
{:shortdesc}

Completa le seguenti istruzioni per eliminare la CLI del servizio {{site.data.keyword.cloudaccesstrailshort}}:

1. Verifica la versione del plugin CLI {{site.data.keyword.cloudaccesstrailshort}} installato.

    Ad esempio, controlla la versione del plugin. Esegui il seguente comando:
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    L'output è simile al seguente:

    ```
    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2           at       IBM Activity Tracker plug-in
    ```
    {: screen}
    
2. Se il plugin è installato, esegui `cf uninstall-plugin` per disinstallare il plugin CLI di registrazione.

    Esegui il seguente comando:
        
    ```
    bx cf uninstall-plugin IBM-ActivityTracker
    ```
    {: codeblock}
  
