---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, configure retention policy

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

# Configurando a política de retenção de eventos
{: #configuring_retention_policy}

Use o comando **ibmcloud at option** para visualizar e configurar a política de retenção que define o número máximo de dias que os eventos são mantidos no {{site.data.keyword.cloudaccesstrailshort}}. Por padrão, a política de retenção é desativada e os eventos são mantidos indefinidamente. Depois que o período de retenção tiver expirado, os eventos serão excluídos automaticamente. 
{:shortdesc}

O {{site.data.keyword.cloudaccesstrailfull}} foi descontinuado. A partir de 9 de maio de 2019, não é possível fornecer novas instâncias do {{site.data.keyword.cloudaccesstrailshort}}. As instâncias existentes do plano premium são suportadas até 30 de setembro de 2019. Para continuar o monitoramento da atividade de sua conta do {{site.data.keyword.cloud_notm}}, provisione uma instância do [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}


É possível configurar a mesma política de retenção para todos os espaços na conta ou você pode customizar o período de retenção para um espaço. 


## Desativando a política de retenção de evento para um espaço
{: #disable_retention_policy_space}

Conclua as etapas a seguir para desativar uma política de retenção:

1. Efetue login no {{site.data.keyword.cloud_notm}}. 

    Execute o comando [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) para efetuar login no {{site.data.keyword.cloud_notm}} e, em seguida, execute o comando [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) para configurar a organização e o espaço nos quais você deseja provisionar o serviço {{site.data.keyword.cloudaccesstrailshort}}.
	
2. Configure o período de retenção como **-1** para desativar o período de retenção. Execute o
comando:

    ```
    ibmcloud at option -r -1
    ```
    {: codeblock}
    
**Exemplo
**
    
Por exemplo, para desativar o período de retenção para um espaço com o ID *d35da1e3-b345-475f-8502-bx cfgh436902a3*, execute o comando a seguir:

```
ibmcloud at option -r -1
```
{: codeblock}

A saída é:

```
+-----------------------------------------+-----------+
|               SPACEID                   | RETENTION |
+-----------------------------------------+-----------+
| d35da1e3-b345-475f-8502-bx cfgh436902a3 |        -1 |
+-----------------------------------------+-----------+
```
{: screen} 



## Verificando a política de retenção de log de um espaço
{: #check_retention_policy_space}

Para obter o período de retenção configurado para um espaço do {{site.data.keyword.cloud_notm}}, conclua as etapas a seguir:

1. Efetue login no {{site.data.keyword.cloud_notm}}. 

    Execute o comando [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) para efetuar login no {{site.data.keyword.cloud_notm}} e, em seguida, execute o comando [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) para configurar a organização e o espaço nos quais você deseja provisionar o serviço {{site.data.keyword.cloudaccesstrailshort}}.
	
2. Obtenha o período de retenção. Execute o
comando:

    ```
    ibmcloud at option
    ```
    {: codeblock}

    A saída para o ID de espaço *d35da1e3-b345-475f-8502-bx cfgh436902a3* é de 30 dias:

    ```
    +-----------------------------------------+-----------+
    |               SPACEID                   | RETENTION |
    +-----------------------------------------+-----------+
    | d35da1e3-b345-475f-8502-bx cfgh436902a3 |        30 |
    +-----------------------------------------+-----------+
    ```
    {: screen}
    

## Verificando a política de retenção de log de todos os espaços em uma conta
{: #check_retention_policy_account}

Para obter o período de retenção configurado para cada espaço do {{site.data.keyword.cloud_notm}} em uma conta, conclua as etapas a seguir:

1. Efetue login no {{site.data.keyword.cloud_notm}}. 

    Execute o comando [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) para efetuar login no {{site.data.keyword.cloud_notm}} e, em seguida, execute o comando [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) para configurar a organização e o espaço nos quais você deseja provisionar o serviço {{site.data.keyword.cloudaccesstrailshort}}.
    
2. Obtenha o período de retenção de cada espaço na conta. Execute o
comando:

    ```
    ibmcloud at option -a
    ```
    {: codeblock}
	
	em que *-a* indica que as informações incluem todos os espaços na conta.

    Por exemplo, a saída da execução do comando é:

    ```
    +-----------------------------------------+-----------+
    |               SPACEID                   | RETENTION |
    +-----------------------------------------+-----------+
    | d35da1e3-b345-475f-8502-bx cfgh436902a3 |        30 |
    +-----------------------------------------+-----------+
    | fdew45e3-b345-4365-8502-bx cfghrfthy5a3 |        30 |
    +-----------------------------------------+-----------+
    ```
    {: screen}
    

## Configurando a política de retenção de log na conta
{: #set_retention_policy_space}

Para configurar o período de retenção para uma conta do {{site.data.keyword.cloud_notm}}, conclua as etapas a seguir:

1. Efetue login no {{site.data.keyword.cloud_notm}}. 

    Execute o comando [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) para efetuar login no {{site.data.keyword.cloud_notm}} e, em seguida, execute o comando [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) para configurar a organização e o espaço nos quais você deseja provisionar o serviço {{site.data.keyword.cloudaccesstrailshort}}.
	
2. Configure o período de retenção. Execute o
comando:

    ```
    ibmcloud at option -r Number_of_days - a
    ```
    {: codeblock}
    
    em que 
	* *-r* é a opção que deve ser especificada para configurar um período de retenção.
	* *Number_of_days* é um número inteiro que define o número de dias que você deseja manter os eventos. 
	* *-a* indica que a solicitação se aplica a todos os espaços na conta.
    
    
**Exemplo
**
    
Por exemplo, para manter qualquer tipo de log em sua conta por 15 dias apenas, execute o comando a seguir:

```
ibmcloud at option -r 15 -a
```
{: codeblock}

A saída lista uma entrada de cada espaço na conta, incluindo informações sobre o período de retenção:

```
+-----------------------------------------+-----------+
|               SPACEID                   | RETENTION |
+-----------------------------------------+-----------+
| d35da1e3-b345-475f-8502-bx cfgh436902a3 |        15 |
+-----------------------------------------+-----------+
| fdew45e3-b345-4365-8502-bx cfghrfthy5a3 |        15 |
+-----------------------------------------+-----------+
```
{: screen}

## Configurando a política de retenção de log de um espaço
{: #set_retention_policy_account}

Para ver o período de retenção de um espaço do {{site.data.keyword.cloud_notm}}, conclua as etapas a seguir:

1. Efetue login no {{site.data.keyword.cloud_notm}}. 

    Execute o comando [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) para efetuar login no {{site.data.keyword.cloud_notm}} e, em seguida, execute o comando [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) para configurar a organização e o espaço nos quais você deseja provisionar o serviço {{site.data.keyword.cloudaccesstrailshort}}.
    
2. Configure o período de retenção. Execute o
comando:

    ```
    ibmcloud at option -r Number_of_days
    ```
    {: codeblock}
    
    em que 
	* *-r* é a opção que deve ser especificada para configurar um período de retenção.
	* *Number_of_days* é um número inteiro que define o número de dias que você deseja manter os eventos.
    
    
**Exemplo
**
    
Por exemplo, para manter os eventos que estão disponíveis em um espaço por um ano, execute o comando a seguir:

```
ibmcloud at option -r 365
```
{: codeblock}

A saída é:

```
+-----------------------------------------+-----------+
|               SPACEID                   | RETENTION |
+-----------------------------------------+-----------+
| d35da1e3-b345-475f-8502-bx cfgh436902a3 |       365 |
+-----------------------------------------+-----------+
```
{: screen}


