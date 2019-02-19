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



# Viewing event information
{: #viewing_events_info_api}

Use the {{site.data.keyword.cloudaccesstrailshort}} API to get information about events that are stored in {{site.data.keyword.cloudaccesstrailshort}}.
{:shortdesc}


## Getting the number of events by using cURL
{: #viewing_events_info_api_records_per_day_curl}

Complete the following steps to view information about the events on a specific date:

1. Get a UAA token.

    For more information, see [Getting a UAA token](/docs/services/cloud-activity-tracker/reference/auth_uaa.html#auth_uaa).

2. Run the following cURL command to get the total number of events that are stored in {{site.data.keyword.cloudaccesstrailshort}} on a specific date.

    ```
    curl -X GET -H "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json"  ENDPOINT/v3/events   -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":false,"SearchTime":""}'
    ```
    {: codeblock}

    where

    * *token* is the UAA token.
    * *$spaceID* represents the UUID of the Cloud Foundry space where you have {{site.data.keyword.cloudaccesstrailshort}} provisioned.
    * *ENDPOINT* represents the entry point to the service. Each region has a different URL. To get the list of endpoints per region, see [Endpoints](/docs/services/cloud-activity-tracker/reference/ref_endpoints.html#api_endpoints).
    * *start* and *end* represent a time range where you want to download events. The date format is YYYY-MM-DD. 
    * *AtAccountLevel* indicates the domain where you want to get information about the events.
    * *SearchTime* indicates the hour of the day for which you want information about the events.


For example, to see get information about events on a specific day in a space domain in the US South region, you can run the following cURL command:

```
curl -X GET -H "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json"  https://activity-tracker.ng.bluemix.net/v3/events   -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":false,"SearchTime":""}'
```
{: codeblock}

For example, to see get information about the account events on a specific day in the US South region, you can run the following cURL command:

```
curl -X GET -H "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json"  https://activity-tracker.ng.bluemix.net/v3/events   -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":true,"SearchTime":""}'
```
{: codeblock}

For example, to see events for the last week, you can tun the following cURL command:

```
curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json" --request GET --data "{\"start\":\"$(date -u -v-7d +%F)\", \"end\":\"$(date -u +%F)\" }" https://activity-tracker.ng.bluemix.net/v3/events
```
{: codeblock}


## NodeJS example of how to view events per day
{: #viewing_events_info_api_node}

This is sample code that you can use to test how to view the number of events per day:

The example assumes that {{site.data.keyword.cloudaccesstrailshort}} service is provisioned in the US South region. 

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



