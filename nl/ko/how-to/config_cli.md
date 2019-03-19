---

copyright:
  years: 2016, 2019
lastupdated: "2019-02-18"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# Activity Tracker CLI 구성
{: #config_cli}

{{site.data.keyword.cloudaccesstraillong}} 서비스에는 클라우드에서 이벤트를 관리하는 데 사용할 수 있는 명령행 인터페이스(CLI)가 포함되어 있습니다. 사용자는 {{site.data.keyword.cloud_notm}} 플러그인을 사용하여 이벤트의 상태를 보거나, 이벤트를 다운로드하거나, 이벤트 보존 정책을 구성할 수 있습니다. 이 CLI에서는 CLI 및 지원되는 명령에 대해 알려주는 일반 도움말, 명령 사용 방법에 대해 알려주는 명령 도움말, 명령의 하위 명령 사용 방법을 알려주는 하위 명령 도움말과 같은 다양한 유형의 도움말을 제공합니다.
{:shortdesc}


## {{site.data.keyword.cloud_notm}} 저장소에서 {{site.data.keyword.cloudaccesstrailshort}} 플러그인 설치
{: #install_cli_repo}

{{site.data.keyword.cloudaccesstrailshort}} CLI를 설치하려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.cloud_notm}} CLI를 설치하십시오.

   자세한 정보는 [{{site.data.keyword.cloud_notm}} CLI 설치](/docs/cli?topic=cloud-cli-ibmcloud-cli#ibmcloud-cli)를 참조하십시오.
   
2. 저장소에서 플러그인의 이름을 찾으십시오. 다음 명령을 실행하십시오.

    ```
    ibmcloud plugin repo-plugins
    ```
    {: codeblock}
    
    이 플러그인의 이름은 **activity-tracker**입니다.

3. {{site.data.keyword.cloudaccesstrailshort}} 플러그인을 설치하십시오. 다음 명령을 실행하십시오.

    ```
    ibmcloud plugin install activity-tracker -r Bluemix
    ```
    {: codeblock}
 
4. {{site.data.keyword.cloudaccesstrailshort}} 플러그인이 설치되었는지 확인하십시오.
  
    예를 들어, 설치된 플러그인의 목록을 보려면 다음 명령을 실행하십시오.
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    


## 파일에서 {{site.data.keyword.cloudaccesstrailshort}} 플러그인 설치
{: #install_cli}

{{site.data.keyword.cloudaccesstrailshort}} CLI를 설치하려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.cloud_notm}} CLI를 설치하십시오.

   자세한 정보는 [{{site.data.keyword.cloud_notm}} CLI 설치](/docs/cli?topic=cloud-cli-ibmcloud-cli#ibmcloud-cli)를 참조하십시오.

2. {{site.data.keyword.cloudaccesstrailshort}} 플러그인을 설치하십시오.

    * Linux의 경우에는 [Linux에서 {{site.data.keyword.cloudaccesstrailshort}} 플러그인 설치](/docs/services/cloud-activity-tracker/how-to/config_cli.html#install_cli_linux)를 참조하십시오.
    * Windows의 경우에는 [Windows에서 {{site.data.keyword.cloudaccesstrailshort}} 플러그인 설치](/docs/services/cloud-activity-tracker/how-to/config_cli.html#install_cli_windows)를 참조하십시오.
    * Mac OS X의 경우에는 [Mac OS X에서 {{site.data.keyword.cloudaccesstrailshort}} 플러그인 설치](/docs/services//cloud-activity-tracker/how-to/config_cli.html#install_cli_mac)를 참조하십시오.
 
3. CLI 플러그인의 설치를 확인하십시오.
  
    예를 들면, 플러그인의 버전을 확인하십시오. 다음 명령을 실행하십시오.
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    


## 파일에서 Linux에 {{site.data.keyword.cloudaccesstrailshort}} 플러그인 설치
{: #install_cli_linux}

Linux에 플러그인을 설치하려면 다음 단계를 완료하십시오.

1. 플러그인을 설치하십시오.

    [{{site.data.keyword.cloud_notm}} CLI 페이지](https://clis.ng.bluemix.net/ui/repository.html#bluemix-plugins)에서 {{site.data.keyword.cloudaccesstrailshort}} 서비스 CLI 플러그인(activity-tracker)의 최신 릴리스를 다운로드하십시오. 
	
	* 플랫폼 값을 **linux64**로 선택하십시오. 
	
	* **파일 저장**을 클릭하십시오. 
    
2. 플러그인을 설치하십시오. 다음 명령을 실행하십시오.
        
    ```
    ibmcloud plugin install -f activity-tracker-linux-amd64-3.3.0
    ```
    {: codeblock}




## 파일에서 Windows에 {{site.data.keyword.cloudaccesstrailshort}} 플러그인 설치
{: #install_cli_windows}

Windows에 플러그인을 설치하려면 다음 단계를 완료하십시오.

1. [{{site.data.keyword.cloud_notm}} CLI 페이지](https://clis.ng.bluemix.net/ui/repository.html#bluemix-plugins)에서 {{site.data.keyword.cloudaccesstrailshort}} 서비스 CLI 플러그인(activity-tracker)의 최신 릴리스를 다운로드하십시오. 
	
	1. 플랫폼 값을 **win64**로 선택하십시오. 
	2. **파일 저장**을 클릭하십시오.  
    
2. 플러그인을 설치하십시오. 다음 명령을 실행하십시오.
        
    ```
    ibmcloud plugin install -f activity-tracker-windows-amd64-3.3.0.exe
    ```
    {: codeblock}

	

## 파일에서 Mac OS X에 {{site.data.keyword.cloudaccesstrailshort}} 플러그인 설치
{: #install_cli_mac}

Mac OS X에 플러그인을 설치하려면 다음 단계를 완료하십시오.

1. [{{site.data.keyword.cloud_notm}} CLI 페이지](https://clis.ng.bluemix.net/ui/repository.html#bluemix-plugins)에서 {{site.data.keyword.cloudaccesstrailshort}} 서비스 CLI 플러그인(activity-tracker)의 최신 릴리스를 다운로드하십시오. 
	
	1. 플랫폼 값을 **osx**로 선택하십시오. 
	2. **파일 저장**을 클릭하십시오.  
    
2. 플러그인을 설치하십시오. 다음 명령을 실행하십시오.
        
    ```
    ibmcloud plugin install -f activity-tracker-darwin-amd64-3.3.0
    ```
    {: codeblock}

	
	
## {{site.data.keyword.cloudaccesstrailshort}} CLI 설치 제거
{: #uninstall_cli}

CLI를 설치 제거하려면 플러그인을 삭제하십시오.
{:shortdesc}

{{site.data.keyword.cloudaccesstrailshort}} 서비스 CLI를 설치 제거하려면 다음 단계를 완료하십시오.

1. 설치된 CLI 플러그인의 버전을 확인하십시오.
  
    예를 들면, 플러그인의 버전을 확인하십시오. 다음 명령을 실행하십시오.
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    
2. 플러그인이 설치되어 있는 경우에는 `ibmcloud plugin uninstall`을 실행하여 CLI 플러그인을 설치 제거하십시오.

    다음 명령을 실행하십시오.
        
    ```
    ibmcloud plugin uninstall activity-tracker
    ```
    {: codeblock}
  

## 저장소에서 {{site.data.keyword.cloudaccesstrailshort}} CLI 업데이트
{: #update_cli}

CLI를 업데이트하려면 *ibmcloud plugin update* 명령을 실행하십시오.
{:shortdesc}

{{site.data.keyword.cloudaccesstrailshort}} 서비스 CLI를 업데이트하려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.cloudaccesstrailshort}} 플러그인을 업데이트하십시오. 다음 명령을 실행하십시오.

    ```
    ibmcloud plugin update activity-tracker -r Bluemix
    ```
    {: codeblock}
 
2. CLI 플러그인의 설치를 확인하십시오.
  
    예를 들면, 플러그인의 버전을 확인하십시오. 다음 명령을 실행하십시오.
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    





## 일반 도움말 보기
{: #general_cli_help}

CLI와 지원되는 명령에 대한 일반 정보를 가져오려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.cloud_notm}}의 지역, 조직 및 영역에 로그인하십시오. 
    
2. 지원되는 명령 및 CLI에 대한 정보를 나열하십시오. 다음 명령을 실행하십시오.

    ```
    ibmcloud at help 
    ```
    {: codeblock}
    
    

## 명령에 대한 도움말 보기
{: #command_cli_help}

특정 명령을 사용하는 방법에 대한 도움말을 보려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.cloud_notm}}의 지역, 조직 및 영역에 로그인하십시오. 
    
2. 지원되는 명령의 목록을 보고 필요한 명령을 식별하십시오. 다음 명령을 실행하십시오.

    ```
    ibmcloud at help 
    ```
    {: codeblock}

3. 해당 명령에 대한 도움말을 보십시오. 다음 명령을 실행하십시오.

    ```
    ibmcloud at help *Command*
    ```
    {: codeblock}
    
    여기서 *Command*는 CLI 명령의 이름(예: *status*)입니다.



## 하위 명령에 대한 도움말 보기
{: #subcommand_cli_help}

특정 명령에는 하위 명령이 있을 수 있습니다. 하위 명령에 대한 도움말을 보려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.cloud_notm}}의 지역, 조직 및 영역에 로그인하십시오. 
    
2. 지원되는 명령의 목록을 보고 필요한 명령을 식별하십시오. 다음 명령을 실행하십시오.

    ```
    ibmcloud at help 
    ```
    {: codeblock}

3. 해당 명령에 대한 도움말을 보고 지원되는 하위 명령을 식별하십시오. 다음 명령을 실행하십시오.

    ```
    ibmcloud at help *Command*
    ```
    {: codeblock}
    
    여기서 *Command*는 CLI 명령의 이름(예: *session*)입니다.

4. 해당 명령에 대한 도움말을 보고 지원되는 하위 명령을 식별하십시오. 다음 명령을 실행하십시오.

    ```
    ibmcloud at *Command* help *Subcommand*
    ```
    {: codeblock}
    
    여기서, 
    
    * 여기서 *Command*는 CLI 명령의 이름(예: *status*)입니다.
    * *Subcommand*는 지원되는 하위 명령의 이름(예: 명령 *session*의 경우 유효한 하위 명령은 *list*)입니다.


## 플러그인의 세부사항 표시
{: #show}
  
플러그인 세부사항을 표시하려면 'ibmcloud plugin show activity-tracker' 명령을 사용하십시오. 

```
ibmcloud plugin show activity-tracker
```
{: codeblock}
    




