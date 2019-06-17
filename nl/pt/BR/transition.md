---

copyright:
  years: 2016, 2019
lastupdated: "2019-06-06"

keywords: IBM Cloud, Activity Tracker, migration

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


# Executando a transição para o {{site.data.keyword.at_full_notm}}
{: #transition}

O {{site.data.keyword.cloudaccesstrailfull}} foi descontinuado em 9 de maio de 2019. [Saiba mais](https://www.ibm.com/blogs/cloud-archive/2019/04/deprecating-ibm-cloud-activity-tracker/). O serviço foi substituído por {{site.data.keyword.at_full_notm}}. [Saiba mais](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started).
{:shortdesc}

O {{site.data.keyword.cloudaccesstrailfull}} foi descontinuado. A partir de 9 de maio de 2019, não é possível fornecer novas instâncias do {{site.data.keyword.cloudaccesstrailshort}}. As instâncias existentes do plano premium são suportadas até 30 de setembro de 2019. Para continuar o monitoramento da atividade de sua conta do {{site.data.keyword.cloud_notm}}, provisione uma instância do [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}


Conclua as etapas a seguir para migrar para o {{site.data.keyword.at_full_notm}}: 

1. Salve uma cópia dos eventos que estão armazenados no {{site.data.keyword.cloudaccesstrailfull}} para procura de longo prazo. É possível usar a CLI ou a API do {{site.data.keyword.cloudaccesstrailshort}}. 

    Certifique-se de salvar os eventos de espaço para cada espaço do Cloud Foundry no qual você tenha uma instância anterior do {{site.data.keyword.cloudaccesstrailshort}} e para cada nome de domínio em cada região que estiver monitorando atualmente.

    * [Fazendo download de eventos usando a CLI](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-downloading_events).

    * [Fazendo download de eventos usando a API](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-downloading_events_api).

2. Provisione o [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-provision).

    É possível provisionar somente uma instância por região. 
    
3. Crie e configure grupos de acesso para gerenciar permissões no {{site.data.keyword.cloud_notm}}. 

    * [Concedendo permissões de administração para um ID de usuário ou de serviço](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-iam_manage_events).

    * [Concedendo permissões de usuário para um ID de usuário ou de serviço](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-iam_view_events).

4. Defina as visualizações e os painéis no {{site.data.keyword.at_full_notm}} para analisar e gerenciar eventos. [Saiba mais](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-views).

    A migração de painéis do Kibana para painéis de LogDNA não é automatizada. É necessário implementar os novos painéis manualmente. 

    Observe que no LogDNA, os histogramas e as pizzas são as únicas visualizações que podem ser implementadas.

5. [Opcional] Configure o arquivamento para a instância do {{site.data.keyword.at_full_notm}}. 

    É possível arquivar eventos no {{site.data.keyword.cos_full_notm}} (COS). [Saiba mais](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-archiving).

    **Nota:** você é responsável por provisionar uma instância do COS usada para arquivar eventos e por manter os eventos arquivados. 

    Essa etapa é necessária apenas para as instâncias do {{site.data.keyword.at_full_notm}} que têm um plano pago.

6. Explore outros recursos como o [alerta](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-alerts).


Quando você estiver pronto para parar o monitoramento da atividade do Cloud por meio de suas instâncias anteriores do {{site.data.keyword.cloudaccesstrailshort}}, conclua as etapas a seguir:

1. Exclua as instâncias anteriores do {{site.data.keyword.cloudaccesstrailshort}} do console do {{site.data.keyword.cloud_notm}}.
2. Remova qualquer permissão para os usuários trabalharem com essas instâncias anteriores. 


