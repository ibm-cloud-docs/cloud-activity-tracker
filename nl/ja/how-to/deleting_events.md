---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, delete events

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

# イベントの削除
{: #deleting_events}

*ibmcloud at delete* コマンドを使用して、{{site.data.keyword.cloudaccesstrailshort}} に保管されたイベントを手動で削除します。
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} は非推奨になりました。2019 年 5 月 9 日以降、新しい {{site.data.keyword.cloudaccesstrailshort}} インスタンスをプロビジョンできません。既存のプレミアム・プランのインスタンスは、2019 年 9 月 30 日までサポートされます。{{site.data.keyword.cloud_notm}} アカウントのアクティビティーのモニタリングを続行するには、[{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) のインスタンスをプロビジョンします。
{: deprecated}


以下のステップを実行します。

## ステップ 1: {{site.data.keyword.cloud_notm}} にログインする
{: #deleting_events_prereq}

{{site.data.keyword.cloud_notm}} にログインします。 以下のステップを実行します。

1. [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) コマンドを実行して、{{site.data.keyword.cloud_notm}} にログインします。
2. [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) コマンドを実行して、{{site.data.keyword.cloudaccesstrailshort}} サービスをプロビジョンする組織とスペースを設定します。

**注:** {{site.data.keyword.cloudaccesstrailshort}} がプロビジョンされる組織とスペースを設定してください。

## ステップ 2: 使用可能なイベントを識別する
{: #deleting_events_step2}

`ibmcloud at status` コマンドを使用して、スペース・ドメイン内の使用可能なイベントに関する情報を表示します。

* スペース・ドメイン内のイベントに関する情報を取得するには、コマンド `ibmcloud at status` を実行します。
* アカウント・ドメイン内のイベントに関する情報を取得するには、オプション `-a` を指定してコマンド `ibmcloud at status` を実行します。

詳しくは、[イベント情報の表示](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-viewing_event_status#viewing_event_status)を参照してください。
	
  
## ステップ 3: イベントを削除する
{: #deleting_events_step3}
	
イベントを削除するには、コマンド `ibmcloud at delete` を実行します。

```
ibmcloud at delete -s YYYY-MM-DD -e YYYY-MM-DD 
```
{: codeblock}
    
ここで、

* *-s* は、開始日を協定世界時 (UTC) *YYYY-MM-DD* で設定するために使用されます。
* *-e* は、終了日を協定世界時 (UTC) *YYYY-MM-DD* で設定するために使用されます。

例えば、2017 年 6 月 10 日のイベントを削除するには、次のコマンドを実行します。

```
ibmcloud at delete -s 2017-06-10 -e 2017-06-10
```
{: screen}

削除されたイベント・レコードに関する情報が示されます。










