---

copyright:
  years: 2016, 2017

lastupdated: "2017-09-17"

---


{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# Activity Tracker-Service bereitstellen
{: #provision}

Sie können den {{site.data.keyword.cloudaccesstraillong}}-Service über die {{site.data.keyword.Bluemix}}-Benutzerschnittstelle oder über die Befehlszeile bereitstellen.
{:shortdesc}


## Über die Benutzerschnittstelle bereitstellen
{: #ui}

Führen Sie die folgenden Schritte aus, um eine Instanz des {{site.data.keyword.cloudaccesstraillong_notm}}-Service in {{site.data.keyword.Bluemix_notm}} bereitzustellen:

1. Melden Sie sich bei Ihrem {{site.data.keyword.Bluemix_notm}}-Konto an.

    Das {{site.data.keyword.Bluemix_notm}}-Dashboard finden Sie unter [http://bluemix.net ![Symbole für externen Link](../../../icons/launch-glyph.svg "Symbol für externen Link")](http://bluemix.net){:new_window}.
    
	Nachdem Sie sich mit Ihrer Benutzer-ID und Ihrem Kennwort angemeldet haben, wird die {{site.data.keyword.Bluemix_notm}}-Benutzerschnittstelle geöffnet.

2. Klicken Sie auf **Katalog**. Die Liste der in {{site.data.keyword.Bluemix_notm}} verfügbaren Services wird geöffnet.

3. Wählen Sie die Kategorie **Sicherheit** aus, um die Liste der angezeigten Services zu filtern.

    Der Service ist außerdem in der Kategorie **DevOps** verfügbar.

4. Klicken Sie auf die Kachel **Activity Tracker**.

5. Konfigurieren Sie die entsprechenden Informationen, um zu definieren, wo der Service bereitgestellt werden soll. 

    Geben Sie die Daten ein, wie in der folgenden Tabelle angegeben: 

    <table>
	  <caption>Tabelle 1. Erforderliche Felder zum Bereitstellen des {{site.data.keyword.cloudaccesstrailshort}}-Service</caption>
	  <tr>
	    <th>Feld</th>
		<th>Wert</th>
	  </tr>
	  <tr>
	    <td>Region für die Bereitstellung auswählen:</td>
		<td>Gültige Werte sind: Vereinigte Staaten (Süden), Vereinigtes Königreich und Deutschland.</td>
	  </tr>
	  <tr>
	    <td>Organisation auswählen:</td>
		<td>Wählen Sie die Organisation aus, in der Sie Aktivitäten überwachen möchten.</td>
	  </tr>
	  <tr>
	    <td>Bereich auswählen</td>
		<td>Wählen Sie den Bereich in der ausgewählten Organisation aus, in dem Sie Aktivitäten überwachen möchten.</td>
	  </tr>
	</table>

6. Wählen Sie einen Serviceplan aus. 

    Standardmäßig ist der Plan **Kostenlos** festgelegt.

    Weitere Informationen finden Sie in [Servicepläne](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#plans).
	
7. Klicken Sie auf **Erstellen**, um den {{site.data.keyword.cloudaccesstrailshort}}-Service in dem {{site.data.keyword.Bluemix_notm}}-Bereich bereitzustellen, bei dem Sie angemeldet sind.
  
 

## Über die CLI bereitstellen
{: #cli}

Führen Sie die folgenden Schritte aus, um eine Instanz des {{site.data.keyword.cloudaccesstraillong_notm}}-Service in {{site.data.keyword.Bluemix_notm}} über die Befehlszeile bereitzustellen:

1. Installieren Sie die Cloud Foundry-CLI (CF-CLI). Wenn die CF-CLI installiert ist, fahren Sie mit dem nächsten Schritt fort.

   Weitere Informationen finden Sie in [CF-CLI installieren ![Symbol für externen Link](../../../icons/launch-glyph.svg "Symbol für externen Link")](http://docs.cloudfoundry.org/cf-cli/install-go-cli.html){: new_window}. 
    
2. Melden Sie sich in {{site.data.keyword.Bluemix_notm}} bei einer Region, einer Organisation und einem Bereich an. 

    Führen Sie zum Beispiel den folgenden Befehl aus, um sich bei der Region 'Vereinigte Staaten (Süden)' anzumelden:

    ```
    cf login -a https://api.ng.bluemix.net
    ```
    {: codeblock}

    Befolgen Sie die angegebenen Anweisungen. Geben Sie Ihre {{site.data.keyword.Bluemix_notm}}-Berechtigungsnachweise ein und wählen Sie eine Organisation und einen Bereich aus.
	
3. Führen Sie den Befehl `cf create-service` aus, um eine Instanz bereitzustellen.

    ```
	cf create-service service_name service_plan service_instance_name
	```
	{: codeblock}
	
	Dabei gilt Folgendes:
	
	* service_name ist der Name des Service, d. h. **activityTracker**.
	* service_plan ist der Name des Serviceplans. Eine Liste der Pläne finden Sie in [Servicepläne](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#plans).
	* service_instance_name ist der Name, den Sie für die neue Serviceinstanz verwenden möchten, die Sie erstellen.
	
	Weitere Informationenn zum Befehl 'cf' finden Sie in [cf create-service](/docs/cli/reference/cfcommands/index.html#cf_create-service).

	Führen Sie zum Beispiel den folgenden Befehl aus, um eine Instanz des {{site.data.keyword.cloudaccesstrailshort}}-Service mit dem Lite-Plan zu erstellen:
	
	```
	cf create-service activityTracker free my_activity_tracker_svc
	```
	{: codeblock}
	
4. Überprüfen Sie, dass der Service erfolgreich erstellt wird. Führen Sie dazu den folgenden Befehl aus:

    ```	
	cf services
	```
	{: codeblock}
	
	Die Ausgabe nach dem Ausführen des Befehls sieht wie folgt aus:
	
	```
    Getting services in org MyOrg / space MySpace as xxx@yyy.com...
    OK
    
    name                           service                  plan                   bound apps              last operation
    my_activity_tracker_svc        activityTracker          free                                           create succeeded
	```
	{: screen}

	



