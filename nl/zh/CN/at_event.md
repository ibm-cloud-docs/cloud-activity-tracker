---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, event fields

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



# 事件字段
{: #at_event}

{{site.data.keyword.cloudaccesstrailshort}} 事件基于 Cloud Auditing Data Federation (CADF) 标准。
{:shortdesc}

不推荐使用 {{site.data.keyword.cloudaccesstrailfull}}。从 2019 年 5 月 9 日开始，无法供应新的 {{site.data.keyword.cloudaccesstrailshort}} 实例。对现有高端套餐实例的支持会持续到 2019 年 9 月 30 日。要继续监视 {{site.data.keyword.cloud_notm}} 帐户的活动，请供应 [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) 的实例。
{: deprecated}

## 发起者字段
{: #initiator}

下表列出了 {{site.data.keyword.cloudaccesstrailshort}} 事件可用的常见字段：

|字段名称|描述|值|
|------------|-------------|-------|
| `initiator.id` |操作发起者的标识。</br></br>发起者的有效类型为 `IBM 标识`、`服务标识`和 `Cloud Foundry (CF) 用户标识`。|IBM 标识的示例为 `IBMid-000000XXX2` </br>服务标识的示例为 `iam-ServiceId-12345678-0165-4c89-847d-9660b1632e14` </br>CF 用户标识的示例为 `7666666b-23ae-4a34-8569-cu75tgdr4da3`|
| `initiator.name` |发起操作的用户的用户名。|例如，电子邮件地址。|
| `initiator.typeURI` |事件源的类型。|有效值为 *service/security/account/user*、*service/security/clientid* 和 *service/security/account/serviceid*。|
| `initiator.credential.type` |发起者标识凭证的类型。|有效值为 *user*、*token* 和 *apikey*。|
{: caption="表 1. 常见发起者字段" caption-side="top"} 

  

## 目标字段
{: #target}

下表列出了 {{site.data.keyword.cloudaccesstrailshort}} 事件可用的常见目标字段：

|字段名称|描述|值|
|------------|-------------|-------|
| `target.id` |要对其执行操作的资源的云资源名称 (CRN)。</br>有关更多信息，请参阅 [CRN 格式](/docs/overview?topic=overview-crn#format-crn)。|例如，`crn:v1:bluemix:public:cloud-object-storage:global:a/12345678e6232019c6567c9123456789:fr56et47-befb-440a-a223c-12345678dae1:bucket:bucket1` |
| `target.name` |要对其执行操作的云资源的人类可以阅读的名称。|  |
| `target.typeURI` |要对其执行操作的云资源的类型。</br>此字段的格式为 **serviceName/objectType**，其中 `servicename` 是服务的名称。| 例如，`iam-am/policy` 或 `cloud-object-storage/bucket/acl` |
{: caption="表 2. 常见目标字段" caption-side="top"} 


 
## 操作字段
{: #action}

下表列出了 {{site.data.keyword.cloudaccesstrailshort}} 事件可用的常见操作字段：

|字段名称|描述|值|
|------------|-------------|-------|
| `action` |触发事件的操作。</br>此字段的格式为 **serviceName.objectType.action**，其中 `servicename` 是服务的名称。</br>有关服务所生成事件的操作值的更多信息，请参阅<a href="/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-cloud_services#cloud_services">云服务</a>|例如，`iam-identity.serviceid-apikey.login` |
| `eventTime` |指示创建事件时的时间戳记。</br>该日期以全球标准时间 (UTC) 来表示。</br>格式符合 ISO 8601。|例如，`2017-10-19T19:07:50.32+0000` |
{: caption="表 3. 常见操作字段" caption-side="top"} 



## 结果字段
{: #outcomes}

下表列出了 {{site.data.keyword.cloudaccesstrailshort}} 事件可用的常见结果字段：

|字段名称|描述|值|
|------------|-------------|-------|
| `outcome` |操作的结果。|有效值为 *success*、*failure* 和 *pending*。|
| `reason.reasonCode` |包含 HTTP 响应代码的数字字段。|例如，*200* 表示成功的结果。|
| `severity` |定义操作可能对云产生的威胁级别。|有效值为 *normal*、*warning* 和 *critical*。</br></br>**Normal** 设置适用于云中的例程操作。例如，启动实例或刷新令牌。</br></br>**Warning** 设置适用于那些更新云资源或修改其元数据的操作。例如，更新工作程序节点的版本，重命名证书或重命名服务实例。</br></br>**Critical** 设置适用于那些影响云中安全性的操作。例如，更改用户的凭证，删除数据，或者通过未经授权的访问方式来使用云资源。|
{: caption="表 4. 常见结果字段" caption-side="top"} 


