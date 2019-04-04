---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, overview

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



# {{site.data.keyword.cloudaccesstrailshort}} 정보
{: #activity_tracker_ov}

애플리케이션과 {{site.data.keyword.cloud_notm}} 서비스가 어떻게 상호작용하는지 추적하려면 {{site.data.keyword.cloudaccesstrailfull}} 서비스를 사용하십시오. {{site.data.keyword.cloudaccesstrailshort}}을 사용하여 비정상 활동을 모니터하고 규정 감사 요구사항을 준수하십시오. 수집되는 이벤트는 CADF(Cloud Auditing Data Federation) 표준을 준수합니다.
{:shortdesc}

* {{site.data.keyword.cloudaccesstrailshort}}은 클라우드에서
사용자의 IT 리소스에 대한 높은 수준의 보안 통제를 제공합니다.
* {{site.data.keyword.cloudaccesstrailshort}}은 관리자가 API 활동을 하나의 위치에서 캡처하고, 저장하고, 보고, 검색하고, 모니터할 수 있는 솔루션을 제공합니다.
* {{site.data.keyword.cloudaccesstrailshort}}은 감사 내역 보고서를 생성하는 데 사용할 수 있는 이벤트를 다운로드하는 기능을 제공합니다. 사용자의 조직에서는 내부적 규정과 외부적 산업 및 국가 규정을
따르기 위해 해당 보고서가 필요할 수 있습니다.

내부 정책 및 산업 규정의 준수는 애플리케이션이 실행되는 위치(온프레미스, 하이브리드 클라우드 또는 퍼블릭 클라우드)에 상관없이 조직의 전략에서 핵심적인 요구사항입니다. {{site.data.keyword.cloudaccesstrailshort}} 서비스는 API 호출을 모니터하고, 회사 정책 및 업계별 규정을 준수하는 데 필요한 증거를 작성하는 프레임워크와 기능을 제공합니다.

{{site.data.keyword.cloud_notm}}와 같은 클라우드 환경에서 작업할 때는 사용자의 내부 정책, 그리고 산업 및 국가 규제 준수 요구사항에 따라 워크로드 및 데이터를 감사하고 모니터하기 위한 클라우드 전략을 계획해야 합니다. {{site.data.keyword.cloudaccesstrailshort}} 서비스를 통해
등록된 정보를 사용하여 보안 사고를 식별하고, 권한 없는 액세스를 발견하며, 규정과 내부 감사 요구사항을
준수할 수 있습니다.

예를 들면, {{site.data.keyword.cloudaccesstrailshort}} 활동 로그를 사용하여 다음 정보를 식별할 수 있습니다.

* 클라우드 서비스에 API 호출을 수행한 사용자.
* API 호출이 발생하는 곳의 소스 IP 주소.
* API 호출이 발생하는 때의 시간소인.
* API 호출의 상태.


## 이벤트 수집
{: #activity_tracker_ov_collect}

{{site.data.keyword.cloudaccesstrailshort}} 서비스는 {{site.data.keyword.cloud_notm}} 내의 선택된 클라우드 서비스에 대해 수행된 API 호출 및 기타 조치와 관련된 활동 데이터를 캡처합니다. 

* 이벤트는 자동으로 수집됩니다. 
* {{site.data.keyword.cloudaccesstrailshort}}에서 수집되는 이벤트는 CADF(Cloud Auditing Data Federation) 표준을 준수합니다. CADF 표준은 클라우드 환경에서 애플리케이션의 보안을 인증, 관리 및 감사하는 데 필요한 정보가 포함된
전체 이벤트 모델을 정의합니다.
* {{site.data.keyword.cloudaccesstrailshort}}은 이벤트를 도메인별로 저장하고 그룹화합니다. 각 지역에는 계정 도메인이 있고, 각 Cloud Foundry 영역에는 영역 도메인이 있습니다. 

CADF 이벤트 모델은 다음 컴포넌트를 포함합니다.

<table>
  <caption>표 1. CADF 이벤트 모델에서 사용 가능한 컴포넌트</caption>
  <tr>
    <th>컴포넌트</th>
	<th>설명</th>
  </tr>
  <tr>
    <td>조치</td>
	<td>조치는 개시자가 수행하거나, 수행하려 시도하거나, 완료되기를 기다리는 오퍼레이션 또는 활동입니다.</td>
  </tr>
  <tr>
    <td>개시자</td>
	<td>개시자는 API 호출을 수행하고 CADF 이벤트를 생성하는 리소스입니다. 트리거되는 이벤트는
API 호출에서 요청하는 조치에 좌우됩니다.</td>
  </tr>
  <tr>
    <td>관찰자</td>
	<td>관찰자는 CADF 이벤트의 사용 가능한 정보로부터 CADF 레코드를 작성하고 저장하는 리소스입니다.</td>
  </tr>
  <tr>
    <td>결과</td>
	<td>결과는 대상에 대한 조치의 상태입니다.</td>
  </tr>
  <tr>
    <td>대상</td>
	<td>대상은 조치가 수행되거나, 수행이 시도되거나, 완료 보류 중인 리소스입니다.</td>
  </tr>
</table>


{{site.data.keyword.IBM_notm}} 퍼블릭 클라우드에서 {{site.data.keyword.cloudaccesstrailshort}} 로그에 대해 작업할 때는 다음 정보를 고려하십시오.

* 사용자는 {{site.data.keyword.IBM_notm}} 퍼블릭 클라우드에서 실행되는 리소스에 대해 수행된 API 호출에 대한 감사 레코드만 저장할 수 있습니다.
* 이벤트를 수집하는 데는 {{site.data.keyword.IBM_notm}} 퍼블릭 클라우드 스토리지만 사용됩니다.
* 정보는 3일간 저장됩니다. 그 이후에는 선입선출(FIFO) 방식으로 정보가 삭제됩니다.
* {{site.data.keyword.cloudaccesstrailshort}} 서비스는 유형이 *Activity*인 CADF 이벤트를 지원합니다.


## Activity Tracker 프로비저닝
{: #activity_tracker_ov_provision}

계정 도메인에 있는 이벤트를 보려면 API 활동을 모니터할 지역의 Cloud Foundry 영역에 {{site.data.keyword.cloudaccesstrailshort}} 서비스를 프로비저닝해야 합니다. 계정 이벤트는 **계정 소유자**만 볼 수 있습니다.

영역 도메인에 있는 이벤트를 보려면 API 활동을 모니터할 영역에 {{site.data.keyword.cloudaccesstrailshort}} 서비스를 프로비저닝해야 합니다.

{{site.data.keyword.cloudaccesstrailshort}} 서비스를 프로비저닝하는 방법에 대한 자세한 정보는 [{{site.data.keyword.cloudaccesstrailshort}} 서비스 프로비저닝](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-provision#provision)을 참조하십시오.



## 활동 로그 분석
{: #activity_tracker_ov_analyze}

활동 로그는 {{site.data.keyword.cloud_notm}}의 {{site.data.keyword.cloudaccesstrailshort}} UI를 통해 분석하거나, 오픈 소스 도구인 Kibana를 사용하여 분석할 수 있습니다. 사용자는 특정 영역, 또는 계정 레벨에서 사용 가능한 이벤트를 모니터할 수 있습니다.

{{site.data.keyword.cloud_notm}}의 {{site.data.keyword.cloudaccesstrailshort}} UI를 통해 최근 24시간에 대한 활동 로그를 검색하고, 분석하고, 모니터할 수 있습니다. 자세한 정보는 [{{site.data.keyword.cloudaccesstrailshort}} UI로 이동](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-launch_at_ui#launch_at_ui)을 참조하십시오.

{{site.data.keyword.cloudaccesstrailshort}} Kibana 대시보드를 사용하거나 사용자 정의 대시보드를 작성하여, Kibana를 통해 최근 3일에 대한 활동 로그를 검색하고, 분석하고 모니터할 수 있습니다. * **참고:** 이 기능은 **프리미엄** 플랜 사용자의 경우 사용할 수 있습니다.

* Kibana를 실행하는 방법에 대한 자세한 정보는 [Kibana 대시보드로 이동](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-launch_kibana#launch_kibana)을 참조하십시오. 
* Kibana에서 이벤트를 분석하는 데 사용할 수 있는 필드의 목록은 [{{site.data.keyword.cloudaccesstrailshort}} 이벤트 필드](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-at_event#at_event)를 참조하십시오.



## 지역
{: #activity_tracker_ov_regions}

{{site.data.keyword.cloudaccesstrailshort}} 서비스는 다음 지역에서 사용 가능합니다.

* 독일
* 시드니
* 영국(Lite 플랜만 사용 가능)
* 미국 남부


## 서비스 플랜
{: #activity_tracker_ov_plan}

{{site.data.keyword.cloudaccesstrailshort}} 서비스는 여러 플랜을 제공합니다.

{{site.data.keyword.cloud_notm}} UI 또는 명령행을 통해 플랜을 변경할 수 있습니다. 플랜은 언제든지 업그레이드 또는 다운그레이드할 수 있습니다. 서비스 플랜 업그레이드에 대한 자세한 정보는 [플랜 변경](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-change_plan#change_plan)을 참조하십시오. 

다음 표에는 사용 가능한 플랜이 간략하게 설명되어 있습니다.

<table>
    <caption>표 1. 이벤트 수집, 이벤트 보존 및 이벤트 내보내기를 위한 기능</caption>
      <tr>
        <th>플랜</th>
        <th>이벤트 수집</th>
        <th>이벤트 보존</th>
		<th>이벤트 내보내기</th>
      </tr>
      <tr>
        <td>Lite(기본값)</td>
        <td>아니오</td>
        <td>최근 3일</td>
		<td>아니오</td>
      </tr>
      <tr>
        <td>프리미엄</td>
        <td>예</td>
        <td>구성 가능한 일 수</td>
		<td>예</td>
      </tr>
</table>

<table>
    <caption>표 2. 이벤트 관리 및 보기를 위한 기능</caption>
      <tr>
        <th>플랜</th>
		    <th>API</th>
		    <th>CLI</th>
        <th>Kibana</th>
      </tr>
      <tr>
        <td>Lite(기본값)</td>
		    <td>아니오</td>
		    <td>아니오</td>
        <td>아니오</td>
      </tr>
      <tr>
        <td>프리미엄</td>
		    <td>예</td>
		    <td>예</td>
        <td>예</td>
      </tr>
</table>

**참고:** 이벤트 스토리지에 대한 월별 비용은 비용 청구 주기의 평균으로 계산됩니다.

## 보안
{: #activity_tracker_ov_security}

{{site.data.keyword.cloudaccesstrailshort}} 서비스에 대해 작업할 때는 보안에 대한 다음 정보를 고려하십시오.

* {{site.data.keyword.cloudaccesstrailshort}} 이벤트를 생성하는 IBM 서비스는 {{site.data.keyword.IBM_notm}} 클라우드 보안 정책을 따릅니다. 자세한 정보는 [Trust the security and privacy of IBM Cloud ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/cloud-computing/learn-more/why-ibm-cloud/security/){: new_window}를 참조하십시오.
* {{site.data.keyword.cloudaccesstrailshort}} 서비스는 클라우드 서비스의 상태를 변경하는, 사용자가 시작한 조치를 캡처합니다. 정보는 데이터베이스 또는 애플리케이션에 대한 직접 액세스를 제공하지 않습니다.
* 권한 부여된 사용자만 {{site.data.keyword.cloudaccesstrailshort}} 이벤트 로그를 보고 모니터할 수 있습니다. 각 사용자는 {{site.data.keyword.cloud_notm}}에서 자신의 고유 ID로 식별됩니다.
