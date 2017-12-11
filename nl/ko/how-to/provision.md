---

copyright:
  years: 2016, 2017

lastupdated: "2017-09-17"

---


{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# Activity Tracker 서비스 프로비저닝
{: #provision}

{{site.data.keyword.cloudaccesstraillong}} 서비스는 {{site.data.keyword.Bluemix}} UI 또는 명령행에서 프로비저닝할 수 있습니다.
{:shortdesc}


## UI에서의 프로비저닝
{: #ui}

{{site.data.keyword.Bluemix_notm}}에서 {{site.data.keyword.cloudaccesstraillong_notm}} 서비스의 인스턴스를 프로비저닝하려면 다음 단계를 완료하십시오. 

1. {{site.data.keyword.Bluemix_notm}} 계정에 로그인하십시오. 

    {{site.data.keyword.Bluemix_notm}} 대시보드는 [http://bluemix.net ![외부 링크 아이콘](../../../icons/launch-glyph.svg "외부 링크 아이콘")](http://bluemix.net){:new_window}에 있습니다. 
    
	사용자 ID 및 비밀번호를 사용하여 로그인하면 {{site.data.keyword.Bluemix_notm}} UI가 열립니다. 

2. **카탈로그**를 클릭하십시오. {{site.data.keyword.Bluemix_notm}}에서 사용 가능한 서비스의 목록이 열립니다. 

3. **보안** 카테고리를 선택하여 표시되는 서비스의 목록을 필터링하십시오. 

    이 서비스는 **DevOps** 카테고리에도 있습니다. 

4. **Activity Tracker** 타일을 클릭하십시오. 

5. 서비스가 프로비저닝될 위치를 정의하는 정보를 구성하십시오.  

    다음 표에 표시되어 있는 바와 같이 데이터를 입력하십시오.  

    <table>
	  <caption>표 1. {{site.data.keyword.cloudaccesstrailshort}} 서비스를 프로비저닝하는 데 필요한 필드</caption>
	  <tr>
	    <th>필드</th>
		<th>값</th>
	  </tr>
	  <tr>
	    <td>배치할 지역 선택:</td>
		<td>올바른 값은 미국 남부, 영국, 독일입니다. </td>
	  </tr>
	  <tr>
	    <td>조직 선택:</td>
		<td>활동을 모니터할 조직을 선택하십시오. </td>
	  </tr>
	  <tr>
	    <td>영역 선택:</td>
		<td>활동을 모니터하기 위해 선택한 조직 내의 영역을 선택하십시오. </td>
	  </tr>
	</table>

6. 서비스 플랜을 선택하십시오.  

    기본적으로는 **무료** 플랜이 설정되어 있습니다. 

    자세한 정보는 [서비스 플랜](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#plans)을 참조하십시오. 
	
7. **작성**을 클릭하여 로그인되어 있는 {{site.data.keyword.Bluemix_notm}} 영역에서 {{site.data.keyword.cloudaccesstrailshort}} 서비스를 프로비저닝하십시오. 
  
 

## CLI에서의 프로비저닝
{: #cli}

CLI를 통해 {{site.data.keyword.cloudaccesstraillong_notm}}의 인스턴스를 {{site.data.keyword.Bluemix_notm}}에서 프로비저닝하려면 다음 단계를 완료하십시오. 

1. Cloud Foundry(CF) CLI를 설치하십시오. CF CLI가 설치되어 있는 경우에는 다음 단계로 진행하십시오. 

   자세한 정보는 [cf CLI 설치 ![외부 링크 아이콘](../../../icons/launch-glyph.svg "외부 링크 아이콘")](http://docs.cloudfoundry.org/cf-cli/install-go-cli.html){: new_window}를 참조하십시오.  
    
2. {{site.data.keyword.Bluemix_notm}} 지역, 조직 및 영역에 로그인하십시오.  

    예를 들어, 미국 남부 지역에 로그인하려면 다음 명령을 실행하십시오. 

    ```
    cf login -a https://api.ng.bluemix.net
    ```
    {: codeblock}

    지시사항에 따르십시오. {{site.data.keyword.Bluemix_notm}} 신임 정보를 입력하고, 조직 및 영역을 선택하십시오. 
	
3. `cf create-service` 명령을 실행하여 인스턴스를 프로비저닝하십시오. 

    ```
	cf create-service service_name service_plan service_instance_name
	```
	{: codeblock}
	
	여기서,
	
	* service_name은 서비스의 이름(즉, **activityTracker**)입니다.
	* service_plan은 서비스 플랜 이름입니다. 플랜의 목록은 [서비스 플랜](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#plans)을 참조하십시오.
	* service_instance_name은 작성하는 새 서비스 인스턴스에 사용할 이름입니다.
	
	이 cf 명령에 대한 자세한 정보는 [cf create-service](/docs/cli/reference/cfcommands/index.html#cf_create-service)를 참조하십시오.

	예를 들어, 라이트 플랜을 사용하여 {{site.data.keyword.cloudaccesstrailshort}} 서비스의 인스턴스를 작성하려면 다음 명령을 실행하십시오.
	
	```
	cf create-service activityTracker free my_activity_tracker_svc
	```
	{: codeblock}
	
4. 서비스가 성공적으로 작성되었는지 확인하십시오. 다음 명령을 실행하십시오.

 ```	
	cf services
	```
	{: codeblock}
	
	이 명령 실행의 출력은 다음과 유사합니다.
	
	```
    Getting services in org MyOrg / space MySpace as xxx@yyy.com...
    OK
    
    name                           service                  plan                   bound apps              last operation
    my_activity_tracker_svc        activityTracker          free                                           create succeeded
	```
	{: screen}

	



