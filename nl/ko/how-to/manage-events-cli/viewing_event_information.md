---

copyright:
  years: 2016, 2017
lastupdated: "2017-09-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 이벤트 정보 보기
{: #viewing_event_status}

*cf at status* 명령을 사용하여 {{site.data.keyword.Bluemix}} 영역에 대한 {{site.data.keyword.cloudaccesstrailshort}}에 수집되어 저장되는 이벤트에 대한 정보를 얻으십시오.
{:shortdesc}

## 이벤트에 대한 정보 얻기
{: #viewing_event_information}

이벤트의 크기, 개수, Kibana에서의 분석 가능 여부를 보려면 `cf at status` 명령을 사용하십시오. 자세한 정보는 [cf at status](/docs/services/cloud-activity-tracker/cli/at_cli.html#status)를 참조하십시오. 

1. {{site.data.keyword.Bluemix_notm}} 지역, 조직 및 영역에 로그인하십시오.  

    ```
    bx login -a Endpoint
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
	</table>

    지시사항에 따르십시오.  

    예를 들어, 미국 남부 지역에 로그인하려면 다음 명령을 실행하십시오. 
	
	```
	bx login -a api.ng.bluemix.net
	```
	{: codeblock}
	
	그런 다음 조직 및 영역을 설정하십시오. 다음 명령을 실행하십시오. 

    ```
    bx target -o OrgName -s SpaceName
    ```
   {: codeblock}

    여기서,


    * OrgName은 조직의 이름입니다. 
    * SpaceName은 영역의 이름입니다. 
    
2. *cf at status* 명령을 실행하여 {{site.data.keyword.cloudaccesstrailshort}}에 수집된 이벤트의 세부사항을 보십시오. 

    ```
    $ bx cf at status -a -s YYYY-MM-DD -e YYYY-MM-DD 
    ```
    {: codeblock}
    
    여기서,

    
    * *-a*는 계정 레벨 정보를 지정하는 데 사용됩니다. 
    * *-s*는 UTC(협정 세계 표준시) 형식(*YYYY-MM-DD*)으로 시작 날짜를 설정하는 데 사용됩니다. 
    * *-e*는 UTC(협정 세계 표준시) 형식(*YYYY-MM-DD*)으로 종료 날짜를 설정하는 데 사용됩니다. 
    	
	시작 일을 설정하려면 옵션 **-s**와 함께, 종료 일을 설정하려면 옵션 **-e**와 함께 `cf at status` 명령을 사용하십시오. 예를 들면, 다음과 같습니다. 

    * `bx cf at status`는 최근 2주일의 정보를 제공합니다. 
    * `bx cf at status -s 2017-05-03`은 2017년 5월 3일부터 현재 날짜까지의 정보를 제공합니다. 
    * `bx cf at status -s 2017-05-03 -e 2017-05-08`은 2017년 5월 3일부터 2017년 5월 8일까지의 정보를 제공합니다.  
 
    계정에 도메인을 설정하려면 옵션 **-a**와 함께 `cf at status` 명령을 사용하십시오. 
	
    예를 들어, 2017년 6월 10일의 사용 가능한 이벤트에 대한 정보를 가져오려면 다음 명령을 실행하십시오. 
    
    ```
    $ bx cf at status -s 2017-06-10 -e 2017-06-10
    +------------+-------+------+-----------------+------------+
    | Date       | Count | Size | Types           | Searchable |
    +------------+-------+------+-----------------+------------+
    | 2017-07-10 | 1     | 2531 | ActivityTracker | All        |
    +------------+-------+------+-----------------+------------+
    ```
    {: screen}
	














