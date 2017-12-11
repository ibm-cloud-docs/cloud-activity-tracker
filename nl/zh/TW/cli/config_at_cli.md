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

{{site.data.keyword.cloudaccesstraillong}} 服務包含一個指令行介面 (CLI)，您可以用來管理雲端中的事件。CLI 是 Cloud Foundry (CF) 外掛程式。您可以使用指令來檢視事件的狀態、下載事件、還原事件、捨棄事件，以及配置事件保留原則。
{:shortdesc}


## 安裝 Activity Tracker CLI
{: #install_cli}

若要安裝 {{site.data.keyword.cloudaccesstrailshort}} CLI，請完成下列步驟：

1. 安裝 {{site.data.keyword.Bluemix_notm}} CLI。

    如需相關資訊，請參閱[從 Shell 安裝](/docs/cli/reference/bluemix_cli/download_cli.html#shell_install)。
	
	例如，若要在 Linux 上安裝 {{site.data.keyword.Bluemix_notm}} CLI，請執行下列指令：
	
	```
	curl -fsSL https://clis.ng.bluemix.net/install/linux | sh
	```
	{: codeblock}

2. 安裝 {{site.data.keyword.cloudaccesstrailshort}} CF 外掛程式。

    * 若為 Linux，請參閱[在 Linux 上安裝 {{site.data.keyword.cloudaccesstrailshort}} CLI](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#install_cli_linux)。
    * 若為 Windows，請參閱[在 Windows 上安裝 {{site.data.keyword.cloudaccesstrailshort}} CLI](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#install_cli_windows)。
    * 若為 Mac OS X，請參閱[在 Mac OS X 上安裝 {{site.data.keyword.cloudaccesstrailshort}} CLI](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#install_cli_mac)。
 
3. 驗證 CLI 外掛程式的安裝。
  
    例如，檢查外掛程式的版本。執行下列指令：
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    輸出的外觀如下：
   
    ```
    Invoking 'cf plugins'...

    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}

	
## 在 Linux 上安裝 Activity Tracker CLI
{: #install_cli_linux}

請完成下列步驟，在 Linux 上安裝 {{site.data.keyword.cloudaccesstrailshort}} CF 外掛程式：

1. 安裝 {{site.data.keyword.cloudaccesstrailshort}} CLI 外掛程式。

    1. 從 [Bluemix CLI 頁面](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins)下載最新版本的 {{site.data.keyword.cloudaccesstrailshort}} 服務 CLI 外掛程式。 
	
		選取平台值：**linux64**。按一下**儲存檔案**。 
    
    2. 解壓縮外掛程式。
    
        例如，若要在 Ubuntu 中解壓縮 `activitytracker-cli-linux_x64_v3.0.2.gz` 外掛程式，請執行下列指令：
        
        ```
        gunzip activitytracker-cli-linux_x64_v3.0.2.gz
        ```
        {: codeblock}

    3. 使檔案成為可執行檔。
    
        例如，若要使檔案 `activitytracker-cli-linux_x64_v3.0.2` 成為可執行檔，請執行下列指令：
        
        ```
        chmod a+x activitytracker-cli-linux_x64_v3.0.2
        ```
        {: codeblock}

    4. 安裝記載 CF 外掛程式。
    
        例如，若要使檔案 `activitytracker-cli-linux_x64_v3.0.2` 成為可執行檔，請執行下列指令：
        
        ```
        bx cf install-plugin -f activitytracker-cli-linux_x64_v3.0.2
        ```
        {: codeblock}

2. 驗證 CLI 外掛程式的安裝。
  
    例如，檢查外掛程式的版本。執行下列指令：
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    輸出的外觀如下：
   
    ```
    Invoking 'cf plugins'...

    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}


## 在 Windows 上安裝 Activity Tracker CLI
{: #install_cli_windows}

請完成下列步驟，在 Windows 上安裝 {{site.data.keyword.cloudaccesstrailshort}} CF 外掛程式：

1. 從 [Bluemix CLI 頁面](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins)下載最新版本的 {{site.data.keyword.cloudaccesstrailshort}} 服務 CLI 外掛程式。 
	
	1. 選取平台值：**win64**。 
	2. 按一下**儲存檔案**。  
    
2. 執行 **cf install-plugins** 指令，以在 Windows 上安裝 {{site.data.keyword.cloudaccesstrailshort}} 外掛程式。 

	```
	bx cf install-plugin PluginName
	```
	{: codeblock}
	
	其中 *PluginName* 是您已下載的檔案名稱。
	
    例如，若要在 Windows 上安裝外掛程式，請從終端機視窗執行下列指令：
	
	```
	bx cf install-plugin activitytracker-cli-windows_x64_v3.0.2.exe
	```
	{: codeblock}
	
    安裝好外掛程式之後，您會得到下列訊息：`Plugin IBM-ActivityTracker successfully installed.`

3. 驗證 CLI 外掛程式的安裝。
  
    例如，檢查外掛程式的版本。執行下列指令：
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    輸出的外觀如下：
   
    ```
    Invoking 'cf plugins'...

    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}



## 在 Mac OS X 上安裝 Activity Tracker CLI
{: #install_cli_mac}

請完成下列步驟，在 Mac OS X 上安裝 {{site.data.keyword.cloudaccesstrailshort}} CF 外掛程式：

1. 從 [Bluemix CLI 頁面](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins)下載最新版本的 {{site.data.keyword.cloudaccesstrailshort}} 服務 CLI 外掛程式。 
	
	1. 選取平台值：**osx**。 
	2. 按一下**儲存檔案**。  
    
2. 執行 **cf install-plugin** 指令，以在 Mac OS X 上安裝 {{site.data.keyword.cloudaccesstrailshort}} 外掛程式。 

	```
	bx cf install-plugin PluginName
	```
	{: codeblock}
	
	其中 *PluginName* 是您已下載的檔案名稱。
	
    例如，若要在 Mac OS X 上安裝外掛程式，請從終端機執行下列指令：
	
	```
	bx cf install-plugin activitytracker-cli-mac_x64_v3.0.2
	```
	{: codeblock}
	
    安裝好外掛程式之後，您會得到下列訊息：`Plugin IBM-ActivityTracker successfully installed.`

3. 驗證 CLI 外掛程式的安裝。
  
    例如，檢查外掛程式的版本。執行下列指令：
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    輸出的外觀如下：
   
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

請完成下列步驟，以更新 {{site.data.keyword.cloudaccesstrailshort}} CF 外掛程式：

1. 從 [Bluemix CLI 頁面](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins)下載最新版本的 {{site.data.keyword.cloudaccesstrailshort}} 服務 CLI 外掛程式。 
	
	1. 選取平台值：Windows 為 **win64**、Mac OS X 為 **osx**、Linux 為 **linux64**。 
	2. 按一下**儲存檔案**。  
    
2. 執行 **cf install-plugin** 指令，以在 Windows 上更新 {{site.data.keyword.cloudaccesstrailshort}} 外掛程式。 

	```
	bx cf install-plugin PluginName -f
	```
	{: codeblock}
	
	其中 
	
	* *PluginName* 是您已下載的檔案名稱。
	* *-f* 是指出要解除安裝舊版本外掛程式然後安裝新版本的選項。
	
    例如，若要在 Windows 上更新外掛程式，請從終端機視窗執行下列指令：
	
	```
	bx cf install-plugin activitytracker-cli-windows_x64_v3.0.2.exe
	```
	{: codeblock}
	
    安裝好外掛程式之後，您會得到下列訊息：`Plugin IBM-ActivityTracker successfully installed.`

3. 驗證 CLI 外掛程式的安裝。
  
    例如，檢查外掛程式的版本。執行下列指令：
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    輸出的外觀如下：
   
    ```
    Invoking 'cf plugins'...

    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}

	
	
## 解除安裝 Activity Tracker CLI
{: #uninstall_cli}

若要解除安裝 {{site.data.keyword.cloudaccesstrailshort}} CLI，請刪除外掛程式。
{:shortdesc}

請完成下列步驟，以解除安裝 {{site.data.keyword.cloudaccesstrailshort}} 服務 CLI：

1. 驗證已安裝的 {{site.data.keyword.cloudaccesstrailshort}} CLI 外掛程式版本。
  
    例如，檢查外掛程式的版本。執行下列指令：
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    輸出的外觀如下：
   
    ```
    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2           at       IBM Activity Tracker plug-in
    ```
    {: screen}
    
2. 如果已安裝外掛程式，請執行 `cf uninstall-plugin` 以解除安裝記載 CLI 外掛程式。

    執行下列指令：
        
    ```
    bx cf uninstall-plugin IBM-ActivityTracker
    ```
    {: codeblock}
  
