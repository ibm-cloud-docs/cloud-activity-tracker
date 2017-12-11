---

copyright:
  years: 2017

lastupdated: "2017-11-09"

---


{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# Frequent questions and answers using the IBM Cloud CLI
{: #cli_qa}

Here are the answers to common questions about using the {{site.data.keyword.Bluemix}} CLI with the {{site.data.keyword.loganalysisshort}} service. 
{:shortdesc}

* [How do I log in to the {{site.data.keyword.Bluemix_notm}}](/docs/services/cloud-activity-tracker/qa/cli_qa.html#login)
* [How do I install the {{site.data.keyword.Bluemix_notm}} CLI](/docs/services/cloud-activity-tracker/qa/cli_qa.html#install_bmx_cli)
* [How do I get the GUID of an account](/docs/services/cloud-activity-tracker/qa/cli_qa.html#account_guid)
* [How do I get the GUID of an organization](/docs/services/cloud-activity-tracker/qa/cli_qa.html#org_guid)
* [How do I get the GUID of a space](/docs/services/cloud-activity-tracker/qa/cli_qa.html#space_guid)

## How do I login in to the {{site.data.keyword.Bluemix_notm}}?
{: #login}

Run the following command to log in to a region, organization, and space in the {{site.data.keyword.Bluemix_notm}}:

```
bx login -a Endpoint
```
{: codeblock}
	
Where *Endpoint* is the URL to log in to the {{site.data.keyword.Bluemix_notm}}. This URL is different per region.
	
<table>
    <caption>List of endpoints to access the {{site.data.keyword.Bluemix_notm}}</caption>
	<tr>
	  <th>Region</th>
	  <th>URL</th>
	</tr>
	<tr>
	  <td>Germany</td>
	  <td>api.eu-de.bluemix.net</td>
	</tr>
	<tr>
	  <td>Sydney</td>
	  <td>api.au-syd.bluemix.net</td>
	</tr>
	<tr>
	  <td>US South</td>
	  <td>api.ng.bluemix.net</td>
	</tr>
	<tr>
	  <td>United Kingdom</td>
	  <td>api.eu-gb.bluemix.net</td>
	</tr>
</table>

For example, to log in to the US South region, run the following command:
	
```
bx login -a https://api.ng.bluemix.net
```
{: codeblock}

Follow the instructions. 

Then, set the organization and space. Run the following command:

```
bx target -o OrgName -s SpaceName
```
{: codeblock}

where

* OrgName is the name of the organization.
* SpaceName is the name of the space.

	
	
## How do I install the IBM Cloud CLI?
{: #install_bmx_cli}

See [Download and install the {{site.data.keyword.Bluemix}} CLI](/docs/cli/reference/bluemix_cli/download_cli.html#download_install).



## How do I get the GUID of an account
{: #account_guid}
	
Complete the following steps to get the GUID of an account:
	
1. Log in to a region, organization, and space in the {{site.data.keyword.Bluemix_notm}}. 

    For more information, see [How do I log in to the {{site.data.keyword.Bluemix_notm}}](/docs/services/cloud-activity-tracker/qa/cli_qa.html#login).
	
2. Run the `bx iam accounts` command to get the GUID of an account.

    ```
	bx iam accounts
	```
	{: codeblock} 
	
	For example, to retrieve all the accounts with their corresponding GUIDs for user xxx@yyy.com, run the command:
	
	```
	bx iam accounts
	Retrieving all accounts of xxx@yyy.com...
    OK
    Account GUID                       Name                               Type    State    Owner User ID   
    12345123451234512345123451234512   A Account                          TRIAL   ACTIVE   xxx@yyy.com   
    23456234562345622456234561234561   B Account                          TRIAL   ACTIVE   zzz@yyy.com   
	```
	{: screen}

	
## How do I get the GUID of an organization
{: #org_guid}

Complete the following steps to get the GUID of an organization:
	
1. Log in to a region, organization, and space in the {{site.data.keyword.Bluemix_notm}}. 

    For more information, see [How do I log in to the {{site.data.keyword.Bluemix_notm}}](/docs/services/cloud-activity-tracker/qa/cli_qa.html#login).

2. Run the `bx iam org` command to get the organization GUID. 

    ```
    bx iam org NAME --guid
    ```
    {: codeblock}
	
    where NAME is the name of the {{site.data.keyword.Bluemix_notm}} organization.        
		
		
		
## How do I get the GUID of a space
{: #space_guid}
	
Complete the following steps to get the GUID of a space:
	
1. Log in to a region, organization, and space in the {{site.data.keyword.Bluemix_notm}}. 

    For more information, see [How do I log in to the {{site.data.keyword.Bluemix_notm}}](/docs/services/cloud-activity-tracker/qa/cli_qa.html#login).
	
2. Run the `bx iam space` command to get the space GUID. 

    ```
    bx iam space NAME --guid
    ```
    {: codeblock}
	
    where NAME is the name of a {{site.data.keyword.Bluemix_notm}} space. 
	
    For example, to get the GUID for the space *dev*, run the following command:
	
    ```
    bx iam space dev --guid
    e03afff1-3456-4af6-1234-59treg1b0abc
    ```
    {: screen}




		
		