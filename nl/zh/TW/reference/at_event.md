---

copyright:
  years: 2016, 2017

lastupdated: "2017-09-18"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# Activity Tracker 事件欄位
{: #at_event}

{{site.data.keyword.cloudaccesstrailshort}} 事件是以雲端審核資料聯盟 (CADF) 標準為基礎。
{:shortdesc}

## 事件欄位
{: #fields}

下表列出可供分析的 {{site.data.keyword.cloudaccesstrailshort}} 事件欄位：

<table>
  <caption>表 1. 每個事件可供監視的欄位。</caption>
  <tr>
    <th>欄位名稱</th>
	<th>狀態</th>
	<th>說明</th>
  </tr>
  <tr>
    <td>outcome</td>
	<td>必要</td>
	<td>有效值為：*success*、*failure*</td>
  </tr>
  <tr>
    <td>typeURI</td>
	<td>必要</td>
	<td>此欄位設為：*http://schemas.dmtf.org/cloud/audit/1.0/event*</td>
  </tr>
  <tr>
    <td>eventType</td>
	<td>必要</td>
	<td>此欄位設為 *activity*。</td>
  </tr>
  <tr>
    <td>eventTime </td>
	<td>必要</td>
	<td>日期呈現為 ISO 字串，例如 *2017-09-17 15:15:32.396 +0000 UTC*。</td>
  </tr>
  <tr>
    <td>action</td>
	<td>必要</td>
	<td>此欄位指出觸發事件的動作，例如 *read.ibm-key-protect.secrets*。</td>
  </tr>
  <tr>
    <td>id</td>
	<td>選用</td>
	<td>此欄位包含事件的 UUID。</td>
  </tr>
  <tr>
    <td>initiator.id</td>
	<td>必要</td>
	<td>此欄位包含事件來源的 ID ，例如實例 ID。</td>
  </tr>
  <tr>
    <td>initiator.name</td>
	<td>選用</td>
	<td>此欄位提供事件來源的人類可讀名稱，例如 userid。</td>
  </tr>
  <tr>
    <td>initiator.typeURI</td>
	<td>必要</td>
	<td>此欄位會告知事件來源類型，例如 *service/security/account/user*</td>
  </tr>
  <tr>
    <td>initiator.host.agent</td>
	<td>選用</td>
	<td>此欄位指出用來傳送要求的用戶端，例如 *python-neutronclient* 或瀏覽器資訊。</td>
  </tr>
  <tr>
    <td>initiator.host.address</td>
	<td>選用</td>
	<td>此欄位包含起始者的 IP 位址。</td>
  </tr>
  <tr>
    <td>target.id</td>
	<td>必要</td>
	<td>此欄位包含目標服務的 ID。</td>
  </tr>
  <tr>
    <td>target.name</td>
	<td>必要</td>
	<td>此欄位包含目標服務的人類可讀名稱，例如 *ibm-key-protect*。</td>
  </tr>
  <tr>
    <td>target.typeURI</td>
	<td>必要</td>
	<td>此欄位包含事件目標的類型，例如 *service/ibm-key-protect/secrets*。</td>
  </tr>
  <tr>
    <td>target.host.address</td>
	<td>選用</td>
	<td>此欄位包含目標服務的 IP 位址或 URL，例如 *xxx.bluemix.net*。</td>
  </tr>
  <tr>
    <td>observer.name</td>
	<td>必要</td>
	<td>此欄位設為下列值：*ActivityTracker*</td>
  </tr>
  <tr>
    <td>observer.id</td>
	<td>必要</td>
	<td>此欄位包含建立和儲存 CADF 事件之資源的相關資訊，例如 *activitytracker.ng.bluemix.net*。</td>
  </tr>
  <tr>
    <td>observer.typeURI</td>
	<td>必要</td>
	<td>此欄位設為下列值：*service/security/edge/activity-tracker*</td>
  </tr>
  <tr>
    <td>reason.reasonCode</td>
	<td>選用</td>
	<td>此欄位包含 HTTP 回應碼（例如，*200* 代表成功）。</td>
  </tr>
  <tr>
    <td>reason.reasonType</td>
	<td>必要</td>
	<td>此欄位包含透過 *reason.reasonCode* 欄位提供 reasonCode 時，它的相關資訊。</td>
  </tr>
</table>

 

