---

copyright:
  years: 2016, 2018

lastupdated: "2018-07-02"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# Service instance events  
{: #at_events}

As a security officer, auditor, or manager, you can use the {{site.data.keyword.cloudaccesstrailfull}} service to track how users and applications interact with the {{site.data.keyword.Bluemix}} services. 
{:shortdesc}

The {{site.data.keyword.cloudaccesstrailfull_notm}} service records user-initiated activities that change the state of a service in {{site.data.keyword.Bluemix_notm}}. For more information, see [About {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#activity_tracker_ov ).

To get started monitoring your user's actions, see [{{site.data.keyword.cloudaccesstrailfull_notm}}](/docs/services/cloud-activity-tracker/index.html#getting-started-with-cla). 

## Events for provisioning and managing service instances
{: #provision}

The following table lists the API methods that generate an event when they are called:

<table>
  <caption>Actions that generate events</caption>
  <tr>
    <th>Action</th>
	  <th>Description</th>
  </tr>
  <tr>
    <td><i>service_name</i>.instance.create</td>
	  <td>An event is generated when you provision a service instance.</td>
  </tr>
  <tr>
    <td><i>service_name</i>.instance.update</td>
	  <td>An event is generated when you rename a service instance or when you change the service plan.</td>
  </tr>
  <tr>
    <td><i>service_name</i>.instance.delete</td>
	  <td>An event is generated when a service instance is deleted.</td>
  </tr>
</table>


##  Events for managing API keys that are associated to a service instance
{: #keys}

The following table lists the API methods that generate an event when they are called:

<table>
  <caption>Actions that generate events</caption>
  <tr>
    <th>Action</th>
	  <th>Description</th>
  </tr>
  <tr>
    <td><i>service_name</i>.key.create</td>
	  <td>An event is generated when an API key is created for a service instance through the *Service credentials* section of the service instance UI.</td>
  </tr>
  <tr>
    <td><i>service_name</i>.key.delete</td>
	  <td>An event is generated when an API key that is associated with a service instance is deleted from the *Service credentials* section of the service instance UI.</td>
  </tr>
</table>

##  Events for binding a service instance to an app
{: #bind}

The following table lists the API methods that generate an event when they are called:

<table>
  <caption>Actions that generate events</caption>
  <tr>
    <th>Action</th>
	  <th>Description</th>
  </tr>
  <tr>
    <td><i>service_name</i>.binding.create</td>
	  <td>An event is generated when you bind a service instance to an application.</td>
  </tr>
  <tr>
    <td><i>service_name</i>.binding.delete</td>
	  <td>An event is generated when you unbind a service instance from an application.</td>
  </tr>
</table>




## Where to look for the events
{: #ui}

{{site.data.keyword.cloudaccesstrailshort}} events are available in the {{site.data.keyword.cloudaccesstrailshort}} **account domain** that is available in the {{site.data.keyword.Bluemix_notm}} region where the events are generated. For more information, see [Viewing account events](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/viewing_events.html#account_events).

{{site.data.keyword.cloudaccesstrailshort}} events are automatically forwarded to the {{site.data.keyword.cloudaccesstrailshort}} service in the same region where the action happens.



