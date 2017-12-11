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

# Come ottenere aiuto su come utilizzare la CLI del programma di traccia dell'attività 
{: #get_help_cli}

La CLI {{site.data.keyword.cloudaccesstrailshort}} offre diversi tipi di assistenza: il supporto generale per informazioni sulla CLI e i comandi supportati, il supporto sul comando per informazioni su come utilizzare un comando o il supporto su un comando secondario per informazioni su come utilizzare i comandi secondari di un comando.
{:shortdesc}


## Come ottenere supporto generale
{: #general_cli_help}

Per ottenere le informazioni generali sulla CLI e su quali comandi sono supportati, completa la seguente procedura:

1. Accedi a uno spazio, organizzazione, regione {{site.data.keyword.Bluemix_notm}}. 

    Ad esempio, per accedere alla regione Stai Uniti Sud, immetti il seguente comando:
	
	```
    bx login -a https://api.ng.bluemix.net
    ```
    {: codeblock}
    
2. Elenca le informazioni sui comandi supportati e sulla CLI. Immetti il seguente comando:

    ```
    bx cf at help 
    ```
    {: codeblock}
    
    

## Ottenere supporto per un comando 
{: #command_cli_help}

Per ottenere supporto sull'utilizzo di un comando, completa la seguente procedura:

1. Accedi a uno spazio, organizzazione, regione {{site.data.keyword.Bluemix_notm}}. 

    Ad esempio, per accedere alla regione Stai Uniti Sud, immetti il seguente comando:
	
	```
    bx login -a https://api.ng.bluemix.net
    ```
    {: codeblock}
    
2. Ottieni un elenco di comandi supportati e identifica quello di cui hai bisogno. Esegui il comando:

    ```
    bx cf at help 
    ```
    {: codeblock}

3. Ottenere supporto sul comando. Immetti il seguente comando:

    ```
    bx cf at help *Command*
    ```
    {: codeblock}
    
    dove *Command* è il nome di un comando CLI, ad esempio, *status*.



## Ottenere supporto per un comando secondario 
{: #subcommand_cli_help}

Un comando può avere comandi secondari. Per ottenere supporto sui comandi secondari, completa la seguente procedura: 

1. Accedi a uno spazio, organizzazione, regione {{site.data.keyword.Bluemix_notm}}. 

    Ad esempio, per accedere alla regione Stai Uniti Sud, immetti il seguente comando:
	
	```
    bx login -a https://api.ng.bluemix.net
    ```
    {: codeblock}
    
2. Ottieni un elenco di comandi supportati e identifica quello di cui hai bisogno. Esegui il comando:

    ```
    bx cf at help 
    ```
    {: codeblock}

3. Ottieni supporto sul comando e identifica i comandi secondari supportati. Immetti il seguente comando:

    ```
    bx cf at help *Command*
    ```
    {: codeblock}
    
    dove *Command* è il nome di un comando CLI, ad esempio, *session*.

4. Ottieni supporto sul comando e identifica i comandi secondari supportati. Immetti il seguente comando:

    ```
    bx cf at *Command* help *Subcommand*
    ```
    {: codeblock}
    
    dove 
    
    * *Command* è il nome di un comando CLI, ad esempio, *status*.
    * *Subcommand* è il nome di un comando secondario supportato, ad esempio, per il comando *session*, un comando secondario valido è *list*.




