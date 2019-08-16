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

# イベント情報の表示
{: #viewing_events_info_api}

{{site.data.keyword.cloudaccesstrailshort}} API を使用して、{{site.data.keyword.cloudaccesstrailshort}} に保管されたイベントに関する情報を取得します。
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} は非推奨になりました。 2019 年 5 月 9 日以降、新しい {{site.data.keyword.cloudaccesstrailshort}} インスタンスをプロビジョンできません。 既存のプレミアム・プランのインスタンスは、2019 年 9 月 30 日までサポートされます。 {{site.data.keyword.cloud_notm}} アカウントのアクティビティーのモニタリングを続行するには、[{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) のインスタンスをプロビジョンします。
{: deprecated}

## cURL を使用したイベント数の取得
{: #viewing_events_info_api_records_per_day_curl}

特定の日のイベントに関する情報を表示するには、以下のステップを実行します。

1. UAA トークンを取得します。

    詳しくは、[UAA トークンの取得](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-auth_uaa#auth_uaa)を参照してください。

2. {{site.data.keyword.cloudaccesstrailshort}} に保管された特定の日のイベントの総数を取得するには、次の cURL コマンドを実行します。

    ```
    curl -X GET -H "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json"  ENDPOINT/v3/events   -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":false,"SearchTime":""}'
    ```
    {: codeblock}

    ここで、

    * *token* は、UAA トークンです。
    * *$spaceID* は、{{site.data.keyword.cloudaccesstrailshort}} をプロビジョンした Cloud Foundry スペースの UUID を表します。
    * *ENDPOINT* は、サービスのエントリー・ポイントを表します。 地域ごとに URL は異なります。 地域ごとのエンドポイントのリストを取得するには、[エンドポイント](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-ref_endpoints#api_endpoints)を参照してください。
    * *start* および *end* は、ダウンロードするイベントの期間を表します。 日付形式は YYYY-MM-DD です。 
    * *AtAccountLevel* は、イベントに関する情報の取得対象ドメインを示します。
    * *SearchTime* は、イベントに関する情報の取得対象時刻を示します。


例えば、米国南部地域のスペース・ドメイン内の特定の 1 日のイベントに関する情報を表示するには、次の cURL コマンドを実行します。

```
curl -X GET -H "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json"  https://activity-tracker.ng.bluemix.net/v3/events   -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":false,"SearchTime":""}'
```
{: codeblock}

例えば、米国南部地域の特定の 1 日のアカウント・イベントに関する情報を表示するには、次の cURL コマンドを実行します。

```
curl -X GET -H "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json"  https://activity-tracker.ng.bluemix.net/v3/events   -d '{"start":"2018-06-28","end":"2018-06-28","AtAccountLevel":true,"SearchTime":""}'
```
{: codeblock}

例えば、先週のイベントを表示するには、次の cURL コマンドを実行します。

```
curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json" --request GET --data "{\"start\":\"$(date -u -v-7d +%F)\", \"end\":\"$(date -u +%F)\" }" https://activity-tracker.ng.bluemix.net/v3/events
```
{: codeblock}


## 1 日当たりのイベント数を表示する NodeJS 例
{: #viewing_events_info_api_node}

以下は、1 日当たりのイベント数を表示する方法をテストするために使用できるサンプル・コードです。

この例では、{{site.data.keyword.cloudaccesstrailshort}} サービスが米国南部地域にプロビジョンされていると想定しています。 

```
var http = require("https")
var fs = require("fs")

var token = "{TOKEN}";

// {{site.data.keyword.cloudaccesstrailshort}} サービスがプロビジョンされている Cloud Foundry スペースのスペース ID
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



