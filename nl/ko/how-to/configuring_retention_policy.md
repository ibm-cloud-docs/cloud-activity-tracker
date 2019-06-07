---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, configure retention policy

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

# 이벤트 보존 정책 구성
{: #configuring_retention_policy}

이벤트가 {{site.data.keyword.cloudaccesstrailshort}}에서 보존되는 최대 일 수를 정의하는 보존 정책을 보고 구성하려면 **ibmcloud at option** 명령을 사용하십시오. 기본적으로 보존 정책은 사용 안함으로 설정되며 이벤트는 무기한으로 보존됩니다. 보존 기간이 만료되면 이벤트는 자동으로 삭제됩니다. 
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}}는 더 이상 사용되지 않습니다. 2019년 5월 9일을 기준으로 새 {{site.data.keyword.cloudaccesstrailshort}} 인스턴스를 프로비저닝할 수 없습니다. 기존 프리미엄 플랜 인스턴스는 2019년 9월 30일까지 지원됩니다. {{site.data.keyword.cloud_notm}} 계정의 활동을 계속 모니터하려면 [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started)의 인스턴스를 프로비저닝하십시오.
{: deprecated}


계정 내의 모든 영역에 대해 동일한 보존 정책을 설정하거나 특정 영역에 대한 보존 기간을 사용자 정의할 수 있습니다. 


## 영역에 대한 이벤트 보존 정책의 사용 안함 설정
{: #disable_retention_policy_space}

보존 정책을 사용 안함으로 설정하려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.cloud_notm}}에 로그인하십시오. 

    [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) 명령을 실행하여 {{site.data.keyword.cloud_notm}}에 로그인한 후 [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) 명령을 실행하여 {{site.data.keyword.cloudaccesstrailshort}} 서비스를 프로비저닝할 조직 및 영역을 설정하십시오.
	
2. 보존 기간을 **-1**로 설정하여 사용 안함으로 설정하십시오. 다음 명령을 실행하십시오.

    ```
    ibmcloud at option -r -1
    ```
    {: codeblock}
    
**예**
    
예를 들어, ID가 *d35da1e3-b345-475f-8502-bx cfgh436902a3*인 영역에 대해 보존 기간을 사용 안함으로 설정하려면 다음 명령을 실행하십시오.

```
ibmcloud at option -r -1
```
{: codeblock}

출력은 다음과 같습니다.

```
+-----------------------------------------+-----------+
|               SPACEID                   | RETENTION |
+-----------------------------------------+-----------+
| d35da1e3-b345-475f-8502-bx cfgh436902a3 |        -1 |
+-----------------------------------------+-----------+
```
{: screen} 



## 영역에 대한 로그 보존 정책 확인
{: #check_retention_policy_space}

{{site.data.keyword.cloud_notm}} 영역에 대해 설정된 보존 기간을 가져오려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.cloud_notm}}에 로그인하십시오. 

    [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) 명령을 실행하여 {{site.data.keyword.cloud_notm}}에 로그인한 후 [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) 명령을 실행하여 {{site.data.keyword.cloudaccesstrailshort}} 서비스를 프로비저닝할 조직 및 영역을 설정하십시오.
	
2. 보존 기간을 가져오십시오. 다음 명령을 실행하십시오.

    ```
    ibmcloud at option
    ```
    {: codeblock}

    영역 ID *d35da1e3-b345-475f-8502-bx cfgh436902a3*에 대한 출력은 30일입니다.

    ```
    +-----------------------------------------+-----------+
    |               SPACEID                   | RETENTION |
    +-----------------------------------------+-----------+
    | d35da1e3-b345-475f-8502-bx cfgh436902a3 |        30 |
    +-----------------------------------------+-----------+
    ```
    {: screen}
    

## 계정 내 모든 영역에 대한 로그 보존 정책 확인
{: #check_retention_policy_account}

계정 내 각 {{site.data.keyword.cloud_notm}} 영역에 대해 설정된 보존 기간을 가져오려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.cloud_notm}}에 로그인하십시오. 

    [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) 명령을 실행하여 {{site.data.keyword.cloud_notm}}에 로그인한 후 [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) 명령을 실행하여 {{site.data.keyword.cloudaccesstrailshort}} 서비스를 프로비저닝할 조직 및 영역을 설정하십시오.
    
2. 계정 내 각 영역에 대한 보존 기간을 가져오십시오. 다음 명령을 실행하십시오.

    ```
    ibmcloud at option -a
    ```
    {: codeblock}
	
	여기서 *-a*는 정보가 계정 내 모든 영역을 포함함을 나타냅니다.

    예를 들면, 이 명령 실행의 출력은 다음과 같습니다.

    ```
    +-----------------------------------------+-----------+
    |               SPACEID                   | RETENTION |
    +-----------------------------------------+-----------+
    | d35da1e3-b345-475f-8502-bx cfgh436902a3 |        30 |
    +-----------------------------------------+-----------+
    | fdew45e3-b345-4365-8502-bx cfghrfthy5a3 |        30 |
    +-----------------------------------------+-----------+
    ```
    {: screen}
    

## 계정 전체의 로그 보존 정책 설정
{: #set_retention_policy_space}

{{site.data.keyword.cloud_notm}} 계정의 보존 기간을 설정하려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.cloud_notm}}에 로그인하십시오. 

    [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) 명령을 실행하여 {{site.data.keyword.cloud_notm}}에 로그인한 후 [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) 명령을 실행하여 {{site.data.keyword.cloudaccesstrailshort}} 서비스를 프로비저닝할 조직 및 영역을 설정하십시오.
	
2. 보존 기간을 설정하십시오. 다음 명령을 실행하십시오.

    ```
    ibmcloud at option -r Number_of_days - a
    ```
    {: codeblock}
    
    여기서, 
	* *-r*은 보존 기간을 설정하기 위해 지정해야 하는 옵션입니다.
	* *Number_of_days*는 이벤트를 보존할 일 수를 정의하는 정수입니다. 
	* *-a*는 요청이 계정 내 모든 영역에 적용됨을 나타냅니다.
    
    
**예**
    
예를 들어, 계정 내 모든 유형의 로그를 15일 간만 보존하려는 경우에는 다음 명령을 실행하십시오.

```
ibmcloud at option -r 15 -a
```
{: codeblock}

출력에는 보존 기간에 대한 정보를 포함, 계정의 각 영역에 대한 항목이 나열됩니다.

```
+-----------------------------------------+-----------+
|               SPACEID                   | RETENTION |
+-----------------------------------------+-----------+
| d35da1e3-b345-475f-8502-bx cfgh436902a3 |        15 |
+-----------------------------------------+-----------+
| fdew45e3-b345-4365-8502-bx cfghrfthy5a3 |        15 |
+-----------------------------------------+-----------+
```
{: screen}

## 영역에 대한 로그 보존 정책 설정
{: #set_retention_policy_account}

{{site.data.keyword.cloud_notm}} 영역의 보존 기간을 설정하려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.cloud_notm}}에 로그인하십시오. 

    [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) 명령을 실행하여 {{site.data.keyword.cloud_notm}}에 로그인한 후 [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) 명령을 실행하여 {{site.data.keyword.cloudaccesstrailshort}} 서비스를 프로비저닝할 조직 및 영역을 설정하십시오.
    
2. 보존 기간을 설정하십시오. 다음 명령을 실행하십시오.

    ```
    ibmcloud at option -r Number_of_days
    ```
    {: codeblock}
    
    여기서, 
	* *-r*은 보존 기간을 설정하기 위해 지정해야 하는 옵션입니다.
	* *Number_of_days*는 이벤트를 보존할 일 수를 정의하는 정수입니다.
    
    
**예**
    
예를 들어, 영역에 있는 이벤트를 1년 간 보존하려면 다음 명령을 실행하십시오.

```
ibmcloud at option -r 365
```
{: codeblock}

출력은 다음과 같습니다.

```
+-----------------------------------------+-----------+
|               SPACEID                   | RETENTION |
+-----------------------------------------+-----------+
| d35da1e3-b345-475f-8502-bx cfgh436902a3 |       365 |
+-----------------------------------------+-----------+
```
{: screen}


