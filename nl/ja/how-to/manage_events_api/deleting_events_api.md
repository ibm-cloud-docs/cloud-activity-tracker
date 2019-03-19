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



# イベント情報の削除
{: #deleting_events_api}

{{site.data.keyword.cloudaccesstrailshort}} API を使用して、{{site.data.keyword.cloudaccesstrailshort}} に保管されたイベントを削除します。
{:shortdesc}

**注:** API 呼び出しを使用してイベントを手動で削除することが可能ですが、イベントを自動的に削除する保存ポリシーを設定することを検討してください。 詳しくは、[イベント保存ポリシーの構成](/docs/services/cloud-activity-tracker/how-to/configuring_retention_policy.html#configuring_retention_policy)を参照してください。

## cURL を使用したイベントの削除
{: #deleting_events_api_records_per_day_curl}

スペース・ドメイン内の使用可能なイベントを削除するには、以下のステップを実行します。

1. UAA トークンを取得します。

    詳しくは、[UAA トークンの取得](/docs/services/cloud-activity-tracker/reference/auth_uaa.html#auth_uaa)を参照してください。

2. {{site.data.keyword.cloudaccesstrailshort}} に保管された特定の日のイベントを削除するには、次の cURL コマンドを実行します。

    ```
    curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json" -X DELETE  ENDPOINT/v3/events -d '{"start":"2018-06-24","end":"2018-06-24","AtAccountLevel":false,"SearchTime":""}'
    ```
    {: codeblock}

    ここで、

    * *token* は、UAA トークンです。
    * *spaceID* は、{{site.data.keyword.cloudaccesstrailshort}} をプロビジョンした Cloud Foundry スペースの UUID を表します。
    * *ENDPOINT* は、サービスのエントリー・ポイントを表します。 地域ごとに URL は異なります。 地域ごとのエンドポイントのリストを取得するには、[エンドポイント](/docs/services/cloud-activity-tracker/reference/ref_endpoints.html#api_endpoints)を参照してください。
    * *start* および *end* は、ダウンロードするイベントの期間を表します。 日付形式は YYYY-MM-DD です。 
    * *AtAccountLevel* は、イベントに関する情報の取得対象ドメインを示します。
    * *SearchTime* は、イベントに関する情報の取得対象時刻を示します。


例えば、米国南部地域のスペース・ドメイン内の特定の 1 日のイベントを削除するには、次の cURL コマンドを実行します。

```
curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json" -X DELETE  https://activity-tracker.ng.bluemix.net/v3/events -d '{"start":"2018-06-24","end":"2018-06-24","AtAccountLevel":false,"SearchTime":""}'
```
{: codeblock}

例えば、スペース・ドメイン内の先週のイベントを削除するには、次の cURL コマンドを実行します。

```
curl -H  "Content-Type:application/json" -H "X-Auth-Token: bearer ${token}" -H "X-Auth-Project-Id:${spaceId}" -H "Accept:application/json" --request DELETE --data "{\"start\":\"$(date -u -v-7d +%F)\", \"end\":\"$(date -u -v-6d +%F)\" }" https://activity-tracker.ng.bluemix.net/v3/events
```
{: codeblock}


## NodeJS でのイベント削除の例
{: #deleting_events_api_node}

以下は、イベントを削除する方法をテストするために使用できるサンプル・コードです。

この例では、{{site.data.keyword.cloudaccesstrailshort}} サービスが米国南部地域にプロビジョンされていると想定しています。 

```
var http = require("https")
var fs = require("fs")

var token = "{TOKEN}";

// {{site.data.keyword.cloudaccesstrailshort}} サービスがプロビジョンされている Cloud Foundry スペースのスペース ID
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
