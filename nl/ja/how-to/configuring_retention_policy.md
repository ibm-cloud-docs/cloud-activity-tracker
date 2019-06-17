---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, configure retention policy

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

# イベント保存ポリシーの構成
{: #configuring_retention_policy}

コマンド **ibmcloud at option** を使用して、{{site.data.keyword.cloudaccesstrailshort}} 内でイベントが保持される最大日数を定義する保存ポリシーを表示および構成します。 デフォルトでは、保存ポリシーは無効になっており、イベントは無期限に保持されます。 保存期間を過ぎると、イベントは自動的に削除されます。 
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} は非推奨になりました。 2019 年 5 月 9 日以降、新しい {{site.data.keyword.cloudaccesstrailshort}} インスタンスをプロビジョンできません。 既存のプレミアム・プランのインスタンスは、2019 年 9 月 30 日までサポートされます。 {{site.data.keyword.cloud_notm}} アカウントのアクティビティーのモニタリングを続行するには、[{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) のインスタンスをプロビジョンします。
{: deprecated}


アカウント内のすべてのスペースに同じ保存ポリシーを設定するか、特定のスペースの保存期間をカスタマイズすることができます。 


## スペースのイベント保存ポリシーの無効化
{: #disable_retention_policy_space}

保存ポリシーを無効化するには、以下のステップを実行します。

1. {{site.data.keyword.cloud_notm}} にログインします。 

    [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) コマンドを実行して {{site.data.keyword.cloud_notm}} にログインし、次に、[ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) コマンドを実行して、{{site.data.keyword.cloudaccesstrailshort}} サービスをプロビジョンする組織とスペースを設定します。
	
2. 保存期間を無効にするため、保存期間を **-1** に設定します。 次のコマンドを実行します。

    ```
    ibmcloud at option -r -1
    ```
    {: codeblock}
    
**例**
    
例えば、ID *d35da1e3-b345-475f-8502-bx cfgh436902a3* のスペースの保存期間を無効にするには、次のコマンドを実行します。

```
ibmcloud at option -r -1
```
{: codeblock}

出力は次のとおりです。

```
+-----------------------------------------+-----------+
|               SPACEID                   | RETENTION |
+-----------------------------------------+-----------+
| d35da1e3-b345-475f-8502-bx cfgh436902a3 |        -1 |
+-----------------------------------------+-----------+
```
{: screen} 



## スペースのログ保存ポリシーの確認
{: #check_retention_policy_space}

{{site.data.keyword.cloud_notm}} スペースに設定されている保存期間を取得するには、以下のステップを実行します。

1. {{site.data.keyword.cloud_notm}} にログインします。 

    [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) コマンドを実行して {{site.data.keyword.cloud_notm}} にログインし、次に、[ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) コマンドを実行して、{{site.data.keyword.cloudaccesstrailshort}} サービスをプロビジョンする組織とスペースを設定します。
	
2. 保存期間を取得します。 次のコマンドを実行します。

    ```
    ibmcloud at option
    ```
    {: codeblock}

    スペース ID *d35da1e3-b345-475f-8502-bx cfgh436902a3* の出力は 30 日間です。

    ```
    +-----------------------------------------+-----------+
    |               SPACEID                   | RETENTION |
    +-----------------------------------------+-----------+
    | d35da1e3-b345-475f-8502-bx cfgh436902a3 |        30 |
    +-----------------------------------------+-----------+
    ```
    {: screen}
    

## アカウントのすべてのスペースのログ保存ポリシーの確認
{: #check_retention_policy_account}

アカウントの各 {{site.data.keyword.cloud_notm}} スペースに設定されている保存期間を取得するには、以下のステップを実行します。

1. {{site.data.keyword.cloud_notm}} にログインします。 

    [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) コマンドを実行して {{site.data.keyword.cloud_notm}} にログインし、次に、[ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) コマンドを実行して、{{site.data.keyword.cloudaccesstrailshort}} サービスをプロビジョンする組織とスペースを設定します。
    
2. アカウントの各スペースの保存期間を取得します。 次のコマンドを実行します。

    ```
    ibmcloud at option -a
    ```
    {: codeblock}
	
	ここで、*-a*  は、情報にアカウント内のすべてのスペースが含まれることを示します。

    例えば、コマンド実行の出力は以下のようになります。

    ```
    +-----------------------------------------+-----------+
    |               SPACEID                   | RETENTION |
    +-----------------------------------------+-----------+
    | d35da1e3-b345-475f-8502-bx cfgh436902a3 |        30 |
    +-----------------------------------------+-----------+
    | fdew45e3-b345-4365-8502-bx cfghrfthy5a3 |        30 |
    +-----------------------------------------+-----------+
    ```
    {: screen}
    

## アカウント全体でのログ保存ポリシーの設定
{: #set_retention_policy_space}

{{site.data.keyword.cloud_notm}} アカウントの保存期間を設定するには、以下のステップを実行します。

1. {{site.data.keyword.cloud_notm}} にログインします。 

    [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) コマンドを実行して {{site.data.keyword.cloud_notm}} にログインし、次に、[ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) コマンドを実行して、{{site.data.keyword.cloudaccesstrailshort}} サービスをプロビジョンする組織とスペースを設定します。
	
2. 保存期間を設定します。 次のコマンドを実行します。

    ```
    ibmcloud at option -r Number_of_days - a
    ```
    {: codeblock}
    
    ここで、 
	* *-r* は、保存期間を設定するために指定する必要があるオプションです。
	* *Number_of_days* は、イベントを保持する日数を定義する整数です。 
	* *-a* は、この要求がアカウント内のすべてのスペースに適用されることを示します。
    
    
**例**
    
例えば、アカウントのすべてのタイプのログを 15 日間だけ保持するには、次のコマンドを実行します。

```
ibmcloud at option -r 15 -a
```
{: codeblock}

出力では、以下のように、保存期間についての情報を含む項目がアカウントのスペースごとにリストされます。

```
+-----------------------------------------+-----------+
|               SPACEID                   | RETENTION |
+-----------------------------------------+-----------+
| d35da1e3-b345-475f-8502-bx cfgh436902a3 |        15 |
+-----------------------------------------+-----------+
| fdew45e3-b345-4365-8502-bx cfghrfthy5a3 |        15 |
+-----------------------------------------+-----------+
```
{: screen}

## スペースのログ保存ポリシーの設定
{: #set_retention_policy_account}

{{site.data.keyword.cloud_notm}} スペースの保存期間を表示するには、以下のステップを実行します。

1. {{site.data.keyword.cloud_notm}} にログインします。 

    [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) コマンドを実行して {{site.data.keyword.cloud_notm}} にログインし、次に、[ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) コマンドを実行して、{{site.data.keyword.cloudaccesstrailshort}} サービスをプロビジョンする組織とスペースを設定します。
    
2. 保存期間を設定します。 次のコマンドを実行します。

    ```
    ibmcloud at option -r Number_of_days
    ```
    {: codeblock}
    
    ここで、 
	* *-r* は、保存期間を設定するために指定する必要があるオプションです。
	* *Number_of_days* は、イベントを保持する日数を定義する整数です。
    
    
**例**
    
例えば、スペース内の使用可能なイベントを 1 年間保持するには、次のコマンドを実行します。

```
ibmcloud at option -r 365
```
{: codeblock}

出力は次のとおりです。

```
+-----------------------------------------+-----------+
|               SPACEID                   | RETENTION |
+-----------------------------------------+-----------+
| d35da1e3-b345-475f-8502-bx cfgh436902a3 |       365 |
+-----------------------------------------+-----------+
```
{: screen}


