---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, UAA, security

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
{:deprecated: .deprecated}


# 取得 UAA 記號
{: #auth_uaa}

請使用 {{site.data.keyword.Bluemix}} UAA 來取得鑑別記號，您可利用它來使用 {{site.data.keyword.cloudaccesstraillong}} 服務。您可以使用 {{site.data.keyword.cloud_notm}} CLI 或使用 API 來取得鑑別記號。
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} 已淘汰。從 2019 年 5 月 9 日開始，您無法佈建新的 {{site.data.keyword.cloudaccesstrailshort}} 實例。現有的超值方案實例將支援到 2019 年 9 月 30 日為止。若要繼續監視 {{site.data.keyword.cloud_notm}} 帳戶的活動，請佈建 [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) 的實例。
{: deprecated}


請考量下列資訊：

* 記號具有有效期限。 
* 當您使用記號時，必須包括記號值中的 *Bearer*。
		
## 使用 IBM Cloud CLI 取得 UAA 記號
{: #uaa_cli_token}

若要取得 UAA 記號，請完成下列步驟：

1. （必要條件）安裝 {{site.data.keyword.cloud_notm}} CLI。

   如需相關資訊，請參閱[安裝 {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-ibmcloud-cli#ibmcloud-cli)。
   
   如果已安裝 CLI，請繼續進行下一步。
    
2. 登入 {{site.data.keyword.cloud_notm}}。 

    執行 [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) 指令以登入 {{site.data.keyword.cloud_notm}}，然後執行 [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) 指令，以設定您要在其中佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務的組織及空間。
	
3. 執行 `ibmcloud iam oauth-tokens` 指令以取得 UAA 記號。

    ```
	ibmcloud iam oauth-tokens
	```
	{: codeblock}
	
	輸出會傳回 UAA 記號。


	


## 使用 API 取得平台 API 金鑰的 UAA 記號
{: #apikey_uaa_token}

若要取得平台 API 金鑰的 UAA 記號，請完成下列步驟：

1. 取得授權端點。執行下列 cURL 指令：

    ```
    curl https://api.ng.bluemix.net/v2/info
    ```
    {: codeblock}

    在回應中，從 **authorization_endpoint** 欄位中擷取端點值。

2. 新增平台 API 金鑰。

    在「IBM Cloud 主控台」中，導覽至**管理 > 安全 > 平台 API 金鑰**。然後，建立「API 金鑰」。

3. 取得記號。執行下列 cURL 指令：

    ```
    curl --user "cf:" --data-urlencode "grant_type=password" --data-urlencode "username=apikey" --data-urlencode "password=$APIKEY" --header "Content-Type: application/x-www-form-urlencoded" --header "Accept: application/json" "AUTHORIZATION_ENDPOINT/oauth/token"
    ```
    {: codeblock}

    其中 
    
    *APIKEY* 是前一個步驟中取得的 apikey 值。
    
    *AUTHORIZATION_ENDPOINT* 代表 IAM 服務的進入點。

    例如：

    ```
    curl --user "cf:" --data-urlencode "grant_type=password" --data-urlencode "username=apikey" --data-urlencode "password=$APIKEY" --header "Content-Type: application/x-www-form-urlencoded" --header "Accept: application/json" "https://login.ng.bluemix.net/UAALoginServerWAR/oauth/token"
    ```
    {: codeblock}


