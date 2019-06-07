---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, Cloud Foundry events, CF

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


# Cloud Foundry イベント
{: #cf}

{{site.data.keyword.cloudaccesstrailfull}} サービスを使用して、{{site.data.keyword.Bluemix}} 内のコア・プラットフォーム・サービスとの対話をトラッキングします。 
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} は非推奨になりました。2019 年 5 月 9 日以降、新しい {{site.data.keyword.cloudaccesstrailshort}} インスタンスをプロビジョンできません。既存のプレミアム・プランのインスタンスは、2019 年 9 月 30 日までサポートされます。{{site.data.keyword.cloud_notm}} アカウントのアクティビティーのモニタリングを続行するには、[{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) のインスタンスをプロビジョンします。
{: deprecated}

{{site.data.keyword.cloudaccesstrailshort}} サービスにイベントを送信するさまざまなコア・プラットフォーム・タスクの概要は、次のリストのとおりです。 

* サービスのプロビジョン、サービスの削除、およびサービスの名前変更。
* アカウント内のユーザーへの Cloud Foundry スペースの役割の付与、更新、および取り消し。
* プラットフォーム API キーの作成、プラットフォーム・キーの名前変更、およびプラットフォーム・キーの削除。


## カタログ・サービスとの対話時に生成されるイベント
{: #cf_catalog}

サービスのプロビジョン、サービスの削除、およびサービスの名前変更を行うと、イベントが生成され、アカウント内の当該サービスが使用可能な Cloud Foundry スペースと関連付けられた、{{site.data.keyword.cloudaccesstrailshort}} 内のスペース・ドメインに送信されます。 

例えば、サービス A を米国南部地域のスペース B にプロビジョンするとします。 イベントが生成されます。 このイベントを表示するには、米国南部で、サービスをプロビジョンしたのと同じスペースに {{site.data.keyword.cloudaccesstrailshort}} サービスをプロビジョンする必要があります。 そうすると、このイベントを {{site.data.keyword.cloudaccesstrailshort}} サービス UI を介して表示することができます。

次の表に、イベントを生成するカタログ・アクションをリストします。

<table>
  <caption>カタログ・アクション</caption>
  <tr>
    <th>アクション</th>
	  <th>説明</th>
  <tr>
  <tr>
    <td>`audit.service_instance.create`</td>
	<td>Cloud Foundry スペースにサービスをプロビジョンすると、イベントが作成されます。</td>
  </tr>
  <tr>
    <td>`audit.service_instance.update`</td>
	<td>Cloud Foundry スペース内で使用可能なサービスの名前を変更すると、イベントが作成されます。</td>
  </tr>
  <tr>
    <td>`audit.service_instance.delete`</td>
	<td>アカウントの Cloud Foundry スペースからサービスを削除すると、イベントが作成されます。</td>
  </tr>
</table>


 	

## アカウント内の Cloud Foundry 役割の管理時に生成されるイベント
{: #cf_cfroles} 

アカウント内のユーザーに Cloud Foundry 役割を付与するか、または取り消す (削除する) と、イベントが生成され、役割の付与または取り消しが行われた Cloud Foundry スペースと関連付けられた、{{site.data.keyword.cloudaccesstrailshort}} 内のスペース・ドメインに送信されます。 

例えば、米国南部地域のスペース B 内のユーザー A に*スペース管理者* 役割を付与します。 イベントが生成されます。 このイベントを表示するには、米国南部で、ユーザーの CF 許可を管理しているのと同じスペースに {{site.data.keyword.cloudaccesstrailshort}} サービスをプロビジョンする必要があります。 そうすると、このイベントを {{site.data.keyword.cloudaccesstrailshort}} サービス UI を介して表示することができます。


次の表に、ユーザーの Cloud Foundry 役割を管理すると {{site.data.keyword.cloudaccesstrailshort}} イベントを生成するアクションをリストします。

<table>
  <caption>Cloud Foundry 役割を管理するアクション</caption>
  <tr>
    <th>アクション</th>
	<th>説明</th>
  <tr>
  <tr>
    <td>`audit.user.space_manager_add`</td>
	<td>Cloud Foundry スペース内での*マネージャー* 役割をユーザーに付与します。</td>
  </tr>
  <tr>
    <td>`audit.user.space_developer_add`</td>
	<td>Cloud Foundry スペース内での*開発者* 役割をユーザーに付与します。</td>
  </tr>
  <tr>
    <td>`audit.user.space_auditor_add`</td>
	<td>Cloud Foundry スペース内での*監査* 役割をユーザーに付与します。</td>
  </tr>
  <tr>
    <td>`audit.user.space_manager_remove`</td>
	<td>Cloud Foundry スペース内でのユーザーの*マネージャー* 役割を削除します。</td>
  </tr>
  <tr>
    <td>`audit.user.space_developer_remove`</td>
	<td>Cloud Foundry スペース内でのユーザーの*開発者* 役割を削除します。</td>
  </tr>
  <tr>
    <td>`audit.user.space_auditor_remove`</td>
	<td>Cloud Foundry スペース内でのユーザーの*監査* 役割を削除します。</td>
  </tr>
</table>






	
 	
 	
