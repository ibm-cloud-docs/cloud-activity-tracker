---

copyright:
  years: 2017
lastupdated: "2017-09-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# プランの変更
{: #change_plan}

{{site.data.keyword.cloudaccesstraillong}} サービス・プランは、{{site.data.keyword.Bluemix_notm}} のサービス・ダッシュボードで変更するか、`cf update-service` コマンドを実行して変更できます。プランのアップグレード、またはライト・プランへの切り替えは、いつでも実行できます。
{:shortdesc}

## UI を介したサービス・プランの変更
{: #change_plan_ui}

サービス・ダッシュボードで {{site.data.keyword.Bluemix_notm}} のサービス・プランを変更するには、以下の手順を実行します。

1. {{site.data.keyword.Bluemix_notm}} にログインし、{{site.data.keyword.Bluemix_notm}} ダッシュボードから {{site.data.keyword.cloudaccesstraillong_notm}} サービスをクリックします。 
    
2. {{site.data.keyword.Bluemix_notm}} UI で**「プラン」**タブを選択します。

    現在のプランに関する情報が表示されます。
	
3. 新しいプランを選択して、プランをアップグレードするか、ライト・プランに切り替えます。 

4. **「保存」**をクリックします。



## CLI を介したサービス・プランの変更
{: #change_plan_cli}

CLI を介して Bluemix のサービス・プランを変更するには、以下の手順を実行します。

1. {{site.data.keyword.Bluemix_notm}} 地域、組織、およびスペースにログインします。 

    ```
    cf login -a Endpoint
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
		<tr>
		  <td>英国</td>
		  <td>api.eu-gb.bluemix.net</td>
		</tr>
		<tr>
		  <td>ドイツ</td>
		  <td>api.eu-de.bluemix.net</td>
		</tr>
	</table>

    表示される指示に従います。{{site.data.keyword.Bluemix_notm}} 資格情報を入力し、組織とスペースを選択します。 

    例えば、米国南部地域にログインするには、次のコマンドを実行します。
	
	```
	cf login -a api.ng.bluemix.net
	```
	{: codeblock}
	
2. `cf services` コマンドを実行して、現在のプランを確認し、スペースで使用可能なサービスのリストから {{site.data.keyword.cloudaccesstrailshort}} サービス名を取得します。 

    プランを変更する際、**name** フィールドの値を使用する必要があります。 

    以下に例を示します。
	
	```
	$ cf services
    xxx@yyy.com として組織 MyOrg / スペース dev 内のサービスを取得しています...
    OK

    名前                   サービス           プラン    バインド済みアプリ      最後の操作
    Activity Tracker-oj    activityTracker    premium                              create succeeded
    ```
	{: screen}
    
3. プランをアップグレードするか、ライト・プランに切り替えます。`cf update-service` コマンドを実行します。
    
	```
	cf update-service service_name [-p new_plan]
	```
	{: codeblock}
	
	ここで、 
	
	* *service_name* は、サービスの名前です。`cf services` コマンドを実行するとこの値を取得できます。
	* *new_plan* は、プランの名前です。
	
	次の表に、各種プランおよびサポートされている値を示します。
	
	<table>
	  <caption>表 1. プランのリスト</caption>
	  <tr>
	    <th>プラン</th>
	    <th>名前</th>
	  </tr>
	  <tr>
	    <td>ライト</td>
	    <td>lite</td>
	  </tr>
	  <tr>
	    <td>プレミアム</td>
	    <td>premium</td>
	  </tr>
	</table>
	
	例えば、プランを*ライト*・プランに切り替えるには、以下のコマンドを実行します。
	
	```
	cf update-service "Activity Tracker-oj" -p lite
    xxx@yyy.com としてサービス・インスタンス Activity Tracker-oj を更新しています...
    OK
	```
	{: screen}

4. 新規プランに変更されたことを検証します。`cf services` コマンドを実行します。

    ```
	cf services
    xxx@yyy.com として組織 MyOrg / スペース dev 内のサービスを取得しています...
    OK

    名前                   サービス           プラン    バインド済みアプリ      最後の操作
    Activity Tracker-oj    activityTracker    lite                              update succeeded
    ```
	{: screen}






