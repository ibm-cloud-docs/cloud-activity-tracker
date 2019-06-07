---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, launch Kibana

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
{:deprecated: .deprecated}


# Kibana 대시보드 열기
{: #launch_kibana}

Kibana는 {{site.data.keyword.cloud_notm}}의 {{site.data.keyword.cloudaccesstrailshort}} UI에서 실행하거나, 웹 브라우저에서 직접 실행할 수 있습니다.
{:shortdesc}
   
{{site.data.keyword.cloudaccesstrailfull}}는 더 이상 사용되지 않습니다. 2019년 5월 9일을 기준으로 새 {{site.data.keyword.cloudaccesstrailshort}} 인스턴스를 프로비저닝할 수 없습니다. 기존 프리미엄 플랜 인스턴스는 2019년 9월 30일까지 지원됩니다. {{site.data.keyword.cloud_notm}} 계정의 활동을 계속 모니터하려면 [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started)의 인스턴스를 프로비저닝하십시오.
{: deprecated}


##  Activity Tracker 서비스의 대시보드에서 Kibana 열기
{: #launch_Kibana_from_at}

Kibana가 표시하는 활동 로그는 사용자가 로그인했으며 {{site.data.keyword.cloudaccesstrailshort}} 서비스가 프로비저닝된 {{site.data.keyword.cloud_notm}} 조직의 영역 내에 배치된 모든 리소스에 대한 이벤트를 포함합니다.

{{site.data.keyword.cloudaccesstrailshort}} 서비스의 대시보드에서 Kibana를 실행하려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.cloud_notm}} 계정에 로그인하십시오.

    {{site.data.keyword.cloud_notm}} 대시보드는 [https://cloud.ibm.com/login ![외부 링크 아이콘](../../../icons/launch-glyph.svg "외부 링크 아이콘")](https://cloud.ibm.com/login){:new_window}에 있습니다.
    
	사용자 ID 및 비밀번호를 사용하여 로그인하면 {{site.data.keyword.cloud_notm}} UI가 열립니다.

2. {{site.data.keyword.cloud_notm}} 대시보드에서 {{site.data.keyword.cloudaccesstrailshort}} 서비스를 선택하십시오. 
    
3. **관리됨** 탭을 선택하십시오.

4. 영역 이벤트를 보려면 *로그 보기* 필드에서 **영역 로그**를 선택하십시오. **참고:** 이는 기본 보기입니다. 그런 다음 **Kibana에서 보기**를 클릭하십시오. 

    Kibana 대시보드가 열립니다. 시간 필터가 최근 24시간으로 설정된 상태로 **ActivityTracker_Space_Dashboard_in_24h** 대시보드가 로드됩니다.

5. 계정 이벤트를 보려면 *로그 보기* 필드에서 **계정 로그**를 선택하십시오. 그런 다음 **Kibana에서 보기**를 클릭하십시오. 

    시간 필터가 최근 24시간으로 설정된 상태로 **ActivityTracker_Account_Dashboard_in_24h** 대시보드가 로드됩니다.
	
	
##  웹 브라우저에서 Kibana 열기
{: #launch_Kibana_from_browser}

브라우저에서 Kibana를 실행하려면 다음 단계를 완료하십시오.

1. 웹 브라우저를 열고 이벤트를 모니터할 지역에서 Kibana를 실행하십시오. 그런 다음 Kibana 사용자 인터페이스에 로그인하십시오.
    
    예를 들어, 다음 표에는 지역별로 Kibana를 실행하기 위해 사용해야 하는 URL이 나열되어 있습니다.
      
    <table>
          <caption>표 1. Kibana 실행을 위한 지역별 URL</caption>
           <tr>
            <th>지역</th>
            <th>URL</th>
          </tr>
          <tr>
            <td>독일</td>
            <td>`https://logging.eu-fra.bluemix.net`</td>
          </tr>
          <tr>
            <td>시드니</td>
            <td>`https://logging.au-syd.bluemix.net` </td>
          </tr>
		  <tr>
            <td>영국</td>
            <td>`https://logging.eu-gb.bluemix.net`</td>
          </tr>
		  <tr>
            <td>미국 남부</td>
            <td>`https://logging.ng.bluemix.net`</td>
          </tr>
    </table>
	
	Kibana의 검색 페이지가 열립니다.
	
2. 활동 이벤트를 보고 분석할 {{site.data.keyword.cloud_notm}} 계정에 로그인했는지 확인하십시오.

3. 영역 또는 계정 이벤트 보기

* 로그인 정보가 표시되는 Kibana 창의 오른쪽 상단을 클릭하십시오.
* **도메인**의 드롭 다운에서 영역 또는 계정을 선택하십시오.
* 영역 이벤트의 경우, 영역 드롭 다운에서 관심 있는 **영역**을 선택하십시오.
* 계정 이벤트의 경우, 계정 드롭 다운에서 올바른 **계정**을 선택하십시오.

4. 검색 시간 조정

* Kibana 기본 검색 시간은 최근 15분으로 설정됩니다.
* 오른쪽 상단 회색 막대에서 `Last 15 minutes`를 클릭하십시오.
* 얼마나 오랜 기간 동안의 이벤트를 볼 것인지 선택하십시오. 최근 3일 동안의 이벤트를 검색할 수 있습니다. 3일 또는 그 미만의 시간 범위를 선택하십시오.

5. Activity Tracker 이벤트만 표시하도록 필터링
* Kibana에서 직접 볼 때 로그 및 Activity Tracker 이벤트 둘 다 발생할 수 있습니다.
* Activity Tracker만 표시하려면 검색 막대에 `type:ActivityTracker`를 입력하십시오.

Kibana에 표시되는 이벤트는 Kibana를 실행한 지역에서 선택한 도메인에서 호스팅되는 이벤트와 일치합니다.

## 제한사항
{: #launch_kibana_limitations}

* Kibana의 제한사항으로 인해, 동일한 세션에서 여러 Kibana 브라우저 탭을 동시에 열어 복수의 영역 또는 계정을 볼 수는 없습니다. 따라서, 동시에 둘 이상의 세션이 있으며 도메인을 영역에서 계정으로, 또는 그 반대로 변경하는 경우에는 문제점이 발생할 수 있습니다.
* 기본적으로 계정 소유자만 계정 이벤트를 볼 수 있습니다. 기타 사용자가 계정 이벤트를 보도록 설정하려면 [계정 이벤트 보기](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-view_acc_events#view_acc_events)의 지시사항을 따르십시오.



