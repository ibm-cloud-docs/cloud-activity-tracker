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



# 檢視事件資訊
{: #viewing_events_info_api}

請使用 {{site.data.keyword.cloudaccesstrailshort}} API，以取得儲存在 {{site.data.keyword.cloudaccesstrailshort}} 中之事件的相關資訊。
{:shortdesc}


## 使用 cURL 取得事件數
{: #viewing_events_info_api_records_per_day_curl}

請完成下列步驟，以檢視特定日期事件的相關資訊：

1. 取得 UAA 記號。

    如需相關資訊，請參閱[取得 UAA 記號](/docs/services/cloud-activity-tracker/reference/auth_uaa.html#auth_uaa)。

2. 執行下列 cURL 指令，以取得於特定日期儲存在 {{site.data.keyword.cloudaccesstrailshort}} 中之事件的總數。

    ```
    curl -X GET -H "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json"  ENDPOINT/v3/events   -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":false,"SearchTime":""}'
    ```
    {: codeblock}

    其中

    * *token* 是 UAA 記號。
    * *$spaceID* 代表已在其中佈建 {{site.data.keyword.cloudaccesstrailshort}} 之 Cloud Foundry 空間的 UUID。
    * *ENDPOINT* 代表服務的進入點。每一個地區都有不同的 URL。若要取得每個地區的端點清單，請參閱[端點](/docs/services/cloud-activity-tracker/reference/ref_endpoints.html#api_endpoints)。
    * *start* 和 *end* 代表您要下載事件的時間範圍。日期格式為 YYYY-MM-DD。 
    * *AtAccountLevel* 指出您要取得事件相關資訊的網域。
    * *SearchTime* 指出您要取得事件相關資訊的當天小時。


例如，若要取得美國南部地區某個空間網域中特定日的事件相關資訊，您可以執行下列 cURL 指令：

```
curl -X GET -H "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json"  https://activity-tracker.ng.bluemix.net/v3/events   -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":false,"SearchTime":""}'
```
{: codeblock}

例如，若要查看美國南部地區中特定日的帳戶事件相關資訊，您可以執行下列 cURL 指令：

```
curl -X GET -H "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json"  https://activity-tracker.ng.bluemix.net/v3/events   -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":true,"SearchTime":""}'
```
{: codeblock}

例如，若要查看上週的事件，您可以執行下列 cURL 指令：

```
curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json" --request GET --data "{\"start\":\"$(date -u -v-7d +%F)\", \"end\":\"$(date -u +%F)\" }" https://activity-tracker.ng.bluemix.net/v3/events
```
{: codeblock}


## 如何檢視每天事件數的 NodeJS 範例
{: #viewing_events_info_api_node}

這是您可用來測試如何檢視每天事件數的範例程式碼：

此範例假設在美國南部地區佈建了 {{site.data.keyword.cloudaccesstrailshort}} 服務。 

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



