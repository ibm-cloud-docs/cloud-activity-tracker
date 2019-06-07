---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, news

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

# 새로운 기능
{: #whatsnew}

{{site.data.keyword.cloudaccesstrailshort}}에 대한 최신 기능과 통합에 대해 알아보십시오.
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}}는 더 이상 사용되지 않습니다. 2019년 5월 9일을 기준으로 새 {{site.data.keyword.cloudaccesstrailshort}} 인스턴스를 프로비저닝할 수 없습니다. 기존 프리미엄 플랜 인스턴스는 2019년 9월 30일까지 지원됩니다. {{site.data.keyword.cloud_notm}} 계정의 활동을 계속 모니터하려면 [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started)의 인스턴스를 프로비저닝하십시오.
{: deprecated}

{{site.data.keyword.cloudaccesstrailshort}}과 통합된 최신 서비스 목록을 보려면 [클라우드 서비스](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-cloud_services#cloud_services)를 참조하십시오.
{: important}


## 2019년 3월
{: #march2019}

* {{site.data.keyword.cloudaccesstrailshort}} CLI

Activity Tracker CLI에 대한 문제를 식별했습니다. 이 문제점을 해결하기 위해 CLI의 새 버전을 릴리스할 예정입니다.

명령행에서 `ibmcloud login`을 사용하여 {{site.data.keyword.cloud_notm}}에 로그인한 후 {{site.data.keyword.cloudaccesstrailshort}} 명령을 실행하면 실행하는 모든 {{site.data.keyword.cloudaccesstrailshort}} 명령에 대해 `Failed: Unauthorized` 오류가 발생합니다. 

그 동안 계속 CLI를 사용하여 작업하려면 다음 명령을 사용하여 {{site.data.keyword.cloud_notm}}에 로그인하십시오.

|지역 |명령 |
|--------|---------|
|`US South` |`bx login -a api.ng.bluemix.net -o OrgName -s SpaceName` |
|`EU DE`    |`bx login -a api.eu-de.bluemix.net -o OrgName -s SpaceName` |
|`EU DE`    |`bx login -a api.au-syd.bluemix.net -o OrgName -s SpaceName` |
{: caption="표 1. 명령" caption-side="top"} 

## 2019년 2월
{: #february2019}

* **{{site.data.keyword.cloudaccesstrailshort}}를 사용하여 {{site.data.keyword.GlobalizationPipeline_short}} 서비스를 모니터할 수 있습니다. **

    {{site.data.keyword.GlobalizationPipeline_short}}을 통해 애플리케이션 개발자가 변환된 애플리케이션을 글로벌 고객에게 신속하게 릴리스할 수 있습니다.

    {{site.data.keyword.cloudaccesstrailshort}} 이벤트에 대한 자세한 정보는 [{{site.data.keyword.GlobalizationPipeline_short}}에 의해 생성된 이벤트](/docs/services/GlobalizationPipeline?topic=GlobalizationPipeline-gpat_events#gpat_events)를 참조하십시오.








