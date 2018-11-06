---

copyright:
  years: 2016, 2018
lastupdated: "2018-09-12"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}



# Services Cloud
{: #cloud_services}

Utilisez le service {{site.data.keyword.cloudaccesstraillong}} pour surveiller les activités utilisateur qui modifient l'état de l'un des services suivants dans le Cloud {{site.data.keyword.IBM_notm}} :
{:shortdesc}

**Remarque :** Pour obtenir des informations sur les régions dans lesquelles un service est disponible dans {{site.data.keyword.Bluemix_notm}}, voir [Services par région](/docs/resources/services_region.html#services_region).


## Infrastructure : services de serveur virtuel
{: #vs}

Le tableau suivant répertorie les services de serveur virtuel qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}} :

| Service     | Description |Evénements {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.BluVirtServers_short}} ](/docs/vsi/vsi_about.html#about-virtual-servers)| Les serveurs {{site.data.keyword.BluVirtServers}} sont des serveurs virtuels évolutifs qui sont achetés avec des coeurs dédiés et des allocations de mémoire. Ils constituent un très bon choix si vous recherchez des ressources de calcul, qui peuvent être ajoutées en quelques minutes, avec un accès à des fonctions telles que des modèles d'image. | [Evénements générés par {{site.data.keyword.BluVirtServers_short}}](/docs/vsi/vsi_activity_tracker_events.html#at_events) |  
{: caption="Liste des services de serveur virtuel qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 


## Plateforme : services d'analyse
{: #analytics}

Le tableau suivant répertorie les services d'analyse qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}} :

| Service     | Description |Evénements {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.streaminganalyticsfull}} ](/docs/services/StreamingAnalytics/index.html#gettingstarted)| {{site.data.keyword.streaminganalyticsfull}} tire sa puissance d'{{site.data.keyword.streamsshort}}, une plateforme d'analyse avancée que vous pouvez utiliser pour recevoir, analyser et mettre en corrélation les informations au fur et à mesure qu'elles arrivent depuis différentes sources de données en temps réel. | [Evénements générés par {{site.data.keyword.streaminganalyticsshort}} ]() |  
{: caption="Liste des services Cloud d'analyse qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 


## Plateforme : services de conteneur
{: #ikcs}

{{site.data.keyword.containershort_notm}} génère deux types d'événements {{site.data.keyword.cloudaccesstrailshort}} :

* **Evénements de gestion de cluster** : 
    
    * Ces événements sont générés automatiquement.
    * Ces événements sont automatiquement transférés vers {{site.data.keyword.cloudaccesstrailshort}}.
    * Vous pouvez afficher ces événements via le **domaine de compte** {{site.data.keyword.cloudaccesstrailshort}}. 

* **Evénements d'audit du serveur d'API Kubernetes** : 

    * Ces événements sont générés automatiquement.
    * Vous devez configurer votre cluster pour le transfert de ces événements au service {{site.data.keyword.cloudaccesstrailshort}}. 
    * Vous pouvez configurer votre cluster pour l'envoi d'événements au **domaine de compte** {{site.data.keyword.cloudaccesstrailshort}} ou à un **domaine d'espace**. Pour plus d'informations, voir [Envoi de journaux d'audit](/docs/containers/cs_health.html#api_forward).

Le tableau suivant répertorie les services de plateforme de conteneur qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}} :

| Service     | Description |Evénements {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.containerlong_notm}} : événements de gestion de cluster](/docs/containers/container_index.html#container_index)| Ces événements traitent d'actions comme la création, la suppression ou la mise à jour de clusters. | [Evénements de gestion de cluster ]() |  
| [{{site.data.keyword.containerlong_notm}} : événements d'audit du serveur d'API](/docs/containers/container_index.html#container_index)| Les événements d'audit du serveur d'API Kubernetes fournissent des informations chronologiques sur la séquence des activités qui affectent un cluster. Chaque action génère un événement. | [Evénements d'audit du serveur d'API Kubernetes](/docs/containers/cs_at_events.html#at_events) |
| [{{site.data.keyword.registrylong_notm}}](/docs/services/Registry/registry_overview.html#registry_overview) | Vous pouvez utiliser le service {{site.data.keyword.registrylong_notm}} pour stocker des images Docker privées et y accéder dans une architecture hautement disponible et évolutive. | [Evénements générés lors de l'interaction avec {{site.data.keyword.registrylong_notm}}](/docs/services/Registry/registry_at_events.html#at_events) | 
{: caption="Événements de conteneur" caption-side="top"} 



## Plateforme : applications Cloud Foundry
{: #platform_cfapps}

Les événements qui sont envoyés par les applications Cloud Foundry à {{site.data.keyword.cloudaccesstrailshort}} sont répertoriés dans la zone de réponse de `GET /v2/events`, sous la section body. La zone *Type* répertorie toutes les actions qui génèrent un événement. Pour plus d'informations, voir [API d'événements](https://apidocs.cloudfoundry.org/270/events/list_all_events.html).


## Plateforme : services intégrés de base
{: #platform_core_integrated}

Les services de plateforme de base génèrent des événements {{site.data.keyword.cloudaccesstrailshort}} que vous pouvez afficher via le **domaine de compte** {{site.data.keyword.cloudaccesstrailshort}}.

Le tableau suivant répertorie les services de plateforme de base qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}} :

| Service     | Description | Evénements {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [Mise à disposition et gestion de services de catalogue pour les ressources gérées par {{site.data.keyword.iamshort}} (IAM)](/docs/overview/ui.html#catalogcreate) | Vous pouvez mettre à disposition une instance de service, la renommer, modifier son plan et la supprimer. | [Evénements générés lors de l'interaction avec des services de catalogue ](/docs/services/cloud-activity-tracker/services/at_events_rc.html#at_events) |  
| [Mise à disposition et gestion de services de catalogue liés à un espace Cloud Foundry](/docs/overview/ui.html#catalogcreate)| Vous pouvez mettre à disposition une instance de service, la renommer, modifier son plan et la supprimer. </br>Ces événements sont générés pour des services qui sont mis à disposition dans un espace CF. | [Evénements générés lors de l'interaction avec des services de catalogue ](/docs/services/cloud-activity-tracker/services/at_events_cf.html#catalog) |  
| [Gestion d'un compte](/docs/account/index.html#accounts) | Vous pouvez vous inscrire à un compte {{site.data.keyword.IBM_notm}} en utilisant un IBMid existant, en créant un nouvel IBMid ou en utilisant un ID fédéré. | [Evénements générés lors de la gestion d'un compte](/docs/services/cloud-activity-tracker/services/at_events_acc_mgt.html#account) |
| [Gestion des utilisateurs](/docs/iam/iamusermanage.html#iamusermanage) |Vous pouvez afficher et gérer des utilisateurs au niveau du compte ou des organisations que vous possédez ou gérez. | [Evénements générés lors de la gestion d'utilisateurs](/docs/services/cloud-activity-tracker/services/at_events_acc_mgt.html#users) |
| [Gestion des organisations](/docs/account/orgs_spaces.html#orgsspacesusers) | En tant que propriétaire de compte, vous pouvez ajouter et gérer des organisations sur le compte. | [Evénements générés lors de la gestion d'organisations](/docs/services/cloud-activity-tracker/services/at_events_acc_mgt.html#org) |
{: caption="Liste des actions de plateforme de base" caption-side="top"} 


## Plateforme : services de base de données
{: #database}

Le tableau suivant répertorie les services de base de données qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}} :

| Service     | Description | Evénements {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.sqlquery_short}}](/docs/services/sql-query/sql-query.html#overview)| Vous pouvez utiliser le service {{site.data.keyword.sqlquery_short}} pour exécuter des requêtes SQL (à savoir, des instructions SELECT) pour analyser, transformer ou nettoyer des données rectangulaires. | [Evénements générés par {{site.data.keyword.sqlquery_short}} ](/docs/services/sql-query/activity.html#activity-tracker-events) |  
{: caption="Liste des services Cloud de base de données qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 


## Plateforme : services de développeur intégrés
{: #integrated_dev_svcs}

Le tableau suivant répertorie les services Cloud que vous pouvez utiliser pour développer des applications et envoyer des événements à {{site.data.keyword.cloudaccesstrailshort}} :

| Service     | Description | Evénements {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.dev_console}}](/docs/apps/index.html#create) |Dans {{site.data.keyword.Bluemix_notm}}, vous pouvez générer des applications mobiles et Web au niveau de l'entreprise, et tirer parti des extensions cloud hébergées par {{site.data.keyword.Bluemix_notm}}. Vous pouvez utiliser les outils de ligne de commande et la console {{site.data.keyword.Bluemix_notm}} pour générer, exécuter et déployer vos applications. Vous pouvez utiliser {{site.data.keyword.dev_console}} pour créer une application à l'aide d'un kit de démarrage. | [Evénements générés par {{site.data.keyword.dev_console}}](/docs/apps/at_events_devx.html#at_events) |
| [{{site.data.keyword.mobilepushshort}}](/docs/services/mobilepush/c_overview_push.html#overview-push)| Vous pouvez utiliser le service {{site.data.keyword.mobilepushshort}} pour envoyer des notifications à des périphériques mobiles et des navigateurs. Les notifications peuvent être ciblées pour tous les utilisateurs d'application ou pour un ensemble spécifique d'utilisateurs et de périphériques à l'aide d'étiquettes. Le public visé reçoit une notification pour chaque message que vous soumettez au service. | [Evénements générés par {{site.data.keyword.mobilepushshort}}](/docs/services/mobilepush/push_activity_tracker.html#push_activity_tracker) |  
{: caption="Liste des services de cloud mobile et Web qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Plateforme : services de sécurité intégrés
{: #platform_integrated_security}

Les services de sécurité intégrés génèrent des événements {{site.data.keyword.cloudaccesstrailshort}} que vous pouvez afficher via le **domaine de compte** {{site.data.keyword.cloudaccesstrailshort}}.


Le tableau suivant répertorie les services de plateforme de sécurité de base qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}} :

| Service     | Description | Evénements {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [Connexion à {{site.data.keyword.Bluemix_notm}}](/docs/iam/quickstart.html#getstarted)| Vous pouvez vous connecter à {{site.data.keyword.Bluemix_notm}} en utilisant un mot de passe, une clé d'API, un code d'autorisation ou un code d'accès. En tant qu'utilisateur fédéré, vous pouvez vous connecter à partir de l'interface de ligne de commande en utilisant un code d'accès à utilisation unique ou une clé d'API. | [Evénements générés lors de la connexion d'un utilisateur ou d'une application à {{site.data.keyword.Bluemix_notm}}](/docs/services/cloud-activity-tracker/services/at_events_iam.html#login) |
| [Gestion de l'accès d'un utilisateur de compte à Cloud Foundry](/docs/iam/mngcf.html#mngcf) | Vous pouvez accorder, révoquer et mettre à jour les autorisations Cloud Foundry (CF) des utilisateurs dans le compte. | [Evénements générés lors de la gestion des rôles CF dans le compte](/docs/services/cloud-activity-tracker/services/at_events_cf.html#cfroles) |
| [{{site.data.keyword.iamlong}} (IAM)](/docs/iam/users_roles.html#userroles) |Vous pouvez utiliser IAM pour gérer des utilisateurs et des rôles dans les services de plateforme et d'infrastructure {{site.data.keyword.Bluemix_notm}}. | [Evénements générés lors de la gestion des règles IAM](/docs/services/cloud-activity-tracker/services/at_events_iam.html#policies) |
| [Gestion des clés d'API de plateforme](/docs/iam/apikeys.html#platform-api-keys) | Vous pouvez définir des clés d'API de plateforme qui sont associées à un ID utilisateur ou de service dans {{site.data.keyword.IBM_notm}} Cloud. | [Evénements générés lors de la gestion des clés d'API de plateforme](/docs/services/cloud-activity-tracker/services/at_events_iam.html#apikeys) |
| [Gestion des ID de service](/docs/iam/serviceid.html#serviceids) | Vous pouvez définir des ID de service au niveau du compte dans {{site.data.keyword.IBM_notm}} Cloud. | [Evénements générés lors de la gestion des ID de service](/docs/services/cloud-activity-tracker/services/at_events_iam.html#serviceids) |
| [Gestion des groupes d'accès](/docs/iam/groups.html#groups) | Vous pouvez définir des groupes d'accès afin d'organiser un ensemble d'utilisateurs et d'ID de service dans une seule entité, et de faciliter l'affectation de droits d'accès. | [Evénements générés lors de la gestion des groupes d'accès](/docs/services/cloud-activity-tracker/services/at_events_iam.html#access) |
{: caption="Liste des services de plateforme de sécurité de base" caption-side="top"} 


## Plateforme : services d'intégration
{: #integration}

Le tableau suivant répertorie les services d'intégration qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}} :

| Service     | Description | Evénements {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.messagehub}}](/docs/services/MessageHub/messagehub010.html#about)| {{site.data.keyword.messagehub}} est un bus de messages à haute capacité généré avec Apache Kafka. Il est optimisé pour l'ingestion d'événements dans {{site.data.keyword.IBM_notm}} et la distribution de flux d'événements dans des services et des applications. | [Evénements générés par {{site.data.keyword.messagehub}} ](/docs/services/MessageHub/at-events.html#at_events) |  
{: caption="Liste des services Cloud d'intégration qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Plateforme : services réseau
{: #network}

Le tableau suivant répertorie les services Cloud de réseau qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}} :

| Service     | Description | Evénements {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [IBM Cloud Internet Services (CIS)](/docs/infrastructure/cis/about.html#about-ibm-cloud-internet-services-cis-)| IBM Cloud Internet Services (CIS) fournit un service Internet rapide, très performant, fiable et sécurisé. | [Evénements générés par IBM Cloud Internet Services](/docs/infrastructure/cis/at_events.html#at_events) |  
{: caption="Liste des services Cloud de réseau qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Plateforme : services de sécurité
{: #security}

Le tableau suivant répertorie les services Cloud de sécurité qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}} :


| Service     | Description | Evénements {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.cloudaccesstraillong_notm}}](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#activity_tracker_ov)| Vous pouvez utiliser le service {{site.data.keyword.cloudaccesstrailshort}} pour surveiller {{site.data.keyword.cloudaccesstraillong_notm}}. | [Evénements générés par le service {{site.data.keyword.cloudaccesstraillong_notm}}](/docs/services/cloud-activity-tracker/reference/events.html#events) |  
| [{{site.data.keyword.appid_full_notm}}](/docs/services/appid/about.html#about) | Vous pouvez utiliser {{site.data.keyword.appid_short}} pour ajouter l'authentification à vos applications mobiles et Web, et pour protéger vos ressources de back end. | [Evénements générés par le service {{site.data.keyword.appid_short}}](/docs/services/appid/iam.html#tracking) |
| [{{site.data.keyword.cloudcerts_full_notm}}](/docs/services/certificate-manager/about.html#about-certificate-manager) | Vous pouvez utiliser {{site.data.keyword.cloudcerts_short}} pour gérer les certificats SSL pour vos applications et services {{site.data.keyword.Bluemix_notm}}. | [Evénements générés par le service {{site.data.keyword.cloudcerts_short}}](/docs/services/certificate-manager/at_events.html#at_events) |
| [{{site.data.keyword.keymanagementservicelong}}](/docs/services/key-protect/index.html#getting-started-with-key-protect) |Vous pouvez utiliser le service {{site.data.keyword.keymanagementserviceshort}} pour mettre à disposition des clés chiffrées pour des applications dans {{site.data.keyword.Bluemix_notm}}. | [Evénements générés par le service {{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect/at-events.html#at-events) |
{: caption="Liste des services Cloud de sécurité qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 


## Plateforme : services de stockage
{: #storage}

Le tableau suivant répertorie les services Cloud de stockage qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}} :

| Service     | Description | Evénements {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.cos_full_notm}}](/docs/services/cloud-object-storage/about-cos.html#about-ibm-cloud-object-storage)| Vous pouvez utiliser {{site.data.keyword.cos_full_notm}} pour stocker des données dans {{site.data.keyword.Bluemix_notm}}. Les données sont chiffrées et dispersées sur plusieurs emplacements géographiques, et sont accessibles via HTTP à l'aide d'une API REST.   | [Evénements générés par {{site.data.keyword.cos_full_notm}}](/docs/services/cloud-object-storage/basics/at.html#at_events) |  
{: caption="Liste des services Cloud de stockage qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Plateforme Watson : services de données
{: #watson_data}


| Service     | Description | Evénements {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [Watson Studio](https://dataplatform.cloud.ibm.com/docs/content/getting-started/overview-ws.html?context=analytics&linkInPage=true) | Watson Studio fournit l'environnement et les outils qui permettent de résoudre vos problèmes métier en utilisant les données de façon collaborative. Vous pouvez choisir les outils dont vous avez besoin pour analyser et visualiser des données, nettoyer et mettre en forme des données, ingérer des flux de données en continu, ou pour créer, former et déployer des modèles d'apprentissage automatique. | [Evénements générés par Watson Studio](https://dataplatform.cloud.ibm.com/docs/content/admin/at-events.html#ws) |  
| [Watson Machine Learning](https://dataplatform.cloud.ibm.com/docs/content/analyze-data/ml-overview.html?audience=dr&context=refinery)| Vous pouvez utiliser Watson Machine Learning pour créer des modèles d'analyse sophistiqués, formés avec vos propres données, que vous pouvez déployer en vue de les utiliser dans des applications. | [Evénements générés par Watson Machine Learning](https://dataplatform.cloud.ibm.com/docs/content/admin/at-events.html#wml) | 
| [Watson Knowledge Catalog](https://dataplatform.cloud.ibm.com/docs/content/catalog/overview-wkc.html?audience=dr&context=refinery&linkInPage=true)| Watson Knowledge Catalog fournit une plateforme de gestion des catalogues d'entreprise sécurisée qui est prise en charge par une infrastructure de stratégie de données. Un catalogue met en relation des données et des connaissances avec les personnes qui ont besoin de les utiliser. L'infrastructure de stratégie de données vérifie que l'accès aux données respecte vos règles métier. | [Evénements générés par Watson Knowledge Catalog](https://dataplatform.cloud.ibm.com/docs/content/admin/at-events.html#wkc) |  
{: caption="Liste des services de données Watson Cloud qui envoient des événements à {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 


