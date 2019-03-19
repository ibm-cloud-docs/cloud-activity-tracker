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


# サービス・インスタンスのイベント  
{: #at_events_rc}

セキュリティー担当者、監査員、またはマネージャーは、{{site.data.keyword.cloudaccesstrailfull}} サービスを使用して、ユーザーおよびアプリケーションが {{site.data.keyword.Bluemix}} サービスとどのように対話しているのかをトラッキングできます。 
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull_notm}} サービスは、{{site.data.keyword.cloud_notm}} 内のサービスの状態を変更するユーザー開始アクティビティーを記録します。 詳しくは、[{{site.data.keyword.cloudaccesstrailshort}} 概要](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#activity_tracker_ov )を参照してください。

ユーザーのアクションのモニターを開始するには、[{{site.data.keyword.cloudaccesstrailfull_notm}}](/docs/services/cloud-activity-tracker/index.html#getting-started-with-cla)を参照してください。 

## サービス・インスタンスのプロビジョンおよび管理のイベント
{: #at_events_rc_provision}

次の表に、呼び出されたときにイベントを生成する API メソッドのリストを示します。

<table>
  <caption>イベントを生成するアクション</caption>
  <tr>
    <th>アクション</th>
	  <th>説明</th>
  </tr>
  <tr>
    <td><i>service_name</i>.instance.create</td>
	  <td>サービス・インスタンスをプロビジョンすると、イベントが生成されます。</td>
  </tr>
  <tr>
    <td><i>service_name</i>.instance.update</td>
	  <td>サービス・インスタンスを名前変更するか、サービス・プランを変更すると、イベントが生成されます。</td>
  </tr>
  <tr>
    <td><i>service_name</i>.instance.delete</td>
	  <td>サービス・インスタンスが削除されると、イベントが生成されます。</td>
  </tr>
</table>


##  サービス・インスタンスに関連付けられている API キーの管理のイベント
{: #at_events_rc_keys}

次の表に、呼び出されたときにイベントを生成する API メソッドのリストを示します。

<table>
  <caption>イベントを生成するアクション</caption>
  <tr>
    <th>アクション</th>
	  <th>説明</th>
  </tr>
  <tr>
    <td><i>service_name</i>.key.create</td>
	  <td>サービス・インスタンス UI の*「サービス資格情報」*セクションを介してサービス・インスタンス用の API キーが作成されると、イベントが生成されます。</td>
  </tr>
  <tr>
    <td><i>service_name</i>.key.delete</td>
	  <td>サービス・インスタンス UI の*「サービス資格情報」*セクションから、サービス・インスタンスと関連付けられた API キーが削除されると、イベントが生成されます。</td>
  </tr>
</table>

##  アプリへのサービス・インスタンスのバインドのイベント
{: #at_events_rc_bind}

次の表に、呼び出されたときにイベントを生成する API メソッドのリストを示します。

<table>
  <caption>イベントを生成するアクション</caption>
  <tr>
    <th>アクション</th>
	  <th>説明</th>
  </tr>
  <tr>
    <td><i>service_name</i>.binding.create</td>
	  <td>サービス・インスタンスをアプリケーションにバインドすると、イベントが生成されます。</td>
  </tr>
  <tr>
    <td><i>service_name</i>.binding.delete</td>
	  <td>サービス・インスタンスをアプリケーションからアンバインドすると、イベントが生成されます。</td>
  </tr>
</table>




## イベントを検索する場所
{: #at_events_rc_ui}

{{site.data.keyword.cloudaccesstrailshort}} イベントは、**米国南部**地域の**アカウント・ドメイン**内で使用可能です。

これらのイベントを表示するには、**米国南部**地域に {{site.data.keyword.cloudaccesstrailshort}} サービスのインスタンスをプロビジョンする必要があります。 次に、{{site.data.keyword.cloudaccesstrailshort}} UI を開き、イベントを表示するアカウント・ドメインに移動します。 詳しくは、[アカウント・イベントの表示](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/viewing_events.html#view_acc_events_account_events)を参照してください。


