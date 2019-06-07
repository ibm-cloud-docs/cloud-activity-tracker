---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, news

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

# O que Há de Novo
{: #whatsnew}

Aprenda sobre os recursos e integrações mais recentes para o {{site.data.keyword.cloudaccesstrailshort}}.
{:shortdesc}

O {{site.data.keyword.cloudaccesstrailfull}} foi descontinuado. A partir de 9 de maio de 2019, não é possível fornecer novas instâncias do {{site.data.keyword.cloudaccesstrailshort}}. As instâncias existentes do plano premium são suportadas até 30 de setembro de 2019. Para continuar o monitoramento da atividade de sua conta do {{site.data.keyword.cloud_notm}}, provisione uma instância do [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}

Para obter a lista mais recente de serviços que estão integrados com o {{site.data.keyword.cloudaccesstrailshort}}, consulte [Serviços de nuvem](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-cloud_services#cloud_services).
{: important}


## Março de 2019
{: #march2019}

* {{site.data.keyword.cloudaccesstrailshort}} CLI

Nós identificamos um problema com a CLI do Activity Tracker. Vamos liberar uma nova versão da CLI para resolver o problema.

Se você efetuar login no {{site.data.keyword.cloud_notm}} por meio da linha de comandos usando `ibmcloud login` e, então, executar comandos do {{site.data.keyword.cloudaccesstrailshort}}, obterá o erro a seguir `Failed: Unauthorized` para qualquer comando do {{site.data.keyword.cloudaccesstrailshort}} que executar. 

Enquanto isso, para continuar trabalhando com a CLI, efetue login no {{site.data.keyword.cloud_notm}} usando os comandos a seguir:

| Região | Comando: |
|--------|---------|
| `US South` | `bx login -a api.ng.bluemix.net -o OrgName -s SpaceName` |
| `EU DE`    | `bx login -a api.eu-de.bluemix.net -o OrgName -s SpaceName` |
| `EU DE`    | `bx login -a api.au-syd.bluemix.net -o OrgName -s SpaceName` |
{: caption="Tabela 1. Comandos" caption-side="top"} 

## Fevereiro de 2019
{: #february2019}

* **É possível monitorar o serviço do {{site.data.keyword.GlobalizationPipeline_short}} com o {{site.data.keyword.cloudaccesstrailshort}}.**

    O {{site.data.keyword.GlobalizationPipeline_short}} permite que os desenvolvedores de aplicativos liberem rapidamente os aplicativos traduzidos para clientes globais.

    Para obter mais informações sobre os eventos do {{site.data.keyword.cloudaccesstrailshort}}, consulte [Eventos que são gerados pelo {{site.data.keyword.GlobalizationPipeline_short}}](/docs/services/GlobalizationPipeline?topic=GlobalizationPipeline-gpat_events#gpat_events).








