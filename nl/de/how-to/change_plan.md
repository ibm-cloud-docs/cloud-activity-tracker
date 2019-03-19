---

copyright:
  years: 2016, 2019
lastupdated: "2019-01-23"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}



# Plan ändern
{: #change_plan}

Sie können Ihren Serviceplan für {{site.data.keyword.cloudaccesstraillong}} über die {{site.data.keyword.cloud_notm}}-Benutzerschnittstelle (UI) oder durch Ausführen des Befehls `ibmcloud service update` ändern. Ein Upgrade oder eine Herabstufung Ihres Plan kann jederzeit vorgenommen werden.
{:shortdesc}

## Serviceplan über die Benutzerschnittstelle ändern
{: #change_plan_ui}

Wenn Sie Ihren Serviceplan über die {{site.data.keyword.cloud_notm}}-Benutzerschnittstelle (UI) ändern wollen, führen Sie die folgenden Schritte aus:

1. Melden Sie sich bei {{site.data.keyword.cloud_notm}} an und klicken Sie im *Dashboard* auf den {{site.data.keyword.cloudaccesstraillong_notm}}-Service. 
    
2. Wählen Sie die Registerkarte **Plan** aus.

    Informationen zu Ihrem aktuellen Plan werden angezeigt.
	
3. Wählen Sie einen neuen Plan aus, um ein Upgrade oder eine Herabstufung für Ihren Plan vorzunehmen. 

4. Klicken Sie auf **Speichern**.



## Serviceplan über die CLI ändern
{: #change_plan_cli}

Wenn Sie Ihren Serviceplan über die Befehlszeilenschnittstelle (CLI) ändern wollen, führen Sie die folgenden Schritte aus:

1. Melden Sie sich bei {{site.data.keyword.cloud_notm}} an. 

    Melden Sie sich durch Ausführen des Befehls [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) bei {{site.data.keyword.cloud_notm}} an und führen Sie dann den Befehl [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) aus, um festzulegen, für welche Organisation und welchen Bereich (Space) der {{site.data.keyword.cloudaccesstrailshort}}-Service bereitgestellt werden soll.
	
2. Führen Sie den Befehl `ibmcloud service list` aus, um Ihren aktuellen Plan zu prüfen und den Namen des {{site.data.keyword.cloudaccesstrailshort}}-Service aus der Liste der in dem Bereich verfügbaren Services abzurufen. 

    Zum Ändern des Plans müssen Sie den Wert aus dem Feld **name** verwenden. 

    Beispiel:
	
	```
	$ ibmcloud service list
    Invoking 'cf services'...

    Getting services in org MyOrg / space dev as xxx@ibm.com...
    OK

    name                       service                  plan                 bound apps                               last operation
    Activity Tracker-zt          OK                     accessTrail             premium                                update succeeded
    ```
	{: screen}
    
3. Nehmen Sie ein Upgrade oder eine Herabstufung für Ihren Plan vor. Führen Sie den Befehl `ibmcloud service update` aus.
    
	```
	ibmcloud service update service_name [-p new_plan]
	```
	{: codeblock}
	
	Dabei gilt Folgendes: 
	
	* *service_name* ist der Name Ihres Service. Diesen Wert können Sie durch Ausführen des Befehls `ibmcloud service list` abrufen.
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
	    <td>free</td>
	  </tr>
	  <tr>
	    <td>Premium</td>
	    <td>premium</td>
	  </tr>
	</table>
	
	Führen Sie zum Beispiel den folgenden Befehl aus, um Ihren Plan auf den Plantyp *Lite* herabzustufen:
	
	```
	ibmcloud service update "Activity Tracker-zt" -p free
    Updating service instance Activity Tracker-zt as xxx@ibm.com...
    OK
	```
	{: screen}



