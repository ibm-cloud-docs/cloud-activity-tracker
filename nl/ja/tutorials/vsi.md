---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, VSI events, tutorial

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


# {{site.data.keyword.cloudaccesstrailshort}} での {{site.data.keyword.BluVirtServers_short}} および {{site.data.keyword.baremetal_short}} のモニター
{: #vsi}

このチュートリアルでは、{{site.data.keyword.cloud_notm}} アカウントでユーザーを構成して、それらのユーザーが {{site.data.keyword.BluVirtServers_short}} および {{site.data.keyword.baremetal_short}} を使用して処理するときに生成される {{site.data.keyword.cloudaccesstrailshort}} イベントをモニターできるようにする方法を説明します。
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} は非推奨になりました。2019 年 5 月 9 日以降、新しい {{site.data.keyword.cloudaccesstrailshort}} インスタンスをプロビジョンできません。既存のプレミアム・プランのインスタンスは、2019 年 9 月 30 日までサポートされます。{{site.data.keyword.cloud_notm}} アカウントのアクティビティーのモニタリングを続行するには、[{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) のインスタンスをプロビジョンします。
{: deprecated}

{{site.data.keyword.BluVirtServers}} は、専用のコアおよびメモリー割り振りと共に購入される拡張が容易な仮想サーバーです。 数分で追加が可能で、イメージ・テンプレートのような機能も利用できる計算リソースをお探しであれば、これは優れた選択肢です。 
* 詳しくは、[{{site.data.keyword.BluVirtServers_short}}](/docs/vsi?topic=virtual-servers-about-virtual-servers#about-virtual-servers)を参照してください。 
* {{site.data.keyword.cloudaccesstrailshort}} イベントを生成するアクションのリストについては、[{{site.data.keyword.BluVirtServers_short}} によって生成されるイベント](/docs/vsi?topic=virtual-servers-at_events#at_events)を参照してください。

{{site.data.keyword.baremetal_short}} は、ハードウェア・リソースへの下位レベルのアクセス権限でパフォーマンスと制御の機能を提供する、シングル・テナントの物理サーバーです。 
* 詳しくは、[{{site.data.keyword.baremetal_long}}](/docs/bare-metal?topic=bare-metal-about#about)を参照してください。
* {{site.data.keyword.cloudaccesstrailshort}} イベントを生成するアクションのリストについては、[{{site.data.keyword.baremetal_short}} によって生成されるイベント](/docs/bare-metal?topic=bare-metal-bm-at-events#bm-at-events)を参照してください。

**ユーザーが {{site.data.keyword.BluVirtServers_short}} および {{site.data.keyword.baremetal_short}} {{site.data.keyword.cloudaccesstrailshort}} イベントを生成するには、ユーザーは IBM Cloud コンソールのインフラストラクチャー・リソースにアクセスできる必要があります。**
{: tip}

## ステップ 1. Softlayer アカウントを {{site.data.keyword.cloud_notm}} アカウントにリンクする
{: #vsi_step1}

** {{site.data.keyword.cloudaccesstrailshort}} イベントを生成するには、Softlayer アカウントが {{site.data.keyword.cloud_notm}} アカウントにリンクされていなければなりません。 詳しくは、『[IBMid への切り替えとアカウントのリンク](/docs/account?topic=account-unifyingaccounts#link_accounts)』を参照してください。

Softlayer アカウントを {{site.data.keyword.cloud_notm}} アカウントにリンクする際には、以下のことを考慮してください。
* すべての新しいアカウントは自動的に IBMid を受け取り、SAML フェデレーテッド・アカウントを除く既存の SoftLayer アカウントは IBMid 認証に切り替えることができます。
* {{site.data.keyword.cloud_notm}} アカウントにリンクする予定の各 SoftLayer アカウントは、固有の E メール・アドレスを持つ固有の IBMid によって所有される必要があります。
* 既存の SoftLayer アカウントを IBMid に切り替えるには、IBMid を作成し、次に登録コードを使用してその ID を確認します。
* アカウントを IBMid アカウントに切り替えた後、Infrastructure as a Service (IaaS) リソースと Platform as a Service (PaaS) リソースを組み合わせて使用するために、SoftLayer アカウントと {{site.data.keyword.cloud_notm}} アカウントをリンクすることができます。 

以下のステップを実行してアカウントをリンクします。
1. [IBMid および登録コードの要求](/docs/account?topic=account-unifyingaccounts#reqIBMidandregcode)
2. [登録コードを使用した IBMid の確認](/docs/account?topic=account-unifyingaccounts#confIBMiduseregcode)
3. [IBMid アカウントのリンク](/docs/account?topic=account-unifyingaccounts#link_user_account)


## ステップ 2. インフラストラクチャーの許可をユーザーに付与する
{: #vsi_step2}

**注:** *{{site.data.keyword.cloud_notm}} インフラストラクチャー・ポータル* から許可を付与すると、そのユーザーは、デバイスを管理するために *{{site.data.keyword.cloud_notm}} インフラストラクチャー* ・ダッシュボードからのアクセス権限を持たず、{{site.data.keyword.cloudaccesstrailshort}} イベントは生成されません。 **デバイスを管理するには、{{site.data.keyword.cloud_notm}} アカウントを通じてインフラストラクチャー許可をユーザーに付与する必要があります。 これらのアクションは、{{site.data.keyword.cloudaccesstrailshort}} イベントを生成します。**
{: tip}

インフラストラクチャー許可をユーザーに付与するには、以下のステップを実行します。

1. [{{site.data.keyword.cloud_notm}} にログイン ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://cloud.ibm.com/login){:new_window} します。
    
	ユーザー ID とパスワードを使用してログインすると、{{site.data.keyword.cloud_notm}} UI が開きます。

2. メニュー・バーで**「管理」** &gt; **「アカウント」**をクリックし、**「ユーザー」**を選択します。 

3. デバイスを処理する許可の付与対象ユーザーを選択します。

4. **「アクセス権限の割り当て (Assign access)」**を選択します。

5. **「SoftLayer アカウントへのアクセス権限の割り当て」**を選択します。 {{site.data.keyword.cloud_notm}} インフラストラクチャー・ポータルが {{site.data.keyword.cloud_notm}} のコンテキスト内で開きます。

6. デバイスを管理するためにユーザーに付与する許可を設定します。 **「ポータルの許可」**を選択します。 次に、**「デバイス」**セクションで、デバイスを管理するためにユーザーが必要とする許可を、ユーザーに付与します。 例えば、`仮想サーバー詳細の表示`、`サーバーをリブートして IPMI システム情報を表示する`、`サーバーのアップグレード`、または `OS 再ロードを実行してレスキュー・カーネルを開始する`などの許可を変更できます。

7. ポータルの許可を保存します。 **「デバイス・アクセス権限」**を選択すると、変更の保存を求めるプロンプトが出されます。 **「保存」**をクリックします。

8. 当該ユーザーが管理できるデバイスを設定します。 **「デバイス・アクセス権限」**セクションで、物理デバイスを選択します。 次に、**「デバイスへのアクセス権限の更新」**をクリックします。






