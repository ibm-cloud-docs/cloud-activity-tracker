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

# Fazendo download de eventos
{: #downloading_events_api}

É possível fazer download de eventos do {{site.data.keyword.cloudaccesstrailshort}} usando a API.
{:shortdesc}


Considere as informações a seguir:

* Deve-se ter a função de **desenvolvedor** no espaço em que o serviço {{site.data.keyword.cloudaccesstrailshort}} é provisionado.
* Não é possível fazer download de mais de 15 dias por sessão.
* Para fazer download de logs da conta, você configura o parâmetro **AtAccountLevel** como *true* e solicita o download dentro do contexto do espaço em que o serviço {{site.data.keyword.cloudaccesstrailshort}} é provisionado.

Para fazer download de eventos, deve-se concluir as etapas a seguir:

1. Obtenha um token da UAA.
2. Crie uma sessão, na qual você especifica as condições que definem o subconjunto de eventos que você deseja fazer download.
3. Faça download dos eventos em um arquivo local.
4. Exclua a sessão.



## Fazendo download de eventos usando CURL
{: #curl}

Conclua as etapas a seguir para fazer download de eventos em um arquivo local:

1. Obtenha um token da UAA.

    Para obter mais informações, consulte [Obtendo um token UAA](/docs/services/cloud-activity-tracker/reference/auth_uaa.html#auth_uaa).

2. Crie uma sessão, na qual você especifica as condições que definem o subconjunto de eventos que você deseja fazer download.

    ```
    curl -X POST -H "Content-Type: application/json" -H "X-Auth-Token: bearer $token" -H "X-Auth-Project-Id: $spaceID" ENDPOINT/v3/sessions -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":true,"SearchTime":""}'
    ```
    {: codeblock}

    em que:
    
    * *token* representa o valor do token da UAA que você obteve em uma etapa anterior.
    * *spaceID* representa o UUID do espaço do Cloud Foundry no qual o {{site.data.keyword.cloudaccesstrailshort}} está provisionado.
    * *ENDPOINT* representa o ponto de entrada para o serviço. Cada região possui uma URL diferente. Para obter a lista de terminais por região, consulte [Terminais](/docs/services/cloud-activity-tracker/reference/ref_endpoints.html#api_endpoints).
    * *start* e *end* representam um intervalo de tempo no qual você deseja fazer download de eventos. O formato de data é
*YYYY-MM-DD*. 
    * *AtAccountLevel* indica se os eventos a serem transferidos por download estão no domínio de contas ou em um domínio de espaço.
    * *SearchTime* indica a hora do dia para a qual você deseja fazer download de eventos.

    Para criar uma sessão para fazer download de eventos de um domínio de espaço na região us-south, configure o parâmetro **AtAccountLevel** como *false*:

    ```
    curl -X POST -H "Content-Type: application/json" -H "X-Auth-Token: bearer $token" -H "X-Auth-Project-Id: $spaceID" https://activity-tracker.ng.bluemix.net/v3/sessions -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":false,"SearchTime":""}'
    ```
    {: codeblock}

    O campo de saída **id** retorna o ID de sessão.
    
    Por exemplo, a saída é semelhante ao seguinte:

    ```
    {"id":"b08cb740-ff85-404f-a6eb-ffec5374c7c6","space":"c1234567-6d55-4193-a9de-378620d6fab5","username":"xxx@ibm.com","create-time":"2018-06-28T12:50:36.012383445Z","access-time":"2018-06-28T12:50:36.012383445Z","date-range":{"Start":"2018-06-27","End":"2018-06-27"},"types":{"Type":"ActivityTracker","AtAccountLevel":true},"search-time":""}
    ```
    {: screen}
    
    Por exemplo, para criar uma sessão para fazer download de eventos de conta por meio do domínio de contas na região us-south, configure o parâmetro **AtAccountLevel** como *true*:

    ```
    curl -X POST -H "Content-Type: application/json" -H "X-Auth-Token: bearer $token" -H "X-Auth-Project-Id: $spaceID" https://activity-tracker.ng.bluemix.net/v3/sessions -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":true,"SearchTime":""}'
    ```
    {: codeblock}

3. Faça download dos eventos em um arquivo local.

    ```
    curl -H "x-auth-token: bearer $token" -H "SESSIONID: $sessionID" -H "X-Auth-Project-Id: $spaceID" -H "accept: application/json" ENDPOINT/v3/events/download > FILENAME.gz
    ```
    {: codeblock}

    em que *FILENAME* é o nome do arquivo local no qual os eventos serão transferidos por download.

    Exemplo:

    ```
    curl -H "x-auth-token: bearer $token" -H "SESSIONID: $sessionID" -H "X-Auth-Project-Id: $spaceID" -H "accept: application/json" https://activity-tracker.ng.bluemix.net/v3/events/download > spaceXevents.gz
    ```
    {: codeblock}

4. Exclua a sessão.

    ```
    curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer $token" -H "Accept:application/json" -H "X-Auth-Project-Id:$spaceId" --request DELETE https://activity-tracker.ng.bluemix.net/v3/sessions/$sessionId

    ```
    {: codeblock}


## Exemplo de NodeJS de como fazer download de eventos
{: #node}

Este é um código de amostra que pode ser usado para testar como fazer download de eventos para um arquivo local:

O exemplo pressupõe que o serviço {{site.data.keyword.cloudaccesstrailshort}} é provisionado na região Sul dos EUA. 

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

