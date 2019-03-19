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



# 플랜 변경
{: #change_plan}

{{site.data.keyword.cloud_notm}} UI를 통해 또는 `ibmcloud service update` 명령을 실행하여 {{site.data.keyword.cloudaccesstraillong}} 서비스 플랜을 변경할 수 있습니다. 플랜은 언제든지 업그레이드 또는 다운그레이드할 수 있습니다.
{:shortdesc}

## UI를 통한 서비스 플랜 변경
{: #change_plan_ui}

{{site.data.keyword.cloud_notm}} UI를 통해 서비스 플랜을 변경하려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.cloud_notm}}에 로그인한 후 *대시보드*에서 {{site.data.keyword.cloudaccesstraillong_notm}} 서비스를 클릭하십시오. 
    
2. **플랜** 탭을 선택하십시오.

    현재 플랜에 대한 정보가 표시됩니다.
	
3. 현재 플랜을 업그레이드하거나 다운그레이드하는 새 플랜을 선택하십시오. 

4. **저장**을 클릭하십시오.



## CLI를 통한 서비스 플랜 변경
{: #change_plan_cli}

CLI를 통해 서비스 플랜을 변경하려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.cloud_notm}}에 로그인하십시오. 

    [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) 명령을 실행하여 {{site.data.keyword.cloud_notm}}에 로그인한 후 [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) 명령을 실행하여 {{site.data.keyword.cloudaccesstrailshort}} 서비스를 프로비저닝할 조직 및 영역을 설정하십시오.
	
2. `ibmcloud service list` 명령을 실행하여 현재 플랜을 확인하고, 영역에서 사용 가능한 서비스의 목록에서 {{site.data.keyword.cloudaccesstrailshort}} 서비스 이름을 가져오십시오. 

    필드 **name**의 값이 플랜을 변경하는 데 사용해야 하는 값입니다. 

    예를 들면, 다음과 같습니다.
	
	```
	$ ibmcloud service list
    Invoking 'cf services'...

    Getting services in org MyOrg / space dev as xxx@ibm.com...
    OK

    name                       service                  plan                 bound apps                               last operation
    Activity Tracker-zt          OK                     accessTrail             premium                                update succeeded
    ```
	{: screen}
    
3. 플랜을 업그레이드하거나 다운그레이드하십시오. `ibmcloud service update` 명령을 실행하십시오.
    
	```
	ibmcloud service update service_name [-p new_plan]
	```
	{: codeblock}
	
	여기서, 
	
	* *service_name*은 서비스의 이름입니다. `ibmcloud service list` 명령을 실행하여 이 값을 가져올 수 있습니다.
	* *new_plan*은 플랜의 이름입니다.
	
	다음 표에는 다양한 플랜과 해당 지원 값이 나열되어 있습니다.
	
	<table>
	  <caption>표 1. 플랜 목록</caption>
	  <tr>
	    <th>플랜</th>
	    <th>이름</th>
	  </tr>
	  <tr>
	    <td>Lite</td>
	    <td>free</td>
	  </tr>
	  <tr>
	    <td>프리미엄</td>
	    <td>premium</td>
	  </tr>
	</table>
	
	예를 들어, 플랜을 *Lite* 플랜으로 다운그레이드하려면 다음 명령을 실행하십시오.
	
	```
	ibmcloud service update "Activity Tracker-zt" -p free
    Updating service instance Activity Tracker-zt as xxx@ibm.com...
    OK
	```
	{: screen}



