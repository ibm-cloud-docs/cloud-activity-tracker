---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-25"

keywords: IBM Cloud, Activity Tracker, delete event, API

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


# Deleting event information
{: #deleting_events_api}

Use the {{site.data.keyword.cloudaccesstrailshort}} API to delete events that are stored in {{site.data.keyword.cloudaccesstrailshort}}.
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} is deprecated. As of 9 May 2019, you cannot provision new {{site.data.keyword.cloudaccesstrailshort}} instances, and access to *Lite* plan instances will be removed. Existing premium plan instances are supported until 9 October 2019. Any instance that is still provisioned as of 9 October 2019 will be deleted. To continue monitoring the activity of your {{site.data.keyword.cloud_notm}} account, provision an instance of the [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}

**Note:** Although you can delete events manually by using the API call, consider setting the retention policy to delete events automatically. For more information, see [Configuring the events retention policy](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-configuring_retention_policy#configuring_retention_policy).

## Deleting events by using cURL
{: #deleting_events_api_records_per_day_curl}

Complete the following steps to delete events that are available in a space domain:

1. Get a UAA token.

    For more information, see [Getting a UAA token](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-auth_uaa#auth_uaa).

2. Run the following cURL command to delete events that are stored in {{site.data.keyword.cloudaccesstrailshort}} on a specific date.

    ```
    curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json" -X DELETE  ENDPOINT/v3/events -d '{"start":"2018-06-24","end":"2018-06-24","AtAccountLevel":false,"SearchTime":""}'
    ```
    {: codeblock}

    where

    * *token* is the UAA token.
    * *spaceID* represents the UUID of the Cloud Foundry space where you have {{site.data.keyword.cloudaccesstrailshort}} provisioned.
    * *ENDPOINT* represents the entry point to the service. Each region has a different URL. To get the list of endpoints per region, see [Endpoints](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-ref_endpoints#api_endpoints).
    * *start* and *end* represent a time range where you want to download events. The date format is YYYY-MM-DD. 
    * *AtAccountLevel* indicates the domain where you want to get information about the events.
    * *SearchTime* indicates the hour of the day for which you want information about the events.


For example, to delete events on a specific day in a space domain in the US South region, you can run the following cURL command:

```
curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json" -X DELETE  https://activity-tracker.ng.bluemix.net/v3/events -d '{"start":"2018-06-24","end":"2018-06-24","AtAccountLevel":false,"SearchTime":""}'
```
{: codeblock}

For example, to delete events in  a space domain for the last week, you can run the following cURL command:

```
curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json" --request DELETE --data "{\"start\":\"$(date -u -v-7d +%F)\", \"end\":\"$(date -u -v-6d +%F)\" }" https://activity-tracker.ng.bluemix.net/v3/events
```
{: codeblock}


## NodeJS example of how to delete events
{: #deleting_events_api_node}

This is sample code that you can use to test how to delete events:

The example assumes that {{site.data.keyword.cloudaccesstrailshort}} service is provisioned in the US South region. 

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


