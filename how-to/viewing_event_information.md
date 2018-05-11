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


# Viewing event information
{: #viewing_event_status}

Use the *bx at status* command to obtain information about the events that are collected and stored in {{site.data.keyword.cloudaccesstrailshort}} for a {{site.data.keyword.Bluemix}} space.
{:shortdesc}

## Obtaining information about events
{: #viewing_event_information}

Use the `bx at status` command to view the size, count, and whether the events are available or not for analysis in Kibana. 

1. Log in to a region, organization, and space in the {{site.data.keyword.Bluemix_notm}}. 

2. Run the *bx at status* command to view details of the events that are collected in {{site.data.keyword.cloudaccesstrailshort}}.

    ```
    $ bx at status -a -s YYYY-MM-DD -e YYYY-MM-DD 
    ```
    {: codeblock}
    
    where
    
    * *-a* is used to specify account level information
    * *-s* is used to set the start date in Universal Coordinated Time (UTC): *YYYY-MM-DD*
    * *-e* is used to set the end date in Universal Coordinated Time (UTC): *YYYY-MM-DD*
    	
	Use `bx at status` command with the options **-s** to set the start day and **-e** to set the end date. For example:

    * `bx at status` provides information for the last 2 weeks.
    * `bx at status -s 2017-05-03` provides information from May 3rd, 2017 till the current date.
    * `bx at status -s 2017-05-03 -e 2017-05-08` provides information between May 3, 2017 and May 8, 2017. 
 
    Use `cf at status` command with the option **-a** to set the donain to account.
	
    For example, to get information about the events that are available for 10 of June 2017, run the following command:
    
    ```
    $ bx at status -s 2017-06-10 -e 2017-06-10
    +------------+-------+------------+
    | Date       | Count | Searchable |
    +------------+-------+------------+
    | 2017-06-10 | 10    | All        |
    +------------+-------+------------+
    ```
    {: screen}
	









