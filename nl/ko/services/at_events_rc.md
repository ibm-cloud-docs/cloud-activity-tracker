---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, resource controller events

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

# 서비스 인스턴스 이벤트  
{: #at_events_rc}

보안 담당자, 감사자 또는 관리자는 {{site.data.keyword.cloudaccesstrailfull}} 서비스를 사용하여 사용자 및 애플리케이션과 {{site.data.keyword.cloud_notm}} 서비스가 어떻게 상호작용하는지 추적할 수 있습니다. 
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}}는 더 이상 사용되지 않습니다. 2019년 5월 9일을 기준으로 새 {{site.data.keyword.cloudaccesstrailshort}} 인스턴스를 프로비저닝할 수 없습니다. 기존 프리미엄 플랜 인스턴스는 2019년 9월 30일까지 지원됩니다. {{site.data.keyword.cloud_notm}} 계정의 활동을 계속 모니터하려면 [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started)의 인스턴스를 프로비저닝하십시오.
{: deprecated}

{{site.data.keyword.cloudaccesstrailfull_notm}} 서비스는 {{site.data.keyword.cloud_notm}} 내 서비스의 상태를 변경하는, 사용자가 시작한 활동을 기록합니다. 자세한 정보는 [{{site.data.keyword.cloudaccesstrailshort}} 정보](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov)를 참조하십시오.

사용자 조치에 대한 모니터링을 시작하려면 [{{site.data.keyword.cloudaccesstrailfull_notm}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started)의 내용을 참조하십시오. 


## 서비스 인스턴스 프로비저닝 및 관리에 대한 이벤트
{: #at_events_rc_provision}

다음 표에는 호출될 때 이벤트를 생성하는 API 메소드가 나열되어 있습니다.

<table>
  <caption>이벤트를 생성하는 조치</caption>
  <tr>
    <th>조치</th>
	  <th>설명</th>
  </tr>
  <tr>
    <td><i>service_name</i>.instance.create</td>
	  <td>서비스 인스턴스를 프로비저닝하면 이벤트가 생성됩니다.</td>
  </tr>
  <tr>
    <td><i>service_name</i>.instance.update</td>
	  <td>서비스 인스턴스의 이름을 바꾸거나 서비스 플랜을 변경하면 이벤트가 생성됩니다.</td>
  </tr>
  <tr>
    <td><i>service_name</i>.instance.delete</td>
	  <td>서비스 인스턴스가 삭제되면 이벤트가 생성됩니다.</td>
  </tr>
</table>


##  서비스 인스턴스와 연관된 API 키의 관리에 대한 이벤트
{: #at_events_rc_keys}

다음 표에는 호출될 때 이벤트를 생성하는 API 메소드가 나열되어 있습니다.

<table>
  <caption>이벤트를 생성하는 조치</caption>
  <tr>
    <th>조치</th>
	  <th>설명</th>
  </tr>
  <tr>
    <td><i>service_name</i>.key.create</td>
	  <td>서비스 인스턴스 UI의 *서비스 인증 정보* 섹션을 통해 서비스 인스턴스에 대해 API 키가 생성되면 이벤트가 생성됩니다.</td>
  </tr>
  <tr>
    <td><i>service_name</i>.key.delete</td>
	  <td>서비스 인스턴스 UI의 *서비스 인증 정보* 섹션에서 서비스 인스턴스와 연관된 API 키가 삭제되면 이벤트가 생성됩니다.</td>
  </tr>
</table>

##  서비스 인스턴스의 앱 바인딩에 대한 이벤트
{: #at_events_rc_bind}

다음 표에는 호출될 때 이벤트를 생성하는 API 메소드가 나열되어 있습니다.

<table>
  <caption>이벤트를 생성하는 조치</caption>
  <tr>
    <th>조치</th>
	  <th>설명</th>
  </tr>
  <tr>
    <td><i>service_name</i>.binding.create</td>
	  <td>서비스 인스턴스를 애플리케이션에 바인드하면 이벤트가 생성됩니다.</td>
  </tr>
  <tr>
    <td><i>service_name</i>.binding.delete</td>
	  <td>서비스 인스턴스를 애플리케이션에서 바인드 해제하면 이벤트가 생성됩니다.</td>
  </tr>
</table>




## 이벤트를 찾을 위치
{: #at_events_rc_ui}

{{site.data.keyword.cloudaccesstrailshort}} 이벤트는 **미국 남부** 지역의 **계정 도메인**에 있습니다.

이러한 이벤트를 보려면 **미국 남부** 지역에 {{site.data.keyword.cloudaccesstrailshort}} 서비스의 인스턴스를 프로비저닝해야 합니다. 이벤트를 보려면 그 후 {{site.data.keyword.cloudaccesstrailshort}} UI를 열고 계정 도메인으로 변경해야 합니다. 

자세한 정보는 [계정 이벤트 보기](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-view_acc_events#view_acc_events_account_events)를 참조하십시오.



