---

copyright:
  years: 2016, 2018
lastupdated: "2018-07-09"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# IBM Cloud Activity Tracker CLI
{: #at_cli_cloud}

{{site.data.keyword.cloudaccesstraillong}} CLI를 사용하여 {{site.data.keyword.cloudaccesstrailshort}} 이벤트를 관리할 수 있습니다.
{: shortdesc}

**전제조건**
* 명령을 실행하기 전에, `ibmcloud login` 명령으로 {{site.data.keyword.Bluemix}}에 로그인하여 액세스 토큰을 생성하고 세션을 인증하십시오. 
* CLI를 사용하여 이벤트를 관리하려면 유료 플랜이 있어야 합니다. 

{{site.data.keyword.cloudaccesstraillong}} CLI 플러그인은 Linux, Mac 및 Windows 플랫폼을 지원합니다.

<table>
  <caption>{{site.data.keyword.cloudaccesstrailshort}} 관리 명령</caption>
  <tr>
    <th>명령</th>
    <th>용도</th>
  </tr>
  <tr>
    <td>[ibmcloud at](#base)</td>
    <td>버전 또는 명령 목록과 같은 CLI 관련 정보를 가져오려면 이 명령을 사용하십시오.</td>
  </tr>
  <tr>
    <td>[ibmcloud at delete](#delete)</td>
    <td>{{site.data.keyword.cloudaccesstrailshort}} 이벤트를 삭제하려면 이 명령을 사용하십시오.</td>
  </tr>
  <tr>
    <td>[ibmcloud at download](#download)</td>
    <td>{{site.data.keyword.cloudaccesstrailshort}} 로그를 로컬 파일에 다운로드하려면 이 명령을 사용하십시오. </td>
  </tr>
  <tr>
    <td>[ibmcloud at help](#help)</td>
    <td>CLI 사용법에 대한 도움말 및 모든 명령의 목록을 보려면 이 명령을 사용하십시오.</td>
  </tr>
  <tr>
    <td>[ibmcloud at option](#option)</td>
    <td>영역 또는 계정에서 사용 가능한, 보존과 같은 {{site.data.keyword.cloudaccesstrailshort}} 이벤트 옵션을 보거나 변경하려면 이 명령을 사용하십시오. </td>
  </tr>
  <tr>
    <td>[ibmcloud at session create](#session_create)</td>
    <td>새 세션을 작성하려면 이 명령을 사용하십시오.</td>
  </tr>
  <tr>
    <td>[ibmcloud at session delete](#session_delete)</td>
    <td>세션을 삭제하려면 이 명령을 사용하십시오.</td>
  </tr>  
  <tr>
    <td>[ibmcloud at session list](#session_list)</td>
    <td>활성 세션 및 해당 ID를 나열하려면 이 명령을 사용하십시오.</td>
  </tr>  
  <tr>
    <td>[ibmcloud at session show](#session_show)</td>
    <td>단일 세션의 상태를 표시하려면 이 명령을 사용하십시오.</td>
  </tr>   
  <tr>
    <td>[ibmcloud at status](#status)</td>
    <td>{{site.data.keyword.cloudaccesstrailshort}}에 저장되는 이벤트의 상태에 대한 정보를 보려면 이 명령을 사용하십시오.</td>
  </tr>
  </table>


## ibmcloud at
{: #base}

CLI의 버전 및 CLI 사용 방법에 대한 정보를 제공합니다.

```
ibmcloud at [parameters]
```
{: codeblock}

**매개변수**

<dl>
<dt>--help, -h</dt>
<dd>명령 목록을 표시하거나, 하나의 명령에 대한 도움말을 보려면 이 매개변수를 설정하십시오.
</dd>

<dt>--version, -v</dt>
<dd>CLI의 버전을 인쇄하려면 이 매개변수를 설정하십시오.</dd>
</dl>

**예**

명령의 목록을 보려면 다음 명령을 실행하십시오.

```
ibmcloud at --help
```
{: codeblock}

CLI의 버전을 보려면 다음 명령을 실행하십시오.

```
ibmcloud at --version
```
{: codeblock}


## ibmcloud at delete
{: #delete}

{{site.data.keyword.cloudaccesstrailshort}} 이벤트를 삭제합니다.

```
ibmcloud at delete [parameters] [arguments..]
```
{: codeblock}

**매개변수**

<dl>
  <dt>--start value, -s value</dt>
  <dd>(선택사항) 시작 날짜를 UTC(협정 세계 표준시)로 설정합니다(*YYYY-MM-DD*). 예를 들면, `2017-01-02`와 같습니다. <br>기본값은 2주일 전으로 설정됩니다. 
  </dd>
  
  <dt>--end value, -e value</dt>
  <dd>(선택사항) 종료 날짜를 UTC(협정 세계 표준시)로 설정합니다(*YYYY-MM-DD*). <br>날짜의 UTC 형식은 **YYYY-MM-DD**로, 예를 들면 `2017-01-02`와 같습니다. <br>기본값은 현재 날짜로 설정됩니다.
  </dd>
  
  <dt>--search-time value, -T value</dt>
  <dd>(선택사항) 이 매개변수를 설정하여 특정 일에 지정된 시간 동안 저장된 이벤트를 삭제할 수 있습니다. 이 필드의 형식은 0 - 23입니다.
  </dd>

</dl>


**예**

2017년 6월 22일의 이벤트를 삭제하려면 다음 명령을 실행하십시오.
```
ibmcloud at delete -s 2017-06-22 -e 2017-06-22
```
{: codeblock}

다음 출력과 유사한 정보를 수신합니다.

`Deleted successfully`
`"6 logs were deleted, freeing 13737 bytes."`


## ibmcloud at download
{: #download}

{{site.data.keyword.cloudaccesstrailshort}} 이벤트를 로컬 파일에 다운로드하거나, 이를 Windows 및 Mac OS X의 터미널 창 또는 Linux 터미널의 표준 출력에 스트리밍합니다. 

**참고:** 파일을 다운로드하려면 먼저 세션을 작성해야 합니다. 세션은 날짜 범위에 따라 어느 이벤트를 다운로드할지 정의합니다. 사용자는 세션의 컨텍스트 내에서 이벤트를 다운로드합니다. 

```
ibmcloud at download [parameters] [arguments...]
```
{: codeblock}

**매개변수**

<dl>
<dt>--output value, -o value</dt>
<dd>(선택사항) 이벤트가 다운로드되는 로컬 출력 파일의 경로 및 파일 이름을 설정합니다. <br>기본값은 하이픈(-)입니다. <br>표준 출력에 로그를 출력하려면 이 매개변수를 기본값으로 설정하십시오.</dd>
</dl>

**인수**

<dl>
<dt>Session ID</dt>
<dd>`ibmcloud at session create` 명령을 실행하여 얻는 세션 ID 값을 설정합니다. 이 값은 이벤트를 다운로드할 때 사용할 세션을 표시합니다. <br>**참고:** `ibmcloud at session create` 명령은 다운로드되는 이벤트를 제어하는 매개변수를 제공합니다. </dd>
</dl>

**참고:** 다운로드가 완료된 후 동일한 데이터를 다시 다운로드하려면 다른 파일 또는 세션을 사용해야 합니다.

**예**

`events.log`라는 파일에 이벤트를 다운로드하려면 다음 명령을 실행하십시오.

```
ibmcloud at download -o events.log 1db6ce16-824d-4d50-bd40-37f1d8fea9b7
```
{: screen}

다음 출력과 유사한 정보를 수신합니다. 

```
6.70 KiB / 3.06 KiB [========] 219.03% 8.60 MiB/s 0s
Download completed successfully
```
{: screen}


## ibmcloud at help
{: #help}

명령을 사용하는 방법에 대한 정보를 제공합니다.

```
ibmcloud at help [parameters]
```
{: codeblock}

**매개변수**

<dl>
<dt>명령</dt>
<dd>도움말을 보려는 명령 이름을 설정합니다.
</dd>
</dl>


**예**

{{site.data.keyword.cloudaccesstrailshort}}의 상태를 확인하기 위해 명령을 실행하는 방법에 대한 도움말을 보려면 다음 명령을 실행하십시오.

```
ibmcloud at help status
```
{: codeblock}


## ibmcloud at option
{: #option}

영역에 있는 이벤트의 보존 기간을 표시하거나 변경합니다. 보존 정책을 설정하는 경우에는 보존 일 수에 도달하면 이벤트가 자동으로 삭제됩니다.

* 이 기간은 일 수 단위로 설정됩니다.
* 기본값은 **-1**로, 이는 이벤트가 저장되고 삭제되지 않음을 의미합니다.

**참고:** 기본적으로는 모든 이벤트가 저장됩니다. 보존 기간을 설정하지 않는 경우에는 `ibmcloud at delete` 명령을 사용하여 이벤트를 수동으로 삭제해야 합니다.  

```
ibmcloud at option [parameters] [arguments...]
```
{: codeblock}

**매개변수**

<dl>
<dt>--retention value, -r value</dt>
<dd>(선택사항) 보존 일 수를 설정합니다. <br> 기본값은 *-1*일입니다.</dd>

<dt>--at-account-level, -a</dt>
<dd>(선택사항) 모든 영역 도메인 및 계정 도메인에 저장된 이벤트의 보존 기간에 대한 정보를 나열하려면 이 매개변수를 설정하십시오. 

</dl>

**예**

로그인되어 있는 영역의 현재 보존 기간을 보려면 다음 명령을 실행하십시오.

```
ibmcloud at option
```
{: codeblock}

출력은 다음 출력과 유사합니다.

```
+--------------------------------------+-----------+
|               SPACEID                | RETENTION |
+--------------------------------------+-----------+
| 2af890ce-fb4f-4e41-a975-901a56ed1f11 |        30 |
+--------------------------------------+-----------+
```
{: screen}


로그인되어 있는 영역의 보존 기간을 25일로 변경하려면 다음 명령을 실행하십시오.

```
ibmcloud at option -r 25
```
{: codeblock}

출력은 다음 출력과 유사합니다.

```
+--------------------------------------+-----------+
|               SPACEID                | RETENTION |
+--------------------------------------+-----------+
| 2af890ce-fb4f-4e41-a975-901a56ed1f11 |        25 |
+--------------------------------------+-----------+
```
{: screen}



## ibmcloud at session create
{: #session_create}

새 세션을 작성합니다.

**참고:** 하나의 영역에 최대 30개의 동시 세션을 포함할 수 있습니다. 세션은 한 명의 사용자에 대해 작성됩니다. 영역에서 사용자 간에 세션을 공유할 수는 없습니다.

```
ibmcloud at session create [parameters] [arguments...]
```
{: codeblock}

**매개변수**

<dl>
  <dt>--at-account-level, -a </dt>
  <dd>(선택사항) 계정 레벨의 범위를 설정합니다. </br>계정 정보를 가져오려면 이 값을 설정하십시오. <br>이 매개변수가 지정되지 않은 경우 기본값은 현재 영역, 즉 `ibmcloud cf login` 명령을 사용하여 로그인한 영역만으로 설정됩니다.
  </dd>

  <dt>--start value, -s value</dt>
  <dd>(선택사항) 시작 날짜를 UTC(협정 세계 표준시)로 설정합니다(*YYYY-MM-DD*). 예를 들면, `2017-01-02`와 같습니다. <br>기본값은 2주일 전으로 설정됩니다. 
  </dd>
  
  <dt>--end value, -e value</dt>
  <dd>(선택사항) 종료 날짜를 UTC(협정 세계 표준시)로 설정합니다(*YYYY-MM-DD*). 예를 들면, `2017-01-02`와 같습니다. <br>기본값은 현재 날짜로 설정됩니다. 
  </dd>

  <dt>--search-time value, -T value</dt>
  <dd>(선택사항) 이 매개변수를 설정하여 특정 일에 지정된 시간 동안 저장된 이벤트를 삭제할 수 있습니다. 이 필드의 형식은 0 - 23입니다.
  </dd>


 </dl>

**리턴값**

<dl>
<dt>Access-Time</dt>
<dd>세션이 마지막으로 사용된 시간을 표시하는 시간소인입니다.</dd>

<dt>Create-Time</dt>
<dd>세션이 작성된 날짜 및 시간에 해당하는 시간소인입니다.</dd>

<dt>Date-Range</dt>
<dd>이벤트를 필터링하는 데 사용된 일 수를 표시합니다. 이 날짜 범위 내에 식별된 이벤트는 세션을 통해 관리할 수 있습니다.</dd>

<dt>ID</dt>
<dd>세션 ID입니다.</dd>

<dt>Space</dt>
<dd>세션이 활성 상태인 영역 ID입니다.</dd>

<dt>Type-Account</dt>
<dd>이 값은 **ActivityTracker**로 설정됩니다.</dd>

<dt>Username</dt>
<dd>세션을 작성한 사용자의 {{site.data.keyword.IBM_notm}} ID입니다.</dd>
</dl>


**예**

2017년 7월 10일에 대한 섹션을 작성하려면 다음 명령을 실행하십시오.

```
ibmcloud at session create -s 2017-07-10 -e 2017-07-10
```
{: screen}

출력은 다음 출력과 유사합니다.

```
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| id           | 9b8c4db8-5841-4993-a449-305815a53a8e      |
| space        | xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx      |
| username     | xxx@yyy.com                               |
| create-time  | 2017-07-25T11:54:00.20042645Z             |
| access-time  | 2017-07-25T11:54:00.20042645Z             |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
+--------------+-------------------------------------------+
```
{: screen}



## ibmcloud at session delete
{: #session_delete}

세션 ID에 의해 지정되는 세션을 삭제합니다.

```
ibmcloud at session delete [arguments...]
```
{: codeblock}


**인수**

<dl>
<dt>Session ID</dt>
<dd>삭제하려는 세션의 ID입니다. <br>`ibmcloud at session list` 명령을 사용하여 활성 세션 ID를 모두 가져올 수 있습니다. </dd>
</dl>

**예**

세션 ID가 *9b8c4db8-5841-4993-a449-305815a53a8e*인 세션을 삭제하려면 다음 명령을 실행하십시오.

```
ibmcloud at session delete 9b8c4db8-5841-4993-a449-305815a53a8e
```
{: screen}

출력은 다음 출력과 유사합니다.

```
+---------------+--------------------------+
|    NAME       |     VALUE                |
+---------------+--------------------------+
|  message      | Delete session success   |
+---------------+--------------------------+
```
{: screen}


## ibmcloud at session list
{: #session_list}

활성 세션 및 해당 ID를 나열합니다.

```
ibmcloud at session list 
```
{: codeblock}

**리턴값**

<dl>
<dt>ID</dt>
<dd>세션 ID입니다.</dd>

<dt>SPACE</dt>
<dd>세션이 활성 상태인 영역 ID입니다.</dd>

<dt>USERNAME</dt>
<dd>세션을 작성한 사용자의 {{site.data.keyword.IBM_notm}} ID입니다.</dd>

<dt>CREATE-TIME</dt>
<dd>세션이 작성된 날짜 및 시간에 해당하는 시간소인입니다.</dd>

<dt>ACCESS-TIME</dt>
<dd>세션이 마지막으로 사용된 시간을 표시하는 시간소인입니다.</dd>
</dl>
 
**예**

세션을 나열하려면 다음 명령을 실행하십시오.

```
ibmcloud at session list
```
{: screen}

출력은 다음 출력과 유사합니다.

```
+--------------------------------------+--------------------------------------+-----------------------------------+--------------------------------+--------------------------------+
| ID                                   | SPACE                                | USERNAME                          | CREATE-TIME                    | ACCESS-TIME                    |
+--------------------------------------+--------------------------------------+-----------------------------------+--------------------------------+--------------------------------+
| fa3f1970-21f3-4e32-b480-1ffb41badc16 | 12345678-fb4f-acdf-a975-11335678r3fg | xxx@yyy.com                       | 2017-07-10T09:04:07.916788069Z | 2017-07-10T09:04:07.916788069Z |
| 9b8c4db8-5841-4993-a449-305815a53a8e | 12345678-fb4f-acdf-a975-11335678r3fg | xxx@yyy.com                       | 2017-07-11T09:19:14.666532796Z | 2017-07-12T09:19:14.666532796Z |
+--------------------------------------+--------------------------------------+-----------------------------------+--------------------------------+--------------------------------+
```
{: screen}


## ibmcloud at session show
{: #session_show}

단일 세션의 상태를 표시합니다.

```
ibmcloud at session show [arguments...]
```
{: codeblock}

**인수**

<dl>
<dt>Session ID</dt>
<dd>정보를 가져오려는 활성 세션의 ID입니다.</dd>
</dl>

**리턴값**

<dl>
<dt>Access-Time</dt>
<dd>세션이 마지막으로 사용된 시간을 표시하는 시간소인입니다.</dd>

<dt>Create-Time</dt>
<dd>세션이 작성된 날짜 및 시간에 해당하는 시간소인입니다.</dd>

<dt>Date-Range</dt>
<dd>이벤트를 필터링하는 데 사용된 일 수를 표시합니다. 이 날짜 범위 내에 식별된 이벤트는 세션을 통해 관리할 수 있습니다.</dd>

<dt>id</dt>
<dd>세션 ID입니다.</dd>

<dt>Space</dt>
<dd>세션이 활성 상태인 영역 ID입니다.</dd>

<dt>Type-Account</dt>
<dd>이 값은 **ActivityTracker**로 설정됩니다.</dd>

<dt>Username</dt>
<dd>세션을 작성한 사용자의 {{site.data.keyword.IBM_notm}} ID입니다.</dd>
</dl>

**예**

세션 ID가 *9b8c4db8-5841-4993-a449-305815a53a8e*인 세션의 세부사항을 표시하려면 다음 명령을 실행하십시오.

```
ibmcloud at session show 9b8c4db8-5841-4993-a449-305815a53a8e
```
{: screen}

출력은 다음 출력과 유사합니다.

```
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| create-time  | 2017-07-25T11:54:00.20042645Z             |
| access-time  | 2017-07-25T11:54:00.20042645Z             |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
| id           | 9b8c4db8-5841-4993-a449-305815a53a8e      |
| space        | xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx      |
| username     | xxx@yyy.com                               |
+--------------+-------------------------------------------+
```
{: screen}


## ibmcloud at status
{: #status}

{{site.data.keyword.cloudaccesstrailshort}} 이벤트의 상태에 대한 정보를 리턴합니다.

```
ibmcloud at status [parameters] [arguments...]
```
{: codeblock}

**매개변수**

<dl>
  <dt>--start value, -s value</dt>
  <dd>(선택사항) 시작 날짜를 UTC(협정 세계 표준시)로 설정합니다(*YYYY-MM-DD*). 예를 들면, `2017-01-02`와 같습니다. <br>기본값은 2주일 전으로 설정됩니다.
  </dd>
  
  <dt>--end value, -e value</dt>
  <dd>(선택사항) 종료 날짜를 UTC(협정 세계 표준시)로 설정합니다(*YYYY-MM-DD*). 예를 들면, `2017-01-02`와 같습니다. <br>기본값은 현재 날짜로 설정됩니다.
  </dd>
  
  <dt>--at-account-level, -a </dt>
  <dd>(선택사항) 계정 레벨의 범위를 설정합니다. <br> **참고:** 계정 정보를 가져오려면 이 값을 설정하십시오. <br>이 매개변수가 지정되지 않은 경우 기본값은 현재 영역, 즉 `ibmcloud cf login` 명령을 사용하여 로그인한 영역만으로 설정됩니다.
  </dd>
  
</dl>


**참고:** `ibmcloud at status` 명령은 시작 및 종료 날짜가 지정되지 않은 경우 {{site.data.keyword.cloudaccesstrailshort}}에 저장된 최근 2주일 간의 이벤트만 보고합니다.  

**리턴값**   

<dl>
  <dt>DATE</dt>
  <dd>UTC(협정 세계 표준시)로 된 날짜입니다(*YYYY-MM-DD*). 예를 들면, `2017-01-02`와 같습니다. 
  </dd>
  
  <dt>COUNT</dt>
  <dd>이벤트의 총 개수입니다.
  </dd>
  
  <dt>SIZE</dt>
  <dd>이벤트의 총 크기(메가바이트)입니다.
  </dd>

  <dt>TYPES</dt>
  <dd>이 값은 **ActivityTracker**로 설정됩니다.
  </dd>
  
  <dt>SEARCHABLE</dt>
  <dd>이 필드는 해당 이벤트를 Kibana에서 검색할 수 있는지 표시합니다. <br>필드 **SEARCHABLE**의 값이 *None*으로 설정된 경우 해당 이벤트는 다운로드 가능하지만, Kibana에서 분석할 수는 없습니다.
  </dd>
  
</dl>

**예**

2017년 7월 20일의 이벤트에 대한 세부사항을 표시하려면 다음 명령을 실행하십시오.

```
ibmcloud at status -s 2017-07-20 -e 2017-07-20
```
{: codeblock}


다음 출력과 유사한 정보를 수신합니다.

```
+------------+-----------+-------+------------------+--------------+
|   Date     |  Count    | Size  | Types            |  Searchable  | 
+------------+-----------+-------+------------------+--------------+
| 2017-07-20 |    1      | 2531  | ActivityTracker  | All          | 
+------------+-----------+-------+------------------+--------------+
```
{: screen}


