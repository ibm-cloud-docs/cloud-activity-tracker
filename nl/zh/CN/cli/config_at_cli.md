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

# 配置 Activity Tracker CLI
{: #config_at_cli}

{{site.data.keyword.cloudaccesstraillong}} 服务包含可用于在云中管理事件的命令行界面 (CLI)。该 CLI 是一个 Cloud Foundry (CF) 插件。可以使用命令来查看事件的状态、下载事件、复原事件、丢弃事件以及配置事件保留时间策略。
{:shortdesc}


## 安装 Activity Tracker CLI
{: #install_cli}

要安装 {{site.data.keyword.cloudaccesstrailshort}} CLI，请完成以下步骤：

1. 安装 {{site.data.keyword.Bluemix_notm}} CLI。

    有关更多信息，请参阅[通过 shell 安装](/docs/cli/reference/bluemix_cli/download_cli.html#shell_install)。
	
	例如，要在 Linux 上安装 {{site.data.keyword.Bluemix_notm}} CLI，请运行以下命令：
	
	```
	curl -fsSL https://clis.ng.bluemix.net/install/linux | sh
	```
	{: codeblock}

2. 安装 {{site.data.keyword.cloudaccesstrailshort}} CF 插件。

    * 对于 Linux，请参阅[在 Linux 上安装 {{site.data.keyword.cloudaccesstrailshort}} CLI](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#install_cli_linux)。
    * 对于 Windows，请参阅[在 Windows 上安装 {{site.data.keyword.cloudaccesstrailshort}} CLI](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#install_cli_windows)。
    * 对于 Mac OS X，请参阅[在 Mac OS X 上安装 {{site.data.keyword.cloudaccesstrailshort}} CLI](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#install_cli_mac)。
 
3. 验证 CLI 插件的安装。
  
    例如，检查插件的版本。运行以下命令：
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    输出如下所示：
   
    ```
    Invoking 'cf plugins'...

    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}

	
## 在 Linux 上安装 Activity Tracker CLI
{: #install_cli_linux}

要在 Linux 上安装 {{site.data.keyword.cloudaccesstrailshort}} CF 插件，请完成以下步骤：

1. 安装 {{site.data.keyword.cloudaccesstrailshort}} CLI 插件。

    1. 从 [Bluemix CLI 页面](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins)下载 {{site.data.keyword.cloudaccesstrailshort}} 服务 CLI 插件的最新发行版。 
	
		选择平台值：**linux64**。单击**保存文件**。 
    
    2. 解压缩插件。
    
        例如，要在 Ubuntu 中解压缩 `activitytracker-cli-linux_x64_v3.0.2.gz` 插件，请运行以下命令：
        
        ```
        gunzip activitytracker-cli-linux_x64_v3.0.2.gz
        ```
        {: codeblock}

    3. 使文件成为可执行文件。
    
        例如，要使文件 `activitytracker-cli-linux_x64_v3.0.2` 成为可执行文件，请运行以下命令：
        
        ```
        chmod a+x activitytracker-cli-linux_x64_v3.0.2
        ```
        {: codeblock}

    4. 安装日志记录 CF 插件。
    
        例如，要使文件 `activitytracker-cli-linux_x64_v3.0.2` 成为可执行文件，请运行以下命令：
        
        ```
        bx cf install-plugin -f activitytracker-cli-linux_x64_v3.0.2
        ```
        {: codeblock}

2. 验证 CLI 插件的安装。
  
    例如，检查插件的版本。运行以下命令：
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    输出如下所示：
   
    ```
    Invoking 'cf plugins'...

    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}


## 在 Windows 上安装 Activity Tracker CLI
{: #install_cli_windows}

要在 Windows 上安装 {{site.data.keyword.cloudaccesstrailshort}} CF 插件，请完成以下步骤：

1. 从 [Bluemix CLI 页面](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins)下载 {{site.data.keyword.cloudaccesstrailshort}} 服务 CLI 插件的最新发行版。 
	
	1. 选择平台值：**win64**。 
	2. 单击**保存文件**。  
    
2. 运行 **cf install-plugins** 命令以在 Windows 上安装 {{site.data.keyword.cloudaccesstrailshort}} 插件。 

    ```
	bx cf install-plugin PluginName
	```
	{: codeblock}
	
	其中，*PluginName* 是已下载的文件的名称。
	
    例如，要在 Windows 上安装插件，请从终端窗口运行以下命令：
	
	```
	bx cf install-plugin activitytracker-cli-windows_x64_v3.0.2.exe
	```
	{: codeblock}
	
    安装插件后，将显示以下消息：`Plugin IBM-ActivityTracker successfully installed.`

3. 验证 CLI 插件的安装。

    例如，检查插件的版本。运行以下命令：

    ```
    bx cf plugins
    ```
    {: codeblock}
    
    输出如下所示：

    ```
    Invoking 'cf plugins'...

    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}



## 在 Mac OS X 上安装 Activity Tracker CLI
{: #install_cli_mac}

要在 Mac OS X 上安装 {{site.data.keyword.cloudaccesstrailshort}} CF 插件，请完成以下步骤：

1. 从 [Bluemix CLI 页面](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins)下载 {{site.data.keyword.cloudaccesstrailshort}} 服务 CLI 插件的最新发行版。
	1. 选择平台值：**osx**。
	2. 单击**保存文件**。

2. 运行 **cf install-plugin** 命令以在 Mac OS X 上安装 {{site.data.keyword.cloudaccesstrailshort}} 插件。

    ```
	bx cf install-plugin PluginName
	```
	{: codeblock}
	
	其中，*PluginName* 是已下载的文件的名称。
	
    例如，要在 Mac OS X 上安装插件，请从终端运行以下命令：
	
	```
	bx cf install-plugin activitytracker-cli-mac_x64_v3.0.2
	```
	{: codeblock}
	
    安装插件后，将显示以下消息：`Plugin IBM-ActivityTracker successfully installed.`

3. 验证 CLI 插件的安装。

    例如，检查插件的版本。运行以下命令：

    ```
    bx cf plugins
    ```
    {: codeblock}

    输出如下所示：

    ```
    Invoking 'cf plugins'...

    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}



## 更新 Activity Tracker CLI
{: #update_cli}

要更新 {{site.data.keyword.cloudaccesstrailshort}} CF 插件，请完成以下步骤：

1. 从 [Bluemix CLI 页面](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins)下载 {{site.data.keyword.cloudaccesstrailshort}} 服务 CLI 插件的最新发行版。

	1. 选择平台值：**win64**（对于 Windows）、**osx**（对于 Mac OS X）或 **linux64**（对于 Linux）。
	2. 单击**保存文件**。

2. 运行 **cf install-plugin** 命令以在 Windows 上更新 {{site.data.keyword.cloudaccesstrailshort}} 插件。

    ```
	bx cf install-plugin PluginName -f
	```
	{: codeblock}
	
	其中
	
	* *PluginName* 是已下载的文件的名称。
	* *-f* 选项指示卸载插件的旧版本并安装新版本。
	
    例如，要在 Windows 上更新插件，请从终端窗口运行以下命令：
	
	```
	bx cf install-plugin activitytracker-cli-windows_x64_v3.0.2.exe
	```
	{: codeblock}
	
    安装插件后，将显示以下消息：`Plugin IBM-ActivityTracker successfully installed.`

3. 验证 CLI 插件的安装。

    例如，检查插件的版本。运行以下命令：

    ```
    bx cf plugins
    ```
    {: codeblock}

    输出如下所示：

    ```
    Invoking 'cf plugins'...

    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}



## 卸载 Activity Tracker CLI
{: #uninstall_cli}

要卸载 {{site.data.keyword.cloudaccesstrailshort}} CLI，请删除该插件。
{:shortdesc}

要卸载 {{site.data.keyword.cloudaccesstrailshort}} 服务 CLI，请完成以下步骤：

1. 验证安装的 {{site.data.keyword.cloudaccesstrailshort}} CLI 插件的版本。

    例如，检查插件的版本。运行以下命令：

    ```
    bx cf plugins
    ```
    {: codeblock}

    输出如下所示：

    ```
    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2           at       IBM Activity Tracker plug-in
    ```
    {: screen}
    
2. 如果插件已安装，请运行 `cf uninstall-plugin` 以卸载日志记录 CLI 插件。

    运行以下命令：

    ```
    bx cf uninstall-plugin IBM-ActivityTracker
    ```
    {: codeblock}
  
