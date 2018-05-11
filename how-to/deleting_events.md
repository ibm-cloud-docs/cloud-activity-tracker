---

copyright:
  years: 2016, 2018
lastupdated: "2018-04-27"

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

Use the *bx at delete* command to delete manually events that are stored in {{site.data.keyword.cloudaccesstrailshort}} for a {{site.data.keyword.Bluemix}} space.
{:shortdesc}

## Deleting events
{: #viewing_events}

Use the `bx at status` command to view the size, count, and whether the events are available or not for analysis in Kibana. 

Complete the following steps to delete events:

1. Log in to a region, organization, and space in the {{site.data.keyword.Bluemix_notm}}. 

2. Run the *bx at status* command to check what events are available for download.

    ```
    $ bx at status -a -s YYYY-MM-DD -e YYYY-MM-DD 
    ```
    {: codeblock}
    
    where
    
    * *-a* is used to specify that the request applies to all spaces in the account.
    * *-s* is used to set the start date in Universal Coordinated Time (UTC): *YYYY-MM-DD*.
    * *-e* is used to set the end date in Universal Coordinated Time (UTC): *YYYY-MM-DD*.
    	
	Use `bx at status` command with the options **-s** to set the start day and **-e** to set the end date. For example:

    * `bx at status` provides information for the last 2 weeks.
    * `bx at status -s 2017-05-03` provides information from May 3rd, 2017 till the current date.
    * `bx at status -s 2017-05-03 -e 2017-05-08` provides information between May 3, 2017 and May 8, 2017. 
 
    Use `bx at status` command with the option **-a** to set the domain to account.
	
    For example, to get information about the events that are available for 10 of June 2017, run the following command:
    
    ```
    $ bx at status -s 2017-06-10 -e 2017-06-10
    +------------+-------+------------+
    | Date       | Count | Searchable |
    +------------+-------+------------+
    | 2017-06-10 | 1     | All        |
    +------------+-------+------------+
    ```
    {: screen}
	
3. Delete events. Run the following command:

    ```
	bx at delete [parameters] [arguments..]
	```
	{: codeblock}

    where 	

    Parameters

    --start value, -s value
        
		(Optional) Sets the start date in Universal Coordinated Time (UTC): YYYY-MM-DD, for example, 2017-01-02.
    
	    The default value is set to 2 weeks ago. 
		
    --end value, -e value
	
        (Optional) Sets the end date in Universal Coordinated Time (UTC): YYYY-MM-DD
		
        The UTC format of the date is YYYY-MM-DD, for example, 2017-01-02.
		
        The default value is set to the current date. 

    For example, to delete the events for 10 June 2017, run the following command:

	```
	bx at delete -s 2017-06-10 -e 2017-06-10
	```
	{: screen}

    You receive information about the log records that have been deleted.







