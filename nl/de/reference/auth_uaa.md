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


# UAA-Token abrufen
{: #auth_uaa}

Verwenden Sie die {{site.data.keyword.Bluemix}}-UAA, um ein Authentifizierungstoken abzurufen, das Sie zum Arbeiten mit dem {{site.data.keyword.cloudaccesstraillong}}-Service verwenden können. Dieses Authentifizierungstoken können Sie über die Befehlszeilenschnittstelle (CLI) für {{site.data.keyword.Bluemix_notm}} oder mithilfe von APIs abrufen.
{:shortdesc}

Berücksichtigen Sie die folgenden Informationen:

* Das Token ist nicht unbegrenzt gültig, sondern hat eine Ablaufzeit. 
* Wenn Sie das Token verwenden, muss der *Träger* aus dem Wert des Tokens eingebunden werden.
		
## Abrufen des UAA-Tokens mithilfe der IBM Cloud-CLI
{: #uaa_cli_token}

Führen Sie zum Abrufen des UAA-Tokens die folgenden Schritte aus:

1. (Voraussetzung) Installieren Sie die Befehlszeilenschnittstelle (CLI) für {{site.data.keyword.Bluemix_notm}}.

   Weitere Informationen finden Sie in [{{site.data.keyword.Bluemix_notm}}-Befehlszeilenschnittstelle (CLI) installieren](/docs/cli/reference/ibmcloud/download_cli.html#install_use).
   
   Wenn die CLI installiert ist, fahren Sie mit dem nächsten Schritt fort.
    
2. Melden Sie sich bei {{site.data.keyword.Bluemix_notm}} an. 

    Melden Sie sich durch Ausführen des Befehls [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) bei {{site.data.keyword.Bluemix_notm}} an und führen Sie dann den Befehl [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) aus, um festzulegen, für welche Organisation und welchen Bereich (Space) der {{site.data.keyword.cloudaccesstrailshort}}-Service bereitgestellt werden soll.
	
3. Rufen Sie das UAA-Token durch Ausführen des Befehls `ibmcloud iam oauth-tokens` ab.

    ```
	ibmcloud iam oauth-tokens
	```
	{: codeblock}
	
	Die Ausgabe gibt das UAA-Token zurück.


	


## Abrufen des UAA-Tokens für einen Plattform-API-Schlüssel mithilfe von APIs
{: #apikey_uaa_token}

Führen Sie zum Abrufen des UAA-Tokens für einen Plattform-API-Schlüssel die folgenden Schritte aus:

1. Rufen Sie den Berechtigungsendpunkt ab. Führen Sie den folgenden cURL-Befehl aus:

    ```
    curl https://api.ng.bluemix.net/v2/info
    ```
    {: codeblock}

    Rufen Sie in der Antwort den Endpunktwert aus dem Feld **authorization_endpoint** ab.

2. Fügen Sie einen Plattform-API-Schlüssel hinzu.

    Navigieren Sie in der IBM Cloud-Konsole zu **Verwalten > Sicherheit > Plattform-API-Schlüssel**.
    Erstellen Sie anschließend einen API-Schlüssel.

3. Rufen Sie das Token ab. Führen Sie den folgenden cURL-Befehl aus:

    ```
    curl --user "cf:" --data-urlencode "grant_type=password" --data-urlencode "username=apikey" --data-urlencode "password=$APIKEY" --header "Content-Type: application/x-www-form-urlencoded" --header "Accept: application/json" "AUTHORIZATION_ENDPOINT/oauth/token"
    ```
    {: codeblock}

    Dabei gilt Folgendes: 
    
    *APIKEY* ist der 'apikey'-Wert, den Sie im vorherigen Schritt abgerufen haben.
    
    *AUTHORIZATION_ENDPOINT* stellt den Eingangspunkt zum IAM-Service dar.

    Beispiel:

    ```
    curl --user "cf:" --data-urlencode "grant_type=password" --data-urlencode "username=apikey" --data-urlencode "password=$APIKEY" --header "Content-Type: application/x-www-form-urlencoded" --header "Accept: application/json" "https://login.ng.bluemix.net/UAALoginServerWAR/oauth/token"
    ```
    {: codeblock}


