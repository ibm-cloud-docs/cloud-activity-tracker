---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, manage events, tutorial

subcollection: cloud-activity-tracker

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}
{:important: .important}
{:note: .note}


# Activity Tracker CLI를 사용한 이벤트 관리
{: #tutorial2}

이 튜토리얼을 통해 명령행으로 이벤트를 관리하기 위해 {{site.data.keyword.cloudaccesstrailshort}} CLI를 사용하는 방법에 대해 알아보십시오. 저장된 이벤트에 대한 정보를 가져오는 방법, {{site.data.keyword.IBM_notm}} 클라우드에 저장된 이벤트를 다운로드하는 방법, 또는 이벤트를 삭제하는 방법을 알아보십시오.
{:shortdesc}

다음 단계를 완료하십시오.

1. [{{site.data.keyword.keymanagementservicelong_notm}} 프로비저닝 및 이벤트 생성](/docs/services/cloud-activity-tracker/tutorials?topic=cloud-activity-tracker-tutorial2#tutorial2_step1)
2. [저장된 이벤트에 대한 정보 가져오기(ibmcloud at status)](/docs/services/cloud-activity-tracker/tutorials?topic=cloud-activity-tracker-tutorial2#tutorial2_step2)
2. [세션을 작성하여 다운로드할 로그 지정(ibmcloud at session create)](/docs/services/cloud-activity-tracker/tutorials?topic=cloud-activity-tracker-tutorial2#tutorial2_step3)
3. [실제 로그 데이터 가져오기(ibmcloud at download)](/docs/services/cloud-activity-tracker/tutorials?topic=cloud-activity-tracker-tutorial2#tutorial2_step4)
4. [다운로드 완료 후 세션 삭제(ibmcloud at session delete)](/docs/services/cloud-activity-tracker/tutorials?topic=cloud-activity-tracker-tutorial2#tutorial2_step5)
5. [필요하지 않은 로그의 수동 삭제(ibmcloud at delete)](/docs/services/cloud-activity-tracker/tutorials?topic=cloud-activity-tracker-tutorial2#tutorial2_step6)


## 가정
{: #tutorial2_assumptions}

1. {{site.data.keyword.cloudaccesstrailshort}} 서비스가 프로비저닝된 {{site.data.keyword.cloud_notm}} 계정의 영역에서 작업할 수 있는 `개발자` 권한을 가진 {{site.data.keyword.cloud_notm}} 사용자 ID가 있습니다.  

    {{site.data.keyword.cloudaccesstrailshort}} 서비스를 프로비저닝하는 방법에 대한 자세한 정보는 [{{site.data.keyword.cloudaccesstrailshort}} 서비스 프로비저닝](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-provision#provision)을 참조하십시오.

2. 프리미엄 플랜을 사용하여 {{site.data.keyword.cloudaccesstrailshort}} 서비스의 인스턴스를 프로비저닝했습니다.

    **참고:** {{site.data.keyword.cloudaccesstrailshort}} CLI는 `Lite` 플랜에서 사용할 수 없습니다.

3. {{site.data.keyword.cloudaccesstrailshort}} CLI를 로컬 시스템에 설치했습니다. CLI가 명령행을 통해 이벤트를 관리해야 합니다. 

    {{site.data.keyword.cloudaccesstrailshort}} CLI 설치에 대한 자세한 정보는 [{{site.data.keyword.cloudaccesstrailshort}} CLI 구성](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-config_cli#config_cli)을 참조하십시오.

4. 명령행을 통해 {{site.data.keyword.cloud_notm}}에 로그인했습니다. 이 튜토리얼을 위해서는 다음 명령을 터미널에서 실행하십시오. 

    `ibmcloud login -a api.ng.bluemix.net`을 실행하여 미국 남부 지역에 로그인하십시오. 자세한 정보는 [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login)을 참조하십시오.
    
    `ibmcloud target -o OrgName -s SpaceName`을 실행하여 {{site.data.keyword.cloudaccesstrailshort}} 서비스가 프로비저닝되는 대상 조직 및 영역을 설정하십시오. 자세한 정보는 [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target)을 참조하십시오.


## 1단계. IBM Key Protect 서비스 프로비저닝 및 이벤트 생성 
{: #tutorial2_step1}
	
다음 단계를 완료하여 {{site.data.keyword.keymanagementserviceshort}} 서비스를 {{site.data.keyword.cloud_notm}}에 프로비저닝하고 이벤트를 생성하십시오.

1. {{site.data.keyword.keymanagementserviceshort}} 서비스의 인스턴스를 미국 남부 지역에 프로비저닝하십시오. 자세한 정보는 [IBM Cloud 콘솔에서 프로비저닝](/docs/services/key-protect?topic=key-protect-provision#provision)을 참조하십시오.

2. 키에 대해 작업하는 데 사용할 사용자의 {{site.data.keyword.cloud_notm}} 권한을 정의하십시오. 

    * 사용자가 키를 작성하려면 서비스 역할이 *관리자* 또는 *작성자*로 설정된 IAM 정책이 필요합니다.
	* 사용자가 키를 삭제하려면 서비스 역할이 *관리자*로 설정된 IAM 정책이 필요합니다.
	* 사용자가 키를 보려면 서비스 역할이 *독자*로 설정된 IAM 정책이 필요합니다. 

3. {{site.data.keyword.cloudaccesstrailshort}} 이벤트 데이터를 생성하기 위해 {{site.data.keyword.keymanagementserviceshort}} 서비스를 사용하여 보안 키를 작성하십시오. 자세한 정보는 [새 키 작성](/docs/services/key-protect?topic=key-protect-create-standard-keys#create-standard-keys)을 참조하십시오.

키를 작성하면 {{site.data.keyword.cloudaccesstrailshort}} 이벤트가 생성됩니다.

## 2단계. 저장된 이벤트에 대한 정보 가져오기
{: #tutorial2_step2}

{{site.data.keyword.keymanagementserviceshort}} 이벤트는 {{site.data.keyword.cloudaccesstrailshort}} 계정 도메인에 있습니다.

이 튜토리얼에서 {{site.data.keyword.keymanagementserviceshort}} 이벤트는 {{site.data.keyword.keymanagementserviceshort}} 서비스를 프로비저닝한 미국 남부 계정 도메인에 있습니다. 

다음 명령을 실행하여 특정 날짜에 수집된 이벤트에 대한 정보를 가져오십시오.

```
ibmcloud at status -s startDate -e endDate -a
```
{: codeblock}

여기서, 

* `-s`는 시작일을 설정하는 데 사용됩니다. 
* `startDate`는 시작 날짜를 나타냅니다. 형식은 *YYYY-MM-DD*입니다.
* `-e`는 종료 날짜를 설정하는 데 사용됩니다.
* `endDate`는 종료 날짜를 나타냅니다. 형식은 *YYYY-MM-DD*입니다.
* `-a`는 계정 도메인의 이벤트를 포함하도록 표시하는 데 사용됩니다.

예를 들면, 다음과 같습니다.

```
ibmcloud at status -s 2017-07-25 -e 2017-07-25 -a
+------------+-------+-------+------------+
| Date       | Count | Size  | Searchable |
+------------+-------+-------+------------+
| 2017-07-25 | 12    | 34994 | All        |
+------------+-------+-------+------------+
```
{: screen}

이 명령은 2017년 6월 25일의 이벤트 수를 카운트합니다. {{site.data.keyword.cloudaccesstrailshort}}는 글로벌 서비스입니다. 따라서 날짜는 협정 표준 세계시입니다. 로컬 시간의 전체 일을 가져오려면, 여러 UTC 일을 다운로드해야 할 수 있습니다.




## 3단계. 다운로드할 이벤트 지정
{: #tutorial2_step3}

이벤트 다운로드를 시작하기 전에 세션을 작성하십시오. 세션은 다운로드할 이벤트를 지정합니다.


세션을 작성하려면 다음 명령을 사용하십시오.

```
ibmcloud at session create -s startDate -e endDate -a
```
{: codeblock}

여기서, 

* `-s`는 시작일을 설정하는 데 사용됩니다. 
* `startDate`는 시작 날짜를 나타냅니다. 형식은 *YYYY-MM-DD*입니다.
* `-e`는 종료 날짜를 설정하는 데 사용됩니다.
* `endDate`는 종료 날짜를 나타냅니다. 형식은 *YYYY-MM-DD*입니다.
* `-a`는 계정 도메인의 이벤트를 포함하도록 표시하는 데 사용됩니다.

예를 들면, 다음과 같습니다. 

```
ibmcloud at session create -s 2017-07-25 -e 2017-07-25 -a
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| id           | 21b19aeb-3d32-4c60-b912-517609c62db2      |
| space        | 667fb895-b5f5-46c9-9f0e-cf4587341095      |
| username     | xxx@yyy.com                               |
| create-time  | 2017-07-25T18:33:22.678350874Z            |
| access-time  | 2017-07-25T18:33:22.678350874Z            |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
+--------------+-------------------------------------------+
```
{: screen}

여기서, 

* `-s`는 시작일을 설정하는 데 사용됩니다.
* `-e`는 종료 날짜를 설정하는 데 사용됩니다.
* `-a`는 계정 도메인의 이벤트를 포함하도록 표시하는 데 사용됩니다.

세션에는 연관된 시작 날짜 및 종료 날짜가 있습니다. 다운로드 명령은 이러한 날짜 범위(경계값 포함)에 속하는 이벤트를 포함합니다.

이 명령 출력의 중요한 부분은 세션 `Id`입니다. 이는 다운로드 명령에서 참조됩니다.

기존 세션에 대한 정보를 가져오려면 `ibmcloud at session list`를 입력하십시오.

세션 및 `ibmcloud at session create` 명령에 대해 자세히 알아보려면 [CLI 참조](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-at_cli_cloud#session_create)를 참조하십시오.

명령행에서 도움말을 보려면 `ibmcloud at session help create`를 사용하십시오.

## 4단계. 세션에 정의된 범위로 식별된 이벤트 다운로드
{: #tutorial2_step4}

세션 매개변수로 지정된 이벤트를 다운로드하려면 다음 명령을 실행하십시오.

```
ibmcloud at download -o outputFile sessionID
```
{: codeblock}

* `-o` 매개변수는 출력 파일을 지정합니다.
* `outputFile`은 로컬 파일의 이름입니다.
* `sessionID`는 마지막에 지정됩니다. 세션 ID 값은 `ibmcloud at session create` 명령의 출력에서 가져옵니다.

다운로드된 데이터의 형식은 압축된 JSON입니다. 

예를 들면, 다음과 같습니다.

```
$ ibmcloud at download -o events.log 21b19aeb-3d32-4c60-b912-517609c62db2
 6.70 KiB / 3.06 KiB [================================================================================================================================================================] 219.03% 8.60 MiB/s 0s
Download Successful
```
{: screen} 

진행 표시기는 이벤트가 다운로드됨에 따라 0에서 100% 로 이동합니다.

`ibmcloud at download` 명령에 대해 자세히 알아보려면 [CLI 참조](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-at_cli_cloud#download)를 참조하십시오.

명령행에서 도움말을 보려면 `ibmcloud at help download`를 사용하십시오.

## 5단계. 세션 삭제
{: #tutorial2_step5}

다운로드가 완료된 후에는 세션을 삭제하십시오. 다음 명령을 실행하십시오.

```
ibmcloud at session delete sessionID
```
{: codeblock}

여기서, 

* `sessionID`는 삭제할 세션의 ID입니다.

세션의 수는 제한되어 있습니다. 세션은 자동으로 삭제되지 않습니다. 사용자는 필요하지 않은 세션을 수동으로 삭제해야 합니다. 

예를 들면, 다음과 같습니다. 

```
$ ibmcloud at session delete 21b19aeb-3d32-4c60-b912-517609c62db2
+---------+------------------------+
| name    | value                  |
+---------+------------------------+
| message | Delete session success |
+---------+------------------------+
```
{: screen}

`ibmcloud at session delete` 명령에 대해 자세히 알아보려면 [CLI 참조](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-at_cli_cloud#session_delete)를 참조하십시오.

명령행에서 도움말을 보려면 `ibmcloud at session help delete`를 사용하십시오.

## 6단계. Activity Tracker에서 이벤트를 수동으로 삭제
{: #tutorial2_step6}

{{site.data.keyword.cloudaccesstrailshort}}에서 고유 이벤트 보존을 제어할 수 있습니다. 사용자는 이벤트를 수동으로 삭제하거나, 이벤트 삭제를 자동화할 수 있습니다.

영역에서 이벤트를 수동으로 삭제하려면 `ibmcloud at delete` 명령을 실행하십시오. 예를 들면, 다음과 같습니다.

```
$ ibmcloud at delete -s 2017-07-25 -e 2017-07-25
Deleted successfully
"6 logs were deleted,freeing 13737 bytes."
```
{: screen}

`ibmcloud at delete` 명령에 대해 자세히 알아보려면 [CLI 참조](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-at_cli_cloud#delete)를 참조하십시오.

명령행에서 도움말을 보려면 `ibmcloud at help delete`를 사용하십시오.

**참고:** 이벤트를 자동으로 삭제하려는 경우에는 CLI 명령 `ibmcloud at option`을 사용하여 보존 정책을 설정할 수 있습니다. 자세한 정보는 [CLI 참조](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-at_cli_cloud#option)를 참조하십시오.


