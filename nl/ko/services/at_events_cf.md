---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, Cloud Foundry events, CF

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


# Cloud Foundry 이벤트
{: #cf}

{{site.data.keyword.Bluemix}}의 코어 플랫폼 서비스와의 상호작용을 추적하려면 {{site.data.keyword.cloudaccesstrailfull}} 서비스를 사용하십시오. 
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}}는 더 이상 사용되지 않습니다. 2019년 5월 9일을 기준으로 새 {{site.data.keyword.cloudaccesstrailshort}} 인스턴스를 프로비저닝할 수 없습니다. 기존 프리미엄 플랜 인스턴스는 2019년 9월 30일까지 지원됩니다. {{site.data.keyword.cloud_notm}} 계정의 활동을 계속 모니터하려면 [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started)의 인스턴스를 프로비저닝하십시오.
{: deprecated}

다음 목록에는 {{site.data.keyword.cloudaccesstrailshort}} 서비스에 이벤트를 전송하는 여러 코어 플랫폼 태스크가 간략하게 설명되어 있습니다. 

* 서비스 프로비저닝, 서비스 제거 및 서비스 이름 변경.
* 계정 내 사용자의 Cloud Foundry 영역 역할 부여, 업데이트 및 취소.
* 플랫폼 API 키 작성, 플랫폼 키 이름 바꾸기 및 플랫폼 키 삭제.


## 카탈로그 서비스와 상호작용하면 생성되는 이벤트
{: #cf_catalog}

서비스를 프로비저닝하고, 제거하고, 서비스의 이름을 변경하면 이벤트가 생성되어 계정 내에서 해당 서비스가 사용 가능한 Cloud Foundry 영역과 연관된 {{site.data.keyword.cloudaccesstrailshort}}의 영역 도메인에 전송됩니다. 

예를 들면, 미국 남부 지역의 영역 B에 서비스 A를 프로비저닝합니다. 이벤트가 생성됩니다. 이 이벤트를 보려면 미국 남부에서 해당 서비스를 프로비저닝한 영역과 동일한 영역에 {{site.data.keyword.cloudaccesstrailshort}} 서비스를 프로비저닝해야 합니다. 이렇게 하면 {{site.data.keyword.cloudaccesstrailshort}} 서비스 UI를 통해 해당 이벤트를 볼 수 있습니다.

다음 표에는 이벤트를 생성하는 카탈로그 조치가 나열되어 있습니다.

<table>
  <caption>카탈로그 조치</caption>
  <tr>
    <th>조치</th>
	  <th>설명</th>
  <tr>
  <tr>
    <td>`audit.service_instance.create`</td>
	<td>Cloud Foundry 영역에 서비스를 프로비저닝하면 이벤트가 작성됩니다.</td>
  </tr>
  <tr>
    <td>`audit.service_instance.update`</td>
	<td>Cloud Foundry 영역에서 사용 가능한 서비스의 이름을 변경하면 이벤트가 작성됩니다.</td>
  </tr>
  <tr>
    <td>`audit.service_instance.delete`</td>
	<td>계정 내의 Cloud Foundry 영역에서 서비스를 제거하면 이벤트가 작성됩니다.</td>
  </tr>
</table>


 	

## 계정 내의 Cloud Foundry 역할을 관리하면 생성되는 이벤트
{: #cf_cfroles} 

계정 내의 사용자에게 Cloud Foundry 역할을 부여하거나 취소(삭제)하면 이벤트가 생성되어 해당 역할이 부여되거나 취소되는 Cloud Foundry 영역과 연관된 {{site.data.keyword.cloudaccesstrailshort}}의 영역 도메인에 전송됩니다. 

예를 들면, 미국 남부 지역의 영역 B에서 사용자 A에게 *영역 관리자* 역할을 부여합니다. 이벤트가 생성됩니다. 이 이벤트를 보려면 미국 남부에서 사용자의 CF 권한을 관리하는 영역과 동일한 영역에 {{site.data.keyword.cloudaccesstrailshort}} 서비스를 프로비저닝해야 합니다. 이렇게 하면 {{site.data.keyword.cloudaccesstrailshort}} 서비스 UI를 통해 해당 이벤트를 볼 수 있습니다.


다음 표에는 사용자의 Cloud Foundry 역할을 관리할 때 {{site.data.keyword.cloudaccesstrailshort}} 이벤트를 생성하는 조치가 나열되어 있습니다.

<table>
  <caption>Cloud Foundry 역할 관리 조치</caption>
  <tr>
    <th>조치</th>
	<th>설명</th>
  <tr>
  <tr>
    <td>`audit.user.space_manager_add`</td>
	<td>Cloud Foundry 영역에서 사용자에게 *관리자* 역할을 부여합니다.</td>
  </tr>
  <tr>
    <td>`audit.user.space_developer_add`</td>
	<td>Cloud Foundry 영역에서 사용자에게 *개발자* 역할을 부여합니다.</td>
  </tr>
  <tr>
    <td>`audit.user.space_auditor_add`</td>
	<td>Cloud Foundry 영역에서 사용자에게 *감사* 역할을 부여합니다.</td>
  </tr>
  <tr>
    <td>`audit.user.space_manager_remove`</td>
	<td>Cloud Foundry 영역에서 사용자의 *관리자* 역할을 삭제합니다.</td>
  </tr>
  <tr>
    <td>`audit.user.space_developer_remove`</td>
	<td>Cloud Foundry 영역에서 사용자의 *개발자* 역할을 삭제합니다.</td>
  </tr>
  <tr>
    <td>`audit.user.space_auditor_remove`</td>
	<td>Cloud Foundry 영역에서 사용자의 *감사* 역할을 삭제합니다.</td>
  </tr>
</table>






	
 	
 	
