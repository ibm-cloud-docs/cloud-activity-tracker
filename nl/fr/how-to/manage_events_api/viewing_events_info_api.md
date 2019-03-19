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



# Affichage des informations sur les événements
{: #viewing_events_info_api}

Utilisez l'API {{site.data.keyword.cloudaccesstrailshort}} pour obtenir des informations sur les événements qui sont stockés dans {{site.data.keyword.cloudaccesstrailshort}}.
{:shortdesc}


## Obtention du nombre d'événements à l'aide de cURL
{: #viewing_events_info_api_records_per_day_curl}

Procédez comme suit pour afficher des informations sur les événements d'une date spécifique :

1. Obtenez un jeton UAA.

    Pour plus d'informations, voir [Obtention d'un jeton UAA](/docs/services/cloud-activity-tracker/reference/auth_uaa.html#auth_uaa).

2. Exécutez la commande cURL suivante pour obtenir le nombre total d'événements qui sont stockés dans {{site.data.keyword.cloudaccesstrailshort}} à une date spécifique.

    ```
    curl -X GET -H "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json"  ENDPOINT/v3/events   -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":false,"SearchTime":""}'
    ```
    {: codeblock}

    où

    * *token* est le jeton UAA.
    * *$spaceID* représente l'identificateur unique universel de l'espace Cloud Foundry où {{site.data.keyword.cloudaccesstrailshort}} est mis à disposition.
    * *ENDPOINT* représente le point d'entrée vers le service. Chaque région a une adresse URL différente. Pour obtenir la liste des noeuds finaux par région, voir [Noeuds finaux](/docs/services/cloud-activity-tracker/reference/ref_endpoints.html#api_endpoints).
    * *start* et *end* représentent la plage de temps pendant laquelle vous souhaitez télécharger des événements. Le format de date est AAAA-MM-JJ. 
    * *AtAccountLevel* indique le domaine dans lequel vous voulez obtenir des informations sur les événements.
    * *SearchTime* indique l'heure de la journée pour laquelle vous souhaitez des informations sur les événements.


Par exemple, pour obtenir des informations sur les événements d'un jour spécifique dans un domaine d'espace dans la région Sud des Etats-Unis, vous pouvez exécuter la commande cURL suivante :

```
curl -X GET -H "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json"  https://activity-tracker.ng.bluemix.net/v3/events   -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":false,"SearchTime":""}'
```
{: codeblock}

Par exemple, pour obtenir des informations sur les événements de compte d'un jour spécifique dans la région Sud des Etats-Unis, vous pouvez exécuter la commande cURL suivante :

```
curl -X GET -H "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json"  https://activity-tracker.ng.bluemix.net/v3/events   -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":true,"SearchTime":""}'
```
{: codeblock}

Par exemple, pour afficher les événements de la semaine dernière, vous pouvez exécuter la commande cURL suivante :

```
curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json" --request GET --data "{\"start\":\"$(date -u -v-7d +%F)\", \"end\":\"$(date -u +%F)\" }" https://activity-tracker.ng.bluemix.net/v3/events
```
{: codeblock}


## Exemple NodeJS d'affichage des événements par jour
{: #viewing_events_info_api_node}

Il s'agit du code exemple que vous pouvez utiliser pour tester l'affichage du nombre d'événements par jour :

L'exemple suppose que le service {{site.data.keyword.cloudaccesstrailshort}} est mis à disposition dans la région Sud des Etats-Unis. 

```
var http = require("https")
var fs = require("fs")

var token = "{TOKEN}";

// ID de l'espace Cloud Foundry où le service {{site.data.keyword.cloudaccesstrailshort}} est mis à disposition.
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



