---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, UAA, security

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


# UAA トークンの取得
{: #auth_uaa}

{{site.data.keyword.Bluemix}} UAA を使用して、{{site.data.keyword.cloudaccesstraillong}} サービスでの作業に使用できる認証トークンを取得します。 {{site.data.keyword.cloud_notm}} CLI を使用するか、または API を使用することによって、認証トークンを取得できます。
{:shortdesc}

以下の事項を考慮してください。

* トークンには有効期限があります。 
* トークンを使用するときには、トークンの値からの*ベアラー* が含まれている必要があります。
		
## IBM Cloud CLI を使用した UAA トークンの取得
{: #uaa_cli_token}

UAA トークンを取得するには、以下の手順を実行します。

1. (前提条件) {{site.data.keyword.cloud_notm}} CLI をインストールします。

   詳しくは、[{{site.data.keyword.cloud_notm}} CLI のインストール](/docs/cli?topic=cloud-cli-ibmcloud-cli#ibmcloud-cli)を参照してください。
   
   CLI がインストールされている場合は、次のステップに進みます。
    
2. {{site.data.keyword.cloud_notm}} にログインします。 

    [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) コマンドを実行して {{site.data.keyword.cloud_notm}} にログインし、次に、[ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) コマンドを実行して、{{site.data.keyword.cloudaccesstrailshort}} サービスをプロビジョンする組織とスペースを設定します。
	
3. `ibmcloud iam oauth-tokens` コマンドを実行して、UAA トークンを取得します。

    ```
	ibmcloud iam oauth-tokens
	```
	{: codeblock}
	
	出力は UAA トークンを返します。


	


## API を使用したプラットフォーム API キーの UAA トークンの取得
{: #apikey_uaa_token}

プラットフォーム API キーの UAA トークンを取得するには、以下の手順を実行します。

1. 許可エンドポイントを取得します。 以下の cURL コマンドを実行します。

    ```
    curl https://api.ng.bluemix.net/v2/info
    ```
    {: codeblock}

    応答のフィールド **authorization_endpoint** からエンドポイント値を取得します。

2. プラットフォーム API キーを追加します。

    IBM Cloud コンソールで、**「管理」 > 「セキュリティー」 > 「プラットフォーム API キー」**と進みます。
    次に、API キーを作成します。

3. トークンを取得します。 以下の cURL コマンドを実行します。

    ```
    curl --user "cf:" --data-urlencode "grant_type=password" --data-urlencode "username=apikey" --data-urlencode "password=$APIKEY" --header "Content-Type: application/x-www-form-urlencoded" --header "Accept: application/json" "AUTHORIZATION_ENDPOINT/oauth/token"
    ```
    {: codeblock}

    ここで、 
    
    *APIKEY* は、前のステップで取得した API キー値です。
    
    *AUTHORIZATION_ENDPOINT* は、IAM サービスのエントリー・ポイントを表します。

    以下に例を示します。

    ```
    curl --user "cf:" --data-urlencode "grant_type=password" --data-urlencode "username=apikey" --data-urlencode "password=$APIKEY" --header "Content-Type: application/x-www-form-urlencoded" --header "Accept: application/json" "https://login.ng.bluemix.net/UAALoginServerWAR/oauth/token"
    ```
    {: codeblock}


