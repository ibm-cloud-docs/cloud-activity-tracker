---

copyright:
  years: 2017
lastupdated: "2017-11-09"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# Changing the plan
{: #change_plan}

You can change your {{site.data.keyword.cloudaccesstraillong}} service plan through the {{site.data.keyword.Bluemix_notm}} UI or by running the `bx cf update-service` command. You can upgrade or reduce your plan at any time.
{:shortdesc}

## Changing the service plan through the UI
{: #change_plan_ui}

To change your service plan through the {{site.data.keyword.Bluemix_notm}} UI, complete the following steps:

1. Log in to  the {{site.data.keyword.Bluemix_notm}}, and then click the {{site.data.keyword.cloudaccesstraillong_notm}} service from the *Dashboard*. 
    
2. Select the **Plan** tab.

    Information about your current plan is displayed.
	
3. Select a new plan to either upgrade or reduce your plan. 

4. Click **Save**.



## Changing the service plan through the CLI
{: #change_plan_cli}

To change your service plan through the CLI, complete the following steps:

1. Log in to a region, organization, and space in the {{site.data.keyword.Bluemix_notm}}. 

    For more information, see [How do I log in to the {{site.data.keyword.Bluemix_notm}}](/docs/services/cloud-activity-tracker/qa/cli_qa.html#login).
	
2. Run the `bx cf services` command to check your current plan, and to get the {{site.data.keyword.cloudaccesstrailshort}} service name from the list of services that is available in the space. 

    The value of the field **name** is the one that you must use to change the plan. 

    For example,
	
	```
	$ bx cf services
    Getting services in org MyOrg / space dev as xxx@yyy.com...
    OK
    
    name                            service              plan          bound apps      last operation
    Activity Tracker-oj            activityTracker       premium                       create succeeded
    ```
	{: screen}
    
3. Upgrade or reduce your plan. Run the `bx cf update-service` command.
    
	```
	bx cf update-service service_name [-p new_plan]
	```
	{: codeblock}
	
	where 
	
	* *service_name* is the name of your service. You can run the `cf services` command to get the value.
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
	    <td>lite</td>
	  </tr>
	  <tr>
	    <td>Premium</td>
	    <td>premium</td>
	  </tr>
	</table>
	
	For example, to reduce your plan to the *Lite* plan, run the following command:
	
	```
	bx cf update-service "Activity Tracker-oj" -p lite
    Updating service instance Activity Tracker-oj as xxx@yyy.com...
    OK
	```
	{: screen}

4. Verify the new plan is changed. Run the `cf services` command.

    ```
	bx cf services
    Getting services in org MyOrg / space dev as xxx@yyy.com...
    OK

    name                   service            plan      bound apps   last operation
    Activity Tracker-oj    activityTracker    lite                   update succeeded
	```
	{: screen}





