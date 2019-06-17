---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, events

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
{:deprecated: .deprecated}


# {{site.data.keyword.cloudaccesstrailshort}} イベント
{: #events}

{{site.data.keyword.cloudaccesstrailfull}} サービスを使用して、{{site.data.keyword.Bluemix}} 内で {{site.data.keyword.cloudaccesstrailshort}} を追跡します。 
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} は非推奨になりました。 2019 年 5 月 9 日以降、新しい {{site.data.keyword.cloudaccesstrailshort}} インスタンスをプロビジョンできません。 既存のプレミアム・プランのインスタンスは、2019 年 9 月 30 日までサポートされます。 {{site.data.keyword.cloud_notm}} アカウントのアクティビティーのモニタリングを続行するには、[{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) のインスタンスをプロビジョンします。
{: deprecated}


## イベントのリスト
{: #actions}

次の表に、イベントを生成するアクションのリストを示します。

<table>
  <caption>表 1. イベントを生成するアクションのリスト</caption>
  <tr>
    <th>アクション</th>
	  <th>説明</th>
  <tr>
  <tr>
    <td>read.events</td>
	  <td>保管されたイベントに関する情報を取得します。</td>
  </tr>
  <tr>
    <td>create.sessions</td>
	  <td>イベントをダウンロードするために使用できるセッションを作成します。</td>
  </tr>
  <tr>
    <td>delete.session</td>
	  <td>セッションを削除します。</td>
  </tr>
  <tr>
    <td>read.sessions</td>
	  <td>セッションをリストします。</td>
  </tr>
  <tr>
    <td>download.events</td>
	  <td>イベントをダウンロードします。</td>
  </tr>
  <tr>
    <td>delete.events</td>
	  <td>イベントを削除します。</td>
  </tr>
</table>


## イベントを検索する場所
{: #ui}
 	
{{site.data.keyword.cloudaccesstrailshort}} イベントは、{{site.data.keyword.cloudaccesstrailshort}} サービスがプロビジョンされた Cloud Foundry スペース内で使用可能です。
