---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

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


# 配置事件保留原則
{: #configuring_retention_policy}

使用 **ibmcloud at option** 指令，可檢視及配置定義 {{site.data.keyword.cloudaccesstrailshort}}
中保留事件最長天數的保留原則。依預設，會停用保留原則，且事件會無限期地保留。在保留期間過期之後，即會自動刪除事件。
{:shortdesc}

您可以為帳戶中的所有空間設定相同的保留原則，也可以自訂空間的保留期間。 


## 停用空間的事件保留原則
{: #disable_retention_policy_space}

請完成下列步驟，以停用保留原則：

1. 登入 {{site.data.keyword.cloud_notm}}。 

    執行 [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) 指令以登入 {{site.data.keyword.cloud_notm}}，然後執行 [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) 指令，以設定您要在其中佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務的組織及空間。
	
2. 將保留期間設為 **-1**，以停用保留期間。執行下列指令：

    ```
    ibmcloud at option -r -1
    ```
    {: codeblock}
    
**範例**
    
例如，若要停用 ID 為 *d35da1e3-b345-475f-8502-bx cfgh436902a3* 之空間的保留期間，請執行下列指令：

```
ibmcloud at option -r -1
```
{: codeblock}

輸出如下：

```
+-----------------------------------------+-----------+
|               SPACEID                   | RETENTION |
+-----------------------------------------+-----------+
| d35da1e3-b345-475f-8502-bx cfgh436902a3 |        -1 |
+-----------------------------------------+-----------+
```
{: screen} 



## 檢查空間的日誌保留原則
{: #check_retention_policy_space}

若要取得針對 {{site.data.keyword.cloud_notm}} 空間所設定的保留期間，請完成下列步驟：

1. 登入 {{site.data.keyword.cloud_notm}}。 

    執行 [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) 指令以登入 {{site.data.keyword.cloud_notm}}，然後執行 [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) 指令，以設定您要在其中佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務的組織及空間。
	
2. 取得保留期間。執行下列指令：

    ```
    ibmcloud at option
    ```
    {: codeblock}

    空間 ID *d35da1e3-b345-475f-8502-bx cfgr436902a3* 的輸出為 30 天：

    ```
    +-----------------------------------------+-----------+
    |               SPACEID                   | RETENTION |
    +-----------------------------------------+-----------+
    | d35da1e3-b345-475f-8502-bx cfgh436902a3 |        30 |
    +-----------------------------------------+-----------+
    ```
    {: screen}
    

## 檢查帳戶中所有空間的日誌保留原則
{: #check_retention_policy_account}

若要取得針對帳戶中每一個 {{site.data.keyword.cloud_notm}} 空間所設定的保留期間，請完成下列步驟：

1. 登入 {{site.data.keyword.cloud_notm}}。 

    執行 [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) 指令以登入 {{site.data.keyword.cloud_notm}}，然後執行 [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) 指令，以設定您要在其中佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務的組織及空間。
    
2. 取得帳戶中每一個空間的保留期間。執行下列指令：

    ```
    ibmcloud at option -a
    ```
    {: codeblock}
	
	其中 *-a* 指出資訊包括帳戶中的所有空間。

    例如，執行指令的輸出如下：

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
    

## 跨帳戶設定日誌保留原則
{: #set_retention_policy_space}

若要設定 {{site.data.keyword.cloud_notm}} 帳戶的保留期間，請完成下列步驟：

1. 登入 {{site.data.keyword.cloud_notm}}。 

    執行 [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) 指令以登入 {{site.data.keyword.cloud_notm}}，然後執行 [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) 指令，以設定您要在其中佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務的組織及空間。
	
2. 設定保留期間。執行下列指令：

    ```
    ibmcloud at option -r Number_of_days - a
    ```
    {: codeblock}
    
    其中 
	* *-r* 是必須指定才能設定保留期間的選項。
	* *Number_of_days* 是一個整數，其定義您要保留事件的天數。 
	* *-a* 指出要求適用於帳戶中的所有空間。
    
    
**範例**
    
例如，若要將帳戶中的任何日誌類型僅保留 15 天，請執行下列指令：

```
ibmcloud at option -r 15 -a
```
{: codeblock}

輸出會針對帳戶中的每一個空間列出一個項目，包括保留期間的相關資訊：

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

## 設定空間的日誌保留原則
{: #set_retention_policy_account}

若要查看 {{site.data.keyword.cloud_notm}} 空間的保留期間，請完成下列步驟：

1. 登入 {{site.data.keyword.cloud_notm}}。 

    執行 [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) 指令以登入 {{site.data.keyword.cloud_notm}}，然後執行 [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) 指令，以設定您要在其中佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務的組織及空間。
    
2. 設定保留期間。執行下列指令：

    ```
    ibmcloud at option -r Number_of_days
    ```
    {: codeblock}
    
    其中 
	* *-r* 是必須指定才能設定保留期間的選項。
	* *Number_of_days* 是一個整數，其定義您要保留事件的天數。
    
    
**範例**
    
例如，若要保留一年的空間中可用事件，請執行下列指令：

```
ibmcloud at option -r 365
```
{: codeblock}

輸出如下：

```
+-----------------------------------------+-----------+
|               SPACEID                   | RETENTION |
+-----------------------------------------+-----------+
| d35da1e3-b345-475f-8502-bx cfgh436902a3 |       365 |
+-----------------------------------------+-----------+
```
{: screen}


