---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, download events

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
{:important: .important}
{:note: .note}


# Ereignisse herunterladen
{: #downloading_events}

Sie können Ereignisse in eine lokale Datei herunterladen. Ereignisse werden im Kontext einer Sitzung heruntergeladen. In einer Sitzung wird angegeben, welche Ereignisse heruntergeladen werden. Nachdem der Download abgeschlossen ist, müssen Sie die Sitzung löschen.
{:shortdesc}

Führen Sie die folgenden Schritte aus, um Ereignisse in eine lokale Datei herunterzuladen:

## Schritt 1: Bei {{site.data.keyword.cloud_notm}} anmelden
{: #prereq}

Melden Sie sich bei {{site.data.keyword.cloud_notm}} an. Führen Sie die folgenden Schritte aus:

1. Melden Sie sich durch Ausführen des Befehls [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) bei {{site.data.keyword.cloud_notm}} an.
2. Führen Sie den Befehl [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) aus, um festzulegen, für welche Organisation und welchen Bereich (Space) der {{site.data.keyword.cloudaccesstrailshort}}-Service bereitgestellt werden soll.

**Hinweis:** Legen Sie die Organisation und den Bereich (Space) fest, in der bzw. dem {{site.data.keyword.cloudaccesstrailshort}} bereitgestellt wird.

## Schritt 2: Ermitteln Sie, welche Ereignisse verfügbar sind.
{: #step2}

Verwenden Sie den Befehl `ibmcloud at status`, um Informationen zu den Ereignissen zu erhalten, die in einer Bereichsdomäne verfügbar sind.

* Um Informationen zu Ereignissen in einer Bereichsdomäne zu erhalten, führen Sie den Befehl `ibmcloud at status` aus.
* Um Informationen zu Ereignissen in der Kontodomäne zu erhalten, führen Sie den Befehl `ibmcloud at status` mit der Option `-a` aus.

Weitere Informationen finden Sie in [Ereignisinformationen anzeigen](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-viewing_event_status#viewing_event_status).
  


## Schritt 3: Eine Sitzung erstellen
{: #step3}

Eine Sitzung ist erforderlich, um den Bereich der Ereignisdaten zu definieren, die für den Download verfügbar sind, und den Downloadstatus beizubehalten. 

Verwenden Sie den Befehl `ibmcloud at session create`, um eine Sitzung zu erstellen. Standardmäßig umfasst eine Sitzung Daten der letzten zwei Wochen.  Optional können Sie beim Erstellen einer Sitzung ein Start- und ein Enddatum festlegen, um einen Zeitbereich anzugeben, eine bestimmte Tageszeit angeben oder den Geltungsbereich der Ereignisse festlegen. 

**Hinweis:** 

* Wenn Sie Start- und Enddatum angeben, bietet die Sitzung Zugriff auf die Ereignisse in diesem (einschließlichen) Datumsbereich. 
* Pro Sitzung können Daten für höchstens 2 Wochen heruntergeladen werden, nicht aber mehr. Daher muss der Zeitbereich weniger als 2 Wochen betragen.
* Sie können Ereignisse für eine Bereichsdomäne oder für die Kontodomäne in einer Region herunterladen.

Um eine Sitzung zu erstellen, mit der Ereignisse für ein bestimmtes Datum heruntergeladen werden, führen Sie den folgenden Befehl aus:

```
ibmcloud at session create -s 2017-07-25 -e 2017-07-25
```
{: codeblock}

Die Sitzung gibt die folgenden Informationen zurück:

* Den Datumsbereich für den Download.
* Die Angabe, ob verfügbare Ereignisse für das gesamte Konto oder nur für den aktuellen Bereich einbezogen werden sollen. Standardmäßig werden Ereignisse für den Bereich abgerufen, bei dem Sie angemeldet sind.
* Die zum Herunterladen von Ereignissen erforderliche Sitzungs-ID.
* Die ID des Benutzers, der die Sitzung erstellt.

Beispiel:

```
$ ibmcloud at session create 
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

**Tipp:** Die Liste der aktiven Sitzungen wird angezeigt, wenn Sie den Befehl `ibmcloud at session list` ausführen.

Beispiel:

```
ibmcloud at session list
+--------------------------------------+--------------------------------------+---------------------+--------------------------------+--------------------------------+
| Id                                   | Space                                |Username             | Create-time                    | Access-time                    |
+--------------------------------------+--------------------------------------+---------------------+--------------------------------+--------------------------------+
| 32c657c5-31c0-4a3c-a139-b380871c737a | 66fe4565-abab-46c9-cdcd-qf4565342345 |xxx@yyy.com          | 2017-07-25T10:29:28.541092735Z | 2017-07-25T10:29:28.541092735Z |
+--------------------------------------+--------------------------------------+---------------------+--------------------------------+--------------------------------+
```
{: screen} 


## Schritt 4: Ereignisse in eine Datei herunterladen
{: #step4}

Führen Sie den folgenden Befehl aus, um die durch die Sitzungsparameter angegebenen Ereignisse herunterzuladen:

```
ibmcloud at download -o Events_File_Name Session_ID
```
{: codeblock}

Dabei gilt Folgendes:

* Events_File_Name ist der Name der Ausgabedatei.
* Session_ID ist die GUID der Sitzung. Dieser Wert wurde im vorherigen Schritt abgerufen. Verwenden Sie diesen Wert für das Feld **ID**.

Beispiel:

```
ibmcloud at download -o Events_File_Name.log 32c657c5-31c0-4a3c-a139-b380871c737a
 29.89 KiB / 12.19 KiB [================================] 245.14% 9.73 MiB/s 0s
Download completed successfully
```
{: screen}

Beim Herunterladen der Ereignisse bewegt sich der Fortschrittsanzeiger von 0 % aufwärts, bis er 100 % erreicht.

**Hinweis:** 

* Die Daten werden im komprimierten JSON-Format heruntergeladen. Wenn Sie beispielsweise Ereignisse in ein Linux-System herunterladen, dekomprimieren und öffnen Sie die .gz-Datei, um die Daten im JSON-Format anzuzeigen. 
* Das komprimierte JSON-Format kann in ElasticSearch oder Logstash aufgenommen werden. Beispiel: Wenn '-o' nicht angegeben ist und Sie auf einem Linux-System arbeiten, werden die Daten an die Standardausgabe (stdout) übermittelt und können direkt an Ihren Elastic-Stack weitergegeben werden.
* Sie können die Daten auch mit jedem anderen Programm zum Parsen von JSON-Daten verarbeiten. 

## Schritt 4: Sitzung löschen

Nachdem der Download abgeschlossen ist, müssen Sie die Sitzung mit dem Befehl `ibmcloud at session delete` löschen. 

Führen Sie den folgenden Befehl aus, um eine Sitzung zu löschen:

```
ibmcloud at session delete Session_ID
```
{: codeblock}

Dabei ist Session_ID die GUID der Sitzung, die Sie in einem vorherigen Schritt erstellt haben. Verwenden Sie diesen Wert für das Feld **ID**.

Beispiel:

```
ibmcloud at session delete 32c657c5-31c0-4a3c-a139-b380871c737a
+---------+------------------------+
| Name    | Value                  |
+---------+------------------------+
| message | Delete session success |
+---------+------------------------+
```
{: screen}




