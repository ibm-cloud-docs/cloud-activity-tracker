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



# Provisioning Activity Tracker
{: #provision}

You can provision the {{site.data.keyword.cloudaccesstraillong}} service from the {{site.data.keyword.Bluemix}} UI, or from the command line.
{:shortdesc}


## Provisioning from the UI
{: #ui}

Complete the following steps to provision an instance of the {{site.data.keyword.cloudaccesstraillong_notm}} service in {{site.data.keyword.Bluemix_notm}}:

1. Log in to your {{site.data.keyword.Bluemix_notm}} account.

    The {{site.data.keyword.Bluemix_notm}} UI can be found at: [http://bluemix.net ![External link icon](../../../icons/launch-glyph.svg "External link icon")](http://bluemix.net){:new_window}.
    
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
		<td>Valid values are: US South, United Kingdom, Germany, Sydney</td>
	  </tr>
	  <tr>
	    <td>Choose an organization:</td>
		<td>Select the organization where you plan to monitor activity.</td>
	  </tr>
	  <tr>
	    <td>Choose a space:</td>
		<td>Select a space in the organization that you have selected where you plan to monitor activity.</td>
	  </tr>
	</table>

6. Select a service plan. 

    By default, the **free** plan is set.

    For more information, see [Service plans](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-change_plan#change_plan).
	
7. Click **Create** to provision the {{site.data.keyword.cloudaccesstrailshort}} service in the {{site.data.keyword.Bluemix_notm}} space where you are logged in.
  
 

## Provisioning from the CLI
{: #cli}

Complete the following steps to provision an instance of the {{site.data.keyword.cloudaccesstrailshort}} service in {{site.data.keyword.Bluemix_notm}} through the command line:

1. [Pre-requisite] Install the {{site.data.keyword.Bluemix_notm}} CLI.

   For more information, see [Installing the {{site.data.keyword.Bluemix_notm}} CLI](/docs/cli/reference/ibmcloud?topic=cloud-cli-install_use#install_use).
   
   If the CLI is installed, continue with the next step.
    
2. Log in to the {{site.data.keyword.Bluemix_notm}}. 

    Run the [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) command to log in to the {{site.data.keyword.Bluemix_notm}}, and then, run the [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) command to set the organization and space where you want to provision the {{site.data.keyword.cloudaccesstrailshort}} service.
	
3. Run the `ibmcloud service create` command to provision an instance.

    ```
	ibmcloud service create service_name service_plan service_instance_name
	```
	{: codeblock}
	
	Where
	
	* service_name is the name of the service, that is, **accessTrail**.
	* service_plan is the service plan name. For a list of plans, see [Service plans](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#plan).
	* service_instance_name is the name that you want to use for the new service instance that you create.

	For example, to create an instance of the {{site.data.keyword.cloudaccesstrailshort}} service with the standard plan, run the following command:
	
	```
	ibmcloud service create accessTrail free my_activitytracker_svc
	```
	{: codeblock}
	
4. Verify that the service is created successfully. Run the following command:

    ```	
	ibmcloud service list
	```
	{: codeblock}
	
	The output of running the command looks as follows:
	
	```
    Getting services in org MyOrg / space MySpace as xxx@yyy.com...
    OK
    
    name                           service                  plan                   bound apps              last operation
    my_activitytracker_svc         accessTrail             free                                            create succeeded
	```
	{: screen}

	




