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



# Serviços de nuvem
{: #cloud_services}

Use o serviço {{site.data.keyword.cloudaccesstraillong}} para monitorar atividades iniciadas pelo usuário que mudam o estado de qualquer dos serviços a seguir no {{site.data.keyword.IBM_notm}} Cloud:
{:shortdesc}

**Nota:** para obter informações sobre as regiões em que um serviço está disponível no {{site.data.keyword.Bluemix_notm}}, consulte [Serviços por região](/docs/resources/services_region.html#services_region).


## Infraestrutura: serviços do Virtual Server
{: #vs}

A tabela a seguir lista os serviços do Virtual Server que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}:

| Serviço     | Descrição | Eventos do {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.BluVirtServers_short}} ](/docs/vsi/vsi_about.html#about-virtual-servers)| {{site.data.keyword.BluVirtServers}} são servidores virtuais escaláveis que são comprados com núcleos dedicados e alocações de memória. Eles são uma boa opção caso você esteja procurando por recursos de cálculo, que podem ser incluídos em minutos, com acesso a recursos como modelos de imagem. | [Eventos gerados pelo {{site.data.keyword.BluVirtServers_short}} ](/docs/vsi/vsi_activity_tracker_events.html#at_events) |  
{: caption="Lista de serviços do Virtual Server que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 


## Plataforma: Serviços de analítica
{: #analytics}

A tabela a seguir lista os serviços do Analytics que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}:

| Serviço     | Descrição | Eventos do {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.streaminganalyticsfull}} ](/docs/services/StreamingAnalytics/index.html#gettingstarted)| O {{site.data.keyword.streaminganalyticsfull}} foi desenvolvido com o {{site.data.keyword.streamsshort}}, uma plataforma analítica avançada que
pode ser usada para alimentar, analisar e correlacionar informações assim que chegam de diferentes tipos de origens de dados em tempo real. | [Eventos gerados pelo {{site.data.keyword.streaminganalyticsshort}} ]() |  
{: caption="Lista de serviços de análise de dados do Cloud que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 


## Plataforma: Serviços de contêineres
{: #ikcs}

O {{site.data.keyword.containershort_notm}} gera dois tipos de eventos do {{site.data.keyword.cloudaccesstrailshort}}:

* **Eventos de gerenciamento de cluster**: 
    
    * Esses eventos são gerados automaticamente.
    * Esses eventos são encaminhados automaticamente para o {{site.data.keyword.cloudaccesstrailshort}}.
    * É possível visualizar esses eventos por meio do **domínio de contas** do {{site.data.keyword.cloudaccesstrailshort}}. 

* **Eventos de auditoria do servidor de API do Kubernetes **: 

    * Esses eventos são gerados automaticamente.
    * Deve-se configurar seu cluster para encaminhar esses eventos para o serviço {{site.data.keyword.cloudaccesstrailshort}}.
    * É possível configurar seu cluster para enviar eventos para o **domínio de contas** ou para um **domínio de espaço** do {{site.data.keyword.cloudaccesstrailshort}}. Para obter mais informações, consulte [Enviando logs de auditoria](/docs/containers/cs_health.html#api_forward).

A tabela a seguir lista os serviços de plataforma de contêiner que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}:

| Serviço     | Descrição | Eventos do {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.containerlong_notm}}: eventos de gerenciamento de cluster](/docs/containers/container_index.html#container_index)| Esses eventos relatam ações como criação, exclusão ou atualização de cluster. | [Eventos de gerenciamento de cluster ]() |  
| [ {{site.data.keyword.containerlong_notm}}: Eventos de auditoria do servidor de API](/docs/containers/container_index.html#container_index)| Os eventos de auditoria do servidor de API do Kubernetes fornecem informações cronológicas sobre a sequência de atividades que afetam um cluster. Cada ação gera um evento | [Eventos de auditoria do servidor de API do Kubernetes](/docs/containers/cs_at_events.html#at_events) |
| [{{site.data.keyword.registrylong_notm}}](/docs/services/Registry/registry_overview.html#registry_overview) | É possível usar o serviço {{site.data.keyword.registrylong_notm}} para armazenar e acessar imagens privadas do Docker em uma arquitetura altamente disponível e escalável. | [Eventos gerados ao interagir com o {{site.data.keyword.registrylong_notm}}](/docs/services/Registry/registry_at_events.html#at_events) | 
{: caption="Eventos de contêiner" caption-side="top"} 



## Plataforma: aplicativos Cloud Foundry
{: #platform_cfapps}

Os eventos que são enviados pelos aplicativos Cloud Foundry para o {{site.data.keyword.cloudaccesstrailshort}} são listados na área de resposta de `GET /v2/events`, sob a seção de corpo. O campo *Tipo* lista todas as ações que geram um evento. Para obter mais informações, consulte [API de eventos](https://apidocs.cloudfoundry.org/270/events/list_all_events.html).


## Plataforma: serviços integrados principais
{: #platform_core_integrated}

Os serviços principais de plataforma geram eventos do {{site.data.keyword.cloudaccesstrailshort}} que podem ser visualizados por meio do **domínio de contas** do {{site.data.keyword.cloudaccesstrailshort}}.

A tabela a seguir lista os serviços principais de plataforma que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}:

| Serviço     | Descrição | Eventos do {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [Provisionando e gerenciando serviços de catálogo para recursos que são gerenciados pelo {{site.data.keyword.iamshort}} (IAM)](/docs/overview/ui.html#catalogcreate) | É possível provisionar uma instância de serviço, renomear uma instância de serviço, mudar o plano de uma instância de serviço e remover uma instância de serviço. | [Eventos gerados ao interagir com serviços de Catálogo ](/docs/services/cloud-activity-tracker/services/at_events_rc.html#at_events) |  
| [Provisionando e gerenciando serviços de catálogo que são ligados a um espaço do Cloud Foundry](/docs/overview/ui.html#catalogcreate)| É possível provisionar uma instância de serviço, renomear uma instância de serviço, mudar o plano de uma instância de serviço e remover uma instância de serviço. </br>Esses eventos são gerados para serviços que são provisionados em um espaço do CF. | [Eventos gerados ao interagir com serviços de Catálogo](/docs/services/cloud-activity-tracker/services/at_events_cf.html#catalog) |  
| [Gerenciando uma conta](/docs/account/index.html#accounts) | É possível inscrever-se para uma conta do {{site.data.keyword.IBM_notm}} usando um IBMid existente,
criando um novo IBMid ou usando um ID federado. | [Eventos gerados ao gerenciar uma conta](/docs/services/cloud-activity-tracker/services/at_events_acc_mgt.html#account) |
| [Gerenciando usuários](/docs/iam/iamusermanage.html#iamusermanage) | É possível visualizar e gerenciar usuários na conta ou nas organizações que você possui ou gerencia. | [Eventos gerados ao gerenciar usuários ](/docs/services/cloud-activity-tracker/services/at_events_acc_mgt.html#users) |
| [Gerenciando organizações](/docs/account/orgs_spaces.html#orgsspacesusers) | Como um proprietário da conta, é possível incluir e gerenciar organizações na conta. | [Eventos gerados ao gerenciar organizações ](/docs/services/cloud-activity-tracker/services/at_events_acc_mgt.html#org) |
{: caption="Lista de ações da plataforma principal" caption-side="top"} 


## Plataforma: Serviços de banco de
{: #database}

A tabela a seguir lista os serviços de banco de dados que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}:

| Serviço     | Descrição | Eventos do {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.sqlquery_short}}](/docs/services/sql-query/sql-query.html#overview)| É possível usar o serviço {{site.data.keyword.sqlquery_short}} para executar consultas SQL (ou seja, instruções SELECT) para analisar, transformar ou limpar dados retangulares. | [Eventos gerados pelo {{site.data.keyword.sqlquery_short}} ](/docs/services/sql-query/activity.html#activity-tracker-events) |  
{: caption="Lista de serviços de banco de dados do Cloud que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 


## Plataforma: serviços integrados do desenvolvedor
{: #integrated_dev_svcs}

A tabela a seguir lista os serviços do Cloud que podem ser usados para desenvolver apps e enviar eventos para o {{site.data.keyword.cloudaccesstrailshort}}:

| Serviço     | Descrição | Eventos do {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.dev_console}}](/docs/apps/index.html#create) | No {{site.data.keyword.Bluemix_notm}}, é possível construir aplicativos móveis e da web no nível corporativo e tirar vantagem das extensões de nuvem que são hospedadas pelo {{site.data.keyword.Bluemix_notm}}. É possível usar o console e as ferramentas de linha de comandos do {{site.data.keyword.Bluemix_notm}} para
construir, executar e implementar seus apps. É possível usar o {{site.data.keyword.dev_console}} para criar um app usando um kit do iniciador. | [Eventos gerados pelo {{site.data.keyword.dev_console}}](/docs/apps/at_events_devx.html#at_events) |
| [{{site.data.keyword.mobilepushshort}}](/docs/services/mobilepush/c_overview_push.html#overview-push)| É possível usar o serviço {{site.data.keyword.mobilepushshort}} para enviar notificações para dispositivos móveis e navegadores. É possível direcionar notificações para todos os usuários
do aplicativo ou para um conjunto específico de usuários e dispositivos usando tags. Para cada mensagem enviada para o serviço, o público desejado recebe uma notificação. | [Eventos gerados pelo {{site.data.keyword.mobilepushshort}}](/docs/services/mobilepush/push_activity_tracker.html#push_activity_tracker) |  
{: caption="Lista de serviços da web e móveis do Cloud que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Plataforma: serviços de segurança integrada
{: #platform_integrated_security}

Os serviços de segurança integrada geram eventos do {{site.data.keyword.cloudaccesstrailshort}} que podem ser visualizados por meio do **domínio de contas** do {{site.data.keyword.cloudaccesstrailshort}}.


A tabela a seguir lista os serviços principais de plataforma de segurança que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}:

| Serviço     | Descrição | Eventos do {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [Efetue login no {{site.data.keyword.Bluemix_notm}}](/docs/iam/quickstart.html#getstarted)| É possível efetuar login no {{site.data.keyword.Bluemix_notm}} usando uma senha, uma chave API ou um código de autorização. Como um usuário federado, é possível efetuar login por meio da interface da linha de comandos (CLI) usando uma senha descartável ou uma chave API. | [Eventos gerados quando um usuário ou um app efetua login no {{site.data.keyword.Bluemix_notm}}](/docs/services/cloud-activity-tracker/services/at_events_iam.html#login) |
| [Gerenciando o acesso ao Cloud Foundry do usuário da conta](/docs/iam/mngcf.html#mngcf) | É possível conceder, revogar e atualizar permissões do Cloud Foundry (CF) para os usuários na conta. | [Eventos gerados ao gerenciar funções do CF na conta](/docs/services/cloud-activity-tracker/services/at_events_cf.html#cfroles) |
| [{{site.data.keyword.iamlong}} (IAM)](/docs/iam/users_roles.html#userroles) | É possível usar o IAM para gerenciar usuários e funções nos serviços de Plataforma e Infraestrutura do {{site.data.keyword.Bluemix_notm}}. | [Eventos gerados ao gerenciar políticas do IAM](/docs/services/cloud-activity-tracker/services/at_events_iam.html#policies) |
| [Gerenciando chaves API da plataforma](/docs/iam/apikeys.html#platform-api-keys) | É possível definir as chaves API da plataforma no {{site.data.keyword.IBM_notm}} Cloud que estão associadas a um usuário ou a um ID de serviço. | [Eventos gerados ao gerenciar chaves API da plataforma](/docs/services/cloud-activity-tracker/services/at_events_iam.html#apikeys) |
| [Gerenciando IDs de serviço](/docs/iam/serviceid.html#serviceids) | É possível definir IDs de serviço no nível de conta no {{site.data.keyword.IBM_notm}} Cloud. | [Eventos gerados ao gerenciar IDs de serviço](/docs/services/cloud-activity-tracker/services/at_events_iam.html#serviceids) |
| [Gerenciando grupos de acesso](/docs/iam/groups.html#groups) | É possível definir grupos de acesso para organizar um conjunto de usuários e IDs de serviço em uma única entidade que torna mais fácil para você designar permissões. | [Eventos gerados ao gerenciar grupos de acesso](/docs/services/cloud-activity-tracker/services/at_events_iam.html#access) |
{: caption="Lista de serviços de plataforma de segurança principal" caption-side="top"} 


## Plataforma: Serviços de integração
{: #integration}

A tabela a seguir lista os serviços de integração que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}:

| Serviço     | Descrição | Eventos do {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.messagehub}}](/docs/services/MessageHub/messagehub010.html#about)| O {{site.data.keyword.messagehub}} é um barramento de mensagem de alto rendimento construído com o Apache Kafka. Ele é otimizado para a ingestão de eventos no {{site.data.keyword.IBM_notm}} e para a distribuição de fluxo de eventos entre os seus serviços e os seus aplicativos. | [Eventos gerados pelo {{site.data.keyword.messagehub}} ](/docs/services/MessageHub/at-events.html#at_events) |  
{: caption="Lista de serviços de integração do Cloud que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Plataforma: serviços de rede
{: #network}

A tabela a seguir lista os serviços de rede do Cloud que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}:

| Serviço     | Descrição | Eventos do {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [IBM Cloud Internet Services (CIS)](/docs/infrastructure/cis/about.html#about-ibm-cloud-internet-services-cis-)| O IBM Cloud Internet Services (CIS) fornece um serviço de Internet rápido, altamente eficaz, confiável e seguro. | [Eventos gerados pelo IBM Cloud Internet Services](/docs/infrastructure/cis/at_events.html#at_events) |  
{: caption="Lista de serviços de rede do Cloud que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Plataforma: serviços de segurança
{: #security}

A tabela a seguir lista os serviços de segurança do Cloud que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}:


| Serviço     | Descrição | Eventos do {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.cloudaccesstraillong_notm}}](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#activity_tracker_ov)| É possível usar o serviço {{site.data.keyword.cloudaccesstrailshort}} para monitorar o {{site.data.keyword.cloudaccesstraillong_notm}}. | [Eventos gerados pelo serviço {{site.data.keyword.cloudaccesstraillong_notm}}](/docs/services/cloud-activity-tracker/reference/events.html#events) |  
| [{{site.data.keyword.appid_full_notm}}](/docs/services/appid/about.html#about) | É possível usar o {{site.data.keyword.appid_short}} para incluir autenticação em seus apps móveis e da web e para proteger os recursos de backend. | [Eventos gerados pelo serviço {{site.data.keyword.appid_short}}](/docs/services/appid/iam.html#tracking) |
| [{{site.data.keyword.cloudcerts_full_notm}}](/docs/services/certificate-manager/about.html#about-certificate-manager) | É possível usar o {{site.data.keyword.cloudcerts_short}} para gerenciar os certificados SSL para seus apps e serviços baseados no {{site.data.keyword.Bluemix_notm}}. | [Eventos gerados pelo serviço {{site.data.keyword.cloudcerts_short}}](/docs/services/certificate-manager/at_events.html#at_events) |
| [{{site.data.keyword.keymanagementservicelong}}](/docs/services/key-protect/index.html#getting-started-with-key-protect) | É possível usar o serviço {{site.data.keyword.keymanagementserviceshort}} para provisionar chaves criptografadas para apps no {{site.data.keyword.Bluemix_notm}}. | [Eventos gerados pelo serviço {{site.data.keyword.keymanagementserviceshort}}](/docs/services/key-protect/at-events.html#at-events) |
{: caption="Lista de serviços de segurança do Cloud que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 


## Plataforma: serviços de armazenamento
{: #storage}

A tabela a seguir lista os serviços de armazenamento do Cloud que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}:

| Serviço     | Descrição | Eventos do {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [{{site.data.keyword.cos_full_notm}}](/docs/services/cloud-object-storage/about-cos.html#about-ibm-cloud-object-storage)| É possível usar o {{site.data.keyword.cos_full_notm}} para armazenar dados no {{site.data.keyword.Bluemix_notm}}. Os dados são criptografados e dispersados para
vários locais geográficos e acessados sobre HTTP usando uma API de REST. | [Eventos gerados pelo {{site.data.keyword.cos_full_notm}}](/docs/services/cloud-object-storage/basics/at.html#at_events) |  
{: caption="Lista de serviços de armazenamento do Cloud que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 



## Watson Platform: serviços de dados
{: #watson_data}


| Serviço     | Descrição | Eventos do {{site.data.keyword.cloudaccesstrailshort}} |
|-------------|-------------|-------------|
| [Watson Studio](https://dataplatform.cloud.ibm.com/docs/content/getting-started/overview-ws.html?context=analytics&linkInPage=true) | O Watson Studio fornece o ambiente e as ferramentas para resolver seus problemas de negócios, trabalhando de forma colaborativa com os dados. É possível escolher as ferramentas que você precisa para analisar e visualizar dados, para limpar e modelar dados, para alimentar os dados de fluxo ou para criar, treinar e implementar modelos de aprendizado de máquina. | [Eventos gerados pelo Watson Studio](https://dataplatform.cloud.ibm.com/docs/content/admin/at-events.html#ws) |  
| [ Watson Machine Learning ](https://dataplatform.cloud.ibm.com/docs/content/analyze-data/ml-overview.html?audience=dr&context=refinery)| É possível usar o Watson Machine Learning para construir modelos analíticos sofisticados, treinados com seus próprios dados, que podem ser implementados para uso em aplicativos. | [Eventos gerados pelo Watson Machine Learning](https://dataplatform.cloud.ibm.com/docs/content/admin/at-events.html#wml) | 
| [Watson Knowledge Catalog](https://dataplatform.cloud.ibm.com/docs/content/catalog/overview-wkc.html?audience=dr&context=refinery&linkInPage=true)| O Watson Knowledge Catalog fornece uma plataforma de gerenciamento de catálogo corporativo segura que é suportada por uma estrutura de política de dados. Um catálogo conecta dados e conhecimento às pessoas que precisam usá-lo. A estrutura de política de dados assegura que o acesso a dados seja compatível com suas regras de negócios. | [Eventos gerados pelo Watson Knowledge Catalog](https://dataplatform.cloud.ibm.com/docs/content/admin/at-events.html#wkc) |  
{: caption="Lista de serviços de dados do Watson Cloud que enviam eventos para o {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"} 


