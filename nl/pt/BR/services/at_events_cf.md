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


# Eventos do Cloud Foundry
{: #cf}

Use o serviço {{site.data.keyword.cloudaccesstrailfull}} para controlar a interação com os serviços principais de plataforma no {{site.data.keyword.Bluemix}}. 
{:shortdesc}


A lista a seguir descreve as diferentes tarefas principais da plataforma que enviam eventos para o serviço {{site.data.keyword.cloudaccesstrailshort}}: 

* Provisionando um serviço, removendo um serviço e mudando o nome de um serviço.
* Concedendo, atualizando e revogando funções de espaço do Cloud Foundry para usuários na conta.
* Criando uma chave API da plataforma, renomeando uma chave de plataforma e excluindo uma chave de plataforma.


## Eventos gerados ao interagir com serviços de catálogo
{: #cf_catalog}

Ao fornecer um serviço, remover um serviço e mudar o nome de um serviço, um evento é gerado e enviado para o domínio de espaço no {{site.data.keyword.cloudaccesstrailshort}} associado ao espaço do Cloud Foundry no qual o serviço está disponível na conta. 

Por exemplo, você provisiona o serviço A no espaço B na região us-south. Um evento é gerado. Para ver o evento, deve-se provisionar o serviço do {{site.data.keyword.cloudaccesstrailshort}} em us-south, no mesmo espaço em que você provisionou o serviço. Em seguida, é possível ver o evento por meio da IU de serviço do {{site.data.keyword.cloudaccesstrailshort}}.

A tabela a seguir lista as ações do catálogo que geram eventos:

<table>
  <caption>Ações de catálogo</caption>
  <tr>
    <th>Ação</th>
	  <th>Descrição</th>
  <tr>
  <tr>
    <td>`audit.service_instance.create`</td>
	<td>Um evento é criado quando você fornece um serviço em um espaço do Cloud Foundry.</td>
  </tr>
  <tr>
    <td>`audit.service_instance.update`</td>
	<td>Um evento é criado quando você muda o nome de um serviço que está disponível em um espaço do Cloud Foundry.</td>
  </tr>
  <tr>
    <td>`audit.service_instance.delete`</td>
	<td>Um evento é criado quando você remove um serviço de um espaço do Cloud Foundry na conta.</td>
  </tr>
</table>


 	

## Eventos gerados ao gerenciar funções do Cloud Foundry na conta
{: #cf_cfroles} 

Ao conceder ou revogar (excluir) uma função do Cloud Foundry para um usuário na conta, um evento é gerado e enviado para o domínio de espaço no {{site.data.keyword.cloudaccesstrailshort}} associado ao espaço do Cloud Foundry no qual a função é concedida ou revogada. 

Por exemplo, você concede ao usuário A, no espaço B da região Sul dos EUA, uma função de *gerenciador de espaço*. Um evento é gerado. Para ver o evento, deve-se provisionar o serviço {{site.data.keyword.cloudaccesstrailshort}} em us-south, no mesmo espaço em que você está gerenciando as permissões de CF do usuário. Em seguida, é possível ver o evento por meio da IU de serviço do {{site.data.keyword.cloudaccesstrailshort}}.


A tabela a seguir lista as ações que geram eventos do {{site.data.keyword.cloudaccesstrailshort}} quando você gerencia as funções do Cloud Foundry de um usuário:

<table>
  <caption>Ações de gerenciamento de funções do Cloud Foundry</caption>
  <tr>
    <th>Ação</th>
	<th>Descrição</th>
  <tr>
  <tr>
    <td>`audit.user.space_manager_add`</td>
	<td>Conceda a um usuário a função de *gerenciador* em um espaço do Cloud Foundry.</td>
  </tr>
  <tr>
    <td>`audit.user.space_developer_add`</td>
	<td>Conceda a um usuário a função de *desenvolvedor* em um espaço do Cloud Foundry.</td>
  </tr>
  <tr>
    <td>`audit.user.space_auditor_add`</td>
	<td>Conceda a um usuário a função de *auditoria* em um espaço do Cloud Foundry.</td>
  </tr>
  <tr>
    <td>`audit.user.space_manager_remove`</td>
	<td>Exclua a função de *gerenciador* do usuário em um espaço do Cloud Foundry.</td>
  </tr>
  <tr>
    <td>`audit.user.space_developer_remove`</td>
	<td>Exclua a função de *desenvolvedor* do usuário em um espaço do Cloud Foundry.</td>
  </tr>
  <tr>
    <td>`audit.user.space_auditor_remove`</td>
	<td>Exclua a função de *auditoria* do usuário em um espaço do Cloud Foundry.</td>
  </tr>
</table>






	
 	
 	
