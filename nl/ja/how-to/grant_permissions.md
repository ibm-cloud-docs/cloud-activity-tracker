---

copyright:
  years: 2017, 2018

lastupdated: "2018-07-09"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# イベントを表示する許可の付与
{: #grant_permissions}

{{site.data.keyword.Bluemix}} では、Cloud Foundry 役割、IAM 役割、あるいは両方をユーザーに割り当てることができます。これらの役割は、ユーザーが {{site.data.keyword.cloudaccesstrailshort}} サービスを使用して作業するときに実行できるタスクを定義します。  
{:shortdesc}

## アカウント・イベントを表示する許可の付与
{: #grant_acc_events}

地域内のアカウント・イベントを表示するための以下の許可をユーザーに付与します。

1. {{site.data.keyword.cloudaccesstrailshort}} がプロビジョンされた地域のいずれかのスペースでの*開発者* 役割。 

    詳しくは、[CF 役割の付与](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_cf_role)を参照してください。

2. 地域での*ビューアー* 役割が指定された、{{site.data.keyword.loganalysisshort}} サービスの IAM ポリシー。 

    ビューアー役割は、必要な最小の IAM 役割です。 
	
	詳しくは、[IAM 許可の付与](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_iam_policy)を参照してください。


## スペース・イベントを表示する許可の付与
{: #grant_space_events}

地域内のスペース・イベントを表示するための以下の許可をユーザーに付与します。

* {{site.data.keyword.cloudaccesstrailshort}} がプロビジョンされた地域の当該スペースでの*開発者* 役割。 

    詳しくは、[CF 役割の付与](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_cf_role)を参照してください。


## IAM 許可の付与
{: #grant_iam_policy}

ユーザーに IAM 役割を付与するには、以下を考慮してください。

* アカウント内の他のユーザーにポリシーを割り当てる許可を持っているか、アカウント所有者である必要があります。アカウント所有者でない場合、**管理者** 役割が指定された、{{site.data.keyword.loganalysisshort}} サービスの IAM ポリシーを持っている必要があります。

* ポリシーを定義するときに指定する地域が、ユーザーがアカウント・ドメイン・イベントを表示する権限を付与される地域を定義します。

アカウント・ドメインからのイベントを表示する許可をユーザーに付与するには、以下のステップを実行します。

1. {{site.data.keyword.Bluemix_notm}} コンソールにログインします。

    Web ブラウザーを開き、{{site.data.keyword.Bluemix_notm}} ダッシュボード [http://bluemix.net ![外部リンク・アイコン](../../../icons/launch-glyph.svg "外部リンク・アイコン")](http://bluemix.net){:new_window} を起動します。
	
	ユーザー ID とパスワードを使用してログインすると、{{site.data.keyword.Bluemix_notm}} UI が開きます。

2. メニュー・バーから、**「管理」>「アカウント」>「ユーザー」**をクリックします。 

    *「ユーザー」*ウィンドウに、現在選択されているアカウントにおけるユーザーのリストが、E メール・アドレスと共に表示されます。
	
3. ユーザーがアカウントのメンバーである場合、リストからユーザー名を選択するか、または、**「アクション」**メニューから*「ユーザーの管理」*をクリックします。

    ユーザーがアカウントのメンバーでない場合、[ユーザーの招待](/docs/iam/iamuserinv.html#iamuserinv)を参照してください。

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
		<td>ユーザーにイベントに対する作業を行う権限が付与される地域を指定できます。1 つ以上の地域を個々に選択するか、または、**「すべての現行地域」**を選択してすべての地域の権限を付与します。</td>
	  </tr>
	  <tr>
	    <td>サービス・インスタンス</td>
		<td>*「すべてのサービス・インスタンス」* を選択します。</td>
	  </tr>
	  <tr>
	    <td>役割</td>
		<td>1 つ以上の IAM 役割を選択してください。 <br>有効な役割は、*管理者*、*オペレーター*、*エディター*、*ビューアー*です。 </td>
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

1. {{site.data.keyword.Bluemix_notm}} コンソールにログインします。

    Web ブラウザーを開き、{{site.data.keyword.Bluemix_notm}} ダッシュボード [http://bluemix.net ![外部リンク・アイコン](../../../icons/launch-glyph.svg "外部リンク・アイコン")](http://bluemix.net){:new_window} を起動します。
	
	ユーザー ID とパスワードを使用してログインすると、{{site.data.keyword.Bluemix_notm}} UI が開きます。

2. メニュー・バーから、**「管理」>「アカウント」>「ユーザー」**をクリックします。 

    *「ユーザー」*ウィンドウに、現在選択されているアカウントにおけるユーザーのリストが、E メール・アドレスと共に表示されます。
	
3. ユーザーがアカウントのメンバーである場合、リストからユーザー名を選択するか、または、**「アクション」**メニューから*「ユーザーの管理」*をクリックします。

    ユーザーがアカウントのメンバーでない場合、[ユーザーの招待](/docs/iam/iamuserinv.html#iamuserinv)を参照してください。

4. **「Cloud Foundry アクセス権限」**を選択し、組織を選択します。

    その組織で使用可能なスペースのリストが表示されます。

5. スペースを 1 つ選択します。 次に、メニュー・アクションから**「スペースの役割の編集」**を選択します。

6. **「開発者」**を選択します。
	
7. **「役割の保存」**をクリックします。




