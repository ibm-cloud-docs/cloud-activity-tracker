---

copyright:
  years: 2016, 2019
lastupdated: "2019-01-22"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}



# Supresión de información de sucesos
{: #deleting_events_api}

Utilice la API de {{site.data.keyword.cloudaccesstrailshort}} para suprimir sucesos almacenados en {{site.data.keyword.cloudaccesstrailshort}}.
{:shortdesc}

**Nota:** aunque puede suprimir sucesos manualmente mediante la llamada de API, considere la posibilidad de establecer una política de retención para suprimir sucesos automáticamente. Para obtener más información, consulte [Configuración de la política de retención de sucesos](/docs/services/cloud-activity-tracker/how-to/configuring_retention_policy.html#configuring_retention_policy).

## Supresión de sucesos mediante cURL
{: #deleting_events_api_records_per_day_curl}

Siga los pasos siguientes para suprimir sucesos que están disponibles en un dominio de espacio:

1. Obtenga una señal de UAA.

    Para obtener más información, consulte [Obtención de una señal de UAA](/docs/services/cloud-activity-tracker/reference/auth_uaa.html#auth_uaa).

2. Ejecute el siguiente mandato cURL para suprimir los sucesos almacenados en {{site.data.keyword.cloudaccesstrailshort}} en una fecha específica.

    ```
    curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json" -X DELETE  ENDPOINT/v3/events -d '{"start":"2018-06-24","end":"2018-06-24","AtAccountLevel":false,"SearchTime":""}'
    ```
    {: codeblock}

    donde

    * *token* es la señal de UAA.
    * *spaceID* representa el UUID del espacio de Cloud Foundry en el que se ha suministrado {{site.data.keyword.cloudaccesstrailshort}}.
    * *ENDPOINT* representa el punto de entrada al servicio. Cada región tiene un URL diferente. Para obtener la lista de puntos finales por región, consulte [Puntos finales](/docs/services/cloud-activity-tracker/reference/ref_endpoints.html#api_endpoints).
    * *start* y *end* representan un intervalo de tiempo en el que desea descargar los sucesos. El formato de fecha es AAAA-MM-DD. 
    * *AtAccountLevel* indica el dominio en el que desea obtener información sobre los sucesos.
    * *SearchTime* indica la hora del día para la que desea información sobre los sucesos.


Por ejemplo, para suprimir sucesos de un determinado día de un dominio de espacio de la región EE. UU. sur, puede ejecutar el siguiente mandato cURL:

```
curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json" -X DELETE  https://activity-tracker.ng.bluemix.net/v3/events -d '{"start":"2018-06-24","end":"2018-06-24","AtAccountLevel":false,"SearchTime":""}'
```
{: codeblock}

Por ejemplo, para suprimir sucesos en un dominio de espacio correspondientes a la última semana, puede ejecutar el mandato cURL siguiente:

```
curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json" --request DELETE --data "{\"start\":\"$(date -u -v-7d +%F)\", \"end\":\"$(date -u -v-6d +%F)\" }" https://activity-tracker.ng.bluemix.net/v3/events
```
{: codeblock}


## Ejemplo de NodeJS de cómo suprimir sucesos
{: #deleting_events_api_node}

Este es el código de ejemplo que puede utilizar para probar cómo suprimir sucesos:

En el ejemplo se da por supuesto que el servicio {{site.data.keyword.cloudaccesstrailshort}} se suministra en la región EE. UU. sur. 

```
var http = require("https")
var fs = require("fs")

var token = "{TOKEN}";

// Space ID of the Cloud Foundry space where the {{site.data.keyword.cloudaccesstrailshort}} service is provisioned.
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
