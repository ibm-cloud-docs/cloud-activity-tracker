---

copyright:
  years: 2016, 2018
lastupdated: "2018-09-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# 이벤트 정보 보기
{: #viewing_event_status}

{{site.data.keyword.Bluemix}} 영역에 대해 {{site.data.keyword.cloudaccesstrailshort}}에 수집되어 저장된 이벤트에 대한 정보를 얻으려면 `ibmcloud at status` 명령을 사용하십시오.
{:shortdesc}

이벤트 로그의 크기, 레코드 수, Kibana에서의 이벤트 분석 가능 여부에 대한 정보를 가져올 수 있습니다.  

이벤트 로그에 대한 정보를 보려면 다음 단계를 완료하십시오. 

## 1단계: {{site.data.keyword.Bluemix_notm}}에 로그인
{: #prereq}

{{site.data.keyword.Bluemix_notm}}에 로그인하십시오. 다음 단계를 완료하십시오.

1. [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) 명령을 실행하여 {{site.data.keyword.Bluemix_notm}}에 로그인하십시오. 
2. [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) 명령을 실행하여 {{site.data.keyword.cloudaccesstrailshort}} 서비스를 프로비저닝할 조직 및 영역을 설정하십시오. 

**참고:** {{site.data.keyword.cloudaccesstrailshort}}이 프로비저닝된 조직 및 영역을 설정하십시오. 

## 2단계: 사용할 수 있는 이벤트 식별
{: #step2}

`ibmcloud at status` 명령을 사용하여 영역 도메인에 있는 이벤트에 대한 정보를 보십시오. 

* 영역 도메인에 있는 이벤트에 대한 정보를 가져오려면 `ibmcloud at status` 명령을 실행하십시오. 
* 계정 도메인에 있는 이벤트에 대한 정보를 가져오려면 `ibmcloud at status` 명령을 옵션 `-a`와 함께 실행하십시오. 

```
$ ibmcloud at status -a -s YYYY-MM-DD -e YYYY-MM-DD 
```
{: codeblock}
    
여기서,
    
* *-a*는 요청을 계정 도메인에 적용하도록 지정하는 데 사용됩니다. 
* *-s*는 UTC(협정 세계 표준시) 형식(*YYYY-MM-DD*)으로 시작 날짜를 설정하는 데 사용됩니다.
* *-e*는 UTC(협정 세계 표준시) 형식(*YYYY-MM-DD*)으로 종료 날짜를 설정하는 데 사용됩니다.

예를 들어, 영역 도메인에 있는 최근 2주일 동안의 이벤트를 보려면 다음 명령을 실행하십시오. 

```
$ ibmcloud at status
```
{: codeblock}
    
예를 들면, 이 명령 실행의 출력은 다음과 같습니다.
    
```
+------------+--------+------------+
|    DATE    |  COUNT | SEARCHABLE |
+------------+--------+------------+
| 2017-07-24 |    16  |    None    |
+------------+--------+------------+
| 2017-07-25 |   1224 |    All     |
+------------+--------+------------+
```
{: screen}

**참고:** {{site.data.keyword.cloudaccesstrailshort}} 서비스는 UTC(협정 세계 표준시)를 사용하는 글로벌 서비스입니다. 일은 UTC 일로 정의됩니다. 특정 로컬 시간 일의 이벤트를 가져오는 경우에는 여러 UTC 일을 다운로드해야 할 수 있습니다.
	














