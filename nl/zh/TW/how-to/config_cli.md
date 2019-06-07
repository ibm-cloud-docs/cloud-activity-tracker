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

# 配置 Activity Tracker CLI
{: #config_cli}

{{site.data.keyword.cloudaccesstraillong}} 服務包含一個指令行介面 (CLI)，您可以用來管理雲端中的事件。您可以使用 {{site.data.keyword.cloud_notm}} 外掛程式來檢視事件的狀態、下載事件，以及配置保留原則。CLI 提供不同類型的說明：瞭解 CLI 及所支援指令的一般說明、瞭解如何使用指令的指令說明，或瞭解如何使用指令之次指令的次指令說明。
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} 已淘汰。從 2019 年 5 月 9 日開始，您無法佈建新的 {{site.data.keyword.cloudaccesstrailshort}} 實例。現有的超值方案實例將支援到 2019 年 9 月 30 日為止。若要繼續監視 {{site.data.keyword.cloud_notm}} 帳戶的活動，請佈建 [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) 的實例。
{: deprecated}


## 從 {{site.data.keyword.cloud_notm}} 儲存庫安裝 {{site.data.keyword.cloudaccesstrailshort}} 外掛程式
{: #install_cli_repo}

若要安裝 {{site.data.keyword.cloudaccesstrailshort}} CLI，請完成下列步驟：

1. 安裝 {{site.data.keyword.cloud_notm}} CLI。

   如需相關資訊，請參閱[安裝 {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-ibmcloud-cli#ibmcloud-cli)。
   
2. 在儲存庫中，找出外掛程式的名稱。執行下列指令：

    ```
    ibmcloud plugin repo-plugins
    ```
    {: codeblock}
    
    外掛程式的名稱是 **activity-tracker**。

3. 安裝 {{site.data.keyword.cloudaccesstrailshort}} 外掛程式。執行下列指令：

    ```
    ibmcloud plugin install activity-tracker
    ```
    {: codeblock}
 
4. 驗證已安裝 {{site.data.keyword.cloudaccesstrailshort}} 外掛程式。
  
    例如，執行下列指令，以查看已安裝的外掛程式清單：
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    


## 從檔案中安裝 {{site.data.keyword.cloudaccesstrailshort}} 外掛程式
{: #install_cli}

若要安裝 {{site.data.keyword.cloudaccesstrailshort}} CLI，請完成下列步驟：

1. 安裝 {{site.data.keyword.cloud_notm}} CLI。

   如需相關資訊，請參閱[安裝 {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-ibmcloud-cli#ibmcloud-cli)。

2. 安裝 {{site.data.keyword.cloudaccesstrailshort}} 外掛程式。

    * 若為 Linux，請參閱[在 Linux 上安裝 {{site.data.keyword.cloudaccesstrailshort}} 外掛程式](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-config_cli#install_cli_linux)。
    * 若為 Windows，請參閱[在 Windows 上安裝 {{site.data.keyword.cloudaccesstrailshort}} 外掛程式](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-config_cli#install_cli_windows)。
    * 若為 Mac OS X，請參閱[在 Mac OS X 上安裝 {{site.data.keyword.cloudaccesstrailshort}} 外掛程式](/docs/services//cloud-activity-tracker/how-to?topic=cloud-activity-tracker-config_cli#install_cli_mac)。
 
3. 驗證 CLI 外掛程式的安裝。
  
    例如，檢查外掛程式的版本。執行下列指令：
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    


## 在 Linux 上從檔案安裝 {{site.data.keyword.cloudaccesstrailshort}} 外掛程式
{: #install_cli_linux}

請完成下列步驟，以在 Linux 上安裝外掛程式：

1. 安裝外掛程式。

    從 [{{site.data.keyword.cloud_notm}} CLI 頁面 ![外部鏈結圖示](../../../icons/launch-glyph.svg "外部鏈結圖示")](https://plugins.cloud.ibm.com/ui/repository.html){:new_window} 下載最新版 {{site.data.keyword.cloudaccesstrailshort}} 服務 CLI 外掛程式 (activity-tracker)。
	
	* 選取平台值：**linux64**。 
	
	* 按一下**儲存檔案**。 
    
2. 安裝外掛程式。執行下列指令：
        
    ```
    ibmcloud plugin install -f activity-tracker-linux-amd64-3.3.0
    ```
    {: codeblock}




## 在 Windows 上從檔案安裝 {{site.data.keyword.cloudaccesstrailshort}} 外掛程式
{: #install_cli_windows}

請完成下列步驟，以在 Windows 上安裝外掛程式：

1. 從 [{{site.data.keyword.cloud_notm}} CLI 頁面 ![外部鏈結圖示](../../../icons/launch-glyph.svg "外部鏈結圖示")](https://plugins.cloud.ibm.com/ui/repository.html){:new_window} 下載最新版 {{site.data.keyword.cloudaccesstrailshort}} 服務 CLI 外掛程式 (activity-tracker)。 
	
	1. 選取平台值：**win64**。 
	2. 按一下**儲存檔案**。  
    
2. 安裝外掛程式。執行下列指令：
        
    ```
    ibmcloud plugin install -f activity-tracker-windows-amd64-3.3.0.exe
    ```
    {: codeblock}

	

## 在 Mac OS X 上從檔案安裝 {{site.data.keyword.cloudaccesstrailshort}} 外掛程式
{: #install_cli_mac}

請完成下列步驟，在 Mac OS X 上安裝外掛程式：

1. 從 [{{site.data.keyword.cloud_notm}} CLI 頁面 ![外部鏈結圖示](../../../icons/launch-glyph.svg "外部鏈結圖示")](https://plugins.cloud.ibm.com/ui/repository.html){:new_window} 下載最新版 {{site.data.keyword.cloudaccesstrailshort}} 服務 CLI 外掛程式 (activity-tracker)。
	
	1. 選取平台值 `osx`。 
	2. 按一下**儲存檔案**。  
    
2. 安裝外掛程式。執行下列指令：
        
    ```
    ibmcloud plugin install -f activity-tracker-darwin-amd64-3.3.0
    ```
    {: codeblock}

	
	
## 解除安裝 {{site.data.keyword.cloudaccesstrailshort}} CLI
{: #uninstall_cli}

若要解除安裝 CLI，請刪除外掛程式。
{:shortdesc}

請完成下列步驟，以解除安裝 {{site.data.keyword.cloudaccesstrailshort}} 服務 CLI：

1. 驗證已安裝的 CLI 外掛程式版本。
  
    例如，檢查外掛程式的版本。執行下列指令：
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    
2. 如果已安裝外掛程式，請執行 `ibmcloud plugin uninstall` 以解除安裝 CLI 外掛程式。

    執行下列指令：
        
    ```
    ibmcloud plugin uninstall activity-tracker
    ```
    {: codeblock}
  

## 從儲存庫更新 {{site.data.keyword.cloudaccesstrailshort}} CLI
{: #update_cli}

若要更新 CLI，請執行 *ibmcloud plugin update* 指令。
{:shortdesc}

請完成下列步驟，以更新 {{site.data.keyword.cloudaccesstrailshort}} 服務 CLI：

1. 更新 {{site.data.keyword.cloudaccesstrailshort}} 外掛程式。執行下列指令：

    ```
    ibmcloud plugin update activity-tracker
    ```
    {: codeblock}
 
2. 驗證 CLI 外掛程式的安裝。
  
    例如，驗證外掛程式的版本。執行下列指令：
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    





## 取得一般說明
{: #general_cli_help}

若要取得 CLI 的一般資訊及支援的指令，請完成下列步驟：

1. 登入 {{site.data.keyword.cloud_notm}} 中的地區、組織及空間。 
    
2. 列出支援指令及 CLI 的相關資訊。執行下列指令：

    ```
    ibmcloud at help 
    ```
    {: codeblock}
    
    

## 取得指令的說明
{: #command_cli_help}

若要取得如何使用指令的說明，請完成下列步驟：

1. 登入 {{site.data.keyword.cloud_notm}} 中的地區、組織及空間。 
    
2. 取得所支援指令的清單，並識別您需要的指令。執行下列指令：

    ```
    ibmcloud at help 
    ```
    {: codeblock}

3. 取得指令的說明。執行下列指令：

    ```
    ibmcloud at help *Command*
    ```
    {: codeblock}
    
    其中 *Command* 是 CLI 指令的名稱，例如 *status*。



## 取得次指令的說明
{: #subcommand_cli_help}

指令可以有次指令。若要取得次指令的說明，請完成下列步驟：

1. 登入 {{site.data.keyword.cloud_notm}} 中的地區、組織及空間。 
    
2. 取得所支援指令的清單，並識別您需要的指令。執行下列指令：

    ```
    ibmcloud at help 
    ```
    {: codeblock}

3. 取得指令的說明並識別支援的次指令。執行下列指令：

    ```
    ibmcloud at help *Command*
    ```
    {: codeblock}
    
    其中 *Command* 是 CLI 指令的名稱，例如 *session*。

4. 取得指令的說明並識別支援的次指令。執行下列指令：

    ```
    ibmcloud at *Command* help *Subcommand*
    ```
    {: codeblock}
    
    其中 
    
    *Command* 是 CLI 指令的名稱，例如 *status*。

    *Subcommand* 是支援的次指令名稱。例如，對於指令 *session* 而言，有效的次指令為 *list*。


## 顯示外掛程式的詳細資料
{: #show}
  
請使用 'ibmcloud plugin show activity-tracker' 指令來顯示外掛程式詳細資料。 

```
ibmcloud plugin show activity-tracker
```
{: codeblock}
    




