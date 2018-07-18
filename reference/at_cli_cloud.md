---

copyright:
  years: 2016, 2018
lastupdated: "2018-07-09"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# IBM Cloud Activity Tracker CLI
{: #at_cli_cloud}

You can use the {{site.data.keyword.cloudaccesstraillong}} CLI to manage {{site.data.keyword.cloudaccesstrailshort}} events.
{: shortdesc}

**Prerequisites**
* Before running the commands, log in to the {{site.data.keyword.Bluemix}} with the `ibmcloud login` command to generate an access token and authenticate your session.
* To manage events by using the CLI, you must have a paid plan.

The {{site.data.keyword.cloudaccesstraillong}} CLI plug-in supports Linux, Mac, and Windows platforms.

<table>
  <caption>Commands for managing {{site.data.keyword.cloudaccesstrailshort}}</caption>
  <tr>
    <th>Command</th>
    <th>When to use it</th>
  </tr>
  <tr>
    <td>[ibmcloud at](#base)</td>
    <td>Use this command to get information about the CLI, such as version or the list of commands.</td>
  </tr>
  <tr>
    <td>[ibmcloud at delete](#delete)</td>
    <td>Use this command to delete {{site.data.keyword.cloudaccesstrailshort}} events.</td>
  </tr>
  <tr>
    <td>[ibmcloud at download](#download)</td>
    <td>Use this command to download {{site.data.keyword.cloudaccesstrailshort}} logs to a local file. </td>
  </tr>
  <tr>
    <td>[ibmcloud at help](#help)</td>
    <td>Use this command to get help on how to use the CLI, and a list of all of the commands.</td>
  </tr>
  <tr>
    <td>[ibmcloud at option](#option)</td>
    <td>Use this command to view or change {{site.data.keyword.cloudaccesstrailshort}} event options, such as retention, that are available in a space or in an account.</td>
  </tr>
  <tr>
    <td>[ibmcloud at session create](#session_create)</td>
    <td>Use this command to create a new session.</td>
  </tr>
  <tr>
    <td>[ibmcloud at session delete](#session_delete)</td>
    <td>Use this command to delete a session.</td>
  </tr>  
  <tr>
    <td>[ibmcloud at session list](#session_list)</td>
    <td>Use this command to list active sessions and their IDs.</td>
  </tr>  
  <tr>
    <td>[ibmcloud at session show](#session_show)</td>
    <td>Use this command to show the status of a single session.</td>
  </tr>   
  <tr>
    <td>[ibmcloud at status](#status)</td>
    <td>Use this command to view information about the status of events that are stores in {{site.data.keyword.cloudaccesstrailshort}}.</td>
  </tr>
  </table>


## ibmcloud at
{: #base}

Provides information about the version of the CLI and how to use the CLI.

```
ibmcloud at [parameters]
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
ibmcloud at --help
```
{: codeblock}

To get the version of the CLI, run the following command:

```
ibmcloud at --version
```
{: codeblock}


## ibmcloud at delete
{: #delete}

Deletes {{site.data.keyword.cloudaccesstrailshort}} events.

```
ibmcloud at delete [parameters] [arguments..]
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
  
  <dt>--search-time value, -T value</dt>
  <dd>(Optional) You can set this parameter to delete events that are stored for a number of hours on a specific day. The format of the field is: 0-23
  </dd>

</dl>


**Example**

To delete the events for 22 June 2017, run the following command:
```
ibmcloud at delete -s 2017-06-22 -e 2017-06-22
```
{: codeblock}

You receive information similar to the following output:

`Deleted successfully`
`"6 logs were deleted, freeing 13737 bytes."`


## ibmcloud at download
{: #download}

Downloads {{site.data.keyword.cloudaccesstrailshort}} events to a local file or streams them out to a terminal window in Windows and Mac OS X, or to stdout in a Linux terminal. 

**Note:** To download files, you must create a session first. A session defines which events to download based on date range. You download events within the context of a session. 

```
ibmcloud at download [parameters] [arguments...]
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
<dd>Set the session ID value that you get when you run the command `ibmcloud at session create`. This value indicates which session to use when downloading events. <br>**Note:** The `ibmcloud at session create` command provides the parameters that control which events are downloaded. </dd>
</dl>

**Note:** After the download completes, to download the same data again, you must use a different file, or a different session.

**Example**

To download events into a file called `events.log`, run the following command:

```
ibmcloud at download -o events.log 1db6ce16-824d-4d50-bd40-37f1d8fea9b7
```
{: screen}

You receive information similar to the following output: 

```
6.70 KiB / 3.06 KiB [========] 219.03% 8.60 MiB/s 0s
Download completed successfully
```
{: screen}


## ibmcloud at help
{: #help}

Provides information about how to use a command.

```
ibmcloud at help [parameters]
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
ibmcloud at help status
```
{: codeblock}


## ibmcloud at option
{: #option}

Displays or changes the retention period for events that are available in a space. When you set a retention policy, events are deleted automatically when the number of retention days in reached.

* The period is set in number of days.
* The default value is **-1**, that is, events are stored and not deleted.

**Note:** By default, all the events are stored. If you do not set a retention period, you must delete them manually by using the `ibmcloud at delete` command. 

```
ibmcloud at option [parameters] [arguments...]
```
{: codeblock}

**Parameters**

<dl>
<dt>--retention value, -r value</dt>
<dd>(Optional) Sets the number of retention days. <br> The default value is *-1* days.</dd>

<dt>--at-account-level, -a</dt>
<dd>(Optional) Set this parameter to list information about the retention period for events that are stored in every space domain and in the account domain.

</dl>

**Example**

To see the current retention period for the space where you are logged in, run the following command:

```
ibmcloud at option
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
ibmcloud at option -r 25
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



## ibmcloud at session create
{: #session_create}

Creates a new session.

**Note:** You can have up to 30 concurrent sessions in a space. The session is created for a user. Sessions cannot be shared between users in a space.

```
ibmcloud at session create [parameters] [arguments...]
```
{: codeblock}

**Parameters**

<dl>
  <dt>--at-account-level, -a </dt>
  <dd>(Optional) Sets the scope to account level. </br>Set this value to get account information. <br>If this parameter is not specified, the default value is set to the current space only, that is, the space where you logged in by using the command `ibmcloud cf login`.
  </dd>

  <dt>--start value, -s value</dt>
  <dd>(Optional) Sets the start date in Universal Coordinated Time (UTC): *YYYY-MM-DD*, for example, `2017-01-02`. <br>The default value is set to 2 weeks ago. 
  </dd>
  
  <dt>--end value, -e value</dt>
  <dd>(Optional)  Sets the end date in Universal Coordinated Time (UTC): *YYYY-MM-DD*, for example, `2017-01-02`. <br>The default value is set to the current date. 
  </dd>

  <dt>--search-time value, -T value</dt>
  <dd>(Optional) You can set this parameter to delete events that are stored for a number of hours on a specific day. The format of the field is: 0-23
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
ibmcloud at session create -s 2017-07-10 -e 2017-07-10
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



## ibmcloud at session delete
{: #session_delete}

Deletes a session that is specified by the session ID.

```
ibmcloud at session delete [arguments...]
```
{: codeblock}


**Arguments**

<dl>
<dt>Session ID</dt>
<dd>ID of the session that you want to delete. <br>You can use the `ibmcloud at session list` command to get all the active session IDs.</dd>
</dl>

**Example**

To delete a session with session ID *9b8c4db8-5841-4993-a449-305815a53a8e*, run the following command:

```
ibmcloud at session delete 9b8c4db8-5841-4993-a449-305815a53a8e
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


## ibmcloud at session list
{: #session_list}

Lists the active sessions and their IDs.

```
ibmcloud at session list 
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
ibmcloud at session list
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


## ibmcloud at session show
{: #session_show}

Shows the status of a single session.

```
ibmcloud at session show [arguments...]
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
ibmcloud at session show 9b8c4db8-5841-4993-a449-305815a53a8e
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


## ibmcloud at status
{: #status}

Returns information about the status of {{site.data.keyword.cloudaccesstrailshort}} events.

```
ibmcloud at status [parameters] [arguments...]
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
  <dd>(Optional) Sets the scope to account level. <br> **Note:** Set this value to get account information. <br>If this parameter is not specified, the default value is set to the current space only, that is, the space where you logged in by using the command `ibmcloud cf login`.
  </dd>
  
</dl>


**Note:** The `ibmcloud at status` command reports only the last two weeks of events that are stored in {{site.data.keyword.cloudaccesstrailshort}} when no start and end dates are specified. 

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
ibmcloud at status -s 2017-07-20 -e 2017-07-20
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


