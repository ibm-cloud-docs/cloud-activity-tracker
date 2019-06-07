---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, compliance

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


# 規範
{: #compliance}

[{{site.data.keyword.cloud_notm}} 提供了一個 Cloud 平台，以及遵照 IBM 嚴格安全標準建置的服務](/docs/overview?topic=overview-security#compliance)。{{site.data.keyword.cloudaccesstraillong}} 服務是針對 {{site.data.keyword.cloud_notm}} 而建置的 DevOps 服務。
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} 已淘汰。從 2019 年 5 月 9 日開始，您無法佈建新的 {{site.data.keyword.cloudaccesstrailshort}} 實例。現有的超值方案實例將支援到 2019 年 9 月 30 日為止。若要繼續監視 {{site.data.keyword.cloud_notm}} 帳戶的活動，請佈建 [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) 的實例。
{: deprecated}

## 一般資料保護規範

「一般資料保護規範 (GDPR)」嘗試建立跨歐盟的協調資料保護法律架構，而且目的是將居民的個人資料控制權返還給居民，同時對於在全球任何位置管理及「處理」此資料的人強制施行嚴格的規則。此「規範」也會建立與在歐盟內外部自由移動個人資料有關的規則。 

**免責聲明：**{{site.data.keyword.cloudaccesstrailshort}} 服務會針對在 {{site.data.keyword.cloud_notm}} 中以您帳戶執行的雲端資源，儲存及顯示其事件記錄。個人資訊 (PI) 不得包含在 {{site.data.keyword.cloudaccesstrailshort}} 所儲存的任何事件項目中，因為此資料可供「企業」內的其他使用者存取，以及可供 {{site.data.keyword.IBM_notm}} 存取，以便能夠支援「雲端服務」。

### 地區
{: #compliance_regions}

{{site.data.keyword.cloudaccesstrailshort}} 服務在提供該服務的 {{site.data.keyword.cloud_notm}} Public 地區中遵循 GDPR。


### 資料保留
{: #compliance_data_retention}

{{site.data.keyword.cloudaccesstrailshort}} 服務包括 2 個儲存事件資料的資料儲存庫： 

* 其中一個儲存庫的事件資料可透過 Kibana 用來進行分析。標準或精簡方案只會將資料儲存在此儲存庫中。資料會保留 3 天。
* 另一個長期儲存儲存庫可用來管理超值方案的事件資料。會一直儲存事件資料，直到您配置保留原則或手動刪除它們為止。依預設，事件會無限期地保留。


### 資料刪除
{: #compliance_data_deletion}

請考量下列資訊：

* 會在 3 天後刪除儲存在儲存庫中為 Kibana 提供資料的事件。

* 在長期儲存庫中儲存的事件會在您配置保留原則，或者在您手動刪除它們的數天之後刪除。 



如果您從付費方案變更為標準或精簡方案，則會在大約一天內刪除在長期儲存儲存庫中的事件。

您可以隨時開立支援問題單並要求刪除您的所有資料。如需開立 IBM 支援問題單的相關資訊，請參閱[取得支援](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support)。



### 相關資訊
{: #compliance_info}

如需相關資訊，請參閱：

[{{site.data.keyword.cloud_notm}} 安全規範](/docs/overview?topic=overview-security#compliance)

[GDPR - {{site.data.keyword.IBM_notm}} 官方頁面 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/data-responsibility/gdpr/){:new_window}



