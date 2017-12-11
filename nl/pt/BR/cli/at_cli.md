---

copyright:

  years: 2016, 2017

lastupdated: "2017-09-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# CLI do IBM Cloud Activity Tracker
{: #at_cli}

A CLI do {{site.data.keyword.cloudaccesstraillong}} é um plug-in CF que pode ser usado para gerenciar eventos do {{site.data.keyword.cloudaccesstrailshort}}.
{: shortdesc}

**Pré-requisitos**
* Antes de executar os comandos, efetue login no {{site.data.keyword.Bluemix}} com o comando `cf login` para gerar um token de acesso do {{site.data.keyword.Bluemix_short}}
e autenticar sua sessão.

Para descobrir sobre como usar a CLI do {{site.data.keyword.cloudaccesstrailshort}}, veja [Gerenciando eventos do {{site.data.keyword.cloudaccesstrailshort}} por meio da CLI](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#managing_events). 

O plug-in CLI do {{site.data.keyword.cloudaccesstraillong}} suporta as plataformas Linux, Mac e Windows.

<table>
  <caption>Comandos para gerenciar o {{site.data.keyword.cloudaccesstrailshort}}</caption>
  <tr>
    <th>Comando:</th>
    <th>Quando utilizá-lo</th>
  </tr>
  <tr>
    <td>[cf at](#base)</td>
    <td>Use esse comando para obter informações sobre a CLI, como versão ou a lista de comandos.</td>
  </tr>
  <tr>
    <td>[cf at delete](#delete)</td>
    <td>Use este comando para excluir eventos do {{site.data.keyword.cloudaccesstrailshort}}.</td>
  </tr>
  <tr>
    <td>[cf at download](#download)</td>
    <td>Use este comando para fazer download de logs do {{site.data.keyword.cloudaccesstrailshort}} para um arquivo local. </td>
  </tr>
  <tr>
    <td>[cf at help](#help)</td>
    <td>Use este comando para obter ajuda sobre como usar a CLI e uma lista de todos os comandos.</td>
  </tr>
  <tr>
    <td>[cf at option](#option)</td>
    <td>Use este comando para visualizar ou mudar as opções de eventos do {{site.data.keyword.cloudaccesstrailshort}}, como a retenção, que estão disponíveis em um espaço ou conta do {{site.data.keyword.Bluemix_notm}}.</td>
  </tr>
  <tr>
    <td>[cf at session create](#session_create)</td>
    <td>Use esse comando para criar uma nova sessão.</td>
  </tr>
  <tr>
    <td>[cf at session delete](#session_delete)</td>
    <td>Use esse comando para excluir uma sessão.</td>
  </tr>  
  <tr>
    <td>[cf at session list](#session_list)</td>
    <td>Use esse comando para listar sessões ativas e seus IDs.</td>
  </tr>  
  <tr>
    <td>[cf at session show](#session_show)</td>
    <td>Use esse comando para mostrar o status de uma única sessão.</td>
  </tr>   
  <tr>
    <td>[cf at status](#status)</td>
    <td>Use este comando para visualizar informações sobre o status de eventos que são armazenamentos no {{site.data.keyword.cloudaccesstrailshort}}.</td>
  </tr>
  <tr>
    <td>[cf at trail](#trail)</td>
    <td>Use este comando para enviar eventos para o {{site.data.keyword.cloudaccesstrailshort}}.</td>
  </tr>
  </table>


## cf at
{: #base}

Fornece informações sobre a versão da CLI e como usar a CLI.

```
cf at [parameters]
```
{: codeblock}

**Parâmetros**

<dl>
<dt>-- help, -h</dt>
<dd>Configure esse parâmetro para mostrar a lista de comandos ou para obter ajuda para um comando.
</dd>

<dt>-- versão, -v</dt>
<dd>Configure esse parâmetro para imprimir a versão da CLI.</dd>
</dl>

**Exemplos**

Para obter a lista de comandos, execute o comando a seguir:

```
cf at --help
```
{: codeblock}

Para obter a versão da CLI, execute o comando a seguir:

```
cf at --version
```
{: codeblock}


## cf at delete
{: #delete}

Exclui eventos do {{site.data.keyword.cloudaccesstrailshort}}.

```
cf at delete [parameters] [arguments..]
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
  
</dl>

**Exemplo
**

Para excluir os eventos para 22 de junho de 2017, execute o comando a seguir:
```
cf at delete -s 2017-06-22 -e 2017-06-22
```
{: codeblock}

Você recebe informações semelhantes à saída a seguir:

`Excluído com êxito`
`"6 logs foram excluídos, liberando 13737 bytes."`


## cf at download
{: #download}

Faz download de eventos do {{site.data.keyword.cloudaccesstrailshort}} para um arquivo local ou os fluem para uma janela do terminal no Windows e Mac OS X ou para o stdout em um terminal Linux. 

**Nota:** para fazer download de arquivos, deve-se criar uma sessão primeiro. Uma sessão define de quais eventos fazer download com base no intervalo de data. Você faz download de eventos no contexto de uma sessão. Para obter mais informações, veja [cf at session create](/docs/services/CloudActivityTracker/reference/at_cli.html#session_create).

```
cf at download [parameters] [arguments...]
```
{: codeblock}

**Parâmetros**

<dl>
<dt>-- output valor, -o valor</dt>
<dd>(Opcional) Configura o caminho e o nome do arquivo para o arquivo de saída local para o qual os eventos são transferidos por download. <br>O valor padrão é um hífen (-). <br>Configure esse parâmetro como o valor padrão para logs de saída para a saída padrão.</dd>
</dl>

**Argumentos**

<dl>
<dt>ID de sessão</dt>
<dd>Configure o valor do ID de sessão obtido ao executar o comando `cf at session create`. Esse valor indica qual sessão usar ao fazer download de eventos. <br>**Nota:** o comando `cf at session create` fornece os parâmetros que controlam quais eventos são transferidos por download. </dd>
</dl>

**Nota:** após a conclusão do download, para fazer download dos mesmos dados novamente, deve-se usar um arquivo diferente ou uma sessão diferente.

**Exemplo
**

Para fazer download de eventos em um arquivo chamado `events.log`, execute o comando a seguir:

```
cf at download -o events.log 1db6ce16-824d-4d50-bd40-37f1d8fea9b7
```
{: screen}

Você recebe informações semelhantes à saída a seguir: 

```
6.70 KiB / 3.06 KiB [========] 219.03% 8.60 MiB/s 0s
Download concluído com êxito
```
{: screen}


## cf at help
{: #help}

Fornece informações sobre como usar um comando.

```
cf at help [parameters]
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
cf at help status
```
{: codeblock}


## cf at option
{: #option}

Exibe ou muda o período de retenção para eventos que estão disponíveis em um espaço do {{site.data.keyword.Bluemix_notm}}. Quando você configura uma política de retenção, os eventos são excluídos automaticamente quando o número de dias de retenção é atingido.

* O período é configurado em número de dias.
* O valor padrão é **-1**, ou seja, os eventos são armazenados e não excluídos.

**Nota:** por padrão, todos os eventos são armazenados. Se você não configura um período de retenção, deve-se excluí-los manualmente usando o comando `cf at delete`. 

```
cf at option [parameters] [arguments...]
```
{: codeblock}

**Parâmetros**

<dl>
<dt>--retention value, -r value</dt>
<dd>(Opcional) Configura o número de dias de retenção. <br> O valor padrão é *-1* dias.</dd>

</dl>

**Exemplo
**

Para ver o período de retenção atual do espaço ao qual você está conectado, execute o comando a seguir:

```
cf at option
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
cf at option -r 25
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



## cf at session create
{: #session_create}

Cria uma nova sessão.

**Nota:** é possível ter até 30 sessões simultâneas em um espaço. A sessão é criada para um usuário. As sessões não podem ser compartilhadas entre usuários em um espaço.

```
cf at session create [parameters] [arguments...]
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
 </dl>

**Valores Retornados**

<dl>
<dt>Tempo de acesso</dt>
<dd>Registro de data e hora que indica quando a sessão foi usada pela última vez.</dd>

<dt>Horário da criação</dt>
<dd>O registro de data e hora que corresponde à data e hora em que a sessão foi criada.</dd>

<dt>Data-Intervalo</dt>
<dd>Indica os dias que são usados para filtrar eventos. Os eventos que são identificados nesse intervalo de data estão disponíveis para gerenciamento por meio da sessão.</dd>

<dt>ID</dt>
<dd>ID de Sessão.</dd>

<dt>Espaço</dt>
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
cf at session create -s 2017-07-10 -e 2017-07-10
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



## cf at session delete
{: #session_delete}

Exclui uma sessão que é especificada pelo ID de sessão.

```
cf at session delete [arguments...]
```
{: codeblock}


**Argumentos**

<dl>
<dt>ID de sessão</dt>
<dd>ID da sessão que você deseja excluir. <br>É possível usar o comando `cf at session list` para obter todos os IDs de sessão ativa.</dd>
</dl>

**Exemplo
**

Para excluir uma sessão com ID de sessão *9b8c4db8-5841-4993-a449-305815a53a8e*, execute o comando a seguir:

```
cf at session delete 9b8c4db8-5841-4993-a449-305815a53a8e
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


## cf at session list
{: #session_list}

Lista as sessões ativas e seus IDs.

```
cf at session list 
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
cf at session list
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


## cf at session show
{: #session_show}

Mostra o status de uma sessão única.

```
cf at session show [arguments...]
```
{: codeblock}

**Argumentos**

<dl>
<dt>ID de sessão</dt>
<dd>ID da sessão ativa da qual você deseja obter informações.</dd>
</dl>

**Valores Retornados**

<dl>
<dt>Tempo de acesso</dt>
<dd>O registro de data e hora que indica quando a sessão foi usada pela última vez.</dd>

<dt>Horário da criação</dt>
<dd>O registro de data e hora que corresponde à data e hora em que a sessão foi criada.</dd>

<dt>Data-Intervalo</dt>
<dd>Indica os dias que são usados para filtrar eventos. Os eventos que são identificados nesse intervalo de data estão disponíveis para gerenciamento por meio da sessão.</dd>

<dt>id</dt>
<dd>ID de Sessão.</dd>

<dt>Espaço</dt>
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
cf at session show 9b8c4db8-5841-4993-a449-305815a53a8e
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


## cf at status
{: #status}

Retorna informações sobre o status de eventos do {{site.data.keyword.cloudaccesstrailshort}}.

```
cf at status [parameters] [arguments...]
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
  <dd>(Opcional) Configura o escopo como nível de conta. <br> **Nota:** configure esse valor para obter dados da conta. <br>Se esse parâmetro não estiver especificado, o valor padrão será configurado somente com o espaço atual, isto é, o espaço em que você efetuou login usando o comando `cf login`.
  </dd>
  
</dl>


**Nota:** o comando `cf at status` relata somente as últimas duas semanas de eventos que são armazenados no {{site.data.keyword.cloudaccesstrailshort}} quando nenhuma data de início e de encerramento é especificada. 

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
  <dd>Este campo indica se os eventos estão disponíveis para procura no Kibana. <br>Quando o valor do campo **SEARCHABLE** é configurado para *None*, os eventos estão disponíveis para download, mas não é possível analisá-los no Kibana.
  </dd>
  
</dl>

**Exemplo
**

Para mostrar detalhes de eventos em 20 de julho de 2017, execute o comando a seguir:

```
cf at status -s 2017-07-20 -e 2017-07-20
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



## cf at trail
{: #trail}

Envie eventos serializado para o {{site.data.keyword.cloudaccesstrailshort}}.

```
cf at trail [parameters] [arguments...]
```
{: codeblock}

**Parâmetros**

<dl>
  <dt>--file FILE, -f FILE</dt>
  <dd>(Opcional) Especifique o arquivo de eventos no formato: `PATH/filename`
  </dd>
  
  <dt>--type FORMAT, -t FORMAT</dt>
  <dd>(Opcional) Especifique o formato dos eventos que são incluídos no arquivo. Os valores válidos são: *cadf* e *kong*. <br> Use *CADF* para enviar eventos que obedecem ao formato CADF. Use *KONG* para enviar eventos que obedecem ao formato Kong. <br> **Nota:** é possível enviar somente eventos do mesmo tipo em um arquivo.
  </dd>
 </dl>
 
**Exemplo
**

Para enviar eventos CADF serializados para o {{site.data.keyword.cloudaccesstrailshort}}, execute o comando a seguir:

```
cf at trail -t cadf -f events.log
```
{: codeblock}

em que *events.log* é o arquivo que contém os eventos que você deseja enviar para o {{site.data.keyword.cloudaccesstrailshort}}. Esse arquivo inclui eventos que obedecem ao formato CADF.

Você recebe informações semelhantes à saída a seguir:

```
+--------------------------------------+---------------------------+
|            ID                        |          Value            |
+--------------------------------------+---------------------------+
| bbb170dc-2b0a-42d4-b560-b416f3308869 | B0UtwP1FhemsZIr4rTJVKA==  |
+--------------------------------------+---------------------------+
| 688f1194-2305-4367-8ece-f468e67c19fb | KLCG9f++usNolgvutRCR1Q==  |
+--------------------------------------+---------------------------+
```
{: screen}
