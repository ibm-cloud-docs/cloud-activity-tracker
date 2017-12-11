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

# Ereignisse herunterladen
{: #downloading_events}

Sie können Ereignisse in eine lokale Datei herunterladen oder an ein anderes Programm weiterleiten. Ereignisse werden im Kontext einer Sitzung heruntergeladen. In einer Sitzung wird angegeben, welche Ereignisse heruntergeladen werden. Wenn das Herunterladen der Ereignisse unterbrochen wird, ermöglicht die Sitzung das Fortsetzen des Vorgangs ab dem Unterbrechungspunkt. Nachdem der Download abgeschlossen ist, müssen Sie die Sitzung löschen.
{:shortdesc}

Führen Sie die folgenden Schritte aus, um die in einem {{site.data.keyword.Bluemix_notm}}-Bereich verfügbaren Ereignisse in eine lokale Datei herunterzuladen:

## Schritt 1: Melden Sie sich bei Bluemix an
{: #prereq}

Melden Sie sich zuerst in {{site.data.keyword.Bluemix_notm}} bei einer Region, einer Organisation und einem Bereich an, in dem der {{site.data.keyword.cloudaccesstrailshort}}-Service bereitgestellt ist. 

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

## Schritt 2: Ermitteln Sie, welche Ereignisse verfügbar sind.
{: #step2}

1. Verwenden Sie den Befehl `cf at status`, um die verfügbaren Ereignisse anzuzeigen.

    Führen Sie zum Beispiel den folgenden Befehl aus, um anzuzeigen, welche Ereignisse für die letzten zwei Wochen verfügbar sind:

    ```
    $ bx cf at status
    ```
    {: codeblock}
    
    Die Ausführung dieses Befehls liefert die folgende Ausgabe:
    
    ```
    +------------+--------+-------+--------------------+------------+
    |    DATE    |  COUNT | SIZE  |       TYPES        | SEARCHABLE |
    +------------+--------+-------+--------------------+------------+
    | 2017-07-24 |    16  | 3020  | ActivityTracker    |   None     |
    +------------+--------+-------+--------------------+------------+
    | 2017-07-25 |   1224 | 76115 | ActivityTracker    |    All     |
    +------------+--------+-------+--------------------+------------+
    ```
    {: screen}

    **Anmerkung:** Der {{site.data.keyword.cloudaccesstrailshort}}-Service ist ein globaler Service und verwendet die koordinierte Weltzeit (Coordinated Universal Time, UTC). Tage sind als UTC-Tage definiert. Um die Ereignisse für einen bestimmten Tag der Ortszeit abzurufen, müssen Sie gegebenenfalls die Daten für mehrere UTC-Tage herunterladen.
	
	Weitere Informationen finden Sie in [cf at status](/docs/services/cloud-activity-tracker/cli/at_cli.html#status).


## Schritt 3: Eine Sitzung erstellen
{: #step3}

Eine Sitzung ist erforderlich, um den Bereich der Ereignisdaten zu definieren, die für den Download verfügbar sind, und den Downloadstatus beizubehalten. 

Verwenden Sie den Befehl [cf at session create](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_create), um eine Sitzung zu erstellen. Beim Erstellen einer Sitzung können Sie optional das Startdatum und das Enddatum angeben. 

**Anmerkung:** Wenn Sie Start- und Enddatum angeben, bietet die Sitzung Zugriff auf die Ereignisse in diesem (einschließlichen) Datumsbereich. 

Führen Sie den folgenden Befehl aus, um eine Sitzung zum Herunterladen der Ereignisse für das aktuelle Datum zu erstellen:

```
bx cf at session create
```
{: codeblock}

Die Sitzung gibt die folgenden Informationen zurück:

* Den Datumsbereich für den Download. Der Standardwert ist das aktuelle Datum in UTC.
* Die Angabe, ob verfügbare Ereignisse für das gesamte Konto oder nur für den aktuellen Bereich einbezogen werden sollen. Standardmäßig werden Ereignisse für den Bereich abgerufen, bei dem Sie angemeldet sind.
* Die zum Herunterladen von Ereignissen erforderliche Sitzungs-ID.
* Die ID des Benutzers, der die Sitzung erstellt.

Beispiel:

```
$ bx cf at session create
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| username     | xxx@yyy.com                               |
| create-time  | 2017-07-25T10:29:28.541092735Z            |
| access-time  | 2017-07-25T10:29:28.541092735Z            |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
| id           | 32c657c5-31c0-4a3c-a139-b380871c737a      |
| space        | 66fe4565-abab-46c9-cdcd-qf4565342345      |
+--------------+-------------------------------------------+
```
{: screen}

**Tipp:** Um die Liste der aktiven Sitzungen anzuzeigen, führen Sie den Befehl [cf at session list](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_list) aus.

Beispiel:

```
bx cf at session list
+--------------------------------------+--------------------------------------+---------------------+--------------------------------+--------------------------------+
| Id                                   | Space                                |Username             | Create-time                    | Access-time                    |
+--------------------------------------+--------------------------------------+---------------------+--------------------------------+--------------------------------+
| 32c657c5-31c0-4a3c-a139-b380871c737a | 66fe4565-abab-46c9-cdcd-qf4565342345 |xxx@yyy.com          | 2017-07-25T10:29:28.541092735Z | 2017-07-25T10:29:28.541092735Z |
+--------------------------------------+--------------------------------------+---------------------+--------------------------------+--------------------------------+
```
{: screen} 


## Schritt 4: Ereignisse in eine Datei herunterladen
{: #step4}

Führen Sie den folgenden Befehl aus, um die in den Sitzungsparametern angegebenen Ereignisse herunterzuladen:

```
bx cf at download -o Events_File_Name Session_ID
```
{: codeblock}

Dabei gilt Folgendes:

* Events_File_Name ist der Name der Ausgabedatei.
* Session_ID ist die GUID der Sitzung. Dieser Wert wurde im vorherigen Schritt abgerufen. Verwenden Sie diesen Wert für das Feld **ID**.

Beispiel:

```
bx cf at download -o Events_File_Name.log 32c657c5-31c0-4a3c-a139-b380871c737a
 29.89 KiB / 12.19 KiB [================================] 245.14% 9.73 MiB/s 0s
Download completed successfully
```
{: screen}

Beim Herunterladen der Ereignisse nimmt der Fortschrittsanzeiger von 0 bis 100 % zu.

**Anmerkung:** 

* Die Daten werden im komprimierten JSON-Format heruntergeladen. Wenn Sie beispielsweise Ereignisse in ein Linux-System herunterladen, dekomprimieren und öffnen Sie die .gz-Datei, um die Daten im JSON-Format anzuzeigen. 
* Das komprimierte JSON-Format kann in ElasticSearch oder Logstash aufgenommen werden. Beispiel: Wenn '-o' nicht angegeben ist und Sie auf einem Linux-System arbeiten, werden die Daten an die Standardausgabe (stdout) übermittelt und können direkt an Ihren Elastic-Stack weitergegeben werden.
* Sie können die Daten auch  mit jedem anderen Programm zum Parsen von JSON-Daten verarbeiten. 

## Schritt 4: Sitzung löschen

Nachdem der Download abgeschlossen ist, müssen Sie die Sitzung mit dem Befehl [cf at session delete](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_delete) löschen. 

Führen Sie den folgenden Befehl aus, um eine Sitzung zu löschen:

```
bx cf at session delete Session_ID
```
{: codeblock}

Dabei ist Session_ID die GUID der Sitzung, die Sie in einem vorherigen Schritt erstellt haben. Verwenden Sie diesen Wert für das Feld **ID**.

Beispiel:

```
bx cf at session delete 32c657c5-31c0-4a3c-a139-b380871c737a
+---------+------------------------+
| Name    | Value                  |
+---------+------------------------+
| message | Delete session success |
+---------+------------------------+
```
{: screen}




