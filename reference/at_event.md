---

copyright:
  years: 2016, 2017

lastupdated: "2017-11-09"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# Activity Tracker event fields
{: #at_event}

{{site.data.keyword.cloudaccesstrailshort}} events are based on the Cloud Auditing Data Federation (CADF) standard. 
{:shortdesc}

## Event fields
{: #fields}

The following table list the fields that are available for analysis for an {{site.data.keyword.cloudaccesstrailshort}} event:

<table>
  <caption>Table 1. Fields that are available for monitoring per event.</caption>
  <tr>
    <th>Field Name</th>
	<th>Status</th>
	<th>Description</th>
  </tr>
  <tr>
    <td>outcome</td>
	<td>Required</td>
	<td>Valid values are: *success*, *failure*</td>
  </tr>
  <tr>
    <td>typeURI</td>
	<td>Required</td>
	<td>This field is set to: *http://schemas.dmtf.org/cloud/audit/1.0/event*</td>
  </tr>
  <tr>
    <td>eventType</td>
	<td>Required</td>
	<td>This field is set to *activity*.</td>
  </tr>
  <tr>
    <td>eventTime</td>
	<td>Required</td>
	<td>(The date is represented as an ISO string, for example: *2017-09-17 15:15:32.396 +0000 UTC*.</td>
  </tr>
  <tr>
    <td>action</td>
	<td>Required</td>
	<td>This field indicates the action that triggered the event, for example, *read.ibm-key-protect.secrets*.</td>
  </tr>
  <tr>
    <td>id</td>
	<td>Optional</td>
	<td>This field contains the UUID of the event.</td>
  </tr>
  <tr>
    <td>initiator.id</td>
	<td>Required</td>
	<td>This field contains the ID for the source of the event, such as an instance id.</td>
  </tr>
  <tr>
    <td>initiator.name</td>
	<td>Optional</td>
	<td>This field provides a human-readable name for the source of the event, such as a userid.</td>
  </tr>
  <tr>
    <td>initiator.typeURI</td>
	<td>Required</td>
	<td>This field informs about the type of the source of the event, for example, *service/security/account/user*</td>
  </tr>
  <tr>
    <td>initiator.host.agent</td>
	<td>Optional</td>
	<td>This field indicates the client that was used to send the request, for example, *python-neutronclient* or browser info.</td>
  </tr>
  <tr>
    <td>initiator.host.address</td>
	<td>Optional</td>
	<td>This field includes the initiator's IP address.</td>
  </tr>
  <tr>
    <td>target.id</td>
	<td>Required</td>
	<td>This field includes the ID of the target service.</td>
  </tr>
  <tr>
    <td>target.name</td>
	<td>Required</td>
	<td>This field includes the human-readable name of the target service, for example, *ibm-key-protect*.</td>
  </tr>
  <tr>
    <td>target.typeURI</td>
	<td>Required</td>
	<td>This field includes the type of the target of the event, for example, *service/ibm-key-protect/secrets*.</td>
  </tr>
  <tr>
    <td>target.host.address</td>
	<td>Optional</td>
	<td>This field includes the IP Address or URL of the target service, for example, *xxx.bluemix.net*.</td>
  </tr>
  <tr>
    <td>observer.name</td>
	<td>Required</td>
	<td>This field is set to the following value: *ActivityTracker*</td>
  </tr>
  <tr>
    <td>observer.id</td>
	<td>Required</td>
	<td>This field includes information about the resource that creates and stores the CADF event, for example, *activitytracker.ng.bluemix.net*.</td>
  </tr>
  <tr>
    <td>observer.typeURI</td>
	<td>Required</td>
	<td>This field is set to the following value: *service/security/edge/activity-tracker*</td>
  </tr>
  <tr>
    <td>reason.reasonCode</td>
	<td>Optional</td>
	<td>This field includes the HTTP response code, for example, *200* for success.</td>
  </tr>
  <tr>
    <td>reason.reasonType</td>
	<td>Required</td>
	<td>This field includes information about the reasonCode when one is provided through the *reason.reasonCode* field.</td>
  </tr>
</table>

 

