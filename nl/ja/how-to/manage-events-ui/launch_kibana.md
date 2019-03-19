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



# Kibana ダッシュボードへのナビゲート
{: #launch_kibana}

Kibana は、{{site.data.keyword.Bluemix}} 内で {{site.data.keyword.cloudaccesstrailshort}} UI から起動するか、または Web ブラウザーから直接起動できます。
{:shortdesc}
   

##  Activity Tracker サービスのダッシュボードから Kibana へのナビゲート
{: #launch_Kibana_from_at}

Kibana で表示されるアクティビティー・ログには、ユーザーがログインしている、{{site.data.keyword.cloudaccesstrailshort}} サービスがプロビジョンされている {{site.data.keyword.cloud_notm}} 組織のスペースにデプロイされた、すべてのリソースのイベントが含まれます。

{{site.data.keyword.cloudaccesstrailshort}} サービスのダッシュボードから Kibana を起動するには、以下のステップを実行します。

1. {{site.data.keyword.cloud_notm}} アカウントにログインします。

    {{site.data.keyword.cloud_notm}} ダッシュボードは、[https://cloud.ibm.com/login ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://cloud.ibm.com/login){:new_window} にあります。
    
	ユーザー ID とパスワードを使用してログインすると、{{site.data.keyword.cloud_notm}} UI が開きます。

2. {{site.data.keyword.cloud_notm}} ダッシュボードから {{site.data.keyword.cloudaccesstrailshort}} サービスを選択します。 
    
3. **「管理」**タブを選択します。

4. スペース・イベントを表示するには、*「ログの表示」* フィールドで**「スペース・ログ」**を選択します。**注:** これはデフォルトの表示です。次に、**「Kibana で表示」**をクリックします。 

    Kibana ダッシュボードが開きます。 時刻フィルターが過去 24 時間に設定され、**ActivityTracker_Space_Dashboard_in_24h** ダッシュボードがロードされます。

5. アカウント・イベントを表示するには、*「ログの表示」* フィールドで**「アカウント・ログ」**を選択します。次に、**「Kibana で表示」**をクリックします。 

    時刻フィルターが過去 24 時間に設定され、**ActivityTracker_Account_Dashboard_in_24h** ダッシュボードがロードされます。
	
	
##  Web ブラウザーから Kibana へのナビゲート
{: #launch_Kibana_from_browser}

ブラウザーから Kibana を起動するには、以下の手順を実行します。

1. イベントをモニターする地域で Web ブラウザーを開き、Kibana を起動します。その後、Kibana ユーザー・インターフェースにログインします。
    
    例えば、Kibana を起動するために使用する必要のある、地域別の URL を以下の表に示します。
      
    <table>
          <caption>表 1. Kibana を起動するために使用する地域ごとの URL</caption>
           <tr>
            <th>地域</th>
            <th>URL</th>
          </tr>
          <tr>
            <td>ドイツ</td>
            <td>[https://logging.eu-fra.bluemix.net](https://logging.eu-fra.bluemix.net) </td>
          </tr>
          <tr>
            <td>シドニー</td>
            <td>[https://logging.au-syd.bluemix.net](https://logging.au-syd.bluemix.net) </td>
          </tr>
		  <tr>
            <td>英国</td>
            <td>[https://logging.eu-gb.bluemix.net](https://logging.eu-gb.bluemix.net)</td>
          </tr>
		  <tr>
            <td>米国南部</td>
            <td>[https://logging.ng.bluemix.net](https://logging.ng.bluemix.net) </td>
          </tr>
    </table>
	
	Kibana の「Discover」ページが開きます。
	
2. アクティビティー・イベントの表示および分析を行いたい {{site.data.keyword.cloud_notm}} アカウントにログインしていることを確認します。

3. **ドメイン**を選択します。

    アカウント・ドメイン内のイベントを表示するには、**「アカウント」**を選択します。
    スペース・ドメイン内のイベントを表示するには、**「スペース」**を選択します。

Kibana に表示されるイベントは、Kibana を起動した地域で選択されたドメインでホストされているイベントに対応します。


## 制限
{: #launch_kibana_limitations}

 Kibana での制約のため、異なるスペースまたはアカウントを表示するために複数の Kibana ブラウザー・タブを同じセッションで一度に開くことはできません。 したがって、一度に複数のセッションを開いて、スペースからアカウントへ (またはアカウントからスペースへ) 有効範囲を変更すると、問題が発生する可能性があります。
	



