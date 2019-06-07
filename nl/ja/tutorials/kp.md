---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, monitoring activity, tutorial

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


# {{site.data.keyword.cloudaccesstrailshort}} での {{site.data.keyword.keymanagementserviceshort}} アクティビティーのモニター
{: #kp}

このチュートリアルでは、{{site.data.keyword.keymanagementserviceshort}} サービスとユーザーとの対話を {{site.data.keyword.cloudaccesstrailfull}} サービスを使用してモニターする方法について説明します。 
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} は非推奨になりました。2019 年 5 月 9 日以降、新しい {{site.data.keyword.cloudaccesstrailshort}} インスタンスをプロビジョンできません。既存のプレミアム・プランのインスタンスは、2019 年 9 月 30 日までサポートされます。{{site.data.keyword.cloud_notm}} アカウントのアクティビティーのモニタリングを続行するには、[{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) のインスタンスをプロビジョンします。
{: deprecated}

1. {{site.data.keyword.cloudaccesstrailshort}} サービスをプロビジョンする方法を説明します。
2. {{site.data.keyword.cloudaccesstrailshort}} サービスによって自動的に収集されるアクティビティー・イベントを生成するためのクラウド・サービスの使用方法を説明します。
3.事前定義された {{site.data.keyword.cloudaccesstrailshort}} ダッシュボードを使用してサービスのクラウド・アクティビティーをモニターする方法を説明します。

次の図は、さまざまなコンポーネントと、サービスの状態を変更するユーザー開始アクティビティーがあったときに起こるアクションを示します。

![コンポーネントと、サービスの状態を変更するユーザー開始アクティビティーがあったときに起こるアクション](../images/AT_f1.png "コンポーネントと、サービスの状態を変更するユーザー開始アクティビティーがあったときに起こるアクション")



## 始めに
{: #kp_prereqs}

[{{site.data.keyword.cloud_notm}} アカウント](https://cloud.ibm.com/login)を作成します。 ユーザー ID は、{{site.data.keyword.cloudaccesstrailshort}} サービスを使用する予定のスペース内で開発者許可を持つ {{site.data.keyword.cloud_notm}} アカウントのメンバーまたは所有者でなければなりません。


## ステップ 1. Activity Tracker をプロビジョンする
{: #kp_step1}

アクティビティーをモニター対象のクラウド・サービスがプロビジョンされているのと同じ地域に {{site.data.keyword.cloudaccesstrailshort}} サービスをプロビジョンする必要があります。 {{site.data.keyword.cloudaccesstrailshort}} サービスがプロビジョンされた後、選択済みクラウド・サービスからイベントが自動的に収集されるようになります。 

**注:** このチュートリアルでは、米国南部地域でクラウド・サービス {{site.data.keyword.keymanagementservicelong_notm}} とユーザーとの対話を {{site.data.keyword.cloudaccesstrailshort}} サービスを使用してモニターする方法について説明します。 したがって、米国南部地域で {{site.data.keyword.cloudaccesstrailshort}} をプロビジョンする必要があります。 どの地域でサービスが使用可能なのかについては、[地域ごとのサービス](/docs/resources?topic=resources-services_region#services_region)を参照してください。

{{site.data.keyword.cloud_notm}} 内で {{site.data.keyword.cloudaccesstraillong_notm}} サービスのインスタンスをプロビジョンするには、以下の手順を実行します。

1. [{{site.data.keyword.cloud_notm}} にログイン ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://cloud.ibm.com/login){:new_window} します。
    
	ユーザー ID とパスワードを使用してログインすると、{{site.data.keyword.cloud_notm}} UI が開きます。

2. **「カタログ」**をクリックします。 {{site.data.keyword.cloud_notm}} で使用可能なサービスのリストが開きます。

3. **「セキュリティーおよび ID」**カテゴリーを選択して、表示されるサービスのリストをフィルタリングします。

    **注:** このサービスは**「開発者ツール」**カテゴリーからも使用可能です。

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
		<td>{{site.data.keyword.cloudaccesstrailshort}} サービスをプロビジョンすることを計画している組織を選択します。</td>
	  </tr>
	  <tr>
	    <td>スペースの選択:</td>
		<td>{{site.data.keyword.cloudaccesstrailshort}} サービスをプロビジョンすることを計画している、組織内のスペースを選択します。</td>
	  </tr>
	</table>

6. **「作成」**をクリックして、ログインしているスペース内で {{site.data.keyword.cloudaccesstrailshort}} サービスをプロビジョンします。
   

## ステップ 2.  クラウド・サービスを構成する  
{: #kp_step2}

このチュートリアルでは、{{site.data.keyword.cloud_notm}} 内で {{site.data.keyword.keymanagementserviceshort}} サービスの API アクティビティーをモニターする方法を示します。

{{site.data.keyword.cloud_notm}} 内で {{site.data.keyword.keymanagementserviceshort}} サービスを構成するには、以下のステップを実行します。

1. 米国南部地域に {{site.data.keyword.keymanagementserviceshort}} サービスのインスタンスをプロビジョンします。 詳しくは、[IBM Cloud コンソールからのプロビジョン](/docs/services/key-protect?topic=key-protect-provision#provision)を参照してください。

2. キーの処理に使用するユーザーの {{site.data.keyword.cloud_notm}} 許可を定義します。 

    キーを作成できるためには、ユーザーは、サービス役割が*マネージャー* または*ライター* に設定された IAM ポリシーを必要とします。

    キーを削除できるためには、ユーザーは、サービス役割が*マネージャー* に設定された IAM ポリシーを必要とします。

    キーを表示できるためには、ユーザーは、サービス役割が*リーダー* に設定された IAM ポリシーを必要とします。 


## ステップ 3. Activity Tracker イベントを生成する
{: #kp_step3}

このステップでは、{{site.data.keyword.cloudaccesstrailshort}} イベント・データを生成するために、{{site.data.keyword.keymanagementserviceshort}} サービスを使用してセキュリティー・キーを作成します。 詳しくは、[新規キーの作成](/docs/services/key-protect?topic=key-protect-create-standard-keys#create-standard-keys)を参照してください。

* 鍵の作成の結果として、{{site.data.keyword.cloudaccesstrailshort}} イベントが生成されます。
* {{site.data.keyword.cloudaccesstrailshort}} イベントは、イベントが生成される {{site.data.keyword.cloud_notm}} 地域内にある {{site.data.keyword.cloudaccesstrailshort}} **アカウント・ドメイン**で使用可能です。 

## ステップ 4. Activity Tracker イベントをモニターする
{: #kp_step4}

このステップでは、{{site.data.keyword.cloudaccesstrailshort}} イベントが生成されたことを {{site.data.keyword.cloud_notm}} UI を介して検証します。

イベントが作成されたことを検証するには、以下の手順を実行します。

1. アカウント・イベントを表示する許可をユーザーに付与します。 詳しくは、[アカウント・イベントの表示](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-view_acc_events#view_acc_events_account_events)および[アカウント・イベントを表示する許可の付与](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-grant_permissions#grant_acc_events)を参照してください。

2. {{site.data.keyword.cloud_notm}} ダッシュボードから {{site.data.keyword.cloudaccesstrailshort}} サービスを選択します。 このサービスのダッシュボードが開きます。

3. ビューを構成して、サービスをプロビジョンして鍵を追加したときに生成された {{site.data.keyword.keymanagementserviceshort}} イベントを検索します。

    * *「ログの表示」*フィールドで**「アカウント・ログ」**を選択します。
    * *「検索」*フィールドで **target.typeURI_str** を選択し、*「フィルター」*フィールドに `kms/secrets` と入力します。
	
    表示されるデータは、過去 24 時間の使用可能な {{site.data.keyword.keymanagementserviceshort}} イベントを示します。 
	


## 次のステップ
{: #kp_next_steps}

次に、{{site.data.keyword.cloudaccesstrailshort}} の事前定義済み Kibana ダッシュボードを使用して、イベント・ログのモニターおよび分析を行います。 Kibana を起動する方法については、[Kibana ダッシュボードへのナビゲート](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-launch_kibana#launch_kibana)を参照してください。 Kibana では、デフォルトで、スペース・アクティビティー・ログは **ActivityTracker_Space_Dashboard_in_24h** ダッシュボードで表示されます。

{{site.data.keyword.cloudaccesstrailshort}} CLI を使用することによって、コマンド・ラインからイベントを管理することもできます。 詳しくは、[イベント情報の表示](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-viewing_event_status#viewing_event_status)を参照してください。



