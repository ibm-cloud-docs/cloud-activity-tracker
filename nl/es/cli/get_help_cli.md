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

# Obtención de ayuda sobre cómo utilizar la CLI de Activity Tracker
{: #get_help_cli}

La CLI de {{site.data.keyword.cloudaccesstrailshort}} ofrece diferentes tipos de ayuda: ayuda general para obtener información sobre la CLI y los mandatos soportados, ayuda de mandatos para aprender a utilizar un mandato o ayuda de submandatos para aprender a utilizar los submandatos de un mandato. {:shortdesc}


## Obtención de ayuda general
{: #general_cli_help}

Para obtener información general sobre la CLI y los mandatos soportados, siga los pasos siguientes: 

1. Inicie una sesión en una región, organización y espacio de {{site.data.keyword.Bluemix_notm}}.  

    Por ejemplo, para iniciar una sesión en la región EE.UU. sur, ejecute el mandato siguiente:
	
	```
    bx login -a https://api.ng.bluemix.net
    ```
    {: codeblock}
    
2. Obtenga una lista de la información sobre los mandatos soportados y la CLI. Ejecute el mandato siguiente:

    ```
    bx cf at help
    ```
    {: codeblock}
    
    

## Obtención de ayuda sobre un mandato
{: #command_cli_help}

Para obtener ayuda sobre cómo utilizar un mandato, siga los pasos siguientes: 

1. Inicie una sesión en una región, organización y espacio de {{site.data.keyword.Bluemix_notm}}.  

    Por ejemplo, para iniciar una sesión en la región EE.UU. sur, ejecute el mandato siguiente:
	
	```
    bx login -a https://api.ng.bluemix.net
    ```
    {: codeblock}
    
2. Obtenga la lista de mandatos soportados e identifique el que necesita. Ejecute el mandato:

    ```
    bx cf at help
    ```
    {: codeblock}

3. Obtenga ayuda sobre el mandato. Ejecute el mandato siguiente:

    ```
    bx cf at help *Mandato*
    ```
    {: codeblock}
    
    donde *Mandato* es el nombre de un mandato de CLI, por ejemplo *status*.



## Obtención de ayuda sobre un submandato
{: #subcommand_cli_help}

Un mandato puede tener submandatos. Para obtener ayuda sobre los submandatos, siga los pasos siguientes: 

1. Inicie una sesión en una región, organización y espacio de {{site.data.keyword.Bluemix_notm}}.  

    Por ejemplo, para iniciar una sesión en la región EE.UU. sur, ejecute el mandato siguiente:
	
	```
    bx login -a https://api.ng.bluemix.net
    ```
    {: codeblock}
    
2. Obtenga la lista de mandatos soportados e identifique el que necesita. Ejecute el mandato:

    ```
    bx cf at help
    ```
    {: codeblock}

3. Obtenga ayuda sobre el mandato e identifique los submandatos soportados. Ejecute el mandato siguiente:

    ```
    bx cf at help *Mandato*
    ```
    {: codeblock}
    
    donde *Mandato* es el nombre de un mandato de CLI, por ejemplo *session*.

4. Obtenga ayuda sobre el mandato e identifique los submandatos soportados. Ejecute el mandato siguiente:

    ```
    bx cf at *Mandato* help *Submandato*
    ```
    {: codeblock}
    
    donde  
    
    * *Mandato* es el nombre de un mandato de CLI, por ejemplo *status*.
    * *Submandato* es el nombre de un submandato soportado, por ejemplo, para el mandato *session*, un submandato válido es *list*.




