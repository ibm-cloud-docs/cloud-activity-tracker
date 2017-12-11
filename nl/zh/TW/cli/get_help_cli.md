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

# 取得如何使用 Activity Tracker CLI 的說明
{: #get_help_cli}

{{site.data.keyword.cloudaccesstrailshort}} CLI 提供不同類型的說明：用來瞭解 CLI 及支援指令的一般說明、用來瞭解如何使用指令的指令說明，或用來瞭解如何使用指令之次指令的次指令說明。
{:shortdesc}


## 取得一般說明
{: #general_cli_help}

若要取得 CLI 的一般資訊及支援的指令，請完成下列步驟：

1. 登入 {{site.data.keyword.Bluemix_notm}} 地區、組織及空間。 

    例如，若要登入美國南部地區，請執行下列指令：
	
	```
    bx login -a https://api.ng.bluemix.net
    ```
    {: codeblock}
    
2. 列出支援指令及 CLI 的相關資訊。執行下列指令：

    ```
    bx cf at help 
    ```
    {: codeblock}
    
    

## 取得指令的說明
{: #command_cli_help}

若要取得如何使用指令的說明，請完成下列步驟：

1. 登入 {{site.data.keyword.Bluemix_notm}} 地區、組織及空間。 

    例如，若要登入美國南部地區，請執行下列指令：
	
	```
    bx login -a https://api.ng.bluemix.net
    ```
    {: codeblock}
    
2. 取得支援的指令清單，並識別您需要的指令。執行指令：

    ```
    bx cf at help 
    ```
    {: codeblock}

3. 取得指令的說明。執行下列指令：

    ```
    bx cf at help *Command*
    ```
    {: codeblock}
    
    其中 *Command* 是 CLI 指令的名稱，例如 *status*。



## 取得次指令的說明
{: #subcommand_cli_help}

指令可以有次指令。若要取得次指令的說明，請完成下列步驟：

1. 登入 {{site.data.keyword.Bluemix_notm}} 地區、組織及空間。 

    例如，若要登入美國南部地區，請執行下列指令：
	
	```
    bx login -a https://api.ng.bluemix.net
    ```
    {: codeblock}
    
2. 取得支援的指令清單，並識別您需要的指令。執行指令：

    ```
    bx cf at help 
    ```
    {: codeblock}

3. 取得指令的說明並識別支援的次指令。執行下列指令：

    ```
    bx cf at help *Command*
    ```
    {: codeblock}
    
    其中 *Command* 是 CLI 指令的名稱，例如 *session*。

4. 取得指令的說明並識別支援的次指令。執行下列指令：

    ```
    bx cf at *Command* help *Subcommand*
    ```
    {: codeblock}
    
    其中 
    
    * *Command* 是 CLI 指令的名稱，例如 *status*。
    * *Subcommand* 是支援的次指令名稱，例如，對於指令 *session* 而言，有效的次指令為 *list*。




