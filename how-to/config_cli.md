---

copyright:
  years: 2016, 2019
lastupdated: "2019-02-18"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# Configuring the Activity Tracker CLI
{: #config_cli}

The {{site.data.keyword.cloudaccesstraillong}} service includes a command line interface (CLI) that you can use to manage your events in the cloud. You can use the {{site.data.keyword.cloud_notm}} plugin to view the status of the events, to download events, and to configure the events retention policy. The CLI offers different types of help: general help to learn about the CLI and supported commands, command help to learn how to use a command, or subcommand help to learn how to use a subcommands for a command.
{:shortdesc}


## Installing the {{site.data.keyword.cloudaccesstrailshort}} plugin from the {{site.data.keyword.cloud_notm}} repo
{: #install_cli_repo}

To install the {{site.data.keyword.cloudaccesstrailshort}} CLI, complete the following steps:

1. Install the {{site.data.keyword.cloud_notm}} CLI.

   For more information, see [Installing the {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-ibmcloud-cli#ibmcloud-cli).
   
2. Find out the name of the plugin in the repo. Run the following command:

    ```
    ibmcloud plugin repo-plugins
    ```
    {: codeblock}
    
    The name of the plugin is **activity-tracker**.

3. Install the {{site.data.keyword.cloudaccesstrailshort}} plugin. Run the following command:

    ```
    ibmcloud plugin install activity-tracker -r Bluemix
    ```
    {: codeblock}
 
4. Verify the {{site.data.keyword.cloudaccesstrailshort}} plugin is installed.
  
    For example, run the following command to see the list of plugins that are installed:
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    


## Installing the {{site.data.keyword.cloudaccesstrailshort}} plugin from a file
{: #install_cli}

To install the {{site.data.keyword.cloudaccesstrailshort}} CLI, complete the following steps:

1. Install the {{site.data.keyword.cloud_notm}} CLI.

   For more information, see [Installing the {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-ibmcloud-cli#ibmcloud-cli).

2. Install the {{site.data.keyword.cloudaccesstrailshort}} plugin.

    * For Linux, see [Installing the {{site.data.keyword.cloudaccesstrailshort}} plugin on Linux](/docs/services/cloud-activity-tracker/how-to/config_cli.html#install_cli_linux).
    * For Windows, see [Installing the {{site.data.keyword.cloudaccesstrailshort}} plugin on Windows](/docs/services/cloud-activity-tracker/how-to/config_cli.html#install_cli_windows).
    * For Mac OS X, see [Installing the {{site.data.keyword.cloudaccesstrailshort}} plugin on Mac OS X ](/docs/services//cloud-activity-tracker/how-to/config_cli.html#install_cli_mac).
 
3. Verify the installation of the CLI plugin.
  
    For example, check the version of the plugin. Run the following command:
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    


## Installing the {{site.data.keyword.cloudaccesstrailshort}} plugin on Linux from a file
{: #install_cli_linux}

Complete the following steps to install the plugin on Linux:

1. Install the plugin.

    Download the latest release of the {{site.data.keyword.cloudaccesstrailshort}} service CLI plugin (activity-tracker) from [the {{site.data.keyword.cloud_notm}} CLI page](https://clis.ng.bluemix.net/ui/repository.html#bluemix-plugins). 
	
	* Select the platform value: **linux64**. 
	
	* Click **Save file**. 
    
2. Install the plugin. Run the following command:
        
    ```
    ibmcloud plugin install -f activity-tracker-linux-amd64-3.3.0
    ```
    {: codeblock}




## Installing the {{site.data.keyword.cloudaccesstrailshort}} plugin on Windows from a file
{: #install_cli_windows}

Complete the following steps to install the plugin on Windows:

1. Download the latest release of the {{site.data.keyword.cloudaccesstrailshort}} service CLI plugin (activity-tracker) from [the {{site.data.keyword.cloud_notm}} CLI page](https://clis.ng.bluemix.net/ui/repository.html#bluemix-plugins). 
	
	1. Select the platform value: **win64**. 
	2. Click **Save file**.  
    
2. Install the plugin. Run the following command:
        
    ```
    ibmcloud plugin install -f activity-tracker-windows-amd64-3.3.0.exe
    ```
    {: codeblock}

	

## Installing the {{site.data.keyword.cloudaccesstrailshort}} plugin on Mac OS X from a file
{: #install_cli_mac}

Complete the following steps to install the plugin on Mac OS X:

1. Download the latest release of the {{site.data.keyword.cloudaccesstrailshort}} service CLI plugin (activity-tracker) from [the {{site.data.keyword.cloud_notm}} CLI page](https://clis.ng.bluemix.net/ui/repository.html#bluemix-plugins). 
	
	1. Select the platform value: **osx**. 
	2. Click **Save file**.  
    
2. Install the plugin. Run the following command:
        
    ```
    ibmcloud plugin install -f activity-tracker-darwin-amd64-3.3.0
    ```
    {: codeblock}

	
	
## Uninstalling the {{site.data.keyword.cloudaccesstrailshort}} CLI
{: #uninstall_cli}

To uninstall the CLI, delete the plugin.
{:shortdesc}

Complete the following steps to uninstall the {{site.data.keyword.cloudaccesstrailshort}} service CLI:

1. Verify the version of the CLI plugin that is installed.
  
    For example, check the version of the plugin. Run the following command:
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    
2. If the plugin is installed, run the `ibmcloud plugin uninstall` to uninstall the CLI plugin.

    Run the following command:
        
    ```
    ibmcloud plugin uninstall activity-tracker
    ```
    {: codeblock}
  

## Updating the {{site.data.keyword.cloudaccesstrailshort}} CLI from the repo
{: #update_cli}

To update the CLI, run the *ibmcloud plugin update* command.
{:shortdesc}

Complete the following steps to update the {{site.data.keyword.cloudaccesstrailshort}} service CLI:

1. Update the {{site.data.keyword.cloudaccesstrailshort}} plugin. Run the following command:

    ```
    ibmcloud plugin update activity-tracker -r Bluemix
    ```
    {: codeblock}
 
2. Verify the installation of the CLI plugin.
  
    For example, verify the version of the plugin. Run the following command:
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    





## Getting general help
{: #general_cli_help}

To get general information about the CLI and what commands are supported, complete the followimg steps:

1. Log in to a region, organization, and space in the {{site.data.keyword.cloud_notm}}. 
    
2. List information about the supported commands and the CLI. Run the following command:

    ```
    ibmcloud at help 
    ```
    {: codeblock}
    
    

## Getting help on a command
{: #command_cli_help}

To get help on how to use a command, complete the followimg steps:

1. Log in to a region, organization, and space in the {{site.data.keyword.cloud_notm}}. 
    
2. Get the list of supported comnmands and identify the one that you need. Run the command:

    ```
    ibmcloud at help 
    ```
    {: codeblock}

3. Get help on the command. Run the following command:

    ```
    ibmcloud at help *Command*
    ```
    {: codeblock}
    
    where *Command* is the name of a CLI command, for example, *status*.



## Getting help on a subcommand
{: #subcommand_cli_help}

A command can have subcommands. To get help on subcommands, complete the followimg steps:

1. Log in to a region, organization, and space in the {{site.data.keyword.cloud_notm}}. 
    
2. Get the list of supported comnmands and identify the one that you need. Run the command:

    ```
    ibmcloud at help 
    ```
    {: codeblock}

3. Get help on the command and identify the supported subcommands. Run the following command:

    ```
    ibmcloud at help *Command*
    ```
    {: codeblock}
    
    where *Command* is the name of a CLI command, for example, *session*.

4. Get help on the command and identify the supported subcommands. Run the following command:

    ```
    ibmcloud at *Command* help *Subcommand*
    ```
    {: codeblock}
    
    where 
    
    * *Command* is the name of a CLI command, for example, *status*.
    * *Subcommand* is the name of a supported subcommand, for example, for the command *session*, a valid subcommand is *list*.


## Show the details of the plugin
{: #show}
  
Use the 'ibmcloud plugin show activity-tracker' command to show the plugin details. 

```
ibmcloud plugin show activity-tracker
```
{: codeblock}
    




