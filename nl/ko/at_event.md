---

copyright:
  years: 2016, 2018
lastupdated: "2018-07-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}



# Activity Tracker 이벤트 필드
{: #at_event}

{{site.data.keyword.cloudaccesstrailshort}} 이벤트는 CADF(Cloud Auditing Data Federation) 표준을 기반으로 합니다. 
{:shortdesc}

## 개시자 필드
{: #initiator}

다음 표에는 {{site.data.keyword.cloudaccesstrailshort}} 이벤트에 대해 사용 가능한 공통 필드가 나열되어 있습니다. 

<table>
  <caption>공통 개시자 필드</caption>
  <tr>
    <th>필드 이름</th>
	  <th>설명</th>
    <th>값</th>
  </tr>
  <tr>
    <td>initiator.id</td>
	  <td>조치 개시자의 ID입니다. </br>개시자에는 IBM ID와 서비스 ID의 두 가지 유형이 있습니다. </td>
    <td>IBM ID의 예: IBMid-000000XXX2</br>서비스 ID의 예: iam-ServiceId-12345678-0165-4c89-847d-9660b1632e14</td>
  </tr>
  <tr>
    <td>initiator.name</td>
	  <td>조치를 시작한 사용자의 사용자 이름입니다. </td>
    <td></td>
  </tr>
  <tr>
    <td>initiator.typeURI</td>
	  <td>이벤트의 소스 유형입니다. </td>
    <td>올바른 값은 *service/security/account/user*, *service/security/clientid*, *service/security/account/serviceid*입니다. </td>
  </tr>
  <tr>
    <td>initiator.credential.type</td>
	  <td>개시자 ID 인증 정보의 유형입니다. </td>
    <td>올바른 값은 *user*, *token*, *apikey*입니다. </td>
  </tr>
</table>

## 대상 필드
{: #target}

다음 표에는 {{site.data.keyword.cloudaccesstrailshort}} 이벤트에 대해 사용 가능한 공통 대상 필드가 나열되어 있습니다. 

<table>
  <caption>공통 대상 필드</caption>
  <tr>
    <th>필드 이름</th>
	  <th>설명</th>
    <th>값</th>
  </tr>
  <tr>
    <td>target.id</td>
	  <td>조치가 수행되는 리소스의 CRN(Cloud Resource Name)입니다. </br>자세한 정보는 [CRN 형식](/docs/overview/crn.html#format)을 참조하십시오. </td>
    <td>예: `crn:v1:bluemix:public:cloud-object-storage:global:a/12345678e6232019c6567c9123456789:fr56et47-befb-440a-a223c-12345678dae1:bucket:bucket1`</td>
  </tr>
  <tr>
    <td>target.name</td>
	  <td>조치가 수행되는 클라우드 리소스의 사람이 읽을 수 있는 이름입니다. </td>
    <td></td>
  </tr>
  <tr>
    <td>target.typeURI</td>
    <td>조치가 실행되는 클라우드 리소스의 유형입니다. </br>이 필드의 형식은 **serviceName/objectType**이며 serviceName은 서비스의 이름입니다. </td>
	  <td>예: `iam-am/policy` 또는 `cloud-object-storage/bucket/acl`</td>
  </tr>
</table>
 
## 조치 필드
{: #action}

다음 표에는 {{site.data.keyword.cloudaccesstrailshort}} 이벤트에 대해 사용 가능한 공통 조치 필드가 나열되어 있습니다. 

<table>
  <caption>공통 조치 필드</caption>
  <tr>
    <th>필드 이름</th>
	  <th>설명</th>
    <th>값</th>
  </tr>
  <tr>
    <td>action</td>
	  <td>이벤트를 트리거하는 조치입니다. </br>이 필드의 형식은 **serviceName.objectType.action**이며 serviceName은 서비스의 이름입니다. </br>서비스에 의해 생성되는 이벤트에 대한 정보는 <a href="/docs/services/cloud-activity-tracker/cloud_services.html#cloud_services">클라우드 서비스</a>를 참조하십시오. </td>
    <td>예: *iam-identity.serviceid-apikey.login*</td>
  </tr>
  <tr>
    <td>eventTime</td>
	  <td>이벤트가 작성된 시간소인을 나타냅니다. </br>날짜는 협정 세계시(UTC)로 표시됩니다. </br>이 형식은 ISO 8601을 준수합니다. </td>
    <td>예: 2017-10-19T19:07:50.32+0000<td>
  </tr>
</table>

## 결과 필드
{: #outcomes}

다음 표에는 {{site.data.keyword.cloudaccesstrailshort}} 이벤트에 대해 사용 가능한 공통 결과 필드가 나열되어 있습니다. 

<table>
  <caption>공통 결과 필드</caption>
  <tr>
    <th>필드 이름</th>
	  <th>설명</th>
    <th>값</th>
  </tr>
  <tr>
    <td>outcome</td>
	  <td>조치의 결과입니다. </td>
    <td>올바른 값은 *success*, *failure*, *pending*입니다. </td>
  </tr>
  <tr>
    <td>reason.reasonCode</td>
	  <td>HTTP 응답 코드를 포함하는 숫자 필드입니다. </td>
    <td>예를 들면, *200*은 성공적인 결과를 나타냅니다. </td>
  </tr>
  <tr>
    <td>severity</td>
	  <td>조치가 클라우드에 미치는 위협의 정도를 정의합니다. </td>
    <td>올바른 값은 *normal*, *warning* 및 *critical*입니다. </br></br>**normal**은 클라우드 내의 일상적인 조치에 대해 설정됩니다. 예: 인스턴스 시작 또는 토큰 새로 고치기. </br></br>**warning**은 클라우드 리소스가 업데이트되거나 해당 메타데이터가 수정되는 조치에 대해 설정됩니다. 예: 작업자 노드의 버전 업데이트, 인증서 이름 바꾸기 또는 서비스 인스턴스 이름 바꾸기. </br></br>**critical**은 클라우드의 보안에 영향을 주는 조치에 대해 설정됩니다. 예: 사용자의 인증 정보 변경, 데이터 삭제, 클라우드 리소스에 대한 작업을 수행하기 위한 무단 액세스. </td>
  </tr>
</table>
