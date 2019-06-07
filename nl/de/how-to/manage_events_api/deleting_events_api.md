---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, delete event, API

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


# Ereignisinformationen löschen
{: #deleting_events_api}

Verwenden Sie die {{site.data.keyword.cloudaccesstrailshort}}-API, um in {{site.data.keyword.cloudaccesstrailshort}} gespeicherte Ereignisse zu löschen.
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} wird nicht mehr verwendet. Ab 09. Mai 2019 können keine neuen {{site.data.keyword.cloudaccesstrailshort}}-Instanzen mehr bereitgestellt werden. Vorhandene Instanzen des Premium-Plans werden bis 30. September 2019 unterstützt. Wenn Sie die Aktivitäten Ihres {{site.data.keyword.cloud_notm}}-Kontos weiterhin verfolgen möchten, stellen Sie eine Instanz von [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) bereit.
{: deprecated}

**Hinweis:** Auch wenn Sie Ereignisse manuell mithilfe des API-Aufrufs löschen können, sollten Sie überlegen, ob Sie die Aufbewahrungsrichtlinie so konfigurieren, dass Ereignisse automatisch gelöscht werden. Weitere Informationen finden Sie in [Ereignisaufbewahrungsrichtlinie konfigurieren](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-configuring_retention_policy#configuring_retention_policy).

## Ereignisse mithilfe von cURL löschen
{: #deleting_events_api_records_per_day_curl}

Führen Sie die folgenden Schritte aus, um Ereignisse zu löschen, die in einer Bereichsdomäne verfügbar sind:

1. Rufen Sie ein UAA-Token ab.

    Weitere Informationen finden Sie in [UAA-Token abrufen](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-auth_uaa#auth_uaa).

2. Wenn Sie Ereignisse löschen wollen, die an einem bestimmten Datum in {{site.data.keyword.cloudaccesstrailshort}} gespeichert wurden, führen Sie den folgenden cURL-Befehl aus:

    ```
    curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json" -X DELETE  ENDPOINT/v3/events -d '{"start":"2018-06-24","end":"2018-06-24","AtAccountLevel":false,"SearchTime":""}'
    ```
    {: codeblock}

    Dabei gilt Folgendes:

    * *token* ist das UAA-Token.
    * *spaceID* stellt die UUID des Cloud Foundry-Bereichs dar, in dem {{site.data.keyword.cloudaccesstrailshort}} bereitgestellt wird.
    * *ENDPOINT* stellt den Eingangspunkt zum Service dar. Jede Region hat eine andere URL. Informationen dazu, wie Sie die Liste der Endpunkte für die jeweilige Region abrufen, finden Sie in [Endpunkte](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-ref_endpoints#api_endpoints).
    * *start* und *end* stellen einen Zeitbereich dar, für den Sie Ereignisse herunterladen möchten. Das Datumsformat ist JJJJ-MM-TT. 
    * *AtAccountLevel* gibt die Domäne an, in der Informationen zu den Ereignissen abgerufen werden sollen.
    * *SearchTime* gibt die Tageszeit an, für die Sie Informationen zu den Ereignissen abrufen wollen.


Wenn Sie zum Beispiel Ereignisse an einem bestimmten Tag in einer Bereichsdomäne im Süden der Vereinigten Staaten löschen wollen, können Sie den folgenden cURL-Befehl ausführen:

```
curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json" -X DELETE  https://activity-tracker.ng.bluemix.net/v3/events -d '{"start":"2018-06-24","end":"2018-06-24","AtAccountLevel":false,"SearchTime":""}'
```
{: codeblock}

Wenn Sie zum Beispiel Ereignisse in einer Bereichsdomäne für die vergangene Woche löschen wollen, können Sie den folgenden cURL-Befehl ausführen:

```
curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json" --request DELETE --data "{\"start\":\"$(date -u -v-7d +%F)\", \"end\":\"$(date -u -v-6d +%F)\" }" https://activity-tracker.ng.bluemix.net/v3/events
```
{: codeblock}


## NodeJS-Beispiel für das Löschen von Ereignissen
{: #deleting_events_api_node}

Mit dem nachfolgenden Beispielcode können Sie testen, wie Sie Beispiele löschen:

In dem Beispiel wird davon ausgegangen, dass der {{site.data.keyword.cloudaccesstrailshort}}-Service in der Region 'Süden' der Vereinigten Staaten (us-south) bereitgestellt wird. 

```
var http = require("https")
var fs = require("fs")

var token = "{TOKEN}";

// Bereichs-ID des Cloud Foundry-Bereichs, wo der {{site.data.keyword.cloudaccesstrailshort}}-Service bereitgestellt wird.
var spaceId = "{SPACE_ID}";

var endDate = "2018-07-02";
var startDate = "2018-06-30";

var http = require("https");

var options = {
    "method": "DELETE",
    "connection": "close",
    "hostname": "activity-tracker.ng.bluemix.net",
    "port": null,
    "path": "/v3/events",
    "headers": {
        "x-auth-token": token,
        "x-auth-project-id": spaceId,
        "accept": "application/json",
        "content-type": "application/json"
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

req.write(JSON.stringify({
    end: endDate,
    start: startDate
}));
req.end();
```
{: codeblock}


