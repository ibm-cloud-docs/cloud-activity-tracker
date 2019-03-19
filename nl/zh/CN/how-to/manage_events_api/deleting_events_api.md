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



# 删除事件信息
{: #deleting_events_api}

使用 {{site.data.keyword.cloudaccesstrailshort}} API 可删除 {{site.data.keyword.cloudaccesstrailshort}} 中存储的事件。
{:shortdesc}

**注：**虽然可以使用 API 调用手动删除事件，但请考虑将保留时间策略设置为自动删除事件。有关更多信息，请参阅
[配置事件保留时间策略](/docs/services/cloud-activity-tracker/how-to/configuring_retention_policy.html#configuring_retention_policy)。

## 使用 cURL 删除事件
{: #deleting_events_api_records_per_day_curl}

要删除空间域中可用的事件，请完成以下步骤：

1. 获取 UAA 令牌。

    有关更多信息，请参阅[获取 UAA 令牌](/docs/services/cloud-activity-tracker/reference/auth_uaa.html#auth_uaa)。

2. 运行以下 cURL 命令，以删除在特定日期存储在 {{site.data.keyword.cloudaccesstrailshort}} 中的事件。

    ```
    curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json" -X DELETE  ENDPOINT/v3/events -d '{"start":"2018-06-24","end":"2018-06-24","AtAccountLevel":false,"SearchTime":""}'
    ```
    {: codeblock}

    其中


    * *token* 是 UAA 令牌。
    * *spaceID* 表示您供应 {{site.data.keyword.cloudaccesstrailshort}} 的 Cloud Foundry 空间的 UUID。
    * *ENDPOINT* 表示服务的入口点。每个区域都有不同的 URL。要获取每个区域的端点的列表，请参阅[端点](/docs/services/cloud-activity-tracker/reference/ref_endpoints.html#api_endpoints)。
    * *start* 和 *end* 表示要下载哪一时间范围的事件。日期格式为 YYYY-MM-DD。 
    * *AtAccountLevel* 指示要获取哪一域中事件的相关信息。
    * *SearchTime* 指示要获取哪一时刻的事件的相关信息。


例如，要删除美国南部区域的空间域中特定一天的事件，可以运行以下 cURL 命令：

```
curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json" -X DELETE  https://activity-tracker.ng.bluemix.net/v3/events -d '{"start":"2018-06-24","end":"2018-06-24","AtAccountLevel":false,"SearchTime":""}'
```
{: codeblock}

例如，要删除空间域中上一周的事件，可以运行以下 cURL 命令：

```
curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json" --request DELETE --data "{\"start\":\"$(date -u -v-7d +%F)\", \"end\":\"$(date -u -v-6d +%F)\" }" https://activity-tracker.ng.bluemix.net/v3/events
```
{: codeblock}


## 如何删除事件的 NodeJS 示例
{: #deleting_events_api_node}

以下是样本代码，可用于测试如何删除事件：

此示例假定 {{site.data.keyword.cloudaccesstrailshort}} 服务是在美国南部区域供应的。 

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
