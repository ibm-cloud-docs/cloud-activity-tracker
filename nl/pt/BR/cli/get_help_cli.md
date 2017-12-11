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

# Obtendo ajuda sobre como usar a CLI do Activity Tracker
{: #get_help_cli}

A CLI do {{site.data.keyword.cloudaccesstrailshort}} oferece diferentes tipos de ajuda: ajuda geral para aprender sobre a CLI e comandos suportados, ajuda de comando para aprender como usar um comando ou ajuda de subcomando para aprender como usar um subcomando para um comando.
{:shortdesc}


## Obtendo ajuda geral
{: #general_cli_help}

Para obter informações gerais sobre a CLI e quais comandos são suportados, conclua as etapas a seguir:

1. Efetue login em uma região, uma organização e um espaço do {{site.data.keyword.Bluemix_notm}}. 

    Por exemplo, para efetuar login na região sul dos EUA, execute o comando a seguir:
	
	```
    bx login -a https://api.ng.bluemix.net
    ```
    {: codeblock}
    
2. Liste informações sobre os comandos suportados e a CLI. Execute o seguinte comando:

    ```
    bx cf at help 
    ```
    {: codeblock}
    
    

## Obtendo ajuda sobre um comando
{: #command_cli_help}

Para obter ajuda sobre como usar um comando, conclua as etapas a seguir:

1. Efetue login em uma região, uma organização e um espaço do {{site.data.keyword.Bluemix_notm}}. 

    Por exemplo, para efetuar login na região sul dos EUA, execute o comando a seguir:
	
	```
    bx login -a https://api.ng.bluemix.net
    ```
    {: codeblock}
    
2. Obtenha a lista de comandos suportados e identifique aquele que você precisa. Execute o
comando:

    ```
    bx cf at help 
    ```
    {: codeblock}

3. Obter ajuda sobre o comando. Execute o seguinte comando:

    ```
    bx cf at help *Command*
    ```
    {: codeblock}
    
    em que *Command* é o nome de um comando da CLI, por exemplo, *status*.



## Obtendo ajuda sobre um subcomando
{: #subcommand_cli_help}

Um comando pode ter subcomandos. Para obter ajuda sobre subcomandos, conclua as etapas a seguir:

1. Efetue login em uma região, uma organização e um espaço do {{site.data.keyword.Bluemix_notm}}. 

    Por exemplo, para efetuar login na região sul dos EUA, execute o comando a seguir:
	
	```
    bx login -a https://api.ng.bluemix.net
    ```
    {: codeblock}
    
2. Obtenha a lista de comandos suportados e identifique aquele que você precisa. Execute o
comando:

    ```
    bx cf at help 
    ```
    {: codeblock}

3. Obtenha ajuda sobre o comando e identifique os subcomandos suportados. Execute o seguinte comando:

    ```
    bx cf at help *Command*
    ```
    {: codeblock}
    
    em que *Command* é o nome de um comando da CLI, por exemplo, *session*.

4. Obtenha ajuda sobre o comando e identifique os subcomandos suportados. Execute o seguinte comando:

    ```
    bx cf at *Command* help *Subcommand*
    ```
    {: codeblock}
    
    em que 
    
    * *Command* é o nome de um comando da CLI, por exemplo, *status*.
    * *Subcommand* é o nome de um subcomando suportado, por exemplo, para o comando *session*, um subcomando válido é *list*.




