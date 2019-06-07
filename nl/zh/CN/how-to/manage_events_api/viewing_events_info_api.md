---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

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
{:deprecated: .deprecated}

# 查看事件信息
{: #viewing_events_info_api}

使用 {{site.data.keyword.cloudaccesstrailshort}} API 可获取 {{site.data.keyword.cloudaccesstrailshort}} 中存储的事件的相关信息。
{:shortdesc}

不推荐使用 {{site.data.keyword.cloudaccesstrailfull}}。从 2019 年 5 月 9 日开始，无法供应新的 {{site.data.keyword.cloudaccesstrailshort}} 实例。对现有高端套餐实例的支持会持续到 2019 年 9 月 30 日。要继续监视 {{site.data.keyword.cloud_notm}} 帐户的活动，请供应 [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) 的实例。
{: deprecated}

## 使用 cURL 来获取事件数
{: #viewing_events_info_api_records_per_day_curl}

要查看特定日期的事件的相关信息，请完成以下步骤：

1. 获取 UAA 令牌。

    有关更多信息，请参阅[获取 UAA 令牌](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-auth_uaa#auth_uaa)。

2. 运行以下 cURL 命令，以获取在特定日期存储在 {{site.data.keyword.cloudaccesstrailshort}} 中的事件总数。

    ```
    curl -X GET -H "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json"  ENDPOINT/v3/events   -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":false,"SearchTime":""}'
    ```
    {: codeblock}

    其中

    * *token* 是 UAA 令牌。
    * *$spaceID* 表示您供应 {{site.data.keyword.cloudaccesstrailshort}} 的 Cloud Foundry 空间的 UUID。
    * *ENDPOINT* 表示服务的入口点。每个区域都有不同的 URL。要获取每个区域的端点的列表，请参阅[端点](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-ref_endpoints#api_endpoints)。
    * *start* 和 *end* 表示要下载哪一时间范围的事件。日期格式为 YYYY-MM-DD。 
    * *AtAccountLevel* 指示要获取哪一域中事件的相关信息。
    * *SearchTime* 指示要获取哪一时刻的事件的相关信息。


例如，要查看美国南部区域的空间域中特定一天的事件相关信息，可以运行以下 cURL 命令：

```
curl -X GET -H "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json"  https://activity-tracker.ng.bluemix.net/v3/events   -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":false,"SearchTime":""}'
```
{: codeblock}

例如，要查看美国南部区域中特定一天的帐户事件相关信息，可以运行以下 cURL 命令：

```
curl -X GET -H "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json"  https://activity-tracker.ng.bluemix.net/v3/events   -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":true,"SearchTime":""}'
```
{: codeblock}

例如，要查看上一周的事件，可以运行以下 cURL 命令：

```
curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json" --request GET --data "{\"start\":\"$(date -u -v-7d +%F)\", \"end\":\"$(date -u +%F)\" }" https://activity-tracker.ng.bluemix.net/v3/events
```
{: codeblock}


## 如何查看每天事件的 NodeJS 示例
{: #viewing_events_info_api_node}

以下是样本代码，可用于测试如何查看每天的事件数：

此示例假定 {{site.data.keyword.cloudaccesstrailshort}} 服务是在美国南部区域供应的。 

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



