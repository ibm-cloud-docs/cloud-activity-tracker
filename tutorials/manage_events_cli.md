---

copyright:
  years: 2016, 2017

lastupdated: "2017-09-07"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# Managing events by using the Activity Tracker CLI
{: #tutorial2}

Use this tutorial to learn how to use the {{site.data.keyword.cloudaccesstrailshort}} CLI to manage events through the command line. Learn how to get information about stored events, how to download events that are stored in the {{site.data.keyword.IBM_notm}} Cloud, or how to delete events.
{:shortdesc}

Complete the following steps:

1. [Provision the {{site.data.keyword.IBM_notm}} Key Protect service and generate events](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step1)
2. [Get information about stored events (cf at status)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step2)
2. [Specify which logs to download by creating a session (cf at session create)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step3)
3. [Get the actual log data (cf at download)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step4)
4. [Delete the session after the download completes (cf at session delete)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step5)
5. [Manually delete logs that are not required (cf at delete)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step6)


## Assumptions
{: #assumptions}

1. You have a {{site.data.keyword.Bluemix_notm}} user ID that has developer permissions to work in a space of a {{site.data.keyword.Bluemix_notm}} account where the {{site.data.keyword.IBM_notm}} Cloud {{site.data.keyword.cloudaccesstrailshort}} service is provisoned. 

    For more information on how to provision the {{site.data.keyword.cloudaccesstrailshort}} service, see [Provisioning the {{site.data.keyword.cloudaccesstrailshort}} service](/docs/services/cloud-activity-tracker/how-to/provision.html#provision).

2. You have installed the {{site.data.keyword.cloudaccesstrailshort}} CF plugin in your local system. This is required for you to be able to use the {{site.data.keyword.cloudaccesstrailshort}} CLI to manage events through the command line. 

    For more information about installing the {{site.data.keyword.cloudaccesstrailshort}} CF plugin, see [Configuring the {{site.data.keyword.cloudaccesstrailshort}} CLI](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#config_at_cli).

3. You have logged in to {{site.data.keyword.Bluemix_notm}} through the command line by using the following command:

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

    For example, run the following command to log in to the US South region:
	
	```
	bx cf login -a api.ng.bluemix.net
	```
	{: codeblock}

	**Note:** You must log in to the region, organization, and space in {{site.data.keyword.Bluemix_notm}} where the {{site.data.keyword.cloudaccesstrailshort}} service is provisioned to be able to run {{site.data.keyword.cloudaccesstrailshort}} commands and manage your events through the command line.
	
	Then, set the organization and space. Run the following command:

    ```
    bx target -o OrgName -s SpaceName
    ```
    {: codeblock}

    where

    * OrgName is the name of the organization.
    * SpaceName is the name of the space.


## Step 1: Provision the IBM Key Protect service and generate events 
{: #step1}
	
1. Complete the following steps to provision an instance of the {{site.data.keyword.keymanagementserviceshort}} service in {{site.data.keyword.Bluemix_notm}}:

    1. Log in to your {{site.data.keyword.Bluemix_notm}} account.

        The {{site.data.keyword.Bluemix_notm}} dashboard can be found at: [http://bluemix.net](http://bluemix.net)

        After you log in with your user ID and password, the {{site.data.keyword.Bluemix_notm}} UI opens.

    2. Click **Catalog**. The list of the services that are available on {{site.data.keyword.Bluemix_notm}} opens.

        Select the **Security** category to filter the list of services that is displayed.

    3. Select the **Key Protect** tile.

    4. Click **Create** to provision the {{site.data.keyword.keymanagementserviceshort}} service in the {{site.data.keyword.Bluemix_notm}} space where you are logged in.

2. Complete the following steps to generate an {{site.data.keyword.cloudaccesstrailshort}} event:

    1. From the {{site.data.keyword.Bluemix_notm}} dashboard, select the {{site.data.keyword.keymanagementserviceshort}} service, The {{site.data.keyword.keymanagementserviceshort}} dashboard opens. Then, select the **Manage** tab.

    2. Click **Add Key**. A new window opens.

        ![{{site.data.keyword.keymanagementserviceshort}} window to add keys](images/KP_f2.gif)

    3. Select **Generate key**, and complete the following steps:

        * Enter a name for the key, for example, *MyFirstKey*.

        * Choose an algorith for the key.

        * Click **Add key**. 

3. Verify that an event has been created:

    1. From the {{site.data.keyword.Bluemix_notm}} Dashboard, select the {{site.data.keyword.cloudaccesstrailshort}} service. The service dashboard opens.

    2. Configure the view to search for the {{site.data.keyword.keymanagementserviceshort}} events that have been generated when you provisioned the service and added a key.

        * Select **Space logs** for the field *View logs*.
	    * Select **target.name** for the field *Search field*.
	    * Enter **ibm-key-protect** in *Filter* field.
	
	    The data that is displayed correspond to {{site.data.keyword.keymanagementserviceshort}} events that are available for the last 24 hours. 

	    ![{{site.data.keyword.cloudaccesstrailshort}} manage tab](images/KP_f3.gif)

## Step 2: Get information about stored events
{: #step2}

Check what events are available for download. For example, if you provision and add a key on the current date, run the following command to get information about events collected today:

```
bx cf at status -s 2017-07-25 -e 2017-07-25
+------------+-------+-------+------------+
| Date       | Count | Size  | Searchable |
+------------+-------+-------+------------+
| 2017-07-25 | 12    | 34994 | All        |
+------------+-------+-------+------------+
```
{: screen}

This command will count the events for 25 of June, 2017.  {{site.data.keyword.cloudaccesstrailshort}} is a global service, therefore, the days are Universal Time. To get a complete local-time day, you will likely need to download multiple UTC days.

To see the information for multiple days, use `-s` to set the start day and `-e` to set the end date. 

To learn more about the `cf at status` command, refer to the [CLI reference](/docs/services/cloud-activity-tracker/cli/at_cli.html#status).

Use `bx cf at help status` to get help from the command line.

## Step 3: Specify which events to download
{: #step3}

Before downloading events, create a session:

* The session specifies which events will be downloaded.
* If the download of the events is interrupted, the session enables resuming the download from where it left off.

Use the following command create a session:

```
bx cf at session create -s 2017-07-25 -e 2017-07-25
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

There is a start date and end date associated with a session. The download command will include events between those inclusive dates. The default date-range is the current day only. 

The important part of the command's output is the session `Id`. It is referenced in the download command.

To get information about existing sessions, type `cf at session list`.

To learn more about sessions and the `cf at session create` command, refer to the [CLI reference](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_create).

Use `cf at session help create` to get help from the command line.

## Step 4: Download the events that are identified for the scope defined for the session
{: #step4}

To download the events specified by the session parameters, run the following command:

```
$ bx cf at events download -o events.log 21b19aeb-3d32-4c60-b912-517609c62db2
 6.70 KiB / 3.06 KiB [================================================================================================================================================================] 219.03% 8.60 MiB/s 0s
Download Successful
```

* The `-o` parameter specifies an output file.
* The session ID is specified last. You get the value of the session ID from the output of the `cf at session create` command.
* The progress indicator moves from 0 to 100% as the events download.

The format of the downloaded data is compressed JSON. 

To learn more about the `cf at download` command, refer to the [CLI reference](/docs/services/cloud-activity-tracker/cli/at_cli.html#download).

Use `bx cf at help download` to get help from the command line.

## Step 5: Delete the session
{: #step5}

After the download completes, delete the session. 

The number of sessions is limited. A session is not deleted automatically. You must manually delete sessions that are not required. 

```
$ bx cf at session delete 21b19aeb-3d32-4c60-b912-517609c62db2
+---------+------------------------+
| name    | value                  |
+---------+------------------------+
| message | Delete session success |
+---------+------------------------+
```

To learn more about the `cf at session delete` command, refer to the [CLI reference](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_delete).

Use `bx cf at session help delete` to get help from the command line.

## Step 6: Delete events from Activity Tracker manually
{: #step6}

You have control of your own event retention in {{site.data.keyword.cloudaccesstrailshort}}. You can delete events manually, or you can automate the deletion of events.

To delete events manually, run the `cf at delete` command. For example,

```
$ bx cf at delete -s 2017-07-25 -e 2017-07-25
Deleted successfully
"6 logs were deleted,freeing 13737 bytes."
```

To learn more about the `cf at delete`command, refer to the [CLI reference](/docs/services/cloud-activity-tracker/cli/at_cli.html#delete).

Use `bx cf at help delete` to get help from the command line.

**Note:** To delete events automatically, you can set a retention policy by using the CLI command `cf at option`. For more information, see [CLI reference](/docs/services/cloud-activity-tracker/cli/at_cli.html#option)


