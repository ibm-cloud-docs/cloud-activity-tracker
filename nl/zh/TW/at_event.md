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



# 事件欄位
{: #at_event}

{{site.data.keyword.cloudaccesstrailshort}} 事件是以雲端審核資料聯盟 (CADF) 標準為基礎。
{:shortdesc}

## 起始者欄位
{: #initiator}

下表列出可用於 {{site.data.keyword.cloudaccesstrailshort}} 事件的一般欄位：

|欄位名稱|說明|值|
|------------|-------------|-------|
| `initiator.id` |動作起始者的 ID。</br></br>起始器有以下不同類型：IBMID、serviceID 和 Cloud Foundry (CF) 使用者 ID。|IBM ID 的範例：IBMid-000000XXX2 </br>服務 ID 的範例：iam-ServiceId-12345678-0165-4c89-847d-9660b1632e14</br>CF 使用者 ID 範例：7666666b-23ae-4a34-8569-cu75tgdr4da3 |
| `initiator.name` |起始動作之使用者的使用者名稱。|例如，電子郵件位址。|
| `initiator.typeURI` |事件來源的類型。| 有效值為：*service/security/account/user*、*service/security/clientid*、*service/security/account/serviceid* |
| `initiator.credential.type` |起始者 ID 認證的類型。| 有效值為：*user*、*token*、*apikey* |
{: caption="表 1. 一般起始者欄位" caption-side="top"} 

  

## 目標欄位
{: #target}

下表列出可用於 {{site.data.keyword.cloudaccesstrailshort}} 事件的一般目標欄位：

|欄位名稱|說明|值|
|------------|-------------|-------|
| `target.id` |執行動作所在資源的「雲端資源名稱 (CRN) 」。</br>如需相關資訊，請參閱 [CRN 格式](/docs/overview?topic=overview-format-crn#format)。| 例如：`crn:v1:bluemix:public:cloud-object-storage:global:a/12345678e6232019c6567c9123456789:fr56et47-befb-440a-a223c-12345678dae1:bucket:bucket1` |
| `target.name` |執行動作所在雲端資源之名稱的人類可讀名稱。|  |
| `target.typeURI` |執行動作所在雲端資源的類型。</br>此欄位的格式為 **serviceName/objectType**，其中 servicename 是服務的名稱。| 例如：`iam-am/policy` or `cloud-object-storage/bucket/acl` |
{: caption="表 2. 一般目標欄位" caption-side="top"} 


 
## 動作欄位
{: #action}

下表列出可用於 {{site.data.keyword.cloudaccesstrailshort}} 事件的一般動作欄位：

|欄位名稱|說明|值|
|------------|-------------|-------|
| `action` |觸發事件的動作。</br>此欄位的格式為 **serviceName.objectType.action**，其中 servicename 是服務的名稱。</br>如需服務所產生之事件的動作值相關資訊，請參閱<a href="/docs/services/cloud-activity-tracker/cloud_services.html#cloud_services">雲端服務</a> | 例如：*iam-identity.serviceid-apikey.login* |
| `eventTime` |指出建立事件的時間戳記。</br>日期以「世界標準時間 (UTC)」表示。</br>該格式符合 ISO 8601 標準。|例如：2017-10-19T19:07:50.32+0000|
{: caption="表 3. 一般動作欄位" caption-side="top"} 



## 成果欄位
{: #outcomes}

下表列出可用於 {{site.data.keyword.cloudaccesstrailshort}} 事件的一般成果欄位：

|欄位名稱|說明|值|
|------------|-------------|-------|
| `outcome` |動作的結果。| 有效值為：*success*、*failure*、*pending* |
| `reason.reasonCode` |包括 HTTP 回應碼的數值欄位。|例如，*200* 表示成果成功。|
| `severity` |定義動作可能對雲端構成的威脅層次。|有效值為：*normal*、*warning* 及 *critical* </br></br>**Normal** 是針對雲端中的常式動作而設定的。例如：啟動實例，或重新整理記號。</br></br>**Warning** 是針對更新雲端資源或修改其 meta 資料的動作而設定的。例如：更新工作者節點的版本、重新命名憑證，或重新命名服務實例。</br></br>**Critical** 是針對會影響雲端中安全的動作而設定的。例如：變更使用者的認證、刪除資料、進行未獲授權的存取來使用雲端資源。|
{: caption="表 4. 一般成果欄位" caption-side="top"} 


