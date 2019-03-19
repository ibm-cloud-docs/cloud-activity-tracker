---

copyright:
  years: 2016, 2019
lastupdated: "2019-01-23"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}



# Visualizando eventos
{: #view_acc_events}

É possível visualizar eventos por meio da IU do {{site.data.keyword.cloudaccesstrailshort}} no console do {{site.data.keyword.cloud_notm}} ou por meio do Kibana.
{:shortdesc}
   

## Visualizando eventos de conta
{: #view_acc_events_account_events}

É possível visualizar eventos em um domínio de contas do {{site.data.keyword.cloudaccesstrailshort}} por meio da IU do {{site.data.keyword.cloudaccesstrailshort}} ou por meio do Kibana.

Um **proprietário da conta** tem permissões para visualizar eventos em um domínio de contas do {{site.data.keyword.cloudaccesstrailshort}} por meio da IU do {{site.data.keyword.cloudaccesstrailshort}} ou por meio do Kibana.

Como um **membro em uma conta**, considere as informações a seguir para visualizar eventos de conta em uma região:

* Deve-se ter a função de *desenvolvedor* no espaço em que o {{site.data.keyword.cloudaccesstrailshort}} é provisionado. Para obter mais informações, consulte [Concedendo uma função do CF](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_cf_role).

* Deve-se ter uma política do IAM para o serviço {{site.data.keyword.loganalysisshort}} com a função de *visualizador* nessa região. A função de visualizador é a função mínima do IAM necessária. Para obter mais informações, consulte [Concedendo permissões do IAM](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_iam_policy).

* É possível visualizar eventos por meio do Kibana. Para obter mais informações sobre como ativar o Kibana, veja [Navegando para o Kibana de um navegador da web](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_kibana.html#launch_Kibana_from_browser).



## Visualizando eventos de espaço
{: #view_acc_events_space_events}

É possível visualizar eventos em um domínio de espaço do {{site.data.keyword.cloudaccesstrailshort}} por meio da IU do {{site.data.keyword.cloudaccesstrailshort}}. Se você tiver um plano premium, também será possível ver eventos por meio do Kibana.

Um **proprietário da conta** tem permissões para visualizar eventos para qualquer domínio de espaço do {{site.data.keyword.cloudaccesstrailshort}}.

Como um **membro em uma conta**, deve-se ter a função de *desenvolvedor* no espaço em que o {{site.data.keyword.cloudaccesstrailshort}} é provisionado.


