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



# Activity Tracker 事件字段
{: #at_event}

{{site.data.keyword.cloudaccesstrailshort}} 事件基于 Cloud Auditing Data Federation (CADF) 标准。
{:shortdesc}

## 发起者字段
{: #initiator}

下表列出了 {{site.data.keyword.cloudaccesstrailshort}} 事件可用的常见字段：

<table>
  <caption>常见的发起者字段</caption>
  <tr>
    <th>字段名称</th>
	  <th>描述</th>
    <th>值</th>
  </tr>
  <tr>
    <td>initiator.id</td>
	  <td>操作发起者的标识。</br>有两种类型的发起者：IBM 标识和服务标识。</td>
    <td>IBM 标识的示例：IBMid-000000XXX2</br>服务标识的示例：iam-ServiceId-12345678-0165-4c89-847d-9660b1632e14</td>
  </tr>
  <tr>
    <td>initiator.name</td>
	  <td>发起操作的用户的用户名。</td>
    <td></td>
  </tr>
  <tr>
    <td>initiator.typeURI</td>
	  <td>事件源的类型。</td>
    <td>有效值为：*service/security/account/user*、*service/security/clientid* 和 *service/security/account/serviceid*</td>
  </tr>
  <tr>
    <td>initiator.credential.type</td>
	  <td>发起者标识凭证的类型。</td>
    <td>有效值为：*user*、*token* 和 *apikey*</td>
  </tr>
</table>

## 目标字段
{: #target}

下表列出了 {{site.data.keyword.cloudaccesstrailshort}} 事件可用的常见目标字段：

<table>
  <caption>常见目标字段</caption>
  <tr>
    <th>字段名称</th>
	  <th>描述</th>
    <th>值</th>
  </tr>
  <tr>
    <td>target.id</td>
	  <td>要对其执行操作的资源的云资源名称 (CRN)。</br>有关更多信息，请参阅 [CRN 格式](/docs/overview/crn.html#format)。</td>
    <td>例如：`crn:v1:bluemix:public:cloud-object-storage:global:a/12345678e6232019c6567c9123456789:fr56et47-befb-440a-a223c-12345678dae1:bucket:bucket1`</td>
  </tr>
  <tr>
    <td>target.name</td>
	  <td>要对其执行操作的云资源的名称（人类可以阅读的名称）。</td>
    <td></td>
  </tr>
  <tr>
    <td>target.typeURI</td>
    <td>要对其执行操作的云资源的类型。</br>此字段的格式为 **serviceName/objectType**，其中 servicename 为服务的名称。</td>
	  <td>例如：`iam-am/policy` 或 `cloud-object-storage/bucket/acl`</td>
  </tr>
</table>
 
## 操作字段
{: #action}

下表列出了 {{site.data.keyword.cloudaccesstrailshort}} 事件可用的常见操作字段：

<table>
  <caption>常见操作字段</caption>
  <tr>
    <th>字段名称</th>
	  <th>描述</th>
    <th>值</th>
  </tr>
  <tr>
    <td>action</td>
	  <td>触发事件的操作。</br>此字段的格式为 **serviceName.objectType.action**，其中 servicename 为服务的名称。</br>有关服务生成的事件的信息，请参阅<a href="/docs/services/cloud-activity-tracker/cloud_services.html#cloud_services">云服务</a></td>
    <td>例如：*iam-identity.serviceid-apikey.login*</td>
  </tr>
  <tr>
    <td>eventTime </td>
	  <td>指示创建事件时的时间戳记。</br>该日期以全球标准时间 (UTC) 来表示。</br>格式符合 ISO 8601。</td>
    <td>例如：2017-10-19T19:07:50.32+0000<td>
  </tr>
</table>

## 结果字段
{: #outcomes}

下表列出了 {{site.data.keyword.cloudaccesstrailshort}} 事件可用的常见结果字段：

<table>
  <caption>常见结果字段</caption>
  <tr>
    <th>字段名称</th>
	  <th>描述</th>
    <th>值</th>
  </tr>
  <tr>
    <td>outcome</td>
	  <td>操作的结果。</td>
    <td>有效值为：*success*、*failure* 和 *pending*</td>
  </tr>
  <tr>
    <td>reason.reasonCode</td>
	  <td>包含 HTTP 响应代码的数字字段。</td>
    <td>例如，*200* 表示成功的结果。</td>
  </tr>
  <tr>
    <td>severity</td>
	  <td>定义操作可能对云产生的威胁级别。</td>
    <td>有效值为：*normal*、*warning* 和 *critical*</br></br>**Normal** 设置适用于云中的例程操作。例如：启动实例或刷新令牌。</br></br>**Warning** 设置适用于那些更新云资源或修改其元数据的操作。例如，更新工作程序节点的版本，重命名证书或重命名服务实例。</br></br>**Critical** 设置适用于那些影响云中安全性的操作。例如：更改用户的凭证，删除数据，或者通过未经授权的访问方式来使用云资源。</td>
  </tr>
</table>
