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


# Ereignisinformationen anzeigen
{: #viewing_event_status}

Verwenden Sie den Befehl `ibmcloud at status`, um Informationen zu den Ereignissen zu erhalten, die in {{site.data.keyword.cloudaccesstrailshort}} für einen {{site.data.keyword.Bluemix}}-Bereich (Space) erfasst und gespeichert werden.
{:shortdesc}

Sie können Informationen zu der Größe des Ereignisprotokolls, zur Anzahl der Ereignisse und dazu abrufen, ob die Ereignisse zu Analysezwecken in Kibana verfügbar sind. 

Führen Sie die folgenden Schritte aus, um Informationen zum Ereignisprotokoll anzuzeigen:

## Schritt 1: Bei {{site.data.keyword.cloud_notm}} anmelden
{: #viewing_event_status_step1}

Melden Sie sich bei {{site.data.keyword.cloud_notm}} an. Führen Sie die folgenden Schritte aus:

1. Melden Sie sich durch Ausführen des Befehls [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) bei {{site.data.keyword.cloud_notm}} an.
2. Führen Sie den Befehl [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) aus, um festzulegen, für welche Organisation und welchen Bereich (Space) der {{site.data.keyword.cloudaccesstrailshort}}-Service bereitgestellt werden soll.

**Hinweis:** Legen Sie die Organisation und den Bereich (Space) fest, in der bzw. dem {{site.data.keyword.cloudaccesstrailshort}} bereitgestellt wird.

## Schritt 2: Ermitteln Sie, welche Ereignisse verfügbar sind.
{: #viewing_event_status_step2}

Verwenden Sie den Befehl `ibmcloud at status`, um Informationen zu den Ereignissen zu erhalten, die in einer Bereichsdomäne verfügbar sind.

* Um Informationen zu Ereignissen in einer Bereichsdomäne zu erhalten, führen Sie den Befehl `ibmcloud at status` aus.
* Um Informationen zu Ereignissen in der Kontodomäne zu erhalten, führen Sie den Befehl `ibmcloud at status` mit der Option `-a` aus.

```
$ ibmcloud at status -a -s YYYY-MM-DD -e YYYY-MM-DD 
```
{: codeblock}
    
Dabei gilt Folgendes:
    
* *-a* gibt an, dass die Anforderung für die Kontodomäne gilt.
* *-s* legt das Startdatum in koordinierter Weltzeit (Universal Coordinated Time, UTC) fest: *JJJJ-MM-TT*.
* *-e* legt das Enddatum in koordinierter Weltzeit (Universal Coordinated Time, UTC) fest: *JJJJ-MM-TT*.

Führen Sie zum Beispiel den folgenden Befehl aus, um anzuzeigen, welche Ereignisse für die letzten zwei Wochen in einer Bereichsdomäne verfügbar sind:

```
$ ibmcloud at status
```
{: codeblock}
    
Die Ausführung dieses Befehls liefert die folgende Ausgabe:
    
```
+------------+--------+------------+
|    DATE    |  COUNT | SEARCHABLE |
+------------+--------+------------+
| 2017-07-24 |    16  |    None    |
+------------+--------+------------+
| 2017-07-25 |   1224 |    All     |
+------------+--------+------------+
```
{: screen}

**Hinweis:** Der {{site.data.keyword.cloudaccesstrailshort}}-Service ist ein globaler Service und verwendet die koordinierte Weltzeit (Coordinated Universal Time, UTC). Tage sind als UTC-Tage definiert. Um die Ereignisse für einen bestimmten Tag der Ortszeit abzurufen, müssen Sie gegebenenfalls die Daten für mehrere UTC-Tage herunterladen.
	














