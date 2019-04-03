---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, manage events, tutorial

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


# Activity Tracker CLI を使用したイベント管理
{: #tutorial2}

このチュートリアルでは、{{site.data.keyword.cloudaccesstrailshort}} CLI を使用して、コマンド・ラインを介してイベントを管理する方法について説明します。 保管されたイベントに関する情報の取得方法、{{site.data.keyword.IBM_notm}} クラウドに保管されたイベントのダウンロード方法、イベントの削除方法を学習できます。
{:shortdesc}

以下のステップを実行します。

1. [{{site.data.keyword.keymanagementservicelong_notm}} をプロビジョンし、イベントを生成する](/docs/services/cloud-activity-tracker/tutorials?topic=cloud-activity-tracker-tutorial2#tutorial2_step1)
2. [保管されたイベントに関する情報を取得する (ibmcloud at status)](/docs/services/cloud-activity-tracker/tutorials?topic=cloud-activity-tracker-tutorial2#tutorial2_step2)
2. [セッションを作成することによって、ダウンロードするログを指定する (ibmcloud at session create)](/docs/services/cloud-activity-tracker/tutorials?topic=cloud-activity-tracker-tutorial2#tutorial2_step3)
3. [実際のログ・データを取得する (ibmcloud at download)](/docs/services/cloud-activity-tracker/tutorials?topic=cloud-activity-tracker-tutorial2#tutorial2_step4)
4. [ダウンロード完了後にセッションを削除する (ibmcloud at session delete)](/docs/services/cloud-activity-tracker/tutorials?topic=cloud-activity-tracker-tutorial2#tutorial2_step5)
5. [不要なログを手動で削除する (ibmcloud at delete)](/docs/services/cloud-activity-tracker/tutorials?topic=cloud-activity-tracker-tutorial2#tutorial2_step6)


## 前提条件
{: #tutorial2_assumptions}

1. {{site.data.keyword.cloudaccesstrailshort}} サービスがプロビジョンされた {{site.data.keyword.cloud_notm}} アカウントのスペース内で作業するために、`developer` 許可がある {{site.data.keyword.cloud_notm}} ユーザー ID を持っていること。 

    {{site.data.keyword.cloudaccesstrailshort}} サービスをプロビジョンする方法について詳しくは、[{{site.data.keyword.cloudaccesstrailshort}} サービスのプロビジョン](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-provision#provision)を参照してください。

2. プレミアム・プランで {{site.data.keyword.cloudaccesstrailshort}} サービスのインスタンスを保有していること。

    **注:** `ライト`・プランでは、{{site.data.keyword.cloudaccesstrailshort}} CLI を使用できません。

3. ローカル・システムに {{site.data.keyword.cloudaccesstrailshort}} CLI がインストール済みであること。この CLI は、コマンド・ラインを介してイベントを管理するために必要です。 

    {{site.data.keyword.cloudaccesstrailshort}} CLI のインストールについて詳しくは、[{{site.data.keyword.cloudaccesstrailshort}} CLI の構成](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-config_cli#config_cli)を参照してください。

4. コマンド・ラインを介して {{site.data.keyword.cloud_notm}} にログイン済みであること。 このチュートリアルの場合、端末から以下のコマンドを実行します。 

    `ibmcloud login -a api.ng.bluemix.net` を実行して、米国南部地域にログインします。 詳しくは、[ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) を参照してください。
    
    `ibmcloud target -o OrgName -s SpaceName` を実行して、{{site.data.keyword.cloudaccesstrailshort}} サービスがプロビジョンされるターゲット組織およびスペースを設定します。 詳しくは、[ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) を参照してください。


## ステップ 1. IBM Key Protect サービスをプロビジョンし、イベントを生成する 
{: #tutorial2_step1}
	
{{site.data.keyword.cloud_notm}} 内で {{site.data.keyword.keymanagementserviceshort}} サービスをプロビジョンし、イベントを生成するため、以下のステップを実行します。

1. 米国南部地域に {{site.data.keyword.keymanagementserviceshort}} サービスのインスタンスをプロビジョンします。 詳しくは、[IBM Cloud コンソールからのプロビジョン](/docs/services/key-protect?topic=key-protect-provision#provision)を参照してください。

2. キーの処理に使用するユーザーの {{site.data.keyword.cloud_notm}} 許可を定義します。 

    * キーを作成できるためには、ユーザーは、サービス役割が*マネージャー* または*ライター* に設定された IAM ポリシーを必要とします。
	* キーを削除できるためには、ユーザーは、サービス役割が*マネージャー* に設定された IAM ポリシーを必要とします。
	* キーを表示できるためには、ユーザーは、サービス役割が*リーダー* に設定された IAM ポリシーを必要とします。 

3. {{site.data.keyword.cloudaccesstrailshort}} イベント・データを生成するために、{{site.data.keyword.keymanagementserviceshort}} サービスを使用してセキュリティー・キーを作成します。 詳しくは、[新規キーの作成](/docs/services/key-protect?topic=key-protect-create-standard-keys#create-standard-keys)を参照してください。

鍵の作成の結果として、{{site.data.keyword.cloudaccesstrailshort}} イベントが生成されます。

## ステップ 2. 保管されたイベントに関する情報を取得する
{: #tutorial2_step2}

{{site.data.keyword.keymanagementserviceshort}} イベントは、{{site.data.keyword.cloudaccesstrailshort}} アカウント・ドメイン内で使用可能です。

このチュートリアルでは、{{site.data.keyword.keymanagementserviceshort}} イベントは、{{site.data.keyword.keymanagementserviceshort}} サービスをプロビジョンした地域である米国南部アカウント・ドメイン内で使用可能です。 

特定の日に収集されたイベントに関する情報を取得するには、以下のコマンドを実行します。

```
ibmcloud at status -s startDate -e endDate -a
```
{: codeblock}

各部の意味は、次のとおりです。 

* `-s` は開始日を設定するために使用されます。 
* `startDate` は、開始日を表します。 形式は *YYYY-MM-DD* です。
* `-e` は、終了日を設定するために使用されます。
* `endDate` は、終了日を表します。 形式は *YYYY-MM-DD* です。
* `-a` は、アカウント・ドメインでのイベントを含めることを指示するために使用されます。

以下に例を示します。

```
ibmcloud at status -s 2017-07-25 -e 2017-07-25 -a
+------------+-------+-------+------------+
| Date       | Count | Size  | Searchable |
+------------+-------+-------+------------+
| 2017-07-25 | 12    | 34994 | All        |
+------------+-------+-------+------------+
```
{: screen}

このコマンドは、2017 年 6 月 25 日のイベントをカウントします。{{site.data.keyword.cloudaccesstrailshort}} は、グローバル・サービスです。したがって、日付は世界時です。現地時間の丸 1 日のイベントを取得するには、複数の UTC 日のダウンロードが必要になることがあります。




## ステップ 3. ダウンロードするイベントを指定する
{: #tutorial2_step3}

イベントのダウンロードを開始する前に、セッションを作成します。セッションは、どのイベントがダウンロードされるのかを指定します。


セッションを作成するには、次のコマンドを使用します。

```
ibmcloud at session create -s startDate -e endDate -a
```
{: codeblock}

各部の意味は、次のとおりです。 

* `-s` は開始日を設定するために使用されます。 
* `startDate` は、開始日を表します。 形式は *YYYY-MM-DD* です。
* `-e` は、終了日を設定するために使用されます。
* `endDate` は、終了日を表します。 形式は *YYYY-MM-DD* です。
* `-a` は、アカウント・ドメインでのイベントを含めることを指示するために使用されます。

以下に例を示します。 

```
ibmcloud at session create -s 2017-07-25 -e 2017-07-25 -a
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
{: screen}

各部の意味は、次のとおりです。 

* `-s` は開始日を設定するために使用されます。
* `-e` は、終了日を設定するために使用されます。
* `-a` は、アカウント・ドメインでのイベントを含めることを指示するために使用されます。

セッションには開始日と終了日が関連付けられています。download コマンドでは、これらの日付の間 (これらの日付を含む) のイベントが含まれます。

このコマンドの出力の重要部分はセッション `ID` です。 これは download コマンドで参照されます。

既存のセッションに関する情報を取得するには、`ibmcloud at session list` と入力します。

セッションおよび `ibmcloud at session create` コマンドについて詳しくは、[CLI リファレンス](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-at_cli_cloud#session_create)を参照してください。

コマンド・ラインからヘルプを利用するには、`ibmcloud at session help create` を使用してください。

## ステップ 4. セッションに定義されたスコープに対して識別されたイベントをダウンロードする
{: #tutorial2_step4}

セッションのパラメーターによって指定されたイベントをダウンロードするには、次のコマンドを実行します。

```
ibmcloud at download -o outputFile sessionID
```
{: codeblock}

* `-o`パラメーターは、出力ファイルを指定します。
* `outputFile` は、ローカル・ファイルの名前です。
* `sessionID` は最後に指定されます。 セッション ID の値は、`ibmcloud at session create` コマンドの出力から取得します。

ダウンロードされたデータのフォーマットは、圧縮 JSON です。 

以下に例を示します。

```
$ ibmcloud at download -o events.log 21b19aeb-3d32-4c60-b912-517609c62db2
 6.70 KiB / 3.06 KiB [================================================================================================================================================================] 219.03% 8.60 MiB/s 0s
Download Successful
```
{: screen} 

進行状況表示は、イベントがダウンロードされるに従って 0% から 100% に進んでいきます。

`ibmcloud at download` コマンドについて詳しくは、[CLI リファレンス](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-at_cli_cloud#download)を参照してください。

コマンド・ラインからヘルプを利用するには、`ibmcloud at help download` を使用してください。

## ステップ 5. セッションを削除する
{: #tutorial2_step5}

ダウンロードが完了した後、セッションを削除します。 以下のコマンドを実行します。

```
ibmcloud at session delete sessionID
```
{: codeblock}

各部の意味は、次のとおりです。 

* `sessionID` は、削除するセッションの ID です。

セッションの数は制限されています。 セッションは自動的には削除されません。 不要なセッションを手動で削除する必要があります。 

以下に例を示します。 

```
$ ibmcloud at session delete 21b19aeb-3d32-4c60-b912-517609c62db2
+---------+------------------------+
| name    | value                  |
+---------+------------------------+
| message | Delete session success |
+---------+------------------------+
```
{: screen}

`ibmcloud at session delete` コマンドについて詳しくは、[CLI リファレンス](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-at_cli_cloud#session_delete)を参照してください。

コマンド・ラインからヘルプを利用するには、`ibmcloud at session help delete` を使用してください。

## ステップ 6. Activity Tracker からイベントを自動的に削除する
{: #tutorial2_step6}

{{site.data.keyword.cloudaccesstrailshort}} では、独自のイベント保存を制御できます。 イベントを手動で削除するか、イベントの削除を自動化することができます。

スペースからイベントを手動で削除するには、`ibmcloud at delete` コマンドを実行します。 以下に例を示します。

```
$ ibmcloud at delete -s 2017-07-25 -e 2017-07-25
Deleted successfully
"6 logs were deleted,freeing 13737 bytes."
```
{: screen}

`ibmcloud at delete` コマンドについて詳しくは、[CLI リファレンス](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-at_cli_cloud#delete)を参照してください。

コマンド・ラインからヘルプを利用するには、`ibmcloud at help delete` を使用してください。

**注:** イベントを自動的に削除するために、CLI コマンド `ibmcloud at option` を使用して保存ポリシーを設定できます。 詳しくは、[CLI リファレンス](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-at_cli_cloud#option)を参照してください。


