---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, view events

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
{: #viewing_event_status}

`ibmcloud at status` コマンドを使用して、{{site.data.keyword.Bluemix}} スペースに対して {{site.data.keyword.cloudaccesstrailshort}} で収集および保管されたイベントに関する情報を取得します。
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} は非推奨になりました。 2019 年 5 月 9 日以降、新しい {{site.data.keyword.cloudaccesstrailshort}} インスタンスをプロビジョンできません。 既存のプレミアム・プランのインスタンスは、2019 年 9 月 30 日までサポートされます。 {{site.data.keyword.cloud_notm}} アカウントのアクティビティーのモニタリングを続行するには、[{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) のインスタンスをプロビジョンします。
{: deprecated}


イベント・ログのサイズに関する情報、レコード数、および、イベントが Kibana での分析に使用可能かどうかの情報を取得できます。 

イベント・ログに関する情報を表示するには、以下のステップを実行します。

## ステップ 1: {{site.data.keyword.cloud_notm}} にログインする
{: #viewing_event_status_step1}

{{site.data.keyword.cloud_notm}} にログインします。 以下のステップを実行します。

1. [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) コマンドを実行して、{{site.data.keyword.cloud_notm}} にログインします。
2. [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) コマンドを実行して、{{site.data.keyword.cloudaccesstrailshort}} サービスをプロビジョンする組織とスペースを設定します。

**注:** {{site.data.keyword.cloudaccesstrailshort}} がプロビジョンされる組織とスペースを設定してください。

## ステップ 2: 使用可能なイベントを識別する
{: #viewing_event_status_step2}

`ibmcloud at status` コマンドを使用して、スペース・ドメイン内の使用可能なイベントに関する情報を表示します。

* スペース・ドメイン内のイベントに関する情報を取得するには、コマンド `ibmcloud at status` を実行します。
* アカウント・ドメイン内のイベントに関する情報を取得するには、オプション `-a` を指定してコマンド `ibmcloud at status` を実行します。

```
$ ibmcloud at status -a -s YYYY-MM-DD -e YYYY-MM-DD 
```
{: codeblock}
    
ここで、
    
* *-a* は、この要求がアカウント・ドメインに適用されることを指定するために使用されます。
* *-s* は、開始日を協定世界時 (UTC) *YYYY-MM-DD* で設定するために使用されます。
* *-e* は、終了日を協定世界時 (UTC) *YYYY-MM-DD* で設定するために使用されます。

例えば、スペース・ドメイン内の過去 2 週間の使用可能なイベントを表示するには、次のコマンドを実行します。

```
$ ibmcloud at status
```
{: codeblock}
    
例えば、このコマンド実行の出力は以下のようになります。
    
```
+------------+--------+------------+
|    DATE    |  COUNT | SEARCHABLE |
+------------+--------+------------+
| 2017-07-24 |    16  |    None    |
+------------+--------+------------+
| 2017-07-25 |   1224 |    All     |
+------------+--------+------------+
```
{: screen}

**注:** {{site.data.keyword.cloudaccesstrailshort}} サービスは、協定世界時 (UTC) を使用するグローバル・サービスです。 日付は UTC 日付で定義されます。 現地時間の特定の 1 日のイベントを取得するために、複数の UTC 日のダウンロードが必要になることがあります。
	














