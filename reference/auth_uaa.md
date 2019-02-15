---

copyright:
  years: 2017, 2018

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


# Getting a UAA token
{: #auth_uaa}

Use {{site.data.keyword.Bluemix}} UAA to get an authentication token that you can use to work with the {{site.data.keyword.cloudaccesstraillong}} service. You can obtain the authentication token by using the {{site.data.keyword.Bluemix_notm}} CLI, or by using APIs.
{:shortdesc}

Consider the following information:

* The token has an expiration time. 
* When you use the token, *Bearer* from the value of the token must be included.
		
## Getting the UAA token by using the IBM Cloud CLI
{: #uaa_cli_token}

To get the UAA token, complete the following steps:

1. (Pre-req) Install the {{site.data.keyword.Bluemix_notm}} CLI.

   For more information, see [Installing the {{site.data.keyword.Bluemix_notm}} CLI](/docs/cli/reference/ibmcloud?topic=cloud-cli-install_use#install_use).
   
   If the CLI is installed, continue with the next step.
    
2. Log in to the {{site.data.keyword.Bluemix_notm}}. 

    Run the [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) command to log in to the {{site.data.keyword.Bluemix_notm}}, and then, run the [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) command to set the organization and space where you want to provision the {{site.data.keyword.cloudaccesstrailshort}} service.
	
3. Run the `ibmcloud iam oauth-tokens` command to get the UAA token.

    ```
	ibmcloud iam oauth-tokens
	```
	{: codeblock}
	
	The output returns the UAA token.


	


## Getting the UAA token for a platform API key by using APIs
{: #apikey_uaa_token}

To get the UAA token for a platform API key, complete the following steps:

1. Get the authorization endpoint. Run the following cURL command:

    ```
    curl https://api.ng.bluemix.net/v2/info
    ```
    {: codeblock}

    In the response, retrieve the endpoint value from the field **authorization_endpoint**.

2. Add a platform API key.

    In the IBM Cloud Console, navigate to **Manage > Security > Platform API Keys**.
    Then, create an API Key.

3. Obtain the token. Run the following cURL command:

    ```
    curl --user "cf:" --data-urlencode "grant_type=password" --data-urlencode "username=apikey" --data-urlencode "password=$APIKEY" --header "Content-Type: application/x-www-form-urlencoded" --header "Accept: application/json" "AUTHORIZATION_ENDPOINT/oauth/token"
    ```
    {: codeblock}

    where 
    
    *APIKEY* is the apikey value obtained in a previous step.
    
    *AUTHORIZATION_ENDPOINT* represents the entry point to the IAM service.

    For example:

    ```
    curl --user "cf:" --data-urlencode "grant_type=password" --data-urlencode "username=apikey" --data-urlencode "password=$APIKEY" --header "Content-Type: application/x-www-form-urlencoded" --header "Accept: application/json" "https://login.ng.bluemix.net/UAALoginServerWAR/oauth/token"
    ```
    {: codeblock}


