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


# IAM 이벤트
{: #at_events_iam}

보안 담당자, 감사자 또는 관리자는 {{site.data.keyword.cloudaccesstrailfull}} 서비스를 사용하여 사용자 및 애플리케이션과 {{site.data.keyword.Bluemix}}의 {{site.data.keyword.iamlong}}(IAM) 서비스가 어떻게 상호작용하는지 추적할 수 있습니다. 
{:shortdesc}

{{site.data.keyword.cloudaccesstrailshort}} 서비스는 {{site.data.keyword.cloud_notm}} 내 서비스의 상태를 변경하는, 사용자가 시작한 활동을 기록합니다. 자세한 정보는 [{{site.data.keyword.cloudaccesstrailshort}} 정보](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#activity_tracker_ov )를 참조하십시오.

사용자 조치에 대한 모니터링을 시작하려면 [{{site.data.keyword.cloudaccesstrailfull_notm}}](/docs/services/cloud-activity-tracker/index.html#getting-started-with-cla)의 내용을 참조하십시오. 

개시자는 사용자, 서비스 또는 애플리케이션일 수 있습니다.
{: tip}

## 액세스 그룹 이벤트 관리
{: #at_events_iam_access}

다음 표에는 이벤트를 생성하는 조치가 나열되어 있습니다.

|조치 |설명 |
|----------|---------|
| `iam-groups.group.create`   | 개시자가 액세스 그룹을 작성하면 이벤트가 생성됩니다. | 
| `iam-groups.group.read`     | 개시자가 액세스 그룹과 관련된 정보를 보면 이벤트가 생성됩니다. |
| `iam-groups.group.update`   | 개시자가 그룹 이름 또는 설명을 업데이트하면 이벤트가 생성됩니다. |
| `iam-groups.group.delete`   | 개시자가 액세스 그룹을 삭제하면 이벤트가 생성됩니다. |
| `iam-groups.member.add`     | 개시자가 액세스 그룹에 구성원을 추가하면 이벤트가 생성됩니다. |
| `iam-groups.member.delete`  | 개시자가 액세스 그룹에서 구성원을 제거하면 이벤트가 생성됩니다. |
| `iam-groups.member.read`    | 개시자가 구성원의 멤버십을 확인하면 이벤트가 생성됩니다. |
| `iam-groups.rule.read`      | 개시자가 액세스 그룹 내의 규칙을 보면 이벤트가 생성됩니다. |
| `iam-groups.rule.create`    | 개시자가 액세스 그룹에 규칙을 추가하면 이벤트가 생성됩니다. |
| `iam-groups.rule.update`    | 개시자가 규칙 이름을 수정하면 이벤트가 생성됩니다. |
| `iam-groups.rule.delete`    | 개시자가 액세스 그룹에서 규칙을 삭제하면 이벤트가 생성됩니다. |
{: caption="표 1. 액세스 그룹 관리 조치" caption-side="top"} 



## 서비스 ID 이벤트에 대한 작업 수행
{: #at_events_iam_serviceids}

다음 표에는 이벤트를 생성하는 조치가 나열되어 있습니다.

|조치 |설명 |
|----------|---------|
| `iam-identity.account-serviceid.create` | 개시자가 서비스 ID를 작성하면 이벤트가 생성됩니다.  | 
| `iam-identity.account-serviceid.update` | 개시자가 서비스 ID의 이름을 바꾸거나 해당 설명을 수정하면 이벤트가 생성됩니다. | 
| `iam-identity.account-serviceid.delete` | 개시자가 서비스 ID를 삭제하면 이벤트가 생성됩니다. | 
{: caption="표 2. 서비스 ID에 대한 작업 수행 조치" caption-side="top"} 


## API 키에 대한 작업 수행
{: #at_events_iam_apikeys}

다음 표에는 이벤트를 생성하는 조치가 나열되어 있습니다.

|조치 |설명 |
|----------|---------|
| `iam-identity.user-apikey.create`      | 개시자가 API 키를 작성하면 이벤트가 생성됩니다. | 
| `iam-identity.user-apikey.update`      | 개시자가 API 키의 이름을 바꾸거나 해당 설명을 수정하면 이벤트가 생성됩니다. |  
| `iam-identity.user-apikey.delete`      | 개시자가 API 키를 삭제하면 이벤트가 생성됩니다. |  
| `iam-identity.serviceid-apikey.create` | 개시자가 서비스 ID에 대한 API 키를 작성하면 이벤트가 생성됩니다. |  
| `iam-identity.serviceid-apikey.delete` | 개시자가 서비스 ID에 대한 API 키를 삭제하면 이벤트가 생성됩니다. |  
{: caption="표 3. API 키에 대한 작업 수행 조치" caption-side="top"} 


## 로그인 이벤트
{: #at_events_iam_login}

다음 표에는 이벤트를 생성하는 조치가 나열되어 있습니다.

|조치 |설명 |
|----------|---------|
| `iam-identity.user-apikey.login`         |사용자가 API 키를 사용하여 {{site.data.keyword.cloud_notm}}에 로그인하면 이벤트가 생성됩니다. |  
| `iam-identity.serviceid-apikey.login`    |개시자가 서비스 ID와 연관된 API 키를 사용하여 {{site.data.keyword.cloud_notm}}에 로그인하면 이벤트가 생성됩니다. |  
| `iam-identity.user-identitycookie.login` | 이는 개시자가 조치를 실행하기 위해 새 식별 쿠키를 요청하면 생성되는 이벤트입니다. |
| `iam-identity.user-refreshtoken.login`   | 이는 개시자가 IBM Cloud에 로그인하거나, 이미 IBM Cloud에 로그인한 개시자가 조치를 실행하기 위해 새 새로 고치기 토큰을 요청하면 생성되는 이벤트입니다. |
{: caption="표 4. 사용자 로그인 조치" caption-side="top"} 


## 정책 이벤트 관리
{: #at_events_iam_policies}

다음 표에는 이벤트를 생성하는 조치가 나열되어 있습니다.

|조치 |설명 |
|----------|---------|
| `iam-am.policy.create` | 개시자가 사용자 또는 액세스 그룹에 정책을 추가하면 이벤트가 생성됩니다. |
| `iam-am.policy.delete` | 개시자가 사용자 또는 액세스 그룹의 정책에 대한 권한을 수정하면 이벤트가 생성됩니다.|
| `iam-am.policy.update` | 개시자가 사용자 또는 액세스 그룹에 지정된 정책을 삭제하면 이벤트가 생성됩니다. |
{: caption="표 5. 정책 조치 관리" caption-side="top"} 


## 이벤트 보기
{: #at_events_iam_ui}

{{site.data.keyword.cloudaccesstrailshort}} 이벤트는 **미국 남부** 지역의 **계정 도메인**에 있습니다.

이러한 이벤트를 보려면 **미국 남부** 지역에 {{site.data.keyword.cloudaccesstrailshort}} 서비스의 인스턴스를 프로비저닝해야 합니다. 이벤트를 보려면 그 후 {{site.data.keyword.cloudaccesstrailshort}} UI를 열고 계정 도메인으로 변경해야 합니다. 자세한 정보는 [계정 이벤트 보기](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/viewing_events.html#account_events)를 참조하십시오.

