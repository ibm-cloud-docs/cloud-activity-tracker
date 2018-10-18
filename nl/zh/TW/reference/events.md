---

copyright:
  years: 2016, 2018

lastupdated: "2018-07-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# {{site.data.keyword.cloudaccesstrailshort}} 事件
{: #events}

請使用 {{site.data.keyword.cloudaccesstrailfull}} 服務來追蹤 {{site.data.keyword.Bluemix}} 中的 {{site.data.keyword.cloudaccesstrailshort}}。
{:shortdesc}



## 事件清單
{: #actions}

下表列出產生事件的動作：

<table>
  <caption>表 1. 產生事件的動作清單</caption>
  <tr>
    <th>動作</th>
	  <th>說明</th>
  <tr>
  <tr>
    <td>read.events</td>
	  <td>取得所儲存事件的相關資訊。</td>
  </tr>
  <tr>
    <td>create.sessions</td>
	  <td>建立可用來下載事件的階段作業。</td>
  </tr>
  <tr>
    <td>delete.session</td>
	  <td>刪除階段作業。</td>
  </tr>
  <tr>
    <td>read.sessions</td>
	  <td>列出階段作業。</td>
  </tr>
  <tr>
    <td>download.events</td>
	  <td>下載事件。</td>
  </tr>
  <tr>
    <td>delete.events</td>
	  <td>刪除事件。</td>
  </tr>
</table>


## 尋找事件的位置
{: #ui}
 	
{{site.data.keyword.cloudaccesstrailshort}} 事件可在佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務的 Cloud Foundry 空間中取得。
