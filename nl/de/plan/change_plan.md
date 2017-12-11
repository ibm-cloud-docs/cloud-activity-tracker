---

copyright:
  years: 2017
lastupdated: "2017-09-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# Plan ändern
{: #change_plan}

Sie können Ihren {{site.data.keyword.cloudaccesstraillong}}-Serviceplan in {{site.data.keyword.Bluemix_notm}} über das Service-Dashboard ändern oder durch Ausführen des Befehls `cf update-service`. Sie können für Ihren Plan jederzeit ein Upgrade oder eine Herabstufung vornehmen.{:shortdesc}

## Serviceplan über die Benutzerschnittstelle ändern
{: #change_plan_ui}

Führen Sie die folgenden Schritte aus, um Ihren Serviceplan in {{site.data.keyword.Bluemix_notm}} über das Service-Dashboard zu ändern:

1. Melden Sie sich bei {{site.data.keyword.Bluemix_notm}} an und klicken Sie dann auf den {{site.data.keyword.cloudaccesstraillong_notm}}-Service im {{site.data.keyword.Bluemix_notm}}-Dashboard. 
    
2. Wählen Sie die Registerkarte **Plan** in der {{site.data.keyword.Bluemix_notm}}-Benutzerschnittstelle aus.

    Informationen zu Ihrem aktuellen Plan werden angezeigt.
	
3. Wählen Sie einen neuen Plan aus, um ein Upgrade oder eine Herabstufung für Ihren Plan vorzunehmen. 

4. Klicken Sie auf **Speichern**.



## Serviceplan über die CLI ändern
{: #change_plan_cli}

Führen Sie die folgenden Schritte aus, um Ihren Serviceplan in Bluemix über die CLI zu ändern:

1. Melden Sie sich in {{site.data.keyword.Bluemix_notm}} bei einer Region, einer Organisation und einem Bereich an. 

    ```
    cf login -a Endpoint
    ```
    {: codeblock}
	
	Dabei ist *Endpoint* die URL für die Anmeldung bei {{site.data.keyword.Bluemix_notm}}. Diese URL variiert je nach Region.
	
	<table>
	    <caption>Liste der Endpunkte für den Zugriff auf {{site.data.keyword.Bluemix_notm}}</caption>
		<tr>
		  <th>Region</th>
		  <th>URL</th>
		</tr>
		<tr>
		  <td>Vereinigte Staaten (Süden)</td>
		  <td>api.ng.bluemix.net</td>
		</tr>
		<tr>
		  <td>Vereinigtes Königreich</td>
		  <td>api.eu-gb.bluemix.net</td>
		</tr>
		<tr>
		  <td>Deutschland</td>
		  <td>api.eu-de.bluemix.net</td>
		</tr>
	</table>

    Befolgen Sie die angegebenen Anweisungen. Geben Sie Ihre {{site.data.keyword.Bluemix_notm}}-Berechtigungsnachweise ein und wählen Sie eine Organisation und einen Bereich aus. 

    Führen Sie zum Beispiel den folgenden Befehl aus, um sich bei der Region 'Vereinigte Staaten (Süden)' anzumelden:
	
	```
	cf login -a api.ng.bluemix.net
	```
	{: codeblock}
	
2. Führen Sie den Befehl `cf services` aus, um Ihren aktuellen Plan zu prüfen und den Namen des {{site.data.keyword.cloudaccesstrailshort}}-Service in der Liste der in dem Bereich verfügbaren Services abzurufen. 

    Sie müssen den Wert aus dem Feld **name** verwenden, um den Plan zu ändern. 

    Beispiel:
	
	```
	$ cf services
    Getting services in org MyOrg / space dev as xxx@yyy.com...
    OK

    name                            service              plan          bound apps      last operation
    Activity Tracker-oj            activityTracker       premium                       create succeeded
    ```
	{: screen}
    
3. Nehmen Sie ein Upgrade oder eine Herabstufung für Ihren Plan vor. Führen Sie dazu den Befehl `cf update-service` aus.
    
	```
	cf update-service service_name [-p new_plan]
	```
	{: codeblock}
	
	Dabei gilt Folgendes: 
	
	* *service_name* ist der Name Ihres Service. Sie können den Befehl `cf services` ausführen, um den Wert abzurufen.
	* *new_plan* ist der Name des Plans.
	
	In der folgenden Tabelle sind die verschiedenen Pläne und die zugehörigen unterstützten Werte aufgelistet:
	
	<table>
	  <caption>Tabelle 1. Liste der Pläne</caption>
	  <tr>
	    <th>Plan</th>
	    <th>Name</th>
	  </tr>
	  <tr>
	    <td>Lite</td>
	    <td>lite</td>
	  </tr>
	  <tr>
	    <td>Premium</td>
	    <td>premium</td>
	  </tr>
	</table>
	
	Führen Sie zum Beispiel den folgenden Befehl aus, um Ihren Plan in den Plantyp *Lite* herabzustufen:
	
	```
	cf update-service "Activity Tracker-oj" -p lite
    Updating service instance Activity Tracker-oj as xxx@yyy.com...
    OK
	```
	{: screen}

4. Überprüfen Sie, dass der neue Plan geändert wurde. Führen Sie dazu den Befehl `cf services` aus.

    ```
	cf services
    Getting services in org MyOrg / space dev as xxx@yyy.com...
    OK

    name                   service            plan      bound apps   last operation
    Activity Tracker-oj    activityTracker    lite                   update succeeded
	```
	{: screen}






