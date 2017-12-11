---

copyright:
  years: 2016, 2017
lastupdated: "2017-09-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Activity Tracker CLI 사용 방법에 대한 도움말 보기
{: #get_help_cli}

{{site.data.keyword.cloudaccesstrailshort}} CLI에서는 CLI 및 지원되는 명령에 대해 알려주는 일반 도움말, 명령 사용 방법에 대해 알려주는 명령 도움말, 명령의 하위 명령 사용 방법을 알려주는 하위 명령 도움말과 같은 다양한 유형의 도움말을 제공합니다.
{:shortdesc}


## 일반 도움말 보기
{: #general_cli_help}

CLI와 지원되는 명령에 대한 일반 정보를 가져오려면 다음 단계를 완료하십시오. 

1. {{site.data.keyword.Bluemix_notm}} 지역, 조직 및 영역에 로그인하십시오.  

    예를 들어, 미국 남부 지역에 로그인하려면 다음 명령을 실행하십시오. 
	
	```
    bx login -a https://api.ng.bluemix.net
    ```
    {: codeblock}
    
2. 지원되는 명령 및 CLI에 대한 정보를 나열하십시오. 다음 명령을 실행하십시오. 

    ```
    bx cf at help 
    ```
    {: codeblock}
    
    

## 명령에 대한 도움말 보기
{: #command_cli_help}

특정 명령을 사용하는 방법에 대한 도움말을 보려면 다음 단계를 완료하십시오. 

1. {{site.data.keyword.Bluemix_notm}} 지역, 조직 및 영역에 로그인하십시오.  

    예를 들어, 미국 남부 지역에 로그인하려면 다음 명령을 실행하십시오. 
	
	```
    bx login -a https://api.ng.bluemix.net
    ```
    {: codeblock}
    
2. 지원되는 명령의 목록을 보고 필요한 명령을 식별하십시오. 다음 명령을 실행하십시오. 

    ```
    bx cf at help 
    ```
    {: codeblock}

3. 해당 명령에 대한 도움말을 보십시오. 다음 명령을 실행하십시오. 

    ```
    bx cf at help *Command*
    ```
    {: codeblock}
    
    여기서 *Command*는 CLI 명령의 이름(예: *status*)입니다. 



## 하위 명령에 대한 도움말 보기
{: #subcommand_cli_help}

특정 명령에는 하위 명령이 있을 수 있습니다. 하위 명령에 대한 도움말을 보려면 다음 단계를 완료하십시오. 

1. {{site.data.keyword.Bluemix_notm}} 지역, 조직 및 영역에 로그인하십시오.  

    예를 들어, 미국 남부 지역에 로그인하려면 다음 명령을 실행하십시오. 
	
	```
    bx login -a https://api.ng.bluemix.net
    ```
    {: codeblock}
    
2. 지원되는 명령의 목록을 보고 필요한 명령을 식별하십시오. 다음 명령을 실행하십시오. 

    ```
    bx cf at help 
    ```
    {: codeblock}

3. 해당 명령에 대한 도움말을 보고 지원되는 하위 명령을 식별하십시오. 다음 명령을 실행하십시오. 

    ```
    bx cf at help *Command*
    ```
    {: codeblock}
    
    여기서 *Command*는 CLI 명령의 이름(예: *session*)입니다. 

4. 해당 명령에 대한 도움말을 보고 지원되는 하위 명령을 식별하십시오. 다음 명령을 실행하십시오. 

    ```
    bx cf at *Command* help *Subcommand*
    ```
    {: codeblock}
    
    여기서,
 
    
    * 여기서 *Command*는 CLI 명령의 이름(예: *status*)입니다. 
    * *Subcommand*는 지원되는 하위 명령의 이름(예: 명령 *session*의 경우 유효한 하위 명령은 *list*)입니다. 




