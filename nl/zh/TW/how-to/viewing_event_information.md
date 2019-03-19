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


# 檢視事件資訊
{: #viewing_event_status}

請使用 `ibmcloud at status` 指令來取得 {{site.data.keyword.Bluemix}} 空間的 {{site.data.keyword.cloudaccesstrailshort}} 中所收集並儲存之事件的相關資訊。
{:shortdesc}

您可以取得事件日誌大小、記錄數，以及事件是否可在 Kibana 中進行分析的相關資訊。 

請完成下列步驟，以檢視事件日誌的相關資訊：

## 步驟 1：登入 {{site.data.keyword.cloud_notm}}
{: #viewing_event_status_step1}

登入 {{site.data.keyword.cloud_notm}}。請完成下列步驟：

1. 執行 [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) 指令以登入 {{site.data.keyword.cloud_notm}}。
2. 執行 [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) 指令，以設定您要在其中佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務的組織及空間。

**附註：**設定在其中佈建 {{site.data.keyword.cloudaccesstrailshort}} 的組織及空間。

## 步驟 2：識別可用的事件
{: #viewing_event_status_step2}

請使用 `ibmcloud at status` 指令來查看空間網域中可用事件的相關資訊。

* 若要取得空間網域中事件的相關資訊，請執行 `ibmcloud at status` 指令。
* 若要取得帳戶網域中事件的相關資訊，請執行 `ibmcloud at status` 指令並搭配 `-a` 選項。

```
$ ibmcloud at status -a -s YYYY-MM-DD -e YYYY-MM-DD
```
{: codeblock}
    
其中
    
* *-a* 用來指定要求適用於帳戶網域。
* *-s* 用來以「世界標準時間 (UTC) 」設定開始日期：*YYYY-MM-DD*。
* *-e* 用來以「世界標準時間 (UTC) 」設定結束日期：*YYYY-MM-DD*。

例如，若要查看空間網域中過去 2 週可用的事件，請執行下列指令：

```
$ ibmcloud at status
```
{: codeblock}
    
例如，執行這個指令的輸出為：
    
```
+------------+--------+------------+
|    DATE    |  COUNT | SEARCHABLE |
+------------+--------+------------+
| 2017-07-24 |    16  |    None    |
+------------+--------+------------+
| 2017-07-25 |   1224 |    All     |
+------------+--------+------------+
```
{: screen}

**附註：**{{site.data.keyword.cloudaccesstrailshort}} 服務是使用「世界標準時間 (UTC)」的廣域服務。「日」的定義為 UTC 日。若要取得當地時間之特定日的事件，您可能需要下載多個 UTC 日。
	














