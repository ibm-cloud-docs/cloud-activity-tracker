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

# Téléchargement d'événements
{: #downloading_events_api}

Vous pouvez télécharger des événements {{site.data.keyword.cloudaccesstrailshort}} à l'aide de l'API.
{:shortdesc}


Prenez en compte les informations suivantes :

* Vous devez disposer du rôle **Développeur** dans l'espace où le service {{site.data.keyword.cloudaccesstrailshort}} est mis à disposition.
* Vous ne pouvez pas télécharger plus de 15 jours par session.
* Pour télécharger des journaux de compte, définissez le paramètre **AtAccountLevel** sur *true* et demandez le téléchargement dans le contexte de l'espace où le service {{site.data.keyword.cloudaccesstrailshort}} est mis à disposition.

Pour télécharger des événements, vous devez procéder comme suit :

1. Obtenez un jeton UAA.
2. Créez une session, dans laquelle vous spécifiez les conditions qui définissent le sous-ensemble d'événements à télécharger.
3. Téléchargez les événements dans un fichier local.
4. Supprimez la session.



## Téléchargement d'événements à l'aide de cURL
{: #downloading_events_api_curl}

Pour télécharger des événements dans un fichier local, procédez comme suit :

1. Obtenez un jeton UAA.

    Pour plus d'informations, voir [Obtention d'un jeton UAA](/docs/services/cloud-activity-tracker/reference/auth_uaa.html#auth_uaa).

2. Créez une session, dans laquelle vous spécifiez les conditions qui définissent le sous-ensemble d'événements à télécharger.

    ```
    curl -X POST -H "Content-Type: application/json" -H "X-Auth-Token: bearer $token" -H "X-Auth-Project-Id: $spaceID" ENDPOINT/v3/sessions -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":true,"SearchTime":""}'
    ```
    {: codeblock}

    où :
    
    * *token* représente la valeur du jeton UAA que vous avez obtenue lors d'une étape précédente.

    * *spaceID* représente l'identificateur unique universel de l'espace Cloud Foundry où {{site.data.keyword.cloudaccesstrailshort}} est mis à disposition.

    * *ENDPOINT* représente le point d'entrée vers le service. Chaque région a une adresse URL différente. Pour obtenir la liste des noeuds finaux par région, voir [Noeuds finaux](/docs/services/cloud-activity-tracker/reference/ref_endpoints.html#api_endpoints).

    * *start* et *end* représentent la plage de temps pendant laquelle vous souhaitez télécharger des événements. Le format de date est *AAAA-MM-JJ*. 

    * *AtAccountLevel* indique si les événements à télécharger se trouvent dans le domaine de compte ou dans un domaine d'espace.
    
    * *SearchTime* indique l'heure de la journée pour laquelle vous souhaitez télécharger des événements.

    Pour créer une session afin de télécharger des événements à partir d'un domaine d'espace dans la région us-south, définissez le paramètre **AtAccountLevel** sur *false* :

    ```
    curl -X POST -H "Content-Type: application/json" -H "X-Auth-Token: bearer $token" -H "X-Auth-Project-Id: $spaceID" https://activity-tracker.ng.bluemix.net/v3/sessions -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":false,"SearchTime":""}'
    ```
    {: codeblock}

    La zone de sortie **id** renvoie l'ID de session.
    
    Par exemple, la sortie est similaire à la suivante :

    ```
    {"id":"b08cb740-ff85-404f-a6eb-ffec5374c7c6","space":"c1234567-6d55-4193-a9de-378620d6fab5","username":"xxx@ibm.com","create-time":"2018-06-28T12:50:36.012383445Z","access-time":"2018-06-28T12:50:36.012383445Z","date-range":{"Start":"2018-06-27","End":"2018-06-27"},"types":{"Type":"ActivityTracker","AtAccountLevel":true},"search-time":""}
    ```
    {: screen}
    
    Par exemple, pour créer une session afin de télécharger des événements de compte à partir du domaine de compte dans la région us-south, définissez le paramètre **AtAccountLevel** sur *true* :

    ```
    curl -X POST -H "Content-Type: application/json" -H "X-Auth-Token: bearer $token" -H "X-Auth-Project-Id: $spaceID" https://activity-tracker.ng.bluemix.net/v3/sessions -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":true,"SearchTime":""}'
    ```
    {: codeblock}

3. Téléchargez les événements dans un fichier local.

    ```
    curl -H "x-auth-token: bearer $token" -H "SESSIONID: $sessionID" -H "X-Auth-Project-Id: $spaceID" -H "accept: application/json" ENDPOINT/v3/events/download > FILENAME.gz
    ```
    {: codeblock}

    où *FILENAME* est le nom du fichier local où les événements seront téléchargés.

    Par exemple :

    ```
    curl -H "x-auth-token: bearer $token" -H "SESSIONID: $sessionID" -H "X-Auth-Project-Id: $spaceID" -H "accept: application/json" https://activity-tracker.ng.bluemix.net/v3/events/download > spaceXevents.gz
    ```
    {: codeblock}

4. Supprimez la session.

    ```
    curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer $token" -H "Accept:application/json" -H "X-Auth-Project-Id:$spaceId" --request DELETE https://activity-tracker.ng.bluemix.net/v3/sessions/$sessionId

    ```
    {: codeblock}


## Exemple NodeJS de téléchargement d'événements
{: #downloading_events_api_node}

Il s'agit du code exemple que vous pouvez utiliser pour tester le téléchargement d'événements dans un fichier local :

L'exemple suppose que le service {{site.data.keyword.cloudaccesstrailshort}} est mis à disposition dans la région Sud des Etats-Unis. 

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

