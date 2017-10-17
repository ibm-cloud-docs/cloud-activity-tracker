---

copyright:
  years: 2016, 2017
lastupdated: "2017-09-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Downloading events
{: #downloading_events}

You can download events to a local file or pipe data into another program. You download events within the context of a session. A session specifies which events will be downloaded. If the download of the events is interrupted, the session enables resuming the download from where it left off. After the download is completed, you must delete the session.
{:shortdesc}

Complete the following steps to download events that are available in a {{site.data.keyword.Bluemix_notm}} space into a local file:

## Step 1: Log in to Bluemix
{: #prereq}

Before you start, log in to a {{site.data.keyword.Bluemix_notm}} region, organization, and space where the {{site.data.keyword.cloudaccesstrailshort}} service is provisioned. 

```
bx login -a Endpoint
```
{: codeblock}
	
Where *Endpoint* is the URL to log in to {{site.data.keyword.Bluemix_notm}}. This URL is different per region.
	
<table>
    <caption>List of endpoints to access {{site.data.keyword.Bluemix_notm}}</caption>
	<tr>
	  <th>Region</th>
	  <th>URL</th>
	</tr>
	<tr>
	  <td>US South</td>
	  <td>api.ng.bluemix.net</td>
	</tr>
</table>

Follow the instructions. 

For example, run the following command to log in to the US South region:
	
```
bx login -a api.ng.bluemix.net
```
{: codeblock}

Then, set the organization and space. Run the following command:

```
bx target -o OrgName -s SpaceName
```
{: codeblock}

where

* OrgName is the name of the organization.
* SpaceName is the name of the space.

## Step 2: Identify what events are available
{: #step2}

1. Use the `cf at status` command to see what events are available.

    For example, to see what events are available for the last 2 weeks, run the following command:

    ```
    $ bx cf at status
    ```
    {: codeblock}
    
    For example, the output of running this command is:
    
    ```
    +------------+--------+-------+--------------------+------------+
    |    DATE    |  COUNT | SIZE  |       TYPES        | SEARCHABLE |
    +------------+--------+-------+--------------------+------------+
    | 2017-07-24 |    16  | 3020  | ActivityTracker    |   None     |
    +------------+--------+-------+--------------------+------------+
    | 2017-07-25 |   1224 | 76115 | ActivityTracker    |    All     |
    +------------+--------+-------+--------------------+------------+
    ```
    {: screen}

    **Note:** The {{site.data.keyword.cloudaccesstrailshort}} service is a global service that uses the Coordinated Universal Time (UTC). Days are define as UTC days. To get events for a specific local-time day, you might need to download multiple UTC days.
	
	For more information, see [cf at status](/docs/services/cloud-activity-tracker/cli/at_cli.html#status).


## Step 3: Create a session
{: #step3}

A session is required to define the scope of the event data that is available for a download, and to keep the status of the download. 

Use the command [cf at session create](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_create) to create a session. Optionally, you can specify start date, and end date when you create a session. 

**Note:** When you specify the start date and the end date, the session provides access to events between those inclusive dates. 

To create a session that is used to download events for the current date, run the following command:

```
bx cf at session create 
```
{: codeblock}

The session returns the following information:

* The date range to be downloaded. The default is the current UTC date.
* Information about whether to include events that are  available for the entire account, or just for the current space. By default, you get events for the space where you are logged in.
* The session ID that is required to download events.
* The user ID that creates the session.

For example,

```
$ bx cf at session create 
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

**Tip:** To see the list of active sessions, run the command [cf at session list](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_list).

For example,

```
bx cf at session list
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
bx cf at download -o Events_File_Name Session_ID
```
{: codeblock}

where

* Events_File_Name is the name of the output file.
* Session_ID is the GUID of the session. You obtain this value in the previous step. Use the value for the field **Id**.

For example,

```
bx cf at download -o Events_File_Name.log 32c657c5-31c0-4a3c-a139-b380871c737a
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

After the download is complete, you must delete the session by using the [cf at session delete](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_delete) command. 

Run the following command to delete a session:

```
bx cf at session delete Session_ID
```
{: codeblock}

Where Session_ID is the GUID of the session that you created in a previous step. Use the value for the field **Id**.

For example,

```
bx cf at session delete 32c657c5-31c0-4a3c-a139-b380871c737a
+---------+------------------------+
| Name    | Value                  |
+---------+------------------------+
| message | Delete session success |
+---------+------------------------+
```
{: screen}




