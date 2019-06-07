---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, CLI

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
{:deprecated: .deprecated}


# CLI do IBM Cloud Activity Tracker
{: #at_cli_cloud}

É possível usar a CLI do {{site.data.keyword.cloudaccesstraillong}} para gerenciar eventos do {{site.data.keyword.cloudaccesstrailshort}}.
{: shortdesc}

O {{site.data.keyword.cloudaccesstrailfull}} foi descontinuado. A partir de 9 de maio de 2019, não é possível fornecer novas instâncias do {{site.data.keyword.cloudaccesstrailshort}}. As instâncias existentes do plano premium são suportadas até 30 de setembro de 2019. Para continuar o monitoramento da atividade de sua conta do {{site.data.keyword.cloud_notm}}, provisione uma instância do [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}


**Pré-requisitos**
* Antes de executar os comandos, efetue login no {{site.data.keyword.Bluemix}} com o comando `ibmcloud login` para gerar um token
de acesso e autenticar sua sessão.
* Para gerenciar eventos usando a CLI, deve-se ter um plano pago.

O plug-in CLI do {{site.data.keyword.cloudaccesstraillong}} suporta as plataformas Linux, Mac e Windows.

<table>
  <caption>Comandos para gerenciar o {{site.data.keyword.cloudaccesstrailshort}}</caption>
  <tr>
    <th>Comando:</th>
    <th>Quando utilizá-lo</th>
  </tr>
  <tr>
    <td>[ibmcloud at](#base)</td>
    <td>Use esse comando para obter informações sobre a CLI, como versão ou a lista de comandos.</td>
  </tr>
  <tr>
    <td>[ibmcloud at delete](#delete)</td>
    <td>Use este comando para excluir eventos do {{site.data.keyword.cloudaccesstrailshort}}.</td>
  </tr>
  <tr>
    <td>[ibmcloud at download](#download)</td>
    <td>Use este comando para fazer download de logs do {{site.data.keyword.cloudaccesstrailshort}} para um arquivo local. </td>
  </tr>
  <tr>
    <td>[ibmcloud at help](#help)</td>
    <td>Use este comando para obter ajuda sobre como usar a CLI e uma lista de todos os comandos.</td>
  </tr>
  <tr>
    <td>[ibmcloud at option](#option)</td>
    <td>Use esse comando para visualizar ou mudar as opções de evento do {{site.data.keyword.cloudaccesstrailshort}}, como a retenção, que estão disponíveis em um espaço ou em uma conta.</td>
  </tr>
  <tr>
    <td>[ibmcloud at session create](#session_create)</td>
    <td>Use esse comando para criar uma nova sessão.</td>
  </tr>
  <tr>
    <td>[ibmcloud at session delete](#session_delete)</td>
    <td>Use esse comando para excluir uma sessão.</td>
  </tr>  
  <tr>
    <td>[ibmcloud at session list](#session_list)</td>
    <td>Use esse comando para listar sessões ativas e seus IDs.</td>
  </tr>  
  <tr>
    <td>[ibmcloud at session show](#session_show)</td>
    <td>Use esse comando para mostrar o status de uma única sessão.</td>
  </tr>   
  <tr>
    <td>[ibmcloud at status](#status)</td>
    <td>Use este comando para visualizar informações sobre o status de eventos que são armazenamentos no {{site.data.keyword.cloudaccesstrailshort}}.</td>
  </tr>
  </table>


## ibmcloud at
{: #base}

Fornece informações sobre a versão da CLI e como usar a CLI.

```
ibmcloud at [parameters]
```
{: codeblock}

**Parâmetros**

<dl>
<dt>--help, -h</dt>
<dd>Configure esse parâmetro para mostrar a lista de comandos ou para obter ajuda para um comando.
</dd>

<dt>--version, -v</dt>
<dd>Configure esse parâmetro para imprimir a versão da CLI.</dd>
</dl>

**Exemplos**

Para obter a lista de comandos, execute o comando a seguir:

```
ibmcloud at --help
```
{: codeblock}

Para obter a versão da CLI, execute o comando a seguir:

```
ibmcloud at --version
```
{: codeblock}


## ibmcloud at delete
{: #delete}

Exclui eventos do {{site.data.keyword.cloudaccesstrailshort}}.

```
ibmcloud at delete [parameters] [arguments..]
```
{: codeblock}

**Parâmetros**

<dl>
  <dt>--start value, -s value</dt>
  <dd>(Opcional) Configura a data de início em Universal Coordinated Time (UTC): *YYYY-MM-DD*, por exemplo, `2017-01-02`. <br>O valor padrão é configurado como 2 semanas atrás. 
  </dd>
  
  <dt>--end value, -e value</dt>
  <dd>(Opcional) Configura a data de encerramento em Universal Coordinated Time (UTC): *AAAA-MM-DD* <br>O formato UTC da data é **AAAA-MM-DD**, por exemplo, `2017-01-02`. <br>O valor padrão é configurado como a data atual.
  </dd>
  
  <dt>--search-time value, -T value</dt>
  <dd>(Opcional) É possível configurar esse parâmetro para excluir eventos que são armazenados por um número de horas em um dia específico. O formato do campo é: 0-23
  </dd>

</dl>


**Exemplo
**

Para excluir os eventos para 22 de junho de 2017, execute o comando a seguir:
```
ibmcloud at delete -s 2017-06-22 -e 2017-06-22
```
{: codeblock}

Você recebe informações semelhantes à saída a seguir:

`Deleted successfully`
`"6 logs were deleted, freeing 13737 bytes."`


## ibmcloud at download
{: #download}

Faz download de eventos do {{site.data.keyword.cloudaccesstrailshort}} para um arquivo local ou os fluem para uma janela do terminal no Windows e Mac OS X ou para o stdout em um terminal Linux. 

**Nota:** para fazer download de arquivos, deve-se criar uma sessão primeiro. Uma sessão define de quais eventos fazer download com base no intervalo de data. Você faz download de eventos no contexto de uma sessão. 

```
ibmcloud at download [parameters] [arguments...]
```
{: codeblock}

**Parâmetros**

<dl>
<dt>--output value, -o value</dt>
<dd>(Opcional) Configura o caminho e o nome do arquivo para o arquivo de saída local no qual os eventos são transferidos por download. <br>O valor padrão é um hífen (-). <br>Configure esse parâmetro como o valor padrão para logs de saída para a saída padrão.</dd>
</dl>

**Argumentos**

<dl>
<dt>ID de sessão</dt>
<dd>Configure o valor de ID de sessão que você obterá ao executar o comando `ibmcloud at session create`. Esse valor indica qual sessão usar ao fazer download de eventos. <br>**Nota:** o comando `ibmcloud at session create` fornece os parâmetros que controlam quais eventos são transferidos por download. </dd>
</dl>

**Nota:** após a conclusão do download, para fazer download dos mesmos dados novamente, deve-se usar um arquivo diferente ou uma sessão diferente.

**Exemplo
**

Para fazer download de eventos em um arquivo chamado `events.log`, execute o comando a seguir:

```
ibmcloud at download -o events.log 1db6ce16-824d-4d50-bd40-37f1d8fea9b7
```
{: screen}

Você recebe informações semelhantes à saída a seguir: 

```
6.70 KiB / 3.06 KiB [========] 219.03% 8.60 MiB/s 0s
Download completed successfully
```
{: screen}


## ibmcloud at help
{: #help}

Fornece informações sobre como usar um comando.

```
ibmcloud at help [parameters]
```
{: codeblock}

**Parâmetros**

<dl>
<dt>Comando:</dt>
<dd>Configure o nome do comando para o qual você deseja obter ajuda.
</dd>
</dl>


**Exemplo
**

Para obter ajuda sobre como executar o comando para visualizar o status do {{site.data.keyword.cloudaccesstrailshort}}, execute o comando a seguir:

```
ibmcloud at help status
```
{: codeblock}


## ibmcloud at option
{: #option}

Exibe ou muda o período de retenção para eventos que estão disponíveis em um espaço. Quando você configura uma política de retenção, os eventos são excluídos automaticamente quando o número de dias de retenção é atingido.

* O período é configurado em número de dias.
* O valor padrão é **-1**, ou seja, os eventos são armazenados e não excluídos.

**Nota:** por padrão, todos os eventos são armazenados. Se você não configurar um período de retenção, deverá excluí-los manualmente usando o comando `ibmcloud at delete`. 

```
ibmcloud at option [parameters] [arguments...]
```
{: codeblock}

**Parâmetros**

<dl>
<dt>--retention value, -r value</dt>
<dd>(Opcional) Configura o número de dias de retenção. <br> O valor padrão é *-1* dias.</dd>

<dt>--at-account-level, -a</dt>
<dd>(Opcional) Configure esse parâmetro para listar informações sobre o período de retenção para eventos que são armazenados em cada domínio de espaço e no domínio de contas.

</dl>

**Exemplo
**

Para ver o período de retenção atual do espaço ao qual você está conectado, execute o comando a seguir:

```
ibmcloud at option
```
{: codeblock}

A saída é semelhante à saída a seguir:

```
+--------------------------------------+-----------+
|               SPACEID                | RETENTION |
+--------------------------------------+-----------+
| 2af890ce-fb4f-4e41-a975-901a56ed1f11 |        30 |
+--------------------------------------+-----------+
```
{: screen}


Para mudar o período de retenção para 25 dias do espaço ao qual você está conectado, execute o comando a seguir:

```
ibmcloud at option -r 25
```
{: codeblock}

A saída é semelhante à saída a seguir:

```
+--------------------------------------+-----------+
|               SPACEID                | RETENTION |
+--------------------------------------+-----------+
| 2af890ce-fb4f-4e41-a975-901a56ed1f11 |        25 |
+--------------------------------------+-----------+
```
{: screen}



## ibmcloud at session create
{: #session_create}

Cria uma nova sessão.

**Nota:** é possível ter até 30 sessões simultâneas em um espaço. A sessão é criada para um usuário. As sessões não podem ser compartilhadas entre usuários em um espaço.

```
ibmcloud at session create [parameters] [arguments...]
```
{: codeblock}

**Parâmetros**

<dl>
  <dt>--at-account-level, -a </dt>
  <dd>(Opcional) Configura o escopo como nível de conta. </br>Configure esse valor para obter informações da conta. <br>Se esse parâmetro não for especificado, o valor padrão será definido somente para o espaço atual,
ou seja, o espaço no qual você efetuou login usando o comando `ibmcloud cf login`.
  </dd>

  <dt>--start value, -s value</dt>
  <dd>(Opcional) Configura a data de início em Universal Coordinated Time (UTC): *YYYY-MM-DD*, por exemplo, `2017-01-02`. <br>O valor padrão é configurado como 2 semanas atrás. 
  </dd>
  
  <dt>--end value, -e value</dt>
  <dd>(Opcional) Configura a data de encerramento em Universal Coordinated Time (UTC): *YYYY-MM-DD*, por exemplo, `2017-01-02`. <br>O valor padrão é configurado como a data atual. 
  </dd>

  <dt>--search-time value, -T value</dt>
  <dd>(Opcional) É possível configurar esse parâmetro para excluir eventos que são armazenados por um número de horas em um dia específico. O formato do campo é: 0-23
  </dd>


 </dl>

**Valores Retornados**

<dl>
<dt>Access-Time</dt>
<dd>Registro de data e hora que indica quando a sessão foi usada pela última vez.</dd>

<dt>Create-Time</dt>
<dd>O registro de data e hora que corresponde à data e hora em que a sessão foi criada.</dd>

<dt>Date-Range</dt>
<dd>Indica os dias que são usados para filtrar eventos. Os eventos que são identificados nesse intervalo de data estão disponíveis para gerenciamento por meio da sessão.</dd>

<dt>ID</dt>
<dd>ID de Sessão.</dd>

<dt>Space</dt>
<dd>O ID do espaço no qual a sessão está ativa.</dd>

<dt>Type-Account</dt>
<dd>Esse valor é configurado para **ActivityTracker**.</dd>

<dt>Username</dt>
<dd>{{site.data.keyword.IBM_notm}}ID do usuário que criou a sessão.</dd>
</dl>


**Exemplo
**

Para criar uma sessão para 10 de julho de 2017, execute o comando a seguir:

```
ibmcloud at session create -s 2017-07-10 -e 2017-07-10
```
{: screen}

A saída é semelhante à saída a seguir:

```
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| id           | 9b8c4db8-5841-4993-a449-305815a53a8e      |
| space        | xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx      |
| username     | xxx@yyy.com                               |
| create-time  | 2017-07-25T11:54:00.20042645Z             |
| access-time  | 2017-07-25T11:54:00.20042645Z             |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
+--------------+-------------------------------------------+
```
{: screen}



## ibmcloud at session delete
{: #session_delete}

Exclui uma sessão que é especificada pelo ID de sessão.

```
ibmcloud at session delete [arguments...]
```
{: codeblock}


**Argumentos**

<dl>
<dt>ID de sessão</dt>
<dd>ID da sessão que você deseja excluir. <br>É possível usar o comando `ibmcloud at session list` para obter todos os IDs de sessão ativos.</dd>
</dl>

**Exemplo
**

Para excluir uma sessão com ID de sessão *9b8c4db8-5841-4993-a449-305815a53a8e*, execute o comando a seguir:

```
ibmcloud at session delete 9b8c4db8-5841-4993-a449-305815a53a8e
```
{: screen}

A saída é semelhante à saída a seguir:

```
+---------------+--------------------------+
|    NAME       |     VALUE                |
+---------------+--------------------------+
|  message      | Delete session success   |
+---------------+--------------------------+
```
{: screen}


## ibmcloud at session list
{: #session_list}

Lista as sessões ativas e seus IDs.

```
ibmcloud at session list 
```
{: codeblock}

**Valores Retornados**

<dl>
<dt>ID</dt>
<dd>ID de Sessão.</dd>

<dt>SPACE</dt>
<dd>O ID do espaço no qual a sessão está ativa.</dd>

<dt>USERNAME</dt>
<dd>{{site.data.keyword.IBM_notm}}ID do usuário que criou a sessão.</dd>

<dt>CREATE-TIME</dt>
<dd>O registro de data e hora que corresponde à data e hora em que a sessão foi criada.</dd>

<dt>ACCESS-TIME</dt>
<dd>O registro de data e hora que indica quando a sessão foi usada pela última vez.</dd>
</dl>
 
**Exemplo
**

Para listar as sessões, execute o comando a seguir:

```
ibmcloud at session list
```
{: screen}

A saída é semelhante à saída a seguir:

```
+--------------------------------------+--------------------------------------+-----------------------------------+--------------------------------+--------------------------------+
| ID                                   | SPACE                                | USERNAME                          | CREATE-TIME                    | ACCESS-TIME                    |
+--------------------------------------+--------------------------------------+-----------------------------------+--------------------------------+--------------------------------+
| fa3f1970-21f3-4e32-b480-1ffb41badc16 | 12345678-fb4f-acdf-a975-11335678r3fg | xxx@yyy.com                       | 2017-07-10T09:04:07.916788069Z | 2017-07-10T09:04:07.916788069Z |
| 9b8c4db8-5841-4993-a449-305815a53a8e | 12345678-fb4f-acdf-a975-11335678r3fg | xxx@yyy.com                       | 2017-07-11T09:19:14.666532796Z | 2017-07-12T09:19:14.666532796Z |
+--------------------------------------+--------------------------------------+-----------------------------------+--------------------------------+--------------------------------+
```
{: screen}


## ibmcloud at session show
{: #session_show}

Mostra o status de uma sessão única.

```
ibmcloud at session show [arguments...]
```
{: codeblock}

**Argumentos**

<dl>
<dt>ID de sessão</dt>
<dd>ID da sessão ativa da qual você deseja obter informações.</dd>
</dl>

**Valores Retornados**

<dl>
<dt>Access-Time</dt>
<dd>O registro de data e hora que indica quando a sessão foi usada pela última vez.</dd>

<dt>Create-Time</dt>
<dd>O registro de data e hora que corresponde à data e hora em que a sessão foi criada.</dd>

<dt>Date-Range</dt>
<dd>Indica os dias que são usados para filtrar eventos. Os eventos que são identificados nesse intervalo de data estão disponíveis para gerenciamento por meio da sessão.</dd>

<dt>id</dt>
<dd>ID de Sessão.</dd>

<dt>Space</dt>
<dd>O ID do espaço no qual a sessão está ativa.</dd>

<dt>Type-Account</dt>
<dd>Esse valor é configurado para **ActivityTracker**.</dd>

<dt>Username</dt>
<dd>{{site.data.keyword.IBM_notm}}ID do usuário que criou a sessão.</dd>
</dl>

**Exemplo
**

Para mostrar detalhes de uma sessão com ID de sessão *9b8c4db8-5841-4993-a449-305815a53a8e*, execute o comando a seguir:

```
ibmcloud at session show 9b8c4db8-5841-4993-a449-305815a53a8e
```
{: screen}

A saída é semelhante à saída a seguir:

```
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| create-time  | 2017-07-25T11:54:00.20042645Z             |
| access-time  | 2017-07-25T11:54:00.20042645Z             |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
| id           | 9b8c4db8-5841-4993-a449-305815a53a8e      |
| space        | xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx      |
| username     | xxx@yyy.com                               |
+--------------+-------------------------------------------+
```
{: screen}


## ibmcloud at status
{: #status}

Retorna informações sobre o status de eventos do {{site.data.keyword.cloudaccesstrailshort}}.

```
ibmcloud at status [parameters] [arguments...]
```
{: codeblock}

**Parâmetros**

<dl>
  <dt>--start value, -s value</dt>
  <dd>(Opcional) Configura a data de início em Universal Coordinated Time (UTC): *YYYY-MM-DD*, por exemplo, `2017-01-02`. <br>O valor padrão é configurado como 2 semanas atrás.
  </dd>
  
  <dt>--end value, -e value</dt>
  <dd>(Opcional) Configura a data de encerramento em Universal Coordinated Time (UTC): *YYYY-MM-DD*, por exemplo, `2017-01-02`. <br>O valor padrão é configurado como a data atual.
  </dd>
  
  <dt>--at-account-level, -a </dt>
  <dd>(Opcional) Configura o escopo como nível de conta. <br> **Nota:** configure esse valor para obter dados da conta. <br>Se esse parâmetro não for especificado, o valor padrão será definido somente para o espaço atual,
ou seja, o espaço no qual você efetuou login usando o comando `ibmcloud cf login`.
  </dd>
  
</dl>


**Nota:** o comando `ibmcloud at status` relata somente as duas últimas semanas de eventos que estão armazenados no {{site.data.keyword.cloudaccesstrailshort}} quando nenhuma data de início nem de encerramento é especificada. 

**Valores Retornados**   

<dl>
  <dt>DATE</dt>
  <dd>Data em Universal Coordinated Time (UTC): *YYYY-MM-DD*, por exemplo, `2017-01-02`. 
  </dd>
  
  <dt>COUNT</dt>
  <dd>Número total de eventos.
  </dd>
  
  <dt>SIZE</dt>
  <dd>O tamanho total de eventos em megabytes.
  </dd>

  <dt>TYPES</dt>
  <dd>Esse valor é configurado para **ActivityTracker**.
  </dd>
  
  <dt>SEARCHABLE</dt>
  <dd>Este campo indica se os eventos estão disponíveis para procura no Kibana. <br>Quando o valor do campo **SEARCHABLE** for configurado como *Nenhum*, então, os eventos ficarão disponíveis para download, mas não será possível analisá-los no Kibana.
  </dd>
  
</dl>

**Exemplo
**

Para mostrar detalhes de eventos em 20 de julho de 2017, execute o comando a seguir:

```
ibmcloud at status -s 2017-07-20 -e 2017-07-20
```
{: codeblock}


Você recebe informações semelhantes à saída a seguir:

```
+------------+-----------+-------+------------------+--------------+
|   Date     |  Count    | Size  | Types            |  Searchable  |
+------------+-----------+-------+------------------+--------------+
| 2017-07-20 |    1      | 2531  | ActivityTracker  | All          |
+------------+-----------+-------+------------------+--------------+
```
{: screen}


