---

copyright:
  years: 2016, 2018
lastupdated: "2018-07-06"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}

# Scaricamento degli eventi
{: #downloading_events_api}

Puoi scaricare gli eventi {{site.data.keyword.cloudaccesstrailshort}} utilizzando l'API.
{:shortdesc}


Tieni conto delle seguenti informazioni:

* Devi avere il ruolo di **sviluppatore** nello spazio in cui viene eseguito il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}.
* Non puoi scaricare più di 15 giorni per sessione.
* Per scaricare i log dell'account, imposta il parametro **AtAccountLevel** su *true* e richiedi lo scaricamento nel contesto dello spazio in cui è stato eseguito il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}.

Per scaricare gli eventi, devi completare la seguente procedura:

1. Ottieni un token UAA.
2. Crea una sessione, in cui specificare le condizioni che definiscono il sottoinsieme di eventi che vuoi scaricare.
3. Scarica gli eventi in un file locale.
4. Elimina la sessione.



## Scaricamento degli eventi utilizzando CURL
{: #curl}

Completa le seguenti istruzioni per scaricare gli eventi in un file locale:

1. Ottieni un token UAA.

    Per ulteriori informazioni, consulta [Acquisizione di un token UAA](/docs/services/cloud-activity-tracker/reference/auth_uaa.html#auth_uaa).

2. Crea una sessione, in cui specificare le condizioni che definiscono il sottoinsieme di eventi che vuoi scaricare.

    ```
    curl -X POST -H "Content-Type: application/json" -H "X-Auth-Token: bearer $token" -H "X-Auth-Project-Id: $spaceID" ENDPOINT/v3/sessions -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":true,"SearchTime":""}'
    ```
    {: codeblock}

    dove:
    
    * *token* rappresenta il valore del token UAA che è stato ottenuto in un passo precedente.
    * *spaceID* rappresenta l'UUID dello spazio Cloud Foundry in cui è stato eseguito il provisioning di {{site.data.keyword.cloudaccesstrailshort}}.
    * *ENDPOINT* rappresenta il punto di ingresso del servizio. Ogni regione ha un URL diverso. Per ottenere l'elenco degli endpoint, consulta [Endpoint](/docs/services/cloud-activity-tracker/reference/ref_endpoints.html#api_endpoints).
    * *start* e *end*rappresentano un intervallo di tempo in cui vuoi scaricare gli eventi. Il formato della data è *YYYY-MM-DD*. 
    * *AtAccountLevel* indica se gli eventi da scaricare sono nel dominio dell'account o dello spazio.
    * *SearchTime* indica l'ora della giornata per la quale vuoi scaricare gli eventi.

    Per creare una sessione per scaricare gli eventi da un dominio dello spazio nella regione Stati Uniti Sud, imposta il parametro **AtAccountLevel** su *false*:

    ```
    curl -X POST -H "Content-Type: application/json" -H "X-Auth-Token: bearer $token" -H "X-Auth-Project-Id: $spaceID" https://activity-tracker.ng.bluemix.net/v3/sessions -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":false,"SearchTime":""}'
    ```
    {: codeblock}

    Il campo di output **id** restituisce l'ID sessione.
    
    Ad esempio, l'output è simile a quanto segue:

    ```
    {"id":"b08cb740-ff85-404f-a6eb-ffec5374c7c6","space":"c1234567-6d55-4193-a9de-378620d6fab5","username":"xxx@ibm.com","create-time":"2018-06-28T12:50:36.012383445Z","access-time":"2018-06-28T12:50:36.012383445Z","date-range":{"Start":"2018-06-27","End":"2018-06-27"},"types":{"Type":"ActivityTracker","AtAccountLevel":true},"search-time":""}
    ```
    {: screen}
    
    Ad esempio, per creare una sessione per scaricare gli eventi dell'account da un dominio dell'account nella regione Stati Uniti Sud, imposta il parametro **AtAccountLevel** su *true*:

    ```
    curl -X POST -H "Content-Type: application/json" -H "X-Auth-Token: bearer $token" -H "X-Auth-Project-Id: $spaceID" https://activity-tracker.ng.bluemix.net/v3/sessions -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":true,"SearchTime":""}'
    ```
    {: codeblock}

3. Scarica gli eventi in un file locale.

    ```
    curl -H "x-auth-token: bearer $token" -H "SESSIONID: $sessionID" -H "X-Auth-Project-Id: $spaceID" -H "accept: application/json" ENDPOINT/v3/events/download > FILENAME.gz
    ```
    {: codeblock}

    dove *FILENAME* è il nome dello spazio in cui sarà scaricato l'evento.

    Ad esempio:

    ```
    curl -H "x-auth-token: bearer $token" -H "SESSIONID: $sessionID" -H "X-Auth-Project-Id: $spaceID" -H "accept: application/json" https://activity-tracker.ng.bluemix.net/v3/events/download > spaceXevents.gz
    ```
    {: codeblock}

4. Elimina la sessione.

    ```
    curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer $token" -H "Accept:application/json" -H "X-Auth-Project-Id:$spaceId" --request DELETE https://activity-tracker.ng.bluemix.net/v3/sessions/$sessionId

    ```
    {: codeblock}


## Esempio NodeJS di come scaricare gli eventi
{: #node}

Questo è il codice di esempio che puoi utilizzare per verificare come scaricare gli eventi in un file locale:

L'esempio presuppone che sia stato eseguito il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}} nella regione Stati Uniti Sud. 

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

