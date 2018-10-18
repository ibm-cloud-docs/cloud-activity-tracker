---

copyright:
  years: 2016, 2018
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


# 刪除事件
{: #deleting_events}

請使用 *ibmcloud at delete* 指令來手動刪除儲存在 {{site.data.keyword.cloudaccesstrailshort}} 中的事件。
{:shortdesc}

請完成下列步驟：

## 步驟 1：登入 {{site.data.keyword.Bluemix_notm}}
{: #prereq}

登入 {{site.data.keyword.Bluemix_notm}}。請完成下列步驟：

1. 執行 [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) 指令以登入 {{site.data.keyword.Bluemix_notm}}。
2. 執行 [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) 指令，以設定您要在其中佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務的組織及空間。

**附註：**設定在其中佈建 {{site.data.keyword.cloudaccesstrailshort}} 的組織及空間。

## 步驟 2：識別可用的事件
{: #step2}

請使用 `ibmcloud at status` 指令來查看空間網域中可用事件的相關資訊。

* 若要取得空間網域中事件的相關資訊，請執行 `ibmcloud at status` 指令。
* 若要取得帳戶網域中事件的相關資訊，請執行 `ibmcloud at status` 指令並搭配 `-a` 選項。

如需相關資訊，請參閱[檢視事件資訊](/docs/services/cloud-activity-tracker/how-to/viewing_event_information.html#viewing_event_status)。
	
  
## 步驟 3：刪除事件
{: #step3}
	
若要刪除事件，請執行 ``ibmcloud at delete`` 指令。

```
ibmcloud at delete -s YYYY-MM-DD -e YYYY-MM-DD 
```
{: codeblock}
    
其中

* *-s* 用來以「世界標準時間 (UTC) 」設定開始日期：*YYYY-MM-DD*。
* *-e* 用來以「世界標準時間 (UTC) 」設定結束日期：*YYYY-MM-DD*。

例如，若要刪除 2017 年 6 月 10 日的事件，請執行下列指令：

```
ibmcloud at delete -s 2017-06-10 -e 2017-06-10
```
{: screen}

您會收到已刪除之事件記錄的相關資訊。










