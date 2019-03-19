---

copyright:
  years: 2016, 2019
lastupdated: "2019-02-18"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# 이벤트 삭제
{: #deleting_events}

{{site.data.keyword.cloudaccesstrailshort}}에 저장된 이벤트를 수동으로 삭제하려면 *ibmcloud at delete* 명령을 사용하십시오.
{:shortdesc}

다음 단계를 완료하십시오.

## 1단계: {{site.data.keyword.cloud_notm}}에 로그인
{: #deleting_events_prereq}

{{site.data.keyword.cloud_notm}}에 로그인하십시오. 다음 단계를 완료하십시오.

1. [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) 명령을 실행하여 {{site.data.keyword.cloud_notm}}에 로그인하십시오.
2. [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) 명령을 실행하여 {{site.data.keyword.cloudaccesstrailshort}} 서비스를 프로비저닝할 조직 및 영역을 설정하십시오.

**참고:** {{site.data.keyword.cloudaccesstrailshort}}이 프로비저닝된 조직 및 영역을 설정하십시오.

## 2단계: 사용할 수 있는 이벤트 식별
{: #deleting_events_step2}

`ibmcloud at status` 명령을 사용하여 영역 도메인에 있는 이벤트에 대한 정보를 보십시오.

* 영역 도메인에 있는 이벤트에 대한 정보를 가져오려면 `ibmcloud at status` 명령을 실행하십시오.
* 계정 도메인에 있는 이벤트에 대한 정보를 가져오려면 `ibmcloud at status` 명령을 옵션 `-a`와 함께 실행하십시오.

자세한 정보는 [이벤트 정보 보기](/docs/services/cloud-activity-tracker/how-to/viewing_event_information.html#viewing_event_status)를 참조하십시오.
	
  
## 3단계: 이벤트 삭제
{: #deleting_events_step3}
	
이벤트를 삭제하려면 `ibmcloud at delete` 명령을 실행하십시오.

```
ibmcloud at delete -s YYYY-MM-DD -e YYYY-MM-DD 
```
{: codeblock}
    
여기서,

* *-s*는 UTC(협정 세계 표준시) 형식(*YYYY-MM-DD*)으로 시작 날짜를 설정하는 데 사용됩니다.
* *-e*는 UTC(협정 세계 표준시) 형식(*YYYY-MM-DD*)으로 종료 날짜를 설정하는 데 사용됩니다.

예를 들어, 2017년 6월 10일의 이벤트를 삭제하려면 다음 명령을 실행하십시오.

```
ibmcloud at delete -s 2017-06-10 -e 2017-06-10
```
{: screen}

삭제된 이벤트 레코드에 대한 정보를 수신합니다.










