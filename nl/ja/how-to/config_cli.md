---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, config CLI

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

# Activity Tracker CLI の構成
{: #config_cli}

{{site.data.keyword.cloudaccesstraillong}} サービスには、クラウドでイベントを管理するために使用できるコマンド・ライン・インターフェース (CLI) が組み込まれています。 {{site.data.keyword.cloud_notm}} プラグインを使用して、イベントの状況の表示、イベントのダウンロード、および保存ポリシーの構成を行うことができます。 この CLI にはいくつかの種類のヘルプがあります。一般ヘルプではこの CLI およびサポートされるコマンドについての情報が、コマンド・ヘルプではコマンドの使用方法が、サブコマンド・ヘルプではコマンドに対するサブコマンドの使用方法が提供されます。
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} は非推奨になりました。 2019 年 5 月 9 日以降、新しい {{site.data.keyword.cloudaccesstrailshort}} インスタンスをプロビジョンできません。 既存のプレミアム・プランのインスタンスは、2019 年 9 月 30 日までサポートされます。 {{site.data.keyword.cloud_notm}} アカウントのアクティビティーのモニタリングを続行するには、[{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) のインスタンスをプロビジョンします。
{: deprecated}


## {{site.data.keyword.cloud_notm}} リポジトリーからの {{site.data.keyword.cloudaccesstrailshort}} プラグインのインストール
{: #install_cli_repo}

{{site.data.keyword.cloudaccesstrailshort}} CLI をインストールするには、以下の手順を実行します。

1. {{site.data.keyword.cloud_notm}} CLI をインストールします。

   詳しくは、[{{site.data.keyword.cloud_notm}} CLI のインストール](/docs/cli?topic=cloud-cli-ibmcloud-cli#ibmcloud-cli)を参照してください。
   
2. リポジトリー内でプラグインの名前を見つけます。 以下のコマンドを実行します。

    ```
    ibmcloud plugin repo-plugins
    ```
    {: codeblock}
    
    プラグインの名前は **activity-tracker** です。

3. {{site.data.keyword.cloudaccesstrailshort}} プラグインをインストールします。 以下のコマンドを実行します。

    ```
    ibmcloud plugin install activity-tracker
    ```
    {: codeblock}
 
4. {{site.data.keyword.cloudaccesstrailshort}} プラグインがインストールされたことを確認します。
  
    例えば、以下のコマンドを実行して、インストール済みのプラグインのリストを表示します。
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    


## ファイルからの {{site.data.keyword.cloudaccesstrailshort}} プラグインのインストール
{: #install_cli}

{{site.data.keyword.cloudaccesstrailshort}} CLI をインストールするには、以下の手順を実行します。

1. {{site.data.keyword.cloud_notm}} CLI をインストールします。

   詳しくは、[{{site.data.keyword.cloud_notm}} CLI のインストール](/docs/cli?topic=cloud-cli-ibmcloud-cli#ibmcloud-cli)を参照してください。

2. {{site.data.keyword.cloudaccesstrailshort}} プラグインをインストールします。

    * Linux の場合、[Linux への {{site.data.keyword.cloudaccesstrailshort}} プラグインのインストール](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-config_cli#install_cli_linux)を参照してください。
    * Windows の場合、[Windows への {{site.data.keyword.cloudaccesstrailshort}} プラグインのインストール](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-config_cli#install_cli_windows)を参照してください。
    * Mac OS X の場合、[Mac OS X への {{site.data.keyword.cloudaccesstrailshort}} プラグインのインストール](/docs/services//cloud-activity-tracker/how-to?topic=cloud-activity-tracker-config_cli#install_cli_mac)を参照してください。
 
3. CLI プラグインのインストールを検証します。
  
    例えば、プラグインのバージョンを確認します。 以下のコマンドを実行します。
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    


## ファイルからの Linux への {{site.data.keyword.cloudaccesstrailshort}} プラグインのインストール
{: #install_cli_linux}

Linux にプラグインをインストールするには、以下のステップを実行します。

1. プラグインをインストールします。

    最新リリースの {{site.data.keyword.cloudaccesstrailshort}} サービス CLI プラグイン (activity-tracker) を [{{site.data.keyword.cloud_notm}} CLI ページ ![外部リンク・アイコン](../../../icons/launch-glyph.svg "外部リンク・アイコン")](https://plugins.cloud.ibm.com/ui/repository.html){:new_window} からダウンロードします。
	
	* プラットフォーム値**「linux64」**を選択します。 
	
	* **「ファイルの保存」**をクリックします。 
    
2. プラグインをインストールします。 以下のコマンドを実行します。
        
    ```
    ibmcloud plugin install -f activity-tracker-linux-amd64-3.3.0
    ```
    {: codeblock}




## ファイルからの Windows への {{site.data.keyword.cloudaccesstrailshort}} プラグインのインストール
{: #install_cli_windows}

Windows にプラグインをインストールするには、以下のステップを実行します。

1. 最新リリースの {{site.data.keyword.cloudaccesstrailshort}} サービス CLI プラグイン (activity-tracker) を [{{site.data.keyword.cloud_notm}} CLI ページ ![外部リンク・アイコン](../../../icons/launch-glyph.svg "外部リンク・アイコン")](https://plugins.cloud.ibm.com/ui/repository.html){:new_window} からダウンロードします。 
	
	1. プラットフォーム値**「win64」**を選択します。 
	2. **「ファイルの保存」**をクリックします。  
    
2. プラグインをインストールします。 以下のコマンドを実行します。
        
    ```
    ibmcloud plugin install -f activity-tracker-windows-amd64-3.3.0.exe
    ```
    {: codeblock}

	

## ファイルからの Mac OS X への {{site.data.keyword.cloudaccesstrailshort}} プラグインのインストール
{: #install_cli_mac}

Mac OS X にプラグインをインストールするには、以下のステップを実行します。

1. 最新リリースの {{site.data.keyword.cloudaccesstrailshort}} サービス CLI プラグイン (activity-tracker) を [{{site.data.keyword.cloud_notm}} CLI ページ ![外部リンク・アイコン](../../../icons/launch-glyph.svg "外部リンク・アイコン")](https://plugins.cloud.ibm.com/ui/repository.html){:new_window} からダウンロードします。
	
	1. プラットフォーム値「`osx`」を選択します。 
	2. **「ファイルの保存」**をクリックします。  
    
2. プラグインをインストールします。 以下のコマンドを実行します。
        
    ```
    ibmcloud plugin install -f activity-tracker-darwin-amd64-3.3.0
    ```
    {: codeblock}

	
	
## {{site.data.keyword.cloudaccesstrailshort}} CLI のアンインストール
{: #uninstall_cli}

CLI をアンインストールするには、プラグインを削除します。
{:shortdesc}

{{site.data.keyword.cloudaccesstrailshort}} サービス CLI をアンインストールするには、以下の手順を実行します。

1. インストールされた CLI プラグインのバージョンを検証します。
  
    例えば、プラグインのバージョンを確認します。 以下のコマンドを実行します。
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    
2. プラグインがインストールされている場合、`ibmcloud plugin uninstall` を実行して、CLI プラグインをアンインストールします。

    以下のコマンドを実行します。
        
    ```
    ibmcloud plugin uninstall activity-tracker
    ```
    {: codeblock}
  

## リポジトリーからの {{site.data.keyword.cloudaccesstrailshort}} CLI の更新
{: #update_cli}

CLI を更新するには、*ibmcloud plugin update* コマンドを実行します。
{:shortdesc}

{{site.data.keyword.cloudaccesstrailshort}} サービス CLI を更新するには、以下のステップを実行します。

1. {{site.data.keyword.cloudaccesstrailshort}} プラグインを更新します。 以下のコマンドを実行します。

    ```
    ibmcloud plugin update activity-tracker
    ```
    {: codeblock}
 
2. CLI プラグインのインストールを検証します。
  
    例えば、プラグインのバージョンを確認します。 以下のコマンドを実行します。
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    





## 一般ヘルプの利用
{: #general_cli_help}

CLI に関する一般情報およびサポートされているコマンドについての情報を取得するには、以下のステップを実行します。

1. {{site.data.keyword.cloud_notm}} で、地域、組織、およびスペースにログインします。 
    
2. サポートされるコマンドおよび CLI についての情報をリストします。 以下のコマンドを実行します。

    ```
    ibmcloud at help 
    ```
    {: codeblock}
    
    

## コマンドに関するヘルプの利用
{: #command_cli_help}

コマンドの使用法に関するヘルプを利用するには、以下のステップを実行します。

1. {{site.data.keyword.cloud_notm}} で、地域、組織、およびスペースにログインします。 
    
2. サポートされるコマンドのリストを取得し、必要なコマンドを識別します。 次のコマンドを実行します。

    ```
    ibmcloud at help 
    ```
    {: codeblock}

3. 特定のコマンドに関するヘルプを取得します。 以下のコマンドを実行します。

    ```
    ibmcloud at help *Command*
    ```
    {: codeblock}
    
    ここで、*Command* は CLI コマンドの名前です (例: *status*)。



## サブコマンドに関するヘルプの利用
{: #subcommand_cli_help}

コマンドにはサブコマンドがある場合があります。 サブコマンドに関するヘルプを利用するには、以下のステップを実行します。

1. {{site.data.keyword.cloud_notm}} で、地域、組織、およびスペースにログインします。 
    
2. サポートされるコマンドのリストを取得し、必要なコマンドを識別します。 次のコマンドを実行します。

    ```
    ibmcloud at help 
    ```
    {: codeblock}

3. 特定のコマンドに関するヘルプを取得し、サポートされるサブコマンドを識別します。 以下のコマンドを実行します。

    ```
    ibmcloud at help *Command*
    ```
    {: codeblock}
    
    ここで、*Command* は CLI コマンドの名前です (例: *session*)。

4. 特定のコマンドに関するヘルプを取得し、サポートされるサブコマンドを識別します。 以下のコマンドを実行します。

    ```
    ibmcloud at *Command* help *Subcommand*
    ```
    {: codeblock}
    
    各部の意味は、次のとおりです。 
    
    *Command* は CLI コマンドの名前です (例: *status*)。

    *Subcommand* は、サポートされるサブコマンドの名前です。 例えば、コマンド *session* の有効なサブコマンドは *list* です。


## プラグインの詳細の表示
{: #show}
  
プラグイン詳細を表示するには、「ibmcloud plugin show activity-tracker」コマンドを使用します。 

```
ibmcloud plugin show activity-tracker
```
{: codeblock}
    




