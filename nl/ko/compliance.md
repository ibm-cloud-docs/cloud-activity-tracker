---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, compliance

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


# 규제 준수
{: #compliance}

[{{site.data.keyword.cloud_notm}}에서는 IBM의 엄격한 보안 표준을 준수하도록 빌드된 클라우드 플랫폼 및 서비스를 제공합니다](/docs/overview?topic=overview-security#compliance). {{site.data.keyword.cloudaccesstraillong}} 서비스는 {{site.data.keyword.cloud_notm}}를 위해 빌드된 DevOps 서비스입니다. 
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}}는 더 이상 사용되지 않습니다. 2019년 5월 9일을 기준으로 새 {{site.data.keyword.cloudaccesstrailshort}} 인스턴스를 프로비저닝할 수 없습니다. 기존 프리미엄 플랜 인스턴스는 2019년 9월 30일까지 지원됩니다. {{site.data.keyword.cloud_notm}} 계정의 활동을 계속 모니터하려면 [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started)의 인스턴스를 프로비저닝하십시오.
{: deprecated}

## 일반 개인정보 보호법률(General Data Protection Regulation)

일반 개인정보 보호법률(GDPR)은 EU 전역에 적용되는 균형 잡힌 데이터 보호 법률 프레임워크를 작성함으로써 시민들에게 자신의 개인 데이터를 제어할 수 있는 능력을 돌려줌과 동시에, 전 세계에서 이러한 데이터를 호스팅하고 처리하는 데 엄격한 규칙을 적용하는 것을 목표로 합니다. 이 법률은 또한 EU 내부 및 외부에서의 자유로운 개인 데이터 이동과 관련된 규칙을 도입합니다. 

**면책사항:** {{site.data.keyword.cloudaccesstrailshort}} 서비스는 {{site.data.keyword.cloud_notm}}의 사용자 계정에서 실행되는 클라우드 리소스의 이벤트 레코드를 저장하고 표시합니다. {{site.data.keyword.cloudaccesstrailshort}}에 저장되는 이벤트 항목은 엔터프라이즈 내의 다른 사용자가 액세스하거나 {{site.data.keyword.IBM_notm}}에서 클라우드 서비스를 지원하기 위해 액세스할 수 있으므로 이러한 항목은 개인 정보(PI)를 포함하지 않아야 합니다.

### 지역
{: #compliance_regions}

{{site.data.keyword.cloudaccesstrailshort}} 서비스는 이 서비스가 사용 가능한 {{site.data.keyword.cloud_notm}} Public 지역의 GDPR을 준수합니다.


### 데이터 보존
{: #compliance_data_retention}

{{site.data.keyword.cloudaccesstrailshort}} 서비스에는 이벤트 데이터가 저장되는 2개의 데이터 저장소가 포함되어 있습니다. 

* Kibana를 통한 분석에 사용 가능한 이벤트 데이터가 저장되는 저장소. 표준 또는 Lite 플랜에서는 이 저장소에만 데이터를 저장합니다. 데이터는 3일 간 보존됩니다.
* 프리미엄 플랜의 이벤트 데이터를 호스팅하는 장기 저장소. 이벤트 데이터는 사용자가 보존 정책을 구성하거나 이를 수동으로 삭제할 때까지 저장됩니다. 기본적으로 이벤트는 무기한으로 보존됩니다.


### 데이터 삭제
{: #compliance_data_deletion}

다음 정보를 고려하십시오.

* Kibana를 위한 데이터를 제공하는 저장소에 저장된 이벤트는 3일 후에 삭제됩니다.

* 장기 저장소에 저장된 이벤트는 보존 정책을 구성한 경우 특정 일 수가 지난 후, 또는 수동으로 삭제할 때 삭제됩니다. 



유료 플랜에서 표준 또는 Lite 플랜으로 변경하는 경우 장기 저장소에 저장된 이벤트는 1일 내에 삭제됩니다.

사용자는 언제든지 지원 티켓을 열어 모든 데이터를 삭제하도록 요청할 수 있습니다. IBM 지원 티켓을 여는 데 대한 정보는 [지원 받기](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support)를 참조하십시오.



### 자세한 정보
{: #compliance_info}

자세한 정보는 다음을 참조하십시오.

[{{site.data.keyword.cloud_notm}} 보안 규제 준수](/docs/overview?topic=overview-security#compliance)

[GDPR - {{site.data.keyword.IBM_notm}} 공식 페이지 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/data-responsibility/gdpr/){:new_window}



