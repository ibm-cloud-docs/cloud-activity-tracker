---

copyright:
  years: 2016, 2019
lastupdated: "2019-02-18"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}



# Servicios en la nube
{: #cloud_services}

Utilice el servicio {{site.data.keyword.cloudaccesstraillong}} para supervisar las actividades iniciadas por el usuario que cambian el estado de alguno de los siguientes servicios en {{site.data.keyword.IBM_notm}} Cloud:
{:shortdesc}

**Nota:** Para obtener información sobre las regiones en las que hay disponible un servicio en {{site.data.keyword.cloud_notm}}, consulte [Servicios por región](/docs/resources/services_region.html#services_region).


## Cálculo: Servicios de infraestructura
{: #infrastructure}

**Nota:** para que un usuario genere sucesos de {{site.data.keyword.BluVirtServers_short}} y de {{site.data.keyword.baremetal_short}} {{site.data.keyword.cloudaccesstrailshort}}, el usuario debe tener acceso a recursos de infraestructura en la consola de IBM Cloud. Para obtener más información, consulte [Supervisión de la actividad de {{site.data.keyword.BluVirtServers_short}} y de {{site.data.keyword.baremetal_short}} con {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/tutorials/vsi.html#vsi).

La tabla siguiente contiene los servicios de infraestructura que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}:

| Servicio     | Descripción | Sucesos de {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.BluVirtServers_short}} ](/docs/vsi/vsi_about.html#about-virtual-servers)| Los {{site.data.keyword.BluVirtServers}} son servidores virtuales escalables que se adquieren con núcleos dedicados y asignaciones de memoria. Constituyen una opción ideal si necesita recursos de cálculo, que se pueden añadir en cuestión de minutos, con acceso a características como plantillas de imágenes.  | [Sucesos generados por {{site.data.keyword.BluVirtServers_short}}](/docs/vsi/vsi_activity_tracker_events.html#at_events) |  
| [{{site.data.keyword.baremetal_long}} ](/docs/bare-metal/about.html#about) | {{site.data.keyword.baremetal_short}} son servidores físicos de un solo arrendatario que le proporcionan rendimiento y control con acceso de bajo nivel a los recursos de hardware. | [Sucesos generados por {{site.data.keyword.baremetal_short}}](/docs/bare-metal/bm-activity-tracker-events.html#at_events) | 
{: caption="Lista de los servicios de infraestructura que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 




## Cálculo: Servicios de cálculo sin servidor
{: #serverless}

La tabla siguiente contiene los servicios de cálculo sin servidor que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}:

| Servicio     | Descripción | Sucesos de {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.openwhisk_short}}](/docs/openwhisk/index.html#index) | {{site.data.keyword.openwhisk_short}} es una plataforma de programación políglota que funciona como un servicio (FaaS) basada en Apache OpenWhisk. {{site.data.keyword.openwhisk_short}} permite a los desarrolladores escribir acciones de llamada de código ligero que ejecutan de forma escalable la lógica de la app. | [Sucesos generados por {{site.data.keyword.openwhisk_short}}](/docs/openwhisk/at-events.html#activity_tracker) |
{: caption="Lista de los servicios de cálculo sin servidor que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 

## Plataforma: servicios de análisis
{: #analytics}

La tabla siguiente contiene los servicios de análisis que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}:

| Servicio     | Descripción | Sucesos de {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.streaminganalyticsfull}} ](/docs/services/StreamingAnalytics/index.html#gettingstarted)| {{site.data.keyword.streaminganalyticsfull}} está basado en {{site.data.keyword.streamsshort}}, una plataforma analítica avanzada que se puede utilizar para introducir, analizar y correlacionar información a medida que llega desde distintos tipos de orígenes de datos en tiempo real. | [Sucesos generados por {{site.data.keyword.streaminganalyticsshort}} ]() |  
{: caption="Lista de los servicios de nube de análisis que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 


## Plataforma: servicios de contenedor
{: #ikcs}

{{site.data.keyword.containershort_notm}} genera dos tipos de sucesos de {{site.data.keyword.cloudaccesstrailshort}}:

* **Sucesos de gestión de clúster**: 
    
    * Estos sucesos se generan de forma automática.
    * Estos sucesos se reenvían automáticamente a {{site.data.keyword.cloudaccesstrailshort}}.
    * Puede ver estos sucesos a través del **dominio de cuenta** de {{site.data.keyword.cloudaccesstrailshort}}. 

* **Sucesos de auditoría del servidor de API de Kubernetes**: 

    * Estos sucesos se generan de forma automática.
    * Debe configurar el clúster de modo que reenvíe estos sucesos al servicio {{site.data.keyword.cloudaccesstrailshort}}.
    * Puede configurar el clúster para que envíe los sucesos al **dominio de cuenta** de {{site.data.keyword.cloudaccesstrailshort}} o a un **dominio de espacio**. Para obtener más información, consulte [Envío de registros de auditoría](/docs/containers/cs_health.html#api_forward).

La tabla siguiente contiene los servicios de la plataforma de contenedor que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}:

| Servicio     | Descripción | Sucesos de {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.containerlong_notm}}: sucesos de gestión de clúster](/docs/containers/container_index.html#container_index)| Estos sucesos informan sobre acciones como la creación, supresión o actualización de clústeres. | [Sucesos de gestión de clúster](/docs/containers/cs_at_events.html#cluster-events) |  
| [{{site.data.keyword.containerlong_notm}}: sucesos de auditoría del servidor de API](/docs/containers/container_index.html#container_index)| Los sucesos de auditoría del servidor de API de Kubernetes proporcionan información cronológica sobre la secuencia de actividades que afectan a un clúster. Cada acción genera un suceso | [Sucesos de auditoría del servidor de API](/docs/containers/cs_at_events.html#kube-events) |
| [{{site.data.keyword.registrylong_notm}}](/docs/services/Registry/registry_overview.html#registry_overview) | Puede utilizar el servicio {{site.data.keyword.registrylong_notm}} para almacenar y acceder a imágenes de Docker privadas en una arquitectura muy disponible y escalable. | [Sucesos generados cuando se interactúa con {{site.data.keyword.registrylong_notm}}](/docs/services/Registry/registry_at_events.html#at_events) | 
{: caption="Sucesos de contenedor" caption-side="top"} 



## Plataforma: aplicaciones de Cloud Foundry
{: #platform_cfapps}

Los sucesos que envían las aplicaciones de Cloud Foundry a {{site.data.keyword.cloudaccesstrailshort}} se muestran en el área de respuesta de `GET /v2/events`, en la sección del cuerpo. El campo *Type* contiene todas las acciones que generan un suceso. Para obtener más información, consulte [API de sucesos ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://apidocs.cloudfoundry.org/270/events/list_all_events.html){:new_window}.


## Plataforma: servicios básicos integrados
{: #platform_core_integrated}

Los servicios básicos de la plataforma generan sucesos de {{site.data.keyword.cloudaccesstrailshort}} que puede ver a través del **dominio de cuenta** de {{site.data.keyword.cloudaccesstrailshort}}.

La tabla siguiente contiene los servicios básicos de la plataforma que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}:

| Servicio     | Descripción | Sucesos de {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [Suministro y gestión de servicios de catálogo para los recursos gestionados por {{site.data.keyword.iamshort}} (IAM)](/docs/overview/ui.html#catalogcreate) | Puede suministrar una instancia de servicio, cambiar el nombre de una instancia de servicio, cambiar el plan de una instancia de servicio y eliminar una instancia de servicio. | [Sucesos generados cuando se interactúa con los servicios de catálogo](/docs/services/cloud-activity-tracker/services/at_events_rc.html#at_events_rc) |  
| [Suministro y gestión de servicios de catálogo que están enlazados a un espacio de Cloud Foundry](/docs/overview/ui.html#catalogcreate)| Puede suministrar una instancia de servicio, cambiar el nombre de una instancia de servicio, cambiar el plan de una instancia de servicio y eliminar una instancia de servicio. </br>Estos sucesos se generan para los servicios que se suministran en un espacio de CF. | [Sucesos generados cuando se interactúa con los servicios de catálogo](/docs/services/cloud-activity-tracker/services/at_events_cf.html#cf_catalog) |  
| [Gestión de una cuenta](/docs/account/index.html#accounts) | Puede registrarse para una cuenta de {{site.data.keyword.IBM_notm}} utilizando un IBMid existente, creando un nuevo IBMid o utilizando un ID federado. | [Sucesos generados cuando se gestiona una cuenta](/docs/services/cloud-activity-tracker/services/at_events_acc_mgt.html#at_events_acc_mgt_account) |
| [Gestión de usuarios](/docs/iam/iamusermanage.html#iamusermanage) | Puede ver y gestionar usuarios de la cuenta o de las organizaciones que posee o gestiona.  | [Sucesos generados cuando se gestionan usuarios](/docs/services/cloud-activity-tracker/services/at_events_acc_mgt.html#at_events_acc_mgt_users) |
| [Gestión de organizaciones](/docs/account/orgs_spaces.html#orgsspacesusers) | Como propietario de la cuenta, puede añadir y gestionar organizaciones de la cuenta. | [Sucesos generados cuando se gestionan organizaciones](/docs/services/cloud-activity-tracker/services/at_events_acc_mgt.html#at_events_acc_mgt_org) |
{: caption="Lista de acciones básicas de la plataforma" caption-side="top"} 


## Plataforma: servicios de base de datos
{: #database}

La tabla siguiente contiene los servicios de base de datos que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}:

| Servicio     | Descripción | Sucesos de {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.databases-for-postgresql_full_notm}}](/docs/services/databases-for-postgresql?topic=databases-for-postgresql-about#about) | {{site.data.keyword.databases-for-postgresql_full_notm}} es un servicio PostgreSQL gestionado alojado en {{site.data.keyword.cloud_notm}} e integrado con otros servicios de {{site.data.keyword.cloud_notm}}. | [Sucesos generados por {{site.data.keyword.databases-for-postgresql_full_notm}}](/docs/services/databases-for-postgresql?topic=databases-for-postgresql-activity-tracker#activity-tracker) |
| [{{site.data.keyword.databases-for-redis_full_notm}}](/docs/services/databases-for-redis/index.html#about-databases-for-redis) | {{site.data.keyword.databases-for-redis_full_notm}} es un servicio Redis gestionado alojado en {{site.data.keyword.cloud_notm}} e integrado con otros servicios de {{site.data.keyword.cloud_notm}}.  | [Sucesos generados por {{site.data.keyword.databases-for-redis_full_notm}} ](/docs/services/databases-for-redis/reference-activity-tracker.html#activity-tracker-integration) |
| [{{site.data.keyword.sqlquery_short}}](/docs/services/sql-query/sql-query.html#overview)| Puede utilizar el servicio {{site.data.keyword.sqlquery_short}} para ejecutar consultas SQL (es decir, sentencias SELECT) para analizar, transformar o limpiar datos rectangulares. | [Sucesos generados por {{site.data.keyword.sqlquery_short}} ](/docs/services/sql-query/activity.html#activity-tracker-events) |  
| [{{site.data.keyword.databases-for-etcd_full_notm}}](/docs/services/databases-for-etcd/index.html#about-databases-for-etcd) | {{site.data.keyword.databases-for-etcd_full_notm}} es un servicio etcd gestionado alojado en {{site.data.keyword.cloud_notm}} e integrado con otros servicios de {{site.data.keyword.cloud_notm}}. | [Sucesos generados por {{site.data.keyword.databases-for-etcd_full_notm}}](/docs/services/databases-for-etcd/reference-activity-tracker.html#activity-tracker-integration) |
| [{{site.data.keyword.databases-for-elasticsearch_full_notm}}](/docs/services/databases-for-elasticsearch/index.html#about-databases-for-elasticsearch) | {{site.data.keyword.databases-for-elasticsearch_full_notm}} es un servicio Elasticsearch gestionado alojado en {{site.data.keyword.cloud_notm}} e integrado con otros servicios de {{site.data.keyword.cloud_notm}}. | [Sucesos generados por [{{site.data.keyword.databases-for-elasticsearch_full_notm}}](/docs/services/databases-for-elasticsearch/reference-activity-tracker.html#activity-tracker-integration) |
| [{{site.data.keyword.messages-for-rabbitmq_full_notm}}](/docs/services/messages-for-rabbitmq/index.html#about-messages-for-rabbitmq)  | {{site.data.keyword.messages-for-rabbitmq_full_notm}} es un servicio RabbitMQ gestionado alojado en {{site.data.keyword.cloud_notm}} e integrado con otros servicios de {{site.data.keyword.cloud_notm}}.   | [Sucesos generados por [{{site.data.keyword.messages-for-rabbitmq_full_notm}](/docs/services/messages-for-rabbitmq/reference-activity-tracker.html#activity-tracker-integration) |
{: caption="Lista de servicios de nube de base de datos que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 

## Plataforma: Herramientas del desarrollador
{: #devops}

La tabla siguiente contiene los servicios DevOps que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}:

| Servicio    | Descripción | Sucesos de {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.DRA_short}}](/docs/services/DevOpsInsights/insights_about.html#insights_about) | {{site.data.keyword.DRA_short}} es una integración en el catálogo de cadena de herramientas abiertas de {{site.data.keyword.cloud_notm}}. | [Sucesos generados por {{site.data.keyword.DRA_short}}](/docs/services/DevOpsInsights/at-events.html#at_events) |
| [{{site.data.keyword.contdelivery_short}}](/docs/services/ContinuousDelivery/cd_overview.html#cd_overview) | Con {{site.data.keyword.contdelivery_short}} puede crear, probar y distribuir aplicaciones mediante el uso de prácticas de DevOps y herramientas líderes del sector. | [Sucesos generados por {{site.data.keyword.contdelivery_short}}](/docs/services/ContinuousDelivery/at-events.html#at_events) |
{: caption="Lista de herramientas del desarrollador que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Plataforma: Servicios integrados del desarrollador
{: #integrated_dev_svcs}

En la tabla siguiente se muestran los servicios de nube que puede utilizar para desarrollar apps y enviar sucesos {{site.data.keyword.cloudaccesstrailshort}}:

| Servicio    | Descripción | Sucesos de {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.dev_console}}](/docs/apps/index.html#create) | En {{site.data.keyword.cloud_notm}}, puede crear aplicaciones web y móviles a nivel de empresa y aprovechar las extensiones de nube alojadas en {{site.data.keyword.cloud_notm}}. Puede utilizar la consola de {{site.data.keyword.cloud_notm}} y las herramientas de línea de mandatos para crear, ejecutar y desplegar las apps. Puede utilizar la {{site.data.keyword.dev_console}} para crear una app utilizando un kit de inicio. | [Sucesos generados por {{site.data.keyword.dev_console}}](/docs/apps/at_events_devx.html#at_events) |
| [{{site.data.keyword.mobilepushshort}}](/docs/services/mobilepush/c_overview_push.html#overview-push)| Puede utilizar el servicio {{site.data.keyword.mobilepushshort}} para enviar notificaciones a dispositivos móviles y navegadores. Las notificaciones se pueden destinar a todos los usuarios de la aplicación o a un conjunto específico de usuarios y dispositivos mediante etiquetas. Para cada mensaje que se envía al servicio, los usuarios de destino reciben una notificación. | [Sucesos generados por {{site.data.keyword.mobilepushshort}}](/docs/services/mobilepush/push_activity_tracker.html#push_activity_tracker) |  
{: caption="Lista de servicios de nube web y móviles que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Plataforma: Servicios de seguridad integrada
{: #platform_integrated_security}

Los servicios integrados de seguridad generan sucesos de {{site.data.keyword.cloudaccesstrailshort}} que puede ver a través del **dominio de cuenta** de {{site.data.keyword.cloudaccesstrailshort}}.


La tabla siguiente contiene los servicios principales de la plataforma de seguridad que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}:

| Servicio    | Descripción | Sucesos de {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [Inicie una sesión en {{site.data.keyword.cloud_notm}}](/docs/iam/quickstart.html#getstarted)| Puede iniciar la sesión en {{site.data.keyword.cloud_notm}} utilizando una contraseña, una clave de API, un código de autorización o un código de acceso. Como usuario federado, puede iniciar la sesión desde la interfaz de línea de mandatos (CLI) utilizando un código de acceso de una sola vez o una clave de API. | [Sucesos generados cuando un usuario o una app inicia una sesión en {{site.data.keyword.cloud_notm}}](/docs/services/cloud-activity-tracker/services/at_events_iam.html#at_events_iam_login) |
| [Gestión del acceso a Cloud Foundry del usuario de la cuenta](/docs/iam/mngcf.html#mngcf) | Puede otorgar, revocar y actualizar permisos de Cloud Foundry (CF) a usuarios de la cuenta. | [Sucesos generados al gestionar roles de CD en la cuenta](/docs/services/cloud-activity-tracker/services/at_events_cf.html#cf_cfroles) |
| [{{site.data.keyword.iamlong}} (IAM)](/docs/iam/users_roles.html#userroles) | Puede utilizar IAM para gestionar usuarios y roles en la plataforma {{site.data.keyword.cloud_notm}} y servicios de infraestructura. | [Sucesos generados cuando se gestionan políticas de IAM](/docs/services/cloud-activity-tracker/services/at_events_iam.html#at_events_iam_policies) |
| [Gestión de claves de API de la plataforma](/docs/iam/apikeys.html#platform-api-keys) | Puede definir claves de API de la plataforma en el {{site.data.keyword.IBM_notm}} Cloud que están asociadas con un usuario o un ID de servicio. | [Sucesos generados cuando se gestionan claves de API de la plataforma](/docs/services/cloud-activity-tracker/services/at_events_iam.html#at_events_iam_apikeys) |
| [Gestión de ID de servicio](/docs/iam/serviceid.html#serviceids) | Puede definir los ID de servicio a nivel de cuenta en {{site.data.keyword.IBM_notm}} Cloud. | [Sucesos generados cuando se gestionan ID de servicio](/docs/services/cloud-activity-tracker/services/at_events_iam.html#at_events_iam_serviceids) |
| [Gestión de grupos de acceso](/docs/iam/groups.html#groups) | Puede definir grupos de acceso para organizar un conjunto de usuarios y de ID de servicio en una sola entidad, lo que le facilita la asignación de permisos. | [Sucesos generados cuando se gestionan grupos de acceso](/docs/services/cloud-activity-tracker/services/at_events_iam.html#at_events_iam_access) |
{: caption="Lista de servicios principales de la plataforma de seguridad" caption-side="top"}


## Plataforma: Servicios de integración
{: #integration}

La tabla siguiente contiene los servicios de integración que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}:

| Servicio    | Descripción | Sucesos de {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.messagehub}}](/docs/services/MessageHub/messagehub010.html#about)| {{site.data.keyword.messagehub}} es un bus de mensajes de alto rendimiento creado con Apache Kafka. Está optimizado para la ingesta de sucesos en {{site.data.keyword.IBM_notm}} y la distribución de secuencias de sucesos entre los servicios y las aplicaciones. | [Sucesos generados por {{site.data.keyword.messagehub}} ](/docs/services/MessageHub/at-events.html#at_events) |  
{: caption="Lista de servicios de nube de integración que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Plataforma: Servicios de red
{: #network}

La tabla siguiente contiene los servicios de nube de red que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}:

| Servicio    | Descripción | Sucesos de {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [IBM Cloud Internet Services (CIS)](/docs/infrastructure/cis/about.html#about-ibm-cloud-internet-services-cis-)| IBM Cloud Internet Services (CIS) proporciona un servicio de Internet rápido, de alto rendimiento, fiable y seguro. | [Sucesos generados por IBM Cloud Internet Services](/docs/infrastructure/cis/at_events.html#at_events) |  
{: caption="Lista de servicios de nube de red que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Plataforma: Servicios de seguridad
{: #security}

La tabla siguiente contiene los servicios de nube de seguridad que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}:


| Servicio    | Descripción | Sucesos de {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.cloudaccesstraillong_notm}}](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#activity_tracker_ov)| Puede utilizar el servicio {{site.data.keyword.cloudaccesstrailshort}} para supervisar {{site.data.keyword.cloudaccesstraillong_notm}}. | [Sucesos generados por el servicio {{site.data.keyword.cloudaccesstraillong_notm}}](/docs/services/cloud-activity-tracker/reference/events.html#events) |  
| [{{site.data.keyword.appid_full_notm}}](/docs/services/appid/about.html#about) | Puede utilizar {{site.data.keyword.appid_short}} para añadir autenticación a sus apps móviles y web y para proteger los recursos de fondo. | [Sucesos generados por el servicio {{site.data.keyword.appid_short}}](/docs/services/appid/iam.html#tracking) |
| [{{site.data.keyword.cloudcerts_full_notm}}](/docs/services/certificate-manager/about.html#about-certificate-manager) | Puede utilizar {{site.data.keyword.cloudcerts_short}} para gestionar los certificados SSL para las apps y servicios basados en {{site.data.keyword.cloud_notm}}.  | [Sucesos generados por el servicio {{site.data.keyword.cloudcerts_short}}](/docs/services/certificate-manager/at_events.html#at_events) |
| [{{site.data.keyword.keymanagementservicelong}}](/docs/services/key-protect/index.html#getting-started-with-key-protect) | Puede utilizar {{site.data.keyword.keymanagementserviceshort}} para facilitar claves cifradas para apps en {{site.data.keyword.cloud_notm}}. | [Sucesos generados por el servicio {{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect/at-events.html#at-events) |
| [{{site.data.keyword.security-advisor_short}}](/docs/services/security-advisor/about.html#about) | Puede utilizar {{site.data.keyword.security-advisor_short}} como ayuda para supervisar la seguridad de sus apps y cargas de trabajo de {{site.data.keyword.cloud_notm}}.   | [Sucesos generados por el servicio {{site.data.keyword.security-advisor_short}}](/docs/services/security-advisor/at-events.html#at_events) |
{: caption="Lista de servicios de nube de seguridad que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 


## Plataforma: Servicios de almacenamiento
{: #storage}

La tabla siguiente contiene los servicios de nube de almacenamiento que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}:

| Servicio    | Descripción | Sucesos de {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.cos_full_notm}}](/docs/services/cloud-object-storage/about-cos.html#about-ibm-cloud-object-storage)| Puede utilizar {{site.data.keyword.cos_full_notm}} para almacenar datos en {{site.data.keyword.cloud_notm}}. Los datos se cifran y se distribuyen entre varias ubicaciones geográficas y se accede a los mismos a través de HTTP utilizando una API REST.   | [Sucesos generados por {{site.data.keyword.cos_full_notm}}](/docs/services/cloud-object-storage/basics/at.html#at_events) |  
{: caption="Lista de servicios de nube de almacenamiento que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Plataforma Watson: Servicios de datos
{: #watson_data}


| Servicio    | Descripción | Sucesos de {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [Watson Studio](https://dataplatform.cloud.ibm.com/docs/content/getting-started/overview-ws.html?context=analytics&linkInPage=true) | Watson Studio proporciona el entorno y las herramientas para resolver sus problemas empresariales trabajando de forma colaborativa con los datos. Puede elegir las herramientas que necesita para analizar y visualizar datos, para limpiar y modelar datos, para ingerir secuencias de datos o para crear, entrenar y desplegar modelos de Machine learning. | [Sucesos generados por Watson Studio](https://dataplatform.cloud.ibm.com/docs/content/admin/at-events.html#ws) |  
| [Watson Machine Learning](https://dataplatform.cloud.ibm.com/docs/content/analyze-data/ml-overview.html?audience=dr&context=refinery)| Puede utilizar Watson Machine Learning para crear modelos analíticos sofisticados, entrenados con sus propios datos, que puede desplegar para utilizarlos en aplicaciones. | [Sucesos generados por Watson Machine Learning](https://dataplatform.cloud.ibm.com/docs/content/admin/at-events.html#wml) | 
| [Watson Knowledge Catalog](https://dataplatform.cloud.ibm.com/docs/content/catalog/overview-wkc.html?audience=dr&context=refinery&linkInPage=true)| Watson Knowledge Catalog proporciona una plataforma de gestión de catálogos de empresa segura que cuenta con el soporte de una infraestructura de políticas de datos. Un catálogo conecta datos y conocimientos con las personas que necesitan usarlos. La infraestructura de políticas de datos garantiza que el acceso a los datos cumple con las reglas de la empresa. | [Sucesos generados por Watson Knowledge Catalog](https://dataplatform.cloud.ibm.com/docs/content/admin/at-events.html#wkc) |  
{: caption="Lista de los servicios de datos de nube de Watson que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 


