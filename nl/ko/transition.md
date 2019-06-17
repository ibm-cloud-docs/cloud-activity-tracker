---

copyright:
  years: 2016, 2019
lastupdated: "2019-06-06"

keywords: IBM Cloud, Activity Tracker, migration

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


# {{site.data.keyword.at_full_notm}}로 상태 전이
{: #transition}

{{site.data.keyword.cloudaccesstrailfull}}는 2019년 5월 9일부터 더 이상 사용되지 않습니다. [자세히 보기](https://www.ibm.com/blogs/cloud-archive/2019/04/deprecating-ibm-cloud-activity-tracker/). 이 서비스는 {{site.data.keyword.at_full_notm}}로 대체됩니다. [자세히 보기](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started). {:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}}는 더 이상 사용되지 않습니다. 2019년 5월 9일을 기준으로 새 {{site.data.keyword.cloudaccesstrailshort}} 인스턴스를 프로비저닝할 수 없습니다. 기존 프리미엄 플랜 인스턴스는 2019년 9월 30일까지 지원됩니다. {{site.data.keyword.cloud_notm}} 계정의 활동을 계속 모니터하려면 [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started)의 인스턴스를 프로비저닝하십시오.
{: deprecated}


{{site.data.keyword.at_full_notm}}로 마이그레이션하려면 다음 단계를 완료하십시오. 

1. 장기간 검색을 수행하려면 {{site.data.keyword.cloudaccesstrailfull}}에 저장된 이벤트 사본을 저장하십시오. {{site.data.keyword.cloudaccesstrailshort}} CLI 또는 API를 사용할 수 있습니다. 

    레거시 {{site.data.keyword.cloudaccesstrailshort}} 인스턴스가 있는 각 Cloud Foundry 영역과 현재 모니터링 중인 각 지역에 있는 각 계정 도메인의 영역 이벤트를 저장하십시오.

    * [CLI를 사용하여 이벤트 다운로드](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-downloading_events)

    * [API를 사용하여 이벤트 다운로드](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-downloading_events_api)

2. [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-provision)을 프로비저닝하십시오.

    지역당 하나의 인스턴스만 프로비저닝할 수 있습니다. 
    
3. {{site.data.keyword.cloud_notm}}에서 권한을 관리할 액세스 그룹을 작성하고 구성하십시오. 

    * [사용자 또는 서비스 ID에 관리 권한 부여](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-iam_manage_events).

    * [사용자 또는 서비스 ID에 사용자 권한 부여](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-iam_view_events).

4. {{site.data.keyword.at_full_notm}}에서 보기와 대시보드를 정의하여 이벤트를 분석하고 관리하십시오. [자세히 보기](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-views). 

    Kibana 대시보드를 LogDNA 대시보드로 마이그레이션하는 작업은 자동으로 수행되지 않습니다. 새로운 대시보드를 수동으로 구현해야 합니다. 

    LogDNA에서 구현할 수 있는 시각화는 히스토그램과 파이(pie)뿐입니다.

5. [선택사항] {{site.data.keyword.at_full_notm}} 인스턴스에 맞게 아카이브를 구성하십시오. 

    {{site.data.keyword.cos_full_notm}}(COS)에 이벤트를 아카이브할 수 있습니다. [자세히 보기](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-archiving). 

    **참고:** 이벤트를 아카이브하는 데 사용하는 COS 인스턴스를 프로비저닝하고 아카이브된 이벤트를 유지보수할 책임이 있습니다. 

    이 단계는 유료 플랜이 있는 {{site.data.keyword.at_full_notm}} 인스턴스에만 필요합니다.

6. [경보](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-alerts)와 같은 기타 기능을 알아보십시오.


레거시 {{site.data.keyword.cloudaccesstrailshort}} 인스턴스를 통한 클라우드 활동의 모니터링을 중지할 준비가 되면 다음 단계를 완료하십시오.

1. {{site.data.keyword.cloud_notm}} 콘솔에서 레거시 {{site.data.keyword.cloudaccesstrailshort}} 인스턴스를 삭제하십시오.
2. 이 레거시 인스턴스에 대해 작업할 사용자의 권한을 제거하십시오. 


