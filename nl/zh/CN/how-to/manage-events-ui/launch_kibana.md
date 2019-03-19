---

copyright:
  years: 2016, 2019
lastupdated: "2019-01-23"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}



# 导航至 Kibana 仪表板
{: #launch_kibana}

您可以通过 {{site.data.keyword.Bluemix}} 中的 {{site.data.keyword.cloudaccesstrailshort}} UI 或直接通过 Web 浏览器启动 Kibana。
{:shortdesc}
   

##  通过 Activity Tracker 服务的仪表板导航至 Kibana
{: #launch_Kibana_from_at}

Kibana 显示的活动日志包含您登录到的 {{site.data.keyword.cloud_notm}} 组织空间中以及供应了 {{site.data.keyword.cloudaccesstrailshort}} 服务的 Bluemix 组织空间中部署的所有资源的事件。

要通过 {{site.data.keyword.cloudaccesstrailshort}} 服务的仪表板启动 Kibana，请完成以下步骤：

1. 登录到您的 {{site.data.keyword.cloud_notm}} 帐户。

    可在以下地址找 {{site.data.keyword.cloud_notm}} 仪表板：[https://cloud.ibm.com/login ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://cloud.ibm.com/login){:new_window}。
    
	使用您的用户标识和密码登录后，{{site.data.keyword.cloud_notm}} UI 会打开。

2. 在 {{site.data.keyword.cloud_notm}} 仪表板中选择 {{site.data.keyword.cloudaccesstrailshort}} 服务。 
    
3. 选择**受管**选项卡。

4. 要查看空间事件，请为*查看日志*字段选择**空间日志**。**注：**此选项为缺省视图。然后，单击**在 Kibana 中查看**。 

    这将打开 Kibana 仪表板。**ActivityTracker_Space_Dashboard_in_24h** 仪表板将通过设置为最近 24 小时的时间过滤器加载数据。

5. 要查看帐户事件，请为*查看日志*字段选择**帐户日志**。然后，单击**在 Kibana 中查看**。 

    **ActivityTracker_Account_Dashboard_in_24h** 仪表板将通过设置为最近 24 小时的时间过滤器加载数据。
	
	
##  通过 Web 浏览器导航至 Kibana
{: #launch_Kibana_from_browser}

要通过浏览器启动 Kibana，请完成以下步骤：

1. 打开 Web 浏览器并在要在其中监视事件的区域中启动 Kibana。然后，登录到 Kibana 用户界面。
    
    例如，下表列出在每个区域启动 Kibana 时必须使用的 URL：
      
    <table>
          <caption>表 1. 用于在每个区域启动 Kibana 的 URL</caption>
           <tr>
            <th>区域</th>
            <th>URL</th>
          </tr>
          <tr>
            <td>德国</td>
            <td>[https://logging.eu-fra.bluemix.net](https://logging.eu-fra.bluemix.net)</td>
          </tr>
          <tr>
            <td>悉尼</td>
            <td>[https://logging.au-syd.bluemix.net](https://logging.au-syd.bluemix.net)</td>
          </tr>
		  <tr>
            <td>英国</td>
            <td>[https://logging.eu-gb.bluemix.net](https://logging.eu-gb.bluemix.net)</td>
          </tr>
		  <tr>
            <td>美国南部</td>
            <td>[https://logging.ng.bluemix.net](https://logging.ng.bluemix.net)</td>
          </tr>
    </table>
	
	这将打开 Kibana 中的“发现”页面。
	
2. 验证您是否已登录到要在其中查看并分析活动事件的 {{site.data.keyword.cloud_notm}} 帐户中。

3. 选择一个**域**。

    选择**帐户**可在帐户域中查看事件。选择**空间**可在空间域中查看事件。

在 Kibana 中显示的事件对应于启动了 Kibana 的区域中所选择域中托管的事件。


## 限制
{: #launch_kibana_limitations}

 由于 Kibana 中的限制，您不能在同一会话中同时打开多个 Kibana 浏览器选项卡来查看不同的空间或帐户。因此，如果同时打开两个或更多会话，并将域从空间更改为帐户或从帐户更改为空间，那么可能会遇到问题。
	



