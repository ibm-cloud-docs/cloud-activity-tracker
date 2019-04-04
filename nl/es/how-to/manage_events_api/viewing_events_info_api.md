---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

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


# Visualización de la información de sucesos
{: #viewing_events_info_api}

Utilice la API de {{site.data.keyword.cloudaccesstrailshort}} para obtener información sobre los sucesos que se almacenan en {{site.data.keyword.cloudaccesstrailshort}}.
{:shortdesc}


## Obtención del número de sucesos mediante cURL
{: #viewing_events_info_api_records_per_day_curl}

Siga los pasos siguientes para ver información sobre los sucesos de una determinada fecha:

1. Obtenga una señal de UAA.

    Para obtener más información, consulte [Obtención de una señal de UAA](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-auth_uaa#auth_uaa).

2. Ejecute el siguiente mandato cURL para obtener el número total de sucesos que se han almacenado en {{site.data.keyword.cloudaccesstrailshort}} en una fecha específica.

    ```
    curl -X GET -H "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json"  ENDPOINT/v3/events   -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":false,"SearchTime":""}'
    ```
    {: codeblock}

    donde

    * *token* es la señal de UAA.
    * *$spaceID* representa el UUID del espacio de Cloud Foundry en el que se ha suministrado {{site.data.keyword.cloudaccesstrailshort}}.
    * *ENDPOINT* representa el punto de entrada al servicio. Cada región tiene un URL diferente. Para obtener la lista de puntos finales por región, consulte [Puntos finales](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-ref_endpoints#api_endpoints).
    * *start* y *end* representan un intervalo de tiempo en el que desea descargar los sucesos. El formato de fecha es AAAA-MM-DD. 
    * *AtAccountLevel* indica el dominio en el que desea obtener información sobre los sucesos.
    * *SearchTime* indica la hora del día para la que desea información sobre los sucesos.


Por ejemplo, para obtener información sobre los sucesos de un determinado día de un dominio de espacio de la región EE. UU. sur, puede ejecutar el siguiente mandato cURL:

```
curl -X GET -H "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json"  https://activity-tracker.ng.bluemix.net/v3/events   -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":false,"SearchTime":""}'
```
{: codeblock}

Por ejemplo, para obtener información sobre los sucesos de cuenta de un determinado día en la región EE. UU. sur, puede ejecutar el siguiente mandato cURL:

```
curl -X GET -H "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json"  https://activity-tracker.ng.bluemix.net/v3/events   -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":true,"SearchTime":""}'
```
{: codeblock}

Por ejemplo, para ver los sucesos correspondientes a la última semana, puede ejecutar el siguiente mandato cURL:

```
curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json" --request GET --data "{\"start\":\"$(date -u -v-7d +%F)\", \"end\":\"$(date -u +%F)\" }" https://activity-tracker.ng.bluemix.net/v3/events
```
{: codeblock}


## Ejemplo de NodeJS sobre cómo ver sucesos por día
{: #viewing_events_info_api_node}

Este es el código de ejemplo que puede utilizar para probar cómo ver el número de sucesos por día:

En el ejemplo se da por supuesto que el servicio {{site.data.keyword.cloudaccesstrailshort}} se suministra en la región EE. UU. sur. 

```
var http = require("https")
var fs = require("fs")

var token = "{TOKEN}";

// Space ID of the Cloud Foundry space where the {{site.data.keyword.cloudaccesstrailshort}} service is provisioned.
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



