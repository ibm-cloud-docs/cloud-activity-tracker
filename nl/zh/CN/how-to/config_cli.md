---

copyright:
  years: 2016, 2019
lastupdated: "2019-02-18"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# 配置 Activity Tracker CLI
{: #config_cli}

{{site.data.keyword.cloudaccesstraillong}} 服务包含可用于在云中管理事件的命令行界面 (CLI)。您可以使用 {{site.data.keyword.cloud_notm}} 插件来查看事件的状态，下载事件以及配置事件保留策略。该 CLI 提供了以下不同类型的帮助：一般帮助（用于了解 CLI 和受支持的命令）、命令帮助（用于了解如何使用命令）和子命令帮助（用于了解如何使用某个命令的子命令）。
{:shortdesc}


## 通过 {{site.data.keyword.cloud_notm}} 存储库安装 {{site.data.keyword.cloudaccesstrailshort}} 插件
{: #install_cli_repo}

要安装 {{site.data.keyword.cloudaccesstrailshort}} CLI，请完成以下步骤：

1. 安装 {{site.data.keyword.cloud_notm}} CLI。

   有关更多信息，请参阅[安装 {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-ibmcloud-cli#ibmcloud-cli)。
   
2. 在存储库中查找插件的名称。运行以下命令：

    ```
    ibmcloud plugin repo-plugins
    ```
    {: codeblock}
    
    插件的名称为 **activity-tracker**。

3. 安装 {{site.data.keyword.cloudaccesstrailshort}} 插件。运行以下命令：

    ```
    ibmcloud plugin install activity-tracker -r Bluemix
    ```
    {: codeblock}
 
4. 验证 {{site.data.keyword.cloudaccesstrailshort}} 插件是否已安装。
  
    例如，运行以下命令来查看已安装插件的列表：
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    


## 通过文件安装 {{site.data.keyword.cloudaccesstrailshort}} 插件
{: #install_cli}

要安装 {{site.data.keyword.cloudaccesstrailshort}} CLI，请完成以下步骤：

1. 安装 {{site.data.keyword.cloud_notm}} CLI。

   有关更多信息，请参阅[安装 {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-ibmcloud-cli#ibmcloud-cli)。

2. 安装 {{site.data.keyword.cloudaccesstrailshort}} 插件。

    * 对于 Linux，请参阅[在 Linux 上安装 {{site.data.keyword.cloudaccesstrailshort}} 插件](/docs/services/cloud-activity-tracker/how-to/config_cli.html#install_cli_linux)。
    * 对于 Windows，请参阅[在 Windows 上安装 {{site.data.keyword.cloudaccesstrailshort}} 插件](/docs/services/cloud-activity-tracker/how-to/config_cli.html#install_cli_windows)。
    * 对于 Mac OS X，请参阅[在 Mac OS X 上安装 {{site.data.keyword.cloudaccesstrailshort}} 插件](/docs/services//cloud-activity-tracker/how-to/config_cli.html#install_cli_mac)。
 
3. 验证 CLI 插件的安装。
  
    例如，检查插件的版本。运行以下命令：
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    


## 在 Linux 上通过文件安装 {{site.data.keyword.cloudaccesstrailshort}} 插件
{: #install_cli_linux}

要在 Linux 上安装插件，请完成以下步骤：

1. 安装插件。

    从 [{{site.data.keyword.cloud_notm}} CLI 页面](https://clis.ng.bluemix.net/ui/repository.html#bluemix-plugins)下载 {{site.data.keyword.cloudaccesstrailshort}} 服务 CLI 插件 (activity-tracker) 的最新发行版。 
	
	* 选择平台值：**linux64**。 
	
	* 单击**保存文件**。 
    
2. 安装插件。运行以下命令：
        
    ```
    ibmcloud plugin install -f activity-tracker-linux-amd64-3.3.0
    ```
    {: codeblock}




## 在 Windows 上通过文件安装 {{site.data.keyword.cloudaccesstrailshort}} 插件
{: #install_cli_windows}

要在 Windows 上安装插件，请完成以下步骤：

1. 从 [{{site.data.keyword.cloud_notm}} CLI 页面](https://clis.ng.bluemix.net/ui/repository.html#bluemix-plugins)下载 {{site.data.keyword.cloudaccesstrailshort}} 服务 CLI 插件 (activity-tracker) 的最新发行版。 
	
	1. 选择平台值：**win64**。 
	2. 单击**保存文件**。  
    
2. 安装插件。运行以下命令：
        
    ```
    ibmcloud plugin install -f activity-tracker-windows-amd64-3.3.0.exe
    ```
    {: codeblock}

	

## 在 Mac OS X 上通过文件安装 {{site.data.keyword.cloudaccesstrailshort}} 插件
{: #install_cli_mac}

要在 Mac OS X 上安装插件，请完成以下步骤：

1. 从 [{{site.data.keyword.cloud_notm}} CLI 页面](https://clis.ng.bluemix.net/ui/repository.html#bluemix-plugins)下载 {{site.data.keyword.cloudaccesstrailshort}} 服务 CLI 插件 (activity-tracker) 的最新发行版。 
	
	1. 选择平台值：**osx**。 
	2. 单击**保存文件**。  
    
2. 安装插件。运行以下命令：
        
    ```
    ibmcloud plugin install -f activity-tracker-darwin-amd64-3.3.0
    ```
    {: codeblock}

	
	
## 卸载 {{site.data.keyword.cloudaccesstrailshort}} CLI
{: #uninstall_cli}

要卸载 CLI，请删除插件。
{:shortdesc}

要卸载 {{site.data.keyword.cloudaccesstrailshort}} 服务 CLI，请完成以下步骤：

1. 确认所安装的 CLI 插件的版本。
  
    例如，检查插件的版本。运行以下命令：
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    
2. 如果插件已安装，请运行 `ibmcloud plugin uninstall` 来卸载 CLI 插件。

    运行以下命令：
        
    ```
    ibmcloud plugin uninstall activity-tracker
    ```
    {: codeblock}
  

## 从存储库更新 {{site.data.keyword.cloudaccesstrailshort}} CLI
{: #update_cli}

要更新 CLI，请运行 *ibmcloud plugin update* 命令。
{:shortdesc}

要更新 {{site.data.keyword.cloudaccesstrailshort}} 服务 CLI，请完成以下步骤：

1. 更新 {{site.data.keyword.cloudaccesstrailshort}} 插件。运行以下命令：

    ```
    ibmcloud plugin update activity-tracker -r Bluemix
    ```
    {: codeblock}
 
2. 验证 CLI 插件的安装。
  
    例如，确认插件的版本。运行以下命令：
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    





## 获取一般帮助
{: #general_cli_help}

要获取有关 CLI 以及支持哪些命令的常规信息，请完成以下步骤：

1. 登录到 {{site.data.keyword.cloud_notm}} 中的区域、组织和空间。 
    
2. 列出有关受支持命令和 CLI 的信息。运行以下命令：

    ```
    ibmcloud at help 
    ```
    {: codeblock}
    
    

## 获取有关命令的帮助
{: #command_cli_help}

要获取有关如何使用命令的帮助，请完成以下步骤：

1. 登录到 {{site.data.keyword.cloud_notm}} 中的区域、组织和空间。 
    
2. 获取受支持命令的列表，并确定需要的命令。运行以下命令：

    ```
    ibmcloud at help 
    ```
    {: codeblock}

3. 获取有关命令的帮助。运行以下命令：

    ```
    ibmcloud at help *Command*
    ```
    {: codeblock}
    
     其中，*Command* 是 CLI 命令的名称，例如 *status*。



## 获取有关子命令的帮助
{: #subcommand_cli_help}

一个命令可以有多个子命令。要获取有关子命令的帮助，请完成以下步骤：

1. 登录到 {{site.data.keyword.cloud_notm}} 中的区域、组织和空间。 
    
2. 获取受支持命令的列表，并确定需要的命令。运行以下命令：

    ```
    ibmcloud at help 
    ```
    {: codeblock}

3. 获取有关命令的帮助，并确定受支持子命令。运行以下命令：

    ```
    ibmcloud at help *Command*
    ```
    {: codeblock}
    
    其中，*Command* 是 CLI 命令的名称，例如 *session*。

4. 获取有关命令的帮助，并确定受支持子命令。运行以下命令：

    ```
    ibmcloud at *Command* help *Subcommand*
    ```
    {: codeblock}
    
    其中
 
    
    * *Command* 是 CLI 命令的名称，例如 *status*。
    * *Subcommand* 是受支持子命令的名称，例如，对于命令 *session*，有效的子命令为 *list*。


## 显示插件的详细信息
{: #show}
  
使用“ibmcloud plugin show activity-tracker”命令来显示插件详细信息。 

```
ibmcloud plugin show activity-tracker
```
{: codeblock}
    




