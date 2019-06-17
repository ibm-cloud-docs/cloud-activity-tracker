---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, IAM

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

# イベントを表示する許可の付与
{: #grant_permissions}

{{site.data.keyword.cloud}} では、Cloud Foundry 役割、IAM 役割、あるいは両方をユーザーに割り当てることができます。 これらの役割は、{{site.data.keyword.cloudaccesstrailshort}} サービスを使用して作業するときにユーザーが実行できるタスクを定義します。  
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} は非推奨になりました。 2019 年 5 月 9 日以降、新しい {{site.data.keyword.cloudaccesstrailshort}} インスタンスをプロビジョンできません。 既存のプレミアム・プランのインスタンスは、2019 年 9 月 30 日までサポートされます。 {{site.data.keyword.cloud_notm}} アカウントのアクティビティーのモニタリングを続行するには、[{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) のインスタンスをプロビジョンします。
{: deprecated}

## アカウント・イベントを表示する許可の付与
{: #grant_acc_events}

地域内のアカウント・イベントを表示するための以下の許可をユーザーに付与します。

1. {{site.data.keyword.cloudaccesstrailshort}} がプロビジョンされた地域のいずれかのスペースでの*開発者* 役割。 

    詳しくは、[CF 役割の付与](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-grant_permissions#grant_cf_role)を参照してください。

2. 地域での*ビューアー* 役割が指定された、{{site.data.keyword.loganalysisshort}} サービスの IAM ポリシー。 

    ビューアー役割は、必要な最小の IAM 役割です。 
	
	詳しくは、[IAM 許可の付与](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-grant_permissions#grant_iam_policy)を参照してください。


## スペース・イベントを表示する許可の付与
{: #grant_space_events}

地域内のスペース・イベントを表示するための以下の許可をユーザーに付与します。

* {{site.data.keyword.cloudaccesstrailshort}} がプロビジョンされた地域の当該スペースでの*開発者* 役割。 

    詳しくは、[CF 役割の付与](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-grant_permissions#grant_cf_role)を参照してください。


## IAM 許可の付与
{: #grant_iam_policy}

ユーザーに IAM 役割を付与するには、以下を考慮してください。

* アカウント内の他のユーザーにポリシーを割り当てる許可を持っているか、アカウント所有者である必要があります。 アカウント所有者でない場合、**管理者** 役割が指定された、{{site.data.keyword.loganalysisshort}} サービスの IAM ポリシーを持っている必要があります。

* ポリシーを定義するときに指定する地域が、ユーザーがアカウント・ドメイン・イベントを表示する権限を付与される地域を定義します。

アカウント・ドメインからのイベントを表示する許可をユーザーに付与するには、以下のステップを実行します。

1. [{{site.data.keyword.cloud_notm}} コンソールにログイン ![外部リンク・アイコン](../../../icons/launch-glyph.svg "外部リンク・アイコン")](https://cloud.ibm.com/login){:new_window} します。
	
	ユーザー ID とパスワードを使用してログインすると、{{site.data.keyword.cloud_notm}} UI が開きます。

2. メニュー・バーから、**「管理」>「アカウント」>「ユーザー」**をクリックします。 

    *「ユーザー」*ウィンドウに、現在選択されているアカウントにおけるユーザーのリストが、E メール・アドレスと共に表示されます。
	
3. ユーザーがアカウントのメンバーである場合、リストからユーザー名を選択するか、または、**「アクション」**メニューから*「ユーザーの管理」*をクリックします。

    ユーザーがアカウントのメンバーでない場合、[ユーザーの招待](/docs/iam?topic=iam-iamuserinv#iamuserinv)を参照してください。

4. **「アクセス・ポリシー」**セクションで、**「アクセス権限の割り当て」**をクリックし、**「リソースへのアクセス権限の割り当て」**を選択します。

    *「ユーザー * へのリソース・アクセス権限の割り当て」* ウィンドウが開きます。

5. ポリシーに関する情報を入力します。 以下の表に、ポリシーを定義するために必要なフィールドを示します。 

    <table>
	  <caption>IAM ポリシーを構成するためのフィールドのリスト。</caption>
	  <tr>
	    <th>フィールド</th>
		<th>値</th>
	  </tr>
	  <tr>
	    <td>サービス</td>
		<td>*IBM Cloud Log Analysis*</td>
	  </tr>	  
	  <tr>
	    <td>地域</td>
		<td>ユーザーにイベントに対する作業を行う権限が付与される地域を指定できます。 1 つ以上の地域を個々に選択するか、または、**「すべての現行地域」**を選択してすべての地域の権限を付与します。</td>
	  </tr>
	  <tr>
	    <td>サービス・インスタンス</td>
		<td>*「すべてのサービス・インスタンス」* を選択します。</td>
	  </tr>
	  <tr>
	    <td>役割</td>
		<td>1 つ以上の IAM 役割を選択してください。 <br>有効な役割は、*アドミニストレーター*、*オペレーター*、*エディター*、*ビューアー*です。</td>
	  </tr>
     </table>
	
6. **「割り当て」**をクリックします。
	
構成したポリシーは、選択した地域で利用できます。 


## CF 役割の付与
{: #grant_cf_role}

ユーザーに CF 役割を付与するには、以下を考慮してください。

* ユーザーに Cloud Foundry 役割を割り当てるには、組織およびスペースでの許可を持っている必要があります。 

* **開発者**役割のみが、ユーザーにイベントの表示を許可します。

スペース・イベントを表示する権限をユーザーに付与するには、以下のステップを実行します。

1. [{{site.data.keyword.cloud_notm}} コンソールにログイン ![外部リンク・アイコン](../../../icons/launch-glyph.svg "外部リンク・アイコン")](https://cloud.ibm.com/login){:new_window} します。
	
	ユーザー ID とパスワードを使用してログインすると、{{site.data.keyword.cloud_notm}} UI が開きます。

2. メニュー・バーから、**「管理」>「アカウント」>「ユーザー」**をクリックします。 

    *「ユーザー」*ウィンドウに、現在選択されているアカウントにおけるユーザーのリストが、E メール・アドレスと共に表示されます。
	
3. ユーザーがアカウントのメンバーである場合、リストからユーザー名を選択するか、または、**「アクション」**メニューから*「ユーザーの管理」*をクリックします。

    ユーザーがアカウントのメンバーでない場合、[ユーザーの招待](/docs/iam?topic=iam-iamuserinv#iamuserinv)を参照してください。

4. **「Cloud Foundry アクセス権限」**を選択します。 次に、組織を選択します。

    その組織で使用可能なスペースがリストされます。

5. スペースを 1 つ選択します。 次に、メニュー・アクションから**「スペースの役割の編集」**を選択します。

6. **「開発者」**を選択します。
	
7. **「役割の保存」**をクリックします。




