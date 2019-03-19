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



# Ereignisse mithilfe der Activity Tracker-CLI verwalten
{: #tutorial2}

In diesem Lernprogramm erfahren Sie, wie Sie mit der {{site.data.keyword.cloudaccesstrailshort}}-CLI Ereignisse über die Befehlszeile verwalten können. Hier erhalten Sie Informationen zum Abrufen gespeicherter Ereignisse, zum Herunterladen von Ereignissen, die in der {{site.data.keyword.IBM_notm}} Cloud gespeichert sind und zum Löschen von Ereignissen.
{:shortdesc}

Führen Sie die folgenden Schritte aus:

1. [Stellen Sie die {{site.data.keyword.keymanagementservicelong_notm}} bereit und generieren Sie Ereignisse](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#tutorial2_step1).
2. [Rufen Sie Informationen zu gespeicherten Ereignissen ab (ibmcloud at status)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#tutorial2_step2).
2. [Geben Sie durch Erstellen einer Sitzung an, welche Protokolle heruntergeladen werden (ibmcloud at session create)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#tutorial2_step3).
3. [Rufen Sie die tatsächlichen Protokolldaten ab (ibmcloud at download)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#tutorial2_step4).
4. [Löschen Sie die Sitzung nach Beendigung des Downloads (ibmcloud at session delete)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#tutorial2_step5).
5. [Löschen Sie nicht erforderliche Protokolle manuell (ibmcloud at delete)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#tutorial2_step6).


## Voraussetzungen
{: #tutorial2_assumptions}

1. Sie verfügen über eine {{site.data.keyword.cloud_notm}}-Benutzer-ID mit Entwicklerberechtigungen zum Arbeiten in einem Bereich eines {{site.data.keyword.cloud_notm}}-Kontos, in dem der {{site.data.keyword.cloudaccesstrailshort}}-Service bereitgestellt ist. 

    Weitere Information zum Bereitstellen des {{site.data.keyword.cloudaccesstrailshort}}-Service finden Sie in [{{site.data.keyword.cloudaccesstrailshort}}-Service](/docs/services/cloud-activity-tracker/how-to/provision.html#provision) bereitstellen.

2. Sie haben eine Instanz des {{site.data.keyword.cloudaccesstrailshort}}-Service mit einem Premium-Plan bereitgestellt.

    **Hinweis:** Die {{site.data.keyword.cloudaccesstrailshort}}-CLI ist mit dem Lite-Plan nicht verfügbar.

3. Die {{site.data.keyword.cloudaccesstrailshort}}-CLI ist in Ihrem lokalen System installiert. Dies ist erforderlich, damit Sie die {{site.data.keyword.cloudaccesstrailshort}}-CLI zum Verwalten von Ereignissen über die Befehlszeile verwenden können. 

    Weitere Informationen zum Installieren der Befehlszeilenschnittstelle (CLI) für {{site.data.keyword.cloudaccesstrailshort}} finden Sie in [{{site.data.keyword.cloudaccesstrailshort}}-CLI konfigurieren](/docs/services/cloud-activity-tracker/how-to/config_cli.html#config_cli).

4. Sie haben sich über die Befehlszeile bei {{site.data.keyword.cloud_notm}} angemeldet. In diesem Lernprogramm sollten Sie die folgenden Befehle von einem Terminal ausführen: 

    Befehl `ibmcloud login -a api.ng.bluemix.net` zum Anmelden bei der Region 'Vereinigte Staaten (Süden)'. Weitere Informationen finden Sie in [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login).
    
    Befehl `ibmcloud target -o OrgName -s SpaceName` zum Festlegen der Zielorganisation und des Zielbereichs, in dem der {{site.data.keyword.cloudaccesstrailshort}}-Service bereitgestellt wird. Weitere Informationen finden Sie in [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target).


## Schritt 1: IBM Key Protect-Service bereitstellen und Ereignisse generieren 
{: #tutorial2_step1}
	
Führen Sie die folgenden Schritte aus, um den {{site.data.keyword.keymanagementserviceshort}}-Service in der {{site.data.keyword.cloud_notm}} bereitzustellen und Ereignisse zu generieren:

1. Stellen Sie eine Instanz des {{site.data.keyword.keymanagementserviceshort}}-Service in der Region 'Vereinigte Staaten (Süden)' bereit. Weitere Informationen finden Sie in [Bereitstellung über IBM Cloud-Konsole durchführen](/docs/services/key-protect/provision.html#provision).

2. Definieren Sie die {{site.data.keyword.cloud_notm}}-Berechtigungen für den Benutzer, der künftig mit Schlüsseln arbeiten soll. 

    * Damit ein Benutzer Schlüssel erstellen kann, ist für ihn eine IAM-Richtlinie erforderlich, bei der für die Servicerolle der Wert *Manager* (Manager) oder *Schreibberechtigter* (Writer) festgelegt ist.
	* Damit ein Benutzer Schlüssel löschen kann, ist für ihn eine IAM-Richtlinie erforderlich, bei der für die Servicerolle der Wert *Manager* (Manager) festgelegt ist.
	* Damit ein Benutzer Schlüssel anzeigen kann, ist für ihn eine IAM-Richtlinie erforderlich, bei der für die Servicerolle der Wert *Leseberechtigter* (Reader) festgelegt ist. 

3. Erstellen Sie mit dem {{site.data.keyword.keymanagementserviceshort}}-Service einen Sicherheitsschlüssel, um {{site.data.keyword.cloudaccesstrailshort}}-Ereignisdaten zu generieren. Weitere Informationen finden Sie in [Neue Schlüssel erstellen](/docs/services/key-protect/create-standard-keys.html#create-standard-keys).

{{site.data.keyword.cloudaccesstrailshort}}-Ereignisse werden als Ergebnis der Erstellung eines Schlüssels generiert.

## Schritt 2: Informationen zu den gespeicherten Ereignissen abrufen
{: #tutorial2_step2}

{{site.data.keyword.keymanagementserviceshort}}-Ereignisse sind in der {{site.data.keyword.cloudaccesstrailshort}}-Kontodomäne verfügbar.

In diesem Lernprogramm sind {{site.data.keyword.keymanagementserviceshort}}-Ereignisse in der Kontodomäne 'Vereinigte Staaten (Süden)' verfügbar. Dies ist die Region, in der Sie den {{site.data.keyword.keymanagementserviceshort}}-Service bereitgestellt haben. 

Führen Sie den folgenden Befehl aus, um Informationen zu Ereignissen abzurufen, die an einem bestimmten Datum erfasst wurden:

```
ibmcloud at status -s startDate -e endDate -a
```
{: codeblock}

Dabei gilt Folgendes: 

* `-s` wird zum Festlegen des Startdatums verwendet. 
* `startDate` stellt das Startdatum dar. Das Format ist *JJJJ-MM-TT*.
* `-e` wird zum Festlegen des Enddatums verwendet.
* `endDate` stellt das Enddatum dar. Das Format ist *JJJJ-MM-TT*.
* `-a` wird verwendet, um anzugeben, dass Ereignisse in der Kontodomäne einbezogen werden sollen.

Beispiel:

```
ibmcloud at status -s 2017-07-25 -e 2017-07-25 -a
+------------+-------+-------+------------+
| Date       | Count | Size  | Searchable |
+------------+-------+-------+------------+
| 2017-07-25 | 12    | 34994 | All        |
+------------+-------+-------+------------+
```
{: screen}

Dieser Befehl zählt die Ereignisse für den 25. Juni 2017.  {{site.data.keyword.cloudaccesstrailshort}} ist ein globaler Service, darum sind die Tage in koordinierter Weltzeit (UTC) angegeben. Um die Ereignisse für einen vollständigen Tag der Ortszeit abzurufen, müssen Sie wahrscheinlich die Daten für mehrere UTC-Tage herunterladen.




## Schritt 3: Ereignisse zum Herunterladen angeben
{: #tutorial2_step3}

Erstellen Sie vor dem Herunterladen von Ereignissen eine Sitzung. In der Sitzung wird angegeben, welche Ereignisse heruntergeladen werden.


Verwenden Sie zum Erstellen einer Sitzung den folgenden Befehl:

```
ibmcloud at session create -s startDate -e endDate -a
```
{: codeblock}

Dabei gilt Folgendes: 

* `-s` wird zum Festlegen des Startdatums verwendet. 
* `startDate` stellt das Startdatum dar. Das Format ist *JJJJ-MM-TT*.
* `-e` wird zum Festlegen des Enddatums verwendet.
* `endDate` stellt das Enddatum dar. Das Format ist *JJJJ-MM-TT*.
* `-a` wird verwendet, um anzugeben, dass Ereignisse in der Kontodomäne einbezogen werden sollen.

Beispiel:

```
ibmcloud at session create -s 2017-07-25 -e 2017-07-25 -a
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
{: screen}

Dabei gilt Folgendes: 

* `-s` wird zum Festlegen des Startdatums verwendet.
* `-e` wird zum Festlegen des Enddatums verwendet.
* `-a` wird verwendet, um anzugeben, dass Ereignisse in der Kontodomäne einbezogen werden sollen.

Einer Sitzung ist ein Startdatum und ein Enddatum zugeordnet. Der Download-Befehl bezieht die Ereignisse zwischen diesen einschließlichen Datumsangaben ein.

Der wichtige Teil der Befehlsausgabe ist die `ID` der Sitzung. Sie wird im Download-Befehl referenziert.

Um Informationen zu bestehenden Sitzungen abzurufen, geben Sie `ibmcloud at session list` ein.

Weitere Informationen zu Sitzungen und zum Befehl `ibmcloud at session create` finden Sie in der [CLI-Referenz](/docs/services/cloud-activity-tracker/reference/at_cli_cloud.html#session_create).

Verwenden Sie den Befehl `ibmcloud at session help create`, um Hilfeinformationen über die Befehlszeile abzurufen.

## Schritt 4: Laden Sie die Ereignisse herunter, die für den Bereich erkannt werden, der für die Sitzung definiert ist
{: #tutorial2_step4}

Führen Sie den folgenden Befehl aus, um die durch die Sitzungsparameter angegebenen Ereignisse herunterzuladen:

```
ibmcloud at events download -o outputFile sessionID
```
{: codeblock}

* Der Parameter `-o` gibt eine Ausgabedatei an.
* `outputFile` ist der Name der lokalen Datei.
* Die `sessionID` wird zuletzt angegeben. Den Wert für die Sitzungs-ID können Sie der Ausgabe des Befehls `ibmcloud at session create` entnehmen.

Die Daten werden im komprimierten JSON-Format heruntergeladen. 

Beispiel:

```
$ ibmcloud at events download -o events.log 21b19aeb-3d32-4c60-b912-517609c62db2
 6.70 KiB / 3.06 KiB [================================================================================================================================================================] 219.03% 8.60 MiB/s 0s
Download Successful
```
{: screen} 

Beim Herunterladen der Ereignisse bewegt sich der Fortschrittsanzeiger von 0 % aufwärts, bis er 100 % erreicht.

Weitere Informationen zum Befehl `ibmcloud at download` finden Sie in der [CLI-Referenz](/docs/services/cloud-activity-tracker/reference/at_cli_cloud.html#download).

Verwenden Sie den Befehl `ibmcloud at help download`, um Hilfeinformationen über die Befehlszeile abzurufen.

## Schritt 5: Sitzung löschen
{: #tutorial2_step5}

Wenn der Download abgeschlossen ist, löschen Sie die Sitzung. Führen Sie dazu den folgenden Befehl aus:

```
ibmcloud at session delete sessionID
```
{: codeblock}

Dabei gilt Folgendes: 

* `sessionID` ist die ID der Sitzung, die Sie löschen möchten.

Die Anzahl der Sitzungen ist begrenzt. Sitzungen werden nicht automatisch gelöscht. Sie müssen Sitzungen, die nicht erforderlich sind, manuell löschen. 

Beispiel: 

```
$ ibmcloud at session delete 21b19aeb-3d32-4c60-b912-517609c62db2
+---------+------------------------+
| name    | value                  |
+---------+------------------------+
| message | Delete session success |
+---------+------------------------+
```
{: screen}

Weitere Informationen zum Befehl `ibmcloud at session delete` finden Sie in der [CLI-Referenz](/docs/services/cloud-activity-tracker/reference/at_cli_cloud.html#session_delete).

Verwenden Sie den Befehl `ibmcloud at session help delete`, um Hilfeinformationen über die Befehlszeile abzurufen.

## Schritt 6: Ereignisse in Activity Tracker automatisch löschen
{: #tutorial2_step6}

Sie können die Aufbewahrungsdauer für Îhre Ereignisse in {{site.data.keyword.cloudaccesstrailshort}} steuern. Sie können Ereignisse manuell löschen oder das automatische Löschen von Ereignissen konfigurieren.

Um Ereignisse automatisch aus einem Bereich (Space) zu löschen, führen Sie den Befehl `ibmcloud at delete` aus. Beispiel:

```
$ ibmcloud at delete -s 2017-07-25 -e 2017-07-25
Deleted successfully
"6 logs were deleted,freeing 13737 bytes."
```
{: screen}

Weitere Informationen zum Befehl `ibmcloud at delete` finden Sie in der [CLI-Referenz](/docs/services/cloud-activity-tracker/reference/at_cli_cloud.html#delete).

Verwenden Sie den Befehl `ibmcloud at help delete`, um Hilfeinformationen über die Befehlszeile abzurufen.

**Anmerkung:** Um Ereignisse automatisch zu löschen, können Sie mit dem CLI-Befehl `ibmcloud at option` eine Aufbewahrungsrichtlinie festlegen. Weitere Informationen finden Sie in der [CLI-Referenz](/docs/services/cloud-activity-tracker/reference/at_cli_cloud.html#option).


