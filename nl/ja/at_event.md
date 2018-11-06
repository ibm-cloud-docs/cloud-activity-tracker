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



# Activity Tracker イベントのフィールド
{: #at_event}

{{site.data.keyword.cloudaccesstrailshort}} イベントは、Cloud Auditing Data Federation (CADF) 標準に基づいています。 
{:shortdesc}

## イニシエーター・フィールド
{: #initiator}

以下の表に、{{site.data.keyword.cloudaccesstrailshort}} イベントに使用可能な共通フィールドを示します。

<table>
  <caption>共通イニシエーター・フィールド</caption>
  <tr>
    <th>フィールド名</th>
	  <th>説明</th>
    <th>値</th>
  </tr>
  <tr>
    <td>initiator.id</td>
	  <td>アクションのイニシエーターの ID。</br>イニシエーターには、IBMID と サービス ID の 2 つのタイプがあります。</td>
    <td>IBMID の例: IBMid-000000XXX2 </br>サービス ID の例: iam-ServiceId-12345678-0165-4c89-847d-9660b1632e14</td>
  </tr>
  <tr>
    <td>initiator.name</td>
	  <td>アクションを開始したユーザーのユーザー名。</td>
    <td></td>
  </tr>
  <tr>
    <td>initiator.typeURI</td>
	  <td>イベントのソースのタイプ。</td>
    <td>有効な値は、*service/security/account/user*、*service/security/clientid*、*service/security/account/serviceid* です。</td>
  </tr>
  <tr>
    <td>initiator.credential.type</td>
	  <td>イニシエーター ID 資格情報のタイプ。</td>
    <td>有効な値は、*user*、*token*、*apikey* です。</td>
  </tr>
</table>

## ターゲット・フィールド
{: #target}

以下の表に、{{site.data.keyword.cloudaccesstrailshort}} イベントに使用可能な共通ターゲット・フィールドを示します。

<table>
  <caption>共通ターゲット・フィールド</caption>
  <tr>
    <th>フィールド名</th>
	  <th>説明</th>
    <th>値</th>
  </tr>
  <tr>
    <td>target.id</td>
	  <td>アクションが実行されるリソースのクラウド・リソース名 (CRN)。</br>詳しくは、 [CRN フォーマット](/docs/overview/crn.html#format)を参照してください。</td>
    <td>例: `crn:v1:bluemix:public:cloud-object-storage:global:a/12345678e6232019c6567c9123456789:fr56et47-befb-440a-a223c-12345678dae1:bucket:bucket1`</td>
  </tr>
  <tr>
    <td>target.name</td>
	  <td>アクションが実行されるクラウド・リソースの、人が読める名前。</td>
    <td></td>
  </tr>
  <tr>
    <td>target.typeURI</td>
    <td>アクションが実行されるクラウド・リソースのタイプ。</br>このフィールドの形式は **serviceName/objectType** です。ここで、serviceName はサービスの名前です。</td>
	  <td>例: `iam-am/policy` または `cloud-object-storage/bucket/acl`</td>
  </tr>
</table>
 
## アクション・フィールド
{: #action}

以下の表に、{{site.data.keyword.cloudaccesstrailshort}} イベントに使用可能な共通アクション・フィールドを示します。

<table>
  <caption>共通アクション・フィールド</caption>
  <tr>
    <th>フィールド名</th>
	  <th>説明</th>
    <th>値</th>
  </tr>
  <tr>
    <td>action</td>
	  <td>イベントをトリガーするアクション。</br>このフィールドの形式は **serviceName.objectType.action** です。ここで、serviceName はサービスの名前です。</br>サービスによって生成されるイベントについて詳しくは、<a href="/docs/services/cloud-activity-tracker/cloud_services.html#cloud_services">Cloud サービス</a>を参照してください。</td>
    <td>例: *iam-identity.serviceid-apikey.login*</td>
  </tr>
  <tr>
    <td>eventTime</td>
	  <td>イベントが作成されたときのタイム・スタンプを示します。</br>日付は協定世界時 (UTC) で表されます。</br>フォーマットは ISO 8601 に準拠します。</td>
    <td>例: 2017-10-19T19:07:50.32+0000<td>
  </tr>
</table>

## 結果フィールド
{: #outcomes}

以下の表に、{{site.data.keyword.cloudaccesstrailshort}} イベントに使用可能な共通結果フィールドを示します。

<table>
  <caption>共通結果フィールド</caption>
  <tr>
    <th>フィールド名</th>
	  <th>説明</th>
    <th>値</th>
  </tr>
  <tr>
    <td>outcome</td>
	  <td>アクションの結果。</td>
    <td>有効な値は、*success*、*failure*、*pending* です。</td>
  </tr>
  <tr>
    <td>reason.reasonCode</td>
	  <td>HTTP 応答コードを含む数値フィールド。</td>
    <td>例えば、正常な結果の場合は *200* です。</td>
  </tr>
  <tr>
    <td>severity</td>
	  <td>クラウドでアクションが持つ可能性のある脅威のレベルを定義します。</td>
    <td>有効な値は、*normal*、*warning*、および *critical* です。</br></br>**normal** は、クラウドでのルーチン・アクションに対して設定されます。例えば、インスタンスの開始や、トークンのリフレッシュなどです。</br></br>**warning** は、クラウド・リソースの更新またはクラウド・リソースのメタデータの変更が行われるアクションに対して設定されます。例えば、ワーカー・ノードのバージョンの更新、証明書の名前変更、サービス・インスタンスを名前変更などです。</br></br>**critical** は、クラウドでのセキュリティーに影響するアクションに対して設定されます。例えば、ユーザーの資格情報の変更、データの削除、クラウド・リソースの処理のための無許可アクセスなどです。</td>
  </tr>
</table>
