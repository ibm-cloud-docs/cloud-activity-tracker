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

# Deleting events
{: #deleting_events}

Use the *cf at delete* command to delete manually events that are stored in {{site.data.keyword.cloudaccesstrailshort}} for a {{site.data.keyword.Bluemix}} space.
{:shortdesc}

## Deleting events
{: #viewing_events}

Use the `cf at status` command to view the size, count, and whether the events are available or not for analysis in Kibana. For more information, see [cf at status](/docs/services/cloud-activity-tracker/cli/at_cli.html#status).

1. Log in to a {{site.data.keyword.Bluemix_notm}} region, organization, and space. 

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

2. Run the *cf at status* command.

    ```
    $ bx cf at status -a -s YYYY-MM-DD -e YYYY-MM-DD 
    ```
    {: codeblock}
    
    where
    
    * *-a* is used to specify that the request applies to all spaces in the account.
    * *-s* is used to set the start date in Universal Coordinated Time (UTC): *YYYY-MM-DD*.
    * *-e* is used to set the end date in Universal Coordinated Time (UTC): *YYYY-MM-DD*.
    	
	Use `cf at status` command with the options **-s** to set the start day and **-e** to set the end date. For example:

    * `bx cf at status` provides information for the last 2 weeks.
    * `bx cf at status -s 2017-05-03` provides information from May 3rd, 2017 till the current date.
    * `bx cf at status -s 2017-05-03 -e 2017-05-08` provides information between May 3, 2017 and May 8, 2017. 
 
    Use `cf at status` command with the option **-a** to set the donain to account.
	
    For example, to get information about the events that are available for 10 of June 2017, run the following command:
    
    ```
    $ bx cf at status -s 2017-06-10 -e 2017-06-10
    +------------+-------+------+------------+
    | Date       | Count | Size | Searchable |
    +------------+-------+------+------------+
    | 2017-07-10 | 1     | 2531 | All        |
    +------------+-------+------+------------+
    ```
    {: screen}
	









