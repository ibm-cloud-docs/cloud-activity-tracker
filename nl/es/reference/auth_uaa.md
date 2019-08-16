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


# Obtención de una señal de UAA
{: #auth_uaa}

Utilice UAA de {{site.data.keyword.cloud_notm}} para obtener una señal de autenticación que puede utilizar para trabajar con el servicio {{site.data.keyword.cloudaccesstraillong}}. Puede obtener la señal de autenticación mediante la CLI de {{site.data.keyword.cloud_notm}} o mediante las API.
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} está en desuso. A partir del 9 de mayo de 2019, no se pueden suministrar nuevas instancias de {{site.data.keyword.cloudaccesstrailshort}}. Las instancias existentes del plan premium recibirán soporte hasta el 30 de septiembre de 2019. Para seguir supervisando la actividad de la cuenta de {{site.data.keyword.cloud_notm}} suministre una instancia de [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}


Tenga en cuenta la información siguiente:

* La señal tiene un tiempo de caducidad. 
* Cuando se utiliza la señal, se debe incluir *Bearer* del valor de la señal.
		
## Obtención de la señal UAA mediante la CLI de IBM Cloud
{: #uaa_cli_token}

Para obtener una señal de UAA, siga estos pasos:

1. (Requisito previo) Instalar la CLI de {{site.data.keyword.cloud_notm}}.

   Para obtener más información, consulte [Instalación de la CLI de {{site.data.keyword.cloud_notm}}](/docs/cli?topic=cloud-cli-ibmcloud-cli#ibmcloud-cli).
   
   Si la CLI está instalada, continúe en el paso siguiente.
    
2. Inicie una sesión en {{site.data.keyword.cloud_notm}}. 

    Ejecute el mandato [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) para iniciar una sesión en {{site.data.keyword.cloud_notm}} y luego ejecute el mandato [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) para definir la organización y el espacio donde desea suministrar el servicio {{site.data.keyword.cloudaccesstrailshort}}.
	
3. Ejecute el mandato `ibmcloud iam oauth-tokens` para obtener la señal de UAA.

    ```
	ibmcloud iam oauth-tokens
	```
	{: codeblock}
	
	La salida devuelve la señal de UAA.


	


## Obtención de la señal de UAA para una clave de API de plataforma mediante las API
{: #apikey_uaa_token}

Para obtener una señal de UAA para una clave de API de la plataforma, siga estos pasos:

1. Obtenga el punto final de autorización. Ejecute el siguiente mandato cURL:

    ```
    curl https://api.ng.bluemix.net/v2/info
    ```
    {: codeblock}

    En la respuesta, recupere el valor de punto final del campo **authorization_endpoint**.

2. Añada una clave de API de la plataforma.

    En la consola de IBM Cloud, vaya a **Gestionar > Seguridad > Claves de API de la plataforma**.
    A continuación, cree una clave de API.

3. Obtenga la señal. Ejecute el siguiente mandato cURL:

    ```
    curl --user "cf:" --data-urlencode "grant_type=password" --data-urlencode "username=apikey" --data-urlencode "password=$APIKEY" --header "Content-Type: application/x-www-form-urlencoded" --header "Accept: application/json" "AUTHORIZATION_ENDPOINT/oauth/token"
    ```
    {: codeblock}

    donde 
    
    *APIKEY* es el valor de apikey obtenido en un paso anterior.
    
    *AUTHORIZATION_ENDPOINT* representa el punto de entrada en el servicio IAM.

    Por ejemplo:

    ```
    curl --user "cf:" --data-urlencode "grant_type=password" --data-urlencode "username=apikey" --data-urlencode "password=$APIKEY" --header "Content-Type: application/x-www-form-urlencoded" --header "Accept: application/json" "https://login.ng.bluemix.net/UAALoginServerWAR/oauth/token"
    ```
    {: codeblock}


