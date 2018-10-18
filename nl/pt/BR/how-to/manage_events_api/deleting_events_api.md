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



# Excluindo informações de evento
{: #deleting_events_api}

Use a API do {{site.data.keyword.cloudaccesstrailshort}} para excluir eventos que estão armazenados no {{site.data.keyword.cloudaccesstrailshort}}.
{:shortdesc}

**Nota:** embora seja possível excluir eventos manualmente usando a chamada API, considere configurar a política de retenção para excluir eventos automaticamente. Para obter mais informações, consulte [Configurando a política de retenção de eventos](/docs/services/cloud-activity-tracker/how-to/configuring_retention_policy.html#configuring_retention_policy).

## Excluindo eventos usando cURL
{: #records_per_day_curl}

Conclua as etapas a seguir para excluir eventos que estão disponíveis em um domínio de espaço:

1. Obtenha um token da UAA.

    Para obter mais informações, consulte [Obtendo um token UAA](/docs/services/cloud-activity-tracker/reference/auth_uaa.html#auth_uaa).

2. Execute o comando cURL a seguir para excluir eventos que estão armazenados no {{site.data.keyword.cloudaccesstrailshort}} em uma data específica.

    ```
    curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json" -X DELETE  ENDPOINT/v3/events -d '{"start":"2018-06-24","end":"2018-06-24","AtAccountLevel":false,"SearchTime":""}'
    ```
    {: codeblock}

    em que

    * *token* é o token da UAA.
    * *spaceID* representa o UUID do espaço do Cloud Foundry no qual o {{site.data.keyword.cloudaccesstrailshort}} está provisionado.
    * *ENDPOINT* representa o ponto de entrada para o serviço. Cada região possui uma URL diferente. Para obter a lista de terminais por região, consulte [Terminais](/docs/services/cloud-activity-tracker/reference/ref_endpoints.html#api_endpoints).
    * *start* e *end* representam um intervalo de tempo no qual você deseja fazer download de eventos. O formato de data é YYYY-MM-DD. 
    * *AtAccountLevel* indica o domínio no qual você deseja obter informações sobre os eventos.
    * *SearchTime* indica a hora do dia para a qual você deseja obter informações sobre os eventos.


Por exemplo, para excluir eventos em um dia específico em um domínio de espaço na região Sul dos EUA, é possível executar o comando cURL a seguir:

```
curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json" -X DELETE  https://activity-tracker.ng.bluemix.net/v3/events -d '{"start":"2018-06-24","end":"2018-06-24","AtAccountLevel":false,"SearchTime":""}'
```
{: codeblock}

Por exemplo, para excluir eventos em um domínio de espaço para a última semana, é possível executar o comando cURL a seguir:

```
curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json" --request DELETE --data "{\"start\":\"$(date -u -v-7d +%F)\", \"end\":\"$(date -u -v-6d +%F)\" }" https://activity-tracker.ng.bluemix.net/v3/events
```
{: codeblock}


## Exemplo de NodeJS de como excluir eventos
{: #node}

Este é um código de amostra que pode ser usado para testar como excluir eventos:

O exemplo pressupõe que o serviço {{site.data.keyword.cloudaccesstrailshort}} é provisionado na região Sul dos EUA. 

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
