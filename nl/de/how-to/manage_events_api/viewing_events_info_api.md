---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, view events, API

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

# Ereignisinformationen anzeigen
{: #viewing_events_info_api}

Verwenden Sie die {{site.data.keyword.cloudaccesstrailshort}}-API, um Informationen zu den in {{site.data.keyword.cloudaccesstrailshort}} gespeicherten Ereignissen abzurufen.
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} wird nicht mehr verwendet. Ab 09. Mai 2019 können keine neuen {{site.data.keyword.cloudaccesstrailshort}}-Instanzen mehr bereitgestellt werden. Vorhandene Instanzen des Premium-Plans werden bis 30. September 2019 unterstützt. Wenn Sie die Aktivitäten Ihres {{site.data.keyword.cloud_notm}}-Kontos weiterhin verfolgen möchten, stellen Sie eine Instanz von [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) bereit.
{: deprecated}

## Anzahl von Ereignissen mithilfe von cURL abrufen
{: #viewing_events_info_api_records_per_day_curl}

Führen Sie die folgenden Schritte aus, um Informationen zu den Ereignissen an einem bestimmten Datum anzuzeigen:

1. Rufen Sie ein UAA-Token ab.

    Weitere Informationen finden Sie in [UAA-Token abrufen](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-auth_uaa#auth_uaa).

2. Wenn Sie die Gesamtzahl von Ereignissen abrufen wollen, die an einem bestimmten Datum in {{site.data.keyword.cloudaccesstrailshort}} gespeichert wurden, führen Sie den folgenden cURL-Befehl aus:

    ```
    curl -X GET -H "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json"  ENDPOINT/v3/events   -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":false,"SearchTime":""}'
    ```
    {: codeblock}

    Dabei gilt Folgendes:

    * *token* ist das UAA-Token.
    * *$spaceID* stellt die UUID des Cloud Foundry-Bereichs dar, in dem {{site.data.keyword.cloudaccesstrailshort}} bereitgestellt wird.
    * *ENDPOINT* stellt den Eingangspunkt zum Service dar. Jede Region hat eine andere URL. Informationen dazu, wie Sie die Liste der Endpunkte für die jeweilige Region abrufen, finden Sie in [Endpunkte](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-ref_endpoints#api_endpoints).
    * *start* und *end* stellen einen Zeitbereich dar, für den Sie Ereignisse herunterladen möchten. Das Datumsformat ist JJJJ-MM-TT. 
    * *AtAccountLevel* gibt die Domäne an, in der Informationen zu den Ereignissen abgerufen werden sollen.
    * *SearchTime* gibt die Tageszeit an, für die Sie Informationen zu den Ereignissen abrufen wollen.


Wenn Sie zum Beispiel Informationen zu den Ereignissen an einem bestimmten Tag in einer Bereichsdomäne im Süden der Vereinigten Staaten abrufen wollen, können Sie den folgenden cURL-Befehl ausführen:

```
curl -X GET -H "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json"  https://activity-tracker.ng.bluemix.net/v3/events   -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":false,"SearchTime":""}'
```
{: codeblock}

Wenn Sie zum Beispiel Informationen zu den Ereignissen für ein Konto an einem bestimmten Tag im Süden der Vereinigten Staaten abrufen wollen, können Sie den folgenden cURL-Befehl ausführen:

```
curl -X GET -H "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json"  https://activity-tracker.ng.bluemix.net/v3/events   -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":true,"SearchTime":""}'
```
{: codeblock}

Wenn Sie zum Beispiel Ereignisse für die vergangene Woche anzeigen wollen, können Sie den folgenden cURL-Befehl ausführen:

```
curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json" --request GET --data "{\"start\":\"$(date -u -v-7d +%F)\", \"end\":\"$(date -u +%F)\" }" https://activity-tracker.ng.bluemix.net/v3/events
```
{: codeblock}


## NodeJS-Beispiel für das Anzeigen von Ereignissen für einen bestimmten Tag
{: #viewing_events_info_api_node}

Mit dem nachfolgenden Beispielcode können Sie testen, wie Sie die Anzahl von Ereignissen für einen bestimmten Tag anzeigen:

In dem Beispiel wird davon ausgegangen, dass der {{site.data.keyword.cloudaccesstrailshort}}-Service in der Region 'Süden' der Vereinigten Staaten ('us-south') bereitgestellt wird. 

```
var http = require("https")
var fs = require("fs")

var token = "{TOKEN}";

// Bereichs-ID des Cloud Foundry-Bereichs, wo der {{site.data.keyword.cloudaccesstrailshort}}-Service bereitgestellt wird.
var spaceId = "{SPACE_ID}";

var endDate = "2018-07-02";
var startDate = "2018-06-30";

var options = {
    "method": "GET",
    "hostname": "activity-tracker.ng.bluemix.net",
    "port": null,
    "path": "/v3/events",
    "headers": {
        "Transfer-Encoding": "Chunked",
        "Content-Type": "application/json",
        "x-auth-token": token,
        "x-auth-project-id": spaceId,
        "accept": "application/json"
    }
};

var req = http.request(options, function (res) {
    var chunks = [];

    res.on("data", function (chunk) {
        chunks.push(chunk);
    });

    res.on("end", function () {
        var body = Buffer.concat(chunks);
        console.log(body.toString());
    });
});

req.write(JSON.stringify({ start: startDate, end: endDate }));
req.end();
```
{: codeblock}



