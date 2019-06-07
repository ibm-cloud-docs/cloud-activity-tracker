---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, launch Kibana

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


# Kibana ダッシュボードのオープン
{: #launch_kibana}

Kibana は、{{site.data.keyword.cloud_notm}} 内で {{site.data.keyword.cloudaccesstrailshort}} UI から起動するか、または Web ブラウザーから直接起動できます。
{:shortdesc}
   
{{site.data.keyword.cloudaccesstrailfull}} は非推奨になりました。2019 年 5 月 9 日以降、新しい {{site.data.keyword.cloudaccesstrailshort}} インスタンスをプロビジョンできません。既存のプレミアム・プランのインスタンスは、2019 年 9 月 30 日までサポートされます。{{site.data.keyword.cloud_notm}} アカウントのアクティビティーのモニタリングを続行するには、[{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) のインスタンスをプロビジョンします。
{: deprecated}


##  Activity Tracker サービスのダッシュボードからの Kibana のオープン
{: #launch_Kibana_from_at}

Kibana で表示されるアクティビティー・ログには、ユーザーがログインしている、{{site.data.keyword.cloudaccesstrailshort}} サービスがプロビジョンされている {{site.data.keyword.cloud_notm}} 組織のスペースにデプロイされた、すべてのリソースのイベントが含まれます。

{{site.data.keyword.cloudaccesstrailshort}} サービスのダッシュボードから Kibana を起動するには、以下のステップを実行します。

1. {{site.data.keyword.cloud_notm}} アカウントにログインします。

    {{site.data.keyword.cloud_notm}} ダッシュボードは、[https://cloud.ibm.com/login ![外部リンク・アイコン](../../../icons/launch-glyph.svg "外部リンク・アイコン")](https://cloud.ibm.com/login){:new_window} にあります。
    
	ユーザー ID とパスワードを使用してログインすると、{{site.data.keyword.cloud_notm}} UI が開きます。

2. {{site.data.keyword.cloud_notm}} ダッシュボードから {{site.data.keyword.cloudaccesstrailshort}} サービスを選択します。 
    
3. **「管理」**タブを選択します。

4. スペース・イベントを表示するには、*「ログの表示」* フィールドで**「スペース・ログ」**を選択します。 **注:** これはデフォルトの表示です。 次に、**「Kibana で表示」**をクリックします。 

    Kibana ダッシュボードが開きます。 時刻フィルターが過去 24 時間に設定され、**ActivityTracker_Space_Dashboard_in_24h** ダッシュボードがロードされます。

5. アカウント・イベントを表示するには、*「ログの表示」* フィールドで**「アカウント・ログ」**を選択します。 次に、**「Kibana で表示」**をクリックします。 

    時刻フィルターが過去 24 時間に設定され、**ActivityTracker_Account_Dashboard_in_24h** ダッシュボードがロードされます。
	
	
##  Web ブラウザーからの Kibana のオープン
{: #launch_Kibana_from_browser}

ブラウザーから Kibana を起動するには、以下の手順を実行します。

1. イベントをモニターする地域で Web ブラウザーを開き、Kibana を起動します。 その後、Kibana ユーザー・インターフェースにログインします。
    
    例えば、Kibana を起動するために使用する必要のある、地域別の URL を以下の表に示します。
      
    <table>
          <caption>表 1. Kibana を起動するために使用する地域ごとの URL</caption>
           <tr>
            <th>地域</th>
            <th>URL</th>
          </tr>
          <tr>
            <td>ドイツ</td>
            <td>`https://logging.eu-fra.bluemix.net`</td>
          </tr>
          <tr>
            <td>シドニー</td>
            <td>`https://logging.au-syd.bluemix.net` </td>
          </tr>
		  <tr>
            <td>英国</td>
            <td>`https://logging.eu-gb.bluemix.net`</td>
          </tr>
		  <tr>
            <td>米国南部</td>
            <td>`https://logging.ng.bluemix.net`</td>
          </tr>
    </table>
	
	Kibana の「Discover」ページが開きます。
	
2. アクティビティー・イベントの表示および分析を行いたい {{site.data.keyword.cloud_notm}} アカウントにログインしていることを確認します。

3. スペースまたはアカウントのイベントを表示します

* Kibana ウィンドウ右上のログイン情報が表示されている場所をクリックします。
* **「ドメイン」**で、ドロップダウンからスペースまたはアカウントを選択します
* スペース・イベントの場合、スペースのドロップダウンから対象の**スペース**を選択します
* アカウント・イベントの場合、アカウントのドロップダウンから正しい**アカウント**を選択します

4. 検索時間を調整します

* Kibana のデフォルトの検索時間は最近 15 分間に設定されています。
* 右上のグレー・バーにある `Last 15 minutes` をクリックします
* どこまでさかのぼってイベントを表示するのかを選択します。 最近 3 日間のイベントが検索可能です。 3 日以内の時間フレームを選出してください。

5. Activity Tracker イベントのみを表示するようにフィルター操作します
* Kibana で直接表示する場合、ログと Activity Tracker イベントの両方が表示されることがあります。
* Activity Tracker イベントのみを表示するには、検索バーに `type:ActivityTracker` を入力します。

Kibana に表示されるイベントは、Kibana を起動した地域で選択されたドメインでホストされているイベントに対応します。

## 制限
{: #launch_kibana_limitations}

* Kibana での制約のため、異なるスペースまたはアカウントを表示するために複数の Kibana ブラウザー・タブを同じセッションで一度に開くことはできません。 したがって、一度に複数のセッションを開いて、スペースからアカウントへ (またはアカウントからスペースへ) 有効範囲を変更すると、問題が発生する可能性があります。
* デフォルトでは、アカウント所有者のみがアカウント・イベントを表示できます。 その他のユーザーがアカウント・イベントを表示できるようにするには、[アカウント・イベントの表示](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-view_acc_events#view_acc_events)に記述されている手順に従ってください。



