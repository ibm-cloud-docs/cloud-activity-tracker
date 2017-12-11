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


# Activity Tracker 事件字段
{: #at_event}

{{site.data.keyword.cloudaccesstrailshort}} 事件基于 Cloud Auditing Data Federation (CADF) 标准。
{:shortdesc}

## 事件字段
{: #fields}

下表列出可用于分析 {{site.data.keyword.cloudaccesstrailshort}} 事件的字段：

<table>
  <caption>表 1. 每个事件可用于监视的字段。</caption>
  <tr>
    <th>字段名称</th>
	<th>状态</th>
	<th>描述</th>
  </tr>
  <tr>
    <td>outcome</td>
	<td>必需</td>
	<td>有效值为：*success* 和 *failure*</td>
  </tr>
  <tr>
    <td>typeURI</td>
	<td>必需</td>
	<td>此字段设置为：*http://schemas.dmtf.org/cloud/audit/1.0/event*</td>
  </tr>
  <tr>
    <td>eventType</td>
	<td>必需</td>
	<td>此字段设置为 *activity*。</td>
  </tr>
  <tr>
    <td>eventTime </td>
	<td>必需</td>
	<td>日期表示为 ISO 字符串，例如：*2017-09-17 15:15:32.396 +0000 UTC*。</td>
  </tr>
  <tr>
    <td>action</td>
	<td>必需</td>
	<td>此字段指示触发了事件的操作，例如 *read.ibm-key-protect.secrets*。</td>
  </tr>
  <tr>
    <td>id</td>
	<td>可选</td>
	<td>此字段包含事件的 UUID。</td>
  </tr>
  <tr>
    <td>initiator.id</td>
	<td>必需</td>
	<td>此字段包含事件源的标识，例如实例标识。</td>
  </tr>
  <tr>
    <td>initiator.name</td>
	<td>可选</td>
	<td>此字段提供人类可以阅读的事件源名称，例如用户标识。</td>
  </tr>
  <tr>
    <td>initiator.typeURI</td>
	<td>必需</td>
	<td>此字段告知事件源的类型，例如 *service/security/account/user*</td>
  </tr>
  <tr>
    <td>initiator.host.agent</td>
	<td>可选</td>
	<td>此字段指示用于发送请求的客户机，例如 *python-neneonclient* 或浏览器信息。</td>
  </tr>
  <tr>
    <td>initiator.host.address</td>
	<td>可选</td>
	<td>此字段包含发起者的 IP 地址。</td>
  </tr>
  <tr>
    <td>target.id</td>
	<td>必需</td>
	<td>此字段包含目标服务的标识。</td>
  </tr>
  <tr>
    <td>target.name</td>
	<td>必需</td>
	<td>此字段包含人类可以阅读的目标服务名称，例如 *ibm-key-protect*。</td>
  </tr>
  <tr>
    <td>target.typeURI</td>
	<td>必需</td>
	<td>此字段包含事件目标的类型，例如，*service/ibm-key-protect/secrets*。</td>
  </tr>
  <tr>
    <td>target.host.address</td>
	<td>可选</td>
	<td>此字段包含目标服务的 IP 地址或 URL，例如 *xxx.bluemix.net*。</td>
  </tr>
  <tr>
    <td>observer.name</td>
	<td>必需</td>
	<td>此字段设置为以下值：*ActivityTracker*</td>
  </tr>
  <tr>
    <td>observer.id</td>
	<td>必需</td>
	<td>此字段包含有关创建和存储 CADF 事件的资源的信息，例如 *activitytracker.ng.bluemix.net*。</td>
  </tr>
  <tr>
    <td>observer.typeURI</td>
	<td>必需</td>
	<td>此字段设置为以下值：*service/security/edge/activity-tracker*</td>
  </tr>
  <tr>
    <td>reason.reasonCode</td>
	<td>可选</td>
	<td>此字段包含 HTTP 响应代码，例如，*200* 表示成功。</td>
  </tr>
  <tr>
    <td>reason.reasonType</td>
	<td>必需</td>
	<td>此字段包含有关通过 *reason.sreasonCode* 字段提供的 reasonCode 的信息。</td>
  </tr>
</table>

 

