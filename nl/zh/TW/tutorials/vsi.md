---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, VSI events, tutorial

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


# 使用 {{site.data.keyword.cloudaccesstrailshort}} 來監視 {{site.data.keyword.BluVirtServers_short}} 和 {{site.data.keyword.baremetal_short}}
{: #vsi}

使用本指導教學，學習如何配置 {{site.data.keyword.cloud_notm}} 帳戶中的使用者，以便您可以監視當這些使用者使用 {{site.data.keyword.BluVirtServers_short}} 及 {{site.data.keyword.baremetal_short}} 時，所產生的 {{site.data.keyword.cloudaccesstrailshort}} 事件。
{:shortdesc}

{{site.data.keyword.BluVirtServers}} 是與專用核心及記憶體配置一起購買的可擴充虛擬伺服器。如果您要尋找可立即新增的計算資源，並存取映像檔範本這類特性，則它們是不錯的選項。 
* 如需相關資訊，請參閱[{{site.data.keyword.BluVirtServers_short}}](/docs/vsi?topic=virtual-servers-about-virtual-servers#about-virtual-servers)。 
* 如需產生 {{site.data.keyword.cloudaccesstrailshort}} 事件的動作清單，請參閱 [{{site.data.keyword.BluVirtServers_short}} 所產生的事件](/docs/vsi?topic=virtual-servers-at_events#at_events)。

{{site.data.keyword.baremetal_short}} 是單一承租戶的實體伺服器，可在對硬體資源進行低階存取的情況下，為您提供效能與控制能力。 
* 如需相關資訊，請參閱[{{site.data.keyword.baremetal_long}}](/docs/bare-metal?topic=bare-metal-about#about)。
* 如需產生 {{site.data.keyword.cloudaccesstrailshort}} 事件的動作清單，請參閱 [{{site.data.keyword.baremetal_short}} 所產生的事件](/docs/bare-metal?topic=bare-metal-at_events#at_events)。

**若要讓使用者產生 {{site.data.keyword.BluVirtServers_short}} 和 {{site.data.keyword.baremetal_short}} {{site.data.keyword.cloudaccesstrailshort}} 事件，該使用者必須要有在「IBM Cloud 主控台」中存取「基礎架構」資源的權限。**
{: tip}

## 步驟 1. 將 Softlayer 帳戶鏈結至 {{site.data.keyword.cloud_notm}} 帳戶
{: #vsi_step1}

** 若要產生 {{site.data.keyword.cloudaccesstrailshort}} 事件，Softlayer 帳戶必須鏈結至 {{site.data.keyword.cloud_notm}} 帳戶。如需相關資訊，請參閱[切換至 IBM ID 及鏈結帳戶](/docs/account?topic=account-unifyingaccounts#link_accounts)。

在將 Softlayer 帳戶鏈結至 {{site.data.keyword.cloud_notm}} 帳戶時，請考量下列資訊：
* 所有新帳戶都會自動收到 IBM ID，而現有的 SoftLayer 帳戶（SAML 聯合帳戶除外）能夠切換至 IBM ID 鑑別。
* 您計劃要鏈結至 {{site.data.keyword.cloud_notm}} 帳戶的每一個 SoftLayer 帳戶，都必須為具有唯一電子郵件位址的唯一 IBM ID 所擁有。
* 若要將現有 SoftLayer 帳戶切換至 IBM ID，您需要建立 IBM ID，然後使用登錄碼來加以確認。
* 帳戶切換至 IBM ID 帳戶之後，您可以鏈結 SoftLayer 帳戶和 {{site.data.keyword.cloud_notm}} 帳戶，以使用基礎架構即服務 (IaaS) 與平台即服務 (PaaS) 的合併資源。 

請完成下列步驟，以鏈結帳戶：
1. [要求 IBM ID 和登錄碼](/docs/account?topic=account-unifyingaccounts#reqIBMidandregcode)
2. [使用登錄碼來確認您的 IBM ID](/docs/account?topic=account-unifyingaccounts#confIBMiduseregcode)
3. [鏈結您的 IBM ID 帳戶](/docs/account?topic=account-unifyingaccounts#link_user_account)


## 步驟 2. 授與使用者基礎架構許可權
{: #vsi_step2}

**附註：**如果您從 *{{site.data.keyword.cloud_notm}} 基礎架構入口網站*授與許可權，使用者就沒有來自 *{{site.data.keyword.cloud_notm}} 基礎架構*儀表板的存取權來管理裝置，而且不會產生 {{site.data.keyword.cloudaccesstrailshort}} 事件。**您必須透過 {{site.data.keyword.cloud_notm}} 帳戶為使用者授與基礎架構許可權來管理裝置。這些動作會產生 {{site.data.keyword.cloudaccesstrailshort}} 事件。**
{: tip}

請完成下列步驟，為使用者授與基礎架構許可權：

1. [登入 {{site.data.keyword.cloud_notm}} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://cloud.ibm.com/login){:new_window}。
    
	使用您的使用者 ID 及密碼登入之後，會開啟 {{site.data.keyword.cloud_notm}} 使用者介面。

2. 從功能表列按一下**管理** &gt; **帳戶**，然後選取**使用者**。 

3. 選擇您要為其授與許可權來使用裝置的使用者。

4. 選取**指派存取權**。

5. 選取**指派存取權給 Softlayer 帳戶**。「{{site.data.keyword.cloud_notm}} 基礎架構入口網站」會在 {{site.data.keyword.cloud_notm}} 的環境定義中開啟。

6. 設定您要授與使用者來管理裝置的許可權。選取**入口網站許可權**。然後在**裝置**區段中，為使用者授與管理裝置所需的許可權。例如，您可以變更`檢視虛擬伺服器詳細資料`、`重新啟動伺服器及檢視 IPMI 系統資訊`、`升級伺服器`或`發出 OS 重新載入及起始救援核心`的許可權。

7. 儲存入口網站許可權。當您選取**裝置存取權**時，系統會提示您儲存變更。按一下**儲存**。

8. 設定使用者可以管理的裝置。在**裝置存取權**區段中，選取實體裝置。然後按一下**更新裝置存取權**。






