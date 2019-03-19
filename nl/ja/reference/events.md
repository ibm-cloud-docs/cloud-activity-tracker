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


# {{site.data.keyword.cloudaccesstrailshort}} イベント
{: #events}

{{site.data.keyword.cloudaccesstrailfull}} サービスを使用して、{{site.data.keyword.Bluemix}} 内で {{site.data.keyword.cloudaccesstrailshort}} を追跡します。 
{:shortdesc}



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
