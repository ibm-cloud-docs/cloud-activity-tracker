---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, configure retention policy

subcollection: cloud-activity-tracker

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}
{:important: .important}
{:note: .note}


# Configuration de la règle de conservation des événements
{: #configuring_retention_policy}

Utilisez la commande **ibmcloud at option** pour afficher et configurer la règle de conservation qui définit le nombre maximal de jours pendant lequel les événements sont conservés dans {{site.data.keyword.cloudaccesstrailshort}}. Par défaut, la règle de conservation est désactivée et les événements sont conservés indéfiniment. Une fois que la durée de conservation a expiré, les événements sont supprimés automatiquement. 
{:shortdesc}

Vous pouvez définir la même règle de conservation pour tous les espaces du compte ou vous pouvez personnaliser la période de conservation pour un espace. 


## Désactivation de la règle de conservation des événements pour un espace
{: #disable_retention_policy_space}

Procédez comme suit pour désactiver une règle de conservation :

1. Connectez-vous à {{site.data.keyword.cloud_notm}}. 

    Exécutez la commande [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) pour vous connecter à {{site.data.keyword.cloud_notm}}, puis exécutez la commande [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) pour définir l'organisation et l'espace où mettre le service {{site.data.keyword.cloudaccesstrailshort}} à disposition.
	
2. Pour désactiver la règle de conservation, définissez la valeur **-1**. Exécutez la commande :

    ```
    ibmcloud at option -r -1
    ```
    {: codeblock}
    
**Exemple**
    
Par exemple, pour désactiver la durée de conservation d'un espace dont l'ID est *d35da1e3-b345-475f-8502-bx cfgh436902a3*, exécutez la commande suivante :

```
ibmcloud at option -r -1
```
{: codeblock}

La sortie est :

```
+-----------------------------------------+-----------+
|               SPACEID                   | RETENTION |
+-----------------------------------------+-----------+
| d35da1e3-b345-475f-8502-bx cfgh436902a3 |        -1 |
+-----------------------------------------+-----------+
```
{: screen} 



## Vérification de la règle de conservation des journaux d'un espace
{: #check_retention_policy_space}

Afin d'obtenir la durée de conservation définie pour un espace {{site.data.keyword.cloud_notm}}, procédez comme suit :

1. Connectez-vous à {{site.data.keyword.cloud_notm}}. 

    Exécutez la commande [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) pour vous connecter à {{site.data.keyword.cloud_notm}}, puis exécutez la commande [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) pour définir l'organisation et l'espace où mettre le service {{site.data.keyword.cloudaccesstrailshort}} à disposition.
	
2. Obtenez la durée de conservation. Exécutez la commande :

    ```
    ibmcloud at option
    ```
    {: codeblock}

    La sortie pour l'ID espace *d35da1e3-b345-475f-8502-bx cfgh436902a3* est 30 jours :

    ```
    +-----------------------------------------+-----------+
    |               SPACEID                   | RETENTION |
    +-----------------------------------------+-----------+
    | d35da1e3-b345-475f-8502-bx cfgh436902a3 |        30 |
    +-----------------------------------------+-----------+
    ```
    {: screen}
    

## Vérification de la règle de conservation des journaux de tous les espaces d'un compte
{: #check_retention_policy_account}

Afin d'obtenir la durée de conservation définie pour chaque espace {{site.data.keyword.cloud_notm}} sur un compte, procédez comme suit :

1. Connectez-vous à {{site.data.keyword.cloud_notm}}. 

    Exécutez la commande [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) pour vous connecter à {{site.data.keyword.cloud_notm}}, puis exécutez la commande [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) pour définir l'organisation et l'espace où mettre le service {{site.data.keyword.cloudaccesstrailshort}} à disposition.
    
2. Obtenez la durée de conservation de chaque espace du compte. Exécutez la commande :

    ```
    ibmcloud at option -a
    ```
    {: codeblock}
	
	où *-a* indique que les informations incluent tous les espaces du compte.

    Par exemple, la sortie de l'exécution de la commande est la suivante :

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
    

## Définition de la règle de conservation des journaux sur le compte
{: #set_retention_policy_space}

Afin de définir la durée de conservation pour un compte {{site.data.keyword.cloud_notm}}, procédez comme suit :

1. Connectez-vous à {{site.data.keyword.cloud_notm}}. 

    Exécutez la commande [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) pour vous connecter à {{site.data.keyword.cloud_notm}}, puis exécutez la commande [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) pour définir l'organisation et l'espace où mettre le service {{site.data.keyword.cloudaccesstrailshort}} à disposition.
	
2. Définissez la durée de conservation. Exécutez la commande :

    ```
    ibmcloud at option -r Nombre_de_jours - a
    ```
    {: codeblock}
    
    où 
	* *-r* est l'option qui doit être spécifiée pour définir une durée de conservation.
	* *Nombre_de_jours* est un nombre entier qui définit le nombre de jours pendant lequel vous souhaitez conserver les événements. 
	* *-a* indique que la demande s'applique à tous les espaces du compte.
    
    
**Exemple**
    
Par exemple, pour conserver un type de journal spécifique dans votre compte pendant seulement 15 jours, exécutez la commande suivante :

```
ibmcloud at option -r 15 -a
```
{: codeblock}

La sortie affiche une entrée pour chaque espace du compte, y compris des informations sur la durée de conservation :

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

## Définition de la règle de conservation des journaux pour un espace
{: #set_retention_policy_account}

Afin d'afficher la durée de conservation pour un espace {{site.data.keyword.cloud_notm}}, procédez comme suit :

1. Connectez-vous à {{site.data.keyword.cloud_notm}}. 

    Exécutez la commande [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) pour vous connecter à {{site.data.keyword.cloud_notm}}, puis exécutez la commande [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) pour définir l'organisation et l'espace où mettre le service {{site.data.keyword.cloudaccesstrailshort}} à disposition.
    
2. Définissez la durée de conservation. Exécutez la commande :

    ```
    ibmcloud at option -r Nombre_de_jours
    ```
    {: codeblock}
    
    où 
	* *-r* est l'option qui doit être spécifiée pour définir une durée de conservation.
	* *Nombre_de_jours* est un nombre entier qui définit le nombre de jours pendant lequel vous souhaitez conserver les événements.
    
    
**Exemple**
    
Par exemple, pour conserver les événements disponibles dans un espace pendant un an, exécutez la commande suivante :

```
ibmcloud at option -r 365
```
{: codeblock}

La sortie est :

```
+-----------------------------------------+-----------+
|               SPACEID                   | RETENTION |
+-----------------------------------------+-----------+
| d35da1e3-b345-475f-8502-bx cfgh436902a3 |       365 |
+-----------------------------------------+-----------+
```
{: screen}


