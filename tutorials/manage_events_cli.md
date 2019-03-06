---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, manage events, tutorial

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


# Managing events by using the Activity Tracker CLI
{: #tutorial2}

Use this tutorial to learn how to use the {{site.data.keyword.cloudaccesstrailshort}} CLI to manage events through the command-line. Learn how to get information about stored events, how to download events that are stored in the {{site.data.keyword.IBM_notm}} Cloud, or how to delete events.
{:shortdesc}

Complete the following steps:

1. [Provision the {{site.data.keyword.keymanagementservicelong_notm}} and generate events](/docs/services/cloud-activity-tracker/tutorials?topic=cloud-activity-tracker-tutorial2#tutorial2_step1)
2. [Get information about stored events (ibmcloud at status)](/docs/services/cloud-activity-tracker/tutorials?topic=cloud-activity-tracker-tutorial2#tutorial2_step2)
2. [Specify which logs to download by creating a session (ibmcloud at session create)](/docs/services/cloud-activity-tracker/tutorials?topic=cloud-activity-tracker-tutorial2#tutorial2_step3)
3. [Get the actual log data (ibmcloud at download)](/docs/services/cloud-activity-tracker/tutorials?topic=cloud-activity-tracker-tutorial2#tutorial2_step4)
4. [Delete the session after the download completes (ibmcloud at session delete)](/docs/services/cloud-activity-tracker/tutorials?topic=cloud-activity-tracker-tutorial2#tutorial2_step5)
5. [Manually delete logs that are not required (ibmcloud at delete)](/docs/services/cloud-activity-tracker/tutorials?topic=cloud-activity-tracker-tutorial2#tutorial2_step6)


## Assumptions
{: #tutorial2_assumptions}

1. You have an {{site.data.keyword.cloud_notm}} user ID that has `developer` permissions to work in a space of an {{site.data.keyword.cloud_notm}} account where the {{site.data.keyword.cloudaccesstrailshort}} service is provisioned. 

    For more information on how to provision the {{site.data.keyword.cloudaccesstrailshort}} service, see [Provisioning the {{site.data.keyword.cloudaccesstrailshort}} service](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-provision#provision).

2. You have an instance of the {{site.data.keyword.cloudaccesstrailshort}} service with a premium plan.

    **Note:** The {{site.data.keyword.cloudaccesstrailshort}} CLI is not available with the `Lite` plan.

3. You have the {{site.data.keyword.cloudaccesstrailshort}} CLI installed in your local system. This CLI is required to manage events through the command-line. 

    For more information about installing the {{site.data.keyword.cloudaccesstrailshort}} CLI, see [Configuring the {{site.data.keyword.cloudaccesstrailshort}} CLI](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-config_cli#config_cli).

4. You are logged in to {{site.data.keyword.cloud_notm}} through the command-line. For this tutorial, run the following commands from a terminal: 

    `ibmcloud login -a api.ng.bluemix.net` to log in to the us-south region. For more information, see [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login).
    
    `ibmcloud target -o OrgName -s SpaceName` to set the target organization and space where the {{site.data.keyword.cloudaccesstrailshort}} service is provisioned. For more information, see [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target).


## Step 1. Provision the IBM Key Protect service and generate events 
{: #tutorial2_step1}
	
Complete the following steps to provision the {{site.data.keyword.keymanagementserviceshort}} service in the {{site.data.keyword.cloud_notm}} and generate events:

1. Provision an instance of the {{site.data.keyword.keymanagementserviceshort}} service in the US South region. For more information, see [Provisioning from the IBM Cloud console](/docs/services/key-protect?topic=key-protect-provision#provision).

2. Define the {{site.data.keyword.cloud_notm}} permissions for the user that you are planning to use to work with keys. 

    * A user needs an IAM policy with a service role set to *manager* or *writer* to be able to create keys.
	* A user needs an IAM policy with a service role set to *manager* to be able to delete keys.
	* A user needs an IAM policy with a service role set to *reader* to be able to see keys. 

3. Create a security key by using the {{site.data.keyword.keymanagementserviceshort}} service to generate {{site.data.keyword.cloudaccesstrailshort}} event data. For more information, see [Creating new keys](/docs/services/key-protect?topic=key-protect-create-standard-keys#create-standard-keys).

{{site.data.keyword.cloudaccesstrailshort}} events are generated as a result of creating a key.

## Step 2. Get information about stored events
{: #tutorial2_step2}

{{site.data.keyword.keymanagementserviceshort}} events are available in the {{site.data.keyword.cloudaccesstrailshort}} account domain.

In this tutorial, {{site.data.keyword.keymanagementserviceshort}} events are available in the US South account domain, which is the region where you provisioned the {{site.data.keyword.keymanagementserviceshort}} service. 

Run the following command to get information about events collected on a specific date:

```
ibmcloud at status -s startDate -e endDate -a
```
{: codeblock}

Where 

* `-s` is used to set the start day. 
* `startDate` represents the start date. The format is *YYYY-MM-DD*.
* `-e` is used to set the end date.
* `endDate` represents the end date. The format is *YYYY-MM-DD*.
* `-a` is used to indicate to include events at the account domain.

For example,

```
ibmcloud at status -s 2017-07-25 -e 2017-07-25 -a
+------------+-------+-------+------------+
| Date       | Count | Size  | Searchable |
+------------+-------+-------+------------+
| 2017-07-25 | 12    | 34994 | All        |
+------------+-------+-------+------------+
```
{: screen}

This command will count the events for 25 of June 2017. {{site.data.keyword.cloudaccesstrailshort}} is a global service. Therefore, the days are Universal Time. To get a complete local-time day, you might need to download multiple UTC days.




## Step 3. Specify which events to download
{: #tutorial2_step3}

Before you start downloading events, create a session. The session specifies which events are downloaded.


Use the following command to create a session:

```
ibmcloud at session create -s startDate -e endDate -a
```
{: codeblock}

Where 

* `-s` is used to set the start day. 
* `startDate` represents the start date. The format is *YYYY-MM-DD*.
* `-e` is used to set the end date.
* `endDate` represents the end date. The format is *YYYY-MM-DD*.
* `-a` is used to indicate to include events at the account domain.

For example, 

```
ibmcloud at session create -s 2017-07-25 -e 2017-07-25 -a
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| id           | 21b19aeb-3d32-4c60-b912-517609c62db2      |
| space        | 667fb895-b5f5-46c9-9f0e-cf4587341095      |
| username     | xxx@yyy.com                               |
| create-time  | 2017-07-25T18:33:22.678350874Z            |
| access-time  | 2017-07-25T18:33:22.678350874Z            |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
+--------------+-------------------------------------------+
```
{: screen}

Where 

* `-s` is used to set the start day.
* `-e` is used to set the end date.
* `-a` is used to indicate to include events at the account domain.

There is a start date and an end date that is associated with a session. The download command includes events between those inclusive dates.

The important part of the command's output is the session `Id`. It is referenced in the download command.

To get information about existing sessions, type `ibmcloud at session list`.

To learn more about sessions and the `ibmcloud at session create` command, refer to the [CLI reference](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-at_cli_cloud#session_create).

Use `ibmcloud at session help create` to get help from the command-line.

## Step 4. Download the events that are identified for the scope that is defined for the session
{: #tutorial2_step4}

To download the events specified by the session parameters, run the following command:

```
ibmcloud at download -o outputFile sessionID
```
{: codeblock}

* The `-o` parameter specifies an output file.
* `outputFile` is the name of the local file.
* The `sessionID` is specified last. You get the value of the session ID from the output of the `ibmcloud at session create` command.

The format of the downloaded data is compressed JSON. 

For example,

```
$ ibmcloud at download -o events.log 21b19aeb-3d32-4c60-b912-517609c62db2
 6.70 KiB / 3.06 KiB [================================================================================================================================================================] 219.03% 8.60 MiB/s 0s
Download Successful
```
{: screen} 

The progress indicator moves 0 - 100% as the events download.

To learn more about the `ibmcloud at download` command, refer to the [CLI reference](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-at_cli_cloud#download).

Use `ibmcloud at help download` to get help from the command-line.

## Step 5. Delete the session
{: #tutorial2_step5}

After the download completes, delete the session. Run the following command:

```
ibmcloud at session delete sessionID
```
{: codeblock}

Where 

* `sessionID` is the ID of the session that you want to delete.

The number of sessions is limited. A session is not deleted automatically. You must manually delete sessions that are not required. 

For example, 

```
$ ibmcloud at session delete 21b19aeb-3d32-4c60-b912-517609c62db2
+---------+------------------------+
| name    | value                  |
+---------+------------------------+
| message | Delete session success |
+---------+------------------------+
```
{: screen}

To learn more about the `ibmcloud at session delete` command, refer to the [CLI reference](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-at_cli_cloud#session_delete).

Use `ibmcloud at session help delete` to get help from the command-line.

## Step 6. Delete events from Activity Tracker automatically
{: #tutorial2_step6}

You have control of your own event retention in {{site.data.keyword.cloudaccesstrailshort}}. You can delete events manually, or you can automate the deletion of events.

To delete events manually from a space, run the `ibmcloud at delete` command. For example,

```
$ ibmcloud at delete -s 2017-07-25 -e 2017-07-25
Deleted successfully
"6 logs were deleted,freeing 13737 bytes."
```
{: screen}

To learn more about the `ibmcloud at delete`command, refer to the [CLI reference](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-at_cli_cloud#delete).

Use `ibmcloud at help delete` to get help from the command-line.

**Note:** To delete events automatically, you can set a retention policy by using the CLI command `ibmcloud at option`. For more information, see [CLI reference](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-at_cli_cloud#option)


