---

copyright:
  years: 2017, 2018

lastupdated: "2018-09-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}    
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# UAA 토큰 가져오기
{: #auth_uaa}

{{site.data.keyword.cloudaccesstraillong}} 서비스에 대해 작업하는 데 사용할 수 있는 인증 토큰을 가져오려면 {{site.data.keyword.Bluemix}} UAA를 사용하십시오. 인증 토큰은 {{site.data.keyword.Bluemix_notm}} CLI 또는 API를 사용하여 얻을 수 있습니다.
{:shortdesc}

다음 정보를 고려하십시오. 

* 토큰에는 만기 시간이 있습니다.  
* 토큰을 사용할 때는 토큰 값에 있는 *Bearer*가 포함되어야 합니다. 
		
## IBM Cloud CLI를 사용하여 UAA 토큰 가져오기
{: #uaa_cli_token}

UAA 토큰을 가져오려면 다음 단계를 완료하십시오. 

1. (전제조건) {{site.data.keyword.Bluemix_notm}} CLI를 설치하십시오. 

   자세한 정보는 [{{site.data.keyword.Bluemix_notm}} CLI 설치](/docs/cli/reference/ibmcloud/download_cli.html#install_use)를 참조하십시오. 
   
   CLI가 설치되어 있는 경우에는 다음 단계로 진행하십시오. 
    
2. {{site.data.keyword.Bluemix_notm}}에 로그인하십시오.  

    [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) 명령을 실행하여 {{site.data.keyword.Bluemix_notm}}에 로그인한 후 [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) 명령을 실행하여 {{site.data.keyword.cloudaccesstrailshort}} 서비스를 프로비저닝할 조직 및 영역을 설정하십시오. 
	
3. `ibmcloud iam oauth-tokens` 명령을 실행하여 UAA 토큰을 가져오십시오. 

    ```
	ibmcloud iam oauth-tokens
	```
	{: codeblock}
	
	출력은 UAA 토큰을 리턴합니다. 


	


## API를 사용하여 플랫폼 API 키에 대한 UAA 토큰 가져오기
{: #apikey_uaa_token}

플랫폼 API 키에 대한 UAA 토큰을 가져오려면 다음 단계를 완료하십시오. 

1. 권한 부여 엔드포인트를 가져오십시오. 다음 cURL 명령을 실행하십시오. 

    ```
    curl https://api.ng.bluemix.net/v2/info
    ```
    {: codeblock}

    응답에 있는 필드 **authorization_endpoint**에서 엔드포인트 값을 검색하십시오. 

2. 플랫폼 API 키를 추가하십시오. 

    IBM Cloud 콘솔에서 **관리 > 보안 > 플랫폼 API 키**로 이동하십시오.
    그런 다음 API 키를 작성하십시오. 

3. 토큰을 얻으십시오. 다음 cURL 명령을 실행하십시오. 

    ```
    curl --user "cf:" --data-urlencode "grant_type=password" --data-urlencode "username=apikey" --data-urlencode "password=$APIKEY" --header "Content-Type: application/x-www-form-urlencoded" --header "Accept: application/json" "AUTHORIZATION_ENDPOINT/oauth/token"
    ```
    {: codeblock}

    여기서, 
    
    *APIKEY*는 이전 단계에서 얻은 apikey 값입니다. 
    
    *AUTHORIZATION_ENDPOINT*는 IAM 서비스의 시작점을 나타냅니다. 

    예를 들면, 다음과 같습니다.

    ```
    curl --user "cf:" --data-urlencode "grant_type=password" --data-urlencode "username=apikey" --data-urlencode "password=$APIKEY" --header "Content-Type: application/x-www-form-urlencoded" --header "Accept: application/json" "https://login.ng.bluemix.net/UAALoginServerWAR/oauth/token"
    ```
    {: codeblock}


