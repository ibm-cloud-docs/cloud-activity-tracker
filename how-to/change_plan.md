---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, change plan

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
{:deprecated: .deprecated}


# Changing the plan
{: #change_plan}

You can change your {{site.data.keyword.cloudaccesstraillong}} service plan through the {{site.data.keyword.cloud_notm}} UI or by running the `ibmcloud service update` command. You can upgrade or reduce your plan at any time.
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} is deprecated. As of 9 May 2019, you cannot provision new {{site.data.keyword.cloudaccesstrailshort}} instances. Existing premium plan instances are supported until 30 September 2019. To continue monitoring the activity of your {{site.data.keyword.cloud_notm}} account, provision an instance of the [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}

## Changing the service plan through the UI
{: #change_plan_ui}

To change your service plan through the {{site.data.keyword.cloud_notm}} UI, complete the following steps:

1. Log in to  the {{site.data.keyword.cloud_notm}}, and then click the {{site.data.keyword.cloudaccesstraillong_notm}} service from the *Dashboard*. 
    
2. Select the **Plan** tab.

    Information about your current plan is displayed.
	
3. Select a new plan to either upgrade or reduce your plan. 

4. Click **Save**.



## Changing the service plan through the CLI
{: #change_plan_cli}

To change your service plan through the CLI, complete the following steps:

1. Log in to the {{site.data.keyword.cloud_notm}}. 

    Run the [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) command to log in to the {{site.data.keyword.cloud_notm}}, and then, run the [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) command to set the organization and space where you want to provision the {{site.data.keyword.cloudaccesstrailshort}} service.
	
2. Run the `ibmcloud service list` command to check your current plan, and to get the {{site.data.keyword.cloudaccesstrailshort}} service name from the list of services that is available in the space. 

    The value of the field **name** is the one that you must use to change the plan. 

    For example,
	
	```
	$ ibmcloud service list
    Invoking 'cf services'...

    Getting services in org MyOrg / space dev as xxx@ibm.com...
    OK

    name                       service                  plan                 bound apps                               last operation
    Activity Tracker-zt          OK                     accessTrail             premium                                update succeeded
    ```
	{: screen}
    
3. Upgrade or reduce your plan. Run the `ibmcloud service update` command.
    
	```
	ibmcloud service update service_name [-p new_plan]
	```
	{: codeblock}
	
	where 
	
	* *service_name* is the name of your service. You can run the `ibmcloud service list` command to get the value.
	* *new_plan* is the name of the plan.
	
	
	The following table lists the different plans and their supported values:
	
	<table>
	  <caption>Table 1. List of plans.</caption>
	  <tr>
	    <th>Plan</th>
	    <th>Name</th>
	  </tr>
	  <tr>
	    <td>Lite</td>
	    <td>free</td>
	  </tr>
	  <tr>
	    <td>Premium</td>
	    <td>premium</td>
	  </tr>
	</table>
	
	For example, to reduce your plan to the *Lite* plan, run the following command:
	
	```
	ibmcloud service update "Activity Tracker-zt" -p free
    Updating service instance Activity Tracker-zt as xxx@ibm.com...
    OK
	```
	{: screen}



