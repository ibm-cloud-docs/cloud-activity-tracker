---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-04"

keywords: IBM Cloud, Activity Tracker, launch Kibana

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
{:important: .important}
{:note: .note}



# Opening the Kibana dashboard
{: #launch_kibana}

You can launch Kibana from the {{site.data.keyword.cloudaccesstrailshort}} UI in the {{site.data.keyword.cloud_notm}}, or directly from a web browser.
{:shortdesc}
   

##  Opening Kibana from the dashboard of the Activity Tracker service
{: #launch_Kibana_from_at}

The activity logs that Kibana displays includes events for all the resources that are deployed within the space of the {{site.data.keyword.cloud_notm}} organization that you are logged in and where the {{site.data.keyword.cloudaccesstrailshort}} service is provisioned.

Complete the following steps to launch Kibana from the dashboard of the {{site.data.keyword.cloudaccesstrailshort}} service:

1. Log in to your {{site.data.keyword.cloud_notm}} account.

    The {{site.data.keyword.cloud_notm}} dashboard can be found at: [https://cloud.ibm.com/login ![External link icon](../../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/login){:new_window}.
    
	After you log in with your user ID and password, the {{site.data.keyword.cloud_notm}} UI opens.

2. Select the {{site.data.keyword.cloudaccesstrailshort}} service from the {{site.data.keyword.cloud_notm}} dashboard. 
    
3. Select the **Managed** tab.

4. To view space events, select **Space logs** for the *View Logs* field. **Note:** This is the default view. Then, click **View in Kibana**. 

    The Kibana dashboard opens. The **ActivityTracker_Space_Dashboard_in_24h** dashboard loads with a time filter set to the last 24 hours.

5. To view account events, select **Account logs** for the *View Logs* field. Then, click **View in Kibana**. 

    The **ActivityTracker_Account_Dashboard_in_24h** dashboard loads with a time filter set to the last 24 hours.
	
	
##  Opening Kibana from a web browser
{: #launch_Kibana_from_browser}

Complete the following steps to launch Kibana from a browser:

1. Open a web browser and launch Kibana in the region where you want to monitor events. Then, log in to the Kibana user interface.
    
    For example, the following table lists the URL that you must use to launch Kibana per region:
      
    <table>
          <caption>Table 1. URLs to launch Kibana per region</caption>
           <tr>
            <th>Region</th>
            <th>URL</th>
          </tr>
          <tr>
            <td>Germany</td>
            <td>[`https://logging.eu-fra.bluemix.net`](https://logging.eu-fra.bluemix.net) </td>
          </tr>
          <tr>
            <td>Sydney</td>
            <td>[`https://logging.au-syd.bluemix.net`](https://logging.au-syd.bluemix.net) </td>
          </tr>
		  <tr>
            <td>United Kingdom</td>
            <td>[`https://logging.eu-gb.bluemix.net`](https://logging.eu-gb.bluemix.net)</td>
          </tr>
		  <tr>
            <td>US South</td>
            <td>[`https://logging.ng.bluemix.net`](https://logging.ng.bluemix.net) </td>
          </tr>
    </table>
	
	The Discover page in Kibana opens.
	
2. Verify that you are logged in to the {{site.data.keyword.cloud_notm}} account where you want to view, and analyze activity events.

3. View space or account events

* Click on the upper right of the Kibana window where your login information is displayed.
* In **Domain** select space or account in the drop-down
* For space events, select the **space** of interest in the Space drop-down
* For account events, select the correct **account** in the Account drop-down

4. Adjust search time

* The Kibana default search time is set to the last 15 minutes.
* Click `Last 15 minutes` in the upper right gray bar
* Select how far back you want to see events. The last 3 days events are searchable. Pick a time frame 3 days or less.

5. Filter to show just Activity Tracker events
* You may encounter both Logs and Activity Tracker events when viewing directly in Kibana.
* In the search bar enter, `type:ActivityTracker` to show only Activity Tracker events.

The events that you see in Kibana correspond to the events that are hosted in the domain selected in the region where you have launched Kibana.

## Limitations
{: #launch_kibana_limitations}

* Due to limitations in Kibana, you cannot have multiple Kibana browser tabs open at once in the same session to view different spaces or accounts. Therefore, if you have two or more sessions open at once, and change the domain from space to account or viceversa, you may experience problems.
* By default, only the account owner can view account events. To enable others to view account events please follow the instructions in [Viewing account events](docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-view_acc_events#view_acc_events).



