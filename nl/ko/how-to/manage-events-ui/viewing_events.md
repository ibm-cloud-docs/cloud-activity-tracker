---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, view events, UI

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

# 이벤트 보기
{: #view_acc_events}

Kibana를 통해 또는 {{site.data.keyword.cloud_notm}} 콘솔에 있는 {{site.data.keyword.cloudaccesstrailshort}} UI를 통해 이벤트를 볼 수 있습니다.
{:shortdesc}
   
{{site.data.keyword.cloudaccesstrailfull}}는 더 이상 사용되지 않습니다. 2019년 5월 9일을 기준으로 새 {{site.data.keyword.cloudaccesstrailshort}} 인스턴스를 프로비저닝할 수 없습니다. 기존 프리미엄 플랜 인스턴스는 2019년 9월 30일까지 지원됩니다. {{site.data.keyword.cloud_notm}} 계정의 활동을 계속 모니터하려면 [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started)의 인스턴스를 프로비저닝하십시오.
{: deprecated}


## 계정 이벤트 보기
{: #view_acc_events_account_events}

{{site.data.keyword.cloudaccesstrailshort}} UI 또는 Kibana를 통해 {{site.data.keyword.cloudaccesstrailshort}} 계정 도메인의 이벤트를 볼 수 있습니다.

**계정 소유자**에게는 {{site.data.keyword.cloudaccesstrailshort}} UI 또는 Kibana를 통해 {{site.data.keyword.cloudaccesstrailshort}} 계정 도메인의 이벤트를 볼 수 있는 권한이 있습니다.

**계정의 구성원**은 지역 내 계정 이벤트를 보려는 경우 다음 정보를 고려해야 합니다.

* {{site.data.keyword.cloudaccesstrailshort}}이 프로비저닝된 영역의 *개발자* 역할을 갖고 있어야 합니다. 자세한 정보는 [CF 역할 부여](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-grant_permissions#grant_cf_role)를 참조하십시오.

* 해당 지역의 *뷰어* 역할이 있는 {{site.data.keyword.loganalysisshort}} 서비스에 대한 IAM 정책이 있어야 합니다. 뷰어 역할은 필요한 최소 IAM 역할입니다. 자세한 정보는 [IAM 권한 부여](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-grant_permissions#grant_iam_policy)를 참조하십시오.

* Kibana를 통해 이벤트를 볼 수 있습니다. Kibana를 실행하는 방법에 대한 자세한 정보는 [웹 브라우저에서 Kibana로 이동](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-launch_kibana#launch_Kibana_from_browser)을 참조하십시오.



## 영역 이벤트 보기
{: #view_acc_events_space_events}

{{site.data.keyword.cloudaccesstrailshort}} UI를 통해 {{site.data.keyword.cloudaccesstrailshort}} 영역 도메인의 이벤트를 볼 수 있습니다. 프리미엄 플랜이 있는 경우에는 Kibana를 통해서도 이러한 이벤트를 볼 수 있습니다.

**계정 소유자**는 모든 {{site.data.keyword.cloudaccesstrailshort}} 영역 도메인의 이벤트를 볼 수 있는 권한이 있습니다.

**계정의 구성원**은 {{site.data.keyword.cloudaccesstrailshort}}가 프로비저닝된 영역의 *개발자* 역할을 갖고 있어야 합니다.


