---

copyright:
  years: 2016, 2018
lastupdated: "2018-07-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}



# Activity Tracker 事件欄位
{: #at_event}

{{site.data.keyword.cloudaccesstrailshort}} 事件是以雲端審核資料聯盟 (CADF) 標準為基礎。
{:shortdesc}

## 起始者欄位
{: #initiator}

下表列出可用於 {{site.data.keyword.cloudaccesstrailshort}} 事件的一般欄位：

<table>
  <caption>一般起始者欄位</caption>
  <tr>
    <th>欄位名稱</th>
	  <th>說明</th>
    <th>值</th>
  </tr>
  <tr>
    <td>initiator.id</td>
	  <td>動作起始者的 ID。</br>有兩種起始者類型：IBM ID 和服務 ID。</td>
    <td>IBM ID 的範例：IBMid-000000XXX2 </br>服務 ID 的範例：iam-ServiceId-12345678-0165-4c89-847d-9660b1632e14</td>
  </tr>
  <tr>
    <td>initiator.name</td>
	  <td>起始動作之使用者的使用者名稱。</td>
    <td></td>
  </tr>
  <tr>
    <td>initiator.typeURI</td>
	  <td>事件來源的類型。</td>
    <td>有效值為：*service/security/account/user*、*service/security/clientid*、*service/security/account/serviceid*</td>
  </tr>
  <tr>
    <td>initiator.credential.type</td>
	  <td>起始者 ID 認證的類型。</td>
    <td>有效值為：*user*、*token*、*apikey*</td>
  </tr>
</table>

## 目標欄位
{: #target}

下表列出可用於 {{site.data.keyword.cloudaccesstrailshort}} 事件的一般目標欄位：

<table>
  <caption>一般目標欄位</caption>
  <tr>
    <th>欄位名稱</th>
	  <th>說明</th>
    <th>值</th>
  </tr>
  <tr>
    <td>target.id</td>
	  <td>執行動作所在資源的「雲端資源名稱 (CRN) 」。</br>如需相關資訊，請參閱 [CRN 格式](/docs/overview/crn.html#format)。</td>
    <td>例如：`crn:v1:bluemix:public:cloud-object-storage:global:a/12345678e6232019c6567c9123456789:fr56et47-befb-440a-a223c-12345678dae1:bucket:bucket1`</td>
  </tr>
  <tr>
    <td>target.name</td>
	  <td>執行動作所在雲端資源之名稱的人類可讀名稱。</td>
    <td></td>
  </tr>
  <tr>
    <td>target.typeURI</td>
    <td>執行動作所在雲端資源的類型。</br>此欄位的格式為 **serviceName/objectType**，其中 servicename 是服務的名稱。</td>
	  <td>例如：`iam-am/policy` 或 `cloud-object-storage/bucket/acl`</td>
  </tr>
</table>
 
## 動作欄位
{: #action}

下表列出可用於 {{site.data.keyword.cloudaccesstrailshort}} 事件的一般動作欄位：

<table>
  <caption>一般動作欄位</caption>
  <tr>
    <th>欄位名稱</th>
	  <th>說明</th>
    <th>值</th>
  </tr>
  <tr>
    <td>action</td>
	  <td>觸發事件的動作。</br>此欄位的格式為 **serviceName.objectType.action**，其中 servicename 是服務的名稱。</br>如需服務所產生之事件的相關資訊，請參閱<a href="/docs/services/cloud-activity-tracker/cloud_services.html#cloud_services">雲端服務</a></td>
    <td>例如：*iam-identity.serviceid-apikey.login*</td>
  </tr>
  <tr>
    <td>eventTime </td>
	  <td>指出建立事件的時間戳記。</br>日期以「世界標準時間 (UTC)」表示。</br>該格式符合 ISO 8601 標準。</td>
    <td>例如：2017-10-19T19:07:50.32+0000<td>
  </tr>
</table>

## 成果欄位
{: #outcomes}

下表列出可用於 {{site.data.keyword.cloudaccesstrailshort}} 事件的一般成果欄位：

<table>
  <caption>一般成果欄位</caption>
  <tr>
    <th>欄位名稱</th>
	  <th>說明</th>
    <th>值</th>
  </tr>
  <tr>
    <td>outcome</td>
	  <td>動作的結果。</td>
    <td>有效值為：*success*、*failure*、*pending*</td>
  </tr>
  <tr>
    <td>reason.reasonCode</td>
	  <td>包括 HTTP 回應碼的數值欄位。</td>
    <td>例如，*200* 表示成果成功。</td>
  </tr>
  <tr>
    <td>嚴重性</td>
	  <td>定義動作可能對雲端構成的威脅層次。</td>
    <td>有效值為：*normal*、*warning* 及 *critical* </br></br>**Normal** 是針對雲端中的常式動作而設定的。例如：啟動實例，或重新整理記號。</br></br>**Warning** 是針對更新雲端資源或修改其 meta 資料的動作而設定的。例如：更新工作者節點的版本、重新命名憑證，或重新命名服務實例。</br></br>**Critical** 是針對會影響雲端中安全的動作而設定的。例如：變更使用者的認證、刪除資料、進行未獲授權的存取來使用雲端資源。</td>
  </tr>
</table>
