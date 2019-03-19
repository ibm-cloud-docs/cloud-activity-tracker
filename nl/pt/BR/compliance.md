---

copyright:
  years: 2016, 2019
lastupdated: "2019-01-23"

---


{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# Conformidade
{: #compliance}

[O {{site.data.keyword.Bluemix}} fornece uma plataforma de nuvem e serviços que são construídos para padrões de segurança rigorosos da IBM.](/docs/security/compliance.html#compliance). O serviço {{site.data.keyword.cloudaccesstraillong}} é um serviço DevOps construído para o {{site.data.keyword.cloud_notm}}. 
{:shortdesc}


## Regulamento Geral de Proteção de Dados

O General Data Protection Regulation (GDPR) procura criar uma estrutura harmonizada de lei de proteção de dados em toda a UE e visa devolver aos cidadãos o controle de seus dados pessoais, impondo regras rígidas aos que hospedam e 'processam' esses dados, em qualquer lugar do mundo. O regulamento também introduz regras relativas à livre circulação de dados pessoais dentro e fora da UE. 

**Renúncia de responsabilidade:** o serviço {{site.data.keyword.cloudaccesstrailshort}} armazena e exibe registros de eventos de recursos de nuvem que são executados em sua conta no {{site.data.keyword.cloud_notm}}. Informações pessoais (PI) não devem ser incluídas em nenhuma das entradas de eventos armazenadas no {{site.data.keyword.cloudaccesstrailshort}}, pois esses dados são acessíveis a outros usuários dentro de sua Empresa, bem como à {{site.data.keyword.IBM_notm}} para poder suportar o serviço do Cloud.

### Regiões
{: #compliance_regions}

O serviço {{site.data.keyword.cloudaccesstrailshort}} é compatível com o GDPR nas regiões do {{site.data.keyword.cloud_notm}} Public em que o serviço está disponível.


### Retenção de Dados
{: #compliance_data_retention}

O serviço {{site.data.keyword.cloudaccesstrailshort}} inclui dois repositórios de dados nos quais os dados do evento são armazenados: 

* Um repositório no qual os dados do evento estão disponíveis para análise por meio do Kibana. O plano padrão ou Lite armazena dados somente nesse repositório. Os dados são mantidos por 3 dias.
* Um repositório de armazenamento de longo prazo que hospeda os dados do evento para o plano premium. Os dados do evento são armazenados até que você configure uma política de retenção ou exclua-os manualmente. Por padrão, os eventos são mantidos indefinidamente.


### Exclusão de dados
{: #compliance_data_deletion}

Considere as informações a seguir:

* Eventos que são armazenados no repositório que fornece os dados para o Kibana são excluídos após 3 dias.

* Eventos que são armazenados no repositório de longo prazo são excluídos após vários dias ao configurar uma política de retenção ou ao excluí-los manualmente. 



Se você mudar de um plano pago para o plano padrão ou Lite, os eventos que estiverem no repositório de armazenamento de longo prazo serão excluídos em aproximadamente um dia.

A qualquer momento, é possível abrir um chamado de suporte e solicitar que todos os seus dados sejam excluídos. Para obter informações sobre como abrir um chamado de suporte IBM, veja [Entrando em contato com o suporte](/docs/get-support/howtogetsupport.html#getting-customer-support).



### Informações adicionais
{: #compliance_info}

Para obter mais informações, veja:

[{{site.data.keyword.cloud_notm}} conformidade de segurança](/docs/security/compliance.html#compliance)

[PIBR- {{site.data.keyword.IBM_notm}} oficial página](https://www.ibm.com/data-responsibility/gdpr/)



