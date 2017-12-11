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


# Activity Tracker イベントのフィールド
{: #at_event}

{{site.data.keyword.cloudaccesstrailshort}} イベントは、Cloud Auditing Data Federation (CADF) 標準に基づいています。
{:shortdesc}

## イベントのフィールド
{: #fields}

以下の表に、{{site.data.keyword.cloudaccesstrailshort}} イベントの分析に使用可能なフィールドのリストを示します。

<table>
  <caption>表 1. イベントごとのモニターに使用可能なフィールド</caption>
  <tr>
    <th>フィールド名</th>
	<th>状況</th>
	<th>説明</th>
  </tr>
  <tr>
    <td>outcome</td>
	<td>必須</td>
	<td>有効な値は、*success*、*failure* です。</td>
  </tr>
  <tr>
    <td>typeURI</td>
	<td>必須</td>
	<td>このフィールドは *http://schemas.dmtf.org/cloud/audit/1.0/event* に設定されます。</td>
  </tr>
  <tr>
    <td>eventType</td>
	<td>必須</td>
	<td>このフィールドは *activity* に設定されます。</td>
  </tr>
  <tr>
    <td>eventTime </td>
	<td>必須</td>
	<td>日付は ISO ストリングで表されます (例: *2017-09-17 15:15:32.396 +0000 UTC*)。</td>
  </tr>
  <tr>
    <td>action</td>
	<td>必須</td>
	<td>このフィールドは、イベントをトリガーしたアクションを示します。例えば、*read.ibm-key-protect.secrets* です。</td>
  </tr>
  <tr>
    <td>id</td>
	<td>オプション</td>
	<td>このフィールドには、イベントの UUID が含まれます。</td>
  </tr>
  <tr>
    <td>initiator.id</td>
	<td>必須</td>
	<td>このフィールドには、イベントのソースの ID が含まれます。例えば、インスタンス ID です。</td>
  </tr>
  <tr>
    <td>initiator.name</td>
	<td>オプション</td>
	<td>このフィールドには、人間が理解しやすい、イベントのソースの名前が含まれます。例えば、ユーザー ID です。</td>
  </tr>
  <tr>
    <td>initiator.typeURI</td>
	<td>必須</td>
	<td>このフィールドは、イベントのソースのタイプを示します。例えば、*service/security/account/user* です。</td>
  </tr>
  <tr>
    <td>initiator.host.agent</td>
	<td>オプション</td>
	<td>このフィールドは、要求を送信するために使用されたクライアントを示します。例えば、*python-neutronclient* またはブラウザー情報です。</td>
  </tr>
  <tr>
    <td>initiator.host.address</td>
	<td>オプション</td>
	<td>このフィールドには、イニシエーターの IP アドレスが含まれます。</td>
  </tr>
  <tr>
    <td>target.id</td>
	<td>必須</td>
	<td>このフィールドには、ターゲット・サービスの ID が含まれます。</td>
  </tr>
  <tr>
    <td>target.name</td>
	<td>必須</td>
	<td>このフィールドには、人間が理解しやすい、ターゲット・サービスの名前が含まれます。例えば、*ibm-key-protect* です。</td>
  </tr>
  <tr>
    <td>target.typeURI</td>
	<td>必須</td>
	<td>このフィールドには、イベントのターゲットのタイプが含まれます。例えば、*service/ibm-key-protect/secrets* です。</td>
  </tr>
  <tr>
    <td>target.host.address</td>
	<td>オプション</td>
	<td>このフィールドには、ターゲット・サービスの IP アドレスまたは URL が含まれます。例えば、*xxx.bluemix.net* です。</td>
  </tr>
  <tr>
    <td>observer.name</td>
	<td>必須</td>
	<td>このフィールドは、値 *ActivityTracker* に設定されます。</td>
  </tr>
  <tr>
    <td>observer.id</td>
	<td>必須</td>
	<td>このフィールドには、CADF イベントを作成および保管するリソースについての情報が含まれます。例えば、*activitytracker.ng.bluemix.net* です。</td>
  </tr>
  <tr>
    <td>observer.typeURI</td>
	<td>必須</td>
	<td>このフィールドは、値 *service/security/edge/activity-tracker* に設定されます。</td>
  </tr>
  <tr>
    <td>reason.reasonCode</td>
	<td>オプション</td>
	<td>このフィールドには、HTTP 応答コードが含まれます。例えば、成功を示す *200* です。</td>
  </tr>
  <tr>
    <td>reason.reasonType</td>
	<td>必須</td>
	<td>このフィールドには、*reason.reasonCode* フィールドで reasonCode が提供された場合、それについての情報が含まれます。</td>
  </tr>
</table>

 

