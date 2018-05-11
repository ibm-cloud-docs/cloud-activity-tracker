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



# Activity Tracker event fields
{: #at_event}

{{site.data.keyword.cloudaccesstrailshort}} events are based on the Cloud Auditing Data Federation (CADF) standard. 
{:shortdesc}

## Common event fields
{: #fields}

The following table list common fields that are available for an {{site.data.keyword.cloudaccesstrailshort}} event:

<table>
  <caption>Table 1. Common fields that are available for an {{site.data.keyword.cloudaccesstrailshort}} event</caption>
  <tr>
    <th>Field Name</th>
	  <th>Description</th>
  </tr>
  <tr>
    <td>initiator.id</td>
	  <td>ID that identifies who initiated the action, for example, IBM ID, or ID of an API key.</td>
  </tr>
  <tr>
    <td>initiator.typeURI</td>
	  <td>Type of the source of the event, for example, *service/security/account/user*</td>
  </tr>
  <tr>
    <td>initiator.credential.type</td>
	  <td>Type of initiator. Valid values are: *user*, *service*.</td>
  </tr>
  <tr>
    <td>target.id</td>
	  <td>ID of the target service.</td>
  </tr>
  <tr>
    <td>target.name</td>
	  <td>Human-readable name of the target service, for example, *IAMTokenService*.</td>
  </tr>
  <tr>
    <td>target.typeURI</td>
	  <td>Type of the target of the event, for example, `https://iam-id-1.ng.bluemix.net/iam/audit/login/apikey`.</td>
  </tr>
  <tr>
    <td>action</td>
	  <td>Action that triggers the event, for example, */iam/audit/login/apikey*.</td>
  </tr>
  <tr>
    <td>outcome</td>
	  <td>Result of the action. For example, valid values are *success*, or *failure*.</td>
  </tr>
  <tr>
    <td>reason.reasonCode</td>
	  <td>Numeric field that includes the HTTP response code, for example, *200* for success.</td>
  </tr>
  <tr>
    <td>severity</td>
	  <td>Defines the severity level of the event, for example: *normal*, or *critical*.</td>
  </tr>
  <tr>
    <td>eventTime</td>
	  <td>Indicates the timestamp when the event was created. The date is represented as Universal Time Coordinated (UTC).</td>
  </tr>
</table>

 

