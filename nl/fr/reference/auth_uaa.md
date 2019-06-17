---

copyright:
  years: 2016, 2019
lastupdated: "2019-06-06"

keywords: IBM Cloud, Activity Tracker, UAA, security

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
{:deprecated: .deprecated}


# Obtention d'un jeton UAA
{: #auth_uaa}

Utilisez {{site.data.keyword.cloud_notm}} UAA pour obtenir un jeton d'authentification dont vous pouvez vous servir pour gérer le service {{site.data.keyword.cloudaccesstraillong}}. Vous pouvez obtenir le jeton d'authentification à l'aide de l'interface de ligne de commande {{site.data.keyword.cloud_notm}}, ou via des API.
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} est obsolète. A compter du 9 mai 2019, vous ne pourrez plus mettre à disposition de nouvelles instances {{site.data.keyword.cloudaccesstrailshort}}. Les instances de plan existantes sont prises en charge jusqu'au 30 septembre 2019. Pour continuer à surveiller l'activité de votre compte {{site.data.keyword.cloud_notm}}, mettez à disposition une instance du [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}


Prenez en compte les informations suivantes :

* Le jeton possède un délai d'expiration. 
* Lorsque vous utilisez le jeton, vous devez inclure *Bearer*, qui provient de la valeur du jeton.
		
## Obtention du jeton UAA à l'aide de l'interface de ligne de commande IBM Cloud
{: #uaa_cli_token}

Pour obtenir le jeton UAA, procédez comme suit :

1. (Prérequis) Installez l'interface de ligne de commande {{site.data.keyword.cloud_notm}}.

   Pour plus d'informations, voir [Installation de l'interface de ligne de commande {{site.data.keyword.cloud_notm}}.](/docs/cli?topic=cloud-cli-ibmcloud-cli#ibmcloud-cli)
   
   Si l'interface de ligne de commande est installée, passez à l'étape suivante.
    
2. Connectez-vous à {{site.data.keyword.cloud_notm}}. 

    Exécutez la commande [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) pour vous connecter à {{site.data.keyword.cloud_notm}}, puis exécutez la commande [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) pour définir l'organisation et l'espace où mettre le service {{site.data.keyword.cloudaccesstrailshort}} à disposition.
	
3. Exécutez la commande `ibmcloud iam oauth-tokens` pour obtenir le jeton UAA.

    ```
	ibmcloud iam oauth-tokens
	```
	{: codeblock}
	
	La sortie de cette commande renvoie le jeton UAA.


	


## Obtention du jeton UAA pour une clé d'API de plateforme via des API
{: #apikey_uaa_token}

Pour obtenir le jeton UAA pour une clé d'API de plateforme, procédez comme suit :

1. Obtenez le noeud final d'autorisation. Exécutez la commande cURL suivante :

    ```
    curl https://api.ng.bluemix.net/v2/info
    ```
    {: codeblock}

    Dans la réponse, extrayez la valeur de noeud final de la zone **authorization_endpoint**.

2. Ajoutez une clé d'API de plateforme.

    Dans la console IBM Cloud, accédez à **Gérer > Sécurité > Clés d'API de la plateforme**.
    Créez ensuite une clé d'API.

3. Obtenez le jeton. Exécutez la commande cURL suivante :

    ```
    curl --user "cf:" --data-urlencode "grant_type=password" --data-urlencode "username=apikey" --data-urlencode "password=$APIKEY" --header "Content-Type: application/x-www-form-urlencoded" --header "Accept: application/json" "AUTHORIZATION_ENDPOINT/oauth/token"
    ```
    {: codeblock}

    où 
    
    *APIKEY* est la valeur apikey obtenue lors d'une étape précédente.
    
    *AUTHORIZATION_ENDPOINT* représente le point d'entrée vers le service IAM.

    Par exemple :

    ```
    curl --user "cf:" --data-urlencode "grant_type=password" --data-urlencode "username=apikey" --data-urlencode "password=$APIKEY" --header "Content-Type: application/x-www-form-urlencoded" --header "Accept: application/json" "https://login.ng.bluemix.net/UAALoginServerWAR/oauth/token"
    ```
    {: codeblock}


