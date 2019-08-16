---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, download events, API

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

# 下载事件
{: #downloading_events_api}

您可以使用 API 下载 {{site.data.keyword.cloudaccesstrailshort}} 事件。
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} 已被弃用。从 2019 年 5 月 9 日开始，您无法供应新的 {{site.data.keyword.cloudaccesstrailshort}} 实例。对现有高端套餐实例的支持会持续到 2019 年 9 月 30 日。要继续监视 {{site.data.keyword.cloud_notm}} 帐户的活动，请供应 [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) 的实例。
{: deprecated}

请考虑以下信息：

* 在您供应 {{site.data.keyword.cloudaccesstrailshort}} 服务的空间中，您必须拥有**开发者**角色。
* 对于每个会话，无法下载超过 15 天的内容。
* 要下载帐户日志，可以将 **AtAccountLevel** 参数设置为 *true*，并且在您供应 {{site.data.keyword.cloudaccesstrailshort}} 服务的空间的上下文中请求下载。

要下载事件，必须完成以下步骤：

1. 获取 UAA 令牌。
2. 创建一个会话，在其中指定用于定义要下载哪一部分事件的条件。
3. 将事件下载到本地文件中。
4. 删除该会话。



## 使用 CURL 下载事件
{: #downloading_events_api_curl}

要将事件下载到本地文件中，请完成以下步骤：

1. 获取 UAA 令牌。

    有关更多信息，请参阅[获取 UAA 令牌](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-auth_uaa#auth_uaa)。

2. 创建一个会话，在其中指定用于定义要下载哪一部分事件的条件。

    ```
    curl -X POST -H "Content-Type: application/json" -H "X-Auth-Token: bearer $token" -H "X-Auth-Project-Id: $spaceID" ENDPOINT/v3/sessions -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":true,"SearchTime":""}'
    ```
    {: codeblock}

    其中：
    
    *token* 表示您在上一步中获取的 UAA 令牌值。

    *spaceID* 表示您供应 {{site.data.keyword.cloudaccesstrailshort}} 的 Cloud Foundry 空间的 UUID。

    *ENDPOINT* 表示服务的入口点。每个区域都有不同的 URL。要获取每个区域的端点的列表，请参阅[端点](/docs/services/cloud-activity-tracker/reference/ref_endpoints.html#api_endpoints)。

    *start* 和 *end* 表示要下载哪一时间范围的事件。日期格式为 *YYYY-MM-DD*。 

    *AtAccountLevel* 指示要下载帐户域中的事件，还是空间域中的事件。
    
    *SearchTime* 指示要下载哪一时刻的事件。

    要创建会话以从美国南部区域的空间域中下载事件，请将 **AtAccountLevel** 参数设置为 *false*：

    ```
    curl -X POST -H "Content-Type: application/json" -H "X-Auth-Token: bearer $token" -H "X-Auth-Project-Id: $spaceID" https://activity-tracker.ng.bluemix.net/v3/sessions -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":false,"SearchTime":""}'
    ```
    {: codeblock}

    输出字段 **id** 会返回会话标识。
    
    例如，输出如下所示：

    ```
    {"id":"b08cb740-ff85-404f-a6eb-ffec5374c7c6","space":"c1234567-6d55-4193-a9de-378620d6fab5","username":"xxx@ibm.com","create-time":"2018-06-28T12:50:36.012383445Z","access-time":"2018-06-28T12:50:36.012383445Z","date-range":{"Start":"2018-06-27","End":"2018-06-27"},"types":{"Type":"ActivityTracker","AtAccountLevel":true},"search-time":""}
    ```
    {: screen}
    
    例如，要创建会话以从美国南部区域的帐户域中下载帐户事件，请将 **AtAccountLevel** 参数设置为 *true*：

    ```
    curl -X POST -H "Content-Type: application/json" -H "X-Auth-Token: bearer $token" -H "X-Auth-Project-Id: $spaceID" https://activity-tracker.ng.bluemix.net/v3/sessions -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":true,"SearchTime":""}'
    ```
    {: codeblock}

3. 将事件下载到本地文件中。

    ```
    curl -H "x-auth-token: bearer $token" -H "SESSIONID: $sessionID" -H "X-Auth-Project-Id: $spaceID" -H "accept: application/json" ENDPOINT/v3/events/download > FILENAME.gz
    ```
    {: codeblock}

    其中，*FILENAME* 是要将事件下载到其中的本地文件的名称。

    例如：

    ```
    curl -H "x-auth-token: bearer $token" -H "SESSIONID: $sessionID" -H "X-Auth-Project-Id: $spaceID" -H "accept: application/json" https://activity-tracker.ng.bluemix.net/v3/events/download > spaceXevents.gz
    ```
    {: codeblock}

4. 删除该会话。

    ```
    curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer $token" -H "Accept:application/json" -H "X-Auth-Project-Id:$spaceId" --request DELETE https://activity-tracker.ng.bluemix.net/v3/sessions/$sessionId

    ```
    {: codeblock}


## 如何下载事件的 NodeJS 示例
{: #downloading_events_api_node}

以下是样本代码，可用于测试如何将事件下载到本地文件中：

此示例假定 {{site.data.keyword.cloudaccesstrailshort}} 服务是在美国南部区域供应的。 

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

