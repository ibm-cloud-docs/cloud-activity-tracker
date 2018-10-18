---

copyright:
  years: 2016, 2018
lastupdated: "2018-07-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}



# Eliminazione delle informazioni dell'evento
{: #deleting_events_api}

Utilizza l'API {{site.data.keyword.cloudaccesstrailshort}} per eliminare gli eventi archiviati in {{site.data.keyword.cloudaccesstrailshort}}.
{:shortdesc}

**Nota:** anche se puoi eliminare gli eventi manualmente utilizzando la chiamata API, considera l'impostazione della politica di conservazione per eliminare gli eventi automaticamente. Per ulteriori informazioni, consulta [Configurazione della politica di conservazione degli eventi](/docs/services/cloud-activity-tracker/how-to/configuring_retention_policy.html#configuring_retention_policy).

## Eliminazione di eventi utilizzando cURL
{: #records_per_day_curl}

Completa la seguente procedura per eliminare gli eventi disponibili in un dominio dello spazio:

1. Ottieni un token UAA.

    Per ulteriori informazioni, consulta [Acquisizione di un token UAA](/docs/services/cloud-activity-tracker/reference/auth_uaa.html#auth_uaa).

2. Immetti il seguente comando cURL per eliminare gli eventi archiviati in {{site.data.keyword.cloudaccesstrailshort}} in una data specifica.

    ```
    curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json" -X DELETE  ENDPOINT/v3/events -d '{"start":"2018-06-24","end":"2018-06-24","AtAccountLevel":false,"SearchTime":""}'
    ```
    {: codeblock}

    dove

    * *token* è il token UAA.
    * *spaceID* rappresenta l'UUID dello spazio Cloud Foundry in cui è stato eseguito il provisioning di {{site.data.keyword.cloudaccesstrailshort}}.
    * *ENDPOINT* rappresenta il punto di ingresso del servizio. Ogni regione ha un URL diverso. Per ottenere l'elenco degli endpoint, consulta [Endpoint](/docs/services/cloud-activity-tracker/reference/ref_endpoints.html#api_endpoints).
    * *start* e *end*rappresentano un intervallo di tempo in cui vuoi scaricare gli eventi. Il formato della data è YYYY-MM-DD. 
    * *AtAccountLevel* indica il dominio in cui vuoi ottenere le informazioni sugli eventi.
    * *SearchTime* indica l'ora della giornata per la quale vuoi le informazioni sugli eventi.


Ad esempio, per eliminare gli eventi in un giorno specifico in un dominio dello spazio nella regione Stati Uniti Sud, puoi immettere il seguente comando cURL:

```
curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json" -X DELETE  https://activity-tracker.ng.bluemix.net/v3/events -d '{"start":"2018-06-24","end":"2018-06-24","AtAccountLevel":false,"SearchTime":""}'
```
{: codeblock}

Ad esempio, per eliminare gli eventi in un dominio dello spazio per l'ultima settimana, puoi immettere il seguente comando cURL:

```
curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json" --request DELETE --data "{\"start\":\"$(date -u -v-7d +%F)\", \"end\":\"$(date -u -v-6d +%F)\" }" https://activity-tracker.ng.bluemix.net/v3/events
```
{: codeblock}


## Esempio NodeJS di come eliminare gli eventi
{: #node}

Questo è il codice di esempio che puoi utilizzare per verificare come eliminare gli eventi:

L'esempio presuppone che sia stato eseguito il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}} nella regione Stati Uniti Sud. 

```
var http = require("https")
var fs = require("fs")

var token = "{TOKEN}";

// ID spazio dello spazio Cloud Foundry in cui è stato eseguito il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}.
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
