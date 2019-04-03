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


# 配置事件保留时间策略
{: #configuring_retention_policy}

保留时间策略可定义事件在 {{site.data.keyword.cloudaccesstrailshort}} 中保留的最大天数。使用 **ibmcloud at option** 命令可查看和配置保留时间策略。缺省情况下，保留时间策略为禁用状态，并且事件的保留时间为无限期。保留期到期后，系统会自动删除事件。
{:shortdesc}

您可以为帐户中的所有空间设置相同的保留时间策略，也可以为空间定制保留期。 


## 禁用空间的事件保留时间策略
{: #disable_retention_policy_space}

要禁用保留时间策略，请完成以下步骤：

1. 登录到 {{site.data.keyword.cloud_notm}}。 

    运行 [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) 命令以登录到 {{site.data.keyword.cloud_notm}}，然后运行 [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) 命令以设置要在其中供应 {{site.data.keyword.cloudaccesstrailshort}} 服务的组织和空间。
	
2. 将保留期设置为 **-1** 以禁用保留期。运行以下命令：

    ```
    ibmcloud at option -r -1
    ```
    {: codeblock}
    
**示例**
    
例如，要禁用标识为 *d35da1e3-b345-475f-8502-bx cfgh436902a3* 的空间的保留期，请运行以下命令：

```
ibmcloud at option -r -1
```
{: codeblock}

输出如下所示：

```
+-----------------------------------------+-----------+
|               SPACEID                   | RETENTION |
+-----------------------------------------+-----------+
| d35da1e3-b345-475f-8502-bx cfgh436902a3 |        -1 |
+-----------------------------------------+-----------+
```
{: screen} 



## 检查空间的日志保留时间策略
{: #check_retention_policy_space}

要获取为 {{site.data.keyword.cloud_notm}} 空间设置的保留期，请完成以下步骤：

1. 登录到 {{site.data.keyword.cloud_notm}}。 

    运行 [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) 命令以登录到 {{site.data.keyword.cloud_notm}}，然后运行 [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) 命令以设置要在其中供应 {{site.data.keyword.cloudaccesstrailshort}} 服务的组织和空间。
	
2. 获取保留期。运行以下命令：

    ```
    ibmcloud at option
    ```
    {: codeblock}

    空间标识 *d35da1e3-b345-475f-8502-bx cfgh436902a3* 的输出为 30 天：

    ```
    +-----------------------------------------+-----------+
    |               SPACEID                   | RETENTION |
    +-----------------------------------------+-----------+
    | d35da1e3-b345-475f-8502-bx cfgh436902a3 |        30 |
    +-----------------------------------------+-----------+
    ```
    {: screen}
    

## 检查帐户中所有空间的日志保留时间策略
{: #check_retention_policy_account}

要获取为帐户中每个 {{site.data.keyword.cloud_notm}} 空间设置的保留期，请完成以下步骤：

1. 登录到 {{site.data.keyword.cloud_notm}}。 

    运行 [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) 命令以登录到 {{site.data.keyword.cloud_notm}}，然后运行 [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) 命令以设置要在其中供应 {{site.data.keyword.cloudaccesstrailshort}} 服务的组织和空间。
    
2. 获取帐户中每个空间的保留期。运行以下命令：

    ```
    ibmcloud at option -a
    ```
    {: codeblock}
	
	其中，*-a* 指示信息包括帐户中的所有空间。

    例如，运行该命令后的输出如下所示：

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
    

## 跨帐户设置日志保留时间策略
{: #set_retention_policy_space}

要设置 {{site.data.keyword.cloud_notm}} 帐户的保留期，请完成以下步骤：

1. 登录到 {{site.data.keyword.cloud_notm}}。 

    运行 [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) 命令以登录到 {{site.data.keyword.cloud_notm}}，然后运行 [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) 命令以设置要在其中供应 {{site.data.keyword.cloudaccesstrailshort}} 服务的组织和空间。
	
2. 设置保留期。运行以下命令：

    ```
    ibmcloud at option -r Number_of_days - a
    ```
    {: codeblock}
    
    其中
 
	* *-r* 是设置保留期时必须指定的选项。
	* *Number_of_days* 是一个整数，用于定义事件的保留天数。 
	* 其中，*-a* 指示请求适用于帐户中的所有空间。
    
    
**示例**
    
例如，要使帐户中任何类型的日志仅保留 15 天，请运行以下命令：

```
ibmcloud at option -r 15 -a
```
{: codeblock}

输出内容列出了帐户中每个空间的条目，包括保留期相关信息：

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

## 设置空间的日志保留时间策略
{: #set_retention_policy_account}

要查看 {{site.data.keyword.cloud_notm}} 空间的保留期，请完成以下步骤：

1. 登录到 {{site.data.keyword.cloud_notm}}。 

    运行 [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) 命令以登录到 {{site.data.keyword.cloud_notm}}，然后运行 [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) 命令以设置要在其中供应 {{site.data.keyword.cloudaccesstrailshort}} 服务的组织和空间。
    
2. 设置保留期。运行以下命令：

    ```
    ibmcloud at option -r Number_of_days
    ```
    {: codeblock}
    
    其中
 
	* *-r* 是设置保留期时必须指定的选项。
	* *Number_of_days* 是一个整数，用于定义事件的保留天数。
    
    
**示例**
    
例如，要使空间中可用的事件保留 1 年，请运行以下命令：

```
ibmcloud at option -r 365
```
{: codeblock}

输出如下所示：

```
+-----------------------------------------+-----------+
|               SPACEID                   | RETENTION |
+-----------------------------------------+-----------+
| d35da1e3-b345-475f-8502-bx cfgh436902a3 |       365 |
+-----------------------------------------+-----------+
```
{: screen}


