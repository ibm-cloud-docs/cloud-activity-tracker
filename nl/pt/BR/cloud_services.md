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



# Serviços de nuvem
{: #cloud_services}

Use o serviço {{site.data.keyword.cloudaccesstraillong}} para monitorar atividades iniciadas pelo usuário que mudam o estado de qualquer dos serviços a seguir no {{site.data.keyword.IBM_notm}} Cloud:
{:shortdesc}

**Nota:** para obter informações sobre as regiões em que um serviço está disponível no {{site.data.keyword.cloud_notm}}, consulte [Serviços por região](/docs/resources?topic=resources-services_region#services_region).


## Serviços de infraestrutura de cálculo
{: #infrastructure}

**Nota:** para que um usuário gere eventos do {{site.data.keyword.BluVirtServers_short}} e do {{site.data.keyword.baremetal_short}} {{site.data.keyword.cloudaccesstrailshort}}, ele deve ter acesso aos recursos de infraestrutura no IBM Cloud Console. Para obter mais informações, consulte [Monitorando a atividade do {{site.data.keyword.BluVirtServers_short}} e do {{site.data.keyword.baremetal_short}} com o {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/tutorials?topic=cloud-activity-tracker-vsi#vsi).

A tabela a seguir lista os serviços de infraestrutura que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}:

| Serviço     | Descrição | Eventos do {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.BluVirtServers_short}} ](/docs/vsi?topic=virtual-servers-about-virtual-servers#about-virtual-servers)| {{site.data.keyword.BluVirtServers}} são servidores virtuais escaláveis que são comprados com núcleos dedicados e alocações de memória. Eles são uma boa opção caso você esteja procurando por recursos de cálculo, que podem ser incluídos em minutos, com acesso a recursos como modelos de imagem.  | [Eventos que são gerados pelo {{site.data.keyword.BluVirtServers_short}}](/docs/vsi?topic=virtual-servers-at_events#at_events) |  
| [{{site.data.keyword.baremetal_long}} ](/docs/bare-metal?topic=bare-metal-about#about) | Os {{site.data.keyword.baremetal_short}} são servidores físicos de locatário único que fornecem desempenho e controle com acesso de baixo nível aos recursos de hardware. | [Eventos que são gerados pelo {{site.data.keyword.baremetal_short}}](/docs/bare-metal?topic=bare-metal-at_events#at_events) | 
{: caption="Lista de serviços de infraestrutura que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 




## Serviços sem servidor de cálculo
{: #serverless}

A tabela a seguir lista os serviços de cálculo serverless que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}:

| Serviço     | Descrição | Eventos do {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.openwhisk_short}}](/docs/openwhisk?topic=cloud-functions-index#index) |O {{site.data.keyword.openwhisk_short}} é uma plataforma de programação poliglota Functions-as-a-Service (FaaS) com base no Apache OpenWhisk que pode ser usada para escrever `code called actions` leves. | [Eventos que são gerados pelo {{site.data.keyword.openwhisk_short}}](/docs/openwhisk?topic=cloud-functions-activity_tracker#activity_tracker) |
{: caption="Lista de serviços de cálculo serverless que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Serviços de contêiner de plataforma
{: #ikcs}

O {{site.data.keyword.containershort_notm}} gera dois tipos de eventos do {{site.data.keyword.cloudaccesstrailshort}}:

* **Eventos de gerenciamento de cluster**
    
    * Esses eventos são gerados automaticamente.
    * Esses eventos são encaminhados automaticamente para o {{site.data.keyword.cloudaccesstrailshort}}.
    * É possível visualizar esses eventos por meio do **domínio de contas** do {{site.data.keyword.cloudaccesstrailshort}}. 

* **Eventos de auditoria do servidor de API do Kubernetes**

    * Esses eventos são gerados automaticamente.
    * Deve-se configurar seu cluster para encaminhar esses eventos para o serviço {{site.data.keyword.cloudaccesstrailshort}}.
    * É possível configurar seu cluster para enviar eventos para o **domínio de contas** ou para um **domínio de espaço** do {{site.data.keyword.cloudaccesstrailshort}}. Para obter mais informações, consulte [Enviando logs de auditoria](/docs/containers?topic=containers-health#api_forward).

A tabela a seguir lista os serviços de plataforma de contêiner que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}:

| Serviço     | Descrição | Eventos do {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.containerlong_notm}}: eventos de gerenciamento de cluster](/docs/containers?topic=containers-container_index#container_index)| Esses eventos relatam ações como criação, exclusão ou atualização de cluster. | [Eventos de gerenciamento de cluster ](/docs/containers?topic=containers-at_events#cluster-events) |  
| [{{site.data.keyword.containerlong_notm}}: Eventos de auditoria do servidor de API](/docs/containers?topic=containers-container_index#container_index)| Os eventos de auditoria do servidor de API do Kubernetes fornecem informações cronológicas sobre a sequência de atividades que afetam um cluster. Cada ação gera um evento | [Eventos de auditoria do servidor de API do Kubernetes](/docs/containers?topic=containers-at_events#kube-events) |
| [{{site.data.keyword.registrylong_notm}}](/docs/services/Registry?topic=registry-registry_overview#registry_overview) | É possível usar o serviço {{site.data.keyword.registrylong_notm}} para armazenar e acessar imagens privadas do Docker em uma arquitetura altamente disponível e escalável. | [Eventos que são gerados quando você interage com o {{site.data.keyword.registrylong_notm}}](/docs/services/Registry?topic=registry-at_events#at_events) | 
{: caption="Eventos de contêiner" caption-side="top"} 



## Aplicativos do Platform Cloud Foundry
{: #platform_cfapps}

Os eventos que são enviados pelos aplicativos Cloud Foundry para o {{site.data.keyword.cloudaccesstrailshort}} são listados na área de resposta de `GET /v2/events`, sob a seção de corpo. O campo *Tipo* lista todas as ações que geram um evento. Para obter mais informações, consulte [API de eventos ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://apidocs.cloudfoundry.org/270/events/list_all_events.html){:new_window}.


## Serviços integrados principais de plataforma
{: #platform_core_integrated}

Os serviços principais de plataforma geram eventos do {{site.data.keyword.cloudaccesstrailshort}} que podem ser visualizados por meio do **domínio de contas** do {{site.data.keyword.cloudaccesstrailshort}}.

A tabela a seguir lista os serviços principais de plataforma que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}:

| Serviço     | Descrição | Eventos do {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [Provisionando e gerenciando serviços de catálogo para recursos que são gerenciados pelo {{site.data.keyword.iamshort}} (IAM)](/docs/overview?topic=overview-ui#catalogcreate) | É possível provisionar uma instância de serviço, renomear uma instância de serviço, mudar o plano de uma instância de serviço e remover uma instância de serviço. | [Eventos que são gerados quando você interage com serviços de catálogo ](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_rc#at_events_rc) |  
| [Provisionando e gerenciando serviços de catálogo que são ligados a um espaço do Cloud Foundry](/docs/overview?topic=overview-ui#catalogcreate)| É possível provisionar uma instância de serviço, renomear uma instância de serviço, mudar o plano de uma instância de serviço e remover uma instância de serviço. </br>Esses eventos são gerados para serviços que são provisionados em um espaço do CF. | [Eventos que são gerados quando você interage com serviços de catálogo ](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-cf#cf_catalog) |  
| [Gerenciando uma conta](/docs/account?topic=account-accounts#accounts) | É possível inscrever-se para uma conta do {{site.data.keyword.IBM_notm}} usando um IBMid existente, criando um novo IBMid ou usando um ID federado. | [Eventos que são gerados quando você gerencia uma conta](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_acc_mgt#at_events_acc_mgt_account) |
| [Gerenciando usuários](/docs/iam?topic=iam-iamuserinv#iamusermanage) | É possível visualizar e gerenciar usuários na conta ou nas organizações que você possui ou gerencia.  | [Eventos que são gerados quando você gerencia usuários ](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_acc_mgt#at_events_acc_mgt_users) |
| [Gerenciando organizações](/docs/account?topic=account-orgsspacesusers#orgsspacesusers) | Como um proprietário da conta, é possível incluir e gerenciar organizações na conta. | [Eventos que são gerados quando você gerencia organizações ](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_acc_mgt#at_events_acc_mgt_org) |
{: caption="Lista de ações da plataforma principal" caption-side="top"} 


## Serviços de banco de dados da plataforma
{: #database}

A tabela a seguir lista os serviços de banco de dados que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}:

| Serviço     | Descrição | Eventos do {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|----------------------------------------------------|
| [{{site.data.keyword.databases-for-postgresql_full_notm}}](/docs/services/databases-for-postgresql?topic=databases-for-postgresql-about#about) | O {{site.data.keyword.databases-for-postgresql_full_notm}} é um serviço PostgreSQL gerenciado que é hospedado no {{site.data.keyword.cloud_notm}} e integrado a outros serviços do {{site.data.keyword.cloud_notm}}. | [Eventos que são gerados pelo {{site.data.keyword.databases-for-postgresql_full_notm}}](/docs/services/databases-for-postgresql?topic=databases-for-postgresql-activity-tracker#activity-tracker) |
| [{{site.data.keyword.databases-for-redis_full_notm}}](/docs/services/databases-for-redis?topic=databases-for-redis-about#about-databases-for-redis) | O {{site.data.keyword.databases-for-redis_full_notm}} é um serviço Redis gerenciado que é hospedado no {{site.data.keyword.cloud_notm}} e integrado a outros serviços do {{site.data.keyword.cloud_notm}}.  | [Eventos que são gerados pelo {{site.data.keyword.databases-for-redis_full_notm}} ](/docs/services/databases-for-redis?topic=databases-for-redis-activity-tracker-integration#activity-tracker-integration) |
| [{{site.data.keyword.sqlquery_short}}](/docs/services/sql-query?topic=sql-query-overview#overview) | É possível usar o serviço {{site.data.keyword.sqlquery_short}} para executar consultas SQL (ou seja, instruções SELECT) para analisar, transformar ou limpar dados retangulares. | [Eventos que são gerados pelo {{site.data.keyword.sqlquery_short}} ](/docs/services/sql-query?topic=sql-query-activitytracker#activity-tracker-events) |  
| [{{site.data.keyword.databases-for-etcd_full_notm}}](/docs/services/databases-for-etcd?topic=databases-for-etcd-about#about-databases-for-etcd) | O {{site.data.keyword.databases-for-etcd_full_notm}} é um serviço de etcd gerenciado que é hospedado no {{site.data.keyword.cloud_notm}} e integrado a outros serviços do {{site.data.keyword.cloud_notm}}. | [Eventos que são gerados pelo {{site.data.keyword.databases-for-etcd_full_notm}}](/docs/services/databases-for-etcd?topic=databases-for-etcd-activity-tracker#activity-tracker-integration) |
| [{{site.data.keyword.databases-for-elasticsearch_full_notm}}](/docs/services/databases-for-elasticsearch?topic=databases-for-elasticsearch-about#about-databases-for-elasticsearch) | O {{site.data.keyword.databases-for-elasticsearch_full_notm}} é um serviço Elasticsearch gerenciado que é hospedado no {{site.data.keyword.cloud_notm}} e integrado a outros serviços do {{site.data.keyword.cloud_notm}}. | [Eventos que são gerados pelo {{site.data.keyword.databases-for-elasticsearch_full_notm}}](/docs/services/databases-for-elasticsearch?topic=databases-for-elasticsearch-activity-tracker#activity-tracker-integration) |
| [{{site.data.keyword.messages-for-rabbitmq_full_notm}}](/docs/services/messages-for-rabbitmq?topic=messages-for-rabbitmq-about#about-messages-for-rabbitmq)  | O {{site.data.keyword.messages-for-rabbitmq_full_notm}} é um serviço RabbitMQ gerenciado que é hospedado no {{site.data.keyword.cloud_notm}} e integrado a outros serviços do {{site.data.keyword.cloud_notm}}.   | [Eventos que são gerados pelo {{site.data.keyword.messages-for-rabbitmq_full_notm}}](/docs/services/messages-for-rabbitmq?topic=messages-for-rabbitmq-activity-tracker#activity-tracker-integration) |
{: caption="Lista de serviços de banco de dados que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 




## Ferramentas do desenvolvedor da plataforma
{: #devops}

A tabela a seguir lista os serviços do DevOps que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}:

| Serviço     | Descrição | Eventos do {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.DRA_short}}](/docs/services/DevOpsInsights?topic=DevOpsInsights-insights_about#insights_about) |O {{site.data.keyword.DRA_short}} é uma integração no catálogo de cadeia de ferramentas aberta do {{site.data.keyword.cloud_notm}}. | [Eventos que são gerados pelo {{site.data.keyword.DRA_short}}](/docs/services/DevOpsInsights?topic=DevOpsInsights-at_events#at_events) |
| [{{site.data.keyword.contdelivery_short}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-cd_overview#cd_overview) | Com o {{site.data.keyword.contdelivery_short}}, é possível construir, testar
e entregar aplicativos usando práticas DevOps e ferramentas líderes de mercado. | [Eventos que são gerados pelo {{site.data.keyword.contdelivery_short}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-at_events#at_events) |
| [{{site.data.keyword.GlobalizationPipeline_short}}](/docs/services/GlobalizationPipeline?topic=GlobalizationPipeline-globalizationpipeline#globalizationpipeline) | Permite que os desenvolvedores de aplicativos liberem rapidamente os aplicativos traduzidos para clientes globais. | [Eventos gerados pelo {{site.data.keyword.GlobalizationPipeline_short}}](/docs/services/GlobalizationPipeline?topic=GlobalizationPipeline-gpat_events#gpat_events)|
{: caption="Lista de ferramentas do desenvolvedor que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Serviços do desenvolvedor integrado da plataforma
{: #integrated_dev_svcs}

A tabela a seguir lista os serviços do Cloud que podem ser usados para desenvolver apps e enviar eventos para o {{site.data.keyword.cloudaccesstrailshort}}:

| Serviço     | Descrição | Eventos do {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.dev_console}}](/docs/apps?topic=creating-apps-tutorial-getting-started#create) | No {{site.data.keyword.cloud_notm}}, é possível construir aplicativos móveis e da web no nível corporativo e tirar vantagem das extensões de nuvem que são hospedadas pelo {{site.data.keyword.cloud_notm}}. É possível usar o console do {{site.data.keyword.cloud_notm}} e as ferramentas de linha de comandos para construir, executar e implementar os seus apps. É possível usar o {{site.data.keyword.dev_console}} para criar um app usando um kit do iniciador. | [Eventos que são gerados pelo {{site.data.keyword.dev_console}}](/docs/apps?topic=creating-apps-at_events#at_events) |
| [{{site.data.keyword.mobilepushshort}}](/docs/services/mobilepush?topic=mobile-pushnotification-overview-push#overview-push)| É possível usar o serviço {{site.data.keyword.mobilepushshort}} para enviar notificações para dispositivos móveis e navegadores. Notificações podem ser destinadas a todos os usuários do aplicativo ou a um conjunto específico de usuários e dispositivos usando tags. Para cada mensagem enviada para o serviço, o público desejado recebe uma notificação. | [Eventos que são gerados pelo {{site.data.keyword.mobilepushshort}}](/docs/services/mobilepush?topic=mobile-pushnotification-push_activity_tracker#push_activity_tracker) |  
{: caption="Lista de serviços da web e móveis do Cloud que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Serviços de segurança integrada da plataforma
{: #platform_integrated_security}

Os serviços de segurança integrada geram eventos do {{site.data.keyword.cloudaccesstrailshort}} que podem ser visualizados por meio do **domínio de contas** do {{site.data.keyword.cloudaccesstrailshort}}.


A tabela a seguir lista os serviços principais de plataforma de segurança que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}:

| Serviço     | Descrição | Eventos do {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [Efetue login no {{site.data.keyword.cloud_notm}}](/docs/iam?topic=iam-features#features)| É possível efetuar login no {{site.data.keyword.cloud_notm}} usando uma senha, uma chave API ou um código de autorização. Como um usuário federado, é possível efetuar login por meio da interface da linha de comandos (CLI) usando uma senha descartável ou uma chave API. | [Eventos gerados quando um usuário ou um app efetua login no {{site.data.keyword.cloud_notm}}](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_login) |
| [Gerenciando o acesso ao Cloud Foundry do usuário da conta](/docs/iam?topic=iam-mngcf#mngcf) | É possível conceder, revogar e atualizar permissões do Cloud Foundry (CF) para os usuários na conta. | [Eventos que são gerados quando você gerencia funções do CF na conta](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-cf#cf_cfroles) |
| [{{site.data.keyword.iamlong}} (IAM)](/docs/iam?topic=iam-userroles#userroles) | É possível usar o IAM para gerenciar usuários e funções nos serviços de Plataforma e Infraestrutura do {{site.data.keyword.cloud_notm}}. | [Eventos que são gerados quando você gerencia políticas do IAM](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_policies) |
| [Gerenciando chaves API da plataforma](/docs/iam?topic=iam-manapikey#platform-api-keys) | É possível definir as chaves API da plataforma no {{site.data.keyword.IBM_notm}} Cloud que estão associadas a um usuário ou a um ID de serviço. | [Eventos que são gerados quando você gerencia as chaves de API da plataforma](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_apikeys) |
| [Gerenciando IDs de serviço](/docs/iam?topic=iam-serviceids#serviceids) | É possível definir IDs de serviço no nível de conta no {{site.data.keyword.IBM_notm}} Cloud. | [Eventos que são gerados quando você gerencia IDs de serviço](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_serviceids) |
| [Gerenciando grupos de acesso](/docs/iam?topic=iam-groups#groups) | É possível definir grupos de acesso para organizar um conjunto de usuários e IDs de serviço em uma única entidade que torna mais fácil para você designar permissões. | [Eventos que são gerados quando você gerencia grupos de acesso](/docs/services/cloud-activity-tracker/services?topic=cloud-activity-tracker-at_events_iam#at_events_iam_access) |
{: caption="Lista de serviços de plataforma de segurança principal" caption-side="top"} 


## Serviços de integração da plataforma
{: #integration}

A tabela a seguir lista os serviços de integração que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}:

| Serviço     | Descrição | Eventos do {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.messagehub}}](/docs/services/EventStreams?topic=eventstreams-about#about)|O {{site.data.keyword.messagehub}} é um barramento de mensagem de alto rendimento que é construído com o Apache Kafka. Ele é otimizado para a ingestão de eventos no {{site.data.keyword.IBM_notm}} e para a distribuição de fluxo de eventos entre os seus serviços e os seus aplicativos. | [Eventos que são gerados pelo {{site.data.keyword.messagehub}} ](/docs/services/EventStreams?topic=eventstreams-at_events#at_events) |  
{: caption="Lista de serviços de integração do Cloud que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Serviços de rede da plataforma
{: #network}

A tabela a seguir lista os serviços de rede do Cloud que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}:

| Serviço     | Descrição | Eventos do {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [IBM Cloud Internet Services (CIS)](/docs/infrastructure/cis?topic=cis-about-ibm-cloud-internet-services-cis-#about-ibm-cloud-internet-services-cis-)| O IBM Cloud Internet Services (CIS) fornece um serviço de Internet rápido, altamente eficaz, confiável e seguro. | [Eventos que são gerados pelo IBM Cloud Internet Services](/docs/infrastructure/cis?topic=cis-at_events#at_events) |  
{: caption="Lista de serviços de rede do Cloud que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Serviços de segurança da plataforma
{: #security}

A tabela a seguir lista os serviços de segurança do Cloud que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}:


| Serviço     | Descrição | Eventos do {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.cloudaccesstraillong_notm}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov)| É possível usar o serviço {{site.data.keyword.cloudaccesstrailshort}} para monitorar o {{site.data.keyword.cloudaccesstraillong_notm}}. | [Eventos que são gerados pelo serviço do {{site.data.keyword.cloudaccesstraillong_notm}}](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-downloading_events#events) |  
| [{{site.data.keyword.appid_full_notm}}](/docs/services/appid?topic=appid-about#about) | É possível usar o {{site.data.keyword.appid_short}} para incluir autenticação em seus apps móveis e da web e para proteger os recursos de backend. | [Eventos que são gerados pelo serviço do {{site.data.keyword.appid_short}}](/docs/services/appid?topic=appid-at-events#at-events) |
| [{{site.data.keyword.cloudcerts_full_notm}}](/docs/services/certificate-manager?topic=certificate-manager-about-certificate-manager#about-certificate-manager) | É possível usar o {{site.data.keyword.cloudcerts_short}} para gerenciar os certificados SSL para seus apps e serviços baseados no {{site.data.keyword.cloud_notm}}.  | [Eventos que são gerados pelo serviço do {{site.data.keyword.cloudcerts_short}}](/docs/services/certificate-manager?topic=certificate-manager-at_events#at_events) |
| [{{site.data.keyword.keymanagementservicelong}}](/docs/services/key-protect?topic=key-protect-getting-started-tutorial#getting-started-with-key-protect) | É possível usar o serviço {{site.data.keyword.keymanagementserviceshort}} para provisionar chaves criptografadas para apps no {{site.data.keyword.cloud_notm}}. | [Eventos que são gerados pelo serviço do {{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect?topic=key-protect-at-events#at-events) |
| [{{site.data.keyword.security-advisor_short}}](/docs/services/security-advisor?topic=security-advisor-about#about) | É possível usar o {{site.data.keyword.security-advisor_short}} para ajudar a monitorar a segurança de seus apps e cargas de trabalho do {{site.data.keyword.cloud_notm}}. | [Eventos que são gerados pelo serviço do {{site.data.keyword.security-advisor_short}}](/docs/services/security-advisor?topic=security-advisor-at_events#at_events) |
{: caption="Lista de serviços de segurança do Cloud que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 


## Serviços de armazenamento da plataforma
{: #storage}

A tabela a seguir lista os serviços de armazenamento do Cloud que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}:

| Serviço     | Descrição | Eventos do {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.cos_full_notm}}](/docs/services/cloud-object-storage?topic=cloud-object-storage-about-ibm-cloud-object-storage#about-ibm-cloud-object-storage)| É possível usar o {{site.data.keyword.cos_full_notm}} para armazenar dados no {{site.data.keyword.cloud_notm}}. Os dados são criptografados e dispersados ao longo de múltiplos locais geográficos e acessados sobre HTTP usando uma API de REST.   | [Eventos que são gerados pelo {{site.data.keyword.cos_full_notm}}](/docs/services/cloud-object-storage/basics?topic=cloud-object-storage-at_events#at_events) |  
{: caption="Lista de serviços de armazenamento do Cloud que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Serviços de dados da plataforma Watson
{: #watson_data}


| Serviço     | Descrição | Eventos do {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [Watson Studio](https://dataplatform.cloud.ibm.com/docs/content/getting-started/overview-ws.html?context=analytics&linkInPage=true) | O Watson Studio fornece o ambiente e as ferramentas para resolver seus problemas de negócios, trabalhando de forma colaborativa com os dados. É possível escolher as ferramentas que você precisa para analisar e visualizar dados, limpar e modelar dados, alimentar dados de fluxo ou criar, treinar e implementar modelos de aprendizado de máquina. | [Eventos que são gerados pelo Watson Studio](https://dataplatform.cloud.ibm.com/docs/content/admin/at-events.html#ws) |  
| [ Watson Machine Learning ](https://dataplatform.cloud.ibm.com/docs/content/analyze-data/ml-overview.html?audience=dr&context=refinery)| É possível usar o Watson Machine Learning para construir modelos analíticos sofisticados, que são treinados com os seus próprios dados, que podem ser implementados para uso em aplicativos. | [Eventos que são gerados pelo Watson Machine Learning](https://dataplatform.cloud.ibm.com/docs/content/admin/at-events.html#wml) | 
| [Watson Knowledge Catalog](https://dataplatform.cloud.ibm.com/docs/content/catalog/overview-wkc.html?audience=dr&context=refinery&linkInPage=true)| O Watson Knowledge Catalog fornece uma plataforma de gerenciamento de catálogo corporativo segura que é suportada por uma estrutura de política de dados. Um catálogo conecta dados e conhecimento às pessoas que precisam usá-lo. A estrutura de política de dados assegura que o acesso a dados seja compatível com suas regras de negócios. | [Eventos que são gerados pelo Watson Knowledge Catalog](https://dataplatform.cloud.ibm.com/docs/content/admin/at-events.html#wkc) |  
{: caption="Lista de serviços de dados do Watson Cloud que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 

