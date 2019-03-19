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


# 获取 UAA 令牌
{: #auth_uaa}

使用 {{site.data.keyword.Bluemix}} UAA，获取可用于 {{site.data.keyword.cloudaccesstraillong}} 服务的认证令牌。您可以使用 {{site.data.keyword.cloud_notm}} CLI 或 API 获取认证令牌。
{:shortdesc}

请考虑以下信息：

* 该令牌有到期时间。 
* 使用令牌时，必须包含令牌值中的 *Bearer*。
		
## 使用 IBM Cloud CLI 获取 UAA 令牌
{: #uaa_cli_token}

要获取 UAA 令牌，请完成以下步骤：

1. （先决条件）安装 {{site.data.keyword.cloud_notm}} CLI。

   有关更多信息，请参阅[安装 {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-ibmcloud-cli#ibmcloud-cli)。
   
   如果 CLI 已安装，请继续执行下一步。
    
2. 登录到 {{site.data.keyword.cloud_notm}}。 

    运行 [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) 命令以登录到 {{site.data.keyword.cloud_notm}}，然后运行 [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) 命令以设置要在其中供应 {{site.data.keyword.cloudaccesstrailshort}} 服务的组织和空间。
	
3. 运行 `ibmcloud iam oauth-tokens` 命令以获取 UAA 令牌。

    ```
	ibmcloud iam oauth-tokens
	```
	{: codeblock}
	
	输出返回 UAA 令牌。


	


## 使用 API 获取平台 API 密钥的 UAA 令牌
{: #apikey_uaa_token}

要获取平台 API 密钥的 UAA 令牌，请完成以下步骤：

1. 获取授权端点。运行以下 cURL 命令：

    ```
    curl https://api.ng.bluemix.net/v2/info
    ```
    {: codeblock}

    在响应中，从字段 **authorization_endpoint** 检索端点值。

2. 添加平台 API 密钥。

    在 IBM Cloud 控制台中，浏览到**管理 > 安全性 > 平台 API 密钥**。然后，创建 API 密钥。

3. 获取令牌。运行以下 cURL 命令：

    ```
    curl --user "cf:" --data-urlencode "grant_type=password" --data-urlencode "username=apikey" --data-urlencode "password=$APIKEY" --header "Content-Type: application/x-www-form-urlencoded" --header "Accept: application/json" "AUTHORIZATION_ENDPOINT/oauth/token"
    ```
    {: codeblock}

    其中
 
    
    *APIKEY* 是在上一步中获取的 apikey 值。
    
    *AUTHORIZATION_ENDPOINT* 表示 IAM 服务的入口点。

    例如：

    ```
    curl --user "cf:" --data-urlencode "grant_type=password" --data-urlencode "username=apikey" --data-urlencode "password=$APIKEY" --header "Content-Type: application/x-www-form-urlencoded" --header "Accept: application/json" "https://login.ng.bluemix.net/UAALoginServerWAR/oauth/token"
    ```
    {: codeblock}


