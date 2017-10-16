---

copyright:
  years: 2016, 2017
lastupdated: "2017-09-17"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Configuring the Activity Tracker CLI
{: #config_at_cli}

The {{site.data.keyword.cloudaccesstraillong}} service includes a command line interface (CLI) that you can use to manage your events in the cloud. The CLI is a Cloud Foundry (CF) plugin. You can use commands to view the status of the events, to download events, to restore events, to discard events, and to configure the events retention policy. 
{:shortdesc}


## Installing the Activity Tracker CLI
{: #install_cli}

To install the {{site.data.keyword.cloudaccesstrailshort}} CLI, complete the following steps:

1. Install the {{site.data.keyword.Bluemix_notm}} CLI.

    For more information, see [Install from shell](/docs/cli/reference/bluemix_cli/download_cli.html#shell_install).
	
	For example, to install the {{site.data.keyword.Bluemix_notm}} CLI on Linux, run the following command:
	
	```
	curl -fsSL https://clis.ng.bluemix.net/install/linux | sh
	```
	{: codeblock}

2. Install the {{site.data.keyword.cloudaccesstrailshort}} CF plugin.

    * For Linux, see [Installing the {{site.data.keyword.cloudaccesstrailshort}} CLI on Linux](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#install_cli_linux).
    * For Windows, see [Installing the {{site.data.keyword.cloudaccesstrailshort}} CLI on Windows](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#install_cli_windows).
    * For Mac OS X, see [Installing the {{site.data.keyword.cloudaccesstrailshort}} CLI on Mac OS X ](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#install_cli_mac).
 
3. Verify the installation of the CLI plugin.
  
    For example, check the version of the plugin. Run the following command:
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    The output looks as follows:
   
    ```
    Invoking 'cf plugins'...

    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}

	
## Installing the Activity Tracker CLI on Linux
{: #install_cli_linux}

Complete the following steps to install the {{site.data.keyword.cloudaccesstrailshort}} CF plugin on Linux:

1. Install the {{site.data.keyword.cloudaccesstrailshort}} CLI plugin.

    1. Download the latest release of the {{site.data.keyword.cloudaccesstrailshort}} service CLI plugin from [the Bluemix CLI page](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins). 
	
		Select the platform value: **linux64**. 
		Click **Save file**. 
    
    2. Unzip the plugin.
    
        For example, to unzip the `activitytracker-cli-linux_x64_v3.0.2.gz` plugin in Ubuntu, run the following command:
        
        ```
        gunzip activitytracker-cli-linux_x64_v3.0.2.gz
        ```
        {: codeblock}

    3. Make the file executable.
    
        For example, to make the file `activitytracker-cli-linux_x64_v3.0.2` executable, run the following command:
        
        ```
        chmod a+x activitytracker-cli-linux_x64_v3.0.2
        ```
        {: codeblock}

    4. Install the logging CF plugin.
    
        For example, to make the file `activitytracker-cli-linux_x64_v3.0.2` executable, run the following command:
        
        ```
        bx cf install-plugin -f activitytracker-cli-linux_x64_v3.0.2
        ```
        {: codeblock}

2. Verify the installation of the CLI plugin.
  
    For example, check the version of the plugin. Run the following command:
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    The output looks as follows:
   
    ```
    Invoking 'cf plugins'...

    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}


## Installing the Activity Tracker CLI on Windows
{: #install_cli_windows}

Complete the following steps to install the{{site.data.keyword.cloudaccesstrailshort}} CF plugin on Windows:

1. Download the latest release of the {{site.data.keyword.cloudaccesstrailshort}} service CLI plugin from [the Bluemix CLI page](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins). 
	
	1. Select the platform value: **win64**. 
	2. Click **Save file**.  
    
2. Run the **cf install-plugins** command to install the {{site.data.keyword.cloudaccesstrailshort}} plugin on Windows. 

    ```
	bx cf install-plugin PluginName
	```
	{: codeblock}
	
	where *PluginName* is the name of the file that you have downloaded.
	
    For example, to install the plugin on Windows, run the following command from a terminal window:
	
	```
	bx cf install-plugin activitytracker-cli-windows_x64_v3.0.2.exe
	```
	{: codeblock}
	
    When the plugin is installed, you get the following message: `Plugin IBM-ActivityTracker successfully installed.`

3. Verify the installation of the CLI plugin.
  
    For example, check the version of the plugin. Run the following command:
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    The output looks as follows:
   
    ```
    Invoking 'cf plugins'...

    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}



## Installing the Activity Tracker CLI on Mac OS X
{: #install_cli_mac}

Complete the following steps to install the {{site.data.keyword.cloudaccesstrailshort}} CF plugin on Mac OS X:

1. Download the latest release of the {{site.data.keyword.cloudaccesstrailshort}} service CLI plugin from [the Bluemix CLI page](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins). 
	
	1. Select the platform value: **osx**. 
	2. Click **Save file**.  
    
2. Run the **cf install-plugin** command to install the {{site.data.keyword.cloudaccesstrailshort}} plugin on Mac OS X. 

    ```
	bx cf install-plugin PluginName
	```
	{: codeblock}
	
	where *PluginName* is the name of the file that you have downloaded.
	
    For example, to install the plugin on a Mac OS X, run the following command from a terminal:
	
	```
	bx cf install-plugin activitytracker-cli-mac_x64_v3.0.2
	```
	{: codeblock}
	
    When the plugin is installed, you get the following message: `Plugin IBM-ActivityTracker successfully installed.`

3. Verify the installation of the CLI plugin.
  
    For example, check the version of the plugin. Run the following command:
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    The output looks as follows:
   
    ```
    Invoking 'cf plugins'...

    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}

	

## Updating the Activity Tracker CLI
{: #update_cli}

Complete the following steps to update the {{site.data.keyword.cloudaccesstrailshort}} CF plugin:

1. Download the latest release of the {{site.data.keyword.cloudaccesstrailshort}} service CLI plugin from [the Bluemix CLI page](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins). 
	
	1. Select the platform value: **win64** for Windows, **osx** for Mac OS X, or **linux64** for Linux. 
	2. Click **Save file**.  
    
2. Run the **cf install-plugin** command to update the {{site.data.keyword.cloudaccesstrailshort}} plugin on Windows. 

    ```
	bx cf install-plugin PluginName -f
	```
	{: codeblock}
	
	where 
	
	* *PluginName* is the name of the file that you have downloaded.
	* *-f* is the option that indicates to uninstall the old version of the plugin and install the new one.
	
    For example, to update the plugin on Windows, run the following command from a terminal window:
	
	```
	bx cf install-plugin activitytracker-cli-windows_x64_v3.0.2.exe
	```
	{: codeblock}
	
    When the plugin is installed, you get the following message: `Plugin IBM-ActivityTracker successfully installed.`

3. Verify the installation of the CLI plugin.
  
    For example, check the version of the plugin. Run the following command:
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    The output looks as follows:
   
    ```
    Invoking 'cf plugins'...

    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2     at             IBM Activity Tracker plug-in.
    ```
    {: screen}

	
	
## Uninstalling the Activity Tracker CLI
{: #uninstall_cli}

To uninstall the {{site.data.keyword.cloudaccesstrailshort}} CLI, delete the plugin.
{:shortdesc}

Complete the following steps to uninstall the {{site.data.keyword.cloudaccesstrailshort}} service CLI:

1. Verify the version of the {{site.data.keyword.cloudaccesstrailshort}} CLI plugin that is installed.
  
    For example, check the version of the plugin. Run the following command:
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    The output looks as follows:
   
    ```
    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2           at       IBM Activity Tracker plug-in
    ```
    {: screen}
    
2. If the plugin is installed, run the `cf uninstall-plugin` to uninstall the logging CLI plugin.

    Run the following command:
        
    ```
    bx cf uninstall-plugin IBM-ActivityTracker
    ```
    {: codeblock}
  
