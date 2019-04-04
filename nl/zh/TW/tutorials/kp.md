---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, monitoring activity, tutorial

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


# 使用 {{site.data.keyword.cloudaccesstrailshort}} 監視 {{site.data.keyword.keymanagementserviceshort}} 活動
{: #kp}

使用本指導教學，學習如何使用 {{site.data.keyword.cloudaccesstrailfull}} 服務來監視使用者與 {{site.data.keyword.keymanagementserviceshort}} 服務的互動。
{:shortdesc}

1. 了解如何佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務。
2. 了解如何使用雲端服務來產生自動由 {{site.data.keyword.cloudaccesstrailshort}} 服務收集的活動事件。事件會符合[雲端審核資料聯盟 (CADF) 標準 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.dmtf.org/sites/default/files/standards/documents/DSP0262_1.0.0.pdf){: new_window}。
3. 了解如何使用預先定義的 {{site.data.keyword.cloudaccesstrailshort}} 儀表板，以監視服務的雲端活動。

下圖顯示當使用者起始的活動變更服務的狀態時，發生的不同元件和動作：

![當使用者起始的活動變更服務的狀態時，發生的元件和動作](../images/AT_f1.png "當使用者起始的活動變更服務的狀態時，發生的元件和動作")



## 開始之前
{: #kp_prereqs}

建立 [{{site.data.keyword.cloud_notm}} 帳戶](https://cloud.ibm.com/login)。您的使用者 ID 必須是 {{site.data.keyword.cloud_notm}} 帳戶的成員或擁有者，且在您計劃使用 {{site.data.keyword.cloudaccesstrailshort}} 服務的空間中具有開發人員許可權。


## 步驟 1. 佈建 Activity Tracker
{: #kp_step1}

您必須將 {{site.data.keyword.cloudaccesstrailshort}} 服務佈建在要監視其活動的雲端服務佈建所在的相同地區中。佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務之後，即會自動從所選取的雲端服務中收集事件。 

**附註：**本指導教學顯示如何使用 {{site.data.keyword.cloudaccesstrailshort}} 服務來監視使用者與美國南部地區之雲端服務 {{site.data.keyword.keymanagementservicelong_notm}} 的互動。因此，您必須在美國南部地區佈建 {{site.data.keyword.cloudaccesstrailshort}}。若要查看服務可用之地區的相關資訊，請參閱[依地區列出的服務](/docs/resources?topic=resources-services_region#services_region)。

請完成下列步驟，以在 {{site.data.keyword.cloud_notm}} 中佈建 {{site.data.keyword.cloudaccesstraillong_notm}} 服務的實例：

1. [登入 {{site.data.keyword.cloud_notm}} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://cloud.ibm.com/login){:new_window}。
    
	使用您的使用者 ID 及密碼登入之後，會開啟 {{site.data.keyword.cloud_notm}} 使用者介面。

2. 按一下**型錄**。即會開啟 {{site.data.keyword.cloud_notm}} 上可用的服務清單。

3. 選取**安全和身分**種類，以過濾顯示的服務清單。

    **附註：**服務也提供於**開發人員工具**種類。

4. 按一下 **Activity Tracker** 磚。 

5. 配置定義將佈建服務之處的資訊。 

    如下表所示輸入資料： 

    <table>
	  <caption>表 1. 佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務所需的欄位</caption>
	  <tr>
	    <th width="50%">欄位</th>
		<th width="50%">值</th>
	  </tr>
	  <tr>
	    <td>選取要部署在哪個地區：</td>
		<td>美國南部</td>
	  </tr>
	  <tr>
	    <td>選擇組織：</td>
		<td>選取您計劃要在其中佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務的組織。</td>
	  </tr>
	  <tr>
	    <td>選擇空間：</td>
		<td>選取您計劃要在其中佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務的組織空間。</td>
	  </tr>
	</table>

6. 按一下**建立**，以在您登入的空間中佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務。
   

## 步驟 2. 配置雲端服務  
{: #kp_step2}

本指導教學顯示如何在 {{site.data.keyword.cloud_notm}} 中監視 {{site.data.keyword.keymanagementserviceshort}} 服務的 API 活動。

請完成下列步驟，以在 {{site.data.keyword.cloud_notm}} 中配置 {{site.data.keyword.keymanagementserviceshort}} 服務：

1. 在美國南部地區佈建 {{site.data.keyword.keymanagementserviceshort}} 服務的實例。如需相關資訊，請參閱[從 IBM Cloud 主控台佈建](/docs/services/key-protect?topic=key-protect-provision#provision)。

2. 針對您計劃用來使用金鑰的使用者定義 {{site.data.keyword.cloud_notm}} 許可權。 

    使用者需要一個 IAM 原則，且服務角色設為*管理員* 或*撰寫者* 才能建立金鑰。

    使用者需要一個 IAM 原則，且服務角色設為*管理員* 才能刪除金鑰。

    使用者需要一個 IAM 原則，且服務角色設為*讀者* 才能查看金鑰。 


## 步驟 3. 產生 Activity Tracker 事件
{: #kp_step3}

在此步驟中，使用 {{site.data.keyword.keymanagementserviceshort}} 服務建立安全金鑰，以產生 {{site.data.keyword.cloudaccesstrailshort}} 事件資料。如需相關資訊，請參閱[建立新金鑰](/docs/services/key-protect?topic=key-protect-create-standard-keys#create-standard-keys)。

* {{site.data.keyword.cloudaccesstrailshort}} 事件會因為建立金鑰而產生。
* {{site.data.keyword.cloudaccesstrailshort}} 事件可在 {{site.data.keyword.cloudaccesstrailshort}} **帳戶網域**（可在產生事件的 {{site.data.keyword.cloud_notm}} 地區中取得）中取得。 

## 步驟 4. 監視 Activity Tracker 事件
{: #kp_step4}

在此步驟中，透過 {{site.data.keyword.cloud_notm}} 使用者介面來驗證是否已產生 {{site.data.keyword.cloudaccesstrailshort}} 事件。

請完成下列步驟來驗證是否已建立事件：

1. 授與使用者可檢視帳戶事件的許可權。如需相關資訊，請參閱[檢視帳戶事件](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-view_acc_events#view_acc_events_account_events)和[授與許可權以查看帳戶事件](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-grant_permissions#grant_acc_events)。

2. 從 {{site.data.keyword.cloud_notm}} 儀表板中，選取 {{site.data.keyword.cloudaccesstrailshort}} 服務。服務儀表板隨即開啟。

3. 配置視圖，以搜尋在您佈建服務及新增金鑰時產生的 {{site.data.keyword.keymanagementserviceshort}} 事件。

    * 針對*檢視日誌* 欄位選取**帳戶日誌**。
    * 針對*搜尋欄位* 欄位選取 **target.typeURI_str**，然後在*過濾器* 欄位中輸入 `kms/secrets`。
	
    顯示的資料會顯示過去 24 小時可用的 {{site.data.keyword.keymanagementserviceshort}} 事件。 
	


## 後續步驟
{: #kp_next_steps}

接著，使用 {{site.data.keyword.cloudaccesstrailshort}} 預先定義 Kibana 儀表板來監視及分析事件日誌。若要啟動 Kibana，請參閱[導覽至 Kibana 儀表板](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-launch_kibana#launch_kibana)。依預設，在 Kibana 中，空間活動日誌是透過 **ActivityTracker_Space_Dashboard_in_24h** 儀表板來顯示：

您也可以使用 {{site.data.keyword.cloudaccesstrailshort}} CLI，從指令行管理事件。如需相關資訊，請參閱[檢視事件資訊](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-viewing_event_status#viewing_event_status)。



