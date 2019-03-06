---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, IAM events

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


# IAM events
{: #at_events_iam}

As a security officer, auditor, or manager, you can use the {{site.data.keyword.cloudaccesstrailfull}} service to track how users and applications interact with the {{site.data.keyword.iamlong}} (IAM) service in {{site.data.keyword.Bluemix}}. 
{:shortdesc}

The {{site.data.keyword.cloudaccesstrailfull_notm}} service records user-initiated activities that change the state of a service in {{site.data.keyword.cloud_notm}}. For more information, see [About {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov).

To get started monitoring your user's actions, see [{{site.data.keyword.cloudaccesstrailfull_notm}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started-with-cla#getting-started-with-cla). 

An initiator can be a user, a service, or an application.
{: tip}

## Managing access groups events
{: #at_events_iam_access}

The following table lists the actions that generate an event:

| Action | Description |
|----------|---------|
| `iam-groups.group.create`   | An event is generated when an initiator creates an access group. | 
| `iam-groups.group.read`     | An event is generated when an initiator looks at information that is related with access groups. |
| `iam-groups.group.update`   | An event is generated when an initiator updates a group name or a description. |
| `iam-groups.group.delete`   | An event is generated when an initiator deletes an access group. |
| `iam-groups.member.add`     | An event is generated when an initiator adds a member to an access group. |
| `iam-groups.member.delete`  | An event is generated when an initiator removes a member from an access group. |
| `iam-groups.member.read`    | An event is generated when an initiator checks a member's membership. |
| `iam-groups.rule.read`      | An event is generated when an initiator views a rule in an access group. |
| `iam-groups.rule.create`    | An event is generated when an initiator adds a rule to an access group. |
| `iam-groups.rule.update`    | An event is generated when an initiator modifies the rule name. |
| `iam-groups.rule.delete`    | An event is generated when an initiator deletes a rule from an access group. |
{: caption="Table 1. Manage access groups actions" caption-side="top"} 



## Working with service IDs events
{: #at_events_iam_serviceids}

The following table lists the actions that generate an event:

| Action | Description |
|----------|---------|
| `iam-identity.account-serviceid.create` | An event is generated when an initiator creates a service ID.  | 
| `iam-identity.account-serviceid.update` | An event is generated when an initiator renames a service ID or modifies its description. | 
| `iam-identity.account-serviceid.delete` | An event is generated when an initiator deletes a service ID. | 
{: caption="Table 2. Working with service IDs actions" caption-side="top"} 


## Working with API keys events
{: #at_events_iam_apikeys}

The following table lists the actions that generate an event:

| Action | Description |
|----------|---------|
| `iam-identity.user-apikey.create`      | An event is generated when an initiator creates an API key. | 
| `iam-identity.user-apikey.update`      | An event is generated when an initiator renames an API key or modifies its description. |  
| `iam-identity.user-apikey.delete`      | An event is generated when an initiator deletes an API key. |  
| `iam-identity.serviceid-apikey.create` | An event is generated when an initiator creates an API key for a service ID. |  
| `iam-identity.serviceid-apikey.delete` | An event is generated when an initiator deletes an API key for a service ID. |  
{: caption="Table 3. Working with API keys actions" caption-side="top"} 


## Logging in events
{: #at_events_iam_login}

The following table lists the actions that generate an event:

| Action | Description |
|----------|---------|
| `iam-identity.user-apikey.login`         | An event is generated when a user logs in to the {{site.data.keyword.cloud_notm}} by using an API key. |  
| `iam-identity.serviceid-apikey.login`    | An event is generated when an initiator logs in to the {{site.data.keyword.cloud_notm}} by using an API key that is associated with a service ID. |  
| `iam-identity.user-identitycookie.login` | This is an event that is generated when an initiator requests a new identity cookie to run an action. |
| `iam-identity.user-refreshtoken.login`   | This is an event that is generated when the initiator logs in to the IBM Cloud , or when an initiator that has already logged in to the IBM Cloud requests a new refresh token to run an action. |
{: caption="Table 4. User login actions" caption-side="top"} 


## Managing policies events
{: #at_events_iam_policies}

The following table lists the actions that generate an event:

| Action | Description |
|----------|---------|
| `iam-am.policy.create` | An event is generated when an initiator adds a policy to a user or access group. |
| `iam-am.policy.delete` | An event is generated when an initiator modifies permissions to a policy of a user or access group.|
| `iam-am.policy.update` | An event is generated when an initiator deletes a policy that is assigned to a user or access group. |
{: caption="Table 5. Managing policy actions" caption-side="top"} 


## Viewing events
{: #at_events_iam_ui}

{{site.data.keyword.cloudaccesstrailshort}} events are available in the **US-South** region **account domain**.

To view these events, you must provision an instance of the {{site.data.keyword.cloudaccesstrailshort}} service in the **US-South** region. Then, you must open the {{site.data.keyword.cloudaccesstrailshort}} UI, and change to the account domain to see events. 

For more information, see [Viewing account events](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-view_acc_events#view_acc_events_account_events).



