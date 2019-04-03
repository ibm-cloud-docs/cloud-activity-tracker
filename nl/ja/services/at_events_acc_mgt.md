---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, account events

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

# アカウント管理イベント  
{: #at_events_acc_mgt}

セキュリティー担当者、監査員、またはマネージャーは、{{site.data.keyword.cloudaccesstrailfull}} サービスを使用して、ユーザーおよびアプリケーションが {{site.data.keyword.Bluemix}} アカウントとどのように対話しているのかをトラッキングできます。 
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull_notm}} サービスは、{{site.data.keyword.cloud_notm}} 内のサービスの状態を変更するユーザー開始アクティビティーを記録します。 詳しくは、[{{site.data.keyword.cloudaccesstrailshort}} の紹介](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov)を参照してください。

ユーザーのアクションのモニターを開始するには、[{{site.data.keyword.cloudaccesstrailfull_notm}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started-with-cla#getting-started-with-cla)を参照してください。 



## アカウント管理のイベント
{: #at_events_acc_mgt_account}

次の表に、呼び出されたときにイベントを生成する API メソッドのリストを示します。

<table>
  <caption>イベントを生成するアクション</caption>
  <tr>
    <th>アクション</th>
	  <th>説明</th>
  </tr>
  <tr>
    <td>billing.account.create</td>
	  <td>アカウントをプロビジョンすると、そのアカウントにアカウント ID が割り当てられた後、イベントが生成されます。</td>
  </tr>
  <tr>
    <td>billing.account.update</td>
	  <td>アカウントに関する情報を更新すると、イベントが生成されます。</td>
  </tr>
  <tr>
    <td>billing.account.active</td>
	  <td>アカウントを検証すると、イベントが生成されます。つまり、アカウントがアクティブになると、イベントが生成されます。</td>
  </tr>
  <tr>
    <td>billing.account.subscription.create</td>
	  <td><a href="/docs/account?topic=account-accounts#subscription-account">サブスクリプション・アカウント</a>を作成すると、イベントが生成されます。</td>
  </tr>
</table>



## ユーザー管理のイベント
{: #at_events_acc_mgt_users}

次の表に、呼び出されたときにイベントを生成する API メソッドのリストを示します。

<table>
  <caption>イベントを生成するアクション</caption>
  <tr>
    <th>アクション</th>
	  <th>説明</th>
  </tr>
  <tr>
    <td>user-management.user.create</td>
	  <td>アカウントに参加するようにユーザーに招待を送信すると、イベントが生成されます。 </br>アカウント内のユーザーでこのアクションを実行できるのは、アカウント所有者のみです。</td>
  </tr>
  <tr>
    <td>user-management.user.active</td>
	  <td>アカウント内のユーザーをアクティブにすると、イベントが生成されます。 </br>このイベントは、そのユーザーが自分の E メール・アドレスを検証したときに生成されます。</td>
  </tr>
  <tr>
    <td>user-management.account.user.delete</td>
	  <td>アカウントからユーザーを削除すると、イベントが生成されます。 </br>アカウント内のユーザーでこのアクションを実行できるのは、アカウント所有者のみです。</td>
  </tr>
</table>

## 組織管理のイベント
{: #at_events_acc_mgt_org}

次の表に、呼び出されたときにイベントを生成する API メソッドのリストを示します。

<table>
  <caption>イベントを生成するアクション</caption>
  <tr>
    <th>アクション</th>
	  <th>説明</th>
  </tr>
  <tr>
    <td>billing.account.org.create</td>
	  <td>アカウントに組織を追加すると、イベントが生成されます。</td>
  </tr>
</table>

## イベントを検索する場所
{: #at_events_acc_mgt_ui}

{{site.data.keyword.cloudaccesstrailshort}} イベントは、**米国南部**地域の**アカウント・ドメイン**内で使用可能です。 

これらのイベントを表示するには、**米国南部**地域に {{site.data.keyword.cloudaccesstrailshort}} サービスのインスタンスをプロビジョンする必要があります。 次に、{{site.data.keyword.cloudaccesstrailshort}} UI を開き、イベントを表示するアカウント・ドメインに移動します。  

詳しくは、[アカウント・イベントの表示](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-view_acc_events#view_acc_events_account_events)を参照してください。








