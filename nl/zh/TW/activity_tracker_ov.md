---

copyright:
  years: 2016, 2017

lastupdated: "2017-09-25"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# Activity Tracker
{: #activity_tracker_ov}

請使用 {{site.data.keyword.cloudaccesstrailfull}} 服務來追蹤應用程式與 {{site.data.keyword.Bluemix}} 服務互動的情形。使用 {{site.data.keyword.cloudaccesstrailshort}} 可以監視異常活動，以及符合法規審核需求。所收集的事件符合雲端審核資料聯盟 (CADF) 標準。
{:shortdesc}

* {{site.data.keyword.cloudaccesstrailshort}} 會在雲端中為 IT 資源提供高階安全控管。
* {{site.data.keyword.cloudaccesstrailshort}} 為網路管理者提供一個解決方案，可在單一位置中擷取、儲存、檢視、搜尋及監視 API 活動。
* {{site.data.keyword.cloudaccesstrailshort}} 提供功能，可用來下載事件，然後您便可以使用這些事件產生審核追蹤報告。您可能需要這些報告，使您的組織符合內部規定及外部產業和國家法規。

不管應用程式是在何處執行（內部部署、在混合式雲端中或在公用雲端中），符合內部原則及產業法規是任何組織策略的主要需求。{{site.data.keyword.cloudaccesstrailshort}} 服務提供用來監視 API 呼叫的架構和功能，並產生符合公司政策及市場產業特有法規的證明。

當您在雲端環境（例如 {{site.data.keyword.Bluemix_notm}}）中工作時，您必須規劃用來審核及監視工作負載和資料的雲端策略，使它符合內部原則及產業和各國法規遵循需求。您可以使用透過 {{site.data.keyword.cloudaccesstrailshort}} 服務所登錄的資訊來識別資安事件，偵測未獲授權的存取，以及符合法規和內部審核需求。

例如，您可以使用 {{site.data.keyword.cloudaccesstrailshort}} 活動日誌來識別下列資訊：

* 對雲端服務發出 API 呼叫的使用者。
* 從中發出 API 呼叫的來源 IP 位址。
* 發出 API 呼叫時的時間戳記。
* API 呼叫的狀態。


## 在 Bluemix 中佈建 Activity Tracker
{: #provision}

您必須將 {{site.data.keyword.cloudaccesstrailshort}} 服務佈建在 {{site.data.keyword.Bluemix_notm}} 帳戶中，想要監視該空間裡執行之雲端服務的 API 活動的的每個空間。

若要了解如何佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務，請參閱[佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務](/docs/services/cloud-activity-tracker/how-to/provision.html#provision)。



## 收集活動日誌
{: #collect}

{{site.data.keyword.cloudaccesstrailshort}} 服務只會擷取針對 {{site.data.keyword.Bluemix_notm}} 中所選取雲端服務進行的 API 呼叫及其他動作相關的活動資料。如需服務清單，請參閱[支援的雲端服務](/docs/services/cloud-activity-tracker/cloud_services.html#cloud_services)。

* 會自動收集事件。 
* 在 {{site.data.keyword.cloudaccesstrailshort}} 中所收集的事件符合雲端審核資料聯盟 (CADF) 標準。CADF 標準定義一個完整事件模型，它包括在雲端環境中認證、管理及審核應用程式安全所需的資訊。

CADF 事件模型包含下列元件：

<table>
  <caption>表 1. CADF 事件模型中可用的元件</caption>
  <tr>
    <th>元件</th>
	<th>說明</th>
  </tr>
  <tr>
    <td>動作</td>
	<td>動作是指起始器執行、嘗試執行或等待完成的作業或活動。</td>
  </tr>
  <tr>
    <td>起始者</td>
	<td>起始者是指發出 API 呼叫及產生 CADF 事件的資源。所觸發的事件視 API 呼叫所要求的動作而定。</td>
  </tr>
  <tr>
    <td>觀察者</td>
	<td>觀察者是指可從 CADF 事件中可用的資訊建立及儲存 CADF 記錄的資源。</td>
  </tr>
  <tr>
    <td>成果</td>
	<td>成果是指針對目標所執行之動作的狀態。</td>
  </tr>
  <tr>
    <td>目標</td>
	<td>目標是指針對其執行、嘗試執行或擱置完成動作的資源。</td>
  </tr>
</table>


當您在 {{site.data.keyword.IBM_notm}} 公用雲端中使用 {{site.data.keyword.cloudaccesstrailshort}} 日誌時，請考量下列資訊：

* 您只能針對 {{site.data.keyword.IBM_notm}} 公用雲端中執行的資源所發出的 API 呼叫儲存審核記錄。
* 只會使用 {{site.data.keyword.IBM_notm}} 公用雲端儲存空間來收集事件。
* 此資訊將儲存 3 天。之後，會根據先進先出來刪除該資訊。
* {{site.data.keyword.cloudaccesstrailshort}} 服務支援類型為*活動*的 CADF 事件。



## 分析活動日誌
{: #analyze}

您可以在 {{site.data.keyword.Bluemix_notm}} 中透過 {{site.data.keyword.cloudaccesstrailshort}} 使用者介面，或使用 Kibana 這項開放程式碼工具，來分析活動日誌。您可以監視在特定空間或帳戶層次可以使用的事件。

您可以在 {{site.data.keyword.Bluemix_notm}} 中透過 {{site.data.keyword.cloudaccesstrailshort}} 使用者介面，搜尋、分析及監視過去 24 小時的活動日誌。如需相關資訊，請參閱[導覽至 {{site.data.keyword.cloudaccesstrailshort}} 使用者介面](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_at_ui.html#launch_at_ui)。

您可以使用 {{site.data.keyword.cloudaccesstrailshort}} Kibana 儀表板，或自行建立自訂儀表板，來搜尋、分析及監視過去 3 天的活動日誌。**附註：**這項特性適用於**進階**方案使用者。

* 如需如何啟動 Kibana 的相關資訊，請參閱[導覽至 Kibana 儀表板](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_kibana.html#launch_kibana)。 
* 如需可用來在 Kibana 中分析事件的欄位清單，請參閱 [{{site.data.keyword.cloudaccesstrailshort}} 事件欄位](/docs/services/cloud-activity-tracker/reference/at_event.html#at_event)



## 地區
{: #regions}

{{site.data.keyword.cloudaccesstrailshort}} 服務可用於下列地區：

* 美國南部
* 英國（測試版）


## 服務方案
{: #plan}

{{site.data.keyword.cloudaccesstrailshort}} 服務提供多種方案。

您可以透過 {{site.data.keyword.Bluemix_notm}} 使用者介面或指令行，來變更方案。您可以隨時升級或降低您的方案。如需 {{site.data.keyword.Bluemix_notm}} 中之服務方案升級的相關資訊，請參閱[變更方案](/docs/services/cloud-activity-tracker/plan/change_plan.html#change_plan)。 

下表概述每個服務方案中可用的特性：

<table>
    <caption>表 1. 事件汲取、事件保留及匯出事件的功能</caption>
      <tr>
        <th>方案</th>
        <th>事件汲取</th>
        <th>事件保留</th>
		<th>匯出事件</th>
      </tr>
      <tr>
        <td>精簡（預設值）</td>
        <td>否</td>
        <td>過去 3 天</td>
		<td>否</td>
      </tr>
      <tr>
        <td>進階</td>
        <td>是</td>
        <td>可配置的天數。</td>
		<td>是</td>
      </tr>
</table>

<table>
    <caption>表 2. 管理及檢視事件的功能</caption>
      <tr>
        <th>方案</th>
		<th>API</th>
		<th>CLI</th>
        <th>Kibana</th>
      </tr>
      <tr>
        <td>精簡（預設值）</td>
		<td>否</td>
		<td>否</td>
        <td>否</td>
      </tr>
      <tr>
        <td>進階</td>
		<td>是</td>
		<td>是</td>
        <td>是</td>
      </tr>
</table>

**附註：**事件儲存空間的每月成本會以計費週期的平均值來計算。

## 安全
{: #security}

使用 {{site.data.keyword.cloudaccesstrailshort}} 服務時，請考量下列有關安全的資訊：

* 產生 {{site.data.keyword.cloudaccesstrailshort}} 事件的 IBM 服務會遵循 {{site.data.keyword.IBM_notm}} Cloud 安全原則。如需相關資訊，請參閱 [Trust the security and privacy of IBM Cloud ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud-computing/learn-more/why-ibm-cloud/security/){: new_window}。
* {{site.data.keyword.cloudaccesstrailshort}} 擷取會擷取變更雲端服務狀態的使用者起始動作。此資訊不提供資料庫或應用程式的直接存取權。
* 只有獲授權的使用者才能檢視及監視 {{site.data.keyword.cloudaccesstrailshort}} 事件日誌。每一個使用者都是透過 {{site.data.keyword.Bluemix_notm}} 中的唯一 ID 加以識別。
