---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, view events, UI

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

# Viewing events
{: #view_acc_events}

You can view events through the {{site.data.keyword.cloudaccesstrailshort}} UI in the {{site.data.keyword.cloud_notm}} console or through Kibana.
{:shortdesc}
   
{{site.data.keyword.cloudaccesstrailfull}} is deprecated. As of 9 May 2019, you cannot provision new {{site.data.keyword.cloudaccesstrailshort}} instances. Existing premium plan instances are supported until 9 October 2019. To continue monitoring the activity of your {{site.data.keyword.cloud_notm}} account, provision an instance of the [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}


## Viewing account events
{: #view_acc_events_account_events}

You can view events in an {{site.data.keyword.cloudaccesstrailshort}} account domain through the {{site.data.keyword.cloudaccesstrailshort}} UI or through Kibana.

An **account owner** has permissions to view events in an {{site.data.keyword.cloudaccesstrailshort}} account domain through the {{site.data.keyword.cloudaccesstrailshort}} UI or through Kibana.

As a **member in an account**, consider the following information to view account events in a region:

* You must have *developer* role in the space where {{site.data.keyword.cloudaccesstrailshort}} is provisioned. For more information, see [Granting a CF role](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-grant_permissions#grant_cf_role).

* You must have an IAM policy for the {{site.data.keyword.loganalysisshort}} service with *viewer* role in that region. Viewer role is the minimum IAM role required. For more information, see [Granting IAM permisisons](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-grant_permissions#grant_iam_policy).

* You can view events through Kibana. For more information on how to launch Kibana, see [Navigating to Kibana from a web browser](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-launch_kibana#launch_Kibana_from_browser).



## Viewing space events
{: #view_acc_events_space_events}

You can view events in an {{site.data.keyword.cloudaccesstrailshort}} space domain through the {{site.data.keyword.cloudaccesstrailshort}} UI. If you have a premium plan, you can also see events through Kibana.

An **account owner** has permissions to view events for any {{site.data.keyword.cloudaccesstrailshort}} space domain.

As a **member in an account**, you must have *developer* role in the space where {{site.data.keyword.cloudaccesstrailshort}} is provisioned.


