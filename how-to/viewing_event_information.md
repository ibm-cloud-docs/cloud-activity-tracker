---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, view events

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

# Viewing event information
{: #viewing_event_status}

Use the `ibmcloud at status` command to obtain information about the events that are collected and stored in {{site.data.keyword.cloudaccesstrailshort}} for a {{site.data.keyword.Bluemix}} space.
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} is deprecated. As of 9 May 2019, you cannot provision new {{site.data.keyword.cloudaccesstrailshort}} instances. Existing premium plan instances are supported until 9 October 2019. To continue monitoring the activity of your {{site.data.keyword.cloud_notm}} account, provision an instance of the [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}


You can get information about the size of teh event log, number of records, and whether the events are available or not for analysis in Kibana. 

Complete the following steps to view information about the events log:

## Step 1: Log in to the {{site.data.keyword.cloud_notm}}
{: #viewing_event_status_step1}

Log in to the {{site.data.keyword.cloud_notm}}. Complete the following steps:

1. Run the [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) command to log in to the {{site.data.keyword.cloud_notm}}.
2. Run the [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) command to set the organization and space where you want to provision the {{site.data.keyword.cloudaccesstrailshort}} service.

**Note:** Set the organization and space where {{site.data.keyword.cloudaccesstrailshort}} is provisioned.

## Step 2: Identify what events are available
{: #viewing_event_status_step2}

Use the `ibmcloud at status` command to see information about events are available in a space domain.

* To get information about events in a space domain, run the command `ibmcloud at status`.
* To get information about events in the account domain, run the command `ibmcloud at status` with the option `-a`.

```
$ ibmcloud at status -a -s YYYY-MM-DD -e YYYY-MM-DD 
```
{: codeblock}
    
where
    
* *-a* is used to specify that the request applies to the account domain.
* *-s* is used to set the start date in Universal Coordinated Time (UTC): *YYYY-MM-DD*.
* *-e* is used to set the end date in Universal Coordinated Time (UTC): *YYYY-MM-DD*.

For example, to see what events are available for the last 2 weeks in a space domain, run the following command:

```
$ ibmcloud at status
```
{: codeblock}
    
For example, the output of running this command is:
    
```
+------------+--------+------------+
|    DATE    |  COUNT | SEARCHABLE |
+------------+--------+------------+
| 2017-07-24 |    16  |    None    |
+------------+--------+------------+
| 2017-07-25 |   1224 |    All     |
+------------+--------+------------+
```
{: screen}

**Note:** The {{site.data.keyword.cloudaccesstrailshort}} service is a global service that uses the Coordinated Universal Time (UTC). Days are define as UTC days. To get events for a specific local-time day, you might need to download multiple UTC days.
	









