---

copyright:
  years: 2016, 2019
lastupdated: "2019-02-18"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# Configuration de l'interface de ligne de commande d'Activity Tracker
{: #config_cli}

Le service {{site.data.keyword.cloudaccesstraillong}} inclut une interface de ligne de commande (CLI) qui vous permet de gérer vos événements dans le cloud. Vous pouvez utiliser le plug-in {{site.data.keyword.cloud_notm}} pour afficher le statut des événements, télécharger des événements et configurer la règle de conservation des événements. L'interface de ligne de commande offre différents types d'aides : une aide générale concernant l'interface de ligne de commande et les commandes prises en charge,
une aide relative aux commandes pour savoir comment utiliser une commande et une aide relative aux sous-commandes pour savoir comment utiliser une sous-commande d'une commande.
{:shortdesc}


## Installation du plug-in {{site.data.keyword.cloudaccesstrailshort}} depuis le référentiel {{site.data.keyword.cloud_notm}}
{: #install_cli_repo}

Pour installer l'interface CLI d'{{site.data.keyword.cloudaccesstrailshort}}, procédez comme suit :

1. Installez l'interface CLI {{site.data.keyword.cloud_notm}}.

   Pour plus d'informations, voir [Installation de l'interface de ligne de commande {{site.data.keyword.cloud_notm}}.](/docs/cli?topic=cloud-cli-ibmcloud-cli#ibmcloud-cli)
   
2. Recherchez le nom du plug-in dans le référentiel. Exécutez la commande suivante :

    ```
    ibmcloud plugin repo-plugins
    ```
    {: codeblock}
    
    Le nom du plug-in est **activity-tracker**.

3. Installez le plug-in {{site.data.keyword.cloudaccesstrailshort}}. Exécutez la commande suivante :

    ```
    ibmcloud plugin install activity-tracker -r Bluemix
    ```
    {: codeblock}
 
4. Vérifiez que le plug-in {{site.data.keyword.cloudaccesstrailshort}} est installé.
  
    Par exemple, exécutez la commande suivante pour afficher la liste des plug-in qui sont installés :
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    


## Installation du plug-in {{site.data.keyword.cloudaccesstrailshort}} depuis un fichier
{: #install_cli}

Pour installer l'interface CLI d'{{site.data.keyword.cloudaccesstrailshort}}, procédez comme suit :

1. Installez l'interface CLI {{site.data.keyword.cloud_notm}}.

   Pour plus d'informations, voir [Installation de l'interface de ligne de commande {{site.data.keyword.cloud_notm}}.](/docs/cli?topic=cloud-cli-ibmcloud-cli#ibmcloud-cli)

2. Installez le plug-in {{site.data.keyword.cloudaccesstrailshort}}.

    * Pour Linux, voir [Installation du plug-in {{site.data.keyword.cloudaccesstrailshort}} sous Linux](/docs/services/cloud-activity-tracker/how-to/config_cli.html#install_cli_linux).
    * Pour Windows, voir [Installation du plug-in {{site.data.keyword.cloudaccesstrailshort}} sous Windows](/docs/services/cloud-activity-tracker/how-to/config_cli.html#install_cli_windows).
    * Pour Mac OS X, voir [Installation du plug-in {{site.data.keyword.cloudaccesstrailshort}} sous Mac OS X](/docs/services//cloud-activity-tracker/how-to/config_cli.html#install_cli_mac).
 
3. Vérifiez l'installation du plug-in de l'interface CLI.
  
    Par exemple, vérifiez la version du plug-in. Exécutez la commande suivante :
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    


## Installation du plug-in {{site.data.keyword.cloudaccesstrailshort}} sous Linux depuis un fichier
{: #install_cli_linux}

Procédez comme suit pour installer le plug-in sous Linux :

1. Installez le plug-in.

    Téléchargez l'édition la plus récente du plug-in d'interface de ligne de commande du service {{site.data.keyword.cloudaccesstrailshort}} (activity-tracker) depuis la [page de l'interface de ligne de commande {{site.data.keyword.cloud_notm}}](https://clis.ng.bluemix.net/ui/repository.html#bluemix-plugins). 
	
	* Sélectionnez la valeur de plateforme : **linux64**. 
	
	* Cliquez sur **Enregistrer le fichier**. 
    
2. Installez le plug-in. Exécutez la commande suivante :
        
    ```
    ibmcloud plugin install -f activity-tracker-linux-amd64-3.3.0
    ```
    {: codeblock}




## Installation du plug-in {{site.data.keyword.cloudaccesstrailshort}} sous Windows depuis un fichier
{: #install_cli_windows}

Procédez comme suit pour installer le plug-in sous Windows :

1. Téléchargez l'édition la plus récente du plug-in d'interface de ligne de commande du service {{site.data.keyword.cloudaccesstrailshort}} (activity-tracker) depuis la [page de l'interface de ligne de commande {{site.data.keyword.cloud_notm}}](https://clis.ng.bluemix.net/ui/repository.html#bluemix-plugins). 
	
	1. Sélectionnez la valeur de plateforme : **win64**. 
	2. Cliquez sur **Enregistrer le fichier**.  
    
2. Installez le plug-in. Exécutez la commande suivante :
        
    ```
    ibmcloud plugin install -f activity-tracker-windows-amd64-3.3.0.exe
    ```
    {: codeblock}

	

## Installation du plug-in {{site.data.keyword.cloudaccesstrailshort}} sous Mac OS X depuis un fichier
{: #install_cli_mac}

Procédez comme suit pour installer le plug-in sous Mac OS X :

1. Téléchargez l'édition la plus récente du plug-in d'interface de ligne de commande du service {{site.data.keyword.cloudaccesstrailshort}} (activity-tracker) depuis la [page de l'interface de ligne de commande {{site.data.keyword.cloud_notm}}](https://clis.ng.bluemix.net/ui/repository.html#bluemix-plugins). 
	
	1. Sélectionnez la valeur de plateforme : **osx**. 
	2. Cliquez sur **Enregistrer le fichier**.  
    
2. Installez le plug-in. Exécutez la commande suivante :
        
    ```
    ibmcloud plugin install -f activity-tracker-darwin-amd64-3.3.0
    ```
    {: codeblock}

	
	
## Désinstallation de l'interface de ligne de commande {{site.data.keyword.cloudaccesstrailshort}}
{: #uninstall_cli}

Pour désinstaller l'interface de ligne de commande, supprimez le plug-in.
{:shortdesc}

Procédez comme suit pour désinstaller l'interface de ligne de commande du service {{site.data.keyword.cloudaccesstrailshort}} :

1. Vérifiez la version du plug-in d'interface de ligne de commande qui est installée.
  
    Par exemple, vérifiez la version du plug-in. Exécutez la commande suivante :
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    
2. Si le plug-in est installé, exécutez la commande `ibmcloud plugin uninstall` pour désinstaller le plug-in d'interface de ligne de commande.

    Exécutez la commande suivante :
        
    ```
    ibmcloud plugin uninstall activity-tracker
    ```
    {: codeblock}
  

## Mise à jour de l'interface de ligne de commande {{site.data.keyword.cloudaccesstrailshort}} depuis le référentiel
{: #update_cli}

Pour mettre à jour l'interface de ligne de commande, exécutez la commande *ibmcloud plugin update*.
{:shortdesc}

Procédez comme suit pour mettre à jour l'interface de ligne de commande du service {{site.data.keyword.cloudaccesstrailshort}} :

1. Mettez à jour le plug-in {{site.data.keyword.cloudaccesstrailshort}}. Exécutez la commande suivante :

    ```
    ibmcloud plugin update activity-tracker -r Bluemix
    ```
    {: codeblock}
 
2. Vérifiez l'installation du plug-in de l'interface CLI.
  
    Par exemple, vérifiez la version du plug-in. Exécutez la commande suivante :
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    





## Obtenir de l'aide
{: #general_cli_help}

Pour obtenir des informations générales sur l'interface de ligne de commande et savoir quelles commandes sont prises en charge, procédez comme suit :

1. Connectez-vous à une région, une organisation et un espace dans {{site.data.keyword.cloud_notm}}. 
    
2. Affichez des informations sur les commandes prises en charge et sur l'interface de ligne de commande. Exécutez la commande suivante :

    ```
    ibmcloud at help 
    ```
    {: codeblock}
    
    

## Obtenir de l'aide sur une commande
{: #command_cli_help}

Pour obtenir de l'aide au sujet de l'utilisation d'une commande, procédez comme suit :

1. Connectez-vous à une région, une organisation et un espace dans {{site.data.keyword.cloud_notm}}. 
    
2. Obtenez la liste des commandes prises en charge et identifiez celle dont vous avez besoin. Exécutez la commande :

    ```
    ibmcloud at help 
    ```
    {: codeblock}

3. Obtenez de l'aide sur la commande. Exécutez la commande suivante :

    ```
    ibmcloud at help *commande*
    ```
    {: codeblock}
    
    où *commande* est le nom d'une commande de l'interface de ligne de commande, par exemple *status*.



## Obtention d'aide sur une sous-commande
{: #subcommand_cli_help}

Une commande peut avoir des sous-commandes. Pour obtenir de l'aide sur des sous-commandes, procédez comme suit :

1. Connectez-vous à une région, une organisation et un espace dans {{site.data.keyword.cloud_notm}}. 
    
2. Obtenez la liste des commandes prises en charge et identifiez celle dont vous avez besoin. Exécutez la commande :

    ```
    ibmcloud at help 
    ```
    {: codeblock}

3. Obtenez de l'aide sur la commande et identifiez les sous-commandes prises en charge. Exécutez la commande suivante :

    ```
    ibmcloud at help *commande*
    ```
    {: codeblock}
    
    où *commande* est le nom d'une commande de l'interface de ligne de commande, par exemple *session*.

4. Obtenez de l'aide sur la commande et identifiez les sous-commandes prises en charge. Exécutez la commande suivante :

    ```
    ibmcloud at *commande* help *sous-commande*
    ```
    {: codeblock}
    
    où 
    
    * *commande* est le nom d'une commande de l'interface de ligne de commande, par exemple *status*.
    * *sous-commande* est le nom d'une sous-commande prise en charge. Par exemple, pour la commande *session*, une sous-commande valide est *list*.


## Affichage des détails du plug-in
{: #show}
  
Utilisez la commande 'ibmcloud plugin show activity-tracker' pour afficher les détails du plug-in. 

```
ibmcloud plugin show activity-tracker
```
{: codeblock}
    




