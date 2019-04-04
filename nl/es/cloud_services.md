---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, cloud services

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



# Servicios en la nube
{: #cloud_services}

Utilice el servicio {{site.data.keyword.cloudaccesstraillong}} para supervisar las actividades iniciadas por el usuario que cambian el estado de alguno de los siguientes servicios en {{site.data.keyword.IBM_notm}} Cloud:
{:shortdesc}

**Nota:** Para obtener información sobre las regiones en las que hay disponible un servicio en {{site.data.keyword.cloud_notm}}, consulte [Servicios por región](/docs/resources?topic=resources-services_region#services_region).


## Servicios de infraestructura de cálculo
{: #infrastructure}

**Nota:** para que un usuario genere sucesos de {{site.data.keyword.BluVirtServers_short}} y de {{site.data.keyword.baremetal_short}} {{site.data.keyword.cloudaccesstrailshort}}, el usuario debe tener acceso a recursos de infraestructura en la consola de IBM Cloud. Para obtener más información, consulte [Supervisión de la actividad de {{site.data.keyword.BluVirtServers_short}} y de {{site.data.keyword.baremetal_short}} con {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/tutorials?topic=cloud-activity-tracker-vsi#vsi).

La tabla siguiente contiene los servicios de infraestructura que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}:

| Servicio     | Descripción | Sucesos de {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.BluVirtServers_short}} ](/docs/vsi?topic=virtual-servers-about-virtual-servers#about-virtual-servers)| Los {{site.data.keyword.BluVirtServers}} son servidores virtuales escalables que se adquieren con núcleos dedicados y asignaciones de memoria. Constituyen una opción ideal si necesita recursos de cálculo, que se pueden añadir en cuestión de minutos, con acceso a características como plantillas de imágenes.  | [Sucesos generados por {{site.data.keyword.BluVirtServers_short}}](/docs/vsi?topic=virtual-servers-at_events#at_events) |  
| [{{site.data.keyword.baremetal_long}} ](/docs/bare-metal?topic=bare-metal-about#about) | {{site.data.keyword.baremetal_short}} son servidores físicos de un solo arrendatario que le proporcionan rendimiento y control con acceso de bajo nivel a los recursos de hardware. | [Sucesos generados por {{site.data.keyword.baremetal_short}}](/docs/bare-metal?topic=bare-metal-at_events#at_events) | 
{: caption="Lista de los servicios de infraestructura que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 




## Servicios de cálculo sin servidor
{: #serverless}

La tabla siguiente contiene los servicios de cálculo sin servidor que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}:

| Servicio     | Descripción | Sucesos de {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.openwhisk_short}}](/docs/openwhisk?topic=cloud-functions-index#index) | {{site.data.keyword.openwhisk_short}} es una plataforma de programación políglota que funciona como un servicio (FaaS) basada en Apache OpenWhisk que puede utilizar para escribir `acciones llamadas por código` ligeras. | [Sucesos generados por {{site.data.keyword.openwhisk_short}}](/docs/openwhisk?topic=cloud-functions-activity_tracker#activity_tracker) |
{: caption="Lista de los servicios de cálculo sin servidor que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Servicios de contenedor de plataforma
{: #ikcs}

{{site.data.keyword.containershort_notm}} genera dos tipos de sucesos de {{site.data.keyword.cloudaccesstrailshort}}:

* **Sucesos de gestión de clúster**
    
    * Estos sucesos se generan de forma automática.
    * Estos sucesos se reenvían automáticamente a {{site.data.keyword.cloudaccesstrailshort}}.
    * Puede ver estos sucesos a través del **dominio de cuenta** de {{site.data.keyword.cloudaccesstrailshort}}. 

* **Sucesos de auditoría del servidor de API de Kubernetes**

    * Estos sucesos se generan de forma automática.
    * Debe configurar el clúster de modo que reenvíe estos sucesos al servicio {{site.data.keyword.cloudaccesstrailshort}}.
    * Puede configurar el clúster para que envíe los sucesos al **dominio de cuenta** de {{site.data.keyword.cloudaccesstrailshort}} o a un **dominio de espacio**. Para obtener más información, consulte [Envío de registros de auditoría](/docs/containers?topic=containers-health#api_forward).

La tabla siguiente contiene los servicios de la plataforma de contenedor que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}:

| Servicio     | Descripción | Sucesos de {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.containerlong_notm}}: sucesos de gestión de clúster](/docs/containers?topic=containers-container_index#container_index)| Estos sucesos informan sobre acciones como la creación, supresión o actualización de clústeres. | [Sucesos de gestión de clúster](/docs/containers?topic=containers-at_events#cluster-events) |  
| [{{site.data.keyword.containerlong_notm}}: sucesos de auditoría del servidor de API](/docs/containers?topic=containers-container_index#container_index)| Los sucesos de auditoría del servidor de API de Kubernetes proporcionan información cronológica sobre la secuencia de actividades que afectan a un clúster. Cada acción genera un suceso | [Sucesos de auditoría del servidor de API de Kubernetes](/docs/containers?topic=containers-at_events#kube-events) |
| [{{site.data.keyword.registrylong_notm}}](/docs/services/Registry?topic=registry-registry_overview#registry_overview) | Puede utilizar el servicio {{site.data.keyword.registrylong_notm}} para almacenar y acceder a imágenes de Docker privadas en una arquitectura muy disponible y escalable. | [Sucesos generados al interactuar con {{site.data.keyword.registrylong_notm}}](/docs/services/Registry?topic=registry-at_events#at_events) | 
{: caption="Sucesos de contenedor" caption-side="top"} 



## Aplicaciones de Cloud Foundry de la plataforma
{: #platform_cfapps}

Los sucesos que envían las aplicaciones de Cloud Foundry a {{site.data.keyword.cloudaccesstrailshort}} se muestran en el área de respuesta de `GET /v2/events`, en la sección del cuerpo. El campo *Type* contiene todas las acciones que generan un suceso. Para obtener más información, consulte [API de sucesos ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://apidocs.cloudfoundry.org/270/events/list_all_events.html){:new_window}.


## Servicios básicos integrados de la plataforma
{: #platform_core_integrated}

Los servicios básicos de la plataforma generan sucesos de {{site.data.keyword.cloudaccesstrailshort}} que puede ver a través del **dominio de cuenta** de {{site.data.keyword.cloudaccesstrailshort}}.

La tabla siguiente contiene los servicios básicos de la plataforma que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}:

| Servicio     | Descripción | Sucesos de {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [Suministro y gestión de servicios de catálogo para los recursos gestionados por {{site.data.keyword.iamshort}} (IAM)](/docs/overview?topic=overview-ui#catalogcreate) | Puede suministrar una instancia de servicio, cambiar el nombre de una instancia de servicio, cambiar el plan de una instancia de servicio y eliminar una instancia de servicio. | [Sucesos generados al interactuar con servicios de catálogo ](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_rc#at_events_rc) |  
| [Suministro y gestión de servicios de catálogo que están enlazados a un espacio de Cloud Foundry](/docs/overview?topic=overview-ui#catalogcreate)| Puede suministrar una instancia de servicio, cambiar el nombre de una instancia de servicio, cambiar el plan de una instancia de servicio y eliminar una instancia de servicio. </br>Estos sucesos se generan para los servicios que se suministran en un espacio de CF. | [Sucesos generados al interactuar con servicios de catálogo](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-cf#cf_catalog) |  
| [Gestión de una cuenta](/docs/account?topic=account-accounts#accounts) | Puede registrarse para una cuenta de {{site.data.keyword.IBM_notm}} utilizando un IBMid existente, creando un nuevo IBMid o utilizando un ID federado. | [Sucesos generados al gestionar una cuenta](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_acc_mgt#at_events_acc_mgt_account) |
| [Gestión de usuarios](/docs/iam?topic=iam-iamuserinv#iamusermanage) | Puede ver y gestionar usuarios de la cuenta o de las organizaciones que posee o gestiona.  | [Sucesos generados al gestionar usuarios ](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_acc_mgt#at_events_acc_mgt_users) |
| [Gestión de organizaciones](/docs/account?topic=account-orgsspacesusers#orgsspacesusers) | Como propietario de la cuenta, puede añadir y gestionar organizaciones de la cuenta. | [Sucesos generados al gestionar organizaciones ](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_acc_mgt#at_events_acc_mgt_org) |
{: caption="Lista de acciones básicas de la plataforma" caption-side="top"} 


## Servicios de base de datos de plataforma
{: #database}

La tabla siguiente contiene los servicios de base de datos que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}:

| Servicio     | Descripción | Sucesos de {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|----------------------------------------------------|
| [{{site.data.keyword.databases-for-postgresql_full_notm}}](/docs/services/databases-for-postgresql?topic=databases-for-postgresql-about#about) | {{site.data.keyword.databases-for-postgresql_full_notm}} es un servicio PostgreSQL gestionado alojado en {{site.data.keyword.cloud_notm}} e integrado con otros servicios de {{site.data.keyword.cloud_notm}}. | [Sucesos generados por {{site.data.keyword.databases-for-postgresql_full_notm}}](/docs/services/databases-for-postgresql?topic=databases-for-postgresql-activity-tracker#activity-tracker) |
| [{{site.data.keyword.databases-for-redis_full_notm}}](/docs/services/databases-for-redis?topic=databases-for-redis-about#about-databases-for-redis) | {{site.data.keyword.databases-for-redis_full_notm}} es un servicio Redis gestionado alojado en {{site.data.keyword.cloud_notm}} e integrado con otros servicios de {{site.data.keyword.cloud_notm}}.  | [Sucesos generados por {{site.data.keyword.databases-for-redis_full_notm}} ](/docs/services/databases-for-redis?topic=databases-for-redis-activity-tracker-integration#activity-tracker-integration) |
| [{{site.data.keyword.sqlquery_short}}](/docs/services/sql-query?topic=sql-query-overview#overview) | Puede utilizar el servicio {{site.data.keyword.sqlquery_short}} para ejecutar consultas SQL (es decir, sentencias SELECT) para analizar, transformar o limpiar datos rectangulares. | [Sucesos generados por {{site.data.keyword.sqlquery_short}}](/docs/services/sql-query?topic=sql-query-activitytracker#activity-tracker-events) |  
| [{{site.data.keyword.databases-for-etcd_full_notm}}](/docs/services/databases-for-etcd?topic=databases-for-etcd-about#about-databases-for-etcd) | {{site.data.keyword.databases-for-etcd_full_notm}} es un servicio etcd gestionado alojado en {{site.data.keyword.cloud_notm}} e integrado con otros servicios de {{site.data.keyword.cloud_notm}}. | [Sucesos generados por {{site.data.keyword.databases-for-etcd_full_notm}}](/docs/services/databases-for-etcd?topic=databases-for-etcd-activity-tracker#activity-tracker-integration) |
| [{{site.data.keyword.databases-for-elasticsearch_full_notm}}](/docs/services/databases-for-elasticsearch?topic=databases-for-elasticsearch-about#about-databases-for-elasticsearch) | {{site.data.keyword.databases-for-elasticsearch_full_notm}} es un servicio Elasticsearch gestionado alojado en {{site.data.keyword.cloud_notm}} e integrado con otros servicios de {{site.data.keyword.cloud_notm}}. | [Sucesos generados por {{site.data.keyword.databases-for-elasticsearch_full_notm}}](/docs/services/databases-for-elasticsearch?topic=databases-for-elasticsearch-activity-tracker#activity-tracker-integration) |
| [{{site.data.keyword.messages-for-rabbitmq_full_notm}}](/docs/services/messages-for-rabbitmq?topic=messages-for-rabbitmq-about#about-messages-for-rabbitmq)  | {{site.data.keyword.messages-for-rabbitmq_full_notm}} es un servicio RabbitMQ gestionado alojado en {{site.data.keyword.cloud_notm}} e integrado con otros servicios de {{site.data.keyword.cloud_notm}}.   | [Sucesos generados por {{site.data.keyword.messages-for-rabbitmq_full_notm}}](/docs/services/messages-for-rabbitmq?topic=messages-for-rabbitmq-activity-tracker#activity-tracker-integration) |
{: caption="Lista de los servicios de base de datos que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 




## Herramientas de desarrollador de la plataforma
{: #devops}

La tabla siguiente contiene los servicios de DevOps que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}:

| Servicio     | Descripción | Sucesos de {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.DRA_short}}](/docs/services/DevOpsInsights?topic=DevOpsInsights-insights_about#insights_about) | {{site.data.keyword.DRA_short}} es una integración en el catálogo de cadenas de herramientas abiertas de {{site.data.keyword.cloud_notm}}. | [Sucesos generados por {{site.data.keyword.DRA_short}}](/docs/services/DevOpsInsights?topic=DevOpsInsights-at_events#at_events) |
| [{{site.data.keyword.contdelivery_short}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-cd_overview#cd_overview) | Con {{site.data.keyword.contdelivery_short}} puede crear, probar y entregar aplicaciones mediante las herramientas más utilizadas de la industria y prácticas de DevOps. | [Sucesos generados por {{site.data.keyword.contdelivery_short}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-at_events#at_events) |
| [{{site.data.keyword.GlobalizationPipeline_short}}](/docs/services/GlobalizationPipeline?topic=GlobalizationPipeline-globalizationpipeline#globalizationpipeline) | Permite que los desarrolladores de apps puedan publicar de forma rápida aplicaciones traducidas para clientes globales. | [Sucesos generados por {{site.data.keyword.GlobalizationPipeline_short}}](/docs/services/GlobalizationPipeline?topic=GlobalizationPipeline-gpat_events#gpat_events)|
{: caption="Lista de herramientas de desarrollador que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Servicios de desarrollador integrados en la plataforma
{: #integrated_dev_svcs}

En la tabla siguiente se muestran los servicios de nube que puede utilizar para desarrollar apps y enviar sucesos a {{site.data.keyword.cloudaccesstrailshort}}:

| Servicio     | Descripción | Sucesos de {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.dev_console}}](/docs/apps?topic=creating-apps-tutorial-getting-started#create) | En {{site.data.keyword.cloud_notm}}, puede crear aplicaciones web y móviles a nivel de empresa y aprovechar las extensiones de nube alojadas en {{site.data.keyword.cloud_notm}}. Puede utilizar la consola de {{site.data.keyword.cloud_notm}} y las herramientas de línea de mandatos para crear, ejecutar y desplegar las apps. Puede utilizar la {{site.data.keyword.dev_console}} para crear una app utilizando un kit de inicio. | [Sucesos generados por {{site.data.keyword.dev_console}}](/docs/apps?topic=creating-apps-at_events#at_events) |
| [{{site.data.keyword.mobilepushshort}}](/docs/services/mobilepush?topic=mobile-pushnotification-overview-push#overview-push)| Puede utilizar el servicio {{site.data.keyword.mobilepushshort}} para enviar notificaciones a dispositivos móviles y navegadores. Las notificaciones se pueden destinar a todos los usuarios de la aplicación o a un conjunto específico de usuarios y dispositivos mediante etiquetas. Para cada mensaje que se envía al servicio, los usuarios de destino reciben una notificación. | [Sucesos generados por {{site.data.keyword.mobilepushshort}}](/docs/services/mobilepush?topic=mobile-pushnotification-push_activity_tracker#push_activity_tracker) |  
{: caption="Lista de los servicios de nube web y móviles que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Servicios de seguridad integrados en la plataforma
{: #platform_integrated_security}

Los servicios integrados de seguridad generan sucesos de {{site.data.keyword.cloudaccesstrailshort}} que puede ver a través del **dominio de cuenta** de {{site.data.keyword.cloudaccesstrailshort}}.


La tabla siguiente contiene los servicios básicos de la plataforma de seguridad que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}:

| Servicio     | Descripción | Sucesos de {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [Inicie una sesión en {{site.data.keyword.cloud_notm}}](/docs/iam?topic=iam-features#features)| Puede iniciar la sesión en {{site.data.keyword.cloud_notm}} utilizando una contraseña, una clave de API, un código de autorización o un código de acceso. Como usuario federado, puede iniciar la sesión desde la interfaz de línea de mandatos (CLI) utilizando un código de acceso de una sola vez o una clave de API. | [Sucesos generados cuando un usuario o app inicia una sesión en {{site.data.keyword.cloud_notm}}](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_login) |
| [Gestión del acceso a Cloud Foundry del usuario de la cuenta](/docs/iam?topic=iam-mngcf#mngcf) | Puede otorgar, revocar y actualizar los permisos de Cloud Foundry (CF) a los usuarios de la cuenta. | [Sucesos generados al gestionar roles de CF en la cuenta](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-cf#cf_cfroles) |
| [{{site.data.keyword.iamlong}} (IAM)](/docs/iam?topic=iam-userroles#userroles) | Puede utilizar IAM para gestionar usuarios y roles en la plataforma {{site.data.keyword.cloud_notm}} y servicios de infraestructura. | [Sucesos generados al gestionar políticas de IAM](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_policies) |
| [Gestión de claves de API de la plataforma](/docs/iam?topic=iam-manapikey#platform-api-keys) | Puede definir claves de API de la plataforma en el {{site.data.keyword.IBM_notm}} Cloud que están asociadas con un usuario o un ID de servicio. | [Sucesos generados al gestionar claves de API de la plataforma](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_apikeys) |
| [Gestión de los ID de servicio](/docs/iam?topic=iam-serviceids#serviceids) | Puede definir los ID de servicio a nivel de cuenta en {{site.data.keyword.IBM_notm}} Cloud. | [Sucesos generados al gestionar ID de servicio](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_serviceids) |
| [Gestión de grupos de acceso](/docs/iam?topic=iam-groups#groups) | Puede definir grupos de acceso para organizar un conjunto de usuarios y de ID de servicio en una sola entidad, lo que le facilita la asignación de permisos. | [Sucesos generados al gestionar grupos de acceso](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_access) |
{: caption="Lista de servicios básicos de seguridad de la plataforma" caption-side="top"} 


## Servicios de integración de la plataforma
{: #integration}

La tabla siguiente contiene los servicios de integración que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}:

| Servicio     | Descripción | Sucesos de {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.messagehub}}](/docs/services/EventStreams?topic=eventstreams-about#about)| {{site.data.keyword.messagehub}} es un bus de mensajes de alto rendimiento creado con Apache Kafka. Está optimizado para la ingesta de sucesos en {{site.data.keyword.IBM_notm}} y la distribución de secuencias de sucesos entre los servicios y las aplicaciones. | [Sucesos generados por {{site.data.keyword.messagehub}}](/docs/services/EventStreams?topic=eventstreams-at_events#at_events) |  
{: caption="Lista de los servicios de nube de integración que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Servicios de red de la plataforma
{: #network}

La tabla siguiente contiene los servicios de nube de red que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}:

| Servicio     | Descripción | Sucesos de {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [IBM Cloud Internet Services (CIS)](/docs/infrastructure/cis?topic=cis-about-ibm-cloud-internet-services-cis-#about-ibm-cloud-internet-services-cis-)| IBM Cloud Internet Services (CIS) proporciona un servicio de internet rápido, de alto rendimiento, fiable y seguro. | [Sucesos generados por IBM Cloud Internet Services](/docs/infrastructure/cis?topic=cis-at_events#at_events) |  
{: caption="Lista de los servicios de nube de red que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Servicios de seguridad de la plataforma
{: #security}

La tabla siguiente contiene los servicios de nube de seguridad que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}:


| Servicio     | Descripción | Sucesos de {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.cloudaccesstraillong_notm}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov)| Puede utilizar el servicio {{site.data.keyword.cloudaccesstrailshort}} para supervisar {{site.data.keyword.cloudaccesstraillong_notm}}. | [Sucesos generados por el servicio {{site.data.keyword.cloudaccesstraillong_notm}}](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-downloading_events#events) |  
| [{{site.data.keyword.appid_full_notm}}](/docs/services/appid?topic=appid-about#about) | Puede utilizar {{site.data.keyword.appid_short}} para añadir autenticación a sus apps móviles y web y para proteger los recursos de fondo. | [Sucesos generados por el servicio {{site.data.keyword.appid_short}}](/docs/services/appid?topic=appid-at-events#at-events) |
| [{{site.data.keyword.cloudcerts_full_notm}}](/docs/services/certificate-manager?topic=certificate-manager-about-certificate-manager#about-certificate-manager) | Puede utilizar {{site.data.keyword.cloudcerts_short}} para gestionar los certificados SSL para las apps y servicios basados en {{site.data.keyword.cloud_notm}}.  | [Sucesos generados por el servicio {{site.data.keyword.cloudcerts_short}}](/docs/services/certificate-manager?topic=certificate-manager-at_events#at_events) |
| [{{site.data.keyword.keymanagementservicelong}}](/docs/services/key-protect?topic=key-protect-getting-started-tutorial#getting-started-with-key-protect) | Puede utilizar el servicio {{site.data.keyword.keymanagementserviceshort}} para facilitar claves cifradas para apps en {{site.data.keyword.cloud_notm}}. | [Sucesos generados por el servicio {{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect?topic=key-protect-at-events#at-events) |
| [{{site.data.keyword.security-advisor_short}}](/docs/services/security-advisor?topic=security-advisor-about#about) | Puede utilizar {{site.data.keyword.security-advisor_short}} como ayuda para supervisar la seguridad de sus apps y cargas de trabajo de {{site.data.keyword.cloud_notm}}.   | [Sucesos generados por el servicio {{site.data.keyword.security-advisor_short}}](/docs/services/security-advisor?topic=security-advisor-at_events#at_events) |
{: caption="Lista de los servicios de nube de seguridad que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 


## Servicios de almacenamiento de la plataforma
{: #storage}

La tabla siguiente contiene los servicios de nube de almacenamiento envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}:

| Servicio     | Descripción | Sucesos de {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.cos_full_notm}}](/docs/services/cloud-object-storage?topic=cloud-object-storage-about-ibm-cloud-object-storage#about-ibm-cloud-object-storage)| Puede utilizar {{site.data.keyword.cos_full_notm}} para almacenar datos en {{site.data.keyword.cloud_notm}}. Los datos se cifran y se distribuyen entre varias ubicaciones geográficas y se accede a los mismos a través de HTTP utilizando una API REST.   | [Sucesos generados por {{site.data.keyword.cos_full_notm}}](/docs/services/cloud-object-storage/basics?topic=cloud-object-storage-at_events#at_events) |  
{: caption="Lista de los servicios de nube de almacenamiento que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Servicios de datos de la plataforma Watson
{: #watson_data}


| Servicio     | Descripción | Sucesos de {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [Watson Studio](https://dataplatform.cloud.ibm.com/docs/content/getting-started/overview-ws.html?context=analytics&linkInPage=true) | Watson Studio proporciona el entorno y las herramientas para resolver sus problemas empresariales trabajando de forma colaborativa con los datos. Puede elegir las herramientas que necesite para analizar y visualizar datos, limpiar y modelar datos, ingerir datos en streaming o crear, formar y desplegar modelos de aprendizaje automático. | [Sucesos generados por Watson Studio](https://dataplatform.cloud.ibm.com/docs/content/admin/at-events.html#ws) |  
| [Watson Machine Learning](https://dataplatform.cloud.ibm.com/docs/content/analyze-data/ml-overview.html?audience=dr&context=refinery)| Puede utilizar Watson Machine Learning para crear modelos analíticos sofisticados, entrenados con sus propios datos, que puede desplegar para utilizarlos en aplicaciones. | [Sucesos generados por Watson Machine Learning](https://dataplatform.cloud.ibm.com/docs/content/admin/at-events.html#wml) | 
| [Watson Knowledge Catalog](https://dataplatform.cloud.ibm.com/docs/content/catalog/overview-wkc.html?audience=dr&context=refinery&linkInPage=true)| Watson Knowledge Catalog proporciona una plataforma de gestión de catálogos de empresa segura que cuenta con el soporte de una infraestructura de políticas de datos. Un catálogo conecta datos y conocimientos con las personas que necesitan usarlos. La infraestructura de políticas de datos garantiza que el acceso a los datos cumple con las reglas de la empresa. | [Sucesos generados por Watson Knowledge Catalog](https://dataplatform.cloud.ibm.com/docs/content/admin/at-events.html#wkc) |  
{: caption="Lista de los servicios de datos de nube de Watson que envían sucesos a {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 

