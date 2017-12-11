---

copyright:
  years: 2016, 2017

lastupdated: "2017-09-17"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# Kibana ダッシュボードへのナビゲート
{: #launch_kibana}

Kibana は、{{site.data.keyword.Bluemix}} 内で {{site.data.keyword.cloudaccesstrailshort}} UI から起動するか、または Web ブラウザーから直接起動できます。
{:shortdesc}
   

##  Activity Tracker サービスのダッシュボードから Kibana へのナビゲート
{: #launch_Kibana_from_at}

Kibana で表示されるアクティビティー・ログには、{{site.data.keyword.cloudaccesstrailshort}} サービスがプロビジョンされていて、ログインしている、{{site.data.keyword.Bluemix_notm}} 組織のスペースにデプロイされたすべてのリソースのイベントが含まれます。

{{site.data.keyword.cloudaccesstrailshort}} サービスのダッシュボードから Kibana を起動するには、以下のステップを実行します。

1. {{site.data.keyword.Bluemix_notm}} アカウントにログインします。

    {{site.data.keyword.Bluemix_notm}} ダッシュボードは、[http://bluemix.net ![外部リンク・アイコン](../../../../icons/launch-glyph.svg "外部リンク・アイコン")](http://bluemix.net){:new_window} にあります。
    
	ユーザー ID とパスワードを使用してログインすると、{{site.data.keyword.Bluemix_notm}} UI が開きます。

2. {{site.data.keyword.Bluemix_notm}} ダッシュボードから {{site.data.keyword.cloudaccesstrailshort}} サービスを選択します。 
    
3. **「管理」**タブを選択します。

4. **「詳細ビュー」**をクリックします。 

    Kibana ダッシュボードが開きます。

デフォルトでは、**ActivityTracker_Space_Dashboard_in_24h** ダッシュボードがロードされ、時刻フィルターは過去 24 時間に設定されます。 


	
	
##  Web ブラウザーから Kibana へのナビゲート
{: #launch_Kibana_from_browser}

Kibana に表示されるログ情報には、ログインしている {{site.data.keyword.Bluemix_notm}} 組織のスペース内にデプロイされているすべてのリソースのイベントが含まれます。

ブラウザーから Kibana を起動するには、以下の手順を実行します。

1. Web ブラウザーを開き、Kibana を起動します。その後、Kibana ユーザー・インターフェースにログインします。
    
    例えば、Kibana を起動するために使用する必要のある、地域別の URL を以下の表に示します。
      
    <table>
          <caption>表 1. Kibana を起動するために使用する地域ごとの URL </caption>
           <tr>
            <th>地域</th>
            <th>URL</th>
          </tr>
          <tr>
            <td>米国南部</td>
            <td>[https://logging.ng.bluemix.net](https://logging.ng.bluemix.net) </td>
          </tr>
		  <tr>
            <td>英国</td>
            <td>[https://logmet.eu-gb.bluemix.net](https://logmet.eu-gb.bluemix.net)</td>
          </tr>
    </table>
	
	Kibana の「Discover」ページが開きます。
	
2. アクティビティー・ログの表示および分析を行いたい、{{site.data.keyword.Bluemix_notm}} アカウント、組織、およびスペースにログインしていることを確認します。

    ログインしているスペースで使用可能なイベントおよびログを表示できます。

3. イベントをフィルタリングするには、メニュー・バーから**「Open」**を選択します。

    保存済みダッシュボードのリストが表示されます。
	
4. ログインしているスペースのイベントを表示するには、**ActivityTracker_Space_Dashboard_in_24h** を選択します。


## 制限
{: #limitations}

 Kibana での制約のため、異なるスペースまたはアカウントを表示するために複数の Kibana ブラウザー・タブを同じセッションで一度に開くことはできません。したがって、一度に複数のセッションを開いて、スペースからアカウントへ (またはアカウントからスペースへ) 領域を変更すると、問題が発生する可能性があります。
	



