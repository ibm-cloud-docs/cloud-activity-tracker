---

copyright:
  years: 2016, 2017
lastupdated: "2017-09-17"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 入門チュートリアル
{: #getting-started-with-cla}

{{site.data.keyword.cloudaccesstrailfull}} サービスは、{{site.data.keyword.IBM}} クラウド内のサービスの状態を変更するユーザー開始アクティビティーを記録します。このチュートリアルでは、クラウド・サービスとユーザーとの対話を {{site.data.keyword.cloudaccesstrailfull}} サービスを使用してモニターする方法について説明します。
{:shortdesc}

この入門チュートリアルの目標は、以下のとおりです。

1. {{site.data.keyword.cloudaccesstrailshort}} サービスをプロビジョンする方法を説明すること。
2. {{site.data.keyword.cloudaccesstrailshort}} サービスによって自動的に収集されるアクティビティー・イベントを生成するためのクラウド・サービスの使用方法を説明すること。イベントは Cloud Auditing Data Federation (CADF) 標準に準拠しています。
3. 事前定義された {{site.data.keyword.cloudaccesstrailshort}} ダッシュボードを使用してサービスのクラウド・アクティビティーをモニターする方法を説明すること。

次の図は、さまざまなコンポーネントと、サービスの状態を変更するユーザー開始アクティビティーがあったときに起こるアクションを示します。

![コンポーネントと、サービスの状態を変更するユーザー開始アクティビティーがあったときに起こるアクション](images/AT_f1.png "コンポーネントと、サービスの状態を変更するユーザー開始アクティビティーがあったときに起こるアクション")



## 始めに
{: #prereqs}

[{{site.data.keyword.Bluemix_notm}} アカウント](https://console.bluemix.net/registration/)を作成します。ユーザー ID は、{{site.data.keyword.cloudaccesstrailshort}} サービスを使用する予定のスペース内で開発者許可を持つ {{site.data.keyword.Bluemix_notm}} アカウントのメンバーまたは所有者でなければなりません。


## ステップ 1: Activity Tracker をプロビジョンする
{: #step1}

アクティビティーをモニターしたいクラウド・サービスがプロビジョンされているのと同じ地域およびスペース内で {{site.data.keyword.cloudaccesstrailshort}} サービスをプロビジョンする必要があります。{{site.data.keyword.cloudaccesstrailshort}} サービスがプロビジョンされた後、そのスペース内にプロビジョンされた選択済みクラウド・サービスからイベントが自動的に収集されるようになります。{{site.data.keyword.cloudaccesstrailshort}} を通してアクティビティーをモニターできるサービスのリストについては、[サポートされるクラウド・サービス](/docs/services/cloud-activity-tracker/cloud_services.html#cloud_services)を参照してください。

**注:** このチュートリアルでは、クラウド・サービス {{site.data.keyword.keymanagementservicelong_notm}} とユーザーとの対話を {{site.data.keyword.cloudaccesstrailshort}} サービスを使用してモニターする方法について説明します。{{site.data.keyword.keymanagementserviceshort}} サービスは、米国南部で使用可能です。したがって、米国南部地域の、{{site.data.keyword.keymanagementserviceshort}} サービスが使用可能であるのと同じスペース内に、{{site.data.keyword.cloudaccesstrailshort}} をプロビジョンする必要があります。どの地域でサービスが使用可能なのかについては、[地域別のサービス](/docs/services/services_region.html#services_region)を参照してください。

{{site.data.keyword.Bluemix_notm}} 内で {{site.data.keyword.cloudaccesstraillong_notm}} サービスのインスタンスをプロビジョンするには、以下の手順を実行します。

1. {{site.data.keyword.Bluemix_notm}} アカウントにログインします。

    {{site.data.keyword.Bluemix_notm}} ダッシュボードは、[http://bluemix.net ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://bluemix.net){:new_window} にあります。
    
	ユーザー ID とパスワードを使用してログインすると、{{site.data.keyword.Bluemix_notm}} UI が開きます。

2. **「カタログ」**をクリックします。{{site.data.keyword.Bluemix_notm}} で使用可能なサービスのリストが開きます。

3. **「セキュリティー」**カテゴリーを選択して、表示されたサービスのリストをフィルタリングします。

4. **Activity Tracker** タイルをクリックします。 

5. サービスがプロビジョンされる場所を定義する情報を構成します。 

    次の表に示されているようにデータを入力します。 

    <table>
	  <caption>表 1. {{site.data.keyword.cloudaccesstrailshort}} サービスをプロビジョンするために必要なフィールド</caption>
	  <tr>
	    <th width="50%">フィールド</th>
		<th width="50%">値</th>
	  </tr>
	  <tr>
	    <td>デプロイする地域の選択:</td>
		<td>米国南部</td>
	  </tr>
	  <tr>
	    <td>組織の選択:</td>
		<td>アクティビティーをモニターすることを計画している組織を選択します。</td>
	  </tr>
	  <tr>
	    <td>スペースの選択:</td>
		<td>アクティビティーをモニターすることを計画している、選択した組織内のスペースを選択します。</td>
	  </tr>
	</table>

6. **「作成」**をクリックして、ログインしている {{site.data.keyword.Bluemix_notm}} スペース内で {{site.data.keyword.cloudaccesstrailshort}} サービスをプロビジョンします。
   

## ステップ 2:  クラウド・サービスをプロビジョンする 
{: #step2}
	
以下の手順を実行して、{{site.data.keyword.Bluemix_notm}} 米国南部地域で {{site.data.keyword.keymanagementserviceshort}} サービスのインスタンスをプロビジョンします。

1. {{site.data.keyword.Bluemix_notm}} アカウントにログインします。

    {{site.data.keyword.Bluemix_notm}} ダッシュボードは、[http://bluemix.net ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://bluemix.net){:new_window} にあります。
	
	ユーザー ID とパスワードを使用してログインすると、{{site.data.keyword.Bluemix_notm}} UI が開きます。

2. **「カタログ」**をクリックします。{{site.data.keyword.Bluemix_notm}} で使用可能なサービスのリストが開きます。

    **「セキュリティー」**カテゴリーを選択して、表示されたサービスのリストをフィルタリングします。

3. **Key Protect** タイルを選択します。

4. サービスがプロビジョンされる場所を定義する情報を構成します。 

    次の表に示されているようにデータを入力します。 

    <table>
	  <caption>表 2. {{site.data.keyword.keymanagementserviceshort}} サービスをプロビジョンするために必要なフィールド</caption>
	  <tr>
	    <th width="50%">フィールド</th>
		<th width="50%">値</th>
	  </tr>
	  <tr>
	    <td>デプロイする地域の選択:</td>
		<td>米国南部</td>
	  </tr>
	  <tr>
	    <td>組織の選択:</td>
		<td>{{site.data.keyword.cloudaccesstrailshort}} サービスをプロビジョンするよう選択した組織を選択します。</td>
	  </tr>
	  <tr>
	    <td>スペースの選択:</td>
		<td>{{site.data.keyword.cloudaccesstrailshort}} サービスをプロビジョンするよう選択したスペースを選択します。</td>
	  </tr>
	</table>

5. **「作成」**をクリックして、ログインしている {{site.data.keyword.Bluemix_notm}} スペース内で {{site.data.keyword.keymanagementserviceshort}} サービスをプロビジョンします。


## ステップ 3: Activity Tracker イベントを生成する
{: # step3}

このステップでは、{{site.data.keyword.cloudaccesstrailshort}} イベント・データを生成するために、{{site.data.keyword.keymanagementserviceshort}} サービスを使用してセキュリティー・キーを作成します。 

以下の手順を実行して {{site.data.keyword.cloudaccesstrailshort}} イベントを生成します。

1. {{site.data.keyword.Bluemix_notm}} ダッシュボードから **Key Protect** サービスを選択します。{{site.data.keyword.keymanagementserviceshort}} ダッシュボードが開きます。次に、**「管理」**タブを選択します。

2. **「鍵の追加」**をクリックします。新しいウィンドウが開きます。

3. **「鍵の生成」**を選択し、以下の手順を実行します。

    * 鍵の名前を入力します (例: *MyFirstKey*)。

    * 鍵のアルゴリズムを選択します。

    * **「鍵の追加」**をクリックします。 
	
鍵の作成の結果として、{{site.data.keyword.cloudaccesstrailshort}} イベントが生成されます。

## ステップ 4: Activity Tracker イベントをモニターする
{: #step4}

このステップでは、{{site.data.keyword.cloudaccesstrailshort}} イベントが生成されたことを {{site.data.keyword.Bluemix_notm}} UI を介して検証します。

イベントが作成されたことを検証するには、以下の手順を実行します。

1. {{site.data.keyword.Bluemix_notm}} ダッシュボードから {{site.data.keyword.cloudaccesstrailshort}} サービスを選択します。このサービスのダッシュボードが開きます。

2. ビューを構成して、サービスをプロビジョンして鍵を追加したときに生成された {{site.data.keyword.keymanagementserviceshort}} イベントを検索します。

    * *「ログの表示」*フィールドで**「スペース・ログ」**を選択します。
    * *「検索フィールド」*フィールドで**「target.name」**を選択します。
    * *「フィルター」*フィールドに **ibm-key-protect** を入力します。
	
    表示されるデータは、過去 24 時間の使用可能な {{site.data.keyword.keymanagementserviceshort}} イベントを示します。 
	
	![UI でのイベントの表示](images/bmx_ui_space_view.png "UI でのイベントの表示")


## 次のステップ
{: #next_steps}

次に、{{site.data.keyword.cloudaccesstrailshort}} の事前定義済み Kibana ダッシュボードを使用して、イベント・ログのモニターおよび分析を行います。Kibana を起動する方法については、[Kibana ダッシュボードへのナビゲート](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_kibana.html#launch_kibana)を参照してください。 

Kibana では、デフォルトで、スペース・アクティビティー・ログは **ActivityTracker_Space_Search_in_24h** ダッシュボードで表示されます。

![Kibana でのイベントの表示](images/kibana_space_view.png "Kibana でのイベントの表示")

{{site.data.keyword.cloudaccesstrailshort}} CLI を使用することによって、コマンド・ラインからイベントを管理することもできます。詳しくは、[イベント情報の表示](/docs/services/cloud-activity-tracker/how-to/manage-events-cli/viewing_event_information.html#viewing_event_status)を参照してください。

                                                                                                                      

