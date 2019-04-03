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


# 이벤트 정보 보기
{: #viewing_events_info_api}

{{site.data.keyword.cloudaccesstrailshort}}에 저장된 이벤트에 대한 정보를 가져오려면 {{site.data.keyword.cloudaccesstrailshort}} API를 사용하십시오.
{:shortdesc}


## cURL을 사용하여 이벤트 수 가져오기
{: #viewing_events_info_api_records_per_day_curl}

특정 날짜의 이벤트에 대한 정보를 보려면 다음 단계를 완료하십시오.

1. UAA 토큰을 가져오십시오.

    자세한 정보는 [UAA 토큰 가져오기](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-auth_uaa#auth_uaa)를 참조하십시오.

2. 다음 cURL 명령을 실행하여 특정 날짜에 {{site.data.keyword.cloudaccesstrailshort}}에 저장된 총 이벤트 수를 가져오십시오.

    ```
    curl -X GET -H "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json"  ENDPOINT/v3/events   -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":false,"SearchTime":""}'
    ```
    {: codeblock}

    여기서,

    * *token*은 UAA 토큰입니다.
    * *spaceID*는 {{site.data.keyword.cloudaccesstrailshort}}이 프로비저닝된 Cloud Foundry 영역의 UUID입니다.
    * *ENDPOINT*는 서비스의 시작점을 나타냅니다. 각 지역에는 서로 다른 URL이 있습니다. 지역별 엔드포인트의 목록을 얻으려면 [엔드포인트](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-ref_endpoints#api_endpoints)를 참조하십시오.
    * *start* 및 *end*는 이벤트를 다운로드할 시간 범위를 나타냅니다. 날짜 형식은 YYYY-MM-DD입니다. 
    * *AtAccountLevel*은 이벤트에 대한 정보를 가져올 도메인을 나타냅니다.
    * *SearchTime*은 이벤트에 대한 정보를 얻을 시간을 나타냅니다.


예를 들어, 미국 남부 지역의 영역 도메인에서 특정 일의 이벤트에 대한 정보를 가져오려는 경우에는 다음 cURL 명령을 실행할 수 있습니다.

```
curl -X GET -H "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json"  https://activity-tracker.ng.bluemix.net/v3/events   -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":false,"SearchTime":""}'
```
{: codeblock}

예를 들어, 미국 남부 지역에서 특정 일의 계정 이벤트에 대한 정보를 가져오려는 경우에는 다음 cURL 명령을 실행할 수 있습니다.

```
curl -X GET -H "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json"  https://activity-tracker.ng.bluemix.net/v3/events   -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":true,"SearchTime":""}'
```
{: codeblock}

예를 들어, 지난 주의 이벤트를 보려는 경우에는 다음 cURL 명령을 실행할 수 있습니다.

```
curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json" --request GET --data "{\"start\":\"$(date -u -v-7d +%F)\", \"end\":\"$(date -u +%F)\" }" https://activity-tracker.ng.bluemix.net/v3/events
```
{: codeblock}


## 일별 이벤트를 보는 방법에 대한 NodeJS 예
{: #viewing_events_info_api_node}

이는 일별 이벤트 수를 보는 방법을 테스트하는 데 사용할 수 있는 샘플 코드입니다.

이 예에서는 {{site.data.keyword.cloudaccesstrailshort}} 서비스가 미국 남부 지역에서 프로비저닝되었다고 가정합니다. 

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



