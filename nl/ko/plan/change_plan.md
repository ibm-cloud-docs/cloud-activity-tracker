---

copyright:
  years: 2017
lastupdated: "2017-09-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# 플랜 변경
{: #change_plan}

{{site.data.keyword.cloudaccesstraillong}} 서비스 플랜은 {{site.data.keyword.Bluemix_notm}} 서비스 대시보드에서 변경하거나, `cf update-service` 명령을 실행하여 변경할 수 있습니다. 플랜은 언제든지 업그레이드 또는 다운그레이드할 수 있습니다.
{:shortdesc}

## UI를 통한 서비스 플랜 변경
{: #change_plan_ui}

서비스 대시보드에서 {{site.data.keyword.Bluemix_notm}}의 서비스 플랜을 변경하려면 다음 단계를 완료하십시오. 

1. {{site.data.keyword.Bluemix_notm}}에 로그인한 후 {{site.data.keyword.Bluemix_notm}} 대시보드에서 {{site.data.keyword.cloudaccesstraillong_notm}} 서비스를 클릭하십시오.  
    
2. {{site.data.keyword.Bluemix_notm}} UI에서 **플랜** 탭을 선택하십시오. 

    현재 플랜에 대한 정보가 표시됩니다. 
	
3. 현재 플랜을 업그레이드하거나 다운그레이드하는 새 플랜을 선택하십시오.  

4. **저장**을 클릭하십시오. 



## CLI를 통한 서비스 플랜 변경
{: #change_plan_cli}

CLI를 통해 Bluemix의 서비스 플랜을 변경하려면 다음 단계를 완료하십시오. 

1. {{site.data.keyword.Bluemix_notm}} 지역, 조직 및 영역에 로그인하십시오.  

    ```
    cf login -a Endpoint
    ```
    {: codeblock}
	
	여기서 *Endpoint*는 {{site.data.keyword.Bluemix_notm}}에 로그인하는 데 필요한 URL입니다. 이 URL은 지역별로 다릅니다. 
	
	<table>
	    <caption>{{site.data.keyword.Bluemix_notm}}에 액세스하기 위한 엔드포인트 목록</caption>
		<tr>
		  <th>지역</th>
		  <th>URL</th>
		</tr>
		<tr>
		  <td>미국 남부</td>
		  <td>api.ng.bluemix.net</td>
		</tr>
		<tr>
		  <td>영국</td>
		  <td>api.eu-gb.bluemix.net</td>
		</tr>
		<tr>
		  <td>독일</td>
		  <td>api.eu-de.bluemix.net</td>
		</tr>
	</table>

    지시사항에 따르십시오. {{site.data.keyword.Bluemix_notm}} 신임 정보를 입력하고, 조직 및 영역을 선택하십시오.  

    예를 들어, 미국 남부 지역에 로그인하려면 다음 명령을 실행하십시오. 
	
	```
	cf login -a api.ng.bluemix.net
	```
	{: codeblock}
	
2. `cf services` 명령을 실행하여 현재 플랜을 확인하고, 영역에서 사용 가능한 서비스 목록에서 {{site.data.keyword.cloudaccesstrailshort}} 서비스 이름을 가져오십시오.  

    필드 **name**의 값이 플랜을 변경하는 데 사용해야 하는 값입니다.  

    예를 들면, 다음과 같습니다. 
	
	```
	$ cf services
    Getting services in org MyOrg / space dev as xxx@yyy.com...
    OK
    
    name                            service              plan          bound apps      last operation
    Activity Tracker-oj            activityTracker       premium                       create succeeded
    ```
	{: screen}
    
3. 플랜을 업그레이드하거나 다운그레이드하십시오. `cf update-service` 명령을 실행하십시오. 
    
	```
	cf update-service service_name [-p new_plan]
	```
	{: codeblock}
	
	여기서,
 
	
	* *service_name*은 서비스의 이름입니다. `cf services` 명령을 실행하여 이 값을 얻을 수 있습니다. 
	* *new_plan*은 플랜의 이름입니다. 
	
	다음 표에는 다양한 플랜과 해당 지원 값이 나열되어 있습니다. 
	
	<table>
	  <caption>표 1. 플랜 목록</caption>
	  <tr>
	    <th>플랜</th>
	    <th>이름</th>
	  </tr>
	  <tr>
	    <td>라이트</td>
	    <td>lite</td>
	  </tr>
	  <tr>
	    <td>프리미엄</td>
	    <td>premium</td>
	  </tr>
	</table>
	
	예를 들어, 플랜을 *라이트* 플랜으로 다운그레이드하려면 다음 명령을 실행하십시오. 
	
	```
	cf update-service "Activity Tracker-oj" -p lite
    Updating service instance Activity Tracker-oj as xxx@yyy.com...
    OK
	```
	{: screen}

4. 새 플랜으로 변경되었는지 확인하십시오. `cf services` 명령을 실행하십시오. 

    ```
	cf services
    Getting services in org MyOrg / space dev as xxx@yyy.com...
    OK

    name                   service            plan      bound apps   last operation
    Activity Tracker-oj    activityTracker    lite                   update succeeded
	```
	{: screen}






