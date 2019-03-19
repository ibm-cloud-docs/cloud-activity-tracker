---

copyright:
  years: 2016, 2019
lastupdated: "2019-01-23"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# 이벤트를 볼 수 있는 권한 부여
{: #grant_permissions}

{{site.data.keyword.Bluemix}}에서는 사용자에게 Cloud Foundry 역할 또는 IAM 역할을 지정하거나, 이를 둘 다 지정할 수 있습니다. 이러한 역할은 {{site.data.keyword.cloudaccesstrailshort}} 서비스에 대해 작업할 때 사용자가 수행할 수 있는 태스크를 정의합니다.  
{:shortdesc}

## 계정 이벤트를 볼 수 있는 권한 부여
{: #grant_acc_events}

지역 내 계정 이벤트를 볼 수 있도록 하려면 사용자에게 다음 권한을 부여하십시오.

1. {{site.data.keyword.cloudaccesstrailshort}}이 프로비저닝된 지역에 있는 영역의 *개발자* 역할. 

    자세한 정보는 [CF 역할 부여](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_cf_role)를 참조하십시오.

2. 해당 지역의 *뷰어* 역할이 있는 {{site.data.keyword.loganalysisshort}} 서비스에 대한 IAM 정책. 

    뷰어 역할은 필요한 최소 IAM 역할입니다. 
	
	자세한 정보는 [IAM 권한 부여](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_iam_policy)를 참조하십시오.


## 영역 이벤트를 볼 수 있는 권한 부여
{: #grant_space_events}

지역 내 영역 이벤트를 볼 수 있도록 하려면 사용자에게 다음 권한을 부여하십시오.

* {{site.data.keyword.cloudaccesstrailshort}}이 프로비저닝된 지역에 있는 영역의 *개발자* 역할. 

    자세한 정보는 [CF 역할 부여](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_cf_role)를 참조하십시오.


## IAM 권한 부여
{: #grant_iam_policy}

사용자에게 IAM 역할을 부여하려는 경우에는 다음 정보를 고려하십시오.

* 계정 내의 다른 사용자에게 정책을 지정할 수 있는 권한이 있거나 계정 소유자여야 합니다. 계정 소유자가 아닌 경우에는 {{site.data.keyword.loganalysisshort}} 서비스에 대한 **관리자** 역할이 있는 IAM 정책이 있어야 합니다.

* 정책을 정의할 때 지정하는 지역은 사용자가 계정 도메인 이벤트를 볼 수 있는 액세스 권한이 부여되는 지역을 정의합니다.

사용자에게 계정 도메인의 이벤트를 볼 수 있는 권한을 부여하려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.cloud_notm}} 콘솔에 로그인하십시오.

    웹 브라우저를 열고 {{site.data.keyword.cloud_notm}} 대시보드를 실행하십시오([http://bluemix.net ![외부 링크 아이콘](../../../icons/launch-glyph.svg "외부 링크 아이콘")](http://bluemix.net){:new_window}).
	
	사용자 ID 및 비밀번호를 사용하여 로그인하면 {{site.data.keyword.cloud_notm}} UI가 열립니다.

2. 메뉴 표시줄에서 **관리 > 계정 > 사용자**를 클릭하십시오. 

    *사용자* 창에는 사용자 및 현재 선택된 계정의 이메일 주소 목록이 표시됩니다.
	
3. 사용자가 계정의 구성원인 경우에는 목록에서 사용자 이름을 선택하거나 *조치* 메뉴에서 **사용자 관리**를 클릭하십시오.

    사용자가 계정의 구성원이 아닌 경우에는 [사용자 초대](/docs/iam/iamuserinv.html#iamuserinv)를 참조하십시오.

4. **액세스 정책** 섹션에서 **액세스 권한 지정**을 클릭한 후 **리소스에 대한 액세스 권한 지정**을 선택하십시오.

    *사용자에게 리소스 액세스 권한 지정** 창이 열립니다.

5. 정책에 대한 정보를 입력하십시오. 다음 표에는 정책을 정의하는 데 필요한 필드가 나열되어 있습니다. 

    <table>
	  <caption>IAM 정책을 구성하기 위한 필드의 목록입니다.</caption>
	  <tr>
	    <th>필드</th>
		<th>값</th>
	  </tr>
	  <tr>
	    <td>서비스</td>
		<td>*IBM Cloud Log Analysis*</td>
	  </tr>	  
	  <tr>
	    <td>지역</td>
		<td>이벤트에 대해 작업할 수 있도록 사용자에게 액세스 권한이 부여될 지역을 지정할 수 있습니다. 하나 이상의 지역을 개별적으로 선택하거나, **모든 현재 지역**을 선택하여 모든 지역에 대한 액세스 권한을 부여하십시오.</td>
	  </tr>
	  <tr>
	    <td>서비스 인스턴스</td>
		<td>*모든 서비스 인스턴스*를 선택하십시오.</td>
	  </tr>
	  <tr>
	    <td>역할</td>
		<td>하나 이상의 IAM 역할을 선택하십시오. <br>올바른 역할은 *관리자*, *운영자*, *편집자* 및 *뷰어*입니다.</td>
	  </tr>
     </table>
	
6. **지정**을 클릭하십시오.
	
구성하는 정책이 선택된 지역에 적용됩니다. 


## CF 역할 부여
{: #grant_cf_role}

사용자에게 CF 역할을 부여하려는 경우에는 다음 정보를 고려하십시오.

* 사용자에게 Cloud Foundry 역할을 지정할 수 있는 조직 및 영역 내 권한이 있어야 합니다. 

* **개발자** 역할이 있는 사용자만 이벤트를 볼 수 있습니다.

사용자에게 영역 이벤트를 볼 수 있는 권한을 부여하려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.cloud_notm}} 콘솔에 로그인하십시오.

    웹 브라우저를 열고 {{site.data.keyword.cloud_notm}} 대시보드를 실행하십시오([http://bluemix.net ![외부 링크 아이콘](../../../icons/launch-glyph.svg "외부 링크 아이콘")](http://bluemix.net){:new_window}).
	
	사용자 ID 및 비밀번호를 사용하여 로그인하면 {{site.data.keyword.cloud_notm}} UI가 열립니다.

2. 메뉴 표시줄에서 **관리 > 계정 > 사용자**를 클릭하십시오. 

    *사용자* 창에는 사용자 및 현재 선택된 계정의 이메일 주소 목록이 표시됩니다.
	
3. 사용자가 계정의 구성원인 경우에는 목록에서 사용자 이름을 선택하거나 *조치* 메뉴에서 **사용자 관리**를 클릭하십시오.

    사용자가 계정의 구성원이 아닌 경우에는 [사용자 초대](/docs/iam/iamuserinv.html#iamuserinv)를 참조하십시오.

4. **Cloud Foundry 액세스 권한**을 선택한 후 조직을 선택하십시오.

    해당 조직에서 사용 가능한 영역의 목록이 나열합니다.

5. 한 영역을 선택하십시오. 그런 다음 메뉴 조치에서 **영역 역할 편집**을 선택하십시오.

6. **개발자**를 선택하십시오.
	
7. **역할 저장**을 클릭하십시오.




