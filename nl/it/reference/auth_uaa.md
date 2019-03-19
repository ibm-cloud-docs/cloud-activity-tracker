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


# Acquisizione di un token UAA
{: #auth_uaa}

Utilizza {{site.data.keyword.Bluemix}} UAA per ottenere un token di autenticazione che puoi utilizzare con il servizio {{site.data.keyword.cloudaccesstraillong}}. Puoi ottenere il token di autenticazione utilizzando la CLI {{site.data.keyword.cloud_notm}} o le API.
{:shortdesc}

Tieni conto delle seguenti informazioni:

* Il token ha un'ora di scadenza. 
* Quando utilizzi il token, deve essere incluso *Bearer* dal valore del token.
		
## Acquisizione del token UAA utilizzando la CLI IBM Cloud
{: #uaa_cli_token}

Per acquisire il token UAA, completa la seguente procedura:

1. (Pre-requisito) Installa la CLI {{site.data.keyword.cloud_notm}}.

   Per ulteriori informazioni, vedi [Installazione della CLI {{site.data.keyword.cloud_notm}}](/docs/cli?topic=cloud-cli-ibmcloud-cli#ibmcloud-cli).
   
   Se la CLI è installata, continua con il prossimo passo.
    
2. Accedi a {{site.data.keyword.cloud_notm}}. 

    Esegui il comando [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) per accedere a {{site.data.keyword.cloud_notm}} e poi esegui il comando [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) per configurare l'organizzazione e lo spazio in cui vuoi eseguire il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}.
	
3. Immetti il comando `ibmcloud iam oauth-tokens` per ottenere il token UAA.

    ```
	ibmcloud iam oauth-tokens
	```
	{: codeblock}
	
	L'output restituisce il token UAA.


	


## Acquisizione del token UAA per una chiave API della piattaforma utilizzando le API
{: #apikey_uaa_token}

Per ottenere il token UAA per una chiave API della piattaforma, completa la seguente procedura:

1. Ottieni l'endpoint di autorizzazione. Immetti il seguente comando cURL:

    ```
    curl https://api.ng.bluemix.net/v2/info
    ```
    {: codeblock}

    Nella risposta, richiama il valore dell'endpoint dal campo **authorization_endpoint**.

2. Aggiungi una chiave API della piattaforma.

    Nella console IBM Cloud, passa a **Manage > Security > Platform API Keys**.
    Quindi, crea una chiave API.

3. Ottieni il token. Immetti il seguente comando cURL:

    ```
    curl --user "cf:" --data-urlencode "grant_type=password" --data-urlencode "username=apikey" --data-urlencode "password=$APIKEY" --header "Content-Type: application/x-www-form-urlencoded" --header "Accept: application/json" "AUTHORIZATION_ENDPOINT/oauth/token"
    ```
    {: codeblock}

    dove 
    
    *APIKEY* è il valore apikey ottenuto in un passo precedente.
    
    *AUTHORIZATION_ENDPOINT* rappresenta il punto di ingresso del servizio IAM.

    Ad esempio:

    ```
    curl --user "cf:" --data-urlencode "grant_type=password" --data-urlencode "username=apikey" --data-urlencode "password=$APIKEY" --header "Content-Type: application/x-www-form-urlencoded" --header "Accept: application/json" "https://login.ng.bluemix.net/UAALoginServerWAR/oauth/token"
    ```
    {: codeblock}


