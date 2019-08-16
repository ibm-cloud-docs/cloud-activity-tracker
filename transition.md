---

copyright:
  years: 2016, 2019
lastupdated: "2019-08-16"

keywords: IBM Cloud, Activity Tracker, migration

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


# Transitioning to {{site.data.keyword.at_full_notm}}
{: #transition}

{{site.data.keyword.cloudaccesstrailfull}} is deprecated on 9 May 2019. [Learn more](https://www.ibm.com/blogs/cloud-archive/2019/04/deprecating-ibm-cloud-activity-tracker/). The service is replaced by {{site.data.keyword.at_full_notm}}. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started).
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} is deprecated. As of 9 May 2019, you cannot provision new {{site.data.keyword.cloudaccesstrailshort}} instances. Existing premium plan instances are supported until 30 September 2019. To continue monitoring the activity of your {{site.data.keyword.cloud_notm}} account, provision an instance of the [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}


Complete the following steps to migrate to {{site.data.keyword.at_full_notm}}: 

1. Save a copy of the events that are stored in {{site.data.keyword.cloudaccesstrailfull}} for long term search. You can use the {{site.data.keyword.cloudaccesstrailshort}} CLI or the API. 

    Ensure that you save space events for each Cloud Foundry space where you have a legacy {{site.data.keyword.cloudaccesstrailshort}} instance, and for each account domain in each region that you currently monitor.

    * [Downloading events by using the CLI](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-downloading_events).

    * [Downloading events by using the API](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-downloading_events_api).

    Use the `-a` flag to download all events in your accountby using the CLI, and `AtAccountLevel: true` when you use the API. This download includes account and the space events from where you are accessing the global domain.
    {: important}

    If you download too much data at one time, it can fail due to network time-outs. If that occurs, download one day (or hour) at a time. 

2. Provision [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-provision).

    You can provision only 1 instance per region. 
    
3. Create and configure access groups to manage permissions in the {{site.data.keyword.cloud_notm}}. 

    * [Granting administration permissions to a user or service ID](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-iam_manage_events).

    * [Granting user permissions to a user or service ID](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-iam_view_events).

4. Define views and dashboards in {{site.data.keyword.at_full_notm}} to analyze and manage events. [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-views).

    Migration of Kibana dashboards to LogDNA dashboards is not automated. You have to manually implement new dashboards. 

    Notice that in LogDNA, histograms ands pies are the only visualizations that you can implement.

5. [Optional] Configure archiving for your {{site.data.keyword.at_full_notm}} instance. 

    You can archive events to {{site.data.keyword.cos_full_notm}} (COS). [Learn more](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-archiving).

    **Note:** You are responsible for provisioning a COS instance that is used to archive events and for maintaining archived events. 

    This step is only required for {{site.data.keyword.at_full_notm}} instances that have a paid plan.

6. Explore other features such as [alerting](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-alerts).


When you are ready to stop monitoring your Cloud activity through your legacy {{site.data.keyword.cloudaccesstrailshort}} instances, complete the following steps:

1. Delete the legacy {{site.data.keyword.cloudaccesstrailshort}} instances from the {{site.data.keyword.cloud_notm}} console.
2. Remove any permissions to users to work with these legacy instances. 


