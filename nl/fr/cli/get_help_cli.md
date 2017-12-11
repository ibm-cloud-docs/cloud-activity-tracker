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

# Obtention d'aide sur l'utilisation de l'interface de ligne de commande d'Activity Tracker
{: #get_help_cli}

L'interface de ligne de commande d'{{site.data.keyword.cloudaccesstrailshort}} propose différents types d'aide : l'aide générale sur l'interface de ligne de commande et les commandes prise en charge, l'aide sur les commandes pour savoir comment utiliser une commande et l'aide sur les sous-commandes pour savoir comment utiliser une sous-commande d'une commande.
{:shortdesc}


## Obtenir de l'aide
{: #general_cli_help}

Pour obtenir des informations générales sur l'interface de ligne de commande et savoir quelles commandes sont prises en charge, procédez comme suit :

1. Connectez-vous à un espace, une organisation ou une région {{site.data.keyword.Bluemix_notm}}. 

    Par exemple, pour vous connecter à la région du sud des États-Unis, exécutez la commande suivante :
	
	```
    bx login -a https://api.ng.bluemix.net
    ```
    {: codeblock}
    
2. Affichez des informations sur les commandes prises en charge et sur l'interface de ligne de commande. Exécutez la commande suivante :

    ```
    bx cf at help 
    ```
    {: codeblock}
    
    

## Obtenir de l'aide sur une commande
{: #command_cli_help}

Pour obtenir de l'aide au sujet de l'utilisation d'une commande, procédez comme suit :

1. Connectez-vous à un espace, une organisation ou une région {{site.data.keyword.Bluemix_notm}}. 

    Par exemple, pour vous connecter à la région du sud des États-Unis, exécutez la commande suivante :
	
	```
    bx login -a https://api.ng.bluemix.net
    ```
    {: codeblock}
    
2. Obtenez la liste des commandes prises en charge et identifiez celle dont vous avez besoin. Exécutez la commande :

    ```
    bx cf at help 
    ```
    {: codeblock}

3. Obtenez de l'aide sur la commande. Exécutez la commande suivante :

    ```
    bx cf at help *Command*
    ```
    {: codeblock}
    
    où *Command* est le nom d'une commande de l'interface de ligne de commande, par exemple *status*.



## Obtention d'aide sur une sous-commande
{: #subcommand_cli_help}

Une commande peut avoir des sous-commandes. Pour obtenir de l'aide sur des sous-commandes, procédez comme suit :

1. Connectez-vous à un espace, une organisation ou une région {{site.data.keyword.Bluemix_notm}}. 

    Par exemple, pour vous connecter à la région du sud des États-Unis, exécutez la commande suivante :
	
	```
    bx login -a https://api.ng.bluemix.net
    ```
    {: codeblock}
    
2. Obtenez la liste des commandes prises en charge et identifiez celle dont vous avez besoin. Exécutez la commande :

    ```
    bx cf at help 
    ```
    {: codeblock}

3. Obtenez de l'aide sur la commande et identifiez les sous-commandes prises en charge. Exécutez la commande suivante :

    ```
    bx cf at help *Command*
    ```
    {: codeblock}
    
    où *Command* est le nom d'une commande de l'interface de ligne de commande, par exemple *session*.

4. Obtenez de l'aide sur la commande et identifiez les sous-commandes prises en charge. Exécutez la commande suivante :

    ```
    bx cf at *Command* help *Subcommand*
    ```
    {: codeblock}
    
    où 
    
    * *Command* est le nom d'une commande de l'interface de ligne de commande, par exemple *status*.
    * *Subcommand* est le nom d'une sous-commande prise en charge. Par exemple, pour la commande *session*, une sous-commande valide est *list*.




