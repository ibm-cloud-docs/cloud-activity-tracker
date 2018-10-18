---

copyright:
  years: 2017, 2018

lastupdated: "2018-07-09"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# 授與許可權以檢視事件
{: #grant_permissions}

在 {{site.data.keyword.Bluemix}} 中，您可以將 Cloud Foundry 角色、IAM 角色或這兩者指派給使用者。這些角色可定義使用者在使用 {{site.data.keyword.cloudaccesstrailshort}} 服務時可以執行的作業。  
{:shortdesc}

## 授與許可權以查看帳戶事件
{: #grant_acc_events}

授與使用者下列許可權，以查看地區中的帳戶事件：

1. 佈建 {{site.data.keyword.cloudaccesstrailshort}} 之地區空間的*開發人員* 角色。 

    如需相關資訊，請參閱[授與 CF 角色](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_cf_role)。

2. {{site.data.keyword.loganalysisshort}} 服務的 IAM 原則，其含有地區的*檢視者* 角色。 

    「檢視者」角色是必要的最小 IAM 角色。 
	
	如需相關資訊，請參閱[授與 IAM 許可權](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_iam_policy)。


## 授與許可權以查看空間事件
{: #grant_space_events}

授與使用者下列許可權，以查看地區中的空間事件：

* 佈建 {{site.data.keyword.cloudaccesstrailshort}} 之地區空間的*開發人員* 角色。 

    如需相關資訊，請參閱[授與 CF 角色](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_cf_role)。


## 授與 IAM 許可權
{: #grant_iam_policy}

若要授與使用者 IAM 角色，請考量下列資訊：

* 您必須具有許可權可以將原則指派給帳戶中的其他使用者，或者您必須是帳戶擁有者。如果您不是帳戶擁有者，則必須具有含**管理者**角色的 IAM 原則，才能執行 {{site.data.keyword.loganalysisshort}} 服務。

* 當您定義原則時，您指定的地區會定義授與使用者檢視帳戶網域事件存取權的地區。

請完成下列步驟，以授與使用者許可權來檢視帳戶網域中的事件：

1. 登入 {{site.data.keyword.Bluemix_notm}} 主控台。

    開啟 Web 瀏覽器，並啟動 {{site.data.keyword.Bluemix_notm}} 儀表板：[http://bluemix.net ![外部鏈結圖示](../../../icons/launch-glyph.svg "外部鏈結圖示")](http://bluemix.net){:new_window}
	
	使用您的使用者 ID 及密碼登入之後，會開啟 {{site.data.keyword.Bluemix_notm}} 使用者介面。

2. 從功能表列中，按一下**管理 > 帳戶 > 使用者**。 

    *使用者* 視窗會顯示目前所選取帳戶的使用者及其電子郵件位址的清單。
	
3. 如果使用者是帳戶成員，請從清單中選取使用者名稱，或按一下*動作* 功能表中的**管理使用者**。

    如果使用者不是帳戶的成員，請參閱[邀請使用者](/docs/iam/iamuserinv.html#iamuserinv)。

4. 在**存取原則**區段中，按一下**指派存取權**，然後選取**指派資源的存取權**。

    即會開啟*將資源存取權指派給使用者* 視窗。

5. 輸入原則的相關資訊。下表列出可定義原則的必要欄位： 

    <table>
	  <caption>配置 IAM 原則的欄位清單。</caption>
	  <tr>
	    <th>欄位</th>
		<th>值</th>
	  </tr>
	  <tr>
	    <td>服務</td>
		<td>*IBM Cloud Log Analysis*</td>
	  </tr>	  
	  <tr>
	    <td>地區</td>
		<td>您可以指定將授與使用者使用事件存取權的地區。個別選取一個以上的地區，或選取**所有現行地區**以將存取權授與所有地區。</td>
	  </tr>
	  <tr>
	    <td>服務實例</td>
		<td>選取*所有服務實例*。</td>
	  </tr>
	  <tr>
	    <td>角色</td>
		<td>選取一個以上的 IAM 角色。<br>有效角色包含：*管理者*、*操作員*、*編輯者* 及*檢視者*。</td>
	  </tr>
     </table>
	
6. 按一下**指派**。
	
配置的原則適用於選取的地區。 


## 授與 CF 角色
{: #grant_cf_role}

若要授與使用者 CF 角色，請考量下列資訊：

* 您必須具有組織及空間的許可權，才能將 Cloud Foundry 角色指派給使用者。 

* 只有**開發人員**角色可讓使用者檢視事件。

請完成下列步驟，以授與使用者檢視空間事件的存取權：

1. 登入 {{site.data.keyword.Bluemix_notm}} 主控台。

    開啟 Web 瀏覽器，並啟動 {{site.data.keyword.Bluemix_notm}} 儀表板：[http://bluemix.net ![外部鏈結圖示](../../../icons/launch-glyph.svg "外部鏈結圖示")](http://bluemix.net){:new_window}
	
	使用您的使用者 ID 及密碼登入之後，會開啟 {{site.data.keyword.Bluemix_notm}} 使用者介面。

2. 從功能表列中，按一下**管理 > 帳戶 > 使用者**。 

    *使用者* 視窗會顯示目前所選取帳戶的使用者及其電子郵件位址的清單。
	
3. 如果使用者是帳戶成員，請從清單中選取使用者名稱，或按一下*動作* 功能表中的**管理使用者**。

    如果使用者不是帳戶的成員，請參閱[邀請使用者](/docs/iam/iamuserinv.html#iamuserinv)。

4. 選取 **Cloud Foundry 存取**，然後選取組織。

    即會列出該組織中可用的空間清單。

5. 選擇一個空間。然後，從功能表動作中，選取**編輯空間角色**。

6. 選取**開發人員**。
	
7. 按一下**儲存角色**。




