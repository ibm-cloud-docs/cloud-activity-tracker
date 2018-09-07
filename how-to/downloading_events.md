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


# Downloading events
{: #downloading_events}

You can download events to a local file. You download events within the context of a session. A session specifies which events will be downloaded. After the download is completed, you must delete the session.
{:shortdesc}

Complete the following steps to download events into a local file:

## Step 1: Log in to the {{site.data.keyword.Bluemix_notm}}
{: #prereq}

Log in to the {{site.data.keyword.Bluemix_notm}}. Complete the following steps:

1. Run the [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) command to log in to the {{site.data.keyword.Bluemix_notm}}.
2. Run the [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) command to set the organization and space where you want to provision the {{site.data.keyword.cloudaccesstrailshort}} service.

**Note:** Set the organization and space where {{site.data.keyword.cloudaccesstrailshort}} is provisioned.

## Step 2: Identify what events are available
{: #step2}

Use the `ibmcloud at status` command to see information about events are available in a space domain.

* To get information about events in a space domain, run the command `ibmcloud at status`.
* To get information about events in the account domain, run the command `ibmcloud at status` with the option `-a`.

For more information, see [Viewing event information](/docs/services/cloud-activity-tracker/how-to/viewing_event_information.html#viewing_event_status).
  


## Step 3: Create a session
{: #step3}

A session is required to define the scope of the event data that is available for a download, and to keep the status of the download. 

Use the command `ibmcloud at session create` to create a session. By default, a session includes data for the last 2 weeks.  Optionally, you can specify start date, and end date when you create a session to specify a time range, a specific hour of the day, and the scope of the events. 

**Note:** 

* When you specify the start date and the end date, the session provides access to events between those inclusive dates. 
* You cannot download more than 2 weeks of data per session. Therefore, the time range must be less than 2 weeks.
* You can download events for a space domain or for the account domain in a region.

To create a session that is used to download events for a specific date, run the following command:

```
ibmcloud at session create -s 2017-07-25 -e 2017-07-25
```
{: codeblock}

The session returns the following information:

* The date range to be downloaded.
* Information about whether to include events that are  available for the entire account, or just for the current space. By default, you get events for the space where you are logged in.
* The session ID that is required to download events.
* The user ID that creates the session.

For example,

```
$ ibmcloud at session create 
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| username     | xxx@yyy.com                               |
| create-time  | 2017-07-25T10:29:28.541092735Z            |
| access-time  | 2017-07-25T10:29:28.541092735Z            |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
| id           | 32c657c5-31c0-4a3c-a139-b380871c737a      |
| space        | 66fe4565-abab-46c9-cdcd-qf4565342345      |
+--------------+-------------------------------------------+
```
{: screen}

**Tip:** To see the list of active sessions, run the command `ibmcloud at session list` command.

For example,

```
ibmcloud at session list
+--------------------------------------+--------------------------------------+---------------------+--------------------------------+--------------------------------+
| Id                                   | Space                                |Username             | Create-time                    | Access-time                    |
+--------------------------------------+--------------------------------------+---------------------+--------------------------------+--------------------------------+
| 32c657c5-31c0-4a3c-a139-b380871c737a | 66fe4565-abab-46c9-cdcd-qf4565342345 |xxx@yyy.com          | 2017-07-25T10:29:28.541092735Z | 2017-07-25T10:29:28.541092735Z |
+--------------------------------------+--------------------------------------+---------------------+--------------------------------+--------------------------------+
```
{: screen} 


## Step 4: Download events to a file
{: #step4}

To download the events that are specified by the session parameters, run the following command:

```
ibmcloud at download -o Events_File_Name Session_ID
```
{: codeblock}

where

* Events_File_Name is the name of the output file.
* Session_ID is the GUID of the session. You obtain this value in the previous step. Use the value for the field **Id**.

For example,

```
ibmcloud at download -o Events_File_Name.log 32c657c5-31c0-4a3c-a139-b380871c737a
 29.89 KiB / 12.19 KiB [================================] 245.14% 9.73 MiB/s 0s
Download completed successfully
```
{: screen}

The progress indicator moves from 0 to 100% as the events download.

**Note:** 

* The format of the downloaded data is compressed JSON. For example, when you download events in a linux system, unzip the .gz file and open it to see the data in JSON format. 
* The compressed JSON is suitable for ingestion by ElasticSearch or Logstash. For example, if -o is not given, and you are working on a Linux system, the data will stream to stdout, so that you can pipe it directly into your own Elastic stack.
* You can also process the data with any program that can parse JSON. 

## Step 4: Delete the session

After the download is complete, you must delete the session by using the `ibmcloud at session delete` command. 

Run the following command to delete a session:

```
ibmcloud at session delete Session_ID
```
{: codeblock}

Where Session_ID is the GUID of the session that you created in a previous step. Use the value for the field **Id**.

For example,

```
ibmcloud at session delete 32c657c5-31c0-4a3c-a139-b380871c737a
+---------+------------------------+
| Name    | Value                  |
+---------+------------------------+
| message | Delete session success |
+---------+------------------------+
```
{: screen}




