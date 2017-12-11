---

copyright:
  years: 2016, 2017
lastupdated: "2017-09-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# イベントの削除
{: #deleting_events}

*cf at delete* コマンドを使用して、特定の {{site.data.keyword.Bluemix}} スペースに対して {{site.data.keyword.cloudaccesstrailshort}} に保管されたイベントを手動で削除します。
{:shortdesc}

## イベントの削除
{: #viewing_events}

`cf at status` コマンドを使用して、サイズおよびカウントと、イベントが Kibana での分析に使用可能かどうかを表示します。詳しくは、[cf at status](/docs/services/cloud-activity-tracker/cli/at_cli.html#status) を参照してください。

1. {{site.data.keyword.Bluemix_notm}} 地域、組織、およびスペースにログインします。 

    ```
    bx login -a Endpoint
    ```
    {: codeblock}
	
	ここで、*Endpoint* は、{{site.data.keyword.Bluemix_notm}} にログインするための URL です。この URL は地域ごとに異なります。
	
	<table>
	    <caption>{{site.data.keyword.Bluemix_notm}} にアクセスするためのエンドポイントのリスト</caption>
		<tr>
		  <th>地域</th>
		  <th>URL</th>
		</tr>
		<tr>
		  <td>米国南部</td>
		  <td>api.ng.bluemix.net</td>
		</tr>
	</table>

    表示される指示に従います。 

    例えば、米国南部地域にログインするには、次のコマンドを実行します。
	
	```
	bx login -a api.ng.bluemix.net
	```
	{: codeblock}
	
	次に、組織およびスペースを設定します。以下のコマンドを実行します。

    ```
    bx target -o OrgName -s SpaceName
    ```
   {: codeblock}

    ここで、

    * OrgName は、組織の名前です。
    * SpaceName は、スペースの名前です。

2. *cf at status* コマンドを実行します。

    ```
    $ bx cf at status -a -s YYYY-MM-DD -e YYYY-MM-DD 
    ```
    {: codeblock}
    
    ここで、
    
    * *-a* は、アカウントのすべてのスペースに要求を適用することを指定するために使用されます。
    * *-s* は、開始日を協定世界時 (UTC) *YYYY-MM-DD* で設定するために使用されます。
    * *-e* は、終了日を協定世界時 (UTC) *YYYY-MM-DD* で設定するために使用されます。
    	
	オプション **-s** で開始日を、**-e** で終了日を設定して、`cf at status` コマンドを使用します。以下に例を示します。

    * `bx cf at status` を使用すると、最近 2 週間の情報が提供されます。
    * `bx cf at status -s 2017-05-03` を使用すると、2017 年 5 月 3 日から現在日付までの情報が提供されます。
    * `bx cf at status -s 2017-05-03 -e 2017-05-08` を使用すると、2017 年 5 月 3 日から 2017 年 5 月 8 日までの情報が提供されます。 
 
    オプション **-a** で有効範囲をアカウントに設定して、`cf at status` コマンドを使用します。
	
    例えば、2017 年 6 月 10 日の使用可能なイベントについての情報を取得するには、次のコマンドを実行します。
    
    ```
    $ bx cf at status -s 2017-06-10 -e 2017-06-10
    +------------+-------+------+------------+
    | Date       | Count | Size | Searchable |
    +------------+-------+------+------------+
    | 2017-07-10 | 1     | 2531 | All        |
    +------------+-------+------+------------+
    ```
    {: screen}
	














