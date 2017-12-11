---

copyright:
  years: 2016, 2017

lastupdated: "2017-09-17"

---


{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# Activity Tracker サービスのプロビジョン
{: #provision}

{{site.data.keyword.Bluemix}} UI またはコマンド・ラインから {{site.data.keyword.cloudaccesstraillong}} サービスをプロビジョンできます。
{:shortdesc}


## UI からのプロビジョン
{: #ui}

{{site.data.keyword.Bluemix_notm}} 内で {{site.data.keyword.cloudaccesstraillong_notm}} サービスのインスタンスをプロビジョンするには、以下の手順を実行します。

1. {{site.data.keyword.Bluemix_notm}} アカウントにログインします。

    {{site.data.keyword.Bluemix_notm}} ダッシュボードは、[http://bluemix.net ![外部リンク・アイコン](../../../icons/launch-glyph.svg "外部リンク・アイコン")](http://bluemix.net){:new_window} にあります。
    
	ユーザー ID とパスワードを使用してログインすると、{{site.data.keyword.Bluemix_notm}} UI が開きます。

2. **「カタログ」**をクリックします。{{site.data.keyword.Bluemix_notm}} で使用可能なサービスのリストが開きます。

3. **「セキュリティー」**カテゴリーを選択して、表示されたサービスのリストをフィルタリングします。

    このサービスは**「DevOps」**カテゴリーにもあります。

4. **Activity Tracker** タイルをクリックします。

5. サービスがプロビジョンされる場所を定義する情報を構成します。 

    次の表に示されているようにデータを入力します。 

    <table>
	  <caption>表 1. {{site.data.keyword.cloudaccesstrailshort}} サービスをプロビジョンするために必要なフィールド</caption>
	  <tr>
	    <th>フィールド</th>
		<th>値</th>
	  </tr>
	  <tr>
	    <td>デプロイする地域の選択:</td>
		<td>有効な値は、米国南部、英国、ドイツです。</td>
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

6. サービス・プランを選択します。 

    デフォルトでは、**「無料」**プランが設定されます。

    詳しくは、[サービス・プラン](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#plans)を参照してください。
	
7. **「作成」**をクリックして、ログインしている {{site.data.keyword.Bluemix_notm}} スペース内で {{site.data.keyword.cloudaccesstrailshort}} サービスをプロビジョンします。
  
 

## CLI からのプロビジョン
{: #cli}

コマンド・ラインを使用して {{site.data.keyword.Bluemix_notm}} 内で {{site.data.keyword.cloudaccesstraillong_notm}} サービスのインスタンスをプロビジョンするには、以下の手順を実行します。

1. Cloud Foundry (CF) CLI をインストールします。CF CLI がインストールされている場合は、次のステップに進みます。

   詳しくは、[Installing the cf CLI ![外部リンク・アイコン](../../../icons/launch-glyph.svg "外部リンク・アイコン")](http://docs.cloudfoundry.org/cf-cli/install-go-cli.html){: new_window} を参照してください。 
    
2. {{site.data.keyword.Bluemix_notm}} 地域、組織、およびスペースにログインします。 

    例えば、米国南部地域にログインするには、以下のコマンドを実行します。

    ```
    cf login -a https://api.ng.bluemix.net
    ```
    {: codeblock}

    表示される指示に従います。{{site.data.keyword.Bluemix_notm}} 資格情報を入力し、組織とスペースを選択します。
	
3. `cf create-service` コマンドを実行して、インスタンスをプロビジョンします。

    ```
	cf create-service service_name service_plan service_instance_name
	```
	{: codeblock}
	
	各部分の説明:
	
	* service_name は、サービスの名前、つまり「activityTracker」です。
	* service_plan は、サービス・プラン名です。プランのリストについては、[サービス・プラン](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#plans) を参照してください。
	* service_instance_name は、作成する新規サービス・インスタンスに使用する名前です。
	
	この cf コマンドについて詳しくは、 [cf create-service](/docs/cli/reference/cfcommands/index.html#cf_create-service) を参照してください。

	例えば、ライト・プランで {{site.data.keyword.cloudaccesstrailshort}} サービスのインスタンスを作成するには、次のコマンドを実行します。
	
	```
	cf create-service activityTracker free my_activity_tracker_svc
	```
	{: codeblock}
	
4. サービスが正常に作成されたことを確認します。以下のコマンドを実行します。```	
	cf services
	```
	{: codeblock}
	
	このコマンドの実行による出力は以下のようになります。
	
	```
    xxx@yyy.com として組織 MyOrg / スペース MySpace 内のサービスを取得しています...
    OK
    
    名前                           サービス                  プラン                   バインド済みアプリ              最後の操作
    my_activity_tracker_svc        activityTracker          free                                           create succeeded
	```
	{: screen}

	



