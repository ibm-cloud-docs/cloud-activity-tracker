---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, account events

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

# 계정 관리 이벤트  
{: #at_events_acc_mgt}

보안 담당자, 감사자 또는 관리자는 {{site.data.keyword.cloudaccesstrailfull}} 서비스를 사용하여 사용자 및 애플리케이션과 {{site.data.keyword.Bluemix}} 계정이 어떻게 상호작용하는지 추적할 수 있습니다. 
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull_notm}} 서비스는 {{site.data.keyword.cloud_notm}} 내 서비스의 상태를 변경하는, 사용자가 시작한 활동을 기록합니다. 자세한 정보는 [{{site.data.keyword.cloudaccesstrailshort}} 정보](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov)를 참조하십시오.

사용자 조치에 대한 모니터링을 시작하려면 [{{site.data.keyword.cloudaccesstrailfull_notm}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started-with-cla#getting-started-with-cla)의 내용을 참조하십시오. 



## 계정 관리에 대한 이벤트
{: #at_events_acc_mgt_account}

다음 표에는 호출될 때 이벤트를 생성하는 API 메소드가 나열되어 있습니다.

<table>
  <caption>이벤트를 생성하는 조치</caption>
  <tr>
    <th>조치</th>
	  <th>설명</th>
  </tr>
  <tr>
    <td>billing.account.create</td>
	  <td>계정에 계정 ID가 지정된 후 계정을 제공하면 이벤트가 생성됩니다.</td>
  </tr>
  <tr>
    <td>billing.account.update</td>
	  <td>계정에 대한 정보를 업데이트하면 이벤트가 생성됩니다.</td>
  </tr>
  <tr>
    <td>billing.account.active</td>
	  <td>계정을 확인하면 이벤트가 생성됩니다(즉, 계정이 활성 상태가 되면 이벤트가 생성됨).</td>
  </tr>
  <tr>
    <td>billing.account.subscription.create</td>
	  <td><a href="/docs/account?topic=account-accounts#subscription-account">구독 계정</a>을 작성하면 이벤트가 생성됩니다.</td>
  </tr>
</table>



## 사용자 관리에 대한 이벤트
{: #at_events_acc_mgt_users}

다음 표에는 호출될 때 이벤트를 생성하는 API 메소드가 나열되어 있습니다.

<table>
  <caption>이벤트를 생성하는 조치</caption>
  <tr>
    <th>조치</th>
	  <th>설명</th>
  </tr>
  <tr>
    <td>user-management.user.create</td>
	  <td>계정에 참여하도록 사용자에게 초대를 전송하면 이벤트가 생성됩니다. </br>계정 소유자는 계정에서 이 조치를 수행할 수 있는 유일한 사용자입니다.</td>
  </tr>
  <tr>
    <td>user-management.user.active</td>
	  <td>계정에서 사용자를 활성화하면 이벤트가 생성됩니다. </br>사용자가 자신의 이메일 주소를 확인하면 이벤트가 생성됩니다.</td>
  </tr>
  <tr>
    <td>user-management.account.user.delete</td>
	  <td>계정에서 사용자를 제거하면 이벤트가 생성됩니다. </br>계정 소유자는 계정에서 이 조치를 수행할 수 있는 유일한 사용자입니다.</td>
  </tr>
</table>

## 조직 관리에 대한 이벤트
{: #at_events_acc_mgt_org}

다음 표에는 호출될 때 이벤트를 생성하는 API 메소드가 나열되어 있습니다.

<table>
  <caption>이벤트를 생성하는 조치</caption>
  <tr>
    <th>조치</th>
	  <th>설명</th>
  </tr>
  <tr>
    <td>billing.account.org.create</td>
	  <td>계정에 조직을 추가하면 이벤트가 생성됩니다.</td>
  </tr>
</table>

## 이벤트를 찾을 위치
{: #at_events_acc_mgt_ui}

{{site.data.keyword.cloudaccesstrailshort}} 이벤트는 **미국 남부** 지역의 **계정 도메인**에 있습니다. 

이러한 이벤트를 보려면 **미국 남부** 지역에 {{site.data.keyword.cloudaccesstrailshort}} 서비스의 인스턴스를 프로비저닝해야 합니다. 이벤트를 보려면 그 후 {{site.data.keyword.cloudaccesstrailshort}} UI를 열고 계정 도메인으로 변경해야 합니다. 

자세한 정보는 [계정 이벤트 보기](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-view_acc_events#view_acc_events_account_events)를 참조하십시오.








