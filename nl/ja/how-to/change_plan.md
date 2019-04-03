---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, change plan

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



# プランの変更
{: #change_plan}

{{site.data.keyword.cloud_notm}} UI を介して、または、`ibmcloud service update` コマンドを実行することによって、{{site.data.keyword.cloudaccesstraillong}} サービス・プランを変更できます。 プランのアップグレード、またはライト・プランへの切り替えは、いつでも実行できます。
{:shortdesc}

## UI を介したサービス・プランの変更
{: #change_plan_ui}

{{site.data.keyword.cloud_notm}} UI を介してサービス・プランを変更するには、以下の手順を実行します。

1. {{site.data.keyword.cloud_notm}} にログインし、*ダッシュボード* から {{site.data.keyword.cloudaccesstraillong_notm}} サービスをクリックします。 
    
2. **「プラン」**タブを選択します。

    現在のプランに関する情報が表示されます。
	
3. 新しいプランを選択して、プランをアップグレードするか、ライト・プランに切り替えます。 

4. **「保存」**をクリックします。



## CLI を介したサービス・プランの変更
{: #change_plan_cli}

CLI を介してサービス・プランを変更するには、以下の手順を実行します。

1. {{site.data.keyword.cloud_notm}} にログインします。 

    [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) コマンドを実行して {{site.data.keyword.cloud_notm}} にログインし、次に、[ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) コマンドを実行して、{{site.data.keyword.cloudaccesstrailshort}} サービスをプロビジョンする組織とスペースを設定します。
	
2. `ibmcloud service list` コマンドを実行して、現在のプランを確認し、スペースで使用可能なサービスのリストから {{site.data.keyword.cloudaccesstrailshort}} サービス名を取得します。 

    プランを変更する際、**name** フィールドの値を使用する必要があります。 

    以下に例を示します。
	
	```
	$ ibmcloud service list
    Invoking 'cf services'...

    Getting services in org MyOrg / space dev as xxx@ibm.com...
    OK

    name                       service                  plan                 bound apps                               last operation
    Activity Tracker-zt          OK                     accessTrail             premium                                update succeeded
    ```
	{: screen}
    
3. プランをアップグレードするか、ライト・プランに切り替えます。 `ibmcloud service update` コマンドを実行します。
    
	```
	ibmcloud service update service_name [-p new_plan]
	```
	{: codeblock}
	
	ここで、 
	
	* *service_name* は、サービスの名前です。 `ibmcloud service list` コマンドを実行するとこの値を取得できます。
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
	    <td>free</td>
	  </tr>
	  <tr>
	    <td>プレミアム</td>
	    <td>premium</td>
	  </tr>
	</table>
	
	例えば、プランを*ライト*・プランに切り替えるには、以下のコマンドを実行します。
	
	```
	ibmcloud service update "Activity Tracker-zt" -p free
    Updating service instance Activity Tracker-zt as xxx@ibm.com...
    OK
	```
	{: screen}



