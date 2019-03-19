---

copyright:
  years: 2016, 2019
lastupdated: "2019-01-23"

---


{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# コンプライアンス
{: #compliance}

[{{site.data.keyword.Bluemix}} は、IBM の厳しいセキュリティー規格に準拠したクラウド・プラットフォームおよびサービスを提供します](/docs/security/compliance.html#compliance)。 {{site.data.keyword.cloudaccesstraillong}} サービスは、{{site.data.keyword.cloud_notm}} 向けに作成された DevOps サービスです。 
{:shortdesc}


## 一般データ保護規則

一般データ保護規則 (GDPR) は、EU 全域における統一されたデータ保護の法的枠組みを作成しようとするものであり、個人データの管理権限を市民の手に取り戻すことを目的とし、世界のどこであろうと個人データをホスティングおよび「処理」するものに対して厳格な規則を課します。 また、この規則では、EU 域内と域外における個人データの自由な移動に関するルールが導入されます。 

**特記事項:** {{site.data.keyword.cloudaccesstrailshort}} サービスは、{{site.data.keyword.cloud_notm}} 内でお客様のアカウントで実行されているクラウド・リソースからのイベント・レコードを保管および表示します。 {{site.data.keyword.cloudaccesstrailshort}} に保管されるイベント項目のどれにも個人情報 (PI) が含まれていてはなりません。なぜなら、このデータは、お客様の社内の他のユーザーからアクセス可能であり、このクラウド・サービスをサポートできるように {{site.data.keyword.IBM_notm}} からもアクセス可能であるためです。

### 地域
{: #compliance_regions}

{{site.data.keyword.cloudaccesstrailshort}} サービスは、このサービスが使用可能な {{site.data.keyword.cloud_notm}} Public 地域では GDPR に準拠しています。


### データ保存
{: #compliance_data_retention}

{{site.data.keyword.cloudaccesstrailshort}} サービスには、イベント・データが保管される以下の 2 つのデータ・リポジトリーが組み込まれています。 

* Kibana を介してイベント・データを分析に使用できるリポジトリー。 標準プランまたはライト・プランの場合、データはこのリポジトリーにのみ保管されます。 データは 3 日間保持されます。
* プレミアム・プランの場合にイベント・データをホストする長期保管リポジトリー。 イベント・データは、保存ポリシーを構成するか、または手動で削除するまで保管されます。 デフォルトでは、イベントは無期限に保存されます。


### データ削除
{: #compliance_data_deletion}

以下の事項を考慮してください。

* Kibana 用のデータを提供するリポジトリーに保管されたイベントは、3 日後に削除されます。

* 長期保管リポジトリーに保管されたイベントは、手動で削除したときに削除されるか、または、保存ポリシーが構成されている場合は一定の日数後に削除されます。 



有料プランから標準プランまたはライト・プランに変更すると、長期保管リポジトリー内のイベントは約 1 日後に削除されます。

いつでも、サポート・チケットをオープンし、すべてのデータを削除するよう依頼できます。 IBM サポート・チケットのオープンについて詳しくは、[サポートへのお問い合わせ](/docs/get-support/howtogetsupport.html#getting-customer-support)を参照してください。



### 詳しい情報
{: #compliance_info}

詳しくは、以下を参照してください。

[{{site.data.keyword.cloud_notm}} セキュリティー・コンプライアンス](/docs/security/compliance.html#compliance)

[GDPR - {{site.data.keyword.IBM_notm}} 公式ページ](https://www.ibm.com/data-responsibility/gdpr/)



