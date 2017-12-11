---

copyright:
  years: 2016, 2017
lastupdated: "2017-09-17"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 시작하기 튜토리얼
{: #getting-started-with-cla}

{{site.data.keyword.cloudaccesstrailfull}} 서비스는 {{site.data.keyword.IBM}} 클라우드 내 서비스의 상태를 변경하는, 사용자가 시작한 활동을 기록합니다. 이 튜토리얼을 통해 {{site.data.keyword.cloudaccesstrailfull}} 서비스를 사용하여 사용자와 클라우드 서비스 간의 상호작용을 모니터하는 방법을 알아보십시오.
{:shortdesc}

이 시작하기 튜토리얼의 목표는 다음과 같습니다. 

1. {{site.data.keyword.cloudaccesstrailshort}} 서비스를 프로비저닝하는 방법을 보여줍니다. 
2. {{site.data.keyword.cloudaccesstrailshort}} 서비스가 자동으로 수집하는 활동 이벤트를 클라우드 서비스를 사용하여 생성하는 방법을 보여줍니다. 이벤트는 CADF(Cloud Auditing Data Federation) 표준을 준수합니다. 
3. 사전 정의된 {{site.data.keyword.cloudaccesstrailshort}} 대시보드를 사용하여 서비스의 클라우드 활동을 모니터하는 방법을 보여줍니다. 

다음 그림은 사용자가 시작한 활동이 서비스의 상태를 변경하는 경우 발생하는 다양한 컴포넌트 및 조치를 보여줍니다. 

![사용자가 시작한 활동이 서비스의 상태를 변경하는 경우 발생하는 컴포넌트 및 조치](images/AT_f1.png "사용자가 시작한 활동이 서비스의 상태를 변경하는 경우 발생하는 컴포넌트 및 조치")



## 시작하기 전에
{: #prereqs}

[{{site.data.keyword.Bluemix_notm}} 계정](https://console.bluemix.net/registration/)을 작성하십시오. 사용자의 사용자 ID는 {{site.data.keyword.Bluemix_notm}} 계정의 구성원 또는 소유자여야 하며, {{site.data.keyword.cloudaccesstrailshort}} 서비스를 사용할 영역의 개발자 권한이 있어야 합니다. 


## 1단계: Activity Tracker 프로비저닝
{: #step1}

모니터하려는 활동이 프로비저닝되는 클라우드 서비스와 동일한 영역 및 지역에서 {{site.data.keyword.cloudaccesstrailshort}} 서비스를 프로비저닝해야 합니다. {{site.data.keyword.cloudaccesstrailshort}} 서비스가 프로비저닝되면 해당 영역에 프로비저닝되어 있는, 선택된 클라우드 서비스로부터 자동으로 이벤트가 수집됩니다. {{site.data.keyword.cloudaccesstrailshort}}을 통해 활동을 모니터할 수 있는 서비스의 목록은 [지원되는 클라우드 서비스](/docs/services/cloud-activity-tracker/cloud_services.html#cloud_services)를 참조하십시오. 

**참고:** 이 튜토리얼은 {{site.data.keyword.cloudaccesstrailshort}} 서비스를 사용하여 사용자와 클라우드 서비스 {{site.data.keyword.keymanagementservicelong_notm}} 간의 상호작용을 모니터하는 방법을 보여줍니다. {{site.data.keyword.keymanagementserviceshort}} 서비스는 미국 남부에서 사용 가능합니다. 따라서 {{site.data.keyword.cloudaccesstrailshort}}은 미국 남부 지역의, {{site.data.keyword.keymanagementserviceshort}} 서비스가 사용 가능한 영역과 동일한 영역에서 프로비저닝해야 합니다. 특정 서비스가 사용 가능한 지역에 대한 정보를 보려면 [지역별 서비스](/docs/services/services_region.html#services_region)를 참조하십시오. 

{{site.data.keyword.Bluemix_notm}}에서 {{site.data.keyword.cloudaccesstraillong_notm}} 서비스의 인스턴스를 프로비저닝하려면 다음 단계를 완료하십시오. 

1. {{site.data.keyword.Bluemix_notm}} 계정에 로그인하십시오. 

    {{site.data.keyword.Bluemix_notm}} 대시보드는 [http://bluemix.net ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://bluemix.net){:new_window}에 있습니다. 
    
	사용자 ID 및 비밀번호를 사용하여 로그인하면 {{site.data.keyword.Bluemix_notm}} UI가 열립니다. 

2. **카탈로그**를 클릭하십시오. {{site.data.keyword.Bluemix_notm}}에서 사용 가능한 서비스의 목록이 열립니다. 

3. **보안** 카테고리를 선택하여 표시되는 서비스의 목록을 필터링하십시오. 

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
		<td>활동을 모니터할 조직을 선택하십시오. </td>
	  </tr>
	  <tr>
	    <td>영역 선택:</td>
		<td>활동을 모니터하려고 선택한 조직에서 영역을 선택하십시오. </td>
	  </tr>
	</table>

6. **작성**을 클릭하여 로그인되어 있는 {{site.data.keyword.Bluemix_notm}} 영역에서 {{site.data.keyword.cloudaccesstrailshort}} 서비스를 프로비저닝하십시오. 
   

## 2단계: 클라우드 서비스 프로비저닝 
{: #step2}
	
{{site.data.keyword.Bluemix_notm}} 미국 남부 지역에 {{site.data.keyword.keymanagementserviceshort}} 서비스의 인스턴스를 프로비저닝하려면 다음 단계를 완료하십시오. 

1. {{site.data.keyword.Bluemix_notm}} 계정에 로그인하십시오. 

    {{site.data.keyword.Bluemix_notm}} 대시보드는 [http://bluemix.net ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://bluemix.net){:new_window}에 있습니다. 
	
	사용자 ID 및 비밀번호를 사용하여 로그인하면 {{site.data.keyword.Bluemix_notm}} UI가 열립니다. 

2. **카탈로그**를 클릭하십시오. {{site.data.keyword.Bluemix_notm}}에서 사용 가능한 서비스의 목록이 열립니다. 

    **보안** 카테고리를 선택하여 표시되는 서비스의 목록을 필터링하십시오. 

3. **Key Protect** 타일을 선택하십시오. 

4. 서비스가 프로비저닝될 위치를 정의하는 정보를 구성하십시오.  

    다음 표에 표시되어 있는 바와 같이 데이터를 입력하십시오.  

    <table>
	  <caption>표 2. {{site.data.keyword.keymanagementserviceshort}} 서비스를 프로비저닝하는 데 필요한 필드</caption>
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
		<td>{{site.data.keyword.cloudaccesstrailshort}} 서비스를 프로비저닝하기 위해 선택한 조직을 선택하십시오. </td>
	  </tr>
	  <tr>
	    <td>영역 선택:</td>
		<td>{{site.data.keyword.cloudaccesstrailshort}} 서비스를 프로비저닝하기 위해 선택한 영역을 선택하십시오. </td>
	  </tr>
	</table>

5. **작성**을 클릭하여 로그인되어 있는 {{site.data.keyword.Bluemix_notm}} 영역에서 {{site.data.keyword.keymanagementserviceshort}} 서비스를 프로비저닝하십시오. 


## 3단계: Activity Tracker 이벤트 생성
{: # step3}

이 단계에서는 {{site.data.keyword.cloudaccesstrailshort}} 이벤트 데이터를 생성하기 위해 {{site.data.keyword.keymanagementserviceshort}} 서비스를 사용하여 보안 키를 작성합니다.  

{{site.data.keyword.cloudaccesstrailshort}} 이벤트를 생성하려면 다음 단계를 완료하십시오. 

1. {{site.data.keyword.Bluemix_notm}} 대시보드에서 **Key Protect** 서비스를 선택하십시오. {{site.data.keyword.keymanagementserviceshort}} 대시보드가 열립니다. 그런 다음 **관리** 탭을 선택하십시오. 

2. **키 추가**를 클릭하십시오. 새 창이 열립니다. 

3. **키 생성**을 선택하고 다음 단계를 완료하십시오. 

    * *MyFirstKey*와 같이 키의 이름을 입력하십시오. 

    * 키의 알고리즘을 선택하십시오. 

    * **키 추가**를 클릭하십시오.  
	
키를 작성하면 {{site.data.keyword.cloudaccesstrailshort}} 이벤트가 생성됩니다. 

## 4단계: Activity Tracker 이벤트 모니터링
{: #step4}

이 단계에서는 {{site.data.keyword.cloudaccesstrailshort}} 이벤트의 생성 여부를 {{site.data.keyword.Bluemix_notm}} UI를 통해 확인합니다. 

다음 단계를 완료하여 이벤트가 작성되었는지 확인하십시오. 

1. {{site.data.keyword.Bluemix_notm}} 대시보드에서 {{site.data.keyword.cloudaccesstrailshort}} 서비스를 선택하십시오. 서비스 대시보드가 열립니다. 

2. 서비스를 프로비저닝하고 키를 추가했을 때 생성된 {{site.data.keyword.keymanagementserviceshort}} 이벤트를 검색하도록 보기를 구성하십시오. 

    * *로그 보기* 필드에서 **영역 로그**를 선택하십시오. 
    * *검색 필드* 필드에서 **target.name**을 선택하십시오. 
    * *필터* 필드에 **ibm-key-protect**를 입력하십시오. 
	
    표시되는 데이터는 최근 24시간 동안 사용 가능한 {{site.data.keyword.keymanagementserviceshort}} 이벤트를 보여줍니다.  
	
	![이벤트에 대한 UI 보기](images/bmx_ui_space_view.png "이벤트에 대한 UI 보기")


## 다음 단계
{: #next_steps}

다음에는 {{site.data.keyword.cloudaccesstrailshort}} 사전 정의된 Kibana 대시보드를 사용하여 이벤트 로그를 모니터하고 분석하십시오. Kibana를 실행하려면 [Kibana 대시보드로 이동](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_kibana.html#launch_kibana)을 참조하십시오.  

기본적으로 Kibana에서는 영역 활동 로그가 **ActivityTracker_Space_Search_in_24h** 대시보드를 통해 표시됩니다. 

![이벤트에 대한 Kibana 보기](images/kibana_space_view.png "이벤트에 대한 Kibana 보기")

{{site.data.keyword.cloudaccesstrailshort}} CLI를 사용하여 명령행에서 이벤트를 관리할 수도 있습니다. 자세한 정보는 [이벤트 정보 보기](/docs/services/cloud-activity-tracker/how-to/manage-events-cli/viewing_event_information.html#viewing_event_status)를 참조하십시오. 

                                                                                                                      

