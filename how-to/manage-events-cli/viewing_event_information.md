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

# Viewing event information
{: #viewing_event_status}

Use the *cf at status* command to obtain information about the events that are collected and stored in {{site.data.keyword.cloudaccesstrailshort}} for a {{site.data.keyword.Bluemix}} space.
{:shortdesc}

## Obtaining information about events
{: #viewing_event_information}

Use the `cf at status` command to view the size, count, and whether the events are available or not for analysis in Kibana. For more information, see [cf at status](/docs/services/cloud-activity-tracker/cli/at_cli.html#status).

1. Log in to a region, organization, and space in the {{site.data.keyword.Bluemix_notm}}. 

    For more information, see [How do I log in to the {{site.data.keyword.Bluemix_notm}}](/docs/services/cloud-activity-tracker/qa/cli_qa.html#login).
    
2. Run the *bx cf at status* command to view details of the events that are collected in {{site.data.keyword.cloudaccesstrailshort}}.

    ```
    $ bx cf at status -a -s YYYY-MM-DD -e YYYY-MM-DD 
    ```
    {: codeblock}
    
    where
    
    * *-a* is used to specify account level information
    * *-s* is used to set the start date in Universal Coordinated Time (UTC): *YYYY-MM-DD*
    * *-e* is used to set the end date in Universal Coordinated Time (UTC): *YYYY-MM-DD*
    	
	Use `cf at status` command with the options **-s** to set the start day and **-e** to set the end date. For example:

    * `bx cf at status` provides information for the last 2 weeks.
    * `bx cf at status -s 2017-05-03` provides information from May 3rd, 2017 till the current date.
    * `bx cf at status -s 2017-05-03 -e 2017-05-08` provides information between May 3, 2017 and May 8, 2017. 
 
    Use `cf at status` command with the option **-a** to set the donain to account.
	
    For example, to get information about the events that are available for 10 of June 2017, run the following command:
    
    ```
    $ bx cf at status -s 2017-06-10 -e 2017-06-10
    +------------+-------+------+-----------------+------------+
    | Date       | Count | Size | Types           | Searchable |
    +------------+-------+------+-----------------+------------+
    | 2017-06-10 | 1     | 2531 | ActivityTracker | All        |
    +------------+-------+------+-----------------+------------+
    ```
    {: screen}
	









