---

copyright:
  years: 2016, 2017
lastupdated: "2017-09-17"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Activity Tracker CLI 구성
{: #config_at_cli}

{{site.data.keyword.cloudaccesstraillong}} 서비스에는 클라우드에서 이벤트를 관리하는 데 사용할 수 있는 명령행 인터페이스(CLI)가 포함되어 있습니다. 이 CLI는 Cloud Foundry(CF) 플러그인입니다. 사용자는 명령을 사용하여 이벤트의 상태를 보거나, 이벤트를 다운로드하거나, 이벤트를 복원하거나, 이벤트를 버리거나 이벤트 보존 정책을 구성할 수 있습니다.
{:shortdesc}


## Activity Tracker CLI 설치
{: #install_cli}

{{site.data.keyword.cloudaccesstrailshort}} CLI를 설치하려면 다음 단계를 완료하십시오. 

1. {{site.data.keyword.Bluemix_notm}} CLI를 설치하십시오. 

    자세한 정보는 [쉘에서 설치](/docs/cli/reference/bluemix_cli/download_cli.html#shell_install)를 참조하십시오. 
	
	예를 들어, Linux에서 {{site.data.keyword.Bluemix_notm}} CLI를 설치하려면 다음 명령을 실행하십시오. 
	
	```
	curl -fsSL https://clis.ng.bluemix.net/install/linux | sh
	```
	{: codeblock}

2. {{site.data.keyword.cloudaccesstrailshort}} CF 플러그인을 설치하십시오. 

    * Linux의 경우에는 [Linux에서 {{site.data.keyword.cloudaccesstrailshort}} CLI 설치](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#install_cli_linux)를 참조하십시오. 
    * Windows의 경우에는 [Windows에서 {{site.data.keyword.cloudaccesstrailshort}} CLI 설치](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#install_cli_windows)를 참조하십시오. 
    * Mac OS X의 경우에는 [Mac OS X에서 {{site.data.keyword.cloudaccesstrailshort}} CLI 설치](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#install_cli_mac)를 참조하십시오. 
 
3. CLI 플러그인의 설치를 확인하십시오. 
  
    예를 들면, 플러그인의 버전을 확인하십시오. 다음 명령을 실행하십시오. 
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    출력은 다음과 같습니다. 
   
    ```
    Invoking 'cf plugins'...

    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}

	
## Linux에서 Activity Tracker CLI 설치
{: #install_cli_linux}

Linux에서 {{site.data.keyword.cloudaccesstrailshort}} CF 플러그인을 설치하려면 다음 단계를 완료하십시오. 

1. {{site.data.keyword.cloudaccesstrailshort}} CLI 플러그인을 설치하십시오. 

    1. [Bluemix CLI 페이지](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins)에서 최신 {{site.data.keyword.cloudaccesstrailshort}} 서비스 CLI 플러그인 릴리스를 다운로드하십시오.  
	
		플랫폼 값을 **linux64**로 선택하십시오.
		**파일 저장**을 클릭하십시오.  
    
    2. 플러그인의 압축을 푸십시오. 
    
        예를 들어, Ubuntu에서 `activitytracker-cli-linux_x64_v3.0.2.gz` 플러그인의 압축을 풀려면 다음 명령을 실행하십시오. 
        
        ```
        gunzip activitytracker-cli-linux_x64_v3.0.2.gz
        ```
        {: codeblock}

    3. 파일을 실행 가능하도록 설정하십시오. 
    
        예를 들어, 파일 `activitytracker-cli-linux_x64_v3.0.2`를 실행 가능하도록 설정하려면 다음 명령을 실행하십시오. 
        
        ```
        chmod a+x activitytracker-cli-linux_x64_v3.0.2
        ```
        {: codeblock}

    4. 로깅 CF 플러그인을 설치하십시오. 
    
        예를 들어, 파일 `activitytracker-cli-linux_x64_v3.0.2`를 실행 가능하도록 설정하려면 다음 명령을 실행하십시오. 
        
        ```
        bx cf install-plugin -f activitytracker-cli-linux_x64_v3.0.2
        ```
        {: codeblock}

2. CLI 플러그인의 설치를 확인하십시오. 
  
    예를 들면, 플러그인의 버전을 확인하십시오. 다음 명령을 실행하십시오. 
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    출력은 다음과 같습니다. 
   
    ```
    Invoking 'cf plugins'...

    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}


## Windows에서 Activity Tracker CLI 설치
{: #install_cli_windows}

Windows에서 {{site.data.keyword.cloudaccesstrailshort}} CF 플러그인을 설치하려면 다음 단계를 완료하십시오. 

1. [Bluemix CLI 페이지](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins)에서 최신 {{site.data.keyword.cloudaccesstrailshort}} 서비스 CLI 플러그인 릴리스를 다운로드하십시오.  
	
	1. 플랫폼 값을 **win64**로 선택하십시오.  
	2. **파일 저장**을 클릭하십시오.   
    
2. **cf install-plugins** 명령을 실행하여 Windows에서 {{site.data.keyword.cloudaccesstrailshort}} 플러그인을 설치하십시오.  

    ```
	bx cf install-plugin PluginName
	```
	{: codeblock}
	
	여기서 *PluginName*은 다운로드한 파일의 이름입니다.
	
    예를 들어, Windows에서 이 플러그인을 설치하려면 터미널 창에서 다음 명령을 실행하십시오.
	
	```
	bx cf install-plugin activitytracker-cli-windows_x64_v3.0.2.exe
	```
	{: codeblock}
	
    플러그인이 설치되면 `Plugin IBM-ActivityTracker successfully installed.`라는 메시지가 표시됩니다.

3. CLI 플러그인의 설치를 확인하십시오.

    예를 들면, 플러그인의 버전을 확인하십시오. 다음 명령을 실행하십시오.

    ```
    bx cf plugins
    ```
    {: codeblock}
    
    출력은 다음과 같습니다.

    ```
    Invoking 'cf plugins'...

    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}



## Mac OS X애서 Activity Tracker CLI 설치
{: #install_cli_mac}

Mac OS X에서 {{site.data.keyword.cloudaccesstrailshort}} CF 플러그인을 설치하려면 다음 단계를 완료하십시오.

1. [Bluemix CLI 페이지](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins)에서 최신 {{site.data.keyword.cloudaccesstrailshort}} 서비스 CLI 플러그인 릴리스를 다운로드하십시오.
	
	1. 플랫폼 값을 **osx**로 선택하십시오.
	2. **파일 저장**을 클릭하십시오.

2. **cf install-plugin** 명령을 실행하여 Mac OS X에서 {{site.data.keyword.cloudaccesstrailshort}} 플러그인을 설치하십시오.

    ```
	bx cf install-plugin PluginName
	```
	{: codeblock}
	
	여기서 *PluginName*은 다운로드한 파일의 이름입니다.
	
    예를 들어, Mac OS X에서 이 플러그인을 설치하려면 터미널 창에서 다음 명령을 실행하십시오.
	
	```
	bx cf install-plugin activitytracker-cli-mac_x64_v3.0.2
	```
	{: codeblock}
	
    플러그인이 설치되면 `Plugin IBM-ActivityTracker successfully installed.`라는 메시지가 표시됩니다.

3. CLI 플러그인의 설치를 확인하십시오.

    예를 들면, 플러그인의 버전을 확인하십시오. 다음 명령을 실행하십시오.

    ```
    bx cf plugins
    ```
    {: codeblock}
    
    출력은 다음과 같습니다.

    ```
    Invoking 'cf plugins'...

    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}

	

## Activity Tracker CLI 업데이트
{: #update_cli}

{{site.data.keyword.cloudaccesstrailshort}} CF 플러그인을 업데이트하려면 다음 단계를 완료하십시오.

1. [Bluemix CLI 페이지](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins)에서 최신 {{site.data.keyword.cloudaccesstrailshort}} 서비스 CLI 플러그인 릴리스를 다운로드하십시오.
	
	1. 플랫폼 값을 Windows의 경우에는 **win64**, Mac OS X의 경우에는 **osx**, Linux의 경우에는 **linux64**로 선택하십시오.
	2. **파일 저장**을 클릭하십시오.

2. **cf install-plugin** 명령을 실행하여 Windows에서 {{site.data.keyword.cloudaccesstrailshort}} 플러그인을 업데이트하십시오.

    ```
	bx cf install-plugin PluginName -f
	```
	{: codeblock}
	
	여기서,
	
	* *PluginName*은 다운로드한 파일의 이름입니다.
	* *-f*는 플러그인의 이전 버전을 설치 제거하고 새 버전을 설치할 것을 표시하는 옵션입니다.
	
    예를 들어, Windows에서 이 플러그인을 업데이트하려면 터미널 창에서 다음 명령을 실행하십시오.
	
	```
	bx cf install-plugin activitytracker-cli-windows_x64_v3.0.2.exe
	```
	{: codeblock}
	
    플러그인이 설치되면 `Plugin IBM-ActivityTracker successfully installed.`라는 메시지가 표시됩니다.

3. CLI 플러그인의 설치를 확인하십시오.

    예를 들면, 플러그인의 버전을 확인하십시오. 다음 명령을 실행하십시오.

    ```
    bx cf plugins
    ```
    {: codeblock}
    
    출력은 다음과 같습니다.

    ```
    Invoking 'cf plugins'...

    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}

	
	
## Activity Tracker CLI 설치 제거
{: #uninstall_cli}

{{site.data.keyword.cloudaccesstrailshort}} CLI를 설치 제거하려면 이 플러그인을 삭제하십시오.
{:shortdesc}

{{site.data.keyword.cloudaccesstrailshort}} 서비스 CLI를 설치 제거하려면 다음 단계를 완료하십시오.

1. 설치된 {{site.data.keyword.cloudaccesstrailshort}} CLI 플러그인의 버전을 확인하십시오.

    예를 들면, 플러그인의 버전을 확인하십시오. 다음 명령을 실행하십시오.

    ```
    bx cf plugins
    ```
    {: codeblock}
    
    출력은 다음과 같습니다.

    ```
    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2           at       IBM Activity Tracker plug-in
    ```
    {: screen}
    
2. 플러그인이 설치된 경우에는 `cf uninstall-plugin`을 실행하여 로깅 CLI 플러그인을 설치 제거하십시오.

    다음 명령을 실행하십시오.

    ```
    bx cf uninstall-plugin IBM-ActivityTracker
    ```
    {: codeblock}
  
