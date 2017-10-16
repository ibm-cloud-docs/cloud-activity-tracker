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


# Provisioning the Activity Tracker service
{: #provision}

You can provision the {{site.data.keyword.cloudaccesstraillong}} service from {{site.data.keyword.Bluemix}} UI, or from the command line.
{:shortdesc}


## Provisioning from the UI
{: #ui}

Complete the following steps to provision an instance of the {{site.data.keyword.cloudaccesstraillong_notm}} service in {{site.data.keyword.Bluemix_notm}}:

1. Log in to your {{site.data.keyword.Bluemix_notm}} account.

    The {{site.data.keyword.Bluemix_notm}} dashboard can be found at: [http://bluemix.net ![External link icon](../../../icons/launch-glyph.svg "External link icon")](http://bluemix.net){:new_window}.
    
	After you log in with your user ID and password, the {{site.data.keyword.Bluemix_notm}} UI opens.

2. Click **Catalog**. The list of the services that are available on {{site.data.keyword.Bluemix_notm}} opens.

3. Select the **Security** category to filter the list of services that is displayed.

    The service is also available under the **DevOps** category.

4. Click the **Activity Tracker** tile.

5. Configure the information that defines where the service is going to be provisioned. 

    Enter the data as indicated in the following table: 

    <table>
	  <caption>Table 1. Fields that are required to provision the {{site.data.keyword.cloudaccesstrailshort}} service</caption>
	  <tr>
	    <th>Field</th>
		<th>Value</th>
	  </tr>
	  <tr>
	    <td>Select region to deploy in:</td>
		<td>Valid values are: US South, United Kingdom, Germany</td>
	  </tr>
	  <tr>
	    <td>Choose an organization:</td>
		<td>Select the organization where you plan to monitor activity.</td>
	  </tr>
	  <tr>
	    <td>Choose a space:</td>
		<td>Select the space in the organization that you have selected where you plan to monitor activity.</td>
	  </tr>
	</table>

6. Select a service plan. 

    By default, the **free** plan is set.

    For more information, see [Service plans](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#plans).
	
7. Click **Create** to provision the {{site.data.keyword.cloudaccesstrailshort}} service in the {{site.data.keyword.Bluemix_notm}} space where you are logged in.
  
 

## Provisioning from the CLI
{: #cli}

Complete the following steps to provision an instance of the {{site.data.keyword.cloudaccesstraillong_notm}} service in {{site.data.keyword.Bluemix_notm}} through the command line:

1. Install the Cloud Foundry (CF) CLI. If the CF CLI is installed, continue with the next step.

   For more information, see [Installing the cf CLI ![External link icon](../../../icons/launch-glyph.svg "External link icon")](http://docs.cloudfoundry.org/cf-cli/install-go-cli.html){: new_window}. 
    
2. Log in to a {{site.data.keyword.Bluemix_notm}} region, organization, and space. 

    For example, to log in to the US South region, run the following command:

    ```
    cf login -a https://api.ng.bluemix.net
    ```
    {: codeblock}

    Follow the instructions. Enter your {{site.data.keyword.Bluemix_notm}} credentials, select an organization and a space.
	
3. Run the `cf create-service` command to provision an instance.

    ```
	cf create-service service_name service_plan service_instance_name
	```
	{: codeblock}
	
	Where
	
	* service_name is the name of the service, that is, **activityTracker**.
	* service_plan is the service plan name. For a list of plans, see [Service plans](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#plans).
	* service_instance_name is the name that you want to use for the new service instance that you create.
	
	For more information about the cf command, see [cf create-service](/docs/cli/reference/cfcommands/index.html#cf_create-service).

	For example, to create an instance of the {{site.data.keyword.cloudaccesstrailshort}} service with the Lite plan, run the following command:
	
	```
	cf create-service activityTracker free my_activity_tracker_svc
	```
	{: codeblock}
	
4. Verify that the service is created successfully. Run the following command:

    ```	
	cf services
	```
	{: codeblock}
	
	The output of running the command looks as follows:
	
	```
    Getting services in org MyOrg / space MySpace as xxx@yyy.com...
    OK
    
    name                           service                  plan                   bound apps              last operation
    my_activity_tracker_svc        activityTracker          free                                           create succeeded
	```
	{: screen}

	



