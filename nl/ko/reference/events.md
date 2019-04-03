---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, events

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


# {{site.data.keyword.cloudaccesstrailshort}} 이벤트
{: #events}

{{site.data.keyword.Bluemix}}에서 {{site.data.keyword.cloudaccesstrailshort}}을 추적하려면 {{site.data.keyword.cloudaccesstrailfull}} 서비스를 사용하십시오. 
{:shortdesc}



## 이벤트 목록
{: #actions}

다음 표에는 이벤트를 생성하는 조치가 나열되어 있습니다.

<table>
  <caption>표 1. 이벤트를 생성하는 조치 목록</caption>
  <tr>
    <th>조치</th>
	  <th>설명</th>
  <tr>
  <tr>
    <td>read.events</td>
	  <td>저장된 이벤트에 대한 정보를 가져옵니다.</td>
  </tr>
  <tr>
    <td>create.sessions</td>
	  <td>이벤트를 다운로드하는 데 사용할 수 있는 세션을 작성합니다.</td>
  </tr>
  <tr>
    <td>delete.session</td>
	  <td>세션을 삭제합니다.</td>
  </tr>
  <tr>
    <td>read.sessions</td>
	  <td>세션을 나열합니다.</td>
  </tr>
  <tr>
    <td>download.events</td>
	  <td>이벤트를 다운로드합니다.</td>
  </tr>
  <tr>
    <td>delete.events</td>
	  <td>이벤트를 삭제합니다.</td>
  </tr>
</table>


## 이벤트를 찾을 위치
{: #ui}
 	
{{site.data.keyword.cloudaccesstrailshort}} 이벤트는 {{site.data.keyword.cloudaccesstrailshort}} 서비스가 프로비저닝된 Cloud Foundry 영역에 있습니다.
