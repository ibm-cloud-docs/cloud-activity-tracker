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

# Descarga de sucesos
{: #downloading_events_api}

Puede descargar sucesos de {{site.data.keyword.cloudaccesstrailshort}} mediante la API.
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} está en desuso. A partir del 9 de mayo de 2019, no se pueden suministrar nuevas instancias de {{site.data.keyword.cloudaccesstrailshort}}. Las instancias existentes del plan premium recibirán soporte hasta el 30 de septiembre de 2019. Para seguir supervisando la actividad de la cuenta de {{site.data.keyword.cloud_notm}} suministre una instancia de [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}

Tenga en cuenta la información siguiente:

* Debe tener el rol de **desarrollador** en el espacio en el que se suministra el servicio {{site.data.keyword.cloudaccesstrailshort}}.
* No puede descargar más de 15 días por sesión.
* Para descargar registros de la cuenta, establezca el parámetro **AtAccountLevel** en *true* y solicite la descarga dentro del contexto del espacio en el que se suministra el servicio {{site.data.keyword.cloudaccesstrailshort}}.

Para descargar sucesos, debe seguir los pasos siguientes:

1. Obtenga una señal de UAA.
2. Cree una sesión, en la que debe especificar las condiciones que definen el subconjunto de sucesos que desea descargar.
3. Descargue los sucesos en un archivo local.
4. Suprima la sesión.



## Descarga de sucesos mediante CURL
{: #downloading_events_api_curl}

Siga los pasos siguientes para descargar los sucesos en un archivo local:

1. Obtenga una señal de UAA.

    Para obtener más información, consulte [Obtención de una señal de UAA](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-auth_uaa#auth_uaa).

2. Cree una sesión, en la que debe especificar las condiciones que definen el subconjunto de sucesos que desea descargar.

    ```
    curl -X POST -H "Content-Type: application/json" -H "X-Auth-Token: bearer $token" -H "X-Auth-Project-Id: $spaceID" ENDPOINT/v3/sessions -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":true,"SearchTime":""}'
    ```
    {: codeblock}

    Donde:
    
    *token* representa el valor de señal de UAA que ha obtenido en un paso anterior.

    *spaceID* representa el UUID del espacio de Cloud Foundry en el que se ha suministrado {{site.data.keyword.cloudaccesstrailshort}}.

    *ENDPOINT* representa el punto de entrada al servicio. Cada región tiene un URL diferente. Para obtener la lista de puntos finales por región, consulte [Puntos finales](/docs/services/cloud-activity-tracker/reference/ref_endpoints.html#api_endpoints).

    *start* y *end* representan un intervalo de tiempo en el que desea descargar los sucesos. El formato de fecha es *AAAA-MM-DD*. 

    *AtAccountLevel* indica si los sucesos que se van a descargar están en el dominio de cuenta o en un dominio de espacio.
    
    *SearchTime* indica la hora del día para la que desea descargar los sucesos.

    Para crear una sesión desde la que descargar sucesos desde un dominio de espacio en la región EE. UU. sur, establezca el parámetro **AtAccountLevel** en *false*:

    ```
    curl -X POST -H "Content-Type: application/json" -H "X-Auth-Token: bearer $token" -H "X-Auth-Project-Id: $spaceID" https://activity-tracker.ng.bluemix.net/v3/sessions -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":false,"SearchTime":""}'
    ```
    {: codeblock}

    El campo de salida **id** devuelve el ID de sesión.
    
    Por ejemplo, la salida tiene el aspecto siguiente:

    ```
    {"id":"b08cb740-ff85-404f-a6eb-ffec5374c7c6","space":"c1234567-6d55-4193-a9de-378620d6fab5","username":"xxx@ibm.com","create-time":"2018-06-28T12:50:36.012383445Z","access-time":"2018-06-28T12:50:36.012383445Z","date-range":{"Start":"2018-06-27","End":"2018-06-27"},"types":{"Type":"ActivityTracker","AtAccountLevel":true},"search-time":""}
    ```
    {: screen}
    
    Por ejemplo, para crear una sesión para descargar sucesos de cuenta desde el dominio de cuenta en la región EE. UU. sur, establezca el parámetro **AtAccountLevel** en *true*:

    ```
    curl -X POST -H "Content-Type: application/json" -H "X-Auth-Token: bearer $token" -H "X-Auth-Project-Id: $spaceID" https://activity-tracker.ng.bluemix.net/v3/sessions -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":true,"SearchTime":""}'
    ```
    {: codeblock}

3. Descargue los sucesos en un archivo local.

    ```
    curl -H "x-auth-token: bearer $token" -H "SESSIONID: $sessionID" -H "X-Auth-Project-Id: $spaceID" -H "accept: application/json" ENDPOINT/v3/events/download > FILENAME.gz
    ```
    {: codeblock}

    Donde *FILENAME* es el nombre del archivo local donde se van a descargar los sucesos.

    Por ejemplo:

    ```
    curl -H "x-auth-token: bearer $token" -H "SESSIONID: $sessionID" -H "X-Auth-Project-Id: $spaceID" -H "accept: application/json" https://activity-tracker.ng.bluemix.net/v3/events/download > spaceXevents.gz
    ```
    {: codeblock}

4. Suprima la sesión.

    ```
    curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer $token" -H "Accept:application/json" -H "X-Auth-Project-Id:$spaceId" --request DELETE https://activity-tracker.ng.bluemix.net/v3/sessions/$sessionId

    ```
    {: codeblock}


## Ejemplo de NodeJS de cómo descargar sucesos
{: #downloading_events_api_node}

Este es el código de ejemplo que puede utilizar para probar cómo se descargan sucesos en un archivo local:

En el ejemplo se da por supuesto que el servicio {{site.data.keyword.cloudaccesstrailshort}} se suministra en la región EE. UU. sur. 

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

