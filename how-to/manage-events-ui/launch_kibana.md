---

copyright:
  years: 2016, 2018
lastupdated: "2018-04-27"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}



# Navigating to the Kibana dashboard
{: #launch_kibana}

You can launch Kibana from the {{site.data.keyword.cloudaccesstrailshort}} UI in the {{site.data.keyword.Bluemix}}, or directly from a web browser.
{:shortdesc}
   

##  Navigating to Kibana from the dashboard of the Activity Tracker service
{: #launch_Kibana_from_at}

The activity logs that Kibana displays includes events for all the resources that are deployed within the space of the {{site.data.keyword.Bluemix_notm}} organization that you are logged in and where the {{site.data.keyword.cloudaccesstrailshort}} service is provisioned.

Complete the following steps to launch Kibana from the dashboard of the {{site.data.keyword.cloudaccesstrailshort}} service:

1. Log in to your {{site.data.keyword.Bluemix_notm}} account.

    The {{site.data.keyword.Bluemix_notm}} dashboard can be found at: [http://bluemix.net ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://bluemix.net){:new_window}.
    
	After you log in with your user ID and password, the {{site.data.keyword.Bluemix_notm}} UI opens.

2. Select the {{site.data.keyword.cloudaccesstrailshort}} service from the {{site.data.keyword.Bluemix_notm}} dashboard. 
    
3. Select the **Managed** tab.

4. Click **Advanced view**. 

    The Kibana dashboard opens.

By default, the **ActivityTracker_Space_Dashboard_in_24h** dashboard loads, and a time filter set to the last 24 hours. 


	
	
##  Navigating to Kibana from a web browser
{: #launch_Kibana_from_browser}

The log information that Kibana displays includes events for all the resources that are deployed within the space of the {{site.data.keyword.Bluemix_notm}} organization that you are logged in.

Complete the following steps to launch Kibana from a browser:

1. Open a web browser and launch Kibana. Then, log in to the Kibana user interface.
    
    For example, the following table lists the URL that you must use to launch Kibana per region:
      
    <table>
          <caption>Table 1. URLs to launch Kibana per region</caption>
           <tr>
            <th>Region</th>
            <th>URL</th>
          </tr>
          <tr>
            <td>Germany</td>
            <td>[https://logging.eu-fra.bluemix.net](https://logging.eu-fra.bluemix.net) </td>
          </tr>
          <tr>
            <td>Sydney</td>
            <td>[https://logging.au-syd.bluemix.net](https://logging.au-syd.bluemix.net) </td>
          </tr>
		  <tr>
            <td>United Kingdom</td>
            <td>[https://logging.eu-gb.bluemix.net](https://logging.eu-gb.bluemix.net)</td>
          </tr>
		  <tr>
            <td>US South</td>
            <td>[https://logging.ng.bluemix.net](https://logging.ng.bluemix.net) </td>
          </tr>
    </table>
	
	The Discover page in Kibana opens.
	
2. Verify that you are logged in to the {{site.data.keyword.Bluemix_notm}} account, organization, and space where you want to view, and analyze activity logs.

    You can see events and logs that are available in the space where you are logged in.

3. To filter for events, select **Open** from the menu bar.

    The list of saved dashboards is displayed.
	
4. To view the events for the space where you are logged in, select **ActivityTracker_Space_Dashboard_in_24h**.


## Limitations
{: #limitations}

 Due to limitations in Kibana, you cannot have multiple Kibana browser tabs open at once in the same session to view different spaces or accounts. Therefore, if you have two or more sessions open at once, and change the domain from space to account or viceversa, you may experience problems.
	



