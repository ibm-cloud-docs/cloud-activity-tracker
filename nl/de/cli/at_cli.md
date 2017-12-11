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

# IBM Cloud Activity Tracker-CLI
{: #at_cli}

Die {{site.data.keyword.cloudaccesstraillong}}-CLI (Command Line Interface, Befehlszeilenschnittstelle) ist ein CF-Plug-in, das Sie zum Verwalten von {{site.data.keyword.cloudaccesstrailshort}}-Ereignissen verwenden können.
{: shortdesc}

**Voraussetzungen**
* Melden Sie sich vor dem Ausführen von Befehlen bei {{site.data.keyword.Bluemix}} mit dem Befehl `cf login` an, um ein {{site.data.keyword.Bluemix_short}}-Zugriffstoken
zu erstellen und Ihre Sitzung zu authentifizieren.

Informationen zur Verwendung der {{site.data.keyword.cloudaccesstrailshort}}-CLI finden Sie in [{{site.data.keyword.cloudaccesstrailshort}}-Ereignisse mit der CLI verwalten](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#managing_events). 

Das CLI-Plug-in von {{site.data.keyword.cloudaccesstraillong}} unterstützt Linux-, Mac- und Windows-Plattformen.

<table>
  <caption>Befehle zur Verwaltung von {{site.data.keyword.cloudaccesstrailshort}}</caption>
  <tr>
    <th>Befehl</th>
    <th>Verwendungszweck</th>
  </tr>
  <tr>
    <td>[cf at](#base)</td>
    <td>Mit diesem Befehl können Sie Informationen zur CLI abrufen (z. B. die Version oder die Liste der Befehle).</td>
  </tr>
  <tr>
    <td>[cf at delete](#delete)</td>
    <td>Mit diesem Befehl können Sie {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse löschen.</td>
  </tr>
  <tr>
    <td>[cf at download](#download)</td>
    <td>Mit diesem Befehl können Sie {{site.data.keyword.cloudaccesstrailshort}}-Protokolle in eine lokale Datei herunterladen. </td>
  </tr>
  <tr>
    <td>[cf at help](#help)</td>
    <td>Mit diesem Befehl können Sie Hilfeinformationen zur Verwendung der CLI und eine Liste aller zugehörigen Befehle abrufen.</td>
  </tr>
  <tr>
    <td>[cf at option](#option)</td>
    <td>Mit diesem Befehl können Sie {{site.data.keyword.cloudaccesstrailshort}}-Ereignisoptionen anzeigen oder ändern (z. B. die Aufbewahrungsdauer), die in einem {{site.data.keyword.Bluemix_notm}}-Bereich oder -Konto verfügbar sind.</td>
  </tr>
  <tr>
    <td>[cf at session create](#session_create)</td>
    <td>Mit diesem Befehl können Sie eine neue Sitzung erstellen.</td>
  </tr>
  <tr>
    <td>[cf at session delete](#session_delete)</td>
    <td>Mit diesem Befehl können Sie eine Sitzung löschen.</td>
  </tr>  
  <tr>
    <td>[cf at session list](#session_list)</td>
    <td>Mit diesem Befehl können Sie aktive Sitzungen und die zugehörigen IDs auflisten.</td>
  </tr>  
  <tr>
    <td>[cf at session show](#session_show)</td>
    <td>Mit diesem Befehl können Sie den Status einer einzelnen Sitzung anzeigen.</td>
  </tr>   
  <tr>
    <td>[cf at status](#status)</td>
    <td>Mit diesem Befehl können Sie Informationen zum Status der Ereignisse anzeigen, die Stores in {{site.data.keyword.cloudaccesstrailshort}} sind.</td>
  </tr>
  <tr>
    <td>[cf at trail](#trail)</td>
    <td>Mit diesem Befehl können Sie Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden.</td>
  </tr>
  </table>


## cf at
{: #base}

Stellt Informationen zur CLI-Version und zur Verwendung der CLI bereit.

```
cf at [parameter]
```
{: codeblock}

**Parameter**

<dl>
<dt>--help, -h</dt>
<dd>Geben Sie diesen Parameter an, um die Liste der Befehle anzuzeigen oder Hilfeinformationen zu einem Befehl abzurufen.
</dd>

<dt>--version, -v</dt>
<dd>Geben Sie diesen Parameter an, um die Version der CLI auszugeben.</dd>
</dl>

**Beispiele**

Führen Sie den folgenden Befehl aus, um die Liste der Befehl abzurufen:

```
cf at --help
```
{: codeblock}

Führen Sie den folgenden Befehl aus, um die Version der CLI abzurufen:

```
cf at --version
```
{: codeblock}


## cf at delete
{: #delete}

Löscht {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse.

```
cf at delete [parameter] [argumente..]
```
{: codeblock}

**Parameter**

<dl>
  <dt>--start wert, -s wert</dt>
  <dd>(Optional) Legt das Startdatum in koordinierter Weltzeit (Universal Coordinated Time, UTC) fest: *JJJJ-MM-TT* (z. B. `2017-01-02`). <br>Der Standardwert ist vor zwei Wochen.
  </dd>
  
  <dt>--end wert, -e wert</dt>
  <dd>(Optional) Legt das Enddatum in koordinierter Weltzeit (Universal Coordinated Time, UTC) fest: *JJJJ-MM-TT*. <br>Das UTC-Datumsformat ist **JJJJ-MM-TT** (z. B. `2017-01-02`). <br>Der Standardwert ist das aktuelle Datum.</dd>
  
</dl>

**Beispiel**

Führen Sie den folgenden Befehl aus, um die Ereignisse für den 22. Juni 2017 zu löschen:
```
cf at delete -s 2017-06-22 -e 2017-06-22
```
{: codeblock}

Sie erhalten ähnliche Informationen wie in der folgenden Ausgabe:

`Deleted successfully`
`"6 logs were deleted, freeing 13737 bytes."`


## cf at download
{: #download}

Lädt {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse in eine lokale Datei herunter oder überträgt sie als Datenstrom an ein Terminalfenster in Windows und Mac OS X bzw. an stdout in einem Linux-Terminal. 

**Hinweis:** Zum Herunterladen von Dateien müssen Sie zunächst eine Sitzung erstellen. Eine Sitzung definiert auf der Basis eines Datumsbereichs, welche Ereignisse heruntergeladen werden sollen. Ereignisse werden im Kontext einer Sitzung heruntergeladen. Weitere Informationen finden Sie in [cf at session create](/docs/services/CloudActivityTracker/reference/at_cli.html#session_create).

```
cf at download [parameter] [argumente...]
```
{: codeblock}

**Parameter**

<dl>
<dt>--output wert, -o wert</dt>
<dd>(Optional) Legt den Pfad und den Dateinamen für die lokale Ausgabedatei fest, in die die Ereignisse heruntergeladen werden.<br>Der Standardwert ist ein Bindestrich (-). <br>Legen Sie für diesen Parameter den Standardwert fest, um Protokolle in die Standardausgabe auszugeben.</dd>
</dl>

**Argumente**

<dl>
<dt>Sitzungs-ID</dt>
<dd>Legen Sie den Wert für die Sitzungs-ID fest, die beim Ausführen des Befehls `cf at session create` abgerufen wird. Dieser Wert gibt an, welche Sitzung zum Herunterladen von Ereignissen verwendet wird.<br>**Hinweis:** Der Befehl `cf at session create` enthält die Parameter, die steuern, welche Ereignisse heruntergeladen werden. </dd>
</dl>

**Hinweis:** Um nach Abschluss des Downloads dieselben Daten erneut herunterzuladen, müssen Sie eine andere Datei oder eine andere Sitzung verwenden.

**Beispiel**

Um Ereignisse in eine Datei mit dem Namen `events.log` herunterzuladen, führen Sie den folgenden Befehl aus:

```
cf at download -o events.log 1db6ce16-824d-4d50-bd40-37f1d8fea9b7
```
{: screen}

Sie erhalten ähnliche Informationen wie in der folgenden Ausgabe: 

```
6.70 KiB / 3.06 KiB [========] 219.03% 8.60 MiB/s 0s
Download completed successfully
```
{: screen}


## cf at help
{: #help}

Stellt Informationen zur Verwendung eines Befehls bereit.

```
cf at help [parameter]
```
{: codeblock}

**Parameter**

<dl>
<dt>Befehl</dt>
<dd>Geben Sie den Namen des Befehls an, für den Sie Hilfe anfordern möchten.
</dd>
</dl>


**Beispiel**

Führen Sie den folgenden Befehl aus, um Hilfe zum Ausführen des Befehls zum Anzeigen des Status von {{site.data.keyword.cloudaccesstrailshort}} aufzurufen:

```
cf at help status
```
{: codeblock}


## cf at option
{: #option}

Ermöglicht das Anzeigen oder Ändern des Aufbewahrungszeitraums für Ereignisse, die in einem {{site.data.keyword.Bluemix_notm}}-Bereich verfügbar sind. Wenn Sie eine Aufbewahrungsrichtlinie festlegen, werden Ereignisse automatisch gelöscht, wenn die Anzahl der für den Aufbewahrungszeitraum angegebenen Tage erreicht ist.

* Der Zeitraum wird durch die Anzahl der Tage festgelegt.
* Der Standardwert ist **-1**, d. h. Ereignisse werden gespeichert und nicht gelöscht.

**Anmerkung:** Standardmäßig werden alle Ereignisse gespeichert. Wenn Sie keinen Aufbewahrungszeitraum festlegen, müssen Sie die Ereignisse mit dem Befehl `cf at delete` manuell löschen. 

```
cf at option [parameter] [argumente...]
```
{: codeblock}

**Parameter**

<dl>
<dt>--retention wert, -r wert</dt>
<dd>(Optional) Legt die Anzahl der Tage für den Aufbewahrungszeitraum fest. <br> Der Standardwert ist *-1* Tage.</dd>

</dl>

**Beispiel**

Um den aktuellen Aufbewahrungszeitraum für den Bereich anzuzeigen, bei dem Sie angemeldet sind, führen Sie den folgenden Befehl aus:

```
cf at option
```
{: codeblock}

Sie erhalten eine Ausgabe ähnlich der folgenden:

```
+--------------------------------------+-----------+
|               SPACEID                | RETENTION |
+--------------------------------------+-----------+
| 2af890ce-fb4f-4e41-a975-901a56ed1f11 |        30 |
+--------------------------------------+-----------+
```
{: screen}


Um den Aufbewahrungszeitraum für den Bereich, bei dem Sie angemeldet sind, in 25 Tage zu ändern, führen Sie den folgenden Befehl aus:

```
cf at option -r 25
```
{: codeblock}

Sie erhalten eine Ausgabe ähnlich der folgenden:

```
+--------------------------------------+-----------+
|               SPACEID                | RETENTION |
+--------------------------------------+-----------+
| 2af890ce-fb4f-4e41-a975-901a56ed1f11 |        25 |
+--------------------------------------+-----------+
```
{: screen}



## cf at session create
{: #session_create}

Erstellt eine neue Sitzung.

**Anmerkung:** In einem Bereich können bis zu 30 Sitzungen gleichzeitig ausgeführt werden. Die Sitzung wird für einen Benutzer erstellt. Sitzungen können von Benutzern in einem Bereich nicht gemeinsam genutzt werden.

```
cf at session create [parameter] [argumente...]
```
{: codeblock}

**Parameter**

<dl>
  <dt>--start wert, -s wert</dt>
  <dd>(Optional) Legt das Startdatum in koordinierter Weltzeit (Universal Coordinated Time, UTC) fest: *JJJJ-MM-TT* (z. B. `2017-01-02`). <br>Der Standardwert ist vor zwei Wochen.
  </dd>
  
  <dt>--end wert, -e wert</dt>
  <dd>(Optional)  Legt das Enddatum in koordinierter Weltzeit (Universal Coordinated Time, UTC) fest: *JJJJ-MM-TT* (z. B. `2017-01-02`). <br>Der Standardwert ist das aktuelle Datum.</dd>
 </dl>

**Zurückgegebene Werte**

<dl>
<dt>Access-Time (Zugriffszeit)</dt>
<dd>Diese Zeitmarke gibt an, wann die Sitzung zuletzt verwendet wurde.</dd>

<dt>Create-Time (Erstellungszeit)</dt>
<dd>Diese Zeitmarke gibt den Zeitpunkt (Datum und Uhrzeit) an, an dem die Sitzung erstellt wurde.</dd>

<dt>Date-Range (Datumsbereich)</dt>
<dd>Gibt den Zeitraum (die Tage) an, der zum Filtern der Ereignisse verwendet wird. Ereignisse, die aus diesem Datumsbereich stammen, können im Rahmen der Sitzung verwaltet werden.</dd>

<dt>ID</dt>
<dd>Die Sitzungs-ID.</dd>

<dt>Space (Bereich)</dt>
<dd>Die ID des Bereichs, in dem die Sitzung aktiv ist.</dd>

<dt>Type-Account (Kontotyp)</dt>
<dd>Für diesen Wert wird **ActivityTracker** festgelegt.</dd>

<dt>Username (Benutzername)</dt>
<dd>Die {{site.data.keyword.IBM_notm}} ID des Benutzers, der die Sitzung erstellt hat.</dd>
</dl>


**Beispiel**

Um eine Sitzung für den 10. Juli 2017 zu erstellen, führen Sie den folgenden Befehl aus:

```
cf at session create -s 2017-07-10 -e 2017-07-10
```
{: screen}

Sie erhalten eine Ausgabe ähnlich der folgenden:

```
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| id           | 9b8c4db8-5841-4993-a449-305815a53a8e      |
| space        | xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx      |
| username     | xxx@yyy.com                               |
| create-time  | 2017-07-25T11:54:00.20042645Z             |
| access-time  | 2017-07-25T11:54:00.20042645Z             |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
+--------------+-------------------------------------------+
```
{: screen}



## cf at session delete
{: #session_delete}

Löscht die durch eine Sitzungs-ID angegebene Sitzung.

```
cf at session delete [argumente...]
```
{: codeblock}


**Argumente**

<dl>
<dt>Sitzungs-ID</dt>
<dd>Die ID der Sitzung, die Sie löschen möchten. <br>Mit dem Befehl `cf at session list` können Sie alle aktiven Sitzungs-IDs abrufen.</dd>
</dl>

**Beispiel**

Um eine Sitzung mit der Sitzungs-ID *9b8c4db8-5841-4993-a449-305815a53a8e* zu löschen, führen Sie den folgenden Befehl aus:

```
cf at session delete 9b8c4db8-5841-4993-a449-305815a53a8e
```
{: screen}

Sie erhalten eine Ausgabe ähnlich der folgenden:

```
+---------------+--------------------------+
|    NAME       |     VALUE                |
+---------------+--------------------------+
|  message      | Delete session success   |
+---------------+--------------------------+
```
{: screen}


## cf at session list
{: #session_list}

Listet die aktiven Sitzungen mit den zugehörigen IDs auf.

```
cf at session list
```
{: codeblock}

**Zurückgegebene Werte**

<dl>
<dt>ID</dt>
<dd>Die Sitzungs-ID.</dd>

<dt>SPACE (Bereich)</dt>
<dd>Die ID des Bereichs, in dem die Sitzung aktiv ist.</dd>

<dt>USERNAME (Benutzername)</dt>
<dd>Die {{site.data.keyword.IBM_notm}} ID des Benutzers, der die Sitzung erstellt hat.</dd>

<dt>CREATE-TIME (Erstellungszeit)</dt>
<dd>Diese Zeitmarke gibt den Zeitpunkt (Datum und Uhrzeit) an, an dem die Sitzung erstellt wurde.</dd>

<dt>ACCESS-TIME (Zugriffszeit)</dt>
<dd>Diese Zeitmarke gibt an, wann die Sitzung zuletzt verwendet wurde.</dd>
</dl>
 
**Beispiel**

Führen Sie den folgenden Befehl aus, um die Sitzungen aufzulisten:

```
cf at session list
```
{: screen}

Sie erhalten eine Ausgabe ähnlich der folgenden:

```
+--------------------------------------+--------------------------------------+-----------------------------------+--------------------------------+--------------------------------+
| ID                                   | SPACE                                | USERNAME                          | CREATE-TIME                    | ACCESS-TIME                    |
+--------------------------------------+--------------------------------------+-----------------------------------+--------------------------------+--------------------------------+
| fa3f1970-21f3-4e32-b480-1ffb41badc16 | 12345678-fb4f-acdf-a975-11335678r3fg | xxx@yyy.com                       | 2017-07-10T09:04:07.916788069Z | 2017-07-10T09:04:07.916788069Z |
| 9b8c4db8-5841-4993-a449-305815a53a8e | 12345678-fb4f-acdf-a975-11335678r3fg | xxx@yyy.com                       | 2017-07-11T09:19:14.666532796Z | 2017-07-12T09:19:14.666532796Z |
+--------------------------------------+--------------------------------------+-----------------------------------+--------------------------------+--------------------------------+
```
{: screen}


## cf at session show
{: #session_show}

Zeigt den Status einer einzelnen Sitzung an.

```
cf at session show [argumente...]
```
{: codeblock}

**Argumente**

<dl>
<dt>Sitzungs-ID</dt>
<dd>Die ID der aktiven Sitzung, zu der Sie Informationen abrufen möchten.</dd>
</dl>

**Zurückgegebene Werte**

<dl>
<dt>Access-Time (Zugriffszeit)</dt>
<dd>Diese Zeitmarke gibt an, wann die Sitzung zuletzt verwendet wurde.</dd>

<dt>Create-Time (Erstellungszeit)</dt>
<dd>Diese Zeitmarke gibt den Zeitpunkt (Datum und Uhrzeit) an, an dem die Sitzung erstellt wurde.</dd>

<dt>Date-Range (Datumsbereich)</dt>
<dd>Gibt den Zeitraum (die Tage) an, der zum Filtern der Ereignisse verwendet wird. Ereignisse, die aus diesem Datumsbereich stammen, können im Rahmen der Sitzung verwaltet werden.</dd>

<dt>id</dt>
<dd>Die Sitzungs-ID.</dd>

<dt>Space (Bereich)</dt>
<dd>Die ID des Bereichs, in dem die Sitzung aktiv ist.</dd>

<dt>Type-Account (Kontotyp)</dt>
<dd>Für diesen Wert wird **ActivityTracker** festgelegt.</dd>

<dt>Username (Benutzername)</dt>
<dd>Die {{site.data.keyword.IBM_notm}} ID des Benutzers, der die Sitzung erstellt hat.</dd>
</dl>

**Beispiel**

Um die Details der Sitzung mit der Sitzungs-ID *9b8c4db8-5841-4993-a449-305815a53a8e* anzuzeigen, führen Sie den folgenden Befehl aus:

```
cf at session show 9b8c4db8-5841-4993-a449-305815a53a8e
```
{: screen}

Sie erhalten eine Ausgabe ähnlich der folgenden:

```
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| create-time  | 2017-07-25T11:54:00.20042645Z             |
| access-time  | 2017-07-25T11:54:00.20042645Z             |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
| id           | 9b8c4db8-5841-4993-a449-305815a53a8e      |
| space        | xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx      |
| username     | xxx@yyy.com                               |
+--------------+-------------------------------------------+
```
{: screen}


## cf at status
{: #status}

Gibt Informationen zum Status von {{site.data.keyword.cloudaccesstrailshort}}-Ereignissen zurück.

```
cf at status [parameter] [argumente...]
```
{: codeblock}

**Parameter**

<dl>
  <dt>--start wert, -s wert</dt>
  <dd>(Optional) Legt das Startdatum in koordinierter Weltzeit (Universal Coordinated Time, UTC) fest: *JJJJ-MM-TT* (z. B. `2017-01-02`). <br>Der Standardwert ist vor zwei Wochen.
  </dd>
  
  <dt>--end wert, -e wert</dt>
  <dd>(Optional)  Legt das Enddatum in koordinierter Weltzeit (Universal Coordinated Time, UTC) fest: *JJJJ-MM-TT* (z. B. `2017-01-02`). <br>Der Standardwert ist das aktuelle Datum.</dd>
  
  <dt>--at-account-level, -a </dt>
  <dd>(Optional) Gibt die Kontoebene als Geltungsbereich an. <br> **Anmerkung:** Legen Sie diesen Wert fest, um Kontoinformationen abzurufen.<br>Wenn dieser Parameter nicht angegeben ist, wird standardmäßig der aktuelle Bereich festgelegt (der Bereich, bei dem Sie sich mit dem Befehl `cf login` angemeldet haben).
  </dd>
  
</dl>


**Anmerkung:** Der Befehl `cf at status` meldet nur die Ereignisse für die beiden letzten Wochen, die in {{site.data.keyword.cloudaccesstrailshort}} gespeichert sind, wenn kein Start- und kein Enddatum angegeben ist. 

**Zurückgegebene Werte**   

<dl>
  <dt>DATE (Datum)</dt>
  <dd>Das Datum in koordinierter Weltzeit (Universal Coordinated Time, UTC): *JJJJ-MM-TT* (z. B. `2017-01-02`).
  </dd>
  
  <dt>COUNT (Anzahl)</dt>
  <dd>Die Gesamtzahl der Ereignisse.
  </dd>
  
  <dt>SIZE (Größe)</dt>
  <dd>Die Gesamtgröße der Ereignisse in Megabyte.
  </dd>

  <dt>TYPES (Typen)</dt>
  <dd>Für diesen Wert wird **ActivityTracker** festgelegt.
  </dd>
  
  <dt>SEARCHABLE (Durchsuchbar)</dt>
  <dd>Dieses Feld gibt an, ob die Ereignisse für die Suche in Kibana verfügbar sind. <br>Wenn der Wert für das Feld **SEARCHABLE** auf *None* gesetzt ist, dann sind zwar Ereignisse zum Herunterladen verfügbar, aber Sie können diese Ereignisse nicht in Kibana analysieren.
  </dd>
  
</dl>

**Beispiel**

Führen Sie den folgenden Befehl aus, um Details der Ereignisse am 20. Juli 2017 anzuzeigen:

```
cf at status -s 2017-07-20 -e 2017-07-20
```
{: codeblock}


Sie erhalten ähnliche Informationen wie in der folgenden Ausgabe:

```
+------------+-----------+-------+------------------+--------------+
|   Date     |  Count    | Size  | Types            |  Searchable  |
+------------+-----------+-------+------------------+--------------+
| 2017-07-20 |    1      | 2531  | ActivityTracker  | All          |
+------------+-----------+-------+------------------+--------------+
```
{: screen}



## cf at trail
{: #trail}

Serialisierte Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} senden.

```
cf at trail [parameter] [argumente...]
```
{: codeblock}

**Parameter**

<dl>
  <dt>--file FILE, -f FILE</dt>
  <dd>(Optional) Geben Sie die Ereignisdatei im folgenden Format an: `PFAD/dateiname`.
  </dd>
  
  <dt>--type FORMAT, -t FORMAT</dt>
  <dd>(Optional) Geben Sie das Format der Ereignisse an, die in der Datei enthalten sind. Gültige Werte sind *cadf* und *kong*. <br> Verwenden Sie *CADF*, um Ereignisse zu senden, die mit dem CADF-Format übereinstimmen. Verwenden Sie *KONG*, um Ereignisse zu senden, die mit dem Kong-Format übereinstimmen. <br> **Anmerkung:** In einer Datei können nur Ereignisse mit demselben Format gesendet werden.</dd>
 </dl>
 
**Beispiel**

Führen Sie den folgenden Befehl aus, um serialisierte CADF-Ereignisse an {{site.data.keyword.cloudaccesstrailshort}} zu senden:

```
cf at trail -t cadf -f events.log
```
{: codeblock}

Dabei ist *events.log* die Datei mit den Ereignissen, die Sie an {{site.data.keyword.cloudaccesstrailshort}} senden möchten. Diese Datei enthält Ereignisse, die mit dem CADF-Format übereinstimmen.

Sie erhalten ähnliche Informationen wie in der folgenden Ausgabe:

```
+--------------------------------------+---------------------------+
|            ID                        |          Value            |
+--------------------------------------+---------------------------+
| bbb170dc-2b0a-42d4-b560-b416f3308869 | B0UtwP1FhemsZIr4rTJVKA==  |
+--------------------------------------+---------------------------+
| 688f1194-2305-4367-8ece-f468e67c19fb | KLCG9f++usNolgvutRCR1Q==  |
+--------------------------------------+---------------------------+
```
{: screen}
