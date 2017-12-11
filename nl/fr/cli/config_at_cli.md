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

# Configuration de l'interface CLI d'Activity Tracker
{: #config_at_cli}

Le service {{site.data.keyword.cloudaccesstraillong}} inclut une interface de ligne de commande (CLI) qui vous permet de gérer vos événements dans le cloud. L'interface CLI est un plug-in Cloud Foundry (CF). Vous pouvez utiliser des commandes pour afficher le statut des événements, pour télécharger, restaurer et supprimer des événements, et pour configurer des règles de conservation des événements.
{:shortdesc}


## Installation de l'interface CLI d'Activity Tracker
{: #install_cli}

Pour installer l'interface CLI d'{{site.data.keyword.cloudaccesstrailshort}}, procédez comme suit :

1. Installez l'interface CLI {{site.data.keyword.Bluemix_notm}}.

    Pour plus d'informations, voir [Installation à partir du shell](/docs/cli/reference/bluemix_cli/download_cli.html#shell_install).
	
	Par exemple, pour installer l'interface CLI {{site.data.keyword.Bluemix_notm}} sous Linux, exécutez la commande suivante :
	
	```
	curl -fsSL https://clis.ng.bluemix.net/install/linux | sh
	```
	{: codeblock}

2. Installez le plug-in CF d'{{site.data.keyword.cloudaccesstrailshort}}.

    * Pour Linux, voir [Installation de l'interface CLI {{site.data.keyword.cloudaccesstrailshort}} sous Linux](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#install_cli_linux).
    * Pour Windows, voir [Installation de l'interface CLI {{site.data.keyword.cloudaccesstrailshort}} sous Windows](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#install_cli_windows).
    * Pour Mac OS X, voir [Installation de l'interface CLI {{site.data.keyword.cloudaccesstrailshort}} sous Mac OS X ](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#install_cli_mac).
 
3. Vérifiez l'installation du plug-in de l'interface CLI.
  
    Par exemple, vérifiez la version du plug-in. Exécutez la commande suivante :
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    La sortie prend la forme suivante :
   
    ```
    Invoking 'cf plugins'...

    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}

	
## Installation de l'interface CLI d'Activity Tracker sous Linux
{: #install_cli_linux}

Pour installer le plug-in CF d'{{site.data.keyword.cloudaccesstrailshort}} sous Linux, procédez comme suit :

1. Installez le plug-in de l'interface de ligne de commande d'{{site.data.keyword.cloudaccesstrailshort}}.

    1. Téléchargez la version la plus récente du plug-in d'interface CLI du service {{site.data.keyword.cloudaccesstrailshort}} depuis la [page Interface de ligne de commande Bluemix](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins). 
	
		Sélectionnez la valeur de plateforme : **linux64**. 
		Cliquez sur **Save file**. 
    
    2. Décompressez le plug-in.
    
        Par exemple, pour décompresser le plug-in `activitytracker-cli-linux_x64_v3.0.2.gz` sous Ubuntu, exécutez la commande suivante :
        
        ```
        gunzip activitytracker-cli-linux_x64_v3.0.2.gz
        ```
        {: codeblock}

    3. Rendez le fichier exécutable.
    
        Par exemple, pour que le fichier `activitytracker-cli-linux_x64_v3.0.2` devienne exécutable, exécutez la commande suivante :
        
        ```
        chmod a+x activitytracker-cli-linux_x64_v3.0.2
        ```
        {: codeblock}

    4. Installation du plug-in CF de journalisation.
    
        Par exemple, pour que le fichier `activitytracker-cli-linux_x64_v3.0.2` devienne exécutable, exécutez la commande suivante :
        
        ```
        bx cf install-plugin -f activitytracker-cli-linux_x64_v3.0.2
        ```
        {: codeblock}

2. Vérifiez l'installation du plug-in de l'interface CLI.
  
    Par exemple, vérifiez la version du plug-in. Exécutez la commande suivante :
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    La sortie prend la forme suivante :
   
    ```
    Invoking 'cf plugins'...

    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}


## Installation de l'interface CLI d'Activity Tracker sous Windows
{: #install_cli_windows}

Pour installer le plug-in CF d'{{site.data.keyword.cloudaccesstrailshort}} sous Windows, procédez comme suit :

1. Téléchargez la version la plus récente du plug-in d'interface CLI du service {{site.data.keyword.cloudaccesstrailshort}} depuis la [page Interface de ligne de commande Bluemix](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins). 
	
	1. Sélectionnez la valeur de plateforme : **win64**. 
	2. Cliquez sur **Save file**.  
    
2. Exécutez la commande **cf install-plugins** pour installer le plug-in {{site.data.keyword.cloudaccesstrailshort}} sous Windows. 

    ```
	bx cf install-plugin PluginName
	```
	{: codeblock}
	
	où *PluginName* est le nom du fichier que vous avez téléchargé.
	
    Par exemple, pour installer le plug-in sous Windows, exécutez la commande suivante à partir d'une fenêtre de terminal :
	
	```
	bx cf install-plugin activitytracker-cli-windows_x64_v3.0.2.exe
	```
	{: codeblock}
	
    Une fois le plug-in installé, vous obtenez le message suivant : `Plugin IBM-ActivityTracker successfully installed.`

3. Vérifiez l'installation du plug-in de l'interface de ligne de commande.

    Par exemple, vérifiez la version du plug-in. Exécutez la commande suivante :
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    La sortie prend la forme suivante :
   
    ```
    Invoking 'cf plugins'...

        Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}



## Installation du plug-in de l'interface de ligne de commande d'Activity Tracker sous Mac OS X
{: #install_cli_mac}

Pour installer le plug-in CF d'{{site.data.keyword.cloudaccesstrailshort}} sous Mac OS X, procédez comme suit :

1. Téléchargez la version la plus récente du plug-in d'interface de ligne de commande du service {{site.data.keyword.cloudaccesstrailshort}} à partir de la [page d'interface de ligne de commande Bluemix](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins). 	
	1. Sélectionnez la valeur de plateforme : **osx**. 
	2. Cliquez sur **Save file**.  
    
2. Exécutez la commande **cf install-plugin** pour installer le plug-in {{site.data.keyword.cloudaccesstrailshort}} sous Mac OS X.

    ```
	bx cf install-plugin PluginName
	```
	{: codeblock}
	
	où *PluginName* est le nom du fichier que vous avez téléchargé.
	
    Par exemple, pour installer le plug-in sous Mac OS X, exécutez la commande suivante à partir d'un terminal :
	
	```
	bx cf install-plugin activitytracker-cli-mac_x64_v3.0.2
	```
	{: codeblock}
	
    Une fois le plug-in installé, vous obtenez le message suivant : `Plugin IBM-ActivityTracker successfully installed.`

3. Vérifiez l'installation du plug-in de l'interface de ligne de commande.

    Par exemple, vérifiez la version du plug-in. Exécutez la commande suivante :
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    La sortie prend la forme suivante :
   
    ```
    Invoking 'cf plugins'...

        Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}

	

## Mise à jour de l'interface de ligne de commande d'Activity Tracker
{: #update_cli}

Pour mettre à jour le plug-in CF d'{{site.data.keyword.cloudaccesstrailshort}}, procédez comme suit :

1. Téléchargez la version la plus récente du plug-in d'interface de ligne de commande du service {{site.data.keyword.cloudaccesstrailshort}} à partir de la [page d'interface de ligne de commande Bluemix](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins). 	
	1. Sélectionnez la valeur de plateforme : **win64** pour Windows, **osx** pour Mac OS X ou **linux64** pour Linux.
	2. Cliquez sur **Save file**.  
    
2. Exécutez la commande **cf install-plugin** pour mettre à jour le plug-in d'{{site.data.keyword.cloudaccesstrailshort}} sous Windows.

    ```
	bx cf install-plugin PluginName -f
	```
	{: codeblock}
	
	où
	
	* *PluginName* est le nom du fichier que vous avez téléchargé.
	* *-f* est l'option qui demande la désinstallation de l'ancienne version du plug-in et l'installation du nouveau.
	
    Par exemple, pour mettre à jour le plug-in sous Windows, exécutez la commande suivante à partir d'une fenêtre de terminal :
	
	```
	bx cf install-plugin activitytracker-cli-windows_x64_v3.0.2.exe
	```
	{: codeblock}
	
    Une fois le plug-in installé, vous obtenez le message suivant : `Plugin IBM-ActivityTracker successfully installed.`

3. Vérifiez l'installation du plug-in de l'interface de ligne de commande.

    Par exemple, vérifiez la version du plug-in. Exécutez la commande suivante :
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    La sortie prend la forme suivante :
   
    ```
    Invoking 'cf plugins'...

        Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}

	
	
## Désinstallation de l'interface de ligne de commande d'Activity Tracker
{: #uninstall_cli}

Pour désinstaller l'interface de ligne de commande du {{site.data.keyword.cloudaccesstrailshort}}, supprimez le plug-in.
{:shortdesc}

Pour désinstaller l'interface de ligne de commande du service {{site.data.keyword.cloudaccesstrailshort}}, procédez comme suit :

1. Vérifiez la version du plug-in de l'interface de ligne de commande du {{site.data.keyword.cloudaccesstrailshort}} qui est installé.

    Par exemple, vérifiez la version du plug-in. Exécutez la commande suivante :
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    La sortie prend la forme suivante :
   
    ```
    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2           at       IBM Activity Tracker plug-in
    ```
    {: screen}
    
2. Si le plug-in est installé, exécutez la commande `cf uninstall-plugin` pour désinstaller le plug-in de l'interface de ligne de commande de journalisaiton (logging).

    Exécutez la commande suivante :
        
    ```
    bx cf uninstall-plugin IBM-ActivityTracker
    ```
    {: codeblock}
  
