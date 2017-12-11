---

copyright:

  years: 2016, 2017

lastupdated: "2017-11-09"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# IBM Cloud Activity Tracker CLI
{: #at_cli}

The {{site.data.keyword.cloudaccesstraillong}} CLI is a CF plug-in that you can use to manage {{site.data.keyword.cloudaccesstrailshort}} events.
{: shortdesc}

**Prerequisites**
* Before running the commands, log in to the {{site.data.keyword.Bluemix}} with the `bx login` command to generate an access token and authenticate your session.

To find out about how to use the {{site.data.keyword.cloudaccesstrailshort}} CLI, see [Managing {{site.data.keyword.cloudaccesstrailshort}} events through the CLI](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#managing_events). 

The {{site.data.keyword.cloudaccesstraillong}} CLI plug-in supports Linux, Mac, and Windows platforms.

<table>
  <caption>Commands for managing {{site.data.keyword.cloudaccesstrailshort}}</caption>
  <tr>
    <th>Command</th>
    <th>When to use it</th>
  </tr>
  <tr>
    <td>[bx cf at](#base)</td>
    <td>Use this command to get information about the CLI, such as version or the list of commands.</td>
  </tr>
  <tr>
    <td>[bx cf at delete](#delete)</td>
    <td>Use this command to delete {{site.data.keyword.cloudaccesstrailshort}} events.</td>
  </tr>
  <tr>
    <td>[bx cf at download](#download)</td>
    <td>Use this command to download {{site.data.keyword.cloudaccesstrailshort}} logs to a local file. </td>
  </tr>
  <tr>
    <td>[bx cf at help](#help)</td>
    <td>Use this command to get help on how to use the CLI, and a list of all of the commands.</td>
  </tr>
  <tr>
    <td>[bx cf at option](#option)</td>
    <td>Use this command to view or change {{site.data.keyword.cloudaccesstrailshort}} event options, such as retention, that are available in a space or in an account.</td>
  </tr>
  <tr>
    <td>[bx cf at session create](#session_create)</td>
    <td>Use this command to create a new session.</td>
  </tr>
  <tr>
    <td>[bx cf at session delete](#session_delete)</td>
    <td>Use this command to delete a session.</td>
  </tr>  
  <tr>
    <td>[bx cf at session list](#session_list)</td>
    <td>Use this command to list active sessions and their IDs.</td>
  </tr>  
  <tr>
    <td>[bx cf at session show](#session_show)</td>
    <td>Use this command to show the status of a single session.</td>
  </tr>   
  <tr>
    <td>[bx cf at status](#status)</td>
    <td>Use this command to view information about the status of events that are stores in {{site.data.keyword.cloudaccesstrailshort}}.</td>
  </tr>
  <tr>
    <td>[bx cf at trail](#trail)</td>
    <td>Use this command to send events to {{site.data.keyword.cloudaccesstrailshort}}.</td>
  </tr>
  </table>


## bx cf at
{: #base}

Provides information about the version of the CLI and how to use the CLI.

```
bx cf at [parameters]
```
{: codeblock}

**Parameters**

<dl>
<dt>--help, -h</dt>
<dd>Set this parameter to show the list of commands, or to get help for one command.
</dd>

<dt>--version, -v</dt>
<dd>Set this parameter to print the version of the CLI.</dd>
</dl>

**Examples**

To get the list of commands, run the following command:

```
bx cf at --help
```
{: codeblock}

To get the version of the CLI, run the following command:

```
bx cf at --version
```
{: codeblock}


## bx cf at delete
{: #delete}

Deletes {{site.data.keyword.cloudaccesstrailshort}} events.

```
bx cf at delete [parameters] [arguments..]
```
{: codeblock}

**Parameters**

<dl>
  <dt>--start value, -s value</dt>
  <dd>(Optional) Sets the start date in Universal Coordinated Time (UTC): *YYYY-MM-DD*, for example, `2017-01-02`. <br>The default value is set to 2 weeks ago. 
  </dd>
  
  <dt>--end value, -e value</dt>
  <dd>(Optional) Sets the end date in Universal Coordinated Time (UTC): *YYYY-MM-DD* <br>The UTC format of the date is **YYYY-MM-DD**, for example, `2017-01-02`. <br>The default value is set to the current date.
  </dd>
  
</dl>

**Example**

To delete the events for 22 June 2017, run the following command:
```
bx cf at delete -s 2017-06-22 -e 2017-06-22
```
{: codeblock}

You receive information similar to the following output:

`Deleted successfully`
`"6 logs were deleted, freeing 13737 bytes."`


## bx cf at download
{: #download}

Downloads {{site.data.keyword.cloudaccesstrailshort}} events to a local file or streams them out to a terminal window in Windows and Mac OS X, or to stdout in a Linux terminal. 

**Note:** To download files, you must create a session first. A session defines which events to download based on date range. You download events within the context of a session. For more information, see [bx cf at session create](/docs/services/CloudActivityTracker/reference/at_cli.html#session_create).

```
bx cf at download [parameters] [arguments...]
```
{: codeblock}

**Parameters**

<dl>
<dt>--output value, -o value</dt>
<dd>(Optional) Sets the path and filename for the local output file where the events are downloaded. <br>The default value is a hyphen (-). <br>Set this parameter to the default value to output logs to standard output.</dd>
</dl>

**Arguments**

<dl>
<dt>Session ID</dt>
<dd>Set the session ID value that you get when you run the command `bx cf at session create`. This value indicates which session to use when downloading events. <br>**Note:** The `bx cf at session create` command provides the parameters that control which events are downloaded. </dd>
</dl>

**Note:** After the download completes, to download the same data again, you must use a different file, or a different session.

**Example**

To download events into a file called `events.log`, run the following command:

```
bx cf at download -o events.log 1db6ce16-824d-4d50-bd40-37f1d8fea9b7
```
{: screen}

You receive information similar to the following output: 

```
6.70 KiB / 3.06 KiB [========] 219.03% 8.60 MiB/s 0s
Download completed successfully
```
{: screen}


## bx cf at help
{: #help}

Provides information about how to use a command.

```
bx cf at help [parameters]
```
{: codeblock}

**Parameters**

<dl>
<dt>Command</dt>
<dd>Set the command name for which you want to get help.
</dd>
</dl>


**Example**

To get help on how to run the command to view the status of {{site.data.keyword.cloudaccesstrailshort}}, run the following command:

```
bx cf at help status
```
{: codeblock}


## bx cf at option
{: #option}

Displays or changes the retention period for events that are available in a space. When you set a retention policy, events are deleted automatically when the number of retention days in reached.

* The period is set in number of days.
* The default value is **-1**, that is, events are stored and not deleted.

**Note:** By default, all the events are stored. If you do not set a retention period, you must delete them manually by using the `bx cf at delete` command. 

```
bx cf at option [parameters] [arguments...]
```
{: codeblock}

**Parameters**

<dl>
<dt>--retention value, -r value</dt>
<dd>(Optional) Sets the number of retention days. <br> The default value is *-1* days.</dd>

</dl>

**Example**

To see the current retention period for the space where you are logged in, run the following command:

```
bx cf at option
```
{: codeblock}

The output is similar to the following output:

```
+--------------------------------------+-----------+
|               SPACEID                | RETENTION |
+--------------------------------------+-----------+
| 2af890ce-fb4f-4e41-a975-901a56ed1f11 |        30 |
+--------------------------------------+-----------+
```
{: screen}


To change the retention period to 25 days for the space where you are logged in, run the following command:

```
bx cf at option -r 25
```
{: codeblock}

The output is similar to the following output:

```
+--------------------------------------+-----------+
|               SPACEID                | RETENTION |
+--------------------------------------+-----------+
| 2af890ce-fb4f-4e41-a975-901a56ed1f11 |        25 |
+--------------------------------------+-----------+
```
{: screen}



## bx cf at session create
{: #session_create}

Creates a new session.

**Note:** You can have up to 30 concurrent sessions in a space. The session is created for a user. Sessions cannot be shared between users in a space.

```
bx cf at session create [parameters] [arguments...]
```
{: codeblock}

**Parameters**

<dl>
  <dt>--start value, -s value</dt>
  <dd>(Optional) Sets the start date in Universal Coordinated Time (UTC): *YYYY-MM-DD*, for example, `2017-01-02`. <br>The default value is set to 2 weeks ago. 
  </dd>
  
  <dt>--end value, -e value</dt>
  <dd>(Optional)  Sets the end date in Universal Coordinated Time (UTC): *YYYY-MM-DD*, for example, `2017-01-02`. <br>The default value is set to the current date. 
  </dd>
 </dl>

**Returned values**

<dl>
<dt>Access-Time</dt>
<dd>Timestamp that indicates when the session was last used.</dd>

<dt>Create-Time</dt>
<dd>Time stamp that corresponds to the date and time when the session was created.</dd>

<dt>Date-Range</dt>
<dd>Indicates the days that are used to filter events. Events that are identified in this date range are available for management through the session.</dd>

<dt>ID</dt>
<dd>Session ID.</dd>

<dt>Space</dt>
<dd>Space ID where the session is active.</dd>

<dt>Type-Account</dt>
<dd>This value is set to **ActivityTracker**.</dd>

<dt>Username</dt>
<dd>{{site.data.keyword.IBM_notm}}ID of the user who created the session.</dd>
</dl>


**Example**

To create a session for 10 July 2017, run the following command:

```
bx cf at session create -s 2017-07-10 -e 2017-07-10
```
{: screen}

The output is similar to the following output:

```
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| id           | 9b8c4db8-5841-4993-a449-305815a53a8e      |
| space        | xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx      |
| username     | xxx@yyy.com                               |
| create-time  | 2017-07-25T11:54:00.20042645Z             |
| access-time  | 2017-07-25T11:54:00.20042645Z             |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
+--------------+-------------------------------------------+
```
{: screen}



## bx cf at session delete
{: #session_delete}

Deletes a session that is specified by the session ID.

```
bx cf at session delete [arguments...]
```
{: codeblock}


**Arguments**

<dl>
<dt>Session ID</dt>
<dd>ID of the session that you want to delete. <br>You can use the `bx cf at session list` command to get all the active session IDs.</dd>
</dl>

**Example**

To delete a session with session ID *9b8c4db8-5841-4993-a449-305815a53a8e*, run the following command:

```
bx cf at session delete 9b8c4db8-5841-4993-a449-305815a53a8e
```
{: screen}

The output is similar to the following output:

```
+---------------+--------------------------+
|    NAME       |     VALUE                |
+---------------+--------------------------+
|  message      | Delete session success   |
+---------------+--------------------------+
```
{: screen}


## bx cf at session list
{: #session_list}

Lists the active sessions and their IDs.

```
bx cf at session list 
```
{: codeblock}

**Returned values**

<dl>
<dt>ID</dt>
<dd>Session ID.</dd>

<dt>SPACE</dt>
<dd>Space ID where the session is active.</dd>

<dt>USERNAME</dt>
<dd>{{site.data.keyword.IBM_notm}}ID of the user that created the session.</dd>

<dt>CREATE-TIME</dt>
<dd>Time stamp that corresponds to the date and time when the session was created.</dd>

<dt>ACCESS-TIME</dt>
<dd>Time stamp that indicates when the session was last used.</dd>
</dl>
 
**Example**

To list the sessions, run the following command:

```
bx cf at session list
```
{: screen}

The output is similar to the following output:

```
+--------------------------------------+--------------------------------------+-----------------------------------+--------------------------------+--------------------------------+
| ID                                   | SPACE                                | USERNAME                          | CREATE-TIME                    | ACCESS-TIME                    |
+--------------------------------------+--------------------------------------+-----------------------------------+--------------------------------+--------------------------------+
| fa3f1970-21f3-4e32-b480-1ffb41badc16 | 12345678-fb4f-acdf-a975-11335678r3fg | xxx@yyy.com                       | 2017-07-10T09:04:07.916788069Z | 2017-07-10T09:04:07.916788069Z |
| 9b8c4db8-5841-4993-a449-305815a53a8e | 12345678-fb4f-acdf-a975-11335678r3fg | xxx@yyy.com                       | 2017-07-11T09:19:14.666532796Z | 2017-07-12T09:19:14.666532796Z |
+--------------------------------------+--------------------------------------+-----------------------------------+--------------------------------+--------------------------------+
```
{: screen}


## bx cf at session show
{: #session_show}

Shows the status of a single session.

```
bx cf at session show [arguments...]
```
{: codeblock}

**Arguments**

<dl>
<dt>Session ID</dt>
<dd>ID of the active session for which you want to get information.</dd>
</dl>

**Returned values**

<dl>
<dt>Access-Time</dt>
<dd>Time stamp that indicates when the session was last used.</dd>

<dt>Create-Time</dt>
<dd>Time stamp that corresponds to the date and time when the session was created.</dd>

<dt>Date-Range</dt>
<dd>Indicates the days that are used to filter events. Events that are identified in this date range are available for management through the session.</dd>

<dt>id</dt>
<dd>Session ID.</dd>

<dt>Space</dt>
<dd>Space ID where the session is active.</dd>

<dt>Type-Account</dt>
<dd>This value is set to **ActivityTracker**.</dd>

<dt>Username</dt>
<dd>{{site.data.keyword.IBM_notm}}ID of the user that created the session.</dd>
</dl>

**Example**

To show details of a session with session ID *9b8c4db8-5841-4993-a449-305815a53a8e*, run the following command:

```
bx cf at session show 9b8c4db8-5841-4993-a449-305815a53a8e
```
{: screen}

The output is similar to the following output:

```
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| create-time  | 2017-07-25T11:54:00.20042645Z             |
| access-time  | 2017-07-25T11:54:00.20042645Z             |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
| id           | 9b8c4db8-5841-4993-a449-305815a53a8e      |
| space        | xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx      |
| username     | xxx@yyy.com                               |
+--------------+-------------------------------------------+
```
{: screen}


## bx cf at status
{: #status}

Returns information about the status of {{site.data.keyword.cloudaccesstrailshort}} events.

```
bx cf at status [parameters] [arguments...]
```
{: codeblock}

**Parameters**

<dl>
  <dt>--start value, -s value</dt>
  <dd>(Optional) Sets the start date in Universal Coordinated Time (UTC): *YYYY-MM-DD*, for example, `2017-01-02`. <br>The default value is set to 2 weeks ago.
  </dd>
  
  <dt>--end value, -e value</dt>
  <dd>(Optional) Sets the end date in Universal Coordinated Time (UTC): *YYYY-MM-DD*, for example, `2017-01-02`. <br>The default value is set to the current date.
  </dd>
  
  <dt>--at-account-level, -a </dt>
  <dd>(Optional) Sets the scope to account level. <br> **Note:** Set this value to get account information. <br>If this parameter is not specified, the default value is set to the current space only, that is, the space where you logged in by using the command `bx cf login`.
  </dd>
  
</dl>


**Note:** The `bx cf at status` command reports only the last two weeks of events that are stored in {{site.data.keyword.cloudaccesstrailshort}} when no start and end dates are specified. 

**Returned values**   

<dl>
  <dt>DATE</dt>
  <dd>Date in Universal Coordinated Time (UTC): *YYYY-MM-DD*, for example, `2017-01-02`. 
  </dd>
  
  <dt>COUNT</dt>
  <dd>Total number of events.
  </dd>
  
  <dt>SIZE</dt>
  <dd>The total size of events in megabytes.
  </dd>

  <dt>TYPES</dt>
  <dd>This value is set to **ActivityTracker**.
  </dd>
  
  <dt>SEARCHABLE</dt>
  <dd>This field indicates if the events are available for search in Kibana. <br>When the value of the field **SEARCHABLE** is set to *None*, then events are available for download, but you can not anlyze them in Kibana.
  </dd>
  
</dl>

**Example**

To show details of events on 20 July 2017, run the following command:

```
bx cf at status -s 2017-07-20 -e 2017-07-20
```
{: codeblock}


You receive information similar to the following output:

```
+------------+-----------+-------+------------------+--------------+
|   Date     |  Count    | Size  | Types            |  Searchable  | 
+------------+-----------+-------+------------------+--------------+
| 2017-07-20 |    1      | 2531  | ActivityTracker  | All          | 
+------------+-----------+-------+------------------+--------------+
```
{: screen}



## bx cf at trail
{: #trail}

Send serialized events to {{site.data.keyword.cloudaccesstrailshort}}.

```
bx cf at trail [parameters] [arguments...]
```
{: codeblock}

**Parameters**

<dl>
  <dt>--file FILE, -f FILE</dt>
  <dd>(Optional) Specify the events file in the format: `PATH/filename`
  </dd>
  
  <dt>--type FORMAT, -t FORMAT</dt>
  <dd>(Optional) Specify the format of the events that are included in the file. Valid values are: *cadf*, and *kong*. <br> Use *CADF* to send events that comply with the CADF format. Use *KONG* to send events that comply with the Kong format. <br> **Note:** You can only send events of the same type in a file.
  </dd>
 </dl>
 
**Example**

To send serialized CADF events to {{site.data.keyword.cloudaccesstrailshort}}, run the following command:

```
bx cf at trail -t cadf -f events.log
```
{: codeblock}

where *events.log* is the file that contains the events that you want to send to {{site.data.keyword.cloudaccesstrailshort}}. This file include events that comply with the CADF format.

You receive information similar to the following output:

```
+--------------------------------------+---------------------------+
|            ID                        |          Value            |
+--------------------------------------+---------------------------+
| bbb170dc-2b0a-42d4-b560-b416f3308869 | B0UtwP1FhemsZIr4rTJVKA==  |
+--------------------------------------+---------------------------+
| 688f1194-2305-4367-8ece-f468e67c19fb | KLCG9f++usNolgvutRCR1Q==  |
+--------------------------------------+---------------------------+
```
{: screen}
