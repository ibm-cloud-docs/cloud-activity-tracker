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


# Ereignisaufbewahrungsrichtlinie konfigurieren
{: #configuring_retention_policy}

Verwenden Sie den Befehl **ibmcloud at option**, um die Aufbewahrungsrichtlinie, die angibt, über welchen Zeitraum (in Tagen) Ereignisse höchstens in {{site.data.keyword.cloudaccesstrailshort}} aufbewahrt werden, anzuzeigen und zu konfigurieren. Die Aufbewahrungsrichtlinie ist standardmäßig inaktiviert und Ereignisse werden für eine unbegrenzte Dauer aufbewahrt. Nach Ablauf des Aufbewahrungszeitraums werden Ereignisse automatisch gelöscht. 
{:shortdesc}

Sie können dieselbe Aufbewahrungsrichtlinie für alle Bereiche (Spaces) des Kontos festlegen oder aber auch die Aufbewahrungsrichtlinie für einen Bereich anpassen. 


## Ereignisaufbewahrungsrichtlinie für einen Bereich inaktivieren
{: #disable_retention_policy_space}

Führen Sie die folgenden Schritte aus, um eine Aufbewahrungsrichtlinie zu inaktivieren:

1. Melden Sie sich bei {{site.data.keyword.cloud_notm}} an. 

    Melden Sie sich durch Ausführen des Befehls [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) bei {{site.data.keyword.cloud_notm}} an und führen Sie dann den Befehl [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) aus, um festzulegen, für welche Organisation und welchen Bereich (Space) der {{site.data.keyword.cloudaccesstrailshort}}-Service bereitgestellt werden soll.
	
2. Legen Sie für den Aufbewahrungszeitraum den Wert **-1** fest, um die Aufbewahrungsrichtlinie zu inaktivieren. Führen Sie den folgenden Befehl aus:

    ```
    ibmcloud at option -r -1
    ```
    {: codeblock}
    
**Beispiel**
    
Wenn Sie zum Beispiel den Aufbewahrungszeitraum für einen Bereich (Space) mit der ID *d35da1e3-b345-475f-8502-bx cfgh436902a3* inaktivieren wollen, führen Sie den folgenden Befehl aus:

```
ibmcloud at option -r -1
```
{: codeblock}

Die Ausgabe sieht wie folgt aus:

```
+-----------------------------------------+-----------+
|               SPACEID                   | RETENTION |
+-----------------------------------------+-----------+
| d35da1e3-b345-475f-8502-bx cfgh436902a3 |        -1 |
+-----------------------------------------+-----------+
```
{: screen} 



## Protokollaufbewahrungsrichtlinie für einen Bereich (Space) prüfen
{: #check_retention_policy_space}

Führen Sie die folgenden Schritte aus, um den für einen {{site.data.keyword.cloud_notm}}-Bereich (Space) festgelegten Aufbewahrungszeitraum abzurufen:

1. Melden Sie sich bei {{site.data.keyword.cloud_notm}} an. 

    Melden Sie sich durch Ausführen des Befehls [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) bei {{site.data.keyword.cloud_notm}} an und führen Sie dann den Befehl [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) aus, um festzulegen, für welche Organisation und welchen Bereich (Space) der {{site.data.keyword.cloudaccesstrailshort}}-Service bereitgestellt werden soll.
	
2. Rufen Sie den Aufbewahrungszeitraum ab. Führen Sie den folgenden Befehl aus:

    ```
    ibmcloud at option
    ```
    {: codeblock}

    Die Ausgabe für den Bereich (Space) mit der ID *d35da1e3-b345-475f-8502-bx cfgh436902a3* gibt eine Dauer von 30 Tagen an:

    ```
    +-----------------------------------------+-----------+
    |               SPACEID                   | RETENTION |
    +-----------------------------------------+-----------+
    | d35da1e3-b345-475f-8502-bx cfgh436902a3 |        30 |
    +-----------------------------------------+-----------+
    ```
    {: screen}
    

## Protokollaufbewahrungsrichtlinie für alle Bereiche (Spaces) in einem Konto prüfen
{: #check_retention_policy_account}

Führen Sie die folgenden Schritte aus, um den für jeden {{site.data.keyword.cloud_notm}}-Bereich (Space) in einem Konto festgelegten Aufbewahrungszeitraum abzurufen:

1. Melden Sie sich bei {{site.data.keyword.cloud_notm}} an. 

    Melden Sie sich durch Ausführen des Befehls [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) bei {{site.data.keyword.cloud_notm}} an und führen Sie dann den Befehl [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) aus, um festzulegen, für welche Organisation und welchen Bereich (Space) der {{site.data.keyword.cloudaccesstrailshort}}-Service bereitgestellt werden soll.
    
2. Rufen Sie den Aufbewahrungszeitraum für jeden Bereich (Space) im Konto ab. Führen Sie den folgenden Befehl aus:

    ```
    ibmcloud at option -a
    ```
    {: codeblock}
	
	Dabei gibt *-a* an, dass die Information alle Bereiche (Spaces) im Konto umfasst.

    Die Ausführung des Befehls kann zum Beispiel die folgende Ausgabe liefern:

    ```
    +-----------------------------------------+-----------+
    |               SPACEID                   | RETENTION |
    +-----------------------------------------+-----------+
    | d35da1e3-b345-475f-8502-bx cfgh436902a3 |        30 |
    +-----------------------------------------+-----------+
    | fdew45e3-b345-4365-8502-bx cfghrfthy5a3 |        30 |
    +-----------------------------------------+-----------+
    ```
    {: screen}
    

## Protokollaufbewahrungsrichtlinie für ein Konto festlegen
{: #set_retention_policy_space}

Führen Sie die folgenden Schritte aus, um den Aufbewahrungszeitraum für ein {{site.data.keyword.cloud_notm}}-Konto festzulegen:

1. Melden Sie sich bei {{site.data.keyword.cloud_notm}} an. 

    Melden Sie sich durch Ausführen des Befehls [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) bei {{site.data.keyword.cloud_notm}} an und führen Sie dann den Befehl [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) aus, um festzulegen, für welche Organisation und welchen Bereich (Space) der {{site.data.keyword.cloudaccesstrailshort}}-Service bereitgestellt werden soll.
	
2. Legen Sie den Aufbewahrungszeitraum fest. Führen Sie den folgenden Befehl aus:

    ```
    ibmcloud at option -r Number_of_days - a
    ```
    {: codeblock}
    
    Dabei gilt Folgendes: 
	* *-r* ist die Option, die angegeben werden muss, um einen Aufbewahrungszeitraum festzulegen.
	* *Number_of_days* ist eine ganze Zahl, die den Aufbewahrungszeitraum für Ereignisse in Tagen definiert. 
	* *-a* gibt an, dass sich die Anforderung auf alle Bereiche (Spaces) im Konto bezieht.
    
    
**Beispiel**
    
Wenn in Ihrem Konto Protokolle beliebiger Art lediglich 15 Tage lang aufbewahrt werden sollen, führen Sie zum Beispiel den folgenden Befehl aus:

```
ibmcloud at option -r 15 -a
```
{: codeblock}

In der Ausgabe wird für jeden Bereich (Space) im Konto ein Eintrag aufgelistet, der Informationen zum Aufbewahrungszeitraum enthält:

```
+-----------------------------------------+-----------+
|               SPACEID                   | RETENTION |
+-----------------------------------------+-----------+
| d35da1e3-b345-475f-8502-bx cfgh436902a3 |        15 |
+-----------------------------------------+-----------+
| fdew45e3-b345-4365-8502-bx cfghrfthy5a3 |        15 |
+-----------------------------------------+-----------+
```
{: screen}

## Protokollaufbewahrungsrichtlinie für einen Bereich (Space) festlegen
{: #set_retention_policy_account}

Führen Sie die folgenden Schritte aus, um den Aufbewahrungszeitraum für einen {{site.data.keyword.cloud_notm}}-Bereich (Space) festzulegen:

1. Melden Sie sich bei {{site.data.keyword.cloud_notm}} an. 

    Melden Sie sich durch Ausführen des Befehls [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) bei {{site.data.keyword.cloud_notm}} an und führen Sie dann den Befehl [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) aus, um festzulegen, für welche Organisation und welchen Bereich (Space) der {{site.data.keyword.cloudaccesstrailshort}}-Service bereitgestellt werden soll.
    
2. Legen Sie den Aufbewahrungszeitraum fest. Führen Sie den folgenden Befehl aus:

    ```
    ibmcloud at option -r Number_of_days
    ```
    {: codeblock}
    
    Dabei gilt Folgendes: 
	* *-r* ist die Option, die angegeben werden muss, um einen Aufbewahrungszeitraum festzulegen.
	* *Number_of_days* ist eine ganze Zahl, die den Aufbewahrungszeitraum für Ereignisse in Tagen definiert.
    
    
**Beispiel**
    
Wenn in einem Bereich (Space) Ereignisse ein Jahr lang aufbewahrt werden sollen, führen Sie zum Beispiel den folgenden Befehl aus:

```
ibmcloud at option -r 365
```
{: codeblock}

Die Ausgabe sieht wie folgt aus:

```
+-----------------------------------------+-----------+
|               SPACEID                   | RETENTION |
+-----------------------------------------+-----------+
| d35da1e3-b345-475f-8502-bx cfgh436902a3 |       365 |
+-----------------------------------------+-----------+
```
{: screen}


