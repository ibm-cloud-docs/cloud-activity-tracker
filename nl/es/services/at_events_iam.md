---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

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
{:deprecated: .deprecated}


# Sucesos de IAM
{: #at_events_iam}

Como agente de seguridad, auditor o gestor, puede utilizar el servicio {{site.data.keyword.cloudaccesstrailfull}} para realizar un seguimiento de cómo interactúan los usuarios y las aplicaciones con el servicio {{site.data.keyword.iamlong}} (IAM) en {{site.data.keyword.Bluemix}}. 
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} está en desuso. A partir del 9 de mayo de 2019, no se pueden suministrar nuevas instancias de {{site.data.keyword.cloudaccesstrailshort}}. Las instancias existentes del plan premium recibirán soporte hasta el 30 de septiembre de 2019. Para seguir supervisando la actividad de la cuenta de {{site.data.keyword.cloud_notm}} suministre una instancia de [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}

El servicio {{site.data.keyword.cloudaccesstrailfull_notm}} registra las actividades iniciadas por el usuario que cambian el estado de un servicio en {{site.data.keyword.cloud_notm}}. Para obtener más información, consulte [Acerca de {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov).

Para empezar a supervisar las acciones del usuario, consulte [{{site.data.keyword.cloudaccesstrailfull_notm}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started). 

Un iniciador puede ser un usuario, un servicio o una aplicación.
{: tip}

## Gestión de sucesos de grupos de acceso
{: #at_events_iam_access}

En la tabla siguiente se muestran las acciones que generan un suceso:

| Acción | Descripción |
|----------|---------|
| `iam-groups.group.create`   | Se genera un suceso cuando un iniciador crea un grupo de acceso. | 
| `iam-groups.group.read`     | Se genera un suceso cuando un iniciador consulta información relacionada con grupos de acceso. |
| `iam-groups.group.update`   | Se genera un suceso cuando un iniciador actualiza un nombre de grupo o una descripción. |
| `iam-groups.group.delete`   | Se genera un suceso cuando un iniciador suprime un grupo de acceso. |
| `iam-groups.member.add`     | Se genera un suceso cuando un iniciador añade un miembro a un grupo de acceso. |
| `iam-groups.member.delete`  | Se genera un suceso cuando un iniciador elimina miembro de un grupo de acceso. |
| `iam-groups.member.read`    | Se genera un suceso cuando un iniciador comprueba la pertenencia de un miembro. |
| `iam-groups.rule.read`      | Se genera un suceso cuando un iniciador visualiza una regla en un grupo de acceso. |
| `iam-groups.rule.create`    | Se genera un suceso cuando un iniciador añade una regla a un grupo de acceso. |
| `iam-groups.rule.update`    | Se genera un suceso cuando un iniciador modifica el nombre de una regla. |
| `iam-groups.rule.delete`    | Se genera un suceso cuando un iniciador suprime una regla de un grupo de acceso. |
{: caption="Tabla 1. Acciones de gestión de grupos de acceso" caption-side="top"} 



## Cómo trabajar con sucesos de ID de servicio
{: #at_events_iam_serviceids}

En la tabla siguiente se muestran las acciones que generan un suceso:

| Acción | Descripción |
|----------|---------|
| `iam-identity.account-serviceid.create` | Se genera un suceso cuando un iniciador crea un ID de servicio.  | 
| `iam-identity.account-serviceid.update` | Se genera un suceso cuando un iniciador cambia el nombre de un ID de servicio o modifica su descripción. | 
| `iam-identity.account-serviceid.delete` | Se genera un suceso cuando un iniciador suprime un ID de servicio. | 
{: caption="Tabla 2. Acciones de cómo trabajar con ID de servicio" caption-side="top"} 


## Cómo trabajar con sucesos de claves de API
{: #at_events_iam_apikeys}

En la tabla siguiente se muestran las acciones que generan un suceso:

| Acción | Descripción |
|----------|---------|
| `iam-identity.user-apikey.create`      | Se genera un suceso cuando un iniciador crea una clave de API. | 
| `iam-identity.user-apikey.update`      | Se genera un suceso cuando un iniciador cambia el nombre de una API o modifica su descripción. |  
| `iam-identity.user-apikey.delete`      | Se genera un suceso cuando un iniciador suprime una clave de API. |  
| `iam-identity.serviceid-apikey.create` | Se genera un suceso cuando un iniciador crea una clave de API para un ID de servicio. |  
| `iam-identity.serviceid-apikey.delete` | Se genera un suceso cuando un iniciador suprime una clave de API para un ID de servicio. |  
{: caption="Tabla 3. Acciones de cómo trabajar con claves de API" caption-side="top"} 


## Sucesos de inicio de sesión
{: #at_events_iam_login}

En la tabla siguiente se muestran las acciones que generan un suceso:

| Acción | Descripción |
|----------|---------|
| `iam-identity.user-apikey.login`         | Se genera un suceso cuando un usuario inicia una sesión en {{site.data.keyword.cloud_notm}} utilizando una clave de API. |  
| `iam-identity.serviceid-apikey.login`    | Se genera un suceso cuando un iniciador inicia una sesión en {{site.data.keyword.cloud_notm}} utilizando una clave de API asociada con un ID de servicio. |  
| `iam-identity.user-identitycookie.login` | Este es un suceso que se genera cuando un iniciador solicita una nueva cookie de identidad para ejecutar una acción. |
| `iam-identity.user-refreshtoken.login`   | Este es un suceso que se genera cuando el iniciador inicia una sesión en IBM Cloud, o cuando un iniciador que ya ha iniciado una sesión en IBM Cloud solicita una nueva señal de renovación para ejecutar una acción. |
{: caption="Tabla 4. Acciones de inicio de sesión de usuario" caption-side="top"} 


## Gestión de sucesos de políticas
{: #at_events_iam_policies}

En la tabla siguiente se muestran las acciones que generan un suceso:

| Acción | Descripción |
|----------|---------|
| `iam-am.policy.create` | Se genera un suceso cuando un iniciador añade una política a un usuario o grupo de acceso. |
| `iam-am.policy.delete` | Se genera un suceso cuando un iniciador modifica los permisos sobre una política de un usuario o grupo de acceso.|
| `iam-am.policy.update` | Se genera un suceso cuando un iniciador suprime una política asignada a un usuario o grupo de acceso. |
{: caption="Tabla 5. Acciones de gestión de políticas" caption-side="top"} 


## Visualización de sucesos
{: #at_events_iam_ui}

Los sucesos de {{site.data.keyword.cloudaccesstrailshort}} están disponibles en el **dominio de cuenta** de la región **EE. UU. sur**.

Para ver estos sucesos, debe suministrar una instancia del servicio {{site.data.keyword.cloudaccesstrailshort}} en la región **EE. UU. sur**. A continuación, debe abrir la interfaz de usuario de {{site.data.keyword.cloudaccesstrailshort}} y cambiar al dominio de cuenta para ver los sucesos. 

Para obtener más información, consulte [Visualización de sucesos de cuenta](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-view_acc_events#view_acc_events_account_events).



