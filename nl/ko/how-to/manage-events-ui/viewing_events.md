---

copyright:
  years: 2016, 2019
lastupdated: "2019-01-23"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}



# 이벤트 보기
{: #view_acc_events}

Kibana를 통해 또는 {{site.data.keyword.cloud_notm}} 콘솔에 있는 {{site.data.keyword.cloudaccesstrailshort}} UI를 통해 이벤트를 볼 수 있습니다.
{:shortdesc}
   

## 계정 이벤트 보기
{: #view_acc_events_account_events}

{{site.data.keyword.cloudaccesstrailshort}} UI 또는 Kibana를 통해 {{site.data.keyword.cloudaccesstrailshort}} 계정 도메인의 이벤트를 볼 수 있습니다.

**계정 소유자**에게는 {{site.data.keyword.cloudaccesstrailshort}} UI 또는 Kibana를 통해 {{site.data.keyword.cloudaccesstrailshort}} 계정 도메인의 이벤트를 볼 수 있는 권한이 있습니다.

**계정의 구성원**은 지역 내 계정 이벤트를 보려는 경우 다음 정보를 고려해야 합니다.

* {{site.data.keyword.cloudaccesstrailshort}}이 프로비저닝된 영역의 *개발자* 역할을 갖고 있어야 합니다. 자세한 정보는 [CF 역할 부여](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_cf_role)를 참조하십시오.

* 해당 지역의 *뷰어* 역할이 있는 {{site.data.keyword.loganalysisshort}} 서비스에 대한 IAM 정책이 있어야 합니다. 뷰어 역할은 필요한 최소 IAM 역할입니다. 자세한 정보는 [IAM 권한 부여](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_iam_policy)를 참조하십시오.

* Kibana를 통해 이벤트를 볼 수 있습니다. Kibana를 실행하는 방법에 대한 자세한 정보는 [웹 브라우저에서 Kibana로 이동](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_kibana.html#launch_Kibana_from_browser)을 참조하십시오.



## 영역 이벤트 보기
{: #view_acc_events_space_events}

{{site.data.keyword.cloudaccesstrailshort}} UI를 통해 {{site.data.keyword.cloudaccesstrailshort}} 영역 도메인의 이벤트를 볼 수 있습니다. 프리미엄 플랜이 있는 경우에는 Kibana를 통해서도 이러한 이벤트를 볼 수 있습니다.

**계정 소유자**는 모든 {{site.data.keyword.cloudaccesstrailshort}} 영역 도메인의 이벤트를 볼 수 있는 권한이 있습니다.

**계정의 구성원**은 {{site.data.keyword.cloudaccesstrailshort}}가 프로비저닝된 영역의 *개발자* 역할을 갖고 있어야 합니다.


