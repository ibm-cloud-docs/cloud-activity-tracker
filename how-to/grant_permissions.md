---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, IAM

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


# Granting permissions to view events
{: #grant_permissions}

In the {{site.data.keyword.cloud}}, you can assign Cloud Foundry roles, IAM roles or both to a user. These roles define the tasks that a user can perform when you work with the {{site.data.keyword.cloudaccesstrailshort}} service.  
{:shortdesc}

## Granting permissions to see account events
{: #grant_acc_events}

Grant a user the following permissions to see account events in a region:

1. *Developer* role in a space of the region where {{site.data.keyword.cloudaccesstrailshort}} is provisioned. 

    For more information, see [Granting a CF role](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-grant_permissions#grant_cf_role).

2. IAM policy for the {{site.data.keyword.loganalysisshort}} service with *viewer* role in the region. 

    Viewer role is the minimum IAM role required. 
	
	For more information, see [Granting IAM permissions](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-grant_permissions#grant_iam_policy).


## Granting permissions to see space events
{: #grant_space_events}

Grant a user the following permission to see space events in a region:

* *Developer* role in the space of the region where {{site.data.keyword.cloudaccesstrailshort}} is provisioned. 

    For more information, see [Granting a CF role](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-grant_permissions#grant_cf_role).


## Granting IAM permissions
{: #grant_iam_policy}

To grant a user an IAM role, consider the following information:

* You must have permissions to assign policies to other users in the account, or you must be the account owner. If you are not the account owner, you must have an IAM policy with **administrator** role for the {{site.data.keyword.loganalysisshort}} service.

* When you define a policy, the regions that you specify define the regions where a user is granted access to view account domain events.

Complete the following steps to grant a user permission to view events from an account domain:

1. [Log in to the {{site.data.keyword.cloud_notm}} console ![External link icon](../../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com){:new_window}.
	
	After you log in with your user ID and password, the {{site.data.keyword.cloud_notm}} UI opens.

2. From the menu bar, click **Manage > Account > Users**. 

    The *Users* window displays a list of users with their email addresses for the currently selected account.
	
3. If the user is a member of the account, select the user name from the list, or click **Manage user** from the *Actions* menu.

    If the user is not a member of the account, see [Inviting users](/docs/iam?topic=iam-iamuserinv#iamuserinv).

4. In the **Access policies** section, click **Assign access**, then select **Assign access to resources**.

    The *Assign resource access to user** window opens.

5. Enter information about the policy. The following table lists the fields that are required to define a policy: 

    <table>
	  <caption>List of fields to configure an IAM policy.</caption>
	  <tr>
	    <th>Field</th>
		<th>Value</th>
	  </tr>
	  <tr>
	    <td>Services</td>
		<td>*IBM Cloud Log Analysis*</td>
	  </tr>	  
	  <tr>
	    <td>Regions</td>
		<td>You can specify the regions where the user is going to be granted access to work with events. Select one or more regions individually, or select **All current regions** to grant access to all regions.</td>
	  </tr>
	  <tr>
	    <td>Service instance</td>
		<td>Select *All service instances*.</td>
	  </tr>
	  <tr>
	    <td>Roles</td>
		<td>Select one or more IAM roles. <br>Valid roles are *administrator*, *operator*, *editor*, and *viewer*.</td>
	  </tr>
     </table>
	
6. Click **Assign**.
	
The policy that you configure is applicable to the selected regions. 


## Granting a CF role
{: #grant_cf_role}

To grant a user a CF role, consider the following information:

* You must have permissions in the organization and space to assign the user a Cloud Foundry role. 

* Only **developer** role allows a user to view events.

Complete the following steps to grant a user access to view space events:

1. [Log in to the {{site.data.keyword.cloud_notm}} console ![External link icon](../../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com){:new_window}.
	
	After you log in with your user ID and password, the {{site.data.keyword.cloud_notm}} UI opens.

2. From the menu bar, click **Manage > Account > Users**. 

    The *Users* window displays a list of users with their email addresses for the currently selected account.
	
3. If the user is a member of the account, select the user name from the list, or click **Manage user** from the *Actions* menu.

    If the user is not a member of the account, see [Inviting users](/docs/iam?topic=iam-iamuserinv#iamuserinv).

4. Select **Cloud Foundry access**. Then select the organization.

    The spaces that are available in that organization is listed.

5. Choose one space. Then, from the menu action, select **Edit space role**.

6. Select **Developer**.
	
7. Click **Save role**.




