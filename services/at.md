---

copyright:
  years: 2016, 2018

lastupdated: "2018-05-12"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# {{site.data.keyword.cloudaccesstrailshort}}
{: #at}

Use the {{site.data.keyword.cloudaccesstrailfull}} service to track {{site.data.keyword.cloudaccesstrailshort}} in the {{site.data.keyword.Bluemix}}. 
{:shortdesc}


## How it works
{: #how}

When you manage {{site.data.keyword.cloudaccesstrailshort}} event data by using the CLI, events are generated to report on these actions. Each action generates one event. You can view these events through the {{site.data.keyword.cloudaccesstrailshort}} UI in the {{site.data.keyword.Bluemix_notm}} or in Kibana if you have a premium plan.



## API methods
{: #methods}

The following table lists the actions that generate an event when they are called:

<table>
  <caption>Table 1. Actions</caption>
  <tr>
    <th>Action</th>
	  <th>Description</th>
  <tr>
  <tr>
    <td>read.events</td>
	  <td>Get information about the events that are stored.</td>
  </tr>
  <tr>
    <td>create.sessions</td>
	  <td>Create a session that can be used to download events.</td>
  </tr>
  <tr>
    <td>delete.session</td>
	  <td>Delete a session.</td>
  </tr>
  <tr>
    <td>read.sessions</td>
	  <td>List the sessions.</td>
  </tr>
  <tr>
    <td>download.events</td>
	  <td>Download events.</td>
  </tr>
  <tr>
    <td>delete.events</td>
	  <td>Delete events.</td>
  </tr>
</table>


	
 	
 	