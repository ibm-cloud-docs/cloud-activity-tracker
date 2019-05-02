---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, account events

subcollection: cloud-activity-tracker

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}

# Account management events  
{: #at_events_acc_mgt}

As a security officer, auditor, or manager, you can use the {{site.data.keyword.cloudaccesstrailfull}} service to track how users and applications interact with the {{site.data.keyword.Bluemix}} account. 
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} is deprecated. As of 9 May 2019, you cannot provision new {{site.data.keyword.cloudaccesstrailshort}} instances. Existing premium plan instances are supported until 30 September 2019. To continue monitoring the activity of your {{site.data.keyword.cloud_notm}} account, provision an instance of the [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}

The {{site.data.keyword.cloudaccesstrailfull_notm}} service records user-initiated activities that change the state of a service in {{site.data.keyword.cloud_notm}}. For more information, see [About {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov).

To get started monitoring your user's actions, see [{{site.data.keyword.cloudaccesstrailfull_notm}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started). 



## Events for managing accounts
{: #at_events_acc_mgt_account}

The following table lists the API method that generates an event when they are called:

<table>
  <caption>Actions that generate events</caption>
  <tr>
    <th>Action</th>
	  <th>Description</th>
  </tr>
  <tr>
    <td>billing.account.create</td>
	  <td>An event is generated when you provison an account, after the account ID is asigned to the account.</td>
  </tr>
  <tr>
    <td>billing.account.update</td>
	  <td>An event is generated when you update information about the account.</td>
  </tr>
  <tr>
    <td>billing.account.active</td>
	  <td>An event is generated when you verify the account, that is, an event is generated when the account becomes active.</td>
  </tr>
  <tr>
    <td>billing.account.subscription.create</td>
	  <td>An event is generated when you create a <a href="/docs/account?topic=account-accounts#subscription-account">Subscription account</a>.</td>
  </tr>
</table>



## Events for managing users
{: #at_events_acc_mgt_users}

The following table lists the API method that generates an event when they are called:

<table>
  <caption>Actions that generate events</caption>
  <tr>
    <th>Action</th>
	  <th>Description</th>
  </tr>
  <tr>
    <td>user-management.user.create</td>
	  <td>An event is generated when you send an invitation to a user to join an account. </br>The account owner is the only user in the account that can perform this action.</td>
  </tr>
  <tr>
    <td>user-management.user.active</td>
	  <td>An event is generated when you activate the user in the account. </br>When the user verifies his email address, the event is generated.</td>
  </tr>
  <tr>
    <td>user-management.user.delete</td>
	  <td>An event is generated when you remove a user from the account. </br>The account owner is the only user in the account that can perform this action.</td>
  </tr>
</table>

## Events for managing organizations
{: #at_events_acc_mgt_org}

The following table lists the API method that generates an event when they are called:

<table>
  <caption>Action that generates events</caption>
  <tr>
    <th>Action</th>
	  <th>Description</th>
  </tr>
  <tr>
    <td>billing.account.org.create</td>
	  <td>An event is generated when you add an organization to the account.</td>
  </tr>
</table>

## Where to look for the events
{: #at_events_acc_mgt_ui}

{{site.data.keyword.cloudaccesstrailshort}} events are available in the **US-South** region **account domain**. 

To view these events, you must provision an instance of the {{site.data.keyword.cloudaccesstrailshort}} service in the **US-South** region. Then, you must open the {{site.data.keyword.cloudaccesstrailshort}} UI, and change to the account domain to see events. 

For more information, see [Viewing account events](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-view_acc_events#view_acc_events_account_events).






