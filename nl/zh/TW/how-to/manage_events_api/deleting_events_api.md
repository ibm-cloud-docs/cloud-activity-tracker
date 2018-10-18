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



# 刪除事件資訊
{: #deleting_events_api}

請使用 {{site.data.keyword.cloudaccesstrailshort}} API 來刪除儲存在 {{site.data.keyword.cloudaccesstrailshort}} 中的事件。
{:shortdesc}

**附註：**雖然您可以使用 API 呼叫手動刪除事件，但請考慮設定保留原則來自動刪除事件。如需相關資訊，請參閱[配置事件保留原則](/docs/services/cloud-activity-tracker/how-to/configuring_retention_policy.html#configuring_retention_policy)。

## 使用 cURL 刪除事件
{: #records_per_day_curl}

請完成下列步驟，以刪除空間網域中可用的事件：

1. 取得 UAA 記號。

    如需相關資訊，請參閱[取得 UAA 記號](/docs/services/cloud-activity-tracker/reference/auth_uaa.html#auth_uaa)。

2. 執行下列 cURL 指令，以刪除於特定日期儲存在 {{site.data.keyword.cloudaccesstrailshort}} 中的事件。

    ```
    curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json" -X DELETE  ENDPOINT/v3/events -d '{"start":"2018-06-24","end":"2018-06-24","AtAccountLevel":false,"SearchTime":""}'
    ```
    {: codeblock}

    其中

    * *token* 是 UAA 記號。
    * *spaceID* 代表已在其中佈建 {{site.data.keyword.cloudaccesstrailshort}} 之 Cloud Foundry 空間的 UUID。
    * *ENDPOINT* 代表服務的進入點。每一個地區都有不同的 URL。若要取得每個地區的端點清單，請參閱[端點](/docs/services/cloud-activity-tracker/reference/ref_endpoints.html#api_endpoints)。
    * *start* 和 *end* 代表您要下載事件的時間範圍。日期格式為 YYYY-MM-DD。 
    * *AtAccountLevel* 指出您要取得事件相關資訊的網域。
    * *SearchTime* 指出您要取得事件相關資訊的當天小時。


例如，若要刪除美國南部地區某個空間網域中特定日的事件，您可以執行下列 cURL 指令：

```
curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json" -X DELETE  https://activity-tracker.ng.bluemix.net/v3/events -d '{"start":"2018-06-24","end":"2018-06-24","AtAccountLevel":false,"SearchTime":""}'
```
{: codeblock}

例如，若要刪除空間網域中上週的事件，您可以執行下列 cURL 指令：

```
curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json" --request DELETE --data "{\"start\":\"$(date -u -v-7d +%F)\", \"end\":\"$(date -u -v-6d +%F)\" }" https://activity-tracker.ng.bluemix.net/v3/events
```
{: codeblock}


## 如何刪除事件的 NodeJS 範例
{: #node}

這是您可用來測試如何刪除事件的範例程式碼：

此範例假設在美國南部地區佈建了 {{site.data.keyword.cloudaccesstrailshort}} 服務。 

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
