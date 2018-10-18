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



# 이벤트 정보 삭제
{: #deleting_events_api}

{{site.data.keyword.cloudaccesstrailshort}}에 저장된 이벤트를 삭제하려면 {{site.data.keyword.cloudaccesstrailshort}} API를 사용하십시오.
{:shortdesc}

**참고:** API 호출을 사용하여 이벤트를 수동으로 삭제할 수도 있지만, 보존 정책을 설정하여 이벤트를 자동으로 삭제하는 것을 고려하십시오. 자세한 정보는 [이벤트 보존 정책 구성](/docs/services/cloud-activity-tracker/how-to/configuring_retention_policy.html#configuring_retention_policy)을 참조하십시오. 

## cURL을 사용하여 이벤트 삭제
{: #records_per_day_curl}

영역 도메인에 있는 이벤트를 삭제하려면 다음 단계를 완료하십시오. 

1. UAA 토큰을 가져오십시오. 

    자세한 정보는 [UAA 토큰 가져오기](/docs/services/cloud-activity-tracker/reference/auth_uaa.html#auth_uaa)를 참조하십시오. 

2. 다음 cURL 명령을 실행하여 특정 날짜에 {{site.data.keyword.cloudaccesstrailshort}}에 저장된 이벤트를 삭제하십시오. 

    ```
    curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json" -X DELETE  ENDPOINT/v3/events -d '{"start":"2018-06-24","end":"2018-06-24","AtAccountLevel":false,"SearchTime":""}'
    ```
    {: codeblock}

    여기서,

    * *token*은 UAA 토큰입니다. 
    * *spaceID*는 {{site.data.keyword.cloudaccesstrailshort}}이 프로비저닝된 Cloud Foundry 영역의 UUID입니다. 
    * *ENDPOINT*는 서비스의 시작점을 나타냅니다. 각 지역에는 서로 다른 URL이 있습니다. 지역별 엔드포인트의 목록을 얻으려면 [엔드포인트](/docs/services/cloud-activity-tracker/reference/ref_endpoints.html#api_endpoints)를 참조하십시오. 
    * *start* 및 *end*는 이벤트를 다운로드할 시간 범위를 나타냅니다. 날짜 형식은 YYYY-MM-DD입니다.  
    * *AtAccountLevel*은 이벤트에 대한 정보를 가져올 도메인을 나타냅니다. 
    * *SearchTime*은 이벤트에 대한 정보를 얻을 시간을 나타냅니다. 


예를 들어, 미국 남부 지역의 영역 도메인에서 특정 일의 이벤트를 삭제하려는 경우에는 다음 cURL 명령을 실행할 수 있습니다. 

```
curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json" -X DELETE  https://activity-tracker.ng.bluemix.net/v3/events -d '{"start":"2018-06-24","end":"2018-06-24","AtAccountLevel":false,"SearchTime":""}'
```
{: codeblock}

예를 들어, 영역 도메인에서 지난 주의 이벤트를 삭제하려는 경우에는 다음 cURL 명령을 실행할 수 있습니다. 

```
curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json" --request DELETE --data "{\"start\":\"$(date -u -v-7d +%F)\", \"end\":\"$(date -u -v-6d +%F)\" }" https://activity-tracker.ng.bluemix.net/v3/events
```
{: codeblock}


## 이벤트 삭제 방법에 대한 NodeJS 예
{: #node}

이는 이벤트 삭제 방법을 테스트하는 데 사용할 수 있는 샘플 코드입니다. 

이 예에서는 {{site.data.keyword.cloudaccesstrailshort}} 서비스가 미국 남부 지역에서 프로비저닝되었다고 가정합니다.  

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
