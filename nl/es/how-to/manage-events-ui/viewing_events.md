---

copyright:
  years: 2016, 2019
lastupdated: "2019-01-23"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}



# Visualización de sucesos
{: #view_acc_events}

Puede ver sucesos desde la interfaz de usuario de {{site.data.keyword.cloudaccesstrailshort}} en la consola de {{site.data.keyword.cloud_notm}} o mediante Kibana.
{:shortdesc}
   

## Visualización de sucesos de cuenta
{: #view_acc_events_account_events}

Puede ver los sucesos de un dominio de cuenta de {{site.data.keyword.cloudaccesstrailshort}} a través de la interfaz de usuario de {{site.data.keyword.cloudaccesstrailshort}} o a través de Kibana.

Un **propietario de cuenta** tiene permisos para ver los sucesos de un dominio de cuenta de {{site.data.keyword.cloudaccesstrailshort}} a través de la interfaz de usuario de {{site.data.keyword.cloudaccesstrailshort}} o a través de Kibana.

Como **miembro en una cuenta**, tenga en cuenta la información siguiente para ver los sucesos de la cuenta en una región:

* Debe tener el rol de *desarrollador* en el espacio en el que se suministra {{site.data.keyword.cloudaccesstrailshort}}. Para obtener más información, consulte [Concesión de un rol de CF](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_cf_role).

* Debe tener una política de IAM para el servicio {{site.data.keyword.loganalysisshort}} con el rol de *visor* en la región. El rol de visor es el rol de IAM mínimo necesario. Para obtener más información, consulte [Concesión de permisos de IAM](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_iam_policy).

* Puede ver los sucesos a través de Kibana. Para obtener más información sobre cómo iniciar Kibana, consulte [Navegación a Kibana desde un navegador web](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_kibana.html#launch_Kibana_from_browser).



## Visualización de sucesos de espacio
{: #view_acc_events_space_events}

Puede ver los sucesos de un dominio de espacio de {{site.data.keyword.cloudaccesstrailshort}} a través de la interfaz de usuario de {{site.data.keyword.cloudaccesstrailshort}}. Si tiene un plan premium, también puede ver los sucesos a través de Kibana.

Un **propietario de cuenta** tiene permisos para ver los sucesos de cualquier dominio de espacio de {{site.data.keyword.cloudaccesstrailshort}}.

Como **miembro de una cuenta**, debe tener el rol de *desarrollador* en el espacio en el que se suministra {{site.data.keyword.cloudaccesstrailshort}}.


