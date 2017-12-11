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

# 이벤트 다운로드
{: #downloading_events}

이벤트를 로컬 파일에 다운로드하거나 데이터를 다른 프로그램으로 전달할 수 있습니다. 사용자는 세션의 컨텍스트 내에서 이벤트를 다운로드합니다. 세션은 다운로드될 이벤트를 지정합니다. 이벤트 다운로드가 인터럽트된 경우, 세션은 다운로드를 중단된 위치에서 재개할 수 있게 해 줍니다. 다운로드가 완료된 후에는 세션을 삭제해야 합니다.
{:shortdesc}

{{site.data.keyword.Bluemix_notm}} 영역에서 사용 가능한 이벤트를 로컬 파일에 다운로드하려면 다음 단계를 완료하십시오. 

## 1단계: Bluemix에 로그인
{: #prereq}

시작하려면 먼저 {{site.data.keyword.cloudaccesstrailshort}} 서비스가 프로비저닝된 {{site.data.keyword.Bluemix_notm}} 지역, 조직 및 영역에 로그인하십시오.  

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

## 2단계: 사용할 수 있는 이벤트 식별
{: #step2}

1. `cf at status` 명령을 사용하여 사용 가능한 이벤트를 보십시오. 

    예를 들어, 최근 2주일에 대해 사용 가능한 이벤트를 보려면 다음 명령을 실행하십시오. 

    ```
    $ bx cf at status
    ```
    {: codeblock}
    
    예를 들면, 이 명령 실행의 출력은 다음과 같습니다. 
    
    ```
    +------------+--------+-------+--------------------+------------+
    |    DATE    |  COUNT | SIZE  |       TYPES        | SEARCHABLE |
    +------------+--------+-------+--------------------+------------+
    | 2017-07-24 |    16  | 3020  | ActivityTracker    |   None     |
    +------------+--------+-------+--------------------+------------+
    | 2017-07-25 |   1224 | 76115 | ActivityTracker    |    All     |
    +------------+--------+-------+--------------------+------------+
    ```
    {: screen}

    **참고:** {{site.data.keyword.cloudaccesstrailshort}} 서비스는 UTC(협정 세계 표준시)를 사용하는 글로벌 서비스입니다. 일은 UTC 일로 정의됩니다. 특정 로컬 시간 일의 이벤트를 가져오는 경우에는 여러 UTC 일을 다운로드해야 할 수 있습니다. 
	
	자세한 정보는 [cf at status](/docs/services/cloud-activity-tracker/cli/at_cli.html#status)를 참조하십시오. 


## 3단계: 세션 작성
{: #step3}

다운로드 가능한 이벤트 데이터의 범위를 정의하고 다운로드의 상태를 보존하려면 세션이 필요합니다.  

세션을 작성하려면 명령 [cf at session create](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_create)를 사용하십시오. 세션을 작성할 때는 선택적으로 시작 날짜 및 종료 날짜를 지정할 수 있습니다.  

**참고:** 시작 날짜와 종료 날짜를 지정하는 경우, 세션은 이러한 날짜 범위(경계값 포함)에 속한 이벤트에 대해 액세스를 제공합니다.  

현재 날짜의 이벤트를 다운로드하는 데 사용되는 세션을 작성하려면 다음 명령을 실행하십시오. 

```
bx cf at session create 
```
{: codeblock}

이 세션은 다음 정보를 리턴합니다. 

* 다운로드할 데이터 범위. 기본값은 현재 UTC 날짜입니다. 
* 전체 계정의 사용 가능한 이벤트를 포함시킬지, 또는 현재 영역의 이벤트만 포함시킬지에 대한 정보. 기본적으로 사용자는 로그인되어 있는 영역의 이벤트를 가져옵니다. 
* 이벤트를 다운로드하는 데 필요한 세션 ID. 
* 세션을 작성하는 사용자 ID. 

예를 들면, 다음과 같습니다. 

```
$ bx cf at session create 
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| username     | xxx@yyy.com                               |
| create-time  | 2017-07-25T10:29:28.541092735Z            |
| access-time  | 2017-07-25T10:29:28.541092735Z            |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
| id           | 32c657c5-31c0-4a3c-a139-b380871c737a      |
| space        | 66fe4565-abab-46c9-cdcd-qf4565342345      |
+--------------+-------------------------------------------+
```
{: screen}

**팁:** 활성 세션의 목록을 보려면 명령 [cf at session list](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_list)를 실행하십시오. 

예를 들면, 다음과 같습니다. 

```
bx cf at session list
+--------------------------------------+--------------------------------------+---------------------+--------------------------------+--------------------------------+
| Id                                   | Space                                |Username             | Create-time                    | Access-time                    |
+--------------------------------------+--------------------------------------+---------------------+--------------------------------+--------------------------------+
| 32c657c5-31c0-4a3c-a139-b380871c737a | 66fe4565-abab-46c9-cdcd-qf4565342345 |xxx@yyy.com          | 2017-07-25T10:29:28.541092735Z | 2017-07-25T10:29:28.541092735Z |
+--------------------------------------+--------------------------------------+---------------------+--------------------------------+--------------------------------+
```
{: screen} 


## 4단계: 파일에 이벤트 다운로드
{: #step4}

세션 매개변수로 지정된 이벤트를 다운로드하려면 다음 명령을 실행하십시오. 

```
bx cf at download -o Events_File_Name Session_ID
```
{: codeblock}

여기서,


* Events_File_Name은 출력 파일의 이름입니다. 
* Session_ID는 세션의 GUID입니다. 이 값은 이전 단계에서 얻을 수 있습니다. 이 값을 필드 **Id**에 사용하십시오. 

예를 들면, 다음과 같습니다. 

```
bx cf at download -o Events_File_Name.log 32c657c5-31c0-4a3c-a139-b380871c737a
 29.89 KiB / 12.19 KiB [================================] 245.14% 9.73 MiB/s 0s
Download completed successfully
```
{: screen}

진행 표시기는 이벤트가 다운로드됨에 따라 0에서 100% 로 이동합니다. 

**참고:** 

* 다운로드된 데이터의 형식은 압축 JSON입니다. 예를 들어, Linux 시스템에서 이벤트를 다운로드한 경우에는 .gz 파일의 압축을 풀고 이벤트를 열어 데이터를 JSON 형식으로 보십시오.  
* 압축된 JSON은 ElasticSearch 또는 Logstash를 통해 수집할 수 있습니다. 예를 들어, -o가 지정되지 않았으며 Linux 시스템에서 작업 중인 경우, 데이터는 사용자가 Elastic 스택으로 바로 전달할 수 있도록 표준 출력으로 스트리밍됩니다. 
* 사용자는 JSON을 구문 분석할 수 있는 그 외의 프로그램을 사용하여 데이터를 처리할 수도 있습니다.  

## 4단계: 세션 삭제

다운로드가 완료된 후에는 [cf at session delete](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_delete) 명령을 사용하여 세션을 삭제해야 합니다.  

세션을 삭제하려면 다음 명령을 실행하십시오. 

```
bx cf at session delete Session_ID
```
{: codeblock}

여기서 Session_ID는 이전 단계에서 작성한 세션의 GUID입니다. 이 값을 필드 **Id**에 사용하십시오. 

예를 들면, 다음과 같습니다. 

```
bx cf at session delete 32c657c5-31c0-4a3c-a139-b380871c737a
+---------+------------------------+
| Name    | Value                  |
+---------+------------------------+
| message | Delete session success |
+---------+------------------------+
```
{: screen}




