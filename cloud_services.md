---

copyright:
  years: 2016, 2018
lastupdated: "2018-06-08"

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

**Note:** To get information about the regions where a service is available in the {{site.data.keyword.Bluemix_notm}}, see [Services by region](/docs/services/services_region.html#services_region).

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
	  <td></td>
  </tr>
  <tr> 
    <td><a href="/docs/containers/container_index.html#container_index">Kubernetes API server audit events.</a></td>
	  <td>Kubernetes API server audit events provide chronological information about the sequence of activities that affect a cluster. Each action generates an event.</td>
	  <td></td>
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
    <td><a href="/docs/overview/ui.html#catalogcreate">Provisioning, editing, and removing catalog services that are bind to a Cloud Foundry space.</a></td>
	  <td>You can provision services, rename a service, and remove a service. </br>These events are generated for services that are provisioned in a CF space. </td>
	  <td><a href="/docs/services/cloud-activity-tracker/services/platform.html#catalog">Events generated when interacting with Catalog services</a></td>
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
	  <td><a href="/docs/services/cloud-activity-tracker/services/security_svcs.html#login">Events generated when a user or app logs in to the {{site.data.keyword.Bluemix_notm}}</a></td>
  </tr>
  <tr>
    <td><a href="/docs/iam/mngcf.html#mngcf">Managing account user's Cloud Foundry access</a></td>
	  <td>You can grant, revoke, and update Cloud Foundry (CF) permissions to users in the account.</td>
	  <td><a href="/docs/services/cloud-activity-tracker/services/platform.html#cfroles">Events generated when managing CF roles in the account</a></td>
  </tr>
  <tr>
    <td><a href="/docs/iam/apikeys.html#platform-api-keys">Managing platform API keys</a></td>
	  <td>You can define platformn API keys at the account level in the {{site.data.keyword.IBM_notm}} Cloud.</td>
	  <td><a href="/docs/services/cloud-activity-tracker/services/security_svcs.html#platform_api_keys">Events generated when managing Platform API keys</a></td>
  </tr>  
  <tr>
    <td><a href="/docs/iam/serviceid.html#serviceids">Managing service IDs</a></td>
	  <td>You can define service IDs at the account level in the {{site.data.keyword.IBM_notm}} Cloud.</td>
	  <td><a href="/docs/services/cloud-activity-tracker/services/security_svcs.html#service_ids">Events generated when managing service IDs</a></td>
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
	  <td><a href="/docs/services/cloud-activity-tracker/services/at.html#at">Events generated by the {{site.data.keyword.cloudaccesstraillong_notm}} service</a></td>
  </tr>
  <tr>
    <td><a href="/docs/services/appid/about.html#about">{{site.data.keyword.appid_full_notm}}</a></td>
	  <td>You can use {{site.data.keyword.appid_short}} to add authentication to your mobile and web apps, and to protect your back-end resources.</td>
	  <td></td>
  </tr>  
  <tr> 
    <td><a href="/docs/services/certificate-manager/about.html#about-certificate-manager">{{site.data.keyword.cloudcerts_full_notm}} </a></td>
	  <td>You can use {{site.data.keyword.cloudcerts_short}} to manage the SSL certificates for your {{site.data.keyword.Bluemix_notm}}-based apps and services. </td>
	  <td><a href="/docs/services/cloud-activity-tracker/services/security_svcs.html#cert_mgr">Events generated by the {{site.data.keyword.cloudcerts_short}} service</a></td>
  </tr>
  <tr>
    <td><a href="/docs/iam/users_roles.html#userroles">{{site.data.keyword.iamlong}} (IAM) </a></td>
  	<td>You can use IAM to manage users and roles across the the {{site.data.keyword.Bluemix_notm}} Platform and Infrastructure services. </td>
	  <td><a href="/docs/services/cloud-activity-tracker/services/platform.html#cfroles">Events generated when you manage CF roles</a></td>
  </tr>
  <tr>
    <td><a href="/docs/services/keymgmt/index.html#getting-started-with-key-protect">{{site.data.keyword.keymanagementservicelong}}</a></td>
	  <td>You can use the {{site.data.keyword.keymanagementserviceshort}} service to provision encrypted keys for apps across the {{site.data.keyword.Bluemix_notm}}.</td>
	  <td><a href="/docs/services/cloud-activity-tracker/services/security_svcs.html#key_protect">Events generated by the {{site.data.keyword.keymanagementserviceshort}} service</a></td>
  </tr>
</table>







