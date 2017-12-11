---

copyright:
  years: 2016, 2017

lastupdated: "2017-09-07"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# Activity Tracker CLI를 사용한 이벤트 관리
{: #tutorial2}

이 튜토리얼을 통해 명령행으로 이벤트를 관리하기 위해 {{site.data.keyword.cloudaccesstrailshort}} CLI를 사용하는 방법에 대해 알아보십시오. 저장된 이벤트에 대한 정보를 가져오는 방법, {{site.data.keyword.IBM_notm}} 클라우드에 저장된 이벤트를 다운로드하는 방법, 또는 이벤트를 삭제하는 방법을 알아보십시오.
{:shortdesc}

다음 단계를 완료하십시오. 

1. [{{site.data.keyword.IBM_notm}} Key Protect 서비스 프로비저닝 및 이벤트 생성](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step1)
2. [저장된 이벤트에 대한 정보 가져오기(cf at status)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step2)
2. [세션을 작성하여 다운로드할 로그 지정(cf at session create)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step3)
3. [실제 로그 데이터 가져오기(cf at download)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step4)
4. [다운로드 완료 후 세션 삭제(cf at session delete)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step5)
5. [필요하지 않은 로그의 수동 삭제(cf at delete)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step6)


## 가정
{: #assumptions}

1. {{site.data.keyword.IBM_notm}} Cloud {{site.data.keyword.cloudaccesstrailshort}} 서비스가 프로비저닝되는 {{site.data.keyword.Bluemix_notm}} 계정의 영역에서 작업할 수 있는 개발자 권한을 가진 {{site.data.keyword.Bluemix_notm}} 사용자 ID가 있습니다.  

    {{site.data.keyword.cloudaccesstrailshort}} 서비스를 프로비저닝하는 방법에 대한 자세한 정보는 [{{site.data.keyword.cloudaccesstrailshort}} 서비스 프로비저닝](/docs/services/cloud-activity-tracker/how-to/provision.html#provision)을 참조하십시오. 

2. 로컬 시스템에 {{site.data.keyword.cloudaccesstrailshort}} CF 플러그인이 설치되어 있습니다. 명령행을 통해 이벤트를 관리하는 데 {{site.data.keyword.cloudaccesstrailshort}} CLI를 사용하려면 이 플러그인이 필요합니다.  

    {{site.data.keyword.cloudaccesstrailshort}} CF 플러그인 설치에 대한 자세한 정보는 [{{site.data.keyword.cloudaccesstrailshort}} CLI 구성](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#config_at_cli)을 참조하십시오. 

3. 다음 명령을 사용하여 명령행을 통해 {{site.data.keyword.Bluemix_notm}}에 로그인되었습니다. 

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

    예를 들어, 미국 남부 지역에 로그인하려면 다음 명령을 실행하십시오. 
	
	```
	bx cf login -a api.ng.bluemix.net
	```
	{: codeblock}

	**참고:** 사용자는 명령행을 통해 {{site.data.keyword.cloudaccesstrailshort}} 명령을 실행하고 이벤트를 관리할 수 있으려면 {{site.data.keyword.cloudaccesstrailshort}} 서비스가 프로비저닝된 {{site.data.keyword.Bluemix_notm}}의 지역, 조직 및 영역에 로그인해야 합니다. 
	
	그런 다음 조직 및 영역을 설정하십시오. 다음 명령을 실행하십시오. 

    ```
    bx target -o OrgName -s SpaceName
    ```
    {: codeblock}

    여기서,


    * OrgName은 조직의 이름입니다. 
    * SpaceName은 영역의 이름입니다. 


## 1단계: IBM Key Protect 서비스 프로비저닝 및 이벤트 생성 
{: #step1}
	
1. {{site.data.keyword.keymanagementserviceshort}}의 인스턴스를 {{site.data.keyword.Bluemix_notm}}에서 프로비저닝하려면 다음 단계를 완료하십시오. 

    1. {{site.data.keyword.Bluemix_notm}} 계정에 로그인하십시오. 

        {{site.data.keyword.Bluemix_notm}} 대시보드는 [http://bluemix.net](http://bluemix.net)에 있습니다. 

        사용자 ID 및 비밀번호를 사용하여 로그인하면 {{site.data.keyword.Bluemix_notm}} UI가 열립니다. 

    2. **카탈로그**를 클릭하십시오. {{site.data.keyword.Bluemix_notm}}에서 사용 가능한 서비스의 목록이 열립니다. 

        **보안** 카테고리를 선택하여 표시되는 서비스의 목록을 필터링하십시오. 

    3. **Key Protect** 타일을 선택하십시오. 

    4. **작성**을 클릭하여 로그인되어 있는 {{site.data.keyword.Bluemix_notm}} 영역에서 {{site.data.keyword.keymanagementserviceshort}} 서비스를 프로비저닝하십시오. 

2. {{site.data.keyword.cloudaccesstrailshort}} 이벤트를 생성하려면 다음 단계를 완료하십시오. 

    1. {{site.data.keyword.Bluemix_notm}} 대시보드에서 {{site.data.keyword.keymanagementserviceshort}} 서비스를 선택하십시오. {{site.data.keyword.keymanagementserviceshort}} 대시보드가 열립니다. 그런 다음 **관리** 탭을 선택하십시오. 

    2. **키 추가**를 클릭하십시오. 새 창이 열립니다. 

        ![{{site.data.keyword.keymanagementserviceshort}} 창(키 추가를 위한 창)](images/KP_f2.gif)

    3. **키 생성**을 선택하고 다음 단계를 완료하십시오. 

        * *MyFirstKey*와 같이 키의 이름을 입력하십시오. 

        * 키의 알고리즘을 선택하십시오. 

        * **키 추가**를 클릭하십시오.  

3. 이벤트가 작성되었는지 확인하십시오. 

    1. {{site.data.keyword.Bluemix_notm}} 대시보드에서 {{site.data.keyword.cloudaccesstrailshort}} 서비스를 선택하십시오. 서비스 대시보드가 열립니다. 

    2. 서비스를 프로비저닝하고 키를 추가했을 때 생성된 {{site.data.keyword.keymanagementserviceshort}} 이벤트를 검색하도록 보기를 구성하십시오. 

        * *로그 보기* 필드에서 **영역 로그**를 선택하십시오. 
	    * *검색 필드* 필드에서 **target.name**을 선택하십시오. 
	    * *필터* 필드에 **ibm-key-protect**를 입력하십시오. 
	
	    표시되는 데이터는 최근 24시간 동안 사용 가능한 {{site.data.keyword.keymanagementserviceshort}} 이벤트에 해당합니다.  

	    ![{{site.data.keyword.cloudaccesstrailshort}} 관리 탭](images/KP_f3.gif)

## 2단계: 저장된 이벤트에 대한 정보 가져오기
{: #step2}

다운로드할 수 있는 이벤트를 확인하십시오. 예를 들어, 현재 날짜에 프로비저닝하고 키를 추가한 경우 오늘 수집된 이벤트에 대한 정보를 가져오려면 다음 명령을 실행하십시오. 

```
bx cf at status -s 2017-07-25 -e 2017-07-25
+------------+-------+-------+------------+
| Date       | Count | Size  | Searchable |
+------------+-------+-------+------------+
| 2017-07-25 | 12    | 34994 | All        |
+------------+-------+-------+------------+
```
{: screen}

이 명령은 2017년 6월 25일의 이벤트 수를 카운트합니다. {{site.data.keyword.cloudaccesstrailshort}}은 글로벌 서비스이므로 날짜는 협정 표준 세계시입니다. 로컬 시간의 전체 일을 가져오려면, 여러 UTC 일을 다운로드해야 할 수 있습니다. 

여러 날에 대한 정보를 보려면 `-s`를 사용하여 시작 일을 설정하고 `-e`를 설정하여 종료 일을 설정하십시오.  

`cf at status` 명령에 대해 자세히 알아보려면 [CLI 참조](/docs/services/cloud-activity-tracker/cli/at_cli.html#status)를 참조하십시오. 

명령행에서 도움말을 보려면 `bx cf at help status`를 사용하십시오. 

## 3단계: 다운로드할 이벤트 지정
{: #step3}

이벤트를 다운로드하려면 먼저 세션을 작성하십시오. 

* 세션은 다운로드할 이벤트를 지정합니다. 
* 이벤트 다운로드가 인터럽트되는 경우, 세션을 통해 중단된 위치에서 다운로드를 재개할 수 있습니다. 

세션을 작성하려면 다음 명령을 사용하십시오. 

```
bx cf at session create -s 2017-07-25 -e 2017-07-25
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

세션에 연관된 시작 날짜 및 종료 날짜가 있습니다. 다운로드 명령은 이러한 날짜 범위(경계값 포함)에 속하는 이벤트를 포함합니다. 기본 날짜 범위는 현재 날짜입니다.  

이 명령 출력의 중요한 부분은 세션 `Id`입니다. 이는 다운로드 명령에서 참조됩니다. 

기존 세션에 대한 정보를 가져오려면 `cf at session list`를 입력하십시오. 

세션 및 `cf at session create` 명령에 대해 자세히 알아보려면 [CLI 참조](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_create)를 참조하십시오. 

명령행에서 도움말을 보려면 `cf at session help create`를 사용하십시오. 

## 4단계: 세션에 정의된 범위로 식별된 이벤트 다운로드
{: #step4}

세션 매개변수로 지정된 이벤트를 다운로드하려면 다음 명령을 실행하십시오. 

```
$ bx cf at events download -o events.log 21b19aeb-3d32-4c60-b912-517609c62db2
 6.70 KiB / 3.06 KiB [================================================================================================================================================================] 219.03% 8.60 MiB/s 0s
Download Successful
```

* `-o` 매개변수는 출력 파일을 지정합니다. 
* 세션 ID는 마지막에 지정됩니다. 세션 ID 값은 `cf at session create` 명령의 출력에서 가져옵니다. 
* 진행 표시기는 이벤트가 다운로드됨에 따라 0에서 100% 로 이동합니다. 

다운로드된 데이터의 형식은 압축된 JSON입니다.  

`cf at download` 명령에 대해 자세히 알아보려면 [CLI 참조](/docs/services/cloud-activity-tracker/cli/at_cli.html#download)를 참조하십시오. 

명령행에서 도움말을 보려면 `bx cf at help download`를 사용하십시오. 

## 5단계: 세션 삭제
{: #step5}

다운로드가 완료된 후에는 세션을 삭제하십시오.  

세션의 수는 제한되어 있습니다. 세션은 자동으로 삭제되지 않습니다. 사용자는 필요하지 않은 세션을 수동으로 삭제해야 합니다.  

```
$ bx cf at session delete 21b19aeb-3d32-4c60-b912-517609c62db2
+---------+------------------------+
| name    | value                  |
+---------+------------------------+
| message | Delete session success |
+---------+------------------------+
```

`cf at session delete` 명령에 대해 자세히 알아보려면 [CLI 참조](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_delete)를 참조하십시오. 

명령행에서 도움말을 보려면 `bx cf at session help delete`를 사용하십시오. 

## 6단계: Activity Tracker에서 이벤트를 수동으로 삭제
{: #step6}

{{site.data.keyword.cloudaccesstrailshort}}에서 고유 이벤트 보존을 제어할 수 있습니다. 사용자는 이벤트를 삭제하거나, 이벤트 삭제를 자동화할 수 있습니다. 

이벤트를 수동으로 삭제하려면 `cf at delete` 명령을 실행하십시오. 예를 들면, 다음과 같습니다. 

```
$ bx cf at delete -s 2017-07-25 -e 2017-07-25
Deleted successfully
"6 logs were deleted,freeing 13737 bytes."
```

`cf at delete` 명령에 대해 자세히 알아보려면 [CLI 참조](/docs/services/cloud-activity-tracker/cli/at_cli.html#delete)를 참조하십시오. 

명령행에서 도움말을 보려면 `bx cf at help delete`를 사용하십시오. 

**참고:** 이벤트를 자동으로 삭제하려는 경우에는 CLI 명령 `cf at option`을 사용하여 보존 정책을 설정할 수 있습니다. 자세한 정보는 [CLI 참조](/docs/services/cloud-activity-tracker/cli/at_cli.html#option)를 참조하십시오. 


