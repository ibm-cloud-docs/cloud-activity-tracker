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


# IAM イベント
{: #at_events_iam}

セキュリティー担当者、監査員、またはマネージャーは、{{site.data.keyword.cloudaccesstrailfull}} サービスを使用して、ユーザーおよびアプリケーションが {{site.data.keyword.Bluemix}} 内の {{site.data.keyword.iamlong}} (IAM) サービスとどのように対話しているのかをトラッキングできます。 
{:shortdesc}

{{site.data.keyword.cloudaccesstrailshort}} サービスは、{{site.data.keyword.cloud_notm}} 内のサービスの状態を変更するユーザー開始アクティビティーを記録します。 詳しくは、[{{site.data.keyword.cloudaccesstrailshort}} 概要](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#activity_tracker_ov )を参照してください。

ユーザーのアクションのモニターを開始するには、[{{site.data.keyword.cloudaccesstrailfull_notm}}](/docs/services/cloud-activity-tracker/index.html#getting-started-with-cla)を参照してください。 

イニシエーターは、ユーザー、サービス、またはアプリケーションのいずれかです。
{: tip}

## アクセス・グループ管理のイベント
{: #at_events_iam_access}

次の表に、イベントを生成するアクションのリストを示します。

| アクション | 説明 |
|----------|---------|
| `iam-groups.group.create`   | イニシエーターがアクセス・グループを作成すると、イベントが生成されます。 | 
| `iam-groups.group.read`     | イニシエーターがアクセス・グループに関連する情報を参照すると、イベントが生成されます。 |
| `iam-groups.group.update`   | イニシエーターがグループの名前または説明を更新すると、イベントが生成されます。 |
| `iam-groups.group.delete`   | イニシエーターがアクセス・グループを削除すると、イベントが生成されます。 |
| `iam-groups.member.add`     | イニシエーターがアクセス・グループにメンバーを追加すると、イベントが生成されます。 |
| `iam-groups.member.delete`  | イニシエーターがアクセス・グループからメンバーを削除すると、イベントが生成されます。 |
| `iam-groups.member.read`    | イニシエーターがメンバーのメンバーシップをチェックすると、イベントが生成されます。 |
| `iam-groups.rule.read`      | イニシエーターがアクセス・グループ内のルールを表示すると、イベントが生成されます。 |
| `iam-groups.rule.create`    | イニシエーターがアクセス・グループにルールを追加すると、イベントが生成されます。 |
| `iam-groups.rule.update`    | イニシエーターがルール名を変更すると、イベントが生成されます。 |
| `iam-groups.rule.delete`    | イニシエーターがアクセス・グループからルールを削除すると、イベントが生成されます。 |
{: caption="表 1. アクセス・グループ管理アクション" caption-side="top"} 



## サービス ID 処理のイベント
{: #at_events_iam_serviceids}

次の表に、イベントを生成するアクションのリストを示します。

| アクション | 説明 |
|----------|---------|
| `iam-identity.account-serviceid.create` | イニシエーターがサービス ID を作成すると、イベントが生成されます。  | 
| `iam-identity.account-serviceid.update` | イニシエーターがサービス ID の名前または説明を変更すると、イベントが生成されます。 | 
| `iam-identity.account-serviceid.delete` | イニシエーターがサービス ID を削除すると、イベントが生成されます。 | 
{: caption="表 2. サービス ID 処理アクション" caption-side="top"} 


## API キー処理のイベント
{: #at_events_iam_apikeys}

次の表に、イベントを生成するアクションのリストを示します。

| アクション | 説明 |
|----------|---------|
| `iam-identity.user-apikey.create`      | イニシエーターが API キーを作成すると、イベントが生成されます。 | 
| `iam-identity.user-apikey.update`      | イニシエーターが API キーの名前または説明を変更すると、イベントが生成されます。 |  
| `iam-identity.user-apikey.delete`      | イニシエーターが API キーを削除すると、イベントが生成されます。 |  
| `iam-identity.serviceid-apikey.create` | イニシエーターがサービス ID 用の API キーを作成すると、イベントが生成されます。 |  
| `iam-identity.serviceid-apikey.delete` | イニシエーターがサービス ID 用の API キーを削除すると、イベントが生成されます。 |  
{: caption="表 3. API キー処理アクション" caption-side="top"} 


## ログインのイベント
{: #at_events_iam_login}

次の表に、イベントを生成するアクションのリストを示します。

| アクション | 説明 |
|----------|---------|
| `iam-identity.user-apikey.login`         | ユーザーが API キーを使用して {{site.data.keyword.cloud_notm}} にログインすると、イベントが生成されます。 |  
| `iam-identity.serviceid-apikey.login`    | イニシエーターがサービス ID と関連付けられた API キーを使用して {{site.data.keyword.cloud_notm}} にログインすると、イベントが生成されます。 |  
| `iam-identity.user-identitycookie.login` | これは、イニシエーターがアクションを実行するために新しい ID Cookie を要求すると生成されるイベントです。 |
| `iam-identity.user-refreshtoken.login`   | これは、イニシエーターが IBM Cloud にログインするか、または、IBM Cloud に既にログインしたイニシエーターがアクションを実行するために新しいリフレッシュ・トークンを要求すると生成されるイベントです。 |
{: caption="表 4. ユーザーのログインのアクション" caption-side="top"} 


## ポリシー管理のイベント
{: #at_events_iam_policies}

次の表に、イベントを生成するアクションのリストを示します。

| アクション | 説明 |
|----------|---------|
| `iam-am.policy.create` | イニシエーターがユーザーまたはアクセス・グループにポリシーを追加すると、イベントが生成されます。 |
| `iam-am.policy.delete` | イニシエーターがユーザーまたはアクセス・グループのポリシーへの許可を変更すると、イベントが生成されます。|
| `iam-am.policy.update` | イニシエーターがユーザーまたはアクセス・グループに割り当てられたポリシーを削除すると、イベントが生成されます。 |
{: caption="表 5. ポリシー管理アクション" caption-side="top"} 


## イベントの表示
{: #at_events_iam_ui}

{{site.data.keyword.cloudaccesstrailshort}} イベントは、**米国南部**地域の**アカウント・ドメイン**内で使用可能です。

これらのイベントを表示するには、**米国南部**地域に {{site.data.keyword.cloudaccesstrailshort}} サービスのインスタンスをプロビジョンする必要があります。 次に、{{site.data.keyword.cloudaccesstrailshort}} UI を開き、イベントを表示するアカウント・ドメインに移動します。 詳しくは、[アカウント・イベントの表示](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/viewing_events.html#account_events)を参照してください。

