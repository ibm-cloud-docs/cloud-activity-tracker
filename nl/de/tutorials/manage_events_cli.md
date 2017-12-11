---

copyright:
  years: 2016, 2017

lastupdated: "2017-09-07"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# Ereignisse mithilfe der Activity Tracker-CLI verwalten
{: #tutorial2}

In diesem Lernprogramm erfahren Sie, wie Sie mit der {{site.data.keyword.cloudaccesstrailshort}}-CLI Ereignisse über die Befehlszeile verwalten können. Hier erhalten Sie Informationen zum Abrufen gespeicherter Ereignisse, zum Herunterladen von Ereignissen, die in der {{site.data.keyword.IBM_notm}} Cloud gespeichert sind und zum Löschen von Ereignissen.
{:shortdesc}

Führen Sie die folgenden Schritte aus:

1. [{{site.data.keyword.IBM_notm}} Key Protect-Service bereitstellen und Ereignisse generieren](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step1)
2. [Informationen zu gespeicherten Ereignissen abrufen (cf at status)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step2)
2. [Durch Erstellen einer Sitzung angeben, welche Protokolle heruntergeladen werden (cf at session create)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step3)
3. [Tatsächliche Protokolldaten abrufen (cf at download)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step4)
4. [Nach Beendigung des Downloads die Sitzung löschen (cf at session delete)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step5)
5. [Nicht erforderliche Protokolle manuell löschen (cf at delete)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step6)


## Voraussetzungen
{: #assumptions}

1. Sie verfügen über eine {{site.data.keyword.Bluemix_notm}}-Benutzer-ID mit Entwicklerberechtigungen zum Arbeiten in einem Bereich eines {{site.data.keyword.Bluemix_notm}}-Kontos, in dem der {{site.data.keyword.IBM_notm}} Cloud {{site.data.keyword.cloudaccesstrailshort}}-Service bereitgestellt ist. 

    Weitere Information zum Bereitstellen des {{site.data.keyword.cloudaccesstrailshort}}-Service finden Sie in [{{site.data.keyword.cloudaccesstrailshort}}-Service](/docs/services/cloud-activity-tracker/how-to/provision.html#provision) bereitstellen.

2. Das CF-Plug-in für {{site.data.keyword.cloudaccesstrailshort}} ist in Ihrem lokalen System installiert. Dies ist erforderlich, damit Sie die {{site.data.keyword.cloudaccesstrailshort}}-CLI zum Verwalten von Ereignissen über die Befehlszeile verwenden können. 

    Weitere Informationen zum Installieren des CF-Plug-ins für {{site.data.keyword.cloudaccesstrailshort}} finden Sie in [{{site.data.keyword.cloudaccesstrailshort}}-CLI konfigurieren](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#config_at_cli).

3. Sie haben sich mit dem folgenden Befehl über die Befehlszeile bei {{site.data.keyword.Bluemix_notm}} angemeldet:

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

    Führen Sie zum Beispiel den folgenden Befehl aus, um sich bei der Region 'Vereinigte Staaten (Süden)' anzumelden:
	
	```
	bx cf login -a api.ng.bluemix.net
	```
	{: codeblock}

	**Anmerkung:** Sie müssen sich bei der Region, der Oranisation und dem Bereich in {{site.data.keyword.Bluemix_notm}} anmelden, in dem der {{site.data.keyword.cloudaccesstrailshort}}-Service bereitgestellt ist, damit Sie {{site.data.keyword.cloudaccesstrailshort}}-Befehle ausführen und Ihre Ereignisse über die Befehlszeile verwalten können.
	
	Legen Sie anschließend die Organisation und den Bereich fest. Führen Sie dazu den folgenden Befehl aus:

    ```
    bx target -o OrgName -s SpaceName
    ```
    {: codeblock}

    Dabei gilt Folgendes:

    * OrgName ist der Name der Organisation.
    * SpaceName ist der Name des Bereichs.


## Schritt: IBM Key Protect-Service bereitstellen und Ereignisse generieren 
{: #step1}
	
1. Führen Sie die folgenden Schritte aus, um eine Instanz des {{site.data.keyword.keymanagementserviceshort}}-Service in {{site.data.keyword.Bluemix_notm}} bereitzustellen:

    1. Melden Sie sich bei Ihrem {{site.data.keyword.Bluemix_notm}}-Konto an.

        Das {{site.data.keyword.Bluemix_notm}}-Dashboard finden Sie unter [http://bluemix.net](http://bluemix.net).

        Nachdem Sie sich mit Ihrer Benutzer-ID und Ihrem Kennwort angemeldet haben, wird die {{site.data.keyword.Bluemix_notm}}-Benutzerschnittstelle geöffnet.

    2. Klicken Sie auf **Katalog**. Die Liste der in {{site.data.keyword.Bluemix_notm}} verfügbaren Services wird geöffnet.

        Wählen Sie die Kategorie **Sicherheit** aus, um die Liste der angezeigten Services zu filtern.

    3. Wählen Sie die Kachel **Key Protect** aus.

    4. Klicken Sie auf **Erstellen**, um den {{site.data.keyword.keymanagementserviceshort}}-Service in dem {{site.data.keyword.Bluemix_notm}}-Bereich bereitzustellen, bei dem Sie angemeldet sind.

2. Führen Sie die folgenden Schritte aus, um ein {{site.data.keyword.cloudaccesstrailshort}}-Ereignis zu generieren:

    1. Wählen Sie im {{site.data.keyword.Bluemix_notm}}-Dashboard den {{site.data.keyword.keymanagementserviceshort}}-Service aus. Das {{site.data.keyword.keymanagementserviceshort}}-Dashboard wird geöffnet. Wählen Sie anschließend die Registerkarte **Verwalten** aus.

    2. Klicken Sie auf **Schlüssel hinzufügen**. Ein neues Fenster wird geöffnet.

        ![{{site.data.keyword.keymanagementserviceshort}}-Fenster zum Hinzufügen von Schlüsseln](images/KP_f2.gif)

    3. Wählen Sie **Schlüssel generieren** aus und führen Sie die folgenden Schritte aus:

        * Geben Sie einen Namen für den Schlüssel ein (z. B. *MeinErsterSchlüssel*).

        * Wählen Sie den Algorithmus für den Schlüssel aus.

        * Klicken Sie auf **Schlüssel hinzufügen**. 

3. Überprüfen Sie, dass ein Ereignis erstellt wurde:

    1. Wählen Sie im {{site.data.keyword.Bluemix_notm}}-Dashboard den {{site.data.keyword.cloudaccesstrailshort}}-Service aus. Das Service-Dashboard wird geöffnet.

    2. Konfigurieren Sie die Ansicht, in der nach den {{site.data.keyword.keymanagementserviceshort}}-Ereignissen gesucht werden soll, die beim Bereitstellen des Service und Hinzufügen eines Schlüssels generiert wurden.

        * Wählen Sie **Bereichsprotokolle** für das Feld *Protokolle anzeigen* aus.
	    * Wählen Sie **target.name** für das Feld *Suchfeld* aus.
	    * Geben Sie **ibm-key-protect** in das Feld *Filter* ein.
	
	    Die angezeigten Daten enthalten verfügbare {{site.data.keyword.keymanagementserviceshort}}-Ereignisse für die letzten 24 Stunden. 

	    Verwaltungsregisterkarte in ![{{site.data.keyword.cloudaccesstrailshort}}](images/KP_f3.gif)

## Schritt 2: Informationen zu den gespeicherten Ereignissen abrufen
{: #step2}

Überprüfen Sie, dass Ereignisse zum Herunterladen verfügbar sind. Wenn Sie beispielsweise einen Schlüssel am aktuellen Datum bereitstellen und hinzufügen, führen Sie den folgenden Befehl aus, um Information zu den heute erfassten Ereignissen abzurufen:

```
bx cf at status -s 2017-07-25 -e 2017-07-25
+------------+-------+-------+------------+
| Date       | Count | Size  | Searchable |
+------------+-------+-------+------------+
| 2017-07-25 | 12    | 34994 | All        |
+------------+-------+-------+------------+
```
{: screen}

Dieser Befehl zählt die Ereignisse für den 25. Juni 2017.  {{site.data.keyword.cloudaccesstrailshort}} ist ein globaler Service, darum sind die Tage in koordinierter Weltzeit (UTC) angegeben. Um die Ereignisse für einen bestimmten Tag der Ortszeit abzurufen, müssen Sie gegebenenfalls die Daten für mehrere UTC-Tage herunterladen.

Um die Informationen für mehrere Tage anzuzeigen, verwenden Sie `-s`, um das Startdatum anzugeben und `-e`, um das Enddatum anzugeben. 

Weitere Informationen zum Befehl `cf at status` finden Sie in der [CLI-Referenz](/docs/services/cloud-activity-tracker/cli/at_cli.html#status).

Verwenden Sie den Befehl `bx cf at help status`, um Hilfeinformationen über die Befehlszeile abzurufen.

## Schritt 3: Ereignisse zum Herunterladen angeben
{: #step3}

Erstellen Sie eine Sitzung, bevor Sie Ereignisse herunterladen:

* In der Sitzung wird angegeben, welche Ereignisse heruntergeladen werden.
* Wenn das Herunterladen der Ereignisse unterbrochen wird, ermöglicht die Sitzung das Fortsetzen des Vorgangs ab dem Unterbrechungspunkt. 

Erstellen Sie mit dem folgenden Befehl eine Sitzung:

```
bx cf at session create -s 2017-07-25 -e 2017-07-25
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| id           | 21b19aeb-3d32-4c60-b912-517609c62db2      |
| space        | 667fb895-b5f5-46c9-9f0e-cf4587341095      |
| username     | xxx@yyy.com                               |
| create-time  | 2017-07-25T18:33:22.678350874Z            |
| access-time  | 2017-07-25T18:33:22.678350874Z            |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
+--------------+-------------------------------------------+
```

Einer Sitzung ist ein Startdatum und ein Enddatum zugeordnet. Der Download-Befehl bezieht die Ereignisse zwischen diesen einschließlichen Datumsangaben ein. Der Standarddatumsbereich ist nur der aktuelle Tag. 

Der wichtige Teil der Befehlsausgabe ist die `ID` der Sitzung. Sie wird im Download-Befehl referenziert.

Um Informationen zu bestehenden Sitzungen abzurufen, geben Sie `cf at session list` ein.

Weitere Informationen zu Sitzungen und zum Befehl `cf at session create` finden Sie in der [CLI-Referenz](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_create).

Verwenden Sie den Befehl `cf at session help create`, um Hilfeinformationen über die Befehlszeile abzurufen.

## Schritt 4: Laden Sie die Ereignisse herunter, die für den Bereich erkannt werden, der für die Sitzung definiert ist
{: #step4}

Führen Sie den folgenden Befehl aus, um die in den Sitzungsparametern angegebenen Ereignisse herunterzuladen:

```
$ bx cf at events download -o events.log 21b19aeb-3d32-4c60-b912-517609c62db2
 6.70 KiB / 3.06 KiB [================================================================================================================================================================] 219.03% 8.60 MiB/s 0s
Download Successful
```

* Der Parameter `-o` gibt eine Ausgabedatei an.
* Die Sitzungs-ID wird zuletzt angegeben. Den Wert für die Sitzungs-ID können Sie der Ausgabe des Befehls `cf at session create` entnehmen.
* Beim Herunterladen der Ereignisse nimmt der Fortschrittsanzeiger von 0 bis 100 % zu.

Die Daten werden im komprimierten JSON-Format heruntergeladen.  

Weitere Informationen zum Befehl `cf at download` finden Sie in der [CLI-Referenz](/docs/services/cloud-activity-tracker/cli/at_cli.html#download).

Verwenden Sie den Befehl `bx cf at help download`, um Hilfeinformationen über die Befehlszeile abzurufen.

## Schritt 5: Sitzung löschen
{: #step5}

Wenn der Download abgeschlossen ist, löschen Sie die Sitzung. 

Die Anzahl der Sitzungen ist begrenzt. Sitzungen werden nicht automatisch gelöscht. Sie müssen Sitzungen, die nicht erforderlich sind, manuell löschen. 

```
$ bx cf at session delete 21b19aeb-3d32-4c60-b912-517609c62db2
+---------+------------------------+
| name    | value                  |
+---------+------------------------+
| message | Delete session success |
+---------+------------------------+
```

Weitere Informationen zum Befehl `cf at session delete` finden Sie in der [CLI-Referenz](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_delete).

Verwenden Sie den Befehl `bx cf at session help delete`, um Hilfeinformationen über die Befehlszeile abzurufen.

## Schritt 6: Ereignisse in Activity Tracker manuell löschen
{: #step6}

Sie können die Aufbewahrungsdauer für Îhre Ereignisse in {{site.data.keyword.cloudaccesstrailshort}} steuern. Sie können Ereignisse manuell löschen oder das automatische Löschen von Ereignissen konfigurieren.

Um Ereignisse manuell zu löschen, führen Sie den Befehl `cf at delete` aus. Beispiel:

```
$ bx cf at delete -s 2017-07-25 -e 2017-07-25
Deleted successfully
"6 logs were deleted,freeing 13737 bytes."
```

Weitere Informationen zum Befehl `cf at delete` finden Sie in der [CLI-Referenz](/docs/services/cloud-activity-tracker/cli/at_cli.html#delete).

Verwenden Sie den Befehl `bx cf at help delete`, um Hilfeinformationen über die Befehlszeile abzurufen.

**Anmerkung:** Um Ereignisse automatisch zu löschen, können Sie mit dem CLI-Befehl `cf at option` eine Aufbewahrungsrichtlinie festlegen. Weitere Informationen finden Sie in der [CLI-Referenz](/docs/services/cloud-activity-tracker/cli/at_cli.html#option).


