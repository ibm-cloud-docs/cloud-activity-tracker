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

# イベントのダウンロード
{: #downloading_events_api}

API を使用して {{site.data.keyword.cloudaccesstrailshort}} イベントをダウンロードできます。
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} は非推奨になりました。2019 年 5 月 9 日以降、新しい {{site.data.keyword.cloudaccesstrailshort}} インスタンスをプロビジョンできません。既存のプレミアム・プランのインスタンスは、2019 年 9 月 30 日までサポートされます。{{site.data.keyword.cloud_notm}} アカウントのアクティビティーのモニタリングを続行するには、[{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) のインスタンスをプロビジョンします。
{: deprecated}

以下の事項を考慮してください。

* {{site.data.keyword.cloudaccesstrailshort}} サービスがプロビジョンされたスペースで**開発者**役割を持っている必要があります。
* セッション当たり 15 日間を超えるイベントをダウンロードすることはできません。
* アカウント・ログをダウンロードするには、**AtAccountLevel** パラメーターを *true* に設定し、{{site.data.keyword.cloudaccesstrailshort}} サービスがプロビジョンされたスペースのコンテキスト内でダウンロードを要求する必要があります。

イベントをダウンロードするには、以下のステップを実行する必要があります。

1. UAA トークンを取得します。
2. セッションを作成し、ダウンロードするイベントのサブセットを定義する条件を指定します。
3. イベントをローカル・ファイルにダウンロードします。
4. セッションを削除します。



## cURL を使用したイベントのダウンロード
{: #downloading_events_api_curl}

イベントをローカル・ファイルにダウンロードするには、以下のステップを実行します。

1. UAA トークンを取得します。

    詳しくは、[UAA トークンの取得](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-auth_uaa#auth_uaa)を参照してください。

2. セッションを作成し、ダウンロードするイベントのサブセットを定義する条件を指定します。

    ```
    curl -X POST -H "Content-Type: application/json" -H "X-Auth-Token: bearer $token" -H "X-Auth-Project-Id: $spaceID" ENDPOINT/v3/sessions -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":true,"SearchTime":""}'
    ```
    {: codeblock}

    各部の意味は次のとおりです。
    
    *token* は、前のステップで取得した UAA トークンを表します。

    *spaceID* は、{{site.data.keyword.cloudaccesstrailshort}} をプロビジョンした Cloud Foundry スペースの UUID を表します。

    *ENDPOINT* は、サービスのエントリー・ポイントを表します。 地域ごとに URL は異なります。 地域ごとのエンドポイントのリストを取得するには、[エンドポイント](/docs/services/cloud-activity-tracker/reference/ref_endpoints.html#api_endpoints)を参照してください。

    *start* および *end* は、ダウンロードするイベントの期間を表します。 日付形式は *YYYY-MM-DD* です。 

    *AtAccountLevel* は、ダウンロードするイベントが、アカウント・ドメイン内にあるのか、スペース・ドメイン内にあるのかを示します。
    
    *SearchTime* は、ダウンロードするイベントの時刻を示します。

    米国南部地域のスペース・ドメインからイベントをダウンロードするためのセッションを作成するには、パラメーター **AtAccountLevel** を *false* に設定します。

    ```
    curl -X POST -H "Content-Type: application/json" -H "X-Auth-Token: bearer $token" -H "X-Auth-Project-Id: $spaceID" https://activity-tracker.ng.bluemix.net/v3/sessions -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":false,"SearchTime":""}'
    ```
    {: codeblock}

    出力フィールド **id** は、セッション ID を返します。
    
    例えば、出力は以下のようになります。

    ```
    {"id":"b08cb740-ff85-404f-a6eb-ffec5374c7c6","space":"c1234567-6d55-4193-a9de-378620d6fab5","username":"xxx@ibm.com","create-time":"2018-06-28T12:50:36.012383445Z","access-time":"2018-06-28T12:50:36.012383445Z","date-range":{"Start":"2018-06-27","End":"2018-06-27"},"types":{"Type":"ActivityTracker","AtAccountLevel":true},"search-time":""}
    ```
    {: screen}
    
    例えば、米国南部地域のアカウント・ドメインからアカウント・イベントをダウンロードするためのセッションを作成するには、パラメーター **AtAccountLevel** を *true* に設定します。

    ```
    curl -X POST -H "Content-Type: application/json" -H "X-Auth-Token: bearer $token" -H "X-Auth-Project-Id: $spaceID" https://activity-tracker.ng.bluemix.net/v3/sessions -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":true,"SearchTime":""}'
    ```
    {: codeblock}

3. イベントをローカル・ファイルにダウンロードします。

    ```
    curl -H "x-auth-token: bearer $token" -H "SESSIONID: $sessionID" -H "X-Auth-Project-Id: $spaceID" -H "accept: application/json" ENDPOINT/v3/events/download > FILENAME.gz
    ```
    {: codeblock}

    ここで、*FILENAME* は、イベントがダウンロードされるローカル・ファイルの名前です。

    以下に例を示します。

    ```
    curl -H "x-auth-token: bearer $token" -H "SESSIONID: $sessionID" -H "X-Auth-Project-Id: $spaceID" -H "accept: application/json" https://activity-tracker.ng.bluemix.net/v3/events/download > spaceXevents.gz
    ```
    {: codeblock}

4. セッションを削除します。

    ```
    curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer $token" -H "Accept:application/json" -H "X-Auth-Project-Id:$spaceId" --request DELETE https://activity-tracker.ng.bluemix.net/v3/sessions/$sessionId

    ```
    {: codeblock}


## NodeJS でのイベントのダウンロードの例
{: #downloading_events_api_node}

以下は、イベントをローカル・ファイルにダウンロードする方法をテストするために使用できるサンプル・コードです。

この例では、{{site.data.keyword.cloudaccesstrailshort}} サービスが米国南部地域にプロビジョンされていると想定しています。 

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
            ]chunks.push(chunk);
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
            ]chunks.push(chunk);
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

