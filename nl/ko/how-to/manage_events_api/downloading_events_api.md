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

# 이벤트 다운로드
{: #downloading_events_api}

API를 사용하여 {{site.data.keyword.cloudaccesstrailshort}} 이벤트를 다운로드할 수 있습니다.
{:shortdesc}


다음 정보를 고려하십시오. 

* {{site.data.keyword.cloudaccesstrailshort}} 서비스가 프로비저닝된 영역의 **개발자** 역할을 갖고 있어야 합니다. 
* 세션당 15일까지만 다운로드할 수 있습니다. 
* 계정 로그를 다운로드하려면 **AtAccountLevel** 매개변수를 *true*로 설정하고 {{site.data.keyword.cloudaccesstrailshort}} 서비스가 프로비저닝된 영역의 컨텍스트 내에서 다운로드를 요청하십시오. 

이벤트를 다운로드하려면 다음 단계를 완료해야 합니다. 

1. UAA 토큰을 가져오십시오. 
2. 다운로드할 이벤트의 서브세트를 정의하는 조건을 지정하는 세션을 작성하십시오. 
3. 이벤트를 로컬 파일로 다운로드하십시오. 
4. 세션을 삭제하십시오. 



## cURL을 사용하여 이벤트 다운로드
{: #curl}

이벤트를 로컬 파일로 다운로드하려면 다음 단계를 완료하십시오. 

1. UAA 토큰을 가져오십시오. 

    자세한 정보는 [UAA 토큰 가져오기](/docs/services/cloud-activity-tracker/reference/auth_uaa.html#auth_uaa)를 참조하십시오. 

2. 다운로드할 이벤트의 서브세트를 정의하는 조건을 지정하는 세션을 작성하십시오. 

    ```
    curl -X POST -H "Content-Type: application/json" -H "X-Auth-Token: bearer $token" -H "X-Auth-Project-Id: $spaceID" ENDPOINT/v3/sessions -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":true,"SearchTime":""}'
    ```
    {: codeblock}

    여기서,
    
    * *token*은 이전 단계에서 획득한 UAA 토큰 값을 나타냅니다. 
    * *spaceID*는 {{site.data.keyword.cloudaccesstrailshort}}이 프로비저닝된 Cloud Foundry 영역의 UUID입니다. 
    * *ENDPOINT*는 서비스의 시작점을 나타냅니다. 각 지역에는 서로 다른 URL이 있습니다. 지역별 엔드포인트의 목록을 얻으려면 [엔드포인트](/docs/services/cloud-activity-tracker/reference/ref_endpoints.html#api_endpoints)를 참조하십시오. 
    * *start* 및 *end*는 이벤트를 다운로드할 시간 범위를 나타냅니다. 날짜 형식은 *YYYY-MM-DD*입니다.  
    * *AtAccountLevel*은 다운로드할 이벤트가 계정 도메인에 있는지, 또는 영역 도메인에 있는지 나타냅니다. 
    * *SearchTime*은 이벤트를 다운로드할 시간을 나타냅니다. 

    미국 남부 지역의 영역 도메인에서 이벤트를 다운로드하기 위한 세션을 작성하려면 매개변수 **AtAccountLevel**을 *false*로 설정하십시오. 

    ```
    curl -X POST -H "Content-Type: application/json" -H "X-Auth-Token: bearer $token" -H "X-Auth-Project-Id: $spaceID" https://activity-tracker.ng.bluemix.net/v3/sessions -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":false,"SearchTime":""}'
    ```
    {: codeblock}

    출력 필드 **id**는 세션 ID를 리턴합니다. 
    
    예를 들면, 출력은 다음과 같습니다. 

    ```
    {"id":"b08cb740-ff85-404f-a6eb-ffec5374c7c6","space":"c1234567-6d55-4193-a9de-378620d6fab5","username":"xxx@ibm.com","create-time":"2018-06-28T12:50:36.012383445Z","access-time":"2018-06-28T12:50:36.012383445Z","date-range":{"Start":"2018-06-27","End":"2018-06-27"},"types":{"Type":"ActivityTracker","AtAccountLevel":true},"search-time":""}
    ```
    {: screen}
    
    예를 들어, 미국 남부 지역의 계정 도메인에서 계정 이벤트를 다운로드하기 위한 세션을 작성하려면 매개변수 **AtAccountLevel**을 *true*로 설정하십시오. 

    ```
    curl -X POST -H "Content-Type: application/json" -H "X-Auth-Token: bearer $token" -H "X-Auth-Project-Id: $spaceID" https://activity-tracker.ng.bluemix.net/v3/sessions -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":true,"SearchTime":""}'
    ```
    {: codeblock}

3. 이벤트를 로컬 파일로 다운로드하십시오. 

    ```
    curl -H "x-auth-token: bearer $token" -H "SESSIONID: $sessionID" -H "X-Auth-Project-Id: $spaceID" -H "accept: application/json" ENDPOINT/v3/events/download > FILENAME.gz
    ```
    {: codeblock}

    여기서 *FILENAME*은 이벤트가 다운로드될 로컬 파일의 이름입니다. 

    예를 들면, 다음과 같습니다.

    ```
    curl -H "x-auth-token: bearer $token" -H "SESSIONID: $sessionID" -H "X-Auth-Project-Id: $spaceID" -H "accept: application/json" https://activity-tracker.ng.bluemix.net/v3/events/download > spaceXevents.gz
    ```
    {: codeblock}

4. 세션을 삭제하십시오. 

    ```
    curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer $token" -H "Accept:application/json" -H "X-Auth-Project-Id:$spaceId" --request DELETE https://activity-tracker.ng.bluemix.net/v3/sessions/$sessionId

    ```
    {: codeblock}


## 이벤트 다운로드 방법에 대한 NodeJS 예
{: #node}

이는 이벤트를 로컬 파일로 다운로드하는 방법을 테스트하는 데 사용할 수 있는 샘플 코드입니다. 

이 예에서는 {{site.data.keyword.cloudaccesstrailshort}} 서비스가 미국 남부 지역에서 프로비저닝되었다고 가정합니다.  

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

