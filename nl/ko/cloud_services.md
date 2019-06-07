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



# 클라우드 서비스
{: #cloud_services}

{{site.data.keyword.cloudaccesstraillong}} 서비스를 사용하여, {{site.data.keyword.IBM_notm}} 클라우드 내 다음 서비스의 상태를 변경하는, 사용자가 시작한 활동을 모니터하십시오.
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}}는 더 이상 사용되지 않습니다. 2019년 5월 9일을 기준으로 새 {{site.data.keyword.cloudaccesstrailshort}} 인스턴스를 프로비저닝할 수 없습니다. 기존 프리미엄 플랜 인스턴스는 2019년 9월 30일까지 지원됩니다. {{site.data.keyword.cloud_notm}} 계정의 활동을 계속 모니터하려면 [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started)의 인스턴스를 프로비저닝하십시오.
{: deprecated}

**참고:** {{site.data.keyword.cloud_notm}}에서 서비스가 사용 가능한 지역에 대한 정보를 가져오려면 [지역별 서비스](/docs/resources?topic=resources-services_region#services_region)를 참조하십시오.


## 인프라 서비스 컴퓨팅
{: #infrastructure}

**참고:** 사용자가 {{site.data.keyword.BluVirtServers_short}} 및 {{site.data.keyword.baremetal_short}} {{site.data.keyword.cloudaccesstrailshort}} 이벤트를 생성하려면 사용자에게 {{site.data.keyword.cloud_notm}} 콘솔의 인프라 리소스에 대한 액세스 권한이 있어야 합니다. 자세한 정보는 [{{site.data.keyword.cloudaccesstrailshort}}를 사용하여 {{site.data.keyword.BluVirtServers_short}} 및 {{site.data.keyword.baremetal_short}} 활동 모니터링](/docs/services/cloud-activity-tracker/tutorials?topic=cloud-activity-tracker-vsi#vsi)을 참조하십시오.

다음 표에는 {{site.data.keyword.cloudaccesstrailshort}}에 이벤트를 전송하는 인프라 서비스가 나열되어 있습니다.

|서비스     |설명 | {{site.data.keyword.cloudaccesstrailshort}} 이벤트 |
|-------------|-------------|-------------|
| [{{site.data.keyword.BluVirtServers_short}} ](/docs/vsi?topic=virtual-servers-about-virtual-servers#about-virtual-servers)| {{site.data.keyword.BluVirtServers}}는 전용 코어 및 메모리 할당을 포함하여 구매하는 확장 가능한 가상 서버입니다. 이미지 템플리트와 같은 기능에 액세스할 수 있으며 몇 분 안에 추가할 수 있는 컴퓨팅 리소스를 찾고 있는 경우 이는 훌륭한 선택사항입니다.  | [{{site.data.keyword.BluVirtServers_short}}에 의해 생성된 이벤트](/docs/vsi?topic=virtual-servers-at_events#at_events) |  
| [{{site.data.keyword.baremetal_long}} ](/docs/bare-metal?topic=bare-metal-about-bm#about-bm) | {{site.data.keyword.baremetal_short}}는 하드웨어 리소스에 대한 하위 레벨 액세스 권한과 함께 성능과 제어를 제공하는 실제 싱글 테넌트 서버입니다. | [{{site.data.keyword.baremetal_short}}에 의해 생성된 이벤트](/docs/bare-metal?topic=bare-metal-bm-at-events#bm-at-events) | 
{: caption="이벤트를 {{site.data.keyword.cloudaccesstrailshort}}에 전송하는 인프라 서비스의 목록" caption-side="top"} 




## 서버리스 서비스 컴퓨팅
{: #serverless}

다음 표에는 {{site.data.keyword.cloudaccesstrailshort}}에 이벤트를 전송하는 서버리스 컴퓨팅 서비스가 나열되어 있습니다.

|서비스     |설명 | {{site.data.keyword.cloudaccesstrailshort}} 이벤트 |
|-------------|-------------|-------------|
| [{{site.data.keyword.openwhisk_short}}](/docs/openwhisk?topic=cloud-functions-index#index) | {{site.data.keyword.openwhisk_short}}는 경량 `code called actions`를 작성하는 데 사용할 수 있는 Apache OpenWhisk를 기반으로 하며 여러 언어로 된 FaaS(Functions-as-a-Service) 프로그래밍 플랫폼입니다. | [{{site.data.keyword.openwhisk_short}}에 의해 생성된 이벤트](/docs/openwhisk?topic=cloud-functions-activity_tracker#activity_tracker) |
{: caption="{{site.data.keyword.cloudaccesstrailshort}}에 이벤트를 전송하는 서버리스 컴퓨팅 서비스 목록" caption-side="top"} 



## 플랫폼 컨테이너 서비스
{: #ikcs}

{{site.data.keyword.containershort_notm}}에서는 두 가지 유형의 {{site.data.keyword.cloudaccesstrailshort}} 이벤트를 생성합니다.

* **클러스터 관리 이벤트**
    
    * 이러한 이벤트는 자동으로 생성됩니다.
    * 이러한 이벤트는 자동으로 {{site.data.keyword.cloudaccesstrailshort}}에 전달됩니다.
    * 이러한 이벤트는 {{site.data.keyword.cloudaccesstrailshort}} **계정 도메인**을 통해 볼 수 있습니다. 

* **Kubernetes API 서버 감사 이벤트**

    * 이러한 이벤트는 자동으로 생성됩니다.
    * 사용자는 이러한 이벤트를 {{site.data.keyword.cloudaccesstrailshort}} 서비스로 전달하도록 클러스터를 구성해야 합니다.
    * 사용자는 이벤트를 {{site.data.keyword.cloudaccesstrailshort}} **계정 도메인** 또는 **영역 도메인**으로 전송하도록 구성할 수 있습니다. 자세한 정보는 [감사 로그 전송](/docs/containers?topic=containers-health#api_forward)을 참조하십시오.

다음 표에는 {{site.data.keyword.cloudaccesstrailshort}}에 이벤트를 전송하는 컨테이너 플랫폼 서비스가 나열되어 있습니다.

|서비스     |설명 | {{site.data.keyword.cloudaccesstrailshort}} 이벤트 |
|-------------|-------------|-------------|
| [{{site.data.keyword.containerlong_notm}}: 클러스터 관리 이벤트](/docs/containers?topic=containers-container_index#container_index)| 이러한 이벤트는 클러스터 작성, 삭제 또는 업데이트와 같은 조치에 대해 보고합니다. | [클러스터 관리 이벤트](/docs/containers?topic=containers-at_events#cluster-events) |  
| [{{site.data.keyword.containerlong_notm}}: API 서버 감사 이벤트](/docs/containers?topic=containers-container_index#container_index)| Kubernetes API 서버 감사 이벤트는 클러스터에 영향을 미치는 활동 시퀀스에 대한 시간 순서대로의 정보를 제공합니다. 각 조치는 이벤트를 생성합니다. | [Kubernetes API 서버 감사 이벤트](/docs/containers?topic=containers-at_events#kube-events) |
| [{{site.data.keyword.registrylong_notm}}](/docs/services/Registry?topic=registry-registry_overview#registry_overview) | {{site.data.keyword.registrylong_notm}} 서비스를 사용하여 확장 가능한 고가용성 아키텍처에서 개인용 Docker 이미지를 저장하고 액세스할 수 있습니다. | [{{site.data.keyword.registrylong_notm}}와 상호작용하면 생성되는 이벤트](/docs/services/Registry?topic=registry-at_events#at_events) | 
{: caption="컨테이너 이벤트" caption-side="top"} 



## 플랫폼 Cloud Foundry 애플리케이션
{: #platform_cfapps}

Cloud Foundry 애플리케이션에서 {{site.data.keyword.cloudaccesstrailshort}}에 전송된 이벤트는 `GET /v2/events`의 응답 영역에서 본문 섹션 아래에 나열됩니다. *유형* 필드에는 이벤트를 생성한 모든 조치가 나열됩니다. 자세한 정보는 [이벤트 API ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://apidocs.cloudfoundry.org/270/events/list_all_events.html){:new_window}를 참조하십시오.


## 플랫폼 코어 내장 서비스
{: #platform_core_integrated}

코어 플랫폼 서비스는 {{site.data.keyword.cloudaccesstrailshort}} **계정 도메인**을 통해 볼 수 있는 {{site.data.keyword.cloudaccesstrailshort}} 이벤트를 생성합니다.

다음 표에는 {{site.data.keyword.cloudaccesstrailshort}}에 이벤트를 전송하는 코어 플랫폼 서비스가 나열되어 있습니다.

|서비스     |설명 | {{site.data.keyword.cloudaccesstrailshort}} 이벤트 |
|-------------|-------------|-------------|
| [{{site.data.keyword.iamshort}}(IAM)에 의해 관리되는 리소스에 대한 카탈로그 서비스의 프로비저닝 및 관리](/docs/overview?topic=overview-ui#catalogcreate) | 사용자는 서비스 인스턴스를 프로비저닝하고, 서비스 인스턴스의 이름을 바꾸고, 서비스 인스턴스의 계획을 변경하고, 서비스 인스턴스를 제거할 수 있습니다. | [카탈로그 서비스와 상호작용하면 생성되는 이벤트](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_rc#at_events_rc) |  
| [Cloud Foundry 영역에 바인드되는 카탈로그 서비스의 프로비저닝 및 관리](/docs/overview?topic=overview-ui#catalogcreate)| 사용자는 서비스 인스턴스를 프로비저닝하고, 서비스 인스턴스의 이름을 바꾸고, 서비스 인스턴스의 계획을 변경하고, 서비스 인스턴스를 제거할 수 있습니다. </br>이러한 이벤트는 CF 영역에 프로비저닝된 서비스에 대해 생성됩니다. | [카탈로그 서비스와 상호작용하면 생성되는 이벤트](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-cf#cf_catalog) |  
| [계정 관리](/docs/account?topic=account-accounts#accounts) | 기존 IBM ID를 사용하거나, 새 IBM ID를 작성하거나, 연합 ID를 사용하여 {{site.data.keyword.IBM_notm}} 계정을 등록할 수 있습니다. | [계정을 관리하면 생성되는 이벤트](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_acc_mgt#at_events_acc_mgt_account) |
| [사용자 관리](/docs/iam?topic=iam-iamuserinv#iamusermanage) | 소유하거나 관리하는 계정 또는 조직의 사용자를 보고 관리할 수 있습니다.  | [사용자를 관리하면 생성되는 이벤트](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_acc_mgt#at_events_acc_mgt_users) |
| [조직 관리](/docs/account?topic=account-orgsspacesusers#orgsspacesusers) | 계정 소유자는 계정에 조직을 추가하고 관리할 수 있습니다. | [조직을 관리하면 생성되는 이벤트](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_acc_mgt#at_events_acc_mgt_org) |
{: caption="코어 플랫폼 조치의 목록" caption-side="top"} 


## 플랫폼 데이터베이스 서비스
{: #database}

다음 표에는 {{site.data.keyword.cloudaccesstrailshort}}에 이벤트를 전송하는 데이터베이스 서비스가 나열되어 있습니다.

|서비스     |설명 | {{site.data.keyword.cloudaccesstrailshort}} 이벤트 |
|-------------|-------------|----------------------------------------------------|
| [{{site.data.keyword.databases-for-postgresql_full_notm}}](/docs/services/databases-for-postgresql?topic=databases-for-postgresql-about#about) | {{site.data.keyword.databases-for-postgresql_full_notm}}은 {{site.data.keyword.cloud_notm}}에서 호스팅되고 다른 {{site.data.keyword.cloud_notm}} 서비스와 통합되는 관리 PostgreSQL 서비스입니다. | [{{site.data.keyword.databases-for-postgresql_full_notm}}에 의해 생성된 이벤트](/docs/services/databases-for-postgresql?topic=databases-for-postgresql-activity-tracker#activity-tracker) |
| [{{site.data.keyword.databases-for-redis_full_notm}}](/docs/services/databases-for-redis?topic=databases-for-redis-about#about-databases-for-redis) | {{site.data.keyword.databases-for-redis_full_notm}}는 {{site.data.keyword.cloud_notm}}에서 호스팅되고 다른 {{site.data.keyword.cloud_notm}} 서비스와 통합되는 관리 서비스입니다. | [{{site.data.keyword.databases-for-redis_full_notm}}에 의해 생성된 이벤트](/docs/services/databases-for-redis?topic=databases-for-redis-activity-tracker-integration#activity-tracker-integration) |
| [{{site.data.keyword.sqlquery_short}}](/docs/services/sql-query?topic=sql-query-overview#overview) | 사각형 데이터를 분석하거나, 변형하거나 정리하기 위해 {{site.data.keyword.sqlquery_short}} 서비스를 사용하여 SQL 조회(즉 SELECT문)를 실행할 수 있습니다. | [{{site.data.keyword.sqlquery_short}}에 의해 생성된 이벤트](/docs/services/sql-query?topic=sql-query-activitytracker#activity-tracker-events) |  
| [{{site.data.keyword.databases-for-etcd_full_notm}}](/docs/services/databases-for-etcd?topic=databases-for-etcd-about#about-databases-for-etcd) | {{site.data.keyword.databases-for-etcd_full_notm}}는 {{site.data.keyword.cloud_notm}}에서 호스팅되고 다른 {{site.data.keyword.cloud_notm}} 서비스와 통합되는 관리 etcd 서비스입니다. | [{{site.data.keyword.databases-for-etcd_full_notm}}에 의해 생성된 이벤트](/docs/services/databases-for-etcd?topic=databases-for-etcd-activity-tracker#activity-tracker-integration) |
| [{{site.data.keyword.databases-for-elasticsearch_full_notm}}](/docs/services/databases-for-elasticsearch?topic=databases-for-elasticsearch-about#about-databases-for-elasticsearch) | {{site.data.keyword.databases-for-elasticsearch_full_notm}}는 {{site.data.keyword.cloud_notm}}에서 호스팅되고 다른 {{site.data.keyword.cloud_notm}} 서비스와 통합되는 관리 Elasticsearch 서비스입니다. | [{{site.data.keyword.databases-for-elasticsearch_full_notm}}에 의해 생성된 이벤트](/docs/services/databases-for-elasticsearch?topic=databases-for-elasticsearch-activity-tracker#activity-tracker-integration) |
| [{{site.data.keyword.messages-for-rabbitmq_full_notm}}](/docs/services/messages-for-rabbitmq?topic=messages-for-rabbitmq-about#about-messages-for-rabbitmq)  | {{site.data.keyword.messages-for-rabbitmq_full_notm}}는 {{site.data.keyword.cloud_notm}}에서 호스팅되고 다른 {{site.data.keyword.cloud_notm}} 서비스와 통합되는 관리 RabbitMQ 서비스입니다.   | [{{site.data.keyword.messages-for-rabbitmq_full_notm}}에 의해 생성된 이벤트](/docs/services/messages-for-rabbitmq?topic=messages-for-rabbitmq-activity-tracker#activity-tracker-integration) |
{: caption="이벤트를 {{site.data.keyword.cloudaccesstrailshort}}에 전송하는 데이터베이스 서비스의 목록" caption-side="top"} 




## 플랫폼 개발자 도구
{: #devops}

다음 표에는 {{site.data.keyword.cloudaccesstrailshort}}에 이벤트를 전송하는 DevOps 서비스가 나열되어 있습니다.

|서비스     |설명 | {{site.data.keyword.cloudaccesstrailshort}} 이벤트 |
|-------------|-------------|-------------|
| [{{site.data.keyword.DRA_short}}](/docs/apps?topic=creating-apps-insights-overview) | {{site.data.keyword.DRA_short}}는 {{site.data.keyword.cloud_notm}} 오픈 도구 체인 카탈로그의 통합입니다. | [{{site.data.keyword.DRA_short}}에 의해 생성된 이벤트](/docs/apps?topic=creating-apps-at_events) |
| [{{site.data.keyword.contdelivery_short}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-cd_overview#cd_overview) | {{site.data.keyword.contdelivery_short}}를 통해 DevOps 사례와 업계 최고의 도구를 사용하여 애플리케이션을 빌드하고 테스트하며 전달할 수 있습니다. | [{{site.data.keyword.contdelivery_short}}에 의해 생성된 이벤트](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-at_events#at_events) |
| [{{site.data.keyword.GlobalizationPipeline_short}}](/docs/services/GlobalizationPipeline?topic=GlobalizationPipeline-globalizationpipeline#globalizationpipeline) | 앱 개발자가 변환된 애플리케이션을 글로벌 고객에게 신속하게 릴리스할 수 있습니다. | [{{site.data.keyword.GlobalizationPipeline_short}}에 의해 생성된 이벤트](/docs/services/GlobalizationPipeline?topic=GlobalizationPipeline-gpat_events#gpat_events)|
{: caption="이벤트를 {{site.data.keyword.cloudaccesstrailshort}}에 전송하는 개발자 도구의 목록" caption-side="top"} 



## 플랫폼 내장 개발자 서비스
{: #integrated_dev_svcs}

다음 표에는 앱을 개발하고 이벤트를 {{site.data.keyword.cloudaccesstrailshort}}에 전송하는 데 사용할 수 있는 클라우드 서비스가 나열되어 있습니다.

|서비스     |설명 | {{site.data.keyword.cloudaccesstrailshort}} 이벤트 |
|-------------|-------------|-------------|
| [{{site.data.keyword.dev_console}}](/docs/apps?topic=creating-apps-tutorial-getting-started#create) | {{site.data.keyword.cloud_notm}}에서는 엔터프라이즈 레벨의 모바일 및 웹 애플리케이션을 빌드하고 {{site.data.keyword.cloud_notm}}에서 호스팅하는 클라우드 확장기능을 이용할 수 있습니다. {{site.data.keyword.cloud_notm}} 콘솔 및 명령행 도구를 사용하여 앱을 빌드하고 실행하고 배치할 수 있습니다. 스타터 킷을 사용하여 {{site.data.keyword.dev_console}}을 사용해 앱을 작성할 수 있습니다. | [{{site.data.keyword.dev_console}}에 의해 생성된 이벤트](/docs/apps?topic=creating-apps-at_events#at_events) |
| [{{site.data.keyword.mobilepushshort}}](/docs/services/mobilepush?topic=mobile-pushnotification-overview-push#overview-push)| {{site.data.keyword.mobilepushshort}} 서비스를 사용하여 모바일 디바이스 및 브라우저에 알림을 전송할 수 있습니다. 알림은 모든 애플리케이션 사용자를 대상으로 하거나, 태그를 사용하여 특정 사용자 및 디바이스 세트를 대상으로 할 수 있습니다. 서비스에 제출되는 모든 메시지에 대해, 의도된 대상이 알림을 수신합니다. | [{{site.data.keyword.mobilepushshort}}에 의해 생성된 이벤트](/docs/services/mobilepush?topic=mobile-pushnotification-push_activity_tracker#push_activity_tracker) |  
{: caption="{{site.data.keyword.cloudaccesstrailshort}}에 이벤트를 전송하는 웹 및 모바일 클라우드 서비스의 목록" caption-side="top"} 



## 플랫폼 내장 보안 서비스
{: #platform_integrated_security}

내장 보안 서비스는 {{site.data.keyword.cloudaccesstrailshort}} **계정 도메인**을 통해 볼 수 있는 {{site.data.keyword.cloudaccesstrailshort}} 이벤트를 생성합니다.


다음 표에는 {{site.data.keyword.cloudaccesstrailshort}}에 이벤트를 전송하는 코어 보안 플랫폼 서비스가 나열되어 있습니다.

|서비스     |설명 | {{site.data.keyword.cloudaccesstrailshort}} 이벤트 |
|-------------|-------------|-------------|
| [{{site.data.keyword.cloud_notm}}에 로그인](/docs/iam?topic=iam-iamoverview#iamoverview) |비밀번호, API 키, 권한 부여 코드 또는 패스코드를 사용하여 {{site.data.keyword.cloud_notm}}에 로그인할 수 있습니다. 연합된 사용자는 일회성 패스코드 또는 API 키를 사용하여 명령행 인터페이스(CLI)에서 로그인할 수 있습니다. | [사용자 또는 앱이 {{site.data.keyword.cloud_notm}}에 로그인하면 생성되는 이벤트](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_login) |
| [계정 사용자의 Cloud Foundry 액세스 권한 관리](/docs/iam?topic=iam-mngcf#mngcf) | 계정 내의 사용자에게 Cloud Foundry(CF) 권한을 부여하거나, 취소하거나, 이를 업데이트할 수 있습니다. | [계정에서 CF 역할을 관리하면 생성되는 이벤트](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-cf#cf_cfroles) |
| [{{site.data.keyword.iamlong}}(IAM)](/docs/iam?topic=iam-userroles#userroles) |IAM을 사용하여 {{site.data.keyword.cloud_notm}} 플랫폼 및 인프라 서비스의 사용자 및 역할을 관리할 수 있습니다. | [IAM 정책을 관리하면 생성되는 이벤트](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_policies) |
| [플랫폼 API 키 관리](/docs/iam?topic=iam-manapikey#platform-api-keys) | {{site.data.keyword.IBM_notm}} Cloud에 사용자 또는 서비스 ID와 연관된 플랫폼 API 키를 정의할 수 있습니다. | [플랫폼 API 키를 관리하면 생성되는 이벤트](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_apikeys) |
| [서비스 ID 관리](/docs/iam?topic=iam-serviceids#serviceids) | {{site.data.keyword.IBM_notm}} Cloud의 계정 레벨에서 서비스 ID를 정의할 수 있습니다. | [서비스를 관리하면 생성되는 이벤트](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_serviceids) |
| [액세스 그룹 관리](/docs/iam?topic=iam-groups#groups) | 액세스 그룹을 정의하여 사용자 및 서비스 ID 세트를 권한 지정이 더 용이한 단일 엔티티로 구성할 수 있습니다. | [액세스 그룹을 관리하면 생성되는 이벤트](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_access) |
{: caption="코어 보안 플랫폼 서비스의 목록" caption-side="top"} 


## 플랫폼 통합 서비스
{: #integration}

다음 표에는 {{site.data.keyword.cloudaccesstrailshort}}에 이벤트를 전송하는 통합 서비스가 나열되어 있습니다.

|서비스     |설명 | {{site.data.keyword.cloudaccesstrailshort}} 이벤트 |
|-------------|-------------|-------------|
| [{{site.data.keyword.messagehub}}](/docs/services/EventStreams?topic=eventstreams-about#about)| {{site.data.keyword.messagehub}}는 Apache Kafka로 빌드된, 처리량 높은 메시지 버스입니다. 이는 {{site.data.keyword.IBM_notm}}으로의 이벤트 수집, 그리고 서비스 및 애플리케이션 간의 이벤트 스트림 분배에 최적화되어 있습니다. | [{{site.data.keyword.messagehub}}에 의해 생성된 이벤트 ](/docs/services/EventStreams?topic=eventstreams-at_events#at_events) |  
{: caption="이벤트를 {{site.data.keyword.cloudaccesstrailshort}}에 전송하는 통합 클라우드 서비스의 목록" caption-side="top"} 



## 플랫폼 네트워크 서비스
{: #network}

다음 표에는 {{site.data.keyword.cloudaccesstrailshort}}에 이벤트를 전송하는 네트워크 클라우드 서비스가 나열되어 있습니다.

|서비스     |설명 | {{site.data.keyword.cloudaccesstrailshort}} 이벤트 |
|-------------|-------------|-------------|
| [IBM Cloud Internet Services(CIS)](/docs/infrastructure/cis?topic=cis-about-ibm-cloud-internet-services-cis#about-ibm-cloud-internet-services-cis)| IBM Cloud Internet Services(CIS)는 빠르고 고성능인 동시에 신뢰할 수 있는 안전한 인터넷 서비스를 제공합니다. | [IBM Cloud Internet Services에 의해 생성된 이벤트](/docs/infrastructure/cis?topic=cis-at_events#at_events) |  
{: caption="이벤트를 {{site.data.keyword.cloudaccesstrailshort}}에 전송하는 네트워크 클라우드 서비스의 목록" caption-side="top"} 



## 플랫폼 보안 서비스
{: #security}

다음 표에는 {{site.data.keyword.cloudaccesstrailshort}}에 이벤트를 전송하는 보안 클라우드 서비스가 나열되어 있습니다.


|서비스     |설명 | {{site.data.keyword.cloudaccesstrailshort}} 이벤트 |
|-------------|-------------|-------------|
| [{{site.data.keyword.cloudaccesstraillong_notm}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov)| {{site.data.keyword.cloudaccesstrailshort}} 서비스를 사용하여 {{site.data.keyword.cloudaccesstraillong_notm}}을 모니터할 수 있습니다. | [{{site.data.keyword.cloudaccesstraillong_notm}} 서비스에 의해 생성된 이벤트](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-downloading_events#events) |  
| [{{site.data.keyword.appid_full_notm}}](/docs/services/appid?topic=appid-about#about) | {{site.data.keyword.appid_short}}를 사용하여 모바일 및 앱에 인증을 추가하고 백엔드 리소스를 보호할 수 있습니다. | [{{site.data.keyword.appid_short}} 서비스에 의해 생성된 이벤트](/docs/services/appid?topic=appid-at-events#at-events) |
| [{{site.data.keyword.cloudcerts_full_notm}}](/docs/services/certificate-manager?topic=certificate-manager-about-certificate-manager#about-certificate-manager) | {{site.data.keyword.cloudcerts_short}}를 사용하여 {{site.data.keyword.cloud_notm}} 기반 앱 및 서비스의 SSL 인증서를 관리할 수 있습니다.  | [{{site.data.keyword.cloudcerts_short}} 서비스에 의해 생성된 이벤트](/docs/services/certificate-manager?topic=certificate-manager-at_events#at_events) |
| [{{site.data.keyword.keymanagementservicelong}}](/docs/services/key-protect?topic=key-protect-getting-started-tutorial#getting-started-with-key-protect) | {{site.data.keyword.keymanagementserviceshort}} 서비스를 사용하여 {{site.data.keyword.cloud_notm}}에서 앱에 대한 암호화된 키를 프로비저닝할 수 있습니다. | [{{site.data.keyword.keymanagementserviceshort}} 서비스에 의해 생성된 이벤트](/docs/services/key-protect?topic=key-protect-activity-tracker-events#activity-tracker-events) |
| [{{site.data.keyword.security-advisor_short}}](/docs/services/security-advisor?topic=security-advisor-about#about) ||{{site.data.keyword.security-advisor_short}}를 사용하여 {{site.data.keyword.cloud_notm}} 앱 및 워크로드의 보안을 모니터할 수 있습니다.   | [{{site.data.keyword.security-advisor_short}} 서비스에 의해 생성된 이벤트](/docs/services/security-advisor?topic=security-advisor-at_events#at_events) |
{: caption="이벤트를 {{site.data.keyword.cloudaccesstrailshort}}에 전송하는 보안 클라우드 서비스의 목록" caption-side="top"} 


## 플랫폼 스토리지 서비스
{: #storage}

다음 표에는 {{site.data.keyword.cloudaccesstrailshort}}에 이벤트를 전송하는 스토리지 클라우드 서비스가 나열되어 있습니다.

|서비스     |설명 | {{site.data.keyword.cloudaccesstrailshort}} 이벤트 |
|-------------|-------------|-------------|
| [{{site.data.keyword.cos_full_notm}}](/docs/services/cloud-object-storage?topic=cloud-object-storage-about#about-ibm-cloud-object-storage)| {{site.data.keyword.cos_full_notm}}를 사용하여 {{site.data.keyword.cloud_notm}}에 데이터를 저장할 수 있습니다. 데이터는 암호화되어 여러 지리적 위치에 분산되며, REST API를 사용하여 HTTP를 통해 액세스할 수 있습니다.   | [{{site.data.keyword.cos_full_notm}}에 의해 생성된 이벤트](/docs/services/cloud-object-storage?topic=cloud-object-storage-at-events) |  
{: caption="이벤트를 {{site.data.keyword.cloudaccesstrailshort}}에 전송하는 스토리지 클라우드 서비스의 목록" caption-side="top"} 



## Watson 플랫폼 데이터 서비스
{: #watson_data}


|서비스     |설명 | {{site.data.keyword.cloudaccesstrailshort}} 이벤트 |
|-------------|-------------|-------------|
| [Watson Studio](https://dataplatform.cloud.ibm.com/docs/content/wsj/getting-started/overview-ws.html) | Watson Studio는 데이터에 대한 협업을 통해 비즈니스 문제점을 해결하기 위한 환경 및 도구를 제공합니다. 사용자는 데이터를 분석하고 시각화하거나, 정리하고 모델화하거나, 스트리밍 데이터를 수집하는 데 필요한 도구, 또는 기계 학습 모델을 작성하고, 훈련하고, 배치하는 데 필요한 도구를 선택할 수 있습니다. | [Watson Studio에 의해 생성된 이벤트](https://dataplatform.cloud.ibm.com/docs/content/wsj/admin/at-events.html#ws) |  
| [Watson Machine Learning](https://dataplatform.cloud.ibm.com/docs/content/wsj/analyze-data/ml-overview.html)| Watson Machine Learning을 사용하여 애플리케이션에서 사용하기 위해 배치할 수 있는, 자신의 데이터로 훈련된 정교한 분석 모델을 빌드할 수 있습니다. | [Watson Machine Learning에 의해 생성된 이벤트](https://dataplatform.cloud.ibm.com/docs/content/wsj/admin/at-events.html#wml) | 
| [Watson Knowledge Catalog](https://dataplatform.cloud.ibm.com/docs/content/wsj/catalog/overview-wkc.html)| Watson Knowledge Catalog는 데이터 정책 프레임워크에서 지원하는 안전한 엔터프라이즈 카탈로그 관리 플랫폼을 제공합니다. 카탈로그는 데이터 및 지식을 이를 사용해야 하는 사용자와 연결합니다. 데이터 정책 프레임워크는 데이터 액세스가 비즈니스 규칙을 준수하여 이뤄지도록 합니다. | [Watson Knowledge Catalog에 의해 생성된 이벤트](https://dataplatform.cloud.ibm.com/docs/content/wsj/admin/at-events.html#wkc) |  
{: caption="이벤트를 {{site.data.keyword.cloudaccesstrailshort}}에 전송하는 Watson 클라우드 데이터 서비스의 목록" caption-side="top"} 

