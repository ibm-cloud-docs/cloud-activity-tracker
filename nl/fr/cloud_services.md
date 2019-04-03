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



# Services Cloud
{: #cloud_services}

Utilisez le service {{site.data.keyword.cloudaccesstraillong}} pour surveiller les activités utilisateur qui modifient l'état de l'un des services suivants dans le Cloud {{site.data.keyword.IBM_notm}} :
{:shortdesc}

**Remarque :** Pour obtenir des informations sur les régions dans lesquelles un service est disponible dans {{site.data.keyword.cloud_notm}}, voir [Services par région](/docs/resources?topic=resources-services_region#services_region).


## Services d'infrastructure de calcul
{: #infrastructure}

**Remarque :** Pour pouvoir générer des événements {{site.data.keyword.cloudaccesstrailshort}} pour les serveurs {{site.data.keyword.BluVirtServers_short}} et {{site.data.keyword.baremetal_short}}, l'utilisateur doit avoir accès aux ressources d'infrastructure dans la console IBM Cloud. Pour plus d'informations, voir [Surveillance de l'activité des serveurs {{site.data.keyword.BluVirtServers_short}} et {{site.data.keyword.baremetal_short}} avec {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/tutorials?topic=cloud-activity-tracker-vsi#vsi).

Le tableau suivant répertorie les services d'infrastructure qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}} :

| Service     | Description | Evénements {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.BluVirtServers_short}} ](/docs/vsi?topic=virtual-servers-about-virtual-servers#about-virtual-servers)| Les serveurs {{site.data.keyword.BluVirtServers}} sont des serveurs virtuels évolutifs qui sont achetés avec des coeurs dédiés et des allocations de mémoire. Ils constituent un très bon choix si vous recherchez des ressources de calcul, qui peuvent être ajoutées en quelques minutes, avec un accès à des fonctions telles que des modèles d'image.  | [Evénements générés par {{site.data.keyword.BluVirtServers_short}}](/docs/vsi?topic=virtual-servers-at_events#at_events) |  
| [{{site.data.keyword.baremetal_long}} ](/docs/bare-metal?topic=bare-metal-about#about) | Les serveurs {{site.data.keyword.baremetal_short}} sont des serveurs physiques à service exclusif, offrant performance et contrôle avec un accès de bas niveau aux ressources matérielles. | [Evénements générés par {{site.data.keyword.baremetal_short}}](/docs/bare-metal?topic=bare-metal-at_events#at_events) | 
{: caption="Liste des services d'infrastructure qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 




## Services de calcul sans serveur
{: #serverless}

Le tableau suivant répertorie les services de calcul sans serveur qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}} :

| Service     | Description | Evénements {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.openwhisk_short}}](/docs/openwhisk?topic=cloud-functions-index#index) | {{site.data.keyword.openwhisk_short}} est une plateforme de programmation de type Functions-as-a-Service (FaaS) polyglotte basée sur Apache OpenWhisk, que vous pouvez utiliser pour écrire du code simple de type `code called actions`. | [Evénements générés par {{site.data.keyword.openwhisk_short}}](/docs/openwhisk?topic=cloud-functions-activity_tracker#activity_tracker) |
{: caption="Liste des services de calcul sans serveur qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Services de conteneur de plateforme
{: #ikcs}

{{site.data.keyword.containershort_notm}} génère deux types d'événements {{site.data.keyword.cloudaccesstrailshort}} :

* **Evénements de gestion de cluster**
    
    * Ces événements sont générés automatiquement.
    * Ces événements sont automatiquement transférés vers {{site.data.keyword.cloudaccesstrailshort}}.
    * Vous pouvez afficher ces événements via le **domaine de compte** {{site.data.keyword.cloudaccesstrailshort}}. 

* **Evénements d'audit du serveur d'API Kubernetes**

    * Ces événements sont générés automatiquement.
    * Vous devez configurer votre cluster pour le transfert de ces événements au service {{site.data.keyword.cloudaccesstrailshort}}.
    * Vous pouvez configurer votre cluster pour l'envoi d'événements au **domaine de compte** {{site.data.keyword.cloudaccesstrailshort}} ou à un **domaine d'espace**. Pour plus d'informations, voir [Envoi de journaux d'audit](/docs/containers?topic=containers-health#api_forward).

Le tableau suivant répertorie les services de plateforme de conteneur qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}} :

| Service     | Description | Evénements {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.containerlong_notm}} : événements de gestion de cluster](/docs/containers?topic=containers-container_index#container_index)| Ces événements traitent d'actions comme la création, la suppression ou la mise à jour de clusters. | [Evénements de gestion de cluster ](/docs/containers?topic=containers-at_events#cluster-events) |  
| [{{site.data.keyword.containerlong_notm}} : événements d'audit du serveur d'API](/docs/containers?topic=containers-container_index#container_index)| Les événements d'audit du serveur d'API Kubernetes fournissent des informations chronologiques sur la séquence des activités qui affectent un cluster. Chaque action génère un événement. | [Evénements d'audit du serveur d'API Kubernetes](/docs/containers?topic=containers-at_events#kube-events) |
| [{{site.data.keyword.registrylong_notm}}](/docs/services/Registry?topic=registry-registry_overview#registry_overview) | Vous pouvez utiliser le service {{site.data.keyword.registrylong_notm}} pour stocker des images Docker privées et y accéder dans une architecture hautement disponible et évolutive. | [Evénements générés lors de vos interactions avec {{site.data.keyword.registrylong_notm}}](/docs/services/Registry?topic=registry-at_events#at_events) | 
{: caption="Evénements de conteneur" caption-side="top"} 



## Applications Cloud Foundry de plateforme
{: #platform_cfapps}

Les événements qui sont envoyés par les applications Cloud Foundry à {{site.data.keyword.cloudaccesstrailshort}} sont répertoriés dans la zone de réponse de `GET /v2/events`, sous la section body. La zone *Type* répertorie toutes les actions qui génèrent un événement. Pour plus d'informations, voir [Events API ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://apidocs.cloudfoundry.org/270/events/list_all_events.html){:new_window}.


## Services de plateforme de base intégrés
{: #platform_core_integrated}

Les services de plateforme de base génèrent des événements {{site.data.keyword.cloudaccesstrailshort}} que vous pouvez afficher via le **domaine de compte** {{site.data.keyword.cloudaccesstrailshort}}.

Le tableau suivant répertorie les services de plateforme de base qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}} :

| Service     | Description | Evénements {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [Mise à disposition et gestion de services de catalogue pour les ressources gérées par {{site.data.keyword.iamshort}} (IAM)](/docs/overview?topic=overview-ui#catalogcreate) | Vous pouvez mettre à disposition une instance de service, la renommer, modifier son plan et la supprimer. | [Evénements générés lors de vos interactions avec les services de catalogue ](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_rc#at_events_rc) |  
| [Mise à disposition et gestion de services de catalogue liés à un espace Cloud Foundry](/docs/overview?topic=overview-ui#catalogcreate)| Vous pouvez mettre à disposition une instance de service, la renommer, modifier son plan et la supprimer. </br>Ces événements sont générés pour des services qui sont mis à disposition dans un espace CF. | [Evénements générés lors de vos interactions avec les services de catalogue](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-cf#cf_catalog) |  
| [Gestion d'un compte](/docs/account?topic=account-accounts#accounts) | Vous pouvez vous inscrire à un compte {{site.data.keyword.IBM_notm}} en utilisant un IBMid existant, en créant un nouvel IBMid ou en utilisant un ID fédéré. | [Evénements générés lorsque vous gérez un compte](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_acc_mgt#at_events_acc_mgt_account) |
| [Gestion des utilisateurs](/docs/iam?topic=iam-iamuserinv#iamusermanage) | Vous pouvez afficher et gérer des utilisateurs au niveau du compte ou des organisations que vous possédez ou gérez.  | [Evénements générés lorsque vous gérez des utilisateurs ](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_acc_mgt#at_events_acc_mgt_users) |
| [Gestion des organisations](/docs/account?topic=account-orgsspacesusers#orgsspacesusers) | En tant que propriétaire de compte, vous pouvez ajouter et gérer des organisations sur le compte. | [Evénements générés lorsque vous gérez des organisations ](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_acc_mgt#at_events_acc_mgt_org) |
{: caption="Liste des actions de plateforme de base" caption-side="top"} 


## Services de base de données de plateforme
{: #database}

Le tableau suivant répertorie les services de base de données qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}} :

| Service     | Description | Evénements {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|----------------------------------------------------|
| [{{site.data.keyword.databases-for-postgresql_full_notm}}](/docs/services/databases-for-postgresql?topic=databases-for-postgresql-about#about) | {{site.data.keyword.databases-for-postgresql_full_notm}} est un service PostgreSQL géré qui est hébergé dans {{site.data.keyword.cloud_notm}} et intégré à d'autres services {{site.data.keyword.cloud_notm}}. | [Evénements générés par {{site.data.keyword.databases-for-postgresql_full_notm}}](/docs/services/databases-for-postgresql?topic=databases-for-postgresql-activity-tracker#activity-tracker) |
| [{{site.data.keyword.databases-for-redis_full_notm}}](/docs/services/databases-for-redis?topic=databases-for-redis-about#about-databases-for-redis) | {{site.data.keyword.databases-for-redis_full_notm}} est un service Redis géré qui est hébergé dans {{site.data.keyword.cloud_notm}} et intégré à d'autres services {{site.data.keyword.cloud_notm}}.  | [Evénements générés par {{site.data.keyword.databases-for-redis_full_notm}} ](/docs/services/databases-for-redis?topic=databases-for-redis-activity-tracker-integration#activity-tracker-integration) |
| [{{site.data.keyword.sqlquery_short}}](/docs/services/sql-query?topic=sql-query-overview#overview) | Vous pouvez utiliser le service {{site.data.keyword.sqlquery_short}} pour exécuter des requêtes SQL (à savoir, des instructions SELECT) pour analyser, transformer ou nettoyer des données rectangulaires. | [Evénements générés par {{site.data.keyword.sqlquery_short}} ](/docs/services/sql-query?topic=sql-query-activitytracker#activity-tracker-events) |  
| [{{site.data.keyword.databases-for-etcd_full_notm}}](/docs/services/databases-for-etcd?topic=databases-for-etcd-about#about-databases-for-etcd) | {{site.data.keyword.databases-for-etcd_full_notm}} est un service etcd géré qui est hébergé dans {{site.data.keyword.cloud_notm}} et intégré à d'autres services {{site.data.keyword.cloud_notm}}. | [Evénements générés par {{site.data.keyword.databases-for-etcd_full_notm}}](/docs/services/databases-for-etcd?topic=databases-for-etcd-activity-tracker#activity-tracker-integration) |
| [{{site.data.keyword.databases-for-elasticsearch_full_notm}}](/docs/services/databases-for-elasticsearch?topic=databases-for-elasticsearch-about#about-databases-for-elasticsearch) | {{site.data.keyword.databases-for-elasticsearch_full_notm}} est un service Elasticsearch géré qui est hébergé dans {{site.data.keyword.cloud_notm}} et intégré à d'autres services {{site.data.keyword.cloud_notm}}. | [Evénements générés par {{site.data.keyword.databases-for-elasticsearch_full_notm}}](/docs/services/databases-for-elasticsearch?topic=databases-for-elasticsearch-activity-tracker#activity-tracker-integration) |
| [{{site.data.keyword.messages-for-rabbitmq_full_notm}}](/docs/services/messages-for-rabbitmq?topic=messages-for-rabbitmq-about#about-messages-for-rabbitmq)  | {{site.data.keyword.messages-for-rabbitmq_full_notm}} est un service RabbitMQ géré qui est hébergé dans {{site.data.keyword.cloud_notm}} et intégré à d'autres services {{site.data.keyword.cloud_notm}}.   | [Evénements générés par {{site.data.keyword.messages-for-rabbitmq_full_notm}}](/docs/services/messages-for-rabbitmq?topic=messages-for-rabbitmq-activity-tracker#activity-tracker-integration) |
{: caption="Liste des services de base de données qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 




## Outils de développement de plateforme
{: #devops}

Le tableau suivant répertorie les services DevOps qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}} :

| Service     | Description | Evénements {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.DRA_short}}](/docs/services/DevOpsInsights?topic=DevOpsInsights-insights_about#insights_about) | {{site.data.keyword.DRA_short}} est une intégration dans le catalogue de chaînes d'outils ouvertes {{site.data.keyword.cloud_notm}}. | [Evénements générés par {{site.data.keyword.DRA_short}}](/docs/services/DevOpsInsights?topic=DevOpsInsights-at_events#at_events) |
| [{{site.data.keyword.contdelivery_short}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-cd_overview#cd_overview) |Avec {{site.data.keyword.contdelivery_short}}, vous pouvez construire, tester et livrer des applications en suivant des pratiques DevOps et en utilisant des outils de pointe.| [Evénements générés par {{site.data.keyword.contdelivery_short}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-at_events#at_events) |
| [{{site.data.keyword.GlobalizationPipeline_short}}](/docs/services/GlobalizationPipeline?topic=GlobalizationPipeline-globalizationpipeline#globalizationpipeline) | Permet aux développeurs d'application de publier rapidement des applications traduites aux clients dans le monde entier. | [Evénements générés par {{site.data.keyword.GlobalizationPipeline_short}}](/docs/services/GlobalizationPipeline?topic=GlobalizationPipeline-gpat_events#gpat_events)|
{: caption="Liste des outils de développement qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Services de développement intégrés de plateforme
{: #integrated_dev_svcs}

Le tableau suivant répertorie les services Cloud que vous pouvez utiliser pour développer des applications et envoyer des événements à {{site.data.keyword.cloudaccesstrailshort}} :

| Service     | Description | Evénements {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.dev_console}}](/docs/apps?topic=creating-apps-tutorial-getting-started#create) | Dans {{site.data.keyword.cloud_notm}}, vous pouvez générer des applications mobiles et Web au niveau de l'entreprise, et tirer parti des extensions cloud hébergées par {{site.data.keyword.cloud_notm}}. Vous pouvez utiliser les outils de ligne de commande et la console {{site.data.keyword.cloud_notm}} pour générer, exécuter et déployer vos applications. Vous pouvez utiliser {{site.data.keyword.dev_console}} pour créer une application à l'aide d'un kit de démarrage. | [Evénements générés par {{site.data.keyword.dev_console}}](/docs/apps?topic=creating-apps-at_events#at_events) |
| [{{site.data.keyword.mobilepushshort}}](/docs/services/mobilepush?topic=mobile-pushnotification-overview-push#overview-push)| Vous pouvez utiliser le service {{site.data.keyword.mobilepushshort}} pour envoyer des notifications à des périphériques mobiles et des navigateurs. Les notifications peuvent être ciblées pour tous les utilisateurs d'application ou pour un ensemble spécifique d'utilisateurs et de périphériques à l'aide d'étiquettes. Le public visé reçoit une notification pour chaque message que vous soumettez au service. | [Evénements générés par {{site.data.keyword.mobilepushshort}}](/docs/services/mobilepush?topic=mobile-pushnotification-push_activity_tracker#push_activity_tracker) |  
{: caption="Liste des services de cloud mobile et Web qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Services de sécurité intégrés de plateforme
{: #platform_integrated_security}

Les services de sécurité intégrés génèrent des événements {{site.data.keyword.cloudaccesstrailshort}} que vous pouvez afficher via le **domaine de compte** {{site.data.keyword.cloudaccesstrailshort}}.


Le tableau suivant répertorie les services de plateforme de sécurité de base qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}} :

| Service     | Description | Evénements {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [Connexion à {{site.data.keyword.cloud_notm}}](/docs/iam?topic=iam-features#features)| Vous pouvez vous connecter à {{site.data.keyword.cloud_notm}} en utilisant un mot de passe, une clé d'API, un code d'autorisation ou un code d'accès. En tant qu'utilisateur fédéré, vous pouvez vous connecter à partir de l'interface de ligne de commande en utilisant un code d'accès à usage unique ou une clé d'API. | [Evénements générés lorsqu'un utilisateur ou une application se connecte à {{site.data.keyword.cloud_notm}}](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_login) |
| [Gestion de l'accès d'un utilisateur de compte à Cloud Foundry](/docs/iam?topic=iam-mngcf#mngcf) | Vous pouvez accorder, révoquer et mettre à jour les autorisations Cloud Foundry (CF) des utilisateurs dans le compte. | [Evénements générés lorsque vous gérez des rôles CF dans le compte](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-cf#cf_cfroles) |
| [{{site.data.keyword.iamlong}} (IAM)](/docs/iam?topic=iam-userroles#userroles) | Vous pouvez utiliser IAM pour gérer des utilisateurs et des rôles dans les services de plateforme et d'infrastructure {{site.data.keyword.cloud_notm}}. | [Evénements générés lorsque vous gérez des règles IAM](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_policies) |
| [Gestion des clés d'API de plateforme](/docs/iam?topic=iam-manapikey#platform-api-keys) | Vous pouvez définir des clés d'API de plateforme qui sont associées à un ID utilisateur ou de service dans {{site.data.keyword.IBM_notm}} Cloud. | [Evénements générés lorsque vous gérez des clés d'API de plateforme](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_apikeys) |
| [Gestion des ID de service](/docs/iam?topic=iam-serviceids#serviceids) | Vous pouvez définir des ID de service au niveau du compte dans {{site.data.keyword.IBM_notm}} Cloud. | [Evénements générés lorsque vous gérez des ID de service](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_serviceids) |
| [Gestion des groupes d'accès](/docs/iam?topic=iam-groups#groups) | Vous pouvez définir des groupes d'accès afin d'organiser un ensemble d'utilisateurs et d'ID de service dans une seule entité, et de faciliter l'affectation de droits d'accès. | [Evénements générés lorsque vous gérez des groupes d'accès](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_access) |
{: caption="Liste des services de plateforme de sécurité de base" caption-side="top"} 


## Services d'intégration de plateforme
{: #integration}

Le tableau suivant répertorie les services d'intégration qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}} :

| Service     | Description | Evénements {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.messagehub}}](/docs/services/EventStreams?topic=eventstreams-about#about)| {{site.data.keyword.messagehub}} est un bus de messages à haute capacité qui est généré avec Apache Kafka. Il est optimisé pour l'ingestion d'événements dans {{site.data.keyword.IBM_notm}} et la distribution de flux d'événements dans des services et des applications. | [Evénements générés par {{site.data.keyword.messagehub}} ](/docs/services/EventStreams?topic=eventstreams-at_events#at_events) |  
{: caption="Liste des services Cloud d'intégration qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Services de réseau de plateforme
{: #network}

Le tableau suivant répertorie les services Cloud de réseau qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}} :

| Service     | Description | Evénements {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [IBM Cloud Internet Services (CIS)](/docs/infrastructure/cis?topic=cis-about-ibm-cloud-internet-services-cis-#about-ibm-cloud-internet-services-cis-)| IBM Cloud Internet Services (CIS) fournit un service Internet rapide, très performant, fiable et sécurisé. | [Evénements générés par IBM Cloud Internet Services](/docs/infrastructure/cis?topic=cis-at_events#at_events) |  
{: caption="Liste des services Cloud de réseau qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Services de sécurité de plateforme
{: #security}

Le tableau suivant répertorie les services Cloud de sécurité qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}} :


| Service     | Description | Evénements {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.cloudaccesstraillong_notm}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov)| Vous pouvez utiliser le service {{site.data.keyword.cloudaccesstrailshort}} pour surveiller {{site.data.keyword.cloudaccesstraillong_notm}}. | [Evénements générés par le service {{site.data.keyword.cloudaccesstraillong_notm}}](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-downloading_events#events) |  
| [{{site.data.keyword.appid_full_notm}}](/docs/services/appid?topic=appid-about#about) | Vous pouvez utiliser {{site.data.keyword.appid_short}} pour ajouter l'authentification à vos applications mobiles et Web, et pour protéger vos ressources de back end. | [Evénements générés par le service {{site.data.keyword.appid_short}}](/docs/services/appid?topic=appid-at-events#at-events) |
| [{{site.data.keyword.cloudcerts_full_notm}}](/docs/services/certificate-manager?topic=certificate-manager-about-certificate-manager#about-certificate-manager) | Vous pouvez utiliser {{site.data.keyword.cloudcerts_short}} pour gérer les certificats SSL pour vos applications et services {{site.data.keyword.cloud_notm}}.  | [Evénements générés par le service {{site.data.keyword.cloudcerts_short}}](/docs/services/certificate-manager?topic=certificate-manager-at_events#at_events) |
| [{{site.data.keyword.keymanagementservicelong}}](/docs/services/key-protect?topic=key-protect-getting-started-tutorial#getting-started-with-key-protect) | Vous pouvez utiliser le service {{site.data.keyword.keymanagementserviceshort}} pour mettre à disposition des clés chiffrées pour des applications dans {{site.data.keyword.cloud_notm}}. | [Evénements générés par le service {{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect?topic=key-protect-at-events#at-events) |
| [{{site.data.keyword.security-advisor_short}}](/docs/services/security-advisor?topic=security-advisor-about#about) | Vous pouvez utiliser {{site.data.keyword.security-advisor_short}} pour vous aider à gérer la sécurité de vos applications et charges de travail {{site.data.keyword.cloud_notm}}.   | [Evénements générés par le service {{site.data.keyword.security-advisor_short}}](/docs/services/security-advisor?topic=security-advisor-at_events#at_events) |
{: caption="Liste des services Cloud de sécurité qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 


## Services de stockage de plateforme
{: #storage}

Le tableau suivant répertorie les services Cloud de stockage qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}} :

| Service     | Description | Evénements {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.cos_full_notm}}](/docs/services/cloud-object-storage?topic=cloud-object-storage-about-ibm-cloud-object-storage#about-ibm-cloud-object-storage)| Vous pouvez utiliser {{site.data.keyword.cos_full_notm}} pour stocker des données dans {{site.data.keyword.cloud_notm}}. Les données sont chiffrées et dispersées sur plusieurs emplacements géographiques, et sont accessibles via HTTP en utilisant une API REST.   | [Evénements générés par {{site.data.keyword.cos_full_notm}}](/docs/services/cloud-object-storage/basics?topic=cloud-object-storage-at_events#at_events) |  
{: caption="Liste des services Cloud de stockage qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Services de données de la plateforme Watson
{: #watson_data}


| Service     | Description | Evénements {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [Watson Studio](https://dataplatform.cloud.ibm.com/docs/content/getting-started/overview-ws.html?context=analytics&linkInPage=true) | Watson Studio fournit l'environnement et les outils qui permettent de résoudre vos problèmes métier en utilisant les données de façon collaborative. Vous pouvez choisir les outils dont vous avez besoin pour analyser et visualiser des données, nettoyer et modéliser des données, ingérer des flux de données en continu, ou pour créer, former et déployer des modèles d'apprentissage automatique. | [Evénements générés par Watson Studio](https://dataplatform.cloud.ibm.com/docs/content/admin/at-events.html#ws) |  
| [Watson Machine Learning](https://dataplatform.cloud.ibm.com/docs/content/analyze-data/ml-overview.html?audience=dr&context=refinery)| Vous pouvez utiliser Watson Machine Learning pour créer des modèles d'analyse sophistiqués, qui sont formés à partir de vos propres données et que vous pouvez déployer afin de les utiliser dans des applications. | [Evénements générés par Watson Machine Learning](https://dataplatform.cloud.ibm.com/docs/content/admin/at-events.html#wml) | 
| [Watson Knowledge Catalog](https://dataplatform.cloud.ibm.com/docs/content/catalog/overview-wkc.html?audience=dr&context=refinery&linkInPage=true)| Watson Knowledge Catalog fournit une plateforme de gestion des catalogues d'entreprise sécurisée qui est prise en charge par une infrastructure de stratégie de données. Un catalogue met en relation des données et des connaissances avec les personnes qui ont besoin de les utiliser. L'infrastructure de stratégie de données vérifie que l'accès aux données respecte vos règles métier. | [Evénements générés par Watson Knowledge Catalog](https://dataplatform.cloud.ibm.com/docs/content/admin/at-events.html#wkc) |  
{: caption="Liste des services de données Watson Cloud qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 

