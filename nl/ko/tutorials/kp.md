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


# {{site.data.keyword.cloudaccesstrailshort}}를 사용한 {{site.data.keyword.keymanagementserviceshort}} 활동 모니터링
{: #kp}

이 튜토리얼을 통해 {{site.data.keyword.cloudaccesstrailfull}} 서비스를 사용하여 사용자와 {{site.data.keyword.keymanagementserviceshort}} 서비스 간의 상호작용을 모니터하는 방법을 알아보십시오.
{:shortdesc}

이 튜토리얼의 목표는 다음과 같습니다.

1. {{site.data.keyword.cloudaccesstrailshort}} 서비스를 프로비저닝하는 방법을 보여줍니다.
2. {{site.data.keyword.cloudaccesstrailshort}} 서비스가 자동으로 수집하는 활동 이벤트를 클라우드 서비스를 사용하여 생성하는 방법을 보여줍니다. 이벤트는 [CADF(Cloud Auditing Data Federation) 표준 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.dmtf.org/sites/default/files/standards/documents/DSP0262_1.0.0.pdf){: new_window}을 준수합니다.
3. 사전 정의된 {{site.data.keyword.cloudaccesstrailshort}} 대시보드를 사용하여 서비스의 클라우드 활동을 모니터하는 방법을 보여줍니다.

다음 그림은 사용자가 시작한 활동이 서비스의 상태를 변경하는 경우 발생하는 다양한 컴포넌트 및 조치를 보여줍니다.

![사용자가 시작한 활동이 서비스의 상태를 변경하는 경우 발생하는 컴포넌트 및 조치](../images/AT_f1.png "사용자가 시작한 활동이 서비스의 상태를 변경하는 경우 발생하는 컴포넌트 및 조치")



## 시작하기 전에
{: #kp_prereqs}

[{{site.data.keyword.cloud_notm}} 계정](https://cloud.ibm.com/registration/)을 작성하십시오. 사용자의 사용자 ID는 {{site.data.keyword.cloud_notm}} 계정의 구성원 또는 소유자여야 하며, {{site.data.keyword.cloudaccesstrailshort}} 서비스를 사용할 영역의 개발자 권한이 있어야 합니다.


## 1단계: Activity Tracker 프로비저닝
{: #kp_step1}

활동을 모니터할 클라우드 서비스가 프로비저닝된 지역과 동일한 지역에 {{site.data.keyword.cloudaccesstrailshort}} 서비스를 프로비저닝해야 합니다. {{site.data.keyword.cloudaccesstrailshort}} 서비스가 프로비저닝되면 선택된 클라우드 서비스로부터 자동으로 이벤트가 수집됩니다. 

**참고:** 이 튜토리얼은 {{site.data.keyword.cloudaccesstrailshort}} 서비스를 사용하여 사용자와 미국 남부 지역의 클라우드 서비스 {{site.data.keyword.keymanagementservicelong_notm}} 간의 상호작용을 모니터하는 방법을 보여줍니다. 따라서 {{site.data.keyword.cloudaccesstrailshort}}를 미국 남부 지역에 프로비저닝해야 합니다. 특정 서비스가 사용 가능한 지역에 대한 정보를 보려면 [지역별 서비스](/docs/resources/services_region.html#services_region)를 참조하십시오.

{{site.data.keyword.cloudaccesstraillong_notm}} 서비스의 인스턴스를 {{site.data.keyword.cloud_notm}}에 프로비저닝하려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.cloud_notm}}에 로그인하십시오.

    {{site.data.keyword.cloud_notm}} 대시보드는 [http://cloud.ibm.com ![외부 링크 아이콘](../../../icons/launch-glyph.svg "외부 링크 아이콘")](http://cloud.ibm.com){:new_window}에 있습니다.
    
	사용자 ID 및 비밀번호를 사용하여 로그인하면 {{site.data.keyword.cloud_notm}} UI가 열립니다.

2. **카탈로그**를 클릭하십시오. {{site.data.keyword.cloud_notm}}에서 사용 가능한 서비스의 목록이 열립니다.

3. **보안 및 ID** 카테고리를 선택하여 표시되는 서비스의 목록을 필터링하십시오.

    **참고:** 이 서비스는 **개발자 도구** 카테고리를 통해서도 사용할 수 있습니다.

4. **Activity Tracker** 타일을 클릭하십시오. 

5. 서비스가 프로비저닝될 위치를 정의하는 정보를 구성하십시오. 

    다음 표에 표시되어 있는 바와 같이 데이터를 입력하십시오. 

    <table>
	  <caption>표 1. {{site.data.keyword.cloudaccesstrailshort}} 서비스를 프로비저닝하는 데 필요한 필드</caption>
	  <tr>
	    <th width="50%">필드</th>
		<th width="50%">값</th>
	  </tr>
	  <tr>
	    <td>배치할 지역 선택:</td>
		<td>미국 남부</td>
	  </tr>
	  <tr>
	    <td>조직 선택:</td>
		<td>{{site.data.keyword.cloudaccesstrailshort}} 서비스를 프로비저닝할 조직을 선택하십시오.</td>
	  </tr>
	  <tr>
	    <td>영역 선택:</td>
		<td>{{site.data.keyword.cloudaccesstrailshort}} 서비스를 프로비저닝하기 위해 선택한 조직 내의 영역을 선택하십시오.</td>
	  </tr>
	</table>

6. **작성**을 클릭하여 로그인되어 있는 영역에 {{site.data.keyword.cloudaccesstrailshort}} 서비스를 프로비저닝하십시오.
   

## 2단계: 클라우드 서비스 구성  
{: #kp_step2}

이 튜토리얼은 {{site.data.keyword.cloud_notm}}에 있는 {{site.data.keyword.keymanagementserviceshort}} 서비스의 API 활동을 모니터하는 방법을 보여줍니다.

{{site.data.keyword.cloud_notm}}에 있는 {{site.data.keyword.keymanagementserviceshort}} 서비스를 구성하려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.keymanagementserviceshort}} 서비스의 인스턴스를 미국 남부 지역에 프로비저닝하십시오. 자세한 정보는 [IBM Cloud 콘솔에서 프로비저닝](/docs/services/key-protect/provision.html#provision)을 참조하십시오.

2. 키에 대해 작업하는 데 사용할 사용자의 {{site.data.keyword.cloud_notm}} 권한을 정의하십시오. 

    * 사용자가 키를 작성하려면 서비스 역할이 *관리자* 또는 *작성자*로 설정된 IAM 정책이 필요합니다.
	* 사용자가 키를 삭제하려면 서비스 역할이 *관리자*로 설정된 IAM 정책이 필요합니다.
	* 사용자가 키를 보려면 서비스 역할이 *독자*로 설정된 IAM 정책이 필요합니다. 


## 3단계: Activity Tracker 이벤트 생성
{: #kp_step3}

이 단계에서는 {{site.data.keyword.cloudaccesstrailshort}} 이벤트 데이터를 생성하기 위해 {{site.data.keyword.keymanagementserviceshort}} 서비스를 사용하여 보안 키를 작성합니다. 자세한 정보는 [새 키 작성](/docs/services/key-protect/create-standard-keys.html#create-standard-keys)을 참조하십시오.

* 키를 작성하면 {{site.data.keyword.cloudaccesstrailshort}} 이벤트가 생성됩니다.
* {{site.data.keyword.cloudaccesstrailshort}} 이벤트는 이벤트가 생성된 {{site.data.keyword.cloud_notm}} 지역에서 사용 가능한 {{site.data.keyword.cloudaccesstrailshort}} **계정 도메인**에서 사용할 수 있습니다. 

## 4단계: Activity Tracker 이벤트 모니터링
{: #kp_step4}

이 단계에서는 {{site.data.keyword.cloudaccesstrailshort}} 이벤트의 생성 여부를 {{site.data.keyword.cloud_notm}} UI를 통해 확인하십시오.

다음 단계를 완료하여 이벤트가 작성되었는지 확인하십시오.

1. 계정 이벤트를 볼 수 있는 사용자 권한을 부여하십시오. 자세한 정보는 [계정 이벤트 보기](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/viewing_events.html#view_acc_events_account_events) 및 [계정 이벤트를 볼 수 있는 권한 부여](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_acc_events)를 참조하십시오.

2. {{site.data.keyword.cloud_notm}} 대시보드에서 {{site.data.keyword.cloudaccesstrailshort}} 서비스를 선택하십시오. 서비스 대시보드가 열립니다.

3. 서비스를 프로비저닝하고 키를 추가했을 때 생성된 {{site.data.keyword.keymanagementserviceshort}} 이벤트를 검색하도록 보기를 구성하십시오.

    * *로그 보기* 필드에서 **계정 로그**를 선택하십시오.
    * *검색 필드*에서 ** target.typeURI_str**을 선택하고 *필터* 필드에서 **kms/secrets**를 입력하십시오.
	
    표시되는 데이터는 최근 24시간 동안 사용 가능한 {{site.data.keyword.keymanagementserviceshort}} 이벤트를 보여줍니다. 
	


## 다음 단계
{: #kp_next_steps}

다음에는 {{site.data.keyword.cloudaccesstrailshort}} 사전 정의된 Kibana 대시보드를 사용하여 이벤트 로그를 모니터하고 분석하십시오. Kibana를 실행하려면 [Kibana 대시보드로 이동](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_kibana.html#launch_kibana)을 참조하십시오. 기본적으로 Kibana에서는 영역 활동 로그가 **ActivityTracker_Space_Dashboard_in_24h** 대시보드를 통해 표시됩니다.

{{site.data.keyword.cloudaccesstrailshort}} CLI를 사용하여 명령행에서 이벤트를 관리할 수도 있습니다. 자세한 정보는 [이벤트 정보 보기](/docs/services/cloud-activity-tracker/how-to/viewing_event_information.html#viewing_event_status)를 참조하십시오.



