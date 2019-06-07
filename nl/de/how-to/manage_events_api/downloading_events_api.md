---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, download events, API

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
{:deprecated: .deprecated}

# Ereignisse herunterladen
{: #downloading_events_api}

Sie können {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse mithilfe der API herunterladen.
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} wird nicht mehr verwendet. Ab 09. Mai 2019 können keine neuen {{site.data.keyword.cloudaccesstrailshort}}-Instanzen mehr bereitgestellt werden. Vorhandene Instanzen des Premium-Plans werden bis 30. September 2019 unterstützt. Wenn Sie die Aktivitäten Ihres {{site.data.keyword.cloud_notm}}-Kontos weiterhin verfolgen möchten, stellen Sie eine Instanz von [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) bereit.
{: deprecated}

Berücksichtigen Sie die folgenden Informationen:

* Sie müssen über die Rolle **Entwickler** in dem Bereich verfügen, in dem der {{site.data.keyword.cloudaccesstrailshort}}-Service bereitgestellt wird.
* Es können maximal 15 Tage pro Sitzung heruntergeladen werden.
* Zum Herunterladen von Kontoprotokollen müssen Sie für den Parameter **AtAccountLevel** den Wert *true* festlegen und den Download innerhalb des Kontexts des Bereichs anfordern, in dem der {{site.data.keyword.cloudaccesstrailshort}}-Service bereitgestellt wird.

Zum Herunterladen von Ereignissen müssen Sie die folgenden Schritte ausführen:

1. Rufen Sie ein UAA-Token ab.
2. Erstellen Sie eine Sitzung, in der Sie die Bedingungen angeben, mit denen die Untergruppe der Ereignisse definiert wird, die Sie herunterladen wollen.
3. Laden Sie die Ereignisse in eine lokale Datei herunter.
4. Löschen Sie die Sitzung.



## Ereignisse mithilfe von cURL herunterladen
{: #downloading_events_api_curl}

Führen Sie die folgenden Schritte aus, um Ereignisse in eine lokale Datei herunterzuladen:

1. Rufen Sie ein UAA-Token ab.

    Weitere Informationen finden Sie in [UAA-Token abrufen](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-auth_uaa#auth_uaa).

2. Erstellen Sie eine Sitzung, in der Sie die Bedingungen angeben, mit denen die Untergruppe der Ereignisse definiert wird, die Sie herunterladen wollen.

    ```
    curl -X POST -H "Content-Type: application/json" -H "X-Auth-Token: bearer $token" -H "X-Auth-Project-Id: $spaceID" ENDPOINT/v3/sessions -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":true,"SearchTime":""}'
    ```
    {: codeblock}

    Dabei gilt Folgendes:
    
    *token* stellt den Wert des UAA-Tokens dar, das Sie in einem früheren Schritt abgerufen haben.

    *spaceID* stellt die UUID des Cloud Foundry-Bereichs dar, in dem {{site.data.keyword.cloudaccesstrailshort}} bereitgestellt wird.

    *ENDPOINT* stellt den Eingangspunkt zum Service dar. Jede Region hat eine andere URL. Informationen dazu, wie Sie die Liste der Endpunkte für die jeweilige Region abrufen, finden Sie in [Endpunkte](/docs/services/cloud-activity-tracker/reference/ref_endpoints.html#api_endpoints).

    *start* und *end* stellen einen Zeitbereich dar, für den Sie Ereignisse herunterladen möchten. Das Datumsformat ist *JJJJ-MM-TT*. 

    *AtAccountLevel* gibt an, ob sich die Ereignisse, die heruntergeladen werden sollen, in der Kontodomäne oder in einer Bereichsdomäne befinden.
    
    *SearchTime* gibt die Tageszeit an, für die Sie Ereignisse herunterladen wollen.

    Wenn Sie eine Sitzung zum Herunterladen von Ereignissen von einer Bereichsdomäne in der Region 'Süden' der Vereinigten Staaten ('us-south') erstellen wollen, legen Sie für den Parameter **AtAccountLevel** den Wert *false* fest:

    ```
    curl -X POST -H "Content-Type: application/json" -H "X-Auth-Token: bearer $token" -H "X-Auth-Project-Id: $spaceID" https://activity-tracker.ng.bluemix.net/v3/sessions -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":false,"SearchTime":""}'
    ```
    {: codeblock}

    Das Ausgabefeld **id** gibt die Sitzungs-ID zurück.
    
    Die Ausgabe sieht zum Beispiel wie folgt aus:

    ```
    {"id":"b08cb740-ff85-404f-a6eb-ffec5374c7c6","space":"c1234567-6d55-4193-a9de-378620d6fab5","username":"xxx@ibm.com","create-time":"2018-06-28T12:50:36.012383445Z","access-time":"2018-06-28T12:50:36.012383445Z","date-range":{"Start":"2018-06-27","End":"2018-06-27"},"types":{"Type":"ActivityTracker","AtAccountLevel":true},"search-time":""}
    ```
    {: screen}
    
    Wenn Sie zum Beispiel eine Sitzung zum Herunterladen von Ereignissen für ein Konto von der Kontodomäne in der Region 'Süden' der Vereinigten Staaten ('us-south') herunterladen wollen, legen Sie für den Parameter **AtAccountLevel** den Wert *true* fest:

    ```
    curl -X POST -H "Content-Type: application/json" -H "X-Auth-Token: bearer $token" -H "X-Auth-Project-Id: $spaceID" https://activity-tracker.ng.bluemix.net/v3/sessions -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":true,"SearchTime":""}'
    ```
    {: codeblock}

3. Laden Sie die Ereignisse in eine lokale Datei herunter.

    ```
    curl -H "x-auth-token: bearer $token" -H "SESSIONID: $sessionID" -H "X-Auth-Project-Id: $spaceID" -H "accept: application/json" ENDPOINT/v3/events/download > FILENAME.gz
    ```
    {: codeblock}

    Dabei ist *FILENAME* der Name der lokalen Datei, in die Ereignisse heruntergeladen werden.

    Beispiel:

    ```
    curl -H "x-auth-token: bearer $token" -H "SESSIONID: $sessionID" -H "X-Auth-Project-Id: $spaceID" -H "accept: application/json" https://activity-tracker.ng.bluemix.net/v3/events/download > spaceXevents.gz
    ```
    {: codeblock}

4. Löschen Sie die Sitzung.

    ```
    curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer $token" -H "Accept:application/json" -H "X-Auth-Project-Id:$spaceId" --request DELETE https://activity-tracker.ng.bluemix.net/v3/sessions/$sessionId

    ```
    {: codeblock}


## NodeJS-Beispiel für das Herunterladen von Ereignissen
{: #downloading_events_api_node}

Mit dem nachfolgenden Beispielcode können Sie testen, wie Sie Beispiele in eine lokale Datei herunterladen:

In dem Beispiel wird davon ausgegangen, dass der {{site.data.keyword.cloudaccesstrailshort}}-Service in der Region 'Süden' der Vereinigten Staaten (us-south) bereitgestellt wird. 

```
var http = require("https")
var fs = require("fs")

var token = "{TOKEN}";

var spaceId = "{SPACE_ID}";

var endDate = "2018-07-02";
var startDate = "2018-06-30";

// Session create request body
var options = {
    "method": "POST",
    "hostname": "activity-tracker.ng.bluemix.net",
    "port": null,
    "path": "/v3/sessions",
    "headers": {
        "accept": "application/json",
        "content-type": "application/json",
        "x-auth-token": token,
        "x-auth-project-id": spaceId
    }
};
var req = http.request(options, createSession);
console.log("Creating new session...")
req.write(JSON.stringify({
    end: endDate,
    start: startDate,
    AtAccountLevel: true,
    SearchTime: ""
}));
req.end();

// Session create callback
function createSession(res) {
    var chunks = [];

    res.on("data", function (chunk) {
        chunks.push(chunk);
    });

    res.on("end", function () {
        var body = Buffer.concat(chunks);
        console.log(body.toString());
        createResp = JSON.parse(body.toString());
        sessionId = createResp['id'];
        downloadSession(sessionId);
    });
}

// session download callback
function downloadSession(sessionId) {
    // session download request body
    var options = {
        "method": "GET",
        "hostname": "activity-tracker.ng.bluemix.net",
        "port": null,
        "path": "/v3/events/download",
        "headers": {
            "x-auth-token": token,
            "x-auth-project-id": spaceId,
            "sessionid": String(sessionId),
            "accept": "application/octet-stream"
        }
    };

    var req = http.request(options, function (res) {
        var chunks = [];

        res.on("data", function (chunk) {
            chunks.push(chunk);
        });

        res.on("end", function () {
            var body = Buffer.concat(chunks);
            console.log("Session " + sessionId + " written to output.gz");

            fs.writeFile("output.gz", body, function (err) {
                if (err) {
                    console.log(err);
                }
            });
            deleteSession(sessionId);
        });
    });
    req.end();
}

// session delete callback
function deleteSession(sessionId) {
    //session delete request body
    options = {
        "method": "DELETE",
        "hostname": "activity-tracker.ng.bluemix.net",
        "port": null,
        "path": "/v3/sessions/" + sessionId,
        "headers": {
            "x-auth-token": token,
            "x-auth-project-id": spaceId,
            "accept": "application/json",
            "content-type": "application/json"
        }
    };

    console.log("Deleting session " + sessionId + "...")
    var req = http.request(options, function (res) {
        var chunks = [];

        res.on("data", function (chunk) {
            chunks.push(chunk);
        });

        res.on("end", function () {
            var body = Buffer.concat(chunks);
            deleteResp = body.toString();
            console.log(deleteResp);
        });
    });
    req.end();
}
```
{: codeblock}

