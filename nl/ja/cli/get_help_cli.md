---

copyright:
  years: 2016, 2017
lastupdated: "2017-09-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Activity Tracker CLI の使用法に関するヘルプの取得
{: #get_help_cli}

{{site.data.keyword.cloudaccesstrailshort}} CLI にはいくつかのタイプのヘルプがあります。つまり、CLI およびサポートされるコマンドについて知ることのできる一般ヘルプ、コマンドの使用法を知ることのできるコマンド・ヘルプ、コマンドのサブコマンドの使用法を知ることのできるサブコマンド・ヘルプがあります。
{:shortdesc}


## 一般ヘルプの利用
{: #general_cli_help}

CLI に関する一般情報およびサポートされているコマンドについての情報を取得するには、以下のステップを実行します。

1. {{site.data.keyword.Bluemix_notm}} 地域、組織、およびスペースにログインします。 

    例えば、米国南部地域にログインするには、以下のコマンドを実行します。
	
	```
    bx login -a https://api.ng.bluemix.net
    ```
    {: codeblock}
    
2. サポートされるコマンドおよび CLI についての情報をリストします。以下のコマンドを実行します。

    ```
    bx cf at help 
    ```
    {: codeblock}
    
    

## コマンドに関するヘルプの利用
{: #command_cli_help}

コマンドの使用法に関するヘルプを利用するには、以下のステップを実行します。

1. {{site.data.keyword.Bluemix_notm}} 地域、組織、およびスペースにログインします。 

    例えば、米国南部地域にログインするには、以下のコマンドを実行します。
	
	```
    bx login -a https://api.ng.bluemix.net
    ```
    {: codeblock}
    
2. サポートされるコマンドのリストを取得し、必要なコマンドを識別します。次のコマンドを実行します。

    ```
    bx cf at help 
    ```
    {: codeblock}

3. 特定のコマンドに関するヘルプを取得します。以下のコマンドを実行します。

    ```
    bx cf at help *Command*
    ```
    {: codeblock}
    
    ここで、*Command* は CLI コマンドの名前です (例: *status*)。



## サブコマンドに関するヘルプの利用
{: #subcommand_cli_help}

コマンドにはサブコマンドがある場合があります。サブコマンドに関するヘルプを利用するには、以下のステップを実行します。

1. {{site.data.keyword.Bluemix_notm}} 地域、組織、およびスペースにログインします。 

    例えば、米国南部地域にログインするには、以下のコマンドを実行します。
	
	```
    bx login -a https://api.ng.bluemix.net
    ```
    {: codeblock}
    
2. サポートされるコマンドのリストを取得し、必要なコマンドを識別します。次のコマンドを実行します。

    ```
    bx cf at help 
    ```
    {: codeblock}

3. 特定のコマンドに関するヘルプを取得し、サポートされるサブコマンドを識別します。以下のコマンドを実行します。

    ```
    bx cf at help *Command*
    ```
    {: codeblock}
    
    ここで、*Command* は CLI コマンドの名前です (例: *session*)。

4. 特定のコマンドに関するヘルプを取得し、サポートされるサブコマンドを識別します。以下のコマンドを実行します。

    ```
    bx cf at *Command* help *Subcommand*
    ```
    {: codeblock}
    
    ここで、 
    
    * *Command* は CLI コマンドの名前です (例: *status*)。
    * *Subcommand* はサポートされるサブコマンドの名前です (例: コマンド *session* の有効なサブコマンドは *list* です)。




