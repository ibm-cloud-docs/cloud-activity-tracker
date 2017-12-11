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

# Ereignisinformationen anzeigen
{: #viewing_event_status}

Verwenden Sie den Befehl *cf at status*, um Informationen zu den Ereignissen abzurufen, die in {{site.data.keyword.cloudaccesstrailshort}} für einen {{site.data.keyword.Bluemix}}-Bereich erfasst und gespeichert werden.
{:shortdesc}

## Informationen zu Ereignissen abrufen
{: #viewing_event_information}

Verwenden Sie den Befehl `cf at status`, um die Größe und Anzahl der Ereignisse und ihre Verfügbarkeit für die Analyse in Kibana anzuzeigen. Weitere Informationen finden Sie in [cf at status](/docs/services/cloud-activity-tracker/cli/at_cli.html#status).

1. Melden Sie sich in {{site.data.keyword.Bluemix_notm}} bei einer Region, einer Organisation und einem Bereich an. 

    ```
    bx login -a Endpoint
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
	</table>

    Befolgen Sie die angegebenen Anweisungen. 

    Führen Sie zum Beispiel den folgenden Befehl aus, um sich bei der Region 'Vereinigte Staaten (Süden)' anzumelden:
	
	```
	bx login -a api.ng.bluemix.net
	```
	{: codeblock}
	
	Legen Sie anschließend die Organisation und den Bereich fest. Führen Sie dazu den folgenden Befehl aus:

    ```
    bx target -o OrgName -s SpaceName
    ```
   {: codeblock}

    Dabei gilt Folgendes:

    * OrgName ist der Name der Organisation.
    * SpaceName ist der Name des Bereichs.
    
2. Führen Sie den Befehl *cf at status* aus, um Details zu den Ereignissen anzuzeigen, die in {{site.data.keyword.cloudaccesstrailshort}} erfasst werden.

    ```
    $ bx cf at status -a -s JJJJ-MM-TT -e JJJJ-MM-TT
    ```
    {: codeblock}
    
    Dabei gilt Folgendes:
    
    * *-a* gibt Informationen auf Kontoebene an
    * *-s* legt das Startdatum in koordinierter Weltzeit (Universal Coordinated Time, UTC) fest: *JJJJ-MM-TT*.
    * *-e* legt das Enddatum in koordinierter Weltzeit (Universal Coordinated Time, UTC) fest: *JJJJ-MM-TT*.
    	
	Verwenden Sie den Befehl `cf at status` und legen Sie mit der Option **-s** das Startdatum und mit der Option **-e** das Enddatum fest. Beispiel:

    * `bx cf at status` stellt Informationen für die letzten 2 Wochen bereit.
    * `bx cf at status -s 2017-05-03` stellt Informationen vom 3. Mai 2017 bis zum aktuellen Datum bereit.
    * `bx cf at status -s 2017-05-03 -e 2017-05-08` stellt Informationen vom 3. bis zum 8. Mai 2017 bereit. 
 
    Verwenden Sie den Befehl `cf at status` mit der Option **-a**, um die Domäne festzulegen, die berücksichtigt werden soll.
	
    Führen Sie zum Beispiel den folgenden Befehl aus, um Informationen zu den verfügbaren Ereignissen für den 10. Juni 2017 abzurufen:
    
    ```
    $ bx cf at status -s 2017-06-10 -e 2017-06-10
    +------------+-------+------+-----------------+------------+
    | Date       | Count | Size | Types           | Searchable |
    +------------+-------+------+-----------------+------------+
    | 2017-07-10 | 1     | 2531 | ActivityTracker | All        |
    +------------+-------+------+-----------------+------------+
    ```
    {: screen}
	














