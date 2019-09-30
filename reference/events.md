---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, events

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
{:deprecated: .deprecated}


# {{site.data.keyword.cloudaccesstrailshort}} events
{: #events}

Use the {{site.data.keyword.cloudaccesstrailfull}} service to track {{site.data.keyword.cloudaccesstrailshort}} in the {{site.data.keyword.Bluemix}}. 
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} is deprecated. As of 9 May 2019, you cannot provision new {{site.data.keyword.cloudaccesstrailshort}} instances. Existing premium plan instances are supported until 9 October 2019. To continue monitoring the activity of your {{site.data.keyword.cloud_notm}} account, provision an instance of the [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}


## List of events
{: #actions}

The following table lists the actions that generate an event:

<table>
  <caption>Table 1. List of actions that genererate an event</caption>
  <tr>
    <th>Action</th>
	  <th>Description</th>
  <tr>
  <tr>
    <td>read.events</td>
	  <td>Get information about the events that are stored.</td>
  </tr>
  <tr>
    <td>create.sessions</td>
	  <td>Create a session that can be used to download events.</td>
  </tr>
  <tr>
    <td>delete.session</td>
	  <td>Delete a session.</td>
  </tr>
  <tr>
    <td>read.sessions</td>
	  <td>List the sessions.</td>
  </tr>
  <tr>
    <td>download.events</td>
	  <td>Download events.</td>
  </tr>
  <tr>
    <td>delete.events</td>
	  <td>Delete events.</td>
  </tr>
</table>


## Where to look for the events
{: #ui}
 	
{{site.data.keyword.cloudaccesstrailshort}} events are available in the Cloud Foundry space where the {{site.data.keyword.cloudaccesstrailshort}} service is provisioned.