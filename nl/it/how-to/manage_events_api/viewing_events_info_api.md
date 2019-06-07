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

# Visualizzazione di informazioni sull'evento
{: #viewing_events_info_api}

Utilizza l'API {{site.data.keyword.cloudaccesstrailshort}} per ottenere le informazioni sugli eventi archiviati in {{site.data.keyword.cloudaccesstrailshort}}.
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} è obsoleto. A partire dal 9 maggio 2019, non puoi eseguire il provisioning delle nuove istanze di {{site.data.keyword.cloudaccesstrailshort}}. Le istanze del piano Premium esistenti sono supportate fino al 30 settembre 2019. Per continuare a monitorare l'attività del tuo account {{site.data.keyword.cloud_notm}}, esegui il provisioning di un'istanza di [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}

## Richiamo del numero di eventi utilizzando cURL
{: #viewing_events_info_api_records_per_day_curl}

Completa la seguente procedura per visualizzare le informazioni sugli eventi in una data specifica:

1. Ottieni un token UAA.

    Per ulteriori informazioni, consulta [Acquisizione di un token UAA](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-auth_uaa#auth_uaa).

2. Immetti il seguente comando cURL per richiamare il numero totale di eventi archiviati in {{site.data.keyword.cloudaccesstrailshort}} in una data specifica.

    ```
    curl -X GET -H "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json"  ENDPOINT/v3/events   -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":false,"SearchTime":""}'
    ```
    {: codeblock}

    dove

    * *token* è il token UAA.
    * *$spaceID* rappresenta l'UUID dello spazio Cloud Foundry in cui è stato eseguito il provisioning di {{site.data.keyword.cloudaccesstrailshort}}.
    * *ENDPOINT* rappresenta il punto di ingresso del servizio. Ogni regione ha un URL diverso. Per ottenere l'elenco degli endpoint, consulta [Endpoint](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-ref_endpoints#api_endpoints).
    * *start* e *end*rappresentano un intervallo di tempo in cui vuoi scaricare gli eventi. Il formato della data è YYYY-MM-DD. 
    * *AtAccountLevel* indica il dominio in cui vuoi ottenere le informazioni sugli eventi.
    * *SearchTime* indica l'ora della giornata per la quale vuoi le informazioni sugli eventi.


Ad esempio, per ottenere le informazioni sugli eventi in un giorno specifico in un dominio dello spazio nella regione Stati Uniti Sud, puoi immettere il seguente comando cURL:

```
curl -X GET -H "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json"  https://activity-tracker.ng.bluemix.net/v3/events   -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":false,"SearchTime":""}'
```
{: codeblock}

Ad esempio, per ottenere le informazioni sugli eventi dell'account in un giorno specifico nella regione Stati Uniti Sud, puoi immettere il seguente comando cURL:

```
curl -X GET -H "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json"  https://activity-tracker.ng.bluemix.net/v3/events   -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":true,"SearchTime":""}'
```
{: codeblock}

Ad esempio, per visualizzare gli eventi per l'ultima settimana, puoi immettere il seguente comando cURL:

```
curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json" --request GET --data "{\"start\":\"$(date -u -v-7d +%F)\", \"end\":\"$(date -u +%F)\" }" https://activity-tracker.ng.bluemix.net/v3/events
```
{: codeblock}


## Esempio NodeJS di come visualizzare gli eventi del giorno
{: #viewing_events_info_api_node}

Questo è il codice di esempio che puoi utilizzare per verificare come visualizzare il numero di eventi del giorno:

L'esempio presuppone che sia stato eseguito il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}} nella regione Stati Uniti Sud. 

```
var http = require("https")
var fs = require("fs")

var token = "{TOKEN}";

// ID spazio dello spazio Cloud Foundry in cui è stato eseguito il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}.
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



