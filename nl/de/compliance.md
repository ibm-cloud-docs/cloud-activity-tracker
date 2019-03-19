---

copyright:
  years: 2016, 2019
lastupdated: "2019-01-23"

---


{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# Konformität
{: #compliance}

[{{site.data.keyword.Bluemix}} bietet eine Cloud-Plattform und Services, die den strengen Sicherheitsstandards von IBM entsprechen.](/docs/security/compliance.html#compliance). Der {{site.data.keyword.cloudaccesstraillong}}-Service ist ein DevOps-Service, der für {{site.data.keyword.cloud_notm}} erstellt wurde. 
{:shortdesc}


## Datenschutz-Grundverordnung

Mit der DSGVO (Datenschutz-Grundverordnung) soll in der gesamten EU ein harmonisierter Rechtsrahmen für den Datenschutz geschaffen werden, in dem Bürger wieder die Kontrolle über ihre personenbezogenen Daten übernehmen, während gleichzeitig denen, die diese Daten an einem beliebigen Standort weltweit hosten und 'verarbeiten' strikte Regeln auferlegt werden. Die Verordnung führt zudem Regeln in Bezug auf den freien Datenverkehr innerhalb und außerhalb der EU ein. 

**Haftungsausschluss:** Der {{site.data.keyword.cloudaccesstrailshort}}-Service speichert und zeigt Ereignisdatensätze von Cloud-Ressourcen an, die in Ihrem Konto in {{site.data.keyword.cloud_notm}} ausgeführt werden. Personenbezogene Daten dürfen in keinem der in {{site.data.keyword.cloudaccesstrailshort}} gespeicherten Ereigniseinträge enthalten sein, da diese Daten anderen Benutzern in Ihrem Unternehmen zugänglich sind und {{site.data.keyword.IBM_notm}} zur Unterstützung des Cloud-Service zur Verfügung stehen.

### Regionen
{: #compliance_regions}

Der {{site.data.keyword.cloudaccesstrailshort}}-Service ist in den {{site.data.keyword.cloud_notm}} Public-Regionen, in denen der Service verfügbar ist, DSGVO-konform.


### Datenspeicherung
{: #compliance_data_retention}

Der {{site.data.keyword.cloudaccesstrailshort}}-Service enthält 2 Datenrepositorys, in denen Ihre Ereignisdaten gespeichert werden: 

* Ein Repository, in dem Ereignisdaten für die Analyse durch Kibana bereitstehen. Der Standard- oder Lite-Plan speichert die Daten nur in diesem Repository. Die Daten werden 3 Tage lang aufbewahrt.
* Ein Repository für die Langzeitspeicherung, in dem die Ereignisdaten für den Premium-Plan aufbewahrt werden. Die Ereignisdaten werden gespeichert, bis Sie eine Aufbewahrungsrichtlinie konfigurieren oder bis Sie die Daten manuell löschen. Standardmäßig werden Ereignisse unbegrenzt lange aufbewahrt.


### Datenlöschung
{: #compliance_data_deletion}

Beachten Sie die folgenden Informationen:

* Ereignisse, die in dem Repository gespeichert sind, das die Daten für Kibana bereitstellt, werden nach 3 Tagen gelöscht.

* Ereignisse, die im Repository für die Langzeitspeicherung gespeichert sind, werden nach einer festgelegten Anzahl von Tagen gelöscht, wenn Sie eine Aufbewahrungsrichtlinie konfigurieren, oder sie werden gelöscht, wenn Sie sie manuell löschen. 



Wenn Sie von einem kostenpflichtigen Plan in den Standard- oder Lite-Plan wechseln, werden Ereignisse, die sich im Langzeitspeicher befinden, in ungefähr einem Tag gelöscht.

Sie können jederzeit ein Support-Ticket öffnen und anfordern, dass alle Ihre Daten gelöscht werden. Informationen zum Öffnen eines IBM Support-Tickets finden Sie in [Kontaktaufnahme mit dem Support](/docs/get-support/howtogetsupport.html#getting-customer-support).



### Weitere Informationen
{: #compliance_info}

Weitere Informationen finden Sie unter:

[{{site.data.keyword.cloud_notm}} - Einhaltung von Sicherheitsbestimmungen](/docs/security/compliance.html#compliance)

[DSGVO - Offizielle Seite von {{site.data.keyword.IBM_notm}}](https://www.ibm.com/data-responsibility/gdpr/)



