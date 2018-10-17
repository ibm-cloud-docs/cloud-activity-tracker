---

copyright:
  years: 2016, 2018
lastupdated: "2018-10-20"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}



# About
{: #activity_tracker_ov}

Use the {{site.data.keyword.cloudaccesstrailfull}} service to track how applications interact with the {{site.data.keyword.Bluemix}} services. Use {{site.data.keyword.cloudaccesstrailshort}} to monitor for abnormal activity, and comply with regulatory audit requirements. The events that are collected comply with the Cloud Auditing Data Federation (CADF) standard.
{:shortdesc}

* {{site.data.keyword.cloudaccesstrailshort}} offers high-level security governance for your IT resources in the cloud.
* {{site.data.keyword.cloudaccesstrailshort}} provides a solution for network administrators to capture, store, view, search, and monitor API activity in a single place.
* {{site.data.keyword.cloudaccesstrailshort}} provides capabilities to download events that you can then use to generate an audit trail report. You might require these reports so that your organization complies with internal regulations and external industry and country regulations.

Compliance with internal policies and industry regulations is a key requirement in any organization's strategy, regardless of where applications run: on-premises, in a hybrid cloud, or in a public cloud. The {{site.data.keyword.cloudaccesstrailshort}} service provides the framework and functionality to monitor API calls and produce the evidence to comply with corporate policies and market industry-specific regulations.

When you work in a cloud environment, such as the {{site.data.keyword.Bluemix_notm}}, you must plan the cloud strategy for auditing and monitoring workloads and data in accordance with your internal policies and with industry and country-based compliance requirements. You can use the information that is registered through the {{site.data.keyword.cloudaccesstrailshort}} service to identify security incidents, detect unauthorized access, and comply with regulatory and internal auditing requirements.

For example, you can use the {{site.data.keyword.cloudaccesstrailshort}} activity logs to identify the following information:

* The users who made API calls to cloud services.
* The source IP address from where the API calls were made.
* The time-stamp when the API calls were made.
* The status of the API call.


## Collecting events
{: #collect}

The {{site.data.keyword.cloudaccesstrailshort}} service only captures activity data that is related to API calls and other actions that are made to selected cloud services in the {{site.data.keyword.Bluemix_notm}}. 

* Events are collected automatically. 
* Events that are collected in {{site.data.keyword.cloudaccesstrailshort}} comply with the Cloud Auditing Data Federation (CADF) standard. The CADF standard defines a full event model that includes the information that is needed to certify, manage, and audit security of applications in cloud environments.
* {{site.data.keyword.cloudaccesstrailshort}} stores and groups events by domain. There is an account domain per region, and a space domain per Cloud Foundry space. 

The CADF event model includes the following components:

<table>
  <caption>Table 1. Components that are available in a CADF event model</caption>
  <tr>
    <th>Component</th>
	<th>Description</th>
  </tr>
  <tr>
    <td>Action</td>
	<td>The action is the operation or activity that an initiator performs, attempts to perform, or is waiting to complete.</td>
  </tr>
  <tr>
    <td>Initiator</td>
	<td>The initiator is the resource that makes an API call and generates a CADF event. The event that is triggered depends on the action that is requested by the API call.</td>
  </tr>
  <tr>
    <td>Observer</td>
	<td>The observer is the resource that creates and stores a CADF record from information available in a CADF event.</td>
  </tr>
  <tr>
    <td>Outcome</td>
	<td>The outcome is the status of the action against the target.</td>
  </tr>
  <tr>
    <td>Target</td>
	<td>The target is the resource against which the action is performed, attempted to perform, or is pending to complete.</td>
  </tr>
</table>


Consider the following information when you work with the {{site.data.keyword.cloudaccesstrailshort}} log in the {{site.data.keyword.IBM_notm}} public cloud:

* You can only store audit records for API calls made to resources that run in the {{site.data.keyword.IBM_notm}} public cloud.
* Only {{site.data.keyword.IBM_notm}} public cloud storage is used to collect events.
* Information is stored for 3 days. After that, the information is deleted on a first-in first-out basis.
* CADF events of type *Activity* are supported by the {{site.data.keyword.cloudaccesstrailshort}} service.


## Provisioning Activity Tracker
{: #provision}

To view events that are available through an account domain, you must provision the {{site.data.keyword.cloudaccesstrailshort}} service in a Cloud Foundry space in the region where you want to monitor API activity. Only the **account owner** can see account events.

To view events that are available through a space doamin, you must provision the {{site.data.keyword.cloudaccesstrailshort}} service in the space  where you want to monitor API activity.

To learn how to provision the {{site.data.keyword.cloudaccesstrailshort}} service , see [Provisioning the {{site.data.keyword.cloudaccesstrailshort}} service](/docs/services/cloud-activity-tracker/how-to/provision.html#provision).



## Analysing activity logs
{: #analyze}

You can analyze activity logs through the {{site.data.keyword.cloudaccesstrailshort}} UI in the {{site.data.keyword.Bluemix_notm}}, or by using Kibana, an open-source tool. You can monitor events that are available in a specific space or at the account level.

You can search, analize, and monitor activity logs for the last 24 hours through the {{site.data.keyword.cloudaccesstrailshort}} UI in the {{site.data.keyword.Bluemix_notm}}. For more information, see [Navigating to the {{site.data.keyword.cloudaccesstrailshort}} UI](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_at_ui.html#launch_at_ui).

You can search, analize, and monitor activity logs for the last 3 days through Kibana by using the {{site.data.keyword.cloudaccesstrailshort}} Kibana dashboard, or by creating your own custom dashboards. * **Note:** This feature is available for **Premium** plan users.

* For more information on how to launch Kibana, see [Navigating to the Kibana dashboard](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_kibana.html#launch_kibana). 
* For a list of fields that you can use to analyze events in Kibana, see [{{site.data.keyword.cloudaccesstrailshort}} event fields](/docs/services/cloud-activity-tracker/at_event.html#at_event)



## Regions
{: #regions}

The {{site.data.keyword.cloudaccesstrailshort}} service is available in the following regions:

* Germany
* Sydney
* United Kingdom 
* US South


## Service Plan
{: #plan}

The {{site.data.keyword.cloudaccesstrailshort}} service provides multiple plans.

You can change a plan through the {{site.data.keyword.Bluemix_notm}} UI or through the command line. You can upgrade or reduce your plan at any time. For more information about service plan upgrades, see [Changing the plan](/docs/services/cloud-activity-tracker/how-to/change_plan.html#change_plan). 

The following table outlines the plans that are available:

<table>
    <caption>Table 1. Capabilities for event ingestion, event retention, and exporting events</caption>
      <tr>
        <th>Plan</th>
        <th>Event Ingestion</th>
        <th>Event Retention</th>
		<th>Export events</th>
      </tr>
      <tr>
        <td>Lite (default)</td>
        <td>No</td>
        <td>Last 3 days</td>
		<td>No</td>
      </tr>
      <tr>
        <td>Premium</td>
        <td>Yes</td>
        <td>Configurable number of days.</td>
		<td>Yes</td>
      </tr>
</table>

<table>
    <caption>Table 2. Capabilities for managing and viewing events</caption>
      <tr>
        <th>Plan</th>
		    <th>API</th>
		    <th>CLI</th>
        <th>Kibana</th>
      </tr>
      <tr>
        <td>Lite (default)</td>
		    <td>No</td>
		    <td>No</td>
        <td>No</td>
      </tr>
      <tr>
        <td>Premium</td>
		    <td>Yes</td>
		    <td>Yes</td>
        <td>Yes</td>
      </tr>
</table>

**Note:** The monthly cost of event storage is calculated as an average of the billing cycle.

## Security
{: #security}

Consider the following information about security when working with the {{site.data.keyword.cloudaccesstrailshort}} service:

* IBM services that generate {{site.data.keyword.cloudaccesstrailshort}} events follow the {{site.data.keyword.IBM_notm}} Cloud security policy. For more information, see [Trust the security and privacy of IBM Cloud ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/cloud-computing/learn-more/why-ibm-cloud/security/){: new_window}.
* The {{site.data.keyword.cloudaccesstrailshort}} service captures user-initiated actions that change the state of Cloud services. The information does not provide direct access to databases or applications.
* Only authorized users can view and monitor {{site.data.keyword.cloudaccesstrailshort}} event logs. Each user is identified by their unique ID in the {{site.data.keyword.Bluemix_notm}}.
