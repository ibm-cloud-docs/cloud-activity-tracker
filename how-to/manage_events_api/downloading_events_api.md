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

# Downloading events
{: #downloading_events_api}

You can download {{site.data.keyword.cloudaccesstrailshort}} events by using the API.
{:shortdesc}


Consider the following information:

* You must have **developer** role in the space where the {{site.data.keyword.cloudaccesstrailshort}} service is provisioned.
* You cannot download more that 15 days per session.
* To download account logs, you set the **AtAccountLevel** parameter to *true* and request the download within the context of the space where the {{site.data.keyword.cloudaccesstrailshort}} service is provisioned.

To download events, you must complete the following steps:

1. Get a UAA token.
2. Create a session, where you specify the conditions that define the subset of events that you want to download.
3. Download the events into a local file.
4. Delete the session.



## Downloading events by using CURL
{: #downloading_events_api_curl}

Complete the following steps to download events into a local file:

1. Get a UAA token.

    For more information, see [Getting a UAA token](/docs/services/cloud-activity-tracker/reference/auth_uaa.html#auth_uaa).

2. Create a session, where you specify the conditions that define the subset of events that you want to download.

    ```
    curl -X POST -H "Content-Type: application/json" -H "X-Auth-Token: bearer $token" -H "X-Auth-Project-Id: $spaceID" ENDPOINT/v3/sessions -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":true,"SearchTime":""}'
    ```
    {: codeblock}

    where:
    
    * *token* represents the UAA token value that you obtained in a previous step.

    * *spaceID* represents the UUID of the Cloud Foundry space where you have {{site.data.keyword.cloudaccesstrailshort}} provisioned.

    * *ENDPOINT* represents the entry point to the service. Each region has a different URL. To get the list of endpoints per region, see [Endpoints](/docs/services/cloud-activity-tracker/reference/ref_endpoints.html#api_endpoints).

    * *start* and *end* represent a time range where you want to download events. The date format is *YYYY-MM-DD*. 

    * *AtAccountLevel* indicates if the events to download are in the account domain or in a space domain.
    
    * *SearchTime* indicates the hour of the day for which you want to download events.

    To create a session to download events from a space domain in the us-south region, set the parameter **AtAccountLevel** to *false*:

    ```
    curl -X POST -H "Content-Type: application/json" -H "X-Auth-Token: bearer $token" -H "X-Auth-Project-Id: $spaceID" https://activity-tracker.ng.bluemix.net/v3/sessions -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":false,"SearchTime":""}'
    ```
    {: codeblock}

    The output field **id** returns the session ID.
    
    For example, the output looks as follows:

    ```
    {"id":"b08cb740-ff85-404f-a6eb-ffec5374c7c6","space":"c1234567-6d55-4193-a9de-378620d6fab5","username":"xxx@ibm.com","create-time":"2018-06-28T12:50:36.012383445Z","access-time":"2018-06-28T12:50:36.012383445Z","date-range":{"Start":"2018-06-27","End":"2018-06-27"},"types":{"Type":"ActivityTracker","AtAccountLevel":true},"search-time":""}
    ```
    {: screen}
    
    For example, to create a session to download account events from the account domain in the us-south region, set the parameter **AtAccountLevel** to *true*:

    ```
    curl -X POST -H "Content-Type: application/json" -H "X-Auth-Token: bearer $token" -H "X-Auth-Project-Id: $spaceID" https://activity-tracker.ng.bluemix.net/v3/sessions -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":true,"SearchTime":""}'
    ```
    {: codeblock}

3. Download the events into a local file.

    ```
    curl -H "x-auth-token: bearer $token" -H "SESSIONID: $sessionID" -H "X-Auth-Project-Id: $spaceID" -H "accept: application/json" ENDPOINT/v3/events/download > FILENAME.gz
    ```
    {: codeblock}

    where *FILENAME* is the name of the local file where evenst will be downloaded.

    For example:

    ```
    curl -H "x-auth-token: bearer $token" -H "SESSIONID: $sessionID" -H "X-Auth-Project-Id: $spaceID" -H "accept: application/json" https://activity-tracker.ng.bluemix.net/v3/events/download > spaceXevents.gz
    ```
    {: codeblock}

4. Delete the session.

    ```
    curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer $token" -H "Accept:application/json" -H "X-Auth-Project-Id:$spaceId" --request DELETE https://activity-tracker.ng.bluemix.net/v3/sessions/$sessionId

    ```
    {: codeblock}


## NodeJS example of how to download events
{: #downloading_events_api_node}

This is sample code that you can use to test how to download events to a local file:

The example assumes that {{site.data.keyword.cloudaccesstrailshort}} service is provisioned in the US South region. 

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

