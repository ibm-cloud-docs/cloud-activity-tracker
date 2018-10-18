---

copyright:
  years: 2016, 2018
lastupdated: "2018-04-27"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}



# Kibana 대시보드로 이동
{: #launch_kibana}

Kibana는 {{site.data.keyword.Bluemix}}의 {{site.data.keyword.cloudaccesstrailshort}} UI에서 실행하거나, 웹 브라우저에서 직접 실행할 수 있습니다.
{:shortdesc}
   

##  Activity Tracker 서비스의 대시보드에서 Kibana로 이동
{: #launch_Kibana_from_at}

Kibana가 표시하는 활동 로그는 사용자가 로그인했으며 {{site.data.keyword.cloudaccesstrailshort}} 서비스가 프로비저닝된 {{site.data.keyword.Bluemix_notm}} 조직의 영역 내에 배치된 모든 리소스에 대한 이벤트를 포함합니다.

{{site.data.keyword.cloudaccesstrailshort}} 서비스의 대시보드에서 Kibana를 실행하려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.Bluemix_notm}} 계정에 로그인하십시오.

    {{site.data.keyword.Bluemix_notm}} 대시보드는 [http://bluemix.net ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://bluemix.net){:new_window}에 있습니다.
    
	사용자 ID 및 비밀번호를 사용하여 로그인하면 {{site.data.keyword.Bluemix_notm}} UI가 열립니다.

2. {{site.data.keyword.Bluemix_notm}} 대시보드에서 {{site.data.keyword.cloudaccesstrailshort}} 서비스를 선택하십시오. 
    
3. **관리됨** 탭을 선택하십시오.

4. **고급 보기**를 클릭하십시오. 

    Kibana 대시보드가 열립니다.

기본적으로 **ActivityTracker_Space_Dashboard_in_24h** 대시보드가 로드되며, 시간 필터가 최근 24시간으로 설정됩니다. 


	
	
##  웹 브라우저에서 Kibana로 이동
{: #launch_Kibana_from_browser}

Kibana가 표시하는 로그 정보는 사용자가 로그인되어 있는 {{site.data.keyword.Bluemix_notm}} 조직의 영역 내에 배치된 모든 리소스에 대한 이벤트를 포함합니다.

브라우저에서 Kibana를 실행하려면 다음 단계를 완료하십시오.

1. 웹 브라우저를 열고 Kibana를 실행하십시오. 그런 다음 Kibana 사용자 인터페이스에 로그인하십시오.
    
    예를 들어, 다음 표에는 지역별로 Kibana를 실행하기 위해 사용해야 하는 URL이 나열되어 있습니다.
      
    <table>
          <caption>표 1. Kibana 실행을 위한 지역별 URL</caption>
           <tr>
            <th>지역</th>
            <th>URL</th>
          </tr>
          <tr>
            <td>독일</td>
            <td>[https://logging.eu-fra.bluemix.net](https://logging.eu-fra.bluemix.net)</td>
          </tr>
          <tr>
            <td>시드니</td>
            <td>[https://logging.au-syd.bluemix.net](https://logging.au-syd.bluemix.net)</td>
          </tr>
		  <tr>
            <td>영국</td>
            <td>[https://logging.eu-gb.bluemix.net](https://logging.eu-gb.bluemix.net)</td>
          </tr>
		  <tr>
            <td>미국 남부</td>
            <td>[https://logging.ng.bluemix.net](https://logging.ng.bluemix.net) </td>
          </tr>
    </table>
	
	Kibana의 검색 페이지가 열립니다.
	
2. 활동 로그를 보고 분석할 {{site.data.keyword.Bluemix_notm}} 계정, 조직 및 영역에 로그인했는지 확인하십시오.

    사용자는 자신이 로그인되어 있는 영역에서 사용 가능한 이벤트 및 로그를 볼 수 있습니다.

3. 이벤트를 필터링하려면 메뉴 표시줄에서 **열기**를 선택하십시오.

    저장된 대시보드의 목록이 표시됩니다.
	
4. 로그인되어 있는 영역의 이벤트를 보려면 **ActivityTracker_Space_Dashboard_in_24h**를 선택하십시오.


## 제한사항
{: #limitations}

 Kibana의 제한사항으로 인해, 동일한 세션에서 여러 Kibana 브라우저 탭을 동시에 열어 복수의 영역 또는 계정을 볼 수는 없습니다. 따라서, 동시에 둘 이상의 세션이 있으며 도메인을 영역에서 계정으로, 또는 그 반대로 변경하는 경우에는 문제점이 발생할 수 있습니다.
	



