---

copyright:
  years: 2016, 2019
lastupdated: "2019-06-06"

keywords: IBM Cloud, Activity Tracker, migration

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


# 轉移至 {{site.data.keyword.at_full_notm}}
{: #transition}

{{site.data.keyword.cloudaccesstrailfull}} 已於 2019 年 5 月 9 日淘汰。[進一步瞭解](https://www.ibm.com/blogs/cloud-archive/2019/04/deprecating-ibm-cloud-activity-tracker/)。服務取代為 {{site.data.keyword.at_full_notm}}。[進一步瞭解](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started)。
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} 已淘汰。從 2019 年 5 月 9 日開始，您無法佈建新的 {{site.data.keyword.cloudaccesstrailshort}} 實例。現有的超值方案實例將支援到 2019 年 9 月 30 日為止。若要繼續監視 {{site.data.keyword.cloud_notm}} 帳戶的活動，請佈建 [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) 的實例。
{: deprecated}


請完成下列步驟，以移轉至 {{site.data.keyword.at_full_notm}}： 

1. 儲存一份 {{site.data.keyword.cloudaccesstrailfull}} 中儲存的事件以便進行長期搜尋。您可以使用 {{site.data.keyword.cloudaccesstrailshort}} CLI 或 API。 

    請務必儲存每個 Cloud Foundry 空間（您在其中具有舊式 {{site.data.keyword.cloudaccesstrailshort}} 實例）的空間事件，以及您目前監視之每個地區中的每個帳戶網域的空間事件。

    * [使用 CLI 下載事件](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-downloading_events)。

    * [使用 API 下載事件](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-downloading_events_api)。

2. 佈建 [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-provision)。

    每個地區只能佈建 1 個實例。 
    
3. 建立並配置存取群組，以在 {{site.data.keyword.cloud_notm}} 中管理許可權。 

    * [授與管理許可權給使用者或服務 ID](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-iam_manage_events)。

    * [授與使用者許可權給使用者或服務 ID](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-iam_view_events)。

4. 在 {{site.data.keyword.at_full_notm}} 中定義視圖及儀表板，以便分析和管理事件。[進一步瞭解](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-views)。

    將 Kibana 儀表板移轉至 LogDNA 儀表板的作業不是自動化作業。您必須手動實作新的儀表板。 

    請注意，在 LogDNA 中，您只能實作直方圖和圓餅圖視覺效果。

5. [選用] 配置 {{site.data.keyword.at_full_notm}} 實例的保存。 

    您可以將事件保存至 {{site.data.keyword.cos_full_notm}} (COS)。[進一步瞭解](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-archiving)。

    **附註：**您要負責佈建 COS 實例以用來保存事件，也要負責維護保存的事件。 

    只有具有付款方案的 {{site.data.keyword.at_full_notm}} 實例需要此步驟。

6. 探索其他特性，例如[警示](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-alerts)。


當您準備好停止透過舊式 {{site.data.keyword.cloudaccesstrailshort}} 實例監視雲端活動時，請完成下列步驟：

1. 從 {{site.data.keyword.cloud_notm}} 主控台刪除舊式 {{site.data.keyword.cloudaccesstrailshort}} 實例。
2. 移除使用者處理這些舊式實例的任何許可權。 


