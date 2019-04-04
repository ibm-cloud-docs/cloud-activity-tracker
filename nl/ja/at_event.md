---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

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



# イベントのフィールド
{: #at_event}

{{site.data.keyword.cloudaccesstrailshort}} イベントは、Cloud Auditing Data Federation (CADF) 標準に基づいています。 
{:shortdesc}

## イニシエーター・フィールド
{: #initiator}

以下の表に、{{site.data.keyword.cloudaccesstrailshort}} イベントに使用可能な共通フィールドを示します。

| フィールド名 | 説明 | 値 |
|------------|-------------|-------|
| `initiator.id` | アクションのイニシエーターの ID。 </br></br>イニシエーターの有効なタイプは、`IBMid`、`サービス ID`、および `Cloud Foundry (CF) ユーザー ID` です。| IBMid の例: `IBMid-000000XXX2` </br>サービス ID の例: `iam-ServiceId-12345678-0165-4c89-847d-9660b1632e14` </br>CF ユーザー ID の例: `7666666b-23ae-4a34-8569-cu75tgdr4da3` |
| `initiator.name` | アクションを開始したユーザーのユーザー名。 | 例えば、E メール・アドレスなどです。 |
| `initiator.typeURI` | イベントのソースのタイプ。 | 有効な値は、*service/security/account/user*、*service/security/clientid*、および *service/security/account/serviceid* です。|
| `initiator.credential.type` | イニシエーター ID 資格情報のタイプ。 | 有効な値は、*user*、*token*、および *apikey* です。|
{: caption="表 1. 共通のイニシエーター・フィールド" caption-side="top"} 

  

## ターゲット・フィールド
{: #target}

以下の表に、{{site.data.keyword.cloudaccesstrailshort}} イベントに使用可能な共通ターゲット・フィールドを示します。

| フィールド名 | 説明 | 値 |
|------------|-------------|-------|
| `target.id` | アクションが実行されるリソースのクラウド・リソース名 (CRN)。 </br>詳しくは、 [CRN フォーマット](/docs/overview?topic=overview-format-crn#format)を参照してください。 | 例: `crn:v1:bluemix:public:cloud-object-storage:global:a/12345678e6232019c6567c9123456789:fr56et47-befb-440a-a223c-12345678dae1:bucket:bucket1` |
| `target.name` | アクションが実行されるクラウド・リソースの、人が読める名前。 |  |
| `target.typeURI` | アクションが実行されるクラウド・リソースのタイプ。 </br>このフィールドの形式は **serviceName/objectType** です。ここで、`servicename` はサービスの名前です。| 例: `iam-am/policy` または `cloud-object-storage/bucket/acl` |
{: caption="表 2. 共通のターゲット・フィールド" caption-side="top"} 


 
## アクション・フィールド
{: #action}

以下の表に、{{site.data.keyword.cloudaccesstrailshort}} イベントに使用可能な共通アクション・フィールドを示します。

| フィールド名 | 説明 | 値 |
|------------|-------------|-------|
| `action` | イベントをトリガーするアクション。 </br>このフィールドの形式は **serviceName.objectType.action** です。ここで、`servicename` はサービスの名前です。</br>サービスによって生成されるイベントのアクション値について詳しくは、<a href="/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-cloud_services#cloud_services">クラウド・サービス</a>を参照してください。 | 例: `iam-identity.serviceid-apikey.login` |
| `eventTime` | イベントが作成されたときのタイム・スタンプを示します。 </br>日付は協定世界時 (UTC) で表されます。</br>フォーマットは ISO 8601 に準拠します。 | 例: `2017-10-19T19:07:50.32+0000` |
{: caption="表 3. 共通アクション・フィールド" caption-side="top"} 



## 結果フィールド
{: #outcomes}

以下の表に、{{site.data.keyword.cloudaccesstrailshort}} イベントに使用可能な共通結果フィールドを示します。

| フィールド名 | 説明 | 値 |
|------------|-------------|-------|
| `outcome` | アクションの結果。 |有効な値は、*success*、*failure*、および *pending* です。 |
| `reason.reasonCode` | HTTP 応答コードを含む数値フィールド。 | 例えば、正常な結果の場合は *200* です。 |
| `severity` | クラウドでアクションが持つ可能性のある脅威のレベルを定義します。 | 有効な値は、*normal*、*warning*、および *critical* です。 </br></br>**normal** は、クラウドでのルーチン・アクションに対して設定されます。 例えば、インスタンスの開始や、トークンのリフレッシュなどです。 </br></br>**warning** は、クラウド・リソースの更新またはクラウド・リソースのメタデータの変更が行われるアクションに対して設定されます。 例えば、ワーカー・ノードのバージョンの更新、証明書の名前変更、サービス・インスタンスの名前変更などです。 </br></br>**critical** は、クラウドでのセキュリティーに影響するアクションに対して設定されます。 例えば、ユーザーの資格情報の変更、データの削除、クラウド・リソースの処理のための無許可アクセスなどです。 |
{: caption="表 4. 共通結果フィールド" caption-side="top"} 


