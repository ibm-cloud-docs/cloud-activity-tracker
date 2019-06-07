---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, cloud services

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



# クラウド・サービス
{: #cloud_services}

{{site.data.keyword.cloudaccesstraillong}} サービスを使用して、{{site.data.keyword.IBM_notm}} クラウド内の以下のいずれかのサービスの状態を変更するユーザー開始アクティビティーをモニターします。
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} は非推奨になりました。2019 年 5 月 9 日以降、新しい {{site.data.keyword.cloudaccesstrailshort}} インスタンスをプロビジョンできません。既存のプレミアム・プランのインスタンスは、2019 年 9 月 30 日までサポートされます。{{site.data.keyword.cloud_notm}} アカウントのアクティビティーのモニタリングを続行するには、[{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) のインスタンスをプロビジョンします。
{: deprecated}

**注:** {{site.data.keyword.cloud_notm}} でサービスが使用可能な地域についての情報を取得するには、[地域ごとのサービス](/docs/resources?topic=resources-services_region#services_region)を参照してください。


## コンピュート・インフラストラクチャー・サービス
{: #infrastructure}

**注:** ユーザーが {{site.data.keyword.BluVirtServers_short}} および {{site.data.keyword.baremetal_short}} {{site.data.keyword.cloudaccesstrailshort}} イベントを生成するには、ユーザーは {{site.data.keyword.cloud_notm}} コンソールのインフラストラクチャー・リソースにアクセスできる必要があります。詳しくは、[{{site.data.keyword.cloudaccesstrailshort}} での {{site.data.keyword.BluVirtServers_short}} および {{site.data.keyword.baremetal_short}} アクティビティーのモニター](/docs/services/cloud-activity-tracker/tutorials?topic=cloud-activity-tracker-vsi#vsi)を参照してください。

以下の表に、イベントを {{site.data.keyword.cloudaccesstrailshort}} に送信するインフラストラクチャー・サービスをリストします。

| サービス     | 説明 | {{site.data.keyword.cloudaccesstrailshort}} イベント |
|-------------|-------------|-------------|
| [{{site.data.keyword.BluVirtServers_short}} ](/docs/vsi?topic=virtual-servers-about-virtual-servers#about-virtual-servers)| {{site.data.keyword.BluVirtServers}} は、専用のコアおよびメモリー割り振りと共に購入される、拡張が容易な仮想サーバーです。 数分で追加が可能で、イメージ・テンプレートのような機能も利用できるコンピュート・リソースをお探しであれば、これは優れた選択肢です。  | [{{site.data.keyword.BluVirtServers_short}} によって生成されるイベント](/docs/vsi?topic=virtual-servers-at_events#at_events) |  
| [{{site.data.keyword.baremetal_long}} ](/docs/bare-metal?topic=bare-metal-about-bm#about-bm) | {{site.data.keyword.baremetal_short}} は、ハードウェア・リソースへの下位レベルのアクセス権限でパフォーマンスと制御の機能を提供する、シングル・テナントの物理サーバーです。 | [{{site.data.keyword.baremetal_short}} によって生成されるイベント](/docs/bare-metal?topic=bare-metal-bm-at-events#bm-at-events) | 
{: caption="イベントを {{site.data.keyword.cloudaccesstrailshort}} に送信するインフラストラクチャー・サービスのリスト" caption-side="top"} 




## コンピュート・サーバーレス・サービス
{: #serverless}

以下の表に、イベントを {{site.data.keyword.cloudaccesstrailshort}} に送信するサーバーレス・コンピュート・サービスをリストします。

| サービス     | 説明 | {{site.data.keyword.cloudaccesstrailshort}} イベント |
|-------------|-------------|-------------|
| [{{site.data.keyword.openwhisk_short}}](/docs/openwhisk?topic=cloud-functions-index#index) | {{site.data.keyword.openwhisk_short}} は、Apache OpenWhisk に基づく多言語 Functions-as-a-Service (FaaS) プログラミング・プラットフォームであり、軽量の`アクションと呼ばれるコード`を書くために使用できます。 | [{{site.data.keyword.openwhisk_short}} によって生成されるイベント](/docs/openwhisk?topic=cloud-functions-activity_tracker#activity_tracker) |
{: caption="イベントを {{site.data.keyword.cloudaccesstrailshort}} に送信するサーバーレス・コンピュート・サービスのリスト" caption-side="top"} 



## プラットフォーム・コンテナー・サービス
{: #ikcs}

{{site.data.keyword.containershort_notm}} は、以下の 2 つのタイプの {{site.data.keyword.cloudaccesstrailshort}} イベントを生成します。

* **クラスター管理イベント**
    
    * これらのイベントは自動的に生成されます。
    * これらのイベントは自動的に {{site.data.keyword.cloudaccesstrailshort}} に転送されます。
    * {{site.data.keyword.cloudaccesstrailshort}} **アカウント・ドメイン**を通してこれらのイベントを表示できます。 

* **Kubernetes API サーバー監査イベント**

    * これらのイベントは自動的に生成されます。
    * これらのイベントを {{site.data.keyword.cloudaccesstrailshort}} サービスに転送するには、クラスターを構成する必要があります。
    * イベントを {{site.data.keyword.cloudaccesstrailshort}} **アカウント・ドメイン**に送信するように、または、**スペース・ドメイン**に送信するように、クラスターを構成できます。 詳しくは、[監査ログの送信](/docs/containers?topic=containers-health#api_forward)を参照してください。

以下の表に、イベントを {{site.data.keyword.cloudaccesstrailshort}} に送信するコンテナー・プラットフォーム・サービスをリストします。

| サービス     | 説明 | {{site.data.keyword.cloudaccesstrailshort}} イベント |
|-------------|-------------|-------------|
| [{{site.data.keyword.containerlong_notm}}: クラスター管理イベント](/docs/containers?topic=containers-container_index#container_index)| これらのイベントは、クラスターの作成、削除、または更新などのアクションについて報告します。 | [クラスター管理イベント](/docs/containers?topic=containers-at_events#cluster-events) |  
| [{{site.data.keyword.containerlong_notm}}: API サーバー監査イベント](/docs/containers?topic=containers-container_index#container_index)| Kubernetes API サーバー監査イベントは、クラスターに影響を与える一連のアクティビティーについて発生順の情報を提供します。 各アクションが 1 つのイベントを生成します。 | [Kubernetes API サーバー監査イベント](/docs/containers?topic=containers-at_events#kube-events) |
| [{{site.data.keyword.registrylong_notm}}](/docs/services/Registry?topic=registry-registry_overview#registry_overview) | {{site.data.keyword.registrylong_notm}} サービスを使用して、可用性の高いスケーラブルなアーキテクチャーでプライベート Docker イメージの保管およびアクセスを行うことができます。 | [{{site.data.keyword.registrylong_notm}} との対話時に生成されるイベント](/docs/services/Registry?topic=registry-at_events#at_events) | 
{: caption="コンテナー・イベント" caption-side="top"} 



## プラットフォーム Cloud Foundry アプリケーション
{: #platform_cfapps}

Cloud Foundry アプリケーションによって {{site.data.keyword.cloudaccesstrailshort}} に送信されるイベントは、`GET /v2/events` の応答域の本体セクション内にリストされます。 *type* フィールドに、イベントを生成するすべてのアクションがリストされます。 詳しくは、[イベント API ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://apidocs.cloudfoundry.org/270/events/list_all_events.html){:new_window} を参照してください。


## プラットフォーム・コア統合サービス
{: #platform_core_integrated}

コア・プラットフォーム・サービスは、{{site.data.keyword.cloudaccesstrailshort}} **アカウント・ドメイン**を通して表示できる、{{site.data.keyword.cloudaccesstrailshort}} イベントを生成します。

以下の表に、イベントを {{site.data.keyword.cloudaccesstrailshort}} に送信するコア・プラットフォーム・サービスをリストします。

| サービス     | 説明 | {{site.data.keyword.cloudaccesstrailshort}} イベント |
|-------------|-------------|-------------|
| [{{site.data.keyword.iamshort}} (IAM) によって管理されるリソース用のカタログ・サービスのプロビジョンおよび管理](/docs/overview?topic=overview-ui#catalogcreate) | サービス・インスタンスのプロビジョン、サービス・インスタンスの名前変更、サービス・インスタンスのプラン変更、およびサービス・インスタンスの削除を行うことができます。 | [カタログ・サービスとの対話時に生成されるイベント](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_rc#at_events_rc) |  
| [Cloud Foundry スペースにバインドされたカタログ・サービスのプロビジョンおよび管理](/docs/overview?topic=overview-ui#catalogcreate)| サービス・インスタンスのプロビジョン、サービス・インスタンスの名前変更、サービス・インスタンスのプラン変更、およびサービス・インスタンスの削除を行うことができます。 </br>これらのイベントは、CF スペースにプロビジョンされたサービスに対して生成されます。 | [カタログ・サービスとの対話時に生成されるイベント](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-cf#cf_catalog) |  
| [アカウントの管理](/docs/account?topic=account-accounts#accounts) | {{site.data.keyword.IBM_notm}} アカウントの登録には、既存の IBMid を使用するか、新規 IBMid を作成するか、フェデレーテッド ID を使用することができます。 | [アカウントの管理時に生成されるイベント](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_acc_mgt#at_events_acc_mgt_account) |
| [ユーザーの管理](/docs/iam?topic=iam-iamuserinv#iamusermanage) | 所有または管理するアカウントまたは組織全体のユーザーを表示および管理することができます。  | [ユーザーの管理時に生成されるイベント](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_acc_mgt#at_events_acc_mgt_users) |
| [組織の管理](/docs/account?topic=account-orgsspacesusers#orgsspacesusers) | アカウント所有者はアカウントへの組織の追加および管理を行うことができます。 | [組織の管理時に生成されるイベント](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_acc_mgt#at_events_acc_mgt_org) |
{: caption="コア・プラットフォーム・アクションのリスト" caption-side="top"} 


## プラットフォーム・データベース・サービス
{: #database}

以下の表に、イベントを {{site.data.keyword.cloudaccesstrailshort}} に送信するデータベース・サービスをリストします。

| サービス     | 説明 | {{site.data.keyword.cloudaccesstrailshort}} イベント |
|-------------|-------------|----------------------------------------------------|
| [{{site.data.keyword.databases-for-postgresql_full_notm}}](/docs/services/databases-for-postgresql?topic=databases-for-postgresql-about#about) | {{site.data.keyword.databases-for-postgresql_full_notm}} は、{{site.data.keyword.cloud_notm}} でホストされ、他の {{site.data.keyword.cloud_notm}} サービスと統合される管理対象 PostgreSQL サービスです。 | [{{site.data.keyword.databases-for-postgresql_full_notm}} によって生成されるイベント](/docs/services/databases-for-postgresql?topic=databases-for-postgresql-activity-tracker#activity-tracker) |
| [{{site.data.keyword.databases-for-redis_full_notm}}](/docs/services/databases-for-redis?topic=databases-for-redis-about#about-databases-for-redis) | {{site.data.keyword.databases-for-redis_full_notm}} は、{{site.data.keyword.cloud_notm}} でホストされ、他の {{site.data.keyword.cloud_notm}} サービスと統合される管理対象サービスです。 | [{{site.data.keyword.databases-for-redis_full_notm}} によって生成されるイベント](/docs/services/databases-for-redis?topic=databases-for-redis-activity-tracker-integration#activity-tracker-integration) |
| [{{site.data.keyword.sqlquery_short}}](/docs/services/sql-query?topic=sql-query-overview#overview) | {{site.data.keyword.sqlquery_short}} サービスを使用して、矩形データを分析、変換、またはクリーンアップするためのSQL 照会 (つまり、SELECT ステートメント) を実行できます。 | [{{site.data.keyword.sqlquery_short}} によって生成されるイベント](/docs/services/sql-query?topic=sql-query-activitytracker#activity-tracker-events) |  
| [{{site.data.keyword.databases-for-etcd_full_notm}}](/docs/services/databases-for-etcd?topic=databases-for-etcd-about#about-databases-for-etcd) | {{site.data.keyword.databases-for-etcd_full_notm}} は、{{site.data.keyword.cloud_notm}} でホストされ、他の {{site.data.keyword.cloud_notm}} サービスと統合される管理対象 etcd サービスです。 | [{{site.data.keyword.databases-for-etcd_full_notm}} によって生成されるイベント](/docs/services/databases-for-etcd?topic=databases-for-etcd-activity-tracker#activity-tracker-integration) |
| [{{site.data.keyword.databases-for-elasticsearch_full_notm}}](/docs/services/databases-for-elasticsearch?topic=databases-for-elasticsearch-about#about-databases-for-elasticsearch) | {{site.data.keyword.databases-for-elasticsearch_full_notm}} は、{{site.data.keyword.cloud_notm}} でホストされ、他の {{site.data.keyword.cloud_notm}} サービスと統合される管理対象 Elasticsearch サービスです。 | [{{site.data.keyword.databases-for-elasticsearch_full_notm}} によって生成されるイベント](/docs/services/databases-for-elasticsearch?topic=databases-for-elasticsearch-activity-tracker#activity-tracker-integration) |
| [{{site.data.keyword.messages-for-rabbitmq_full_notm}}](/docs/services/messages-for-rabbitmq?topic=messages-for-rabbitmq-about#about-messages-for-rabbitmq)  | {{site.data.keyword.messages-for-rabbitmq_full_notm}} は、{{site.data.keyword.cloud_notm}} でホストされ、他の {{site.data.keyword.cloud_notm}} サービスと統合される管理対象 RabbitMQ サービスです。   | [{{site.data.keyword.messages-for-rabbitmq_full_notm}} によって生成されるイベント](/docs/services/messages-for-rabbitmq?topic=messages-for-rabbitmq-activity-tracker#activity-tracker-integration) |
{: caption="イベントを {{site.data.keyword.cloudaccesstrailshort}} に送信するデータベース・サービスのリスト" caption-side="top"} 




## プラットフォーム開発者用ツール
{: #devops}

以下の表に、イベントを {{site.data.keyword.cloudaccesstrailshort}} に送信する DevOps サービスをリストします。

| サービス     | 説明 | {{site.data.keyword.cloudaccesstrailshort}} イベント |
|-------------|-------------|-------------|
| [{{site.data.keyword.DRA_short}}](/docs/apps?topic=creating-apps-insights-overview) | {{site.data.keyword.DRA_short}} は、{{site.data.keyword.cloud_notm}} オープン・ツールチェーン・カタログ内の統合の 1 つです。 | [{{site.data.keyword.DRA_short}} によって生成されるイベント](/docs/apps?topic=creating-apps-at_events) |
| [{{site.data.keyword.contdelivery_short}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-cd_overview#cd_overview) | {{site.data.keyword.contdelivery_short}} は、DevOps プラクティスや業界最高レベルのツールを使用したアプリケーションのビルド、テスト、デリバリーを可能にします。 | [{{site.data.keyword.contdelivery_short}} によって生成されるイベント](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-at_events#at_events) |
| [{{site.data.keyword.GlobalizationPipeline_short}}](/docs/services/GlobalizationPipeline?topic=GlobalizationPipeline-globalizationpipeline#globalizationpipeline) | アプリの開発者が翻訳済みアプリケーションをグローバルな顧客に素早くリリースすることを可能にします。 | [{{site.data.keyword.GlobalizationPipeline_short}} によって生成されるイベント](/docs/services/GlobalizationPipeline?topic=GlobalizationPipeline-gpat_events#gpat_events)|
{: caption="イベントを {{site.data.keyword.cloudaccesstrailshort}} に送信する開発者用ツールのリスト" caption-side="top"} 



## プラットフォーム統合開発者サービス
{: #integrated_dev_svcs}

以下の表に、アプリの開発および {{site.data.keyword.cloudaccesstrailshort}} へのイベントの送信を行うために使用できるクラウド・サービスをリストします。

| サービス     | 説明 | {{site.data.keyword.cloudaccesstrailshort}} イベント |
|-------------|-------------|-------------|
| [{{site.data.keyword.dev_console}}](/docs/apps?topic=creating-apps-tutorial-getting-started#create) | {{site.data.keyword.cloud_notm}} では、企業レベルのモバイル・アプリケーションおよび Web アプリケーションを作成でき、{{site.data.keyword.cloud_notm}} でホストされているクラウド拡張機能を利用できます。 アプリをビルド、実行、およびデプロイするには、{{site.data.keyword.cloud_notm}} コンソールおよびコマンド・ライン・ツールを使用できます。 スターター・キットを使用してアプリを作成するには、{{site.data.keyword.dev_console}} を使用できます。 | [{{site.data.keyword.dev_console}} によって生成されるイベント](/docs/apps?topic=creating-apps-at_events#at_events) |
| [{{site.data.keyword.mobilepushshort}}](/docs/services/mobilepush?topic=mobile-pushnotification-overview-push#overview-push)| {{site.data.keyword.mobilepushshort}} サービスを使用して、通知をモバイル・デバイスおよびブラウザーに送信できます。 通知は、すべてのアプリケーション・ユーザーを宛先にするか、または、タグを使用することによって特定のユーザーおよびデバイスのセットを宛先にすることができます。 このサービスにサブミットするメッセージごとに、対象者は通知を受け取ります。 | [{{site.data.keyword.mobilepushshort}} によって生成されるイベント](/docs/services/mobilepush?topic=mobile-pushnotification-push_activity_tracker#push_activity_tracker) |  
{: caption="イベントを {{site.data.keyword.cloudaccesstrailshort}} に送信する Web クラウド・サービスおよびモバイル・クラウド・サービスのリスト" caption-side="top"} 



## プラットフォーム統合セキュリティー・サービス
{: #platform_integrated_security}

統合セキュリティー・サービスは、{{site.data.keyword.cloudaccesstrailshort}} **アカウント・ドメイン**を通して表示できる、{{site.data.keyword.cloudaccesstrailshort}} イベントを生成します。


以下の表に、イベントを {{site.data.keyword.cloudaccesstrailshort}} に送信するコア・セキュリティー・プラットフォーム・サービスをリストします。

| サービス     | 説明 | {{site.data.keyword.cloudaccesstrailshort}} イベント |
|-------------|-------------|-------------|
| [{{site.data.keyword.cloud_notm}} へのログイン](/docs/iam?topic=iam-iamoverview#iamoverview)| パスワード、API キー、許可コード、またはパスコードを使用して、{{site.data.keyword.cloud_notm}} にログインできます。 フェデレーテッド・ユーザーとして、ワンタイム・パスコードまたは API キーを使用してコマンド・ライン・インターフェース (CLI) からログインできます。 | [ユーザーまたはアプリが {{site.data.keyword.cloud_notm}} にログインしたときに生成されるイベント](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_login) |
| [アカウント・ユーザーの Cloud Foundry アクセス権限の管理](/docs/iam?topic=iam-mngcf#mngcf) | アカウント内のユーザーに対して、Cloud Foundry (CF) 許可の付与、取り消し、および更新を行うことができます。 | [アカウント内の CF 役割の管理時に生成されるイベント](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-cf#cf_cfroles) |
| [{{site.data.keyword.iamlong}} (IAM)](/docs/iam?topic=iam-userroles#userroles) | IAM を使用して、{{site.data.keyword.cloud_notm}} プラットフォームおよびインフラストラクチャーのサービス全体でユーザーおよび役割を管理することができます。 | [IAM ポリシーの管理時に生成されるイベント](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_policies) |
| [プラットフォーム API キーの管理](/docs/iam?topic=iam-manapikey#platform-api-keys) | {{site.data.keyword.IBM_notm}} Cloud 内で、ユーザーまたはサービス ID に関連付けられたプラットフォーム API キーを定義できます。 | [プラットフォーム API キーの管理時に生成されるイベント](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_apikeys) |
| [サービス ID の管理](/docs/iam?topic=iam-serviceids#serviceids) | {{site.data.keyword.IBM_notm}} Cloud 内で、アカウント・レベルでサービス ID を定義できます。 | [サービス ID の管理時に生成されるイベント](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_serviceids) |
| [アクセス・グループの管理](/docs/iam?topic=iam-groups#groups) | 許可の割り当てを簡単に行うことができるように、アクセス・グループを定義して、ユーザーとサービス ID のセットを単一のエンティティーに編成することができます。 | [アクセス・グループの管理時に生成されるイベント](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_access) |
{: caption="コア・セキュリティー・プラットフォーム・サービスのリスト" caption-side="top"} 


## プラットフォーム統合サービス
{: #integration}

以下の表に、イベントを {{site.data.keyword.cloudaccesstrailshort}} に送信する統合サービスをリストします。

| サービス     | 説明 | {{site.data.keyword.cloudaccesstrailshort}} イベント |
|-------------|-------------|-------------|
| [{{site.data.keyword.messagehub}}](/docs/services/EventStreams?topic=eventstreams-about#about)| {{site.data.keyword.messagehub}} は、Apache Kafka で構築されている高スループットのメッセージ・バスです。 これは、{{site.data.keyword.IBM_notm}} へのイベントの取り込みのため、および、お客様のサービスおよびアプリケーション間でイベント・ストリームを分散させるために最適化されています。 | [{{site.data.keyword.messagehub}} によって生成されるイベント](/docs/services/EventStreams?topic=eventstreams-at_events#at_events) |  
{: caption="イベントを {{site.data.keyword.cloudaccesstrailshort}} に送信する統合クラウド・サービスのリスト" caption-side="top"} 



## プラットフォーム・ネットワーク・サービス
{: #network}

以下の表に、イベントを {{site.data.keyword.cloudaccesstrailshort}} に送信するネットワーク・クラウド・サービスをリストします。

| サービス     | 説明 | {{site.data.keyword.cloudaccesstrailshort}} イベント |
|-------------|-------------|-------------|
| [IBM Cloud Internet Services (CIS)](/docs/infrastructure/cis?topic=cis-about-ibm-cloud-internet-services-cis#about-ibm-cloud-internet-services-cis)| IBM Cloud Internet Services (CIS) は、高速、高パフォーマンスの、信頼できる安全なインターネット・サービスを提供します。 | [IBM Cloud Internet Services によって生成されるイベント](/docs/infrastructure/cis?topic=cis-at_events#at_events) |  
{: caption="イベントを {{site.data.keyword.cloudaccesstrailshort}} に送信するネットワーク・クラウド・サービスのリスト" caption-side="top"} 



## プラットフォーム・セキュリティー・サービス
{: #security}

以下の表に、イベントを {{site.data.keyword.cloudaccesstrailshort}} に送信するセキュリティー・クラウド・サービスをリストします。


| サービス     | 説明 | {{site.data.keyword.cloudaccesstrailshort}} イベント |
|-------------|-------------|-------------|
| [{{site.data.keyword.cloudaccesstraillong_notm}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov)| {{site.data.keyword.cloudaccesstrailshort}} サービスを使用して、{{site.data.keyword.cloudaccesstraillong_notm}} をモニターできます。 | [{{site.data.keyword.cloudaccesstraillong_notm}} サービスによって生成されるイベント](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-downloading_events#events) |  
| [{{site.data.keyword.appid_full_notm}}](/docs/services/appid?topic=appid-about#about) | {{site.data.keyword.appid_short}} を使用して、モバイル・アプリおよび Web アプリに認証を追加したり、 バックエンド・リソースを保護したりできます。 | [{{site.data.keyword.appid_short}} サービスによって生成されるイベント](/docs/services/appid?topic=appid-at-events#at-events) |
| [{{site.data.keyword.cloudcerts_full_notm}}](/docs/services/certificate-manager?topic=certificate-manager-about-certificate-manager#about-certificate-manager) | {{site.data.keyword.cloudcerts_short}} を使用して、{{site.data.keyword.cloud_notm}} ベースのアプリおよびサービス用に SSL 証明書を管理できます。  | [{{site.data.keyword.cloudcerts_short}} サービスによって生成されるイベント](/docs/services/certificate-manager?topic=certificate-manager-at_events#at_events) |
| [{{site.data.keyword.keymanagementservicelong}}](/docs/services/key-protect?topic=key-protect-getting-started-tutorial#getting-started-with-key-protect) | {{site.data.keyword.keymanagementserviceshort}} サービスを使用して、{{site.data.keyword.cloud_notm}} 全体でアプリの暗号化鍵をプロビジョンできます。 | [{{site.data.keyword.keymanagementserviceshort}} サービスによって生成されるイベント](/docs/services/key-protect?topic=key-protect-activity-tracker-events#activity-tracker-events) |
| [{{site.data.keyword.security-advisor_short}}](/docs/services/security-advisor?topic=security-advisor-about#about) | {{site.data.keyword.security-advisor_short}} を利用して、{{site.data.keyword.cloud_notm}} アプリおよびワークロードのセキュリティーをモニターできます。   | [{{site.data.keyword.security-advisor_short}} サービスによって生成されるイベント](/docs/services/security-advisor?topic=security-advisor-at_events#at_events) |
{: caption="イベントを {{site.data.keyword.cloudaccesstrailshort}} に送信するセキュリティー・クラウド・サービスのリスト" caption-side="top"} 


## プラットフォーム・ストレージ・サービス
{: #storage}

以下の表に、イベントを {{site.data.keyword.cloudaccesstrailshort}} に送信するストレージ・クラウド・サービスをリストします。

| サービス     | 説明 | {{site.data.keyword.cloudaccesstrailshort}} イベント |
|-------------|-------------|-------------|
| [{{site.data.keyword.cos_full_notm}}](/docs/services/cloud-object-storage?topic=cloud-object-storage-about#about-ibm-cloud-object-storage)| {{site.data.keyword.cos_full_notm}} を使用して、{{site.data.keyword.cloud_notm}} にデータを保管できます。 データは、暗号化され、複数の地理的ロケーションに分散され、REST API を使用して HTTP 経由でアクセスされます。   | [{{site.data.keyword.cos_full_notm}} によって生成されるイベント](/docs/services/cloud-object-storage?topic=cloud-object-storage-at-events) |  
{: caption="イベントを {{site.data.keyword.cloudaccesstrailshort}} に送信するストレージ・クラウド・サービスのリスト" caption-side="top"} 



## Watson プラットフォーム・データ・サービス
{: #watson_data}


| サービス     | 説明 | {{site.data.keyword.cloudaccesstrailshort}} イベント |
|-------------|-------------|-------------|
| [Watson Studio](https://dataplatform.cloud.ibm.com/docs/content/wsj/getting-started/overview-ws.html) | Watson Studio は、データを活用した協働によってビジネス課題を解決するための環境とツールを提供します。 データの分析と視覚化、データのクレンジングとモデル化、ストリーミング・データの取り込み、または、機械学習モデルの作成、トレーニング、およびデプロイを行うために必要なツールを選択できます。 | [Watson Studio によって生成されるイベント](https://dataplatform.cloud.ibm.com/docs/content/wsj/admin/at-events.html#ws) |  
| [Watson Machine Learning](https://dataplatform.cloud.ibm.com/docs/content/wsj/analyze-data/ml-overview.html)| Watson Machine Learning を使用して、ユーザー独自のデータを使用してトレーニングされた高度な分析モデルを構築することができ、アプリケーションで使用するためにこれをデプロイできます。 | [Watson Machine Learning によって生成されるイベント](https://dataplatform.cloud.ibm.com/docs/content/wsj/admin/at-events.html#wml) | 
| [Watson Knowledge Catalog](https://dataplatform.cloud.ibm.com/docs/content/wsj/catalog/overview-wkc.html)| Watson Knowledge Catalog は、データ・ポリシー・フレームワークによってサポートされる、企業向けのセキュアなカタログ管理プラットフォームを提供します。 カタログは、データおよび知識を、それを使用する必要のある人と結び付けます。 データ・ポリシー・フレームワークは、データ・アクセスがお客様のビジネス・ルールに確実に準拠するようにします。 | [Watson Knowledge Catalog によって生成されるイベント](https://dataplatform.cloud.ibm.com/docs/content/wsj/admin/at-events.html#wkc) |  
{: caption="イベントを {{site.data.keyword.cloudaccesstrailshort}} に送信する Watson クラウド・データ・サービスのリスト" caption-side="top"} 

