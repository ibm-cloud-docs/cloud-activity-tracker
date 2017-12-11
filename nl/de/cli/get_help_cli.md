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

# Hilfe zur Verwendung der Activity Tracker-CLI abrufen
{: #get_help_cli}

Die {{site.data.keyword.cloudaccesstrailshort}}-CLI stellt verschiedene Hilfeinformationen bereit: Erweiterte Hilfe für die CLI und die unterstützten Befehle, Hilfe für Befehle mit Informationen zur Verwendung eines einzelnen Befehls sowie Hilfe zu Unterbefehlen mit Informationen zur Verwendung der Unterbefehle für einen bestimmten Befehl.
{:shortdesc}


## Erweiterte Hilfe abrufen
{: #general_cli_help}

Führen Sie die folgenden Schritte aus, um allgemeine Hilfeinformationen zur Befehlszeilenschnittstelle (Command Line Interface, CLI) und zu den unterstützten Befehlen abzurufen:

1. Melden Sie sich in {{site.data.keyword.Bluemix_notm}} bei einer Region, einer Organisation und einem Bereich an. 

    Führen Sie zum Beispiel den folgenden Befehl aus, um sich bei der Region 'Vereinigte Staaten (Süden)' anzumelden:
	
	```
    bx login -a https://api.ng.bluemix.net
    ```
    {: codeblock}
    
2. Rufen Sie die Informationen zu den unterstützten Befehlen und zur CLI auf. Führen Sie dazu den folgenden Befehl aus:

    ```
    bx cf at help
    ```
    {: codeblock}
    
    

## Hilfe zu einem Befehl abrufen
{: #command_cli_help}

Führen Sie die folgenden Schritte aus, um Hilfeinformationen zur Verwendung eines Befehls abzurufen:

1. Melden Sie sich in {{site.data.keyword.Bluemix_notm}} bei einer Region, einer Organisation und einem Bereich an. 

    Führen Sie zum Beispiel den folgenden Befehl aus, um sich bei der Region 'Vereinigte Staaten (Süden)' anzumelden:
	
	```
    bx login -a https://api.ng.bluemix.net
    ```
    {: codeblock}
    
2. Rufen Sie die Liste der unterstützten Befehle ab und geben Sie den gewünschten Befehl an. Führen Sie dazu den folgenden Befehl aus:

    ```
    bx cf at help
    ```
    {: codeblock}

3. Rufen Sie die Hilfeinformationen zu dem Befehl ab. Führen Sie dazu den folgenden Befehl aus:

    ```
    bx cf at help *Command*
    ```
    {: codeblock}
    
    Dabei ist *Command* der Name eines CLI-Befehls (zum Beispiel *status*).



## Hilfe zu einem Unterbefehl abrufen
{: #subcommand_cli_help}

Ein Befehl kann Unterbefehle beinhalten. Führen Sie die folgenden Schritte aus, um Hilfeinformationen zu Unterbefehlen abzurufen:

1. Melden Sie sich in {{site.data.keyword.Bluemix_notm}} bei einer Region, einer Organisation und einem Bereich an. 

    Führen Sie zum Beispiel den folgenden Befehl aus, um sich bei der Region 'Vereinigte Staaten (Süden)' anzumelden:
	
	```
    bx login -a https://api.ng.bluemix.net
    ```
    {: codeblock}
    
2. Rufen Sie die Liste der unterstützten Befehle ab und geben Sie den gewünschten Befehl an. Führen Sie dazu den folgenden Befehl aus:

    ```
    bx cf at help
    ```
    {: codeblock}

3. Rufen Sie die Hilfeinformationen zu dem Befehl ab und ermitteln Sie die unterstützten Unterbefehle. Führen Sie dazu den folgenden Befehl aus:

    ```
    bx cf at help *Command*
    ```
    {: codeblock}
    
    Dabei ist *Command* der Name des CLI-Befehls (zum Beispiel *session*).

4. Rufen Sie die Hilfeinformationen zu dem Befehl ab und ermitteln Sie die unterstützten Unterbefehle. Führen Sie dazu den folgenden Befehl aus:

    ```
    bx cf at *Command* help *Subcommand*
    ```
    {: codeblock}
    
    Dabei gilt Folgendes: 
    
    * *Command* ist der Name des CLI-Befehls (zum Beispiel *status*).
    * *Subcommand* ist der Name eines unterstützten Unterbefehls (ein unterstützter Unterbefehl für den Befehl *session* ist z. B. *list*).




