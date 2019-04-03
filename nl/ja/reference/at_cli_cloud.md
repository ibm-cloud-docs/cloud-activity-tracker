---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, CLI

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


# IBM Cloud Activity Tracker CLI
{: #at_cli_cloud}

{{site.data.keyword.cloudaccesstraillong}} CLI を使用して {{site.data.keyword.cloudaccesstrailshort}} イベントを管理できます。
{: shortdesc}

**前提条件**
* コマンドを実行する前に、`ibmcloud login` コマンドで {{site.data.keyword.Bluemix}} にログインして、アクセス・トークンを生成し、セッションを認証します。
* CLI を使用してイベントを管理するには、有料プランが必要です。

{{site.data.keyword.cloudaccesstraillong}} CLI プラグインがサポートするプラットフォームは、Linux、Mac、および Windows です。

<table>
  <caption>{{site.data.keyword.cloudaccesstrailshort}} を管理するためのコマンド</caption>
  <tr>
    <th>コマンド</th>
    <th>いつ使用するか</th>
  </tr>
  <tr>
    <td>[ibmcloud at](#base)</td>
    <td>この CLI についての情報 (バージョンまたはコマンド・リストなど) を取得するには、このコマンドを使用します。</td>
  </tr>
  <tr>
    <td>[ibmcloud at delete](#delete)</td>
    <td>{{site.data.keyword.cloudaccesstrailshort}} イベントを削除するには、このコマンドを使用します。</td>
  </tr>
  <tr>
    <td>[ibmcloud at download](#download)</td>
    <td>{{site.data.keyword.cloudaccesstrailshort}} ログをローカル・ファイルにダウンロードするには、このコマンドを使用します。 </td>
  </tr>
  <tr>
    <td>[ibmcloud at help](#help)</td>
    <td>CLI の使用法に関するヘルプおよびすべてのコマンドのリストを取得するには、このコマンドを使用します。</td>
  </tr>
  <tr>
    <td>[ibmcloud at option](#option)</td>
    <td>スペースまたはアカウントで使用可能な {{site.data.keyword.cloudaccesstrailshort}} イベント・オプション (保存など) を表示または変更するには、このコマンドを使用します。</td>
  </tr>
  <tr>
    <td>[ibmcloud at session create](#session_create)</td>
    <td>新規セッションを作成するには、このコマンドを使用します。</td>
  </tr>
  <tr>
    <td>[ibmcloud at session delete](#session_delete)</td>
    <td>セッションを削除するには、このコマンドを使用します。</td>
  </tr>  
  <tr>
    <td>[ibmcloud at session list](#session_list)</td>
    <td>アクティブ・セッションおよびその ID をリストするには、このコマンドを使用します。</td>
  </tr>  
  <tr>
    <td>[ibmcloud at session show](#session_show)</td>
    <td>単一セッションの状況を表示するには、このコマンドを使用します。</td>
  </tr>   
  <tr>
    <td>[ibmcloud at status](#status)</td>
    <td>{{site.data.keyword.cloudaccesstrailshort}} に保管されたイベントの状況についての情報を表示するには、このコマンドを使用します。</td>
  </tr>
  </table>


## ibmcloud at
{: #base}

CLI のバージョンおよび CLI の使用方法についての情報を提供します。

```
ibmcloud at [parameters]
```
{: codeblock}

**パラメーター**

<dl>
<dt>--help、-h</dt>
<dd>コマンドのリストを表示するか、または 1 つのコマンドのヘルプを取得するには、このパラメーターを設定します。
</dd>

<dt>--version、-v</dt>
<dd>CLI のバージョンを表示するには、このパラメーターを設定します。</dd>
</dl>

**例**

コマンドのリストを取得するには、次のコマンドを実行します。

```
ibmcloud at --help
```
{: codeblock}

CLI のバージョンを取得するには、次のコマンドを実行します。

```
ibmcloud at --version
```
{: codeblock}


## ibmcloud at delete
{: #delete}

{{site.data.keyword.cloudaccesstrailshort}} イベントを削除します。

```
ibmcloud at delete [parameters] [arguments..]
```
{: codeblock}

**パラメーター**

<dl>
  <dt>--start value、-s value</dt>
  <dd>(オプション) 開始日を協定世界時 (UTC) *YYYY-MM-DD* で設定します。例えば、`2017-01-02` です。 <br>デフォルト値は、2 週間前に設定されます。 
  </dd>
  
  <dt>--end value、-e value</dt>
  <dd>(オプション) 終了日を協定世界時 (UTC) *YYYY-MM-DD* で設定します。 <br>日付の UTC フォーマットは **YYYY-MM-DD** です (例: `2017-01-02`)。 <br>デフォルト値は、現在日付に設定されます。
  </dd>
  
  <dt>--search-time value、-T value</dt>
  <dd>(オプション) 特定の日の一定時間についての保管されたイベントを削除するように、このパラメーターを設定できます。 このフィールドの形式は、0 から 23 です。
  </dd>

</dl>


**例**

2017 年 6 月 22 日のイベントを削除するには、次のコマンドを実行します。
```
ibmcloud at delete -s 2017-06-22 -e 2017-06-22
```
{: codeblock}

以下の出力のような情報が表示されます。

`Deleted successfully`
`"6 logs were deleted, freeing 13737 bytes."`


## ibmcloud at download
{: #download}

{{site.data.keyword.cloudaccesstrailshort}} イベントをローカル・ファイルにダウンロードするか、または、Windows および Mac OS X の端末ウィンドウに、または Linux 端末の stdout に出力します。 

**注:** ファイルをダウンロードするには、まずセッションを作成する必要があります。 セッションは、日付範囲に基づいてどのイベントをダウンロードするのかを定義します。 イベントのダウンロードは、1 つのセッションのコンテキスト内で行います。 

```
ibmcloud at download [parameters] [arguments...]
```
{: codeblock}

**パラメーター**

<dl>
<dt>--output value、-o value</dt>
<dd>(オプション) イベントがダウンロードされるローカル出力ファイルのパスとファイル名を設定します。 <br>デフォルト値はハイフン (-) です。 <br>ログを標準出力に出力するには、このパラメーターをデフォルト値に設定してください。</dd>
</dl>

**引数**

<dl>
<dt>セッション ID</dt>
<dd>`ibmcloud at session create` コマンドの実行時に取得したセッション ID 値を設定します。 この値は、イベントをダウンロードするときに使用するセッションを指示します。 <br>**注:** `ibmcloud at session create` コマンドには、どのイベントがダウンロードされるのかを制御するパラメーターがあります。 </dd>
</dl>

**注:** ダウンロードが完了した後、同じデータを再度ダウンロードするには、異なるファイルまたは異なるセッションを使用する必要があります。

**例**

`events.log` という名前のファイルにイベントをダウンロードするには、次のコマンドを実行します。

```
ibmcloud at download -o events.log 1db6ce16-824d-4d50-bd40-37f1d8fea9b7
```
{: screen}

以下の出力のような情報が表示されます。 

```
6.70 KiB / 3.06 KiB [========] 219.03% 8.60 MiB/s 0s
Download completed successfully
```
{: screen}


## ibmcloud at help
{: #help}

コマンドの使用方法に関する情報を提供します。

```
ibmcloud at help [parameters]
```
{: codeblock}

**パラメーター**

<dl>
<dt>コマンド</dt>
<dd>ヘルプを取得したいコマンド名を設定します。
</dd>
</dl>


**例**

{{site.data.keyword.cloudaccesstrailshort}} の状況を表示するためのコマンドの実行方法に関するヘルプを取得するには、次のコマンドを実行します。

```
ibmcloud at help status
```
{: codeblock}


## ibmcloud at option
{: #option}

スペースで使用可能なイベントの保存期間を表示または変更します。 保存ポリシーを設定した場合、保存日数に達するとイベントは自動的に削除されます。

* 期間は日数で設定されます。
* デフォルト値は **-1** です。これは、イベントが保管され、削除されないことを示します。

**注:** デフォルトでは、すべてのイベントが保管されます。 保存期間を設定しない場合、`ibmcloud at delete` コマンドを使用して手動で削除する必要があります。 

```
ibmcloud at option [parameters] [arguments...]
```
{: codeblock}

**パラメーター**

<dl>
<dt>--retention value、-r value</dt>
<dd>(オプション) 保存日数を設定します。 <br> デフォルト値は *-1* 日です。</dd>

<dt>--at-account-level、-a</dt>
<dd>(オプション) 各スペース・ドメインおよびアカウント・ドメインに保管されたイベントの保存期間に関する情報をリストするには、このパラメーターを設定します。

</dl>

**例**

ログインしているスペースに対する現在の保存期間を表示するには、次のコマンドを実行します。

```
ibmcloud at option
```
{: codeblock}

出力内容は、以下のようになります。

```
+--------------------------------------+-----------+
|               SPACEID                | RETENTION |
+--------------------------------------+-----------+
| 2af890ce-fb4f-4e41-a975-901a56ed1f11 |        30 |
+--------------------------------------+-----------+
```
{: screen}


ログインしているスペースに対する保存期間を 25 日間に変更するには、次のコマンドを実行します。

```
ibmcloud at option -r 25
```
{: codeblock}

出力内容は、以下のようになります。

```
+--------------------------------------+-----------+
|               SPACEID                | RETENTION |
+--------------------------------------+-----------+
| 2af890ce-fb4f-4e41-a975-901a56ed1f11 |        25 |
+--------------------------------------+-----------+
```
{: screen}



## ibmcloud at session create
{: #session_create}

新規セッションを作成します。

**注:** 1 つのスペースで最大 30 までの並行セッションを保有できます。 セッションは 1 人のユーザーのために作成されます。 スペース内の複数のユーザーでセッションを共有することはできません。

```
ibmcloud at session create [parameters] [arguments...]
```
{: codeblock}

**パラメーター**

<dl>
  <dt>--at-account-level、-a </dt>
  <dd>(オプション) スコープをアカウント・レベルに設定します。 </br>アカウント情報を取得するには、この値を設定します。 <br>このパラメーターが指定されていない場合、デフォルト値は、現行スペース (つまり、`ibmcloud cf login` コマンドを使用してログインしたスペース) のみに設定されます。
  </dd>

  <dt>--start value、-s value</dt>
  <dd>(オプション) 開始日を協定世界時 (UTC) *YYYY-MM-DD* で設定します。例えば、`2017-01-02` です。 <br>デフォルト値は、2 週間前に設定されます。 
  </dd>
  
  <dt>--end value、-e value</dt>
  <dd>(オプション) 終了日を協定世界時 (UTC) *YYYY-MM-DD* で設定します。例えば、`2017-01-02` です。 <br>デフォルト値は、現在日付に設定されます。 
  </dd>

  <dt>--search-time value、-T value</dt>
  <dd>(オプション) 特定の日の一定時間についての保管されたイベントを削除するように、このパラメーターを設定できます。 このフィールドの形式は、0 から 23 です。
  </dd>


 </dl>

**返される値**

<dl>
<dt>アクセス時刻</dt>
<dd>セッションが最後に使用された時刻を示すタイム・スタンプ。</dd>

<dt>作成時刻</dt>
<dd>セッションが作成された日時に対応するタイム・スタンプ。</dd>

<dt>日付範囲</dt>
<dd>イベントのフィルタリングに使用される日付を示します。 この日付範囲内で識別されたイベントが、セッションを通した管理に使用可能です。</dd>

<dt>ID</dt>
<dd>セッション ID。</dd>

<dt>スペース</dt>
<dd>セッションがアクティブであるスペースの ID。</dd>

<dt>タイプ・アカウント</dt>
<dd>この値は **ActivityTracker** に設定されます。</dd>

<dt>ユーザー名</dt>
<dd>セッションを作成したユーザーの {{site.data.keyword.IBM_notm}} ID。</dd>
</dl>


**例**

2017 年 7 月 10 日に対するセッションを作成するには、次のコマンドを実行します。

```
ibmcloud at session create -s 2017-07-10 -e 2017-07-10
```
{: screen}

出力内容は、以下のようになります。

```
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| id           | 9b8c4db8-5841-4993-a449-305815a53a8e      |
| space        | xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx      |
| username     | xxx@yyy.com                               |
| create-time  | 2017-07-25T11:54:00.20042645Z             |
| access-time  | 2017-07-25T11:54:00.20042645Z             |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
+--------------+-------------------------------------------+
```
{: screen}



## ibmcloud at session delete
{: #session_delete}

セッション ID で指定されたセッションを削除します。

```
ibmcloud at session delete [arguments...]
```
{: codeblock}


**引数**

<dl>
<dt>セッション ID</dt>
<dd>削除するセッションの ID。 <br>`ibmcloud at session list` コマンドを使用して、すべてのアクティブ・セッション ID を取得できます。</dd>
</dl>

**例**

セッション ID *9b8c4db8-5841-4993-a449-305815a53a8e* のセッションを削除するには、次のコマンドを実行します。

```
ibmcloud at session delete 9b8c4db8-5841-4993-a449-305815a53a8e
```
{: screen}

出力内容は、以下のようになります。

```
+---------------+--------------------------+
|    NAME       |     VALUE                |
+---------------+--------------------------+
|  message      | Delete session success   |
+---------------+--------------------------+
```
{: screen}


## ibmcloud at session list
{: #session_list}

アクティブ・セッションおよびその ID をリストします。

```
ibmcloud at session list 
```
{: codeblock}

**返される値**

<dl>
<dt>ID</dt>
<dd>セッション ID。</dd>

<dt>スペース</dt>
<dd>セッションがアクティブであるスペースの ID。</dd>

<dt>ユーザー名</dt>
<dd>セッションを作成したユーザーの {{site.data.keyword.IBM_notm}} ID。</dd>

<dt>作成時刻</dt>
<dd>セッションが作成された日時に対応するタイム・スタンプ。</dd>

<dt>アクセス時刻</dt>
<dd>セッションが最後に使用された時刻を示すタイム・スタンプ。</dd>
</dl>
 
**例**

セッションをリストするには、次のコマンドを実行します。

```
ibmcloud at session list
```
{: screen}

出力内容は、以下のようになります。

```
+--------------------------------------+--------------------------------------+-----------------------------------+--------------------------------+--------------------------------+
| ID                                   | SPACE                                | USERNAME                          | CREATE-TIME                    | ACCESS-TIME                    |
+--------------------------------------+--------------------------------------+-----------------------------------+--------------------------------+--------------------------------+
| fa3f1970-21f3-4e32-b480-1ffb41badc16 | 12345678-fb4f-acdf-a975-11335678r3fg | xxx@yyy.com                       | 2017-07-10T09:04:07.916788069Z | 2017-07-10T09:04:07.916788069Z |
| 9b8c4db8-5841-4993-a449-305815a53a8e | 12345678-fb4f-acdf-a975-11335678r3fg | xxx@yyy.com                       | 2017-07-11T09:19:14.666532796Z | 2017-07-12T09:19:14.666532796Z |
+--------------------------------------+--------------------------------------+-----------------------------------+--------------------------------+--------------------------------+
```
{: screen}


## ibmcloud at session show
{: #session_show}

単一セッションの状況を表示します。

```
ibmcloud at session show [arguments...]
```
{: codeblock}

**引数**

<dl>
<dt>セッション ID</dt>
<dd>情報を取得したいアクティブ・セッションの ID。</dd>
</dl>

**返される値**

<dl>
<dt>アクセス時刻</dt>
<dd>セッションが最後に使用された時刻を示すタイム・スタンプ。</dd>

<dt>作成時刻</dt>
<dd>セッションが作成された日時に対応するタイム・スタンプ。</dd>

<dt>日付範囲</dt>
<dd>イベントのフィルタリングに使用される日付を示します。 この日付範囲内で識別されたイベントが、セッションを通した管理に使用可能です。</dd>

<dt>ID</dt>
<dd>セッション ID。</dd>

<dt>スペース</dt>
<dd>セッションがアクティブであるスペースの ID。</dd>

<dt>タイプ・アカウント</dt>
<dd>この値は **ActivityTracker** に設定されます。</dd>

<dt>ユーザー名</dt>
<dd>セッションを作成したユーザーの {{site.data.keyword.IBM_notm}} ID。</dd>
</dl>

**例**

セッション ID *9b8c4db8-5841-4993-a449-305815a53a8e* のセッションの詳細を表示するには、次のコマンドを実行します。

```
ibmcloud at session show 9b8c4db8-5841-4993-a449-305815a53a8e
```
{: screen}

出力内容は、以下のようになります。

```
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| create-time  | 2017-07-25T11:54:00.20042645Z             |
| access-time  | 2017-07-25T11:54:00.20042645Z             |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
| id           | 9b8c4db8-5841-4993-a449-305815a53a8e      |
| space        | xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx      |
| username     | xxx@yyy.com                               |
+--------------+-------------------------------------------+
```
{: screen}


## ibmcloud at status
{: #status}

{{site.data.keyword.cloudaccesstrailshort}} イベントの状況に関する情報を返します。

```
ibmcloud at status [parameters] [arguments...]
```
{: codeblock}

**パラメーター**

<dl>
  <dt>--start value、-s value</dt>
  <dd>(オプション) 開始日を協定世界時 (UTC) *YYYY-MM-DD* で設定します。例えば、`2017-01-02` です。 <br>デフォルト値は、2 週間前に設定されます。
  </dd>
  
  <dt>--end value、-e value</dt>
  <dd>(オプション) 終了日を協定世界時 (UTC) *YYYY-MM-DD* で設定します。例えば、`2017-01-02` です。 <br>デフォルト値は、現在日付に設定されます。
  </dd>
  
  <dt>--at-account-level、-a </dt>
  <dd>(オプション) スコープをアカウント・レベルに設定します。 <br> **注:** アカウント情報を取得するには、この値を設定します。 <br>このパラメーターが指定されていない場合、デフォルト値は、現行スペース (つまり、`ibmcloud cf login` コマンドを使用してログインしたスペース) のみに設定されます。
  </dd>
  
</dl>


**注:** `ibmcloud at status` コマンドは、開始日および終了日が指定されていない場合、{{site.data.keyword.cloudaccesstrailshort}} に保管された最近 2 週間分のイベントのみを報告します。 

**返される値**   

<dl>
  <dt>日付</dt>
  <dd>協定世界時 (UTC) *YYYY-MM-DD* で表した日付。例えば、`2017-01-02` です。 
  </dd>
  
  <dt>カウント</dt>
  <dd>イベントの総数。
  </dd>
  
  <dt>サイズ</dt>
  <dd>イベントの合計サイズ (メガバイト単位)。
  </dd>

  <dt>タイプ</dt>
  <dd>この値は **ActivityTracker** に設定されます。
  </dd>
  
  <dt>検索可能</dt>
  <dd>このフィールドは、イベントが Kibana での検索に使用可能かどうかを示します。 <br>**「検索可能」**フィールドの値が *None* に設定されている場合、イベントはダウンロードすることはできますが、Kibana で分析することはできません。
  </dd>
  
</dl>

**例**

2017 年 7 月 20 日のイベントの詳細を表示するには、次のコマンドを実行します。

```
ibmcloud at status -s 2017-07-20 -e 2017-07-20
```
{: codeblock}


以下の出力のような情報が表示されます。

```
+------------+-----------+-------+------------------+--------------+
|   Date     |  Count    | Size  | Types            |  Searchable  | 
+------------+-----------+-------+------------------+--------------+
| 2017-07-20 |    1      | 2531  | ActivityTracker  | All          | 
+------------+-----------+-------+------------------+--------------+
```
{: screen}


