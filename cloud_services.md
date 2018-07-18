---

copyright:
  years: 2016, 2018
lastupdated: "2018-07-09"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}



# Cloud services
{: #cloud_services}

Use the {{site.data.keyword.cloudaccesstraillong}} service to monitor user-initiated activities that change the state of any of the following services in the {{site.data.keyword.IBM_notm}} Cloud:
{:shortdesc}

**Note:** To get information about the regions where a service is available in the {{site.data.keyword.Bluemix_notm}}, see [Services by region](/docs/resources/services_region.html#services_region).

## Infrastructure: {{site.data.keyword.containershort_notm}}
{: #icks}

The {{site.data.keyword.containershort_notm}} generates two types of {{site.data.keyword.cloudaccesstrailshort}} events:

* **Cluster management events**: 
    
    * These events are automatically generated.
    * These events are automatically forwarded to {{site.data.keyword.cloudaccesstrailshort}}.
    * You can view these events through the {{site.data.keyword.cloudaccesstrailshort}} **account domain**. 

* **Kubernetes API server audit events**: 

    * These events are automatically generated.
    * You must configure your cluster to forward these events to the {{site.data.keyword.cloudaccesstrailshort}} service.
    * You can configure your cluster to send events to the {{site.data.keyword.cloudaccesstrailshort}} **account domain** or to a **space domain**. For more information, see [Sending audit logs](/docs/containers/cs_health.html#api_forward).

The following table lists the types of events that are sent by the {{site.data.keyword.containershort_notm}} to {{site.data.keyword.cloudaccesstrailshort}}:

<table>
  <caption>Types of events that are sent by the {{site.data.keyword.containershort_notm}}</caption>
  <tr>
    <th>Type</th>
	  <th>Description</th>
	  <th>{{site.data.keyword.cloudaccesstrailshort}} events</th>
  </tr>
  <tr> 
    <td><a href="/docs/containers/container_index.html#container_index">Cluster management events</a></td>
	  <td>These events report on actions like cluster creation, deletion, or update.</td>
	  <td><a href="/docs/containers/cs_at_events.html#at_events">Cluster management events generated</a></td>
  </tr>
  <tr> 
    <td><a href="/docs/containers/container_index.html#container_index">Kubernetes API server audit events.</a></td>
	  <td>Kubernetes API server audit events provide chronological information about the sequence of activities that affect a cluster. Each action generates an event.</td>
	  <td><a href="/docs/containers/cs_at_events.html#at_events">Kubernetes API server audit events generated</a></td>
  </tr>
</table>


## Platform: Cloud Foundry applications
{: #platform_cfapps}

The events that are sent by Cloud Foundry applications to {{site.data.keyword.cloudaccesstrailshort}} are listed in the response area of the `GET /v2/events`, under the body section. The *Type* field lists all actions that generate an event. For more information, see [Events API](https://apidocs.cloudfoundry.org/270/events/list_all_events.html).


## Platform: Core integrated services
{: #platform_core_integrated}

Core platform services generate {{site.data.keyword.cloudaccesstrailshort}} events that you can view through the {{site.data.keyword.cloudaccesstrailshort}} **account domain**.

The following table lists core platform services that send events to {{site.data.keyword.cloudaccesstrailshort}}:

<table>
  <caption>List of core platform actions</caption>
  <tr>
    <th>Action</th>
	  <th>Description</th>
	  <th>{{site.data.keyword.cloudaccesstrailshort}} events</th>
  </tr>
  <tr> 
    <td><a href="/docs/overview/ui.html#catalogcreate">Provisioning and managing catalog services for resources that are managed by {{site.data.keyword.iamshort}} (IAM)</a></td>
	  <td>You can provision a service instance, rename a service instance, change the plan of a service instance, and remove a service instance. </td>
	  <td><a href="/docs/services/cloud-activity-tracker/services/at_events_rc.html#at_events">Events generated when interacting with Catalog services</a></td>
  </tr>
  <tr> 
    <td><a href="/docs/overview/ui.html#catalogcreate">Provisioning and managing catalog services that are bind to a Cloud Foundry space</a></td>
	  <td>You can provision a service instance, rename a service instance, change the plan of a service instance, and remove a service instance. </br>These events are generated for services that are provisioned in a CF space. </td>
	  <td><a href="/docs/services/cloud-activity-tracker/services/at_events_cf.html#catalog">Events generated when interacting with Catalog services</a></td>
  </tr>
  <tr> 
    <td><a href="/docs/account/index.html#accounts">Managing an account </a></td>
	  <td>You can sign up for an {{site.data.keyword.IBM_notm}} account by using an existing IBMid, creating a new IBMid, or using a federated ID.</td>
	  <td><a href="/docs/services/cloud-activity-tracker/services/at_events_acc_mgt.html#account">Events generated when you manage an account</a></td>
  </tr>
  <tr> 
    <td><a href="/docs/iam/iamusermanage.html#iamusermanage">Managing users </a></td>
	  <td>You can view and manage users across the account or organizations that you own or manage. </td>
	  <td><a href="/docs/services/cloud-activity-tracker/services/at_events_acc_mgt.html#users">Events generated when you manage users</a></td>
  </tr>
  <tr> 
    <td><a href="/docs/account/orgs_spaces.html#orgsspacesusers">Managing organizations </a></td>
	  <td>As an account owner, you can add and manage organizations to the account. </td>
	  <td><a href="/docs/services/cloud-activity-tracker/services/at_events_acc_mgt.html#org">Events generated when you manage organizations</a></td>
  </tr>
</table>



## Platform: Integrated developer services
{: #integrated_dev_svcs}

The following table lists Cloud services that you can use to develop apps and send events to {{site.data.keyword.cloudaccesstrailshort}}:

<table>
  <caption>List of Cloud services that you can use to develop apps and send events to {{site.data.keyword.cloudaccesstrailshort}}</caption>
  <tr>
    <th>Service</th>
	  <th>Description</th>
	  <th>{{site.data.keyword.cloudaccesstrailshort}} events</th>
  </tr>
  <tr>
    <td><a href="/docs/apps/index.html#create">{{site.data.keyword.dev_console}}</a></td>
	  <td>In {{site.data.keyword.Bluemix_notm}}, you can build enterprise-level mobile and web applications, and take advantage of cloud extensions that are hosted by {{site.data.keyword.Bluemix_notm}}. You can use the {{site.data.keyword.Bluemix_notm}} console and command line tools to build, run, and deploy your apps. You can use the {{site.data.keyword.dev_console}} to create an app by using a starter kit.</td>
	  <td><a href="/docs/apps/at_events_devx.html#at_events">Events generated by the {{site.data.keyword.dev_console}}</a></td>
  </tr>
</table>

## Platform: Integrated security services
{: #platform_integrated_security}

Integrated security services generate {{site.data.keyword.cloudaccesstrailshort}} events that you can view through the {{site.data.keyword.cloudaccesstrailshort}} **account domain**.


The following table lists core security platform services that send events to {{site.data.keyword.cloudaccesstrailshort}}:

<table>
  <caption>List of core security platform services</caption>
  <tr>
    <th>Action</th>
	  <th>Description</th>
	  <th>{{site.data.keyword.cloudaccesstrailshort}} events</th>
  </tr>
  <tr> 
    <td><a href="/docs/iam/quickstart.html#getstarted">Log in to the {{site.data.keyword.Bluemix_notm}}</a></td>
	  <td>You can log into the {{site.data.keyword.Bluemix_notm}} by using a password, an API key, an authorization code, or a passcode. As a federated user, you can log in from the command-line interface (CLI) by using either a one-time passcode or an API key. </td>
	  <td><a href="/docs/services/cloud-activity-tracker/services/at_events_iam.html#login">Events generated when a user or app logs in to the {{site.data.keyword.Bluemix_notm}}</a></td>
  </tr>
  <tr>
    <td><a href="/docs/iam/mngcf.html#mngcf">Managing account user's Cloud Foundry access</a></td>
	  <td>You can grant, revoke, and update Cloud Foundry (CF) permissions to users in the account.</td>
	  <td><a href="/docs/services/cloud-activity-tracker/services/at_events_cf.html#cfroles">Events generated when managing CF roles in the account</a></td>
  </tr>
  <tr>
    <td><a href="/docs/iam/users_roles.html#userroles">{{site.data.keyword.iamlong}} (IAM) </a></td>
  	<td>You can use IAM to manage users and roles across the the {{site.data.keyword.Bluemix_notm}} Platform and Infrastructure services. </td>
	  <td><a href="/docs/services/cloud-activity-tracker/services/at_events_iam.html#policies">Events generated when you manage IAM policies</a></td>
  </tr>
  <tr>
    <td><a href="/docs/iam/apikeys.html#platform-api-keys">Managing platform API keys</a></td>
	  <td>You can define platform API keys in the {{site.data.keyword.IBM_notm}} Cloud that are associated with a user or a service ID.</td>
	  <td><a href="/docs/services/cloud-activity-tracker/services/at_events_iam.html#apikeys">Events generated when managing Platform API keys</a></td>
  </tr>  
  <tr>
    <td><a href="/docs/iam/serviceid.html#serviceids">Managing service IDs</a></td>
	  <td>You can define service IDs at the account level in the {{site.data.keyword.IBM_notm}} Cloud.</td>
	  <td><a href="/docs/services/cloud-activity-tracker/services/at_events_iam.html#serviceids">Events generated when managing service IDs</a></td>
  </tr>
  <tr>
    <td><a href="/docs/iam/groups.html#groups">Managing access groups</a></td>
	  <td>You can define access groups to organize a set of users and service IDs into a single entity that makes it easy for you to assign permissions.</td>
	  <td><a href="/docs/services/cloud-activity-tracker/services/at_events_iam.html#access">Events generated when managing access groups</a></td>
  </tr>    
</table>


## Platform: Network services
{: #network}

The following table lists network Cloud services that send events to {{site.data.keyword.cloudaccesstrailshort}}:

<table>
  <caption>List of network Cloud services that send events to {{site.data.keyword.cloudaccesstrailshort}}</caption>
  <tr>
    <th>Service</th>
	  <th>Description</th>
	  <th>{{site.data.keyword.cloudaccesstrailshort}} events</th>
  </tr>
  <tr>
    <td><a href="/docs/infrastructure/cis/about.html#about-ibm-cloud-internet-services-cis-">IBM Cloud Internet Services (CIS)</a></td>
	  <td>IBM Cloud Internet Services (CIS) provides a fast, highly performant, reliable, and secure internet service.</td>
	  <td><a href="/docs/infrastructure/cis/at_events.html#at_events">Events generated by IBM Cloud Internet Services</a></td>
  </tr>
</table>



## Platform: Security services
{: #security}

The following table lists security Cloud services that send events to {{site.data.keyword.cloudaccesstrailshort}}:

<table>
  <caption>List of security Cloud services that send events to {{site.data.keyword.cloudaccesstrailshort}}</caption>
  <tr>
    <th>Service</th>
	  <th>Description</th>
	  <th>Monitoring cloud activity</th>
  </tr>
  <tr>
    <td><a href="/docs/services/cloud-activity-tracker/activity_tracker_ov.html#activity_tracker_ov">{{site.data.keyword.cloudaccesstraillong_notm}} </a></td>
	  <td>You can use the {{site.data.keyword.cloudaccesstrailshort}} service to monitor {{site.data.keyword.cloudaccesstraillong_notm}}. </td>
	  <td><a href="/docs/services/cloud-activity-tracker/reference/events.html#events">Events generated by the {{site.data.keyword.cloudaccesstraillong_notm}} service</a></td>
  </tr>
  <tr>
    <td><a href="/docs/services/appid/about.html#about">{{site.data.keyword.appid_full_notm}}</a></td>
	  <td>You can use {{site.data.keyword.appid_short}} to add authentication to your mobile and web apps, and to protect your back-end resources.</td>
	  <td></td>
  </tr>  
  <tr> 
    <td><a href="/docs/services/certificate-manager/about.html#about-certificate-manager">{{site.data.keyword.cloudcerts_full_notm}} </a></td>
	  <td>You can use {{site.data.keyword.cloudcerts_short}} to manage the SSL certificates for your {{site.data.keyword.Bluemix_notm}}-based apps and services. </td>
	  <td><a href="/docs/services/certificate-manager/at_events.html#at_events">Events generated by the {{site.data.keyword.cloudcerts_short}} service</a></td>
  </tr>
  <tr>
    <td><a href="/docs/services/keymgmt/index.html#getting-started-with-key-protect">{{site.data.keyword.keymanagementservicelong}}</a></td>
	  <td>You can use the {{site.data.keyword.keymanagementserviceshort}} service to provision encrypted keys for apps across the {{site.data.keyword.Bluemix_notm}}.</td>
	  <td></td>
  </tr>
</table>





## Platform: Storage services
{: #storage}

The following table lists storage Cloud services that send events to {{site.data.keyword.cloudaccesstrailshort}}:

<table>
  <caption>List of storage Cloud services that send events to {{site.data.keyword.cloudaccesstrailshort}}</caption>
  <tr>
    <th>Service</th>
	  <th>Description</th>
	  <th>{{site.data.keyword.cloudaccesstrailshort}} events</th>
  </tr>
  <tr>
    <td><a href="/docs/services/cloud-object-storage/about-cos.html#about-ibm-cloud-object-storage">{{site.data.keyword.cos_full_notm}}</a></td>
	  <td>You can use {{site.data.keyword.cos_full_notm}} to store data in the {{site.data.keyword.Bluemix_notm}}. Data is encrypted and dispersed across multiple geographic locations, and accessed over HTTP using a REST API.</td>
	  <td><a href="/docs/services/cloud-object-storage/basics/at.html#at_eventss">Events generated by {{site.data.keyword.cos_full_notm}}</a></td>
  </tr>
</table>


