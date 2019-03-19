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


# 이벤트 다운로드
{: #downloading_events}

이벤트를 로컬 파일로 다운로드할 수 있습니다. 사용자는 세션의 컨텍스트 내에서 이벤트를 다운로드합니다. 세션은 다운로드될 이벤트를 지정합니다. 다운로드가 완료된 후에는 세션을 삭제해야 합니다.
{:shortdesc}

이벤트를 로컬 파일로 다운로드하려면 다음 단계를 완료하십시오.

## 1단계: {{site.data.keyword.cloud_notm}}에 로그인
{: #prereq}

{{site.data.keyword.cloud_notm}}에 로그인하십시오. 다음 단계를 완료하십시오.

1. [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) 명령을 실행하여 {{site.data.keyword.cloud_notm}}에 로그인하십시오.
2. [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) 명령을 실행하여 {{site.data.keyword.cloudaccesstrailshort}} 서비스를 프로비저닝할 조직 및 영역을 설정하십시오.

**참고:** {{site.data.keyword.cloudaccesstrailshort}}이 프로비저닝된 조직 및 영역을 설정하십시오.

## 2단계: 사용할 수 있는 이벤트 식별
{: #step2}

`ibmcloud at status` 명령을 사용하여 영역 도메인에 있는 이벤트에 대한 정보를 보십시오.

* 영역 도메인에 있는 이벤트에 대한 정보를 가져오려면 `ibmcloud at status` 명령을 실행하십시오.
* 계정 도메인에 있는 이벤트에 대한 정보를 가져오려면 `ibmcloud at status` 명령을 옵션 `-a`와 함께 실행하십시오.

자세한 정보는 [이벤트 정보 보기](/docs/services/cloud-activity-tracker/how-to/viewing_event_information.html#viewing_event_status)를 참조하십시오.
  


## 3단계: 세션 작성
{: #step3}

다운로드 가능한 이벤트 데이터의 범위를 정의하고 다운로드의 상태를 보존하려면 세션이 필요합니다. 

세션을 작성하려면 `ibmcloud at session create` 명령을 사용하십시오. 기본적으로 세션은 최근 2주 동안의 데이터를 포함합니다.  세션을 작성할 때는 선택적으로 시작 날짜 및 종료 날짜를 지정하여 시간 범위, 특정 시간 및 이벤트 범위를 지정할 수 있습니다. 

**참고:** 

* 시작 날짜와 종료 날짜를 지정하는 경우, 세션은 이러한 날짜 범위(경계값 포함)에 속한 이벤트에 대해 액세스를 제공합니다. 
* 각 세션에 대해 2주 분량보다 많은 데이터는 다운로드할 수 없습니다. 따라서 시간 범위는 2주 미만이어야 합니다.
* 지역 내 영역 도메인 또는 계정 도메인의 이벤트를 다운로드할 수 있습니다.

특정 날짜의 이벤트를 다운로드하는 데 사용되는 세션을 작성하려면 다음 명령을 실행하십시오.

```
ibmcloud at session create -s 2017-07-25 -e 2017-07-25
```
{: codeblock}

이 세션은 다음 정보를 리턴합니다.

* 다운로드할 날짜 범위.
* 전체 계정의 사용 가능한 이벤트를 포함시킬지, 또는 현재 영역의 이벤트만 포함시킬지에 대한 정보. 기본적으로 사용자는 로그인되어 있는 영역의 이벤트를 가져옵니다.
* 이벤트를 다운로드하는 데 필요한 세션 ID.
* 세션을 작성하는 사용자 ID.

예를 들면, 다음과 같습니다.

```
$ ibmcloud at session create 
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

**팁:** 활성 세션의 목록을 보려면 `ibmcloud at session list` 명령을 실행하십시오.

예를 들면, 다음과 같습니다.

```
ibmcloud at session list
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
ibmcloud at download -o Events_File_Name Session_ID
```
{: codeblock}

여기서,

* Events_File_Name은 출력 파일의 이름입니다.
* Session_ID는 세션의 GUID입니다. 이 값은 이전 단계에서 얻을 수 있습니다. 이 값을 필드 **Id**에 사용하십시오.

예를 들면, 다음과 같습니다.

```
ibmcloud at download -o Events_File_Name.log 32c657c5-31c0-4a3c-a139-b380871c737a
 29.89 KiB / 12.19 KiB [================================] 245.14% 9.73 MiB/s 0s
Download completed successfully
```
{: screen}

진행 표시기는 이벤트가 다운로드됨에 따라 0에서 100% 로 이동합니다.

**참고:** 

* 다운로드된 데이터의 형식은 압축된 JSON입니다. 예를 들어, Linux 시스템에서 이벤트를 다운로드한 경우에는 .gz 파일의 압축을 풀고 이벤트를 열어 데이터를 JSON 형식으로 보십시오. 
* 압축된 JSON은 ElasticSearch 또는 Logstash를 통해 수집할 수 있습니다. 예를 들어, -o가 지정되지 않았으며 Linux 시스템에서 작업 중인 경우, 데이터는 사용자가 Elastic 스택으로 바로 전달할 수 있도록 표준 출력으로 스트리밍됩니다.
* 사용자는 JSON을 구문 분석할 수 있는 그 외의 프로그램을 사용하여 데이터를 처리할 수도 있습니다. 

## 4단계: 세션 삭제

다운로드가 완료된 후에는 `ibmcloud at session delete` 명령을 사용하여 세션을 삭제해야 합니다. 

세션을 삭제하려면 다음 명령을 실행하십시오.

```
ibmcloud at session delete Session_ID
```
{: codeblock}

여기서 Session_ID는 이전 단계에서 작성한 세션의 GUID입니다. 이 값을 필드 **Id**에 사용하십시오.

예를 들면, 다음과 같습니다.

```
ibmcloud at session delete 32c657c5-31c0-4a3c-a139-b380871c737a
+---------+------------------------+
| Name    | Value                  |
+---------+------------------------+
| message | Delete session success |
+---------+------------------------+
```
{: screen}




