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

# Getting help on how to use the Activity Tracker CLI
{: #get_help_cli}

The {{site.data.keyword.cloudaccesstrailshort}} CLI offers different types of help: general help to learn about the CLI and supported commands, command help to learn how to use a command, or subcommand help to learn how to use a subcommands for a command.
{:shortdesc}


## Getting general help
{: #general_cli_help}

To get general information about the CLI and what commands are supported, complete the followimg steps:

1. Log in to a {{site.data.keyword.Bluemix_notm}} region, organization, and space. 

    For example, to log in to the US South region, run the following command:
	
	```
    bx login -a https://api.ng.bluemix.net
    ```
    {: codeblock}
    
2. List information about the supported commands and the CLI. Run the following command:

    ```
    bx cf at help 
    ```
    {: codeblock}
    
    

## Getting help on a command
{: #command_cli_help}

To get help on how to use a command, complete the followimg steps:

1. Log in to a {{site.data.keyword.Bluemix_notm}} region, organization, and space. 

    For example, to log in to the US South region, run the following command:
	
	```
    bx login -a https://api.ng.bluemix.net
    ```
    {: codeblock}
    
2. Get the list of supported comnmands and identify the one that you need. Run the command:

    ```
    bx cf at help 
    ```
    {: codeblock}

3. Get help on the command. Run the following command:

    ```
    bx cf at help *Command*
    ```
    {: codeblock}
    
    where *Command* is the name of a CLI command, for example, *status*.



## Getting help on a subcommand
{: #subcommand_cli_help}

A command can have subcommands. To get help on subcommands, complete the followimg steps:

1. Log in to a {{site.data.keyword.Bluemix_notm}} region, organization, and space. 

    For example, to log in to the US South region, run the following command:
	
	```
    bx login -a https://api.ng.bluemix.net
    ```
    {: codeblock}
    
2. Get the list of supported comnmands and identify the one that you need. Run the command:

    ```
    bx cf at help 
    ```
    {: codeblock}

3. Get help on the command and identify the supported subcommands. Run the following command:

    ```
    bx cf at help *Command*
    ```
    {: codeblock}
    
    where *Command* is the name of a CLI command, for example, *session*.

4. Get help on the command and identify the supported subcommands. Run the following command:

    ```
    bx cf at *Command* help *Subcommand*
    ```
    {: codeblock}
    
    where 
    
    * *Command* is the name of a CLI command, for example, *status*.
    * *Subcommand* is the name of a supported subcommand, for example, for the command *session*, a valid subcommand is *list*.




