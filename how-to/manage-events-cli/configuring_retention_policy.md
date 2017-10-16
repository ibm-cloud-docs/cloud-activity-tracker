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

# Configuring the events retention policy
{: #configuring_retention_policy}

Use the command **cf at option** to view and configure the retention policy that defines the maximum number of days that events are kept in {{site.data.keyword.cloudaccesstrailshort}}. By default, the retention policy is disabled, and events are kept indefinitely. After the retention period has expired, events are deleted automatically. 
{:shortdesc}

You can set the same retention policy for all spaces in the account or you can customize the retention period for a space. 


## Disabling the event retention policy for a space
{: #disable_retention_policy_space}

Complete the following steps to disable a retention policy:

1. Log in to the {{site.data.keyword.Bluemix_notm}} region, organization, and space where you want to set a retention policy. 

    ```
    cf login -a Endpoint
    ```
    {: codeblock}
	
	Where *Endpoint* is the URL to log in to {{site.data.keyword.Bluemix_notm}}. This URL is different per region.
	
	<table>
	    <caption>List of endpoints to access {{site.data.keyword.Bluemix_notm}}</caption>
		<tr>
		  <th>Region</th>
		  <th>URL</th>
		</tr>
		<tr>
		  <td>US South</td>
		  <td>api.ng.bluemix.net</td>
		</tr>
		<tr>
		  <td>United Kingdom</td>
		  <td>api.eu-gb.bluemix.net</td>
		</tr>
		<tr>
		  <td>Germany</td>
		  <td>api.eu-de.bluemix.net</td>
		</tr>
	</table>

    Follow the instructions. Enter your {{site.data.keyword.Bluemix_notm}} credentials, select an organization and a space. 

    For example, run the following command to log in to the US South region:
	
	```
	cf login -a api.ng.bluemix.net
	```
	{: codeblock}
    
2. Set the retention period to **-1** to disable the retention period. Run the command:

    ```
    cf at option -r -1
    ```
    {: codeblock}
    
**Example**
    
For example, to disable the retention period for a space with ID *d35da1e3-b345-475f-8502-cfgh436902a3*, run the following command:

```
cf at option -r -1
```
{: codeblock}

The output is:

```
+--------------------------------------+-----------+
|               SPACEID                | RETENTION |
+--------------------------------------+-----------+
| d35da1e3-b345-475f-8502-cfgh436902a3 |        -1 |
+--------------------------------------+-----------+
```
{: screen} 



## Checking the log retention policy for a space
{: #check_retention_policy_space}

To get the retention period that is set for a {{site.data.keyword.Bluemix_notm}} space, complete the following steps:

1. Log in to the {{site.data.keyword.Bluemix_notm}} region, organization, and space where you want to set a log retention policy. 

    ```
    cf login -a Endpoint
    ```
    {: codeblock}
	
	Where *Endpoint* is the URL to log in to {{site.data.keyword.Bluemix_notm}}. This URL is different per region.
	
	<table>
	    <caption>List of endpoints to access {{site.data.keyword.Bluemix_notm}}</caption>
		<tr>
		  <th>Region</th>
		  <th>URL</th>
		</tr>
		<tr>
		  <td>US South</td>
		  <td>api.ng.bluemix.net</td>
		</tr>
		<tr>
		  <td>United Kingdom</td>
		  <td>api.eu-gb.bluemix.net</td>
		</tr>
		<tr>
		  <td>Germany</td>
		  <td>api.eu-de.bluemix.net</td>
		</tr>
	</table>

    Follow the instructions. Enter your {{site.data.keyword.Bluemix_notm}} credentials, select an organization and a space. 

    For example, run the following command to log in to the US South region:
	
	```
	cf login -a api.ng.bluemix.net
	```
    {: codeblock}
    
2. Get the the retention period. Run the command:

    ```
    cf at option
    ```
    {: codeblock}

    The output for space ID *d35da1e3-b345-475f-8502-cfgh436902a3* is 30 days:

    ```
    +--------------------------------------+-----------+
    |               SPACEID                | RETENTION |
    +--------------------------------------+-----------+
    | d35da1e3-b345-475f-8502-cfgh436902a3 |        30 |
    +--------------------------------------+-----------+
    ```
    {: screen}
    

## Checking the log retention policy for all spaces in an account
{: #check_retention_policy_account}

To get the retention period that is set for each {{site.data.keyword.Bluemix_notm}} space in an account, complete the following steps:

1. Log in to the {{site.data.keyword.Bluemix_notm}} region, organization, and space where you want to set a log retention policy. 

    ```
    cf login -a Endpoint
    ```
    {: codeblock}
	
	Where *Endpoint* is the URL to log in to {{site.data.keyword.Bluemix_notm}}. This URL is different per region.
	
	<table>
	    <caption>List of endpoints to access {{site.data.keyword.Bluemix_notm}}</caption>
		<tr>
		  <th>Region</th>
		  <th>URL</th>
		</tr>
		<tr>
		  <td>US South</td>
		  <td>api.ng.bluemix.net</td>
		</tr>
		<tr>
		  <td>United Kingdom</td>
		  <td>api.eu-gb.bluemix.net</td>
		</tr>
		<tr>
		  <td>Germany</td>
		  <td>api.eu-de.bluemix.net</td>
		</tr>
	</table>

    Follow the instructions. Enter your {{site.data.keyword.Bluemix_notm}} credentials, select an organization and a space. 

    For example, run the following command to log in to the US South region:
	
	```
	cf login -a api.ng.bluemix.net
	```
    {: codeblock}
    
2. Get the the retention period for each space in the account. Run the command:

    ```
    cf at option -a
    ```
    {: codeblock}
	
	where *-a* indicates that the information includes all the spaces in the account.

    For example, the output of running the command is:

    ```
    +--------------------------------------+-----------+
    |               SPACEID                | RETENTION |
    +--------------------------------------+-----------+
    | d35da1e3-b345-475f-8502-cfgh436902a3 |        30 |
    +--------------------------------------+-----------+
    | fdew45e3-b345-4365-8502-cfghrfthy5a3 |        30 |
    +--------------------------------------+-----------+
    ```
    {: screen}
    

## Setting across the account the log retention policy
{: #set_retention_policy_space}

To set the retention period for a {{site.data.keyword.Bluemix_notm}} account, complete the following steps:

1. Log in to the {{site.data.keyword.Bluemix_notm}} region, organization, and space where you want to set a log retention policy. 

   ```
    cf login -a Endpoint
    ```
    {: codeblock}
	
	Where *Endpoint* is the URL to log in to {{site.data.keyword.Bluemix_notm}}. This URL is different per region.
	
	<table>
	    <caption>List of endpoints to access {{site.data.keyword.Bluemix_notm}}</caption>
		<tr>
		  <th>Region</th>
		  <th>URL</th>
		</tr>
		<tr>
		  <td>US South</td>
		  <td>api.ng.bluemix.net</td>
		</tr>
		<tr>
		  <td>United Kingdom</td>
		  <td>api.eu-gb.bluemix.net</td>
		</tr>
		<tr>
		  <td>Germany</td>
		  <td>api.eu-de.bluemix.net</td>
		</tr>
	</table>

    Follow the instructions. Enter your {{site.data.keyword.Bluemix_notm}} credentials, select an organization and a space. 

    For example, run the following command to log in to the US South region:
	
	```
	cf login -a api.ng.bluemix.net
	```
    {: codeblock}
    
2. Set the retention period. Run the command:

    ```
    cf at option -r Number_of_days - a
    ```
    {: codeblock}
    
    where 
	* *-r* is the option that must be specified to set a retention period.
	* *Number_of_days* is an integer that defines the number of days that you want to keep events. 
	* *-a* indicates that the request applies to all the spaces in the account.
    
    
**Example**
    
For example, to keep any type of log in your account for 15 days only, run the following command:

```
cf at option -r 15 -a
```
{: codeblock}

The output lists an entry for each space in the account, including information about the retention period:

```
+--------------------------------------+-----------+
|               SPACEID                | RETENTION |
+--------------------------------------+-----------+
| d35da1e3-b345-475f-8502-cfgh436902a3 |        15 |
+--------------------------------------+-----------+
| fdew45e3-b345-4365-8502-cfghrfthy5a3 |        15 |
+--------------------------------------+-----------+
```
{: screen}

## Setting the log retention policy for a space
{: #set_retention_policy_account}

To see the retention period for a {{site.data.keyword.Bluemix_notm}} space, complete the following steps:

1. Log in to the {{site.data.keyword.Bluemix_notm}} region, organization, and space where you want to set a log retention policy. 

    ```
    cf login -a Endpoint
    ```
    {: codeblock}
	
	Where *Endpoint* is the URL to log in to {{site.data.keyword.Bluemix_notm}}. This URL is different per region.
	
	<table>
	    <caption>List of endpoints to access {{site.data.keyword.Bluemix_notm}}</caption>
		<tr>
		  <th>Region</th>
		  <th>URL</th>
		</tr>
		<tr>
		  <td>US South</td>
		  <td>api.ng.bluemix.net</td>
		</tr>
		<tr>
		  <td>United Kingdom</td>
		  <td>api.eu-gb.bluemix.net</td>
		</tr>
		<tr>
		  <td>Germany</td>
		  <td>api.eu-de.bluemix.net</td>
		</tr>
	</table>

    Follow the instructions. Enter your {{site.data.keyword.Bluemix_notm}} credentials, select an organization and a space. 

    For example, run the following command to log in to the US South region:
	
	```
	cf login -a api.ng.bluemix.net
	```
    {: codeblock}
    
2. Set the retention period. Run the command:

    ```
    cf at option -r Number_of_days
    ```
    {: codeblock}
    
    where 
	* *-r* is the option that must be specified to set a retention period.
	* *Number_of_days* is an integer that defines the number of days that you want to keep events.
    
    
**Example**
    
For example, to keep events that are available in a space for a year, run the following command:

```
cf at option -r 365
```
{: codeblock}

The output is:

```
+--------------------------------------+-----------+
|               SPACEID                | RETENTION |
+--------------------------------------+-----------+
| d35da1e3-b345-475f-8502-cfgh436902a3 |       365 |
+--------------------------------------+-----------+
```
{: screen}


