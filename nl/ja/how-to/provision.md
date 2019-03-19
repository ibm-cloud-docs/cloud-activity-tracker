---

copyright:
  years: 2016, 2019
lastupdated: "2019-02-18"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}



# Activity Tracker のプロビジョン
{: #provision}

{{site.data.keyword.Bluemix}} UI またはコマンド・ラインから {{site.data.keyword.cloudaccesstraillong}} サービスをプロビジョンできます。
{:shortdesc}


## UI からのプロビジョン
{: #provision_ui}

{{site.data.keyword.cloud_notm}} 内で {{site.data.keyword.cloudaccesstraillong_notm}} サービスのインスタンスをプロビジョンするには、以下の手順を実行します。

1. {{site.data.keyword.cloud_notm}} アカウントにログインします。

    {{site.data.keyword.cloud_notm}} UI は、[http://bluemix.net ![外部リンク・アイコン](../../../icons/launch-glyph.svg "外部リンク・アイコン")](http://bluemix.net){:new_window} にあります。
    
	ユーザー ID とパスワードを使用してログインすると、{{site.data.keyword.cloud_notm}} UI が開きます。

2. **「カタログ」**をクリックします。 {{site.data.keyword.cloud_notm}} で使用可能なサービスのリストが開きます。

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
		<td>有効な値は、米国南部、英国、ドイツ、シドニーです。</td>
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

    詳しくは、[サービス・プラン](/docs/services/cloud-activity-tracker/how-to/change_plan.html#change_plan)を参照してください。
	
7. **「作成」**をクリックして、ログインしている {{site.data.keyword.cloud_notm}} スペース内で {{site.data.keyword.cloudaccesstrailshort}} サービスをプロビジョンします。
  
 

## CLI からのプロビジョン
{: #provision_cli}

コマンド・ラインを使用して {{site.data.keyword.cloud_notm}} 内で {{site.data.keyword.cloudaccesstrailshort}} サービスのインスタンスをプロビジョンするには、以下の手順を実行します。

1. [前提条件] {{site.data.keyword.cloud_notm}} CLI をインストールします。

   詳しくは、[{{site.data.keyword.cloud_notm}} CLI のインストール](/docs/cli?topic=cloud-cli-ibmcloud-cli#ibmcloud-cli)を参照してください。
   
   CLI がインストールされている場合は、次のステップに進みます。
    
2. {{site.data.keyword.cloud_notm}} にログインします。 

    [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) コマンドを実行して {{site.data.keyword.cloud_notm}} にログインし、次に、[ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) コマンドを実行して、{{site.data.keyword.cloudaccesstrailshort}} サービスをプロビジョンする組織とスペースを設定します。
	
3. `ibmcloud service create` コマンドを実行して、インスタンスをプロビジョンします。

    ```
	ibmcloud service create service_name service_plan service_instance_name
	```
	{: codeblock}
	
	各部の意味は、次のとおりです。
	
	* service_name は、サービスの名前、つまり**「accessTrail」**です。
	* service_plan は、サービス・プラン名です。 プランのリストについては、[サービス・プラン](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#activity_tracker_ov_plan)を参照してください。
	* service_instance_name は、作成する新規サービス・インスタンスに使用する名前です。

	例えば、標準プランで {{site.data.keyword.cloudaccesstrailshort}} サービスのインスタンスを作成するには、以下のコマンドを実行します。
	
	```
	ibmcloud service create accessTrail free my_activitytracker_svc
	```
	{: codeblock}
	
4. サービスが正常に作成されたことを確認します。 以下のコマンドを実行します。

    ```	
	ibmcloud service list
	```
	{: codeblock}
	
	このコマンドの実行による出力は以下のようになります。
	
	```
    Getting services in org MyOrg / space MySpace as xxx@yyy.com...
    OK
    
    name                           service                  plan                   bound apps              last operation
    my_activitytracker_svc         accessTrail             free                                            create succeeded
	```
	{: screen}

	




