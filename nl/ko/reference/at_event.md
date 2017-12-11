---

copyright:
  years: 2016, 2017

lastupdated: "2017-09-18"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# Activity Tracker 이벤트 필드
{: #at_event}

{{site.data.keyword.cloudaccesstrailshort}} 이벤트는 CADF(Cloud Auditing Data Federation) 표준을 기반으로 합니다.
{:shortdesc}

## 이벤트 필드
{: #fields}

다음 표에는 {{site.data.keyword.cloudaccesstrailshort}} 이벤트의 분석에 사용 가능한 필드가 나열되어 있습니다. 

<table>
  <caption>표 1. 이벤트당 모니터링에 사용 가능한 필드</caption>
  <tr>
    <th>필드 이름</th>
	<th>상태</th>
	<th>설명</th>
  </tr>
  <tr>
    <td>outcome</td>
	<td>필수</td>
	<td>올바른 값: *success*, *failure*</td>
  </tr>
  <tr>
    <td>typeURI</td>
	<td>필수</td>
	<td>이 필드는 *http://schemas.dmtf.org/cloud/audit/1.0/event*로 설정됩니다. </td>
  </tr>
  <tr>
    <td>eventType</td>
	<td>필수</td>
	<td>이 필드는 *activity*로 설정됩니다. </td>
  </tr>
  <tr>
    <td>eventTime </td>
	<td>필수</td>
	<td>(날짜는 *2017-09-17 15:15:32.396 +0000 UTC*와 같이 ISO 문자열로 표현됩니다.)</td>
  </tr>
  <tr>
    <td>action</td>
	<td>필수</td>
	<td>이 필드는 *read.ibm-key-protect.secrets*와 같은, 이벤트를 트리거한 조치를 표시합니다. </td>
  </tr>
  <tr>
    <td>id</td>
	<td>선택사항</td>
	<td>이 필드는 이벤트의 UUID를 포함합니다. </td>
  </tr>
  <tr>
    <td>initiator.id</td>
	<td>필수</td>
	<td>이 필드는 인스턴스 ID와 같은 이벤트 소스의 ID를 포함합니다. </td>
  </tr>
  <tr>
    <td>initiator.name</td>
	<td>선택사항</td>
	<td>이 필드는 사용자 ID와 같은, 이벤트 소스에 대한 사람이 읽을 수 있는 이름을 제공합니다. </td>
  </tr>
  <tr>
    <td>initiator.typeURI</td>
	<td>필수</td>
	<td>이 필드는 *service/security/account/user*와 같은, 이벤트 소스의 유형에 대한 정보를 알려줍니다. </td>
  </tr>
  <tr>
    <td>initiator.host.agent</td>
	<td>선택사항</td>
	<td>이 필드는 *python-neutronclient*와 같은, 요청을 전송하는 데 사용된 클라이언트 또는 브라우저 정보를 표시합니다. </td>
  </tr>
  <tr>
    <td>initiator.host.address</td>
	<td>선택사항</td>
	<td>이 필드는 개시자의 IP 주소를 포함합니다. </td>
  </tr>
  <tr>
    <td>target.id</td>
	<td>필수</td>
	<td>이 필드는 대상 서비스의 ID를 포함합니다. </td>
  </tr>
  <tr>
    <td>target.name</td>
	<td>필수</td>
	<td>이 필드는 *ibm-key-protect*와 같은, 대상 서비스에 대한 사람이 읽을 수 있는 이름을 포함합니다. </td>
  </tr>
  <tr>
    <td>target.typeURI</td>
	<td>필수</td>
	<td>이 필드는 *service/ibm-key-protect/secrets*와 같은, 이벤트 대상의 유형을 포함합니다. </td>
  </tr>
  <tr>
    <td>target.host.address</td>
	<td>선택사항</td>
	<td>이 필드는 *xxx.bluemix.net*과 같은, 대상 서비스의 IP 주소 또는 URL을 포함합니다. </td>
  </tr>
  <tr>
    <td>observer.name</td>
	<td>필수</td>
	<td>이 필드는 *ActivityTracker*로 설정됩니다. </td>
  </tr>
  <tr>
    <td>observer.id</td>
	<td>필수</td>
	<td>이 필드는 *activitytracker.ng.bluemix.net*과 같은, CADF 이벤트를 작성하고 저장하는 리소스에 대한 정보를 포함합니다. </td>
  </tr>
  <tr>
    <td>observer.typeURI</td>
	<td>필수</td>
	<td>이 필드는 *service/security/edge/activity-tracker*로 설정됩니다. </td>
  </tr>
  <tr>
    <td>reason.reasonCode</td>
	<td>선택사항</td>
	<td>이 필드는 성공에 대한 *200*과 같은, HTTP 응답 코드를 포함합니다. </td>
  </tr>
  <tr>
    <td>reason.reasonType</td>
	<td>필수</td>
	<td>이 필드는 reasonCode가 *reason.reasonCode* 필드를 통해 제공된 경우 이에 대한 정보를 포함합니다. </td>
  </tr>
</table>

 

