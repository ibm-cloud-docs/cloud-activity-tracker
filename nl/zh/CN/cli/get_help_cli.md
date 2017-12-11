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

# 获取有关如何使用 Activity Tracker CLI 的帮助
{: #get_help_cli}

{{site.data.keyword.cloudaccesstrailshort}} CLI 提供不同类型的帮助：一般帮助用于了解 CLI 和受支持命令，命令帮助用于了解如何使用命令，子命令帮助用于了解如何使用命令的子命令。
{:shortdesc}


## 获取一般帮助
{: #general_cli_help}

要获取有关 CLI 以及支持哪些命令的常规信息，请完成以下步骤：

1. 登录到 {{site.data.keyword.Bluemix_notm}} 区域、组织和空间。 

    例如，要登录到美国南部区域，请运行以下命令：
	
	```
    bx login -a https://api.ng.bluemix.net
    ```
    {: codeblock}
    
2. 列出有关受支持命令和 CLI 的信息。运行以下命令：

    ```
    bx cf at help 
    ```
    {: codeblock}
    
    

## 获取有关命令的帮助
{: #command_cli_help}

要获取有关如何使用命令的帮助，请完成以下步骤：

1. 登录到 {{site.data.keyword.Bluemix_notm}} 区域、组织和空间。 

    例如，要登录到美国南部区域，请运行以下命令：
	
	```
    bx login -a https://api.ng.bluemix.net
    ```
    {: codeblock}
    
2. 获取受支持命令的列表，并确定需要的命令。运行以下命令：

    ```
    bx cf at help 
    ```
    {: codeblock}

3. 获取有关命令的帮助。运行以下命令：

    ```
    bx cf at help *Command*
    ```
    {: codeblock}
    
     其中，*Command* 是 CLI 命令的名称，例如 *status*。



## 获取有关子命令的帮助
{: #subcommand_cli_help}

一个命令可以有多个子命令。要获取有关子命令的帮助，请完成以下步骤：

1. 登录到 {{site.data.keyword.Bluemix_notm}} 区域、组织和空间。 

    例如，要登录到美国南部区域，请运行以下命令：
	
	```
    bx login -a https://api.ng.bluemix.net
    ```
    {: codeblock}
    
2. 获取受支持命令的列表，并确定需要的命令。运行以下命令：

    ```
    bx cf at help
    ```
    {: codeblock}

3. 获取有关命令的帮助，并确定受支持子命令。运行以下命令：

    ```
    bx cf at help *Command*
    ```
    {: codeblock}
    
    其中，*Command* 是 CLI 命令的名称，例如 *session*。

4. 获取有关命令的帮助，并确定受支持子命令。运行以下命令：

    ```
    bx cf at *Command* help *Subcommand*
    ```
    {: codeblock}
    
    其中
 
    
    * *Command* 是 CLI 命令的名称，例如 *status*。
    * *Subcommand* 是受支持子命令的名称，例如，对于命令 *session*，有效的子命令为 *list*。




