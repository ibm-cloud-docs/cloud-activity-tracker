---

copyright:
  years: 2016, 2017

lastupdated: "2017-09-07"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# Activity Tracker CLI を使用したイベント管理
{: #tutorial2}

このチュートリアルでは、{{site.data.keyword.cloudaccesstrailshort}} CLI を使用して、コマンド・ラインを介してイベントを管理する方法について説明します。保管されたイベントに関する情報の取得方法、{{site.data.keyword.IBM_notm}} クラウドに保管されたイベントのダウンロード方法、イベントの削除方法を学習できます。
{:shortdesc}

以下のステップを実行します。

1. [{{site.data.keyword.IBM_notm}} Key Protect サービスをプロビジョンし、イベントを生成する](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step1)
2. [保管されたイベントに関する情報を取得する (cf at status)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step2)
2. [セッションを作成することによって、ダウンロードするログを指定する (cf at session create)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step3)
3. [実際のログ・データを取得する (cf at download)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step4)
4. [ダウンロード完了後にセッションを削除する (cf at session delete)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step5)
5. [不要なログを手動で削除する (cf at delete)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step6)


## 前提条件
{: #assumptions}

1. {{site.data.keyword.IBM_notm}} クラウド {{site.data.keyword.cloudaccesstrailshort}} サービスがプロビジョンされた {{site.data.keyword.Bluemix_notm}} アカウントのスペース内で作業するために、開発者の許可がある {{site.data.keyword.Bluemix_notm}} ユーザー ID を持っていること。 

    {{site.data.keyword.cloudaccesstrailshort}} サービスをプロビジョンする方法について詳しくは、[{{site.data.keyword.cloudaccesstrailshort}} サービスのプロビジョン](/docs/services/cloud-activity-tracker/how-to/provision.html#provision)を参照してください。

2. ローカル・システムに {{site.data.keyword.cloudaccesstrailshort}} CF プラグインをインストール済みであること。コマンド・ラインを介してイベントを管理するために {{site.data.keyword.cloudaccesstrailshort}} CLI を使用できるためには、これが必要です。 

    {{site.data.keyword.cloudaccesstrailshort}} CF プラグインのインストールについて詳しくは、[{{site.data.keyword.cloudaccesstrailshort}} CLI の構成](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#config_at_cli)を参照してください。

3. 以下のコマンドを使用して、コマンド・ラインを介して {{site.data.keyword.Bluemix_notm}} にログイン済みであること。

    ```
    bx login -a Endpoint
    ```
    {: codeblock}
	
	ここで、*Endpoint* は、{{site.data.keyword.Bluemix_notm}} にログインするための URL です。この URL は地域ごとに異なります。
	
	<table>
	    <caption>{{site.data.keyword.Bluemix_notm}} にアクセスするためのエンドポイントのリスト</caption>
		<tr>
		  <th>地域</th>
		  <th>URL</th>
		</tr>
		<tr>
		  <td>米国南部</td>
		  <td>api.ng.bluemix.net</td>
		</tr>
	</table>

    例えば、米国南部地域にログインするには、次のコマンドを実行します。
	
	```
	bx cf login -a api.ng.bluemix.net
	```
	{: codeblock}

	**注:** {{site.data.keyword.cloudaccesstrailshort}} コマンドの実行およびイベントの管理をコマンド・ラインを介して実行できるためには、{{site.data.keyword.cloudaccesstrailshort}} サービスがプロビジョンされた、{{site.data.keyword.Bluemix_notm}} 内の地域、組織、およびスペースにログインする必要があります。
	
	次に、組織およびスペースを設定します。以下のコマンドを実行します。

    ```
    bx target -o OrgName -s SpaceName
    ```
    {: codeblock}

    ここで、

    * OrgName は、組織の名前です。
    * SpaceName は、スペースの名前です。


## ステップ 1: IBM Key Protect サービスをプロビジョンし、イベントを生成する 
{: #step1}
	
1. 以下の手順を実行して、{{site.data.keyword.Bluemix_notm}} で {{site.data.keyword.keymanagementserviceshort}} サービスのインスタンスをプロビジョンします。

    1. {{site.data.keyword.Bluemix_notm}} アカウントにログインします。

        {{site.data.keyword.Bluemix_notm}} ダッシュボードは、[http://bluemix.net](http://bluemix.net) にあります。

        ユーザー ID とパスワードを使用してログインすると、{{site.data.keyword.Bluemix_notm}} UI が開きます。

    2. **「カタログ」**をクリックします。{{site.data.keyword.Bluemix_notm}} で使用可能なサービスのリストが開きます。

        **「セキュリティー」**カテゴリーを選択して、表示されたサービスのリストをフィルタリングします。

    3. **Key Protect** タイルを選択します。

    4. **「作成」**をクリックして、ログインしている {{site.data.keyword.Bluemix_notm}} スペース内で {{site.data.keyword.keymanagementserviceshort}} サービスをプロビジョンします。

2. 以下の手順を実行して {{site.data.keyword.cloudaccesstrailshort}} イベントを生成します。

    1. {{site.data.keyword.Bluemix_notm}} ダッシュボードから {{site.data.keyword.keymanagementserviceshort}} サービスを選択します。{{site.data.keyword.keymanagementserviceshort}} ダッシュボードが開きます。次に、**「管理」**タブを選択します。

    2. **「鍵の追加」**をクリックします。新しいウィンドウが開きます。

        ![鍵を追加するための {{site.data.keyword.keymanagementserviceshort}} ウィンドウ](images/KP_f2.gif)

    3. **「鍵の生成」**を選択し、以下の手順を実行します。

        * 鍵の名前を入力します (例: *MyFirstKey*)。

        * 鍵のアルゴリズムを選択します。

        * **「鍵の追加」**をクリックします。 

3. イベントが作成されたことを検証します。

    1. {{site.data.keyword.Bluemix_notm}} ダッシュボードから {{site.data.keyword.cloudaccesstrailshort}} サービスを選択します。このサービスのダッシュボードが開きます。

    2. ビューを構成して、サービスをプロビジョンして鍵を追加したときに生成された {{site.data.keyword.keymanagementserviceshort}} イベントを検索します。

        * *「ログの表示」*フィールドで**「スペース・ログ」**を選択します。
	    * *「検索フィールド」*フィールドで**「target.name」**を選択します。
	    * *「フィルター」*フィールドに **ibm-key-protect** を入力します。
	
	    表示されるデータは、過去 24 時間の使用可能な {{site.data.keyword.keymanagementserviceshort}} イベントに対応します。 

	    ![{{site.data.keyword.cloudaccesstrailshort}} 管理タブ](images/KP_f3.gif)

## ステップ 2: 保管されたイベントに関する情報を取得する
{: #step2}

ダウンロードに使用可能なイベントを確認します。例えば、プロビジョンと鍵の追加を行ったのが現在日付である場合、次のコマンドを実行して、本日収集されたイベントについての情報を取得します。

```
bx cf at status -s 2017-07-25 -e 2017-07-25
+------------+-------+-------+------------+
| Date       | Count | Size  | Searchable |
+------------+-------+-------+------------+
| 2017-07-25 | 12    | 34994 | All        |
+------------+-------+-------+------------+
```
{: screen}

このコマンドは、2017 年 6 月 25 日のイベントをカウントします。{{site.data.keyword.cloudaccesstrailshort}} はグローバル・サービスであるため、日付は世界時です。現地時間の完全な 1 日を取得するために、複数の UTC 日のダウンロードが必要になることがあります。

複数日の情報を確認するには、`-s` を使用して開始日を、`-e` を使用して終了日を設定します。 

`cf at status` コマンドについて詳しくは、[CLI リファレンス](/docs/services/cloud-activity-tracker/cli/at_cli.html#status)を参照してください。

コマンド・ラインからヘルプを取得するには、`bx cf at help status` を使用してください。

## ステップ 3: ダウンロードするイベントを指定する
{: #step3}

イベントをダウンロードする前に、セッションを作成します。

* セッションは、どのイベントがダウンロードされるのかを指定します。
* イベントのダウンロードが中断された場合、セッションは中断した箇所からのダウンロードの再開を可能にします。

セッションを作成するには、次のコマンドを使用します。

```
bx cf at session create -s 2017-07-25 -e 2017-07-25
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| id           | 21b19aeb-3d32-4c60-b912-517609c62db2      |
| space        | 667fb895-b5f5-46c9-9f0e-cf4587341095      |
| username     | xxx@yyy.com                               |
| create-time  | 2017-07-25T18:33:22.678350874Z            |
| access-time  | 2017-07-25T18:33:22.678350874Z            |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
+--------------+-------------------------------------------+
```

セッションに関連付けられた開始日と終了日があります。download コマンドには、これらの日付の間 (これらの日付を含む) のイベントが含まれることになります。デフォルトの日付範囲は、現在日付のみです。 

このコマンドの出力の重要部分はセッション `ID` です。これは download コマンドで参照されます。

既存のセッションに関する情報を取得するには、`cf at session list` と入力します。

セッションおよび `cf at session create` コマンドについて詳しくは、[CLI リファレンス](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_create)を参照してください。

コマンド・ラインからヘルプを取得するには、`cf at session help create` を使用してください。

## ステップ 4: セッションに定義されたスコープに対して識別されたイベントをダウンロードする
{: #step4}

セッションのパラメーターによって指定されたイベントをダウンロードするには、次のコマンドを実行します。

```
$ bx cf at events download -o events.log 21b19aeb-3d32-4c60-b912-517609c62db2
 6.70 KiB / 3.06 KiB [================================================================================================================================================================] 219.03% 8.60 MiB/s 0s
Download Successful
```

* `-o`パラメーターは、出力ファイルを指定します。
* セッション ID は最後に指定されます。セッション ID の値は、`cf at session create` コマンドの出力から取得します。
* 進行状況表示は、イベントがダウンロードされるに従って 0% から 100% に進んでいきます。

ダウンロードされたデータのフォーマットは、圧縮 JSON です。 

`cf at download` コマンドについて詳しくは、[CLI リファレンス](/docs/services/cloud-activity-tracker/cli/at_cli.html#download)を参照してください。

コマンド・ラインからヘルプを取得するには、`bx cf at help download` を使用してください。

## ステップ 5: セッションを削除する
{: #step5}

ダウンロードが完了した後、セッションを削除します。 

セッションの数は制限されています。セッションは自動的には削除されません。不要なセッションを手動で削除する必要があります。 

```
$ bx cf at session delete 21b19aeb-3d32-4c60-b912-517609c62db2
+---------+------------------------+
| name    | value                  |
+---------+------------------------+
| message | Delete session success |
+---------+------------------------+
```

`cf at session delete` コマンドについて詳しくは、[CLI リファレンス](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_delete)を参照してください。

コマンド・ラインからヘルプを取得するには、`bx cf at session help delete` を使用してください。

## ステップ 6: Activity Tracker からイベントを手動で削除する
{: #step6}

{{site.data.keyword.cloudaccesstrailshort}} では、独自のイベント保存を制御できます。イベントを手動で削除するか、イベントの削除を自動化することができます。

イベントを手動で削除するには、`cf at delete` コマンドを実行します。以下に例を示します。

```
$ bx cf at delete -s 2017-07-25 -e 2017-07-25
Deleted successfully
"6 logs were deleted,freeing 13737 bytes."
```

`cf at delete` コマンドについて詳しくは、[CLI リファレンス](/docs/services/cloud-activity-tracker/cli/at_cli.html#delete)を参照してください。

コマンド・ラインからヘルプを取得するには、`bx cf at help delete` を使用してください。

**注:** イベントを自動的に削除するために、CLI コマンド `cf at option` を使用して保存ポリシーを設定できます。詳しくは、[CLI リファレンス](/docs/services/cloud-activity-tracker/cli/at_cli.html#option)を参照してください。


