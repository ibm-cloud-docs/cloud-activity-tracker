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

# Activity Tracker CLI の構成
{: #config_at_cli}

{{site.data.keyword.cloudaccesstraillong}} サービスには、クラウドでイベントを管理するために使用できるコマンド・ライン・インターフェース (CLI) が組み込まれています。この CLI は Cloud Foundry (CF) プラグインです。コマンドを使用して、イベント状況の表示、イベントのダウンロード、イベントのリストア、イベントの破棄、およびイベント保存ポリシーの構成を行うことができます。
{:shortdesc}


## Activity Tracker CLI のインストール
{: #install_cli}

{{site.data.keyword.cloudaccesstrailshort}} CLI をインストールするには、以下の手順を実行します。

1. {{site.data.keyword.Bluemix_notm}} CLI をインストールします。

    詳しくは、[シェルからのインストール](/docs/cli/reference/bluemix_cli/download_cli.html#shell_install)を参照してください。
	
	例えば、Linux に {{site.data.keyword.Bluemix_notm}} CLI をインストールするには、次のコマンドを実行します。
	
	```
	curl -fsSL https://clis.ng.bluemix.net/install/linux | sh
	```
	{: codeblock}

2. {{site.data.keyword.cloudaccesstrailshort}} CF プラグインをインストールします。

    * Linux の場合、[Linux への {{site.data.keyword.cloudaccesstrailshort}} CLI のインストール](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#install_cli_linux)を参照してください。
    * Windows の場合、[Windows への {{site.data.keyword.cloudaccesstrailshort}} CLI のインストール](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#install_cli_windows)を参照してください。
    * Mac OS X の場合、[Mac OS X への {{site.data.keyword.cloudaccesstrailshort}} CLI のインストール](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#install_cli_mac)を参照してください。
 
3. CLI プラグインのインストールを検証します。
  
    例えば、プラグインのバージョンを確認します。以下のコマンドを実行します。
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    出力は以下のようになります。
   
    ```
    'cf plugins'を起動しています...

    インストール済みプラグインをリストしています...
    OK

    プラグイン名        バージョン  コマンド名     コマンド・ヘルプ
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}

	
## Linux への Activity Tracker CLI のインストール
{: #install_cli_linux}

Linux に {{site.data.keyword.cloudaccesstrailshort}} CF プラグインをインストールするには、以下の手順を実行します。

1. {{site.data.keyword.cloudaccesstrailshort}} CLI プラグインをインストールします。

    1. 最新リリースの {{site.data.keyword.cloudaccesstrailshort}} サービス CLI プラグインを [Bluemix CLI ページ](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins)からダウンロードします。 
	
		プラットフォーム値**「linux64」**を選択します。
		**「ファイルの保存」**をクリックします。 
    
    2. プラグインを unzip します。
    
        例えば、Ubuntu で `activitytracker-cli-linux_x64_v3.0.2.gz` プラグインを unzip するには、次のコマンドを実行します。
        
        ```
        gunzip activitytracker-cli-linux_x64_v3.0.2.gz
        ```
        {: codeblock}

    3. ファイルを実行可能にします。
    
        例えば、ファイル `activitytracker-cli-linux_x64_v3.0.2` を実行可能にするには、次のコマンドを実行します。
        
        ```
        chmod a+x activitytracker-cli-linux_x64_v3.0.2
        ```
        {: codeblock}

    4. ロギング CF プラグインをインストールします。
    
        例えば、ファイル `activitytracker-cli-linux_x64_v3.0.2` を実行可能にするには、次のコマンドを実行します。
        
        ```
        bx cf install-plugin -f activitytracker-cli-linux_x64_v3.0.2
        ```
        {: codeblock}

2. CLI プラグインのインストールを検証します。
  
    例えば、プラグインのバージョンを確認します。以下のコマンドを実行します。
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    出力は以下のようになります。
   
    ```
    'cf plugins'を起動しています...

    インストール済みプラグインをリストしています...
    OK

    プラグイン名        バージョン  コマンド名     コマンド・ヘルプ
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}


## Windows への Activity Tracker CLI のインストール
{: #install_cli_windows}

Windows に {{site.data.keyword.cloudaccesstrailshort}} CF プラグインをインストールするには、以下の手順を実行します。

1. 最新リリースの {{site.data.keyword.cloudaccesstrailshort}} サービス CLI プラグインを [Bluemix CLI ページ](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins)からダウンロードします。 
	
	1. プラットフォーム値**「win64」**を選択します。 
	2. **「ファイルの保存」**をクリックします。  
    
2. **cf install-plugins** コマンドを実行して、{{site.data.keyword.cloudaccesstrailshort}} プラグインを Windows にインストールします。 

    ```
	bx cf install-plugin PluginName
	```
	{: codeblock}
	
	ここで、「PluginName」はダウンロードしたファイルの名前です。
	
    例えば、Windows にプラグインをインストールするには、端末ウィンドウから次のコマンドを実行します。
	
	```
	bx cf install-plugin activitytracker-cli-windows_x64_v3.0.2.exe
	```
	{: codeblock}
	
    プラグインがインストールされたら、「Plugin IBM-ActivityTracker successfully installed」というメッセージが表示されます。`

3. CLI プラグインのインストールを検証します。

    例えば、プラグインのバージョンを確認します。以下のコマンドを実行します。```
    bx cf plugins
    ```
    {: codeblock}
    
    出力は以下のようになります。

    ```
    'cf plugins'を起動しています...

    インストール済みプラグインをリストしています...
    OK

    プラグイン名        バージョン  コマンド名     コマンド・ヘルプ
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    
    ```
    {: screen}



## Mac OS X への Activity Tracker CLI のインストール
{: #install_cli_mac}

Mac OS X に {{site.data.keyword.cloudaccesstrailshort}} CF プラグインをインストールするには、以下の手順を実行します。

1. 最新リリースの {{site.data.keyword.cloudaccesstrailshort}} サービス CLI プラグインを [Bluemix CLI ページ](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins) からダウンロードします。
	
	1. プラットフォーム値「osx」を選択します。
	2. 「ファイルの保存」をクリックします。

2. 「cf install-plugin」コマンドを実行して、{{site.data.keyword.cloudaccesstrailshort}} プラグインを Mac OS X にインストールします。

    ```
	bx cf install-plugin PluginName
	```
	{: codeblock}
	
	ここで、「PluginName」はダウンロードしたファイルの名前です。
	
    例えば、Mac OS X にプラグインをインストールするには、端末から次のコマンドを実行します。
	
	```
	bx cf install-plugin activitytracker-cli-mac_x64_v3.0.2
	```
	{: codeblock}
	
    プラグインがインストールされたら、「Plugin IBM-ActivityTracker successfully installed」というメッセージが表示されます。`

3. CLI プラグインのインストールを検証します。

    例えば、プラグインのバージョンを確認します。以下のコマンドを実行します。```
    bx cf plugins
    ```
    {: codeblock}
    
    出力は以下のようになります。

    ```
    'cf plugins'を起動しています...

    インストール済みプラグインをリストしています...
    OK

    プラグイン名        バージョン  コマンド名     コマンド・ヘルプ
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in. 
    ```
    {: screen}

	

## Activity Tracker CLI の更新
{: #update_cli}

{{site.data.keyword.cloudaccesstrailshort}} CF プラグインを更新するには、以下の手順を実行します。

1. 最新リリースの {{site.data.keyword.cloudaccesstrailshort}} サービス CLI プラグインを [Bluemix CLI ページ](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins) からダウンロードします。
	
	1. プラットフォーム値「win64」(Windows の場合)、「osx」(Mac OS X の場合)、または「linux64」(Linux の場合) を選択します。
	2. 「ファイルの保存」をクリックします。

2. 「cf install-plugin」コマンドを実行して、Windows で {{site.data.keyword.cloudaccesstrailshort}} プラグインを更新します。

    ```
	bx cf install-plugin PluginName -f
	```
	{: codeblock}
	
	ここで、
	
	「PluginName」はダウンロードしたファイルの名前です。
	「-f」は、古いバージョンのプラグインをアンインストールした後で新しいものをインストールすることを指示するオプションです。
	
    例えば、Windows でプラグインを更新するには、端末ウィンドウから次のコマンドを実行します。
	
	```
	bx cf install-plugin activitytracker-cli-windows_x64_v3.0.2.exe
	```
	{: codeblock}
	
    プラグインがインストールされたら、「Plugin IBM-ActivityTracker successfully installed」というメッセージが表示されます。`

3. CLI プラグインのインストールを検証します。

    例えば、プラグインのバージョンを確認します。以下のコマンドを実行します。```
    bx cf plugins
    ```
    {: codeblock}
    
    出力は以下のようになります。

    ```
    'cf plugins'を起動しています...

    インストール済みプラグインをリストしています...
    OK

    プラグイン名        バージョン  コマンド名     コマンド・ヘルプ
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in. 
    ```
    {: screen}

	
	
## Activity Tracker CLI のアンインストール
{: #uninstall_cli}

{{site.data.keyword.cloudaccesstrailshort}} CLI をアンインストールするには、プラグインを削除します。
{:shortdesc}

{{site.data.keyword.cloudaccesstrailshort}} サービス CLI をアンインストールするには、以下の手順を実行します。

1. インストールされた {{site.data.keyword.cloudaccesstrailshort}} CLI プラグインのバージョンを検証します。

    例えば、プラグインのバージョンを確認します。以下のコマンドを実行します。```
    bx cf plugins
    ```
    {: codeblock}
    
    出力は以下のようになります。

    ```
    インストール済みプラグインをリストしています...
    OK

    プラグイン名        バージョン  コマンド名     コマンド・ヘルプ
    IBM-ActivityTracker   3.0.2           at       IBM Activity Tracker plug-in
    ```
    {: screen}
    
2. プラグインがインストールされている場合、「cf uninstall-plugin」を実行して、ロギング CLI プラグインをアンインストールします。
    以下のコマンドを実行します。```
    bx cf uninstall-plugin IBM-ActivityTracker
    ```
    {: codeblock}
  
