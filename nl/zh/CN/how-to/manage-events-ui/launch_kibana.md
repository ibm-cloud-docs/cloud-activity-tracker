---

copyright:
  years: 2016, 2017

lastupdated: "2017-09-17"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# 导航至 Kibana 仪表板
{: #launch_kibana}

可以通过 {{site.data.keyword.Bluemix}} 中的 {{site.data.keyword.cloudaccesstrailshort}} UI 或直接通过 Web 浏览器启动 Kibana。
{:shortdesc}
   

##  通过 Activity Tracker 服务的仪表板导航至 Kibana
{: #launch_Kibana_from_at}

Kibana 显示的活动日志包含您登录到的 {{site.data.keyword.Bluemix_notm}} 组织空间中以及供应了 {{site.data.keyword.cloudaccesstrailshort}} 服务的 Bluemix 组织空间中部署的所有资源的事件。

要通过 {{site.data.keyword.cloudaccesstrailshort}} 服务的仪表板启动 Kibana，请完成以下步骤：

1. 登录到您的 {{site.data.keyword.Bluemix_notm}} 帐户。

    可在以下地址找到 {{site.data.keyword.Bluemix_notm}}“仪表板”：[http://bluemix.net ![外部链接图标](../../../../icons/launch-glyph.svg "外部链接图标")](http://bluemix.net){:new_window}。
    
	使用您的用户标识和密码登录后，{{site.data.keyword.Bluemix_notm}} UI 会打开。

2. 在 {{site.data.keyword.Bluemix_notm}}“仪表板”中，选择 {{site.data.keyword.cloudaccesstrailshort}} 服务。 
    
3. 选择**受管**选项卡。

4. 单击**高级视图**。 

    这将打开 Kibana 仪表板。

缺省情况下，将装入 **ActivityTracker_Space_Dashboard_in_24h** 仪表板，并且时间过滤器设置为最近 24 小时。 


	
	
##  通过 Web 浏览器导航至 Kibana
{: #launch_Kibana_from_browser}

Kibana 显示的日志信息包含您登录到的 {{site.data.keyword.Bluemix_notm}} 组织空间中部署的所有资源的事件。

要通过浏览器启动 Kibana，请完成以下步骤：

1. 打开 Web 浏览器并启动 Kibana。然后，登录到 Kibana 用户界面。
    
    例如，下表列出在每个区域启动 Kibana 时必须使用的 URL：
      
    <table>
          <caption>表 1. 用于在每个区域启动 Kibana 的 URL</caption>
           <tr>
            <th>区域</th>
            <th>URL</th>
          </tr>
          <tr>
            <td>美国南部</td>
            <td>[https://logging.ng.bluemix.net](https://logging.ng.bluemix.net)</td>
          </tr>
		  <tr>
            <td>英国</td>
            <td>[https://logmet.eu-gb.bluemix.net](https://logmet.eu-gb.bluemix.net)</td>
          </tr>
    </table>
	
	这将打开 Kibana 中的“发现”页面。
	
2. 验证您是否已登录到要查看和分析其活动日志的 {{site.data.keyword.Bluemix_notm}} 帐户、组织和空间。

    您可以看到在登录到的空间中可用的事件和日志。

3. 要过滤事件，请从菜单栏中选择**打开**。

    这将显示已保存仪表板的列表。
	
4. 要查看您登录到的空间的事件，请选择 **ActivityTracker_Space_Dashboard_in_24h**。


## 限制
{: #limitations}

 由于 Kibana 中的限制，您不能在同一会话中同时打开多个 Kibana 浏览器选项卡来查看不同的空间或帐户。因此，如果同时打开两个或更多会话，并将域从空间更改为帐户或从帐户更改为空间，那么可能会遇到问题。
	



