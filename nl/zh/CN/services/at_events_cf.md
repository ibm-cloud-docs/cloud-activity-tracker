---

copyright:
  years: 2016, 2019
lastupdated: "2019-01-23"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# Cloud Foundry 事件
{: #cf}

使用 {{site.data.keyword.cloudaccesstrailfull}} 服务在 {{site.data.keyword.Bluemix}} 中跟踪与核心平台服务的交互。
{:shortdesc}


以下列表概述了将事件发送至 {{site.data.keyword.cloudaccesstrailshort}} 服务的不同核心平台任务： 

* 供应服务、除去服务以及更改服务的名称。
* 针对帐户中的用户授予、更新和撤销 Cloud Foundry 空间角色。
* 创建平台 API 密钥，重命名平台密钥以及删除平台密钥。


## 与目录服务交互时生成的事件
{: #cf_catalog}

当供应服务、除去服务和更改服务的名称时，将生成事件并将其发送到 {{site.data.keyword.cloudaccesstrailshort}} 中与 Cloud Foundry 空间（该空间中的服务在该帐户中可用）相关联的空间域。 

例如，在美国南部区域的空间 B 中供应服务 A。将生成事件。要查看该事件，必须在美国南部供应该服务的同一空间中供应 {{site.data.keyword.cloudaccesstrailshort}} 服务。然后，您可以通过 {{site.data.keyword.cloudaccesstrailshort}} 服务 UI 来查看事件。

下表列出生成事件的目录操作：

<table>
  <caption>目录操作</caption>
  <tr>
    <th>操作</th>
	  <th>描述</th>
  <tr>
  <tr>
    <td>`audit.service_instance.create`</td>
	<td>在 Cloud Foundry 空间中供应服务时会创建事件。</td>
  </tr>
  <tr>
    <td>`audit.service_instance.update`</td>
	<td>更改 Cloud Foundry 空间中提供的服务名称时会创建事件。</td>
  </tr>
  <tr>
    <td>`audit.service_instance.delete`</td>
	<td>在帐户中从 Cloud Foundry 空间除去服务时会创建事件。</td>
  </tr>
</table>


 	

## 管理帐户中 Cloud Foundry 角色时生成的事件
{: #cf_cfroles} 

针对帐户中的用户授予或撤销（删除）Cloud Foundry 角色时，将生成事件并将其发送到 {{site.data.keyword.cloudaccesstrailshort}} 中与 Cloud Foundry 空间（在该空间中授予或撤销了该角色）相关联的空间域。 

例如，为美国南部区域的空间 B 中的用户 A 授予 *space manager* 角色。将生成事件。要查看该事件，必须在美国南部管理用户的 CF 许可权的同一空间中供应 {{site.data.keyword.cloudaccesstrailshort}} 服务。然后，您可以通过 {{site.data.keyword.cloudaccesstrailshort}} 服务 UI 来查看事件。


下表列出了在管理用户的 Cloud Foundry 角色时生成 {{site.data.keyword.cloudaccesstrailshort}} 事件的操作：

<table>
  <caption>管理 Cloud Foundry 角色的操作</caption>
  <tr>
    <th>操作</th>
	<th>描述</th>
  <tr>
  <tr>
    <td>`audit.user.space_manager_add`</td>
	<td>为用户授予 Cloud Foundry 空间中的 *manager* 角色。</td>
  </tr>
  <tr>
    <td>`audit.user.space_developer_add`</td>
	<td>为用户授予 Cloud Foundry 空间中的 *developer* 角色。</td>
  </tr>
  <tr>
    <td>`audit.user.space_auditor_add`</td>
	<td>为用户授予 Cloud Foundry 空间中的 *audit* 角色。</td>
  </tr>
  <tr>
    <td>`audit.user.space_manager_remove`</td>
	<td>删除用户在 Cloud Foundry 空间中的 *manager* 角色。</td>
  </tr>
  <tr>
    <td>`audit.user.space_developer_remove`</td>
	<td>删除用户在 Cloud Foundry 空间中的 *developer* 角色。</td>
  </tr>
  <tr>
    <td>`audit.user.space_auditor_remove`</td>
	<td>删除用户在 Cloud Foundry 空间中的 *audit* 角色。</td>
  </tr>
</table>






	
 	
 	
