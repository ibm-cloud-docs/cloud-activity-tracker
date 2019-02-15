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


# Deleting events
{: #deleting_events}

Use the *ibmcloud at delete* command to delete manually events that are stored in {{site.data.keyword.cloudaccesstrailshort}}.
{:shortdesc}

Complete the following steps:

## Step 1: Log in to the {{site.data.keyword.Bluemix_notm}}
{: #prereq}

Log in to the {{site.data.keyword.Bluemix_notm}}. Complete the following steps:

1. Run the [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) command to log in to the {{site.data.keyword.Bluemix_notm}}.
2. Run the [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) command to set the organization and space where you want to provision the {{site.data.keyword.cloudaccesstrailshort}} service.

**Note:** Set the organization and space where {{site.data.keyword.cloudaccesstrailshort}} is provisioned.

## Step 2: Identify what events are available
{: #step2}

Use the `ibmcloud at status` command to see information about events are available in a space domain.

* To get information about events in a space domain, run the command `ibmcloud at status`.
* To get information about events in the account domain, run the command `ibmcloud at status` with the option `-a`.

For more information, see [Viewing event information](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-viewing_event_status#viewing_event_status).
	
  
## Step 3: Delete events
{: #step3}
	
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







