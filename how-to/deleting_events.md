---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, delete events

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

# Deleting events
{: #deleting_events}

Use the *ibmcloud at delete* command to delete manually events that are stored in {{site.data.keyword.cloudaccesstrailshort}}.
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} is deprecated. As of 9 May 2019, you cannot provision new {{site.data.keyword.cloudaccesstrailshort}} instances. Existing premium plan instances are supported until 30 September 2019. To continue monitoring the activity of your {{site.data.keyword.cloud_notm}} account, provision an instance of the [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}


Complete the following steps:

## Step 1: Log in to the {{site.data.keyword.cloud_notm}}
{: #deleting_events_prereq}

Log in to the {{site.data.keyword.cloud_notm}}. Complete the following steps:

1. Run the [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) command to log in to the {{site.data.keyword.cloud_notm}}.
2. Run the [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) command to set the organization and space where you want to provision the {{site.data.keyword.cloudaccesstrailshort}} service.

**Note:** Set the organization and space where {{site.data.keyword.cloudaccesstrailshort}} is provisioned.

## Step 2: Identify what events are available
{: #deleting_events_step2}

Use the `ibmcloud at status` command to see information about events are available in a space domain.

* To get information about events in a space domain, run the command `ibmcloud at status`.
* To get information about events in the account domain, run the command `ibmcloud at status` with the option `-a`.

For more information, see [Viewing event information](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-viewing_event_status#viewing_event_status).
	
  
## Step 3: Delete events
{: #deleting_events_step3}
	
To delete events, run the command `ibmcloud at delete`.

```
ibmcloud at delete -s YYYY-MM-DD -e YYYY-MM-DD 
```
{: codeblock}
    
where

* *-s* is used to set the start date in Universal Coordinated Time (UTC): *YYYY-MM-DD*.
* *-e* is used to set the end date in Universal Coordinated Time (UTC): *YYYY-MM-DD*.

For example, to delete the events for 10 June 2017, run the following command:

```
ibmcloud at delete -s 2017-06-10 -e 2017-06-10
```
{: screen}

You receive information about the event records that have been deleted.







