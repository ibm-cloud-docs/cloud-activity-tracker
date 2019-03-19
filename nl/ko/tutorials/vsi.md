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


# {{site.data.keyword.cloudaccesstrailshort}}를 사용하여 {{site.data.keyword.BluVirtServers_short}} 및 {{site.data.keyword.baremetal_short}} 모니터링
{: #vsi}

사용자가 {{site.data.keyword.BluVirtServers_short}} 및 {{site.data.keyword.baremetal_short}}를 사용하여 작성된 인프라 디바이스를 관리하고 사용자 조치에서 {{site.data.keyword.cloudaccesstrailshort}}를 사용하여 모니터할 수 있는 {{site.data.keyword.cloudaccesstrailshort}} 이벤트를 생성할 수 있도록 이 튜토리얼을 통해 {{site.data.keyword.cloud_notm}} 계정의 사용자를 구성하는 방법에 대해 알아보십시오.
{:shortdesc}

 {{site.data.keyword.BluVirtServers}}는 전용 코어 및 메모리 할당을 포함하여 구매하는 확장 가능한 가상 서버입니다. 이미지 템플리트와 같은 기능에 액세스할 수 있으며 몇 분 안에 추가할 수 있는 컴퓨팅 리소스를 찾고 있는 경우 이는 훌륭한 선택사항입니다. 
* 추가 정보는 [{{site.data.keyword.BluVirtServers_short}} ](/docs/vsi/vsi_about.html#about-virtual-servers)의 내용을 참조하십시오. 
* {{site.data.keyword.cloudaccesstrailshort}} 이벤트를 생성하는 조치 목록은 [{{site.data.keyword.BluVirtServers_short}}에 의해 생성된 이벤트](/docs/vsi/vsi_activity_tracker_events.html#at_events)를 참조하십시오.

{{site.data.keyword.baremetal_short}}는 하드웨어 리소스에 대한 하위 레벨 액세스 권한과 함께 성능과 제어를 제공하는 실제 싱글 테넌트 서버입니다. 
* 추가 정보는 [{{site.data.keyword.baremetal_long}} ](/docs/bare-metal/about.html#about)의 내용을 참조하십시오.
* {{site.data.keyword.cloudaccesstrailshort}} 이벤트를 생성하는 조치 목록은 [{{site.data.keyword.baremetal_short}}에 의해 생성된 이벤트](/docs/bare-metal/bm-activity-tracker-events.html#at_events)를 참조하십시오.

**사용자가 {{site.data.keyword.BluVirtServers_short}} 및 {{site.data.keyword.baremetal_short}} {{site.data.keyword.cloudaccesstrailshort}} 이벤트를 생성하려면 사용자에게 IBM Cloud 콘솔의 인프라 리소스에 대한 액세스 권한이 있어야 합니다.**
{: tip}

## 1단계: {{site.data.keyword.cloud_notm}} 계정에 Softlayer 계정 연결
{: #vsi_step1}

** {{site.data.keyword.cloudaccesstrailshort}} 이벤트를 생성하려면 Softlayer 계정을 {{site.data.keyword.cloud_notm}} 계정에 연결해야 합니다. 자세한 정보는 [IBM ID로 전환 및 계정 연결](/docs/account?topic=account-unifyingaccounts#link_accounts)을 참조하십시오.

{{site.data.keyword.cloud_notm}} 계정에 Softlayer 계정을 연결할 때 다음 정보를 고려하십시오.
* SAML 연합 계정이 IBM ID 인증으로 전환하는 데 사용되는 경우를 제외하고 모든 새 계정은 자동으로 IBM ID 및 기존 SoftLayer 계정을 수신합니다.
* {{site.data.keyword.cloud_notm}} 계정에 연결할 각 SoftLayer 계정은 고유 이메일 주소가 있는 고유 IBM ID에서 소유해야 합니다.
* 기존 SoftLayer 계정을 IBM ID로 전환하려면 IBM ID를 작성한 다음 등록 코드를 사용하여 확인합니다.
* 계정을 IBM ID 계정으로 전환한 후에는 SoftLayer 계정과 {{site.data.keyword.cloud_notm}} 계정을 연결하여 결합된 IaaS(Infrastructure as a Service)와 PaaS(Platform as a Service) 리소스를 사용할 수 있습니다. 

계정을 연결하려면 다음 단계를 완료하십시오.
1. [IBM ID 및 등록 코드 요청](/docs/account/softlayerlink.html#reqIBMidandregcode)
2. [등록 코드로 IBM ID 확인](/docs/account/softlayerlink.html#confIBMiduseregcode)
3. [IBM ID 계정 연결](/docs/account/softlayerlink.html#link_user_account)


## 2단계: 사용자에게 인프라 권한 부여
{: #vsi_step2}

**참고:** *{{site.data.keyword.cloud_notm}} 인프라 포털*에서 권한을 부여하는 경우 사용자에게 디바이스를 관리할 수 있는, *{{site.data.keyword.cloud_notm}} 인프라* 대시보드의 액세스 권한이 없으며 {{site.data.keyword.cloudaccesstrailshort}} 이벤트가 생성되지 않습니다. **{{site.data.keyword.cloud_notm}} 계정을 통해, 디바이스를 관리할 수 있는 인프라 권한을 사용자에게 부여해야 합니다. 이러한 조치는 {{site.data.keyword.cloudaccesstrailshort}} 이벤트를 생성합니다.**
{: tip}

사용자에게 인프라 권한을 부여하려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.cloud_notm}}에 로그인하십시오.

    {{site.data.keyword.cloud_notm}} 대시보드는 [http://bluemix.net ![외부 링크 아이콘](../../../icons/launch-glyph.svg "외부 링크 아이콘")](http://bluemix.net){:new_window}에 있습니다.
    
	사용자 ID 및 비밀번호를 사용하여 로그인하면 {{site.data.keyword.cloud_notm}} UI가 열립니다.

2. 메뉴 표시줄에서 **관리** &gt; **계정**을 클릭한 다음 **사용자**를 선택하십시오. 

3. 디바이스에 대한 작업을 수행할 수 있는 권한을 부여할 사용자를 선택하십시오.

4. **액세스 지정**을 선택하십시오.

5. **Softlayer 계정에 대한 액세스 권한 지정**을 선택하십시오. {{site.data.keyword.cloud_notm}} 인프라 포털이 {{site.data.keyword.cloud_notm}}의 컨텍스트 내에서 열립니다.

6. 사용자에게 디바이스를 관리할 수 있도록 부여할 권한을 설정하십시오. **포털 권한**을 선택하십시오. 그런 다음 **디바이스** 섹션에서 사용자가 디바이스를 관리하는 데 필요한 권한을 사용자에게 부여하십시오. 예를 들면, *가상 서버 세부사항 보기*, *서버 재부팅 및 IPMI 시스템 정보 보기*, *서버 업그레이드* 또는 *OS 다시 로드 실행 및 복구 커널 시작*입니다.

7. 포털 권한을 저장하십시오. **디바이스 액세스**를 선택하면 변경사항을 저장하도록 프롬프트가 표시됩니다. **저장**을 클릭하십시오.

8. 사용자가 관리할 수 있는 디바이스를 설정하십시오. **디바이스 액세스** 섹션에서 실제 디바이스를 선택하십시오. 그런 다음 **디바이스 액세스 업데이트**를 클릭하십시오.






