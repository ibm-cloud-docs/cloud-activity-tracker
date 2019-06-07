---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, overview

subcollection: cloud-activity-tracker

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}



# Informationen zu {{site.data.keyword.cloudaccesstrailshort}}
{: #activity_tracker_ov}

Verwenden Sie den {{site.data.keyword.cloudaccesstrailfull}}-Service, um zu verfolgen, wie Anwendungen mit {{site.data.keyword.cloud_notm}}-Service interagieren. {{site.data.keyword.cloudaccesstrailshort}} unterstützt
die Überwachung auf abnormale Aktivitäten und die Einhaltung gesetzlicher Prüfvorschriften. Die erfassten Ereignisse erfüllen den
Standard der Cloud Auditing Data Federation (CADF).
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} wird nicht mehr verwendet. Ab 09. Mai 2019 können keine neuen {{site.data.keyword.cloudaccesstrailshort}}-Instanzen mehr bereitgestellt werden. Vorhandene Instanzen des Premium-Plans werden bis 30. September 2019 unterstützt. Wenn Sie die Aktivitäten Ihres {{site.data.keyword.cloud_notm}}-Kontos weiterhin verfolgen möchten, stellen Sie eine Instanz von [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) bereit.
{: deprecated}

* {{site.data.keyword.cloudaccesstrailshort}} bietet allgemeine Sicherheitsgovernance für Ihre IT-Ressourcen in der Cloud.
* {{site.data.keyword.cloudaccesstrailshort}} bietet eine Lösung für Administratoren zum Erfassen, Speichern, Anzeigen, Suchen und Überwachen der API-Aktivität von einem einzigen Punkt aus.
* {{site.data.keyword.cloudaccesstrailshort}} bietet Funktionen zum Herunterladen von Ereignissen, die Sie anschließend zum Erstellen eines Prüfprotokollberichts verwenden können. Sie benötigen diese Berichte möglicherweise, damit Ihre Organisation interne Vorschriften und externe branchen- oder länderspezifische Vorschriften einhalten kann.

Die Einhaltung interner Richtlinien und branchenspezifischer Vorschriften ist eine wichtige Voraussetzung in jeder Unternehmensstrategie, unabhängig davon, wo Anwendungen ausgeführt werden: vor Ort, in einer Hybrid-Cloud oder in einer öffentlichen Cloud. Der {{site.data.keyword.cloudaccesstrailshort}}-Service liefert das Gerüst und die Funktionalität zum Überwachen von API-Aufrufen und zum Nachweisen der Einhaltung von Unternehmensrichtlinien und branchenspezifischen Marktvorschriften.

Beim Arbeiten in einer Cloudumgebung wie {{site.data.keyword.cloud_notm}} müssen Sie die Cloudstrategie zum Prüfen und Überwachen von Workloads und Daten in Übereinstimmung mit Ihren internen Richtlinien sowie mit branchen- und länderspezifischen Compliance-Anforderungen planen. Anhand der Informationen, die vom {{site.data.keyword.cloudaccesstrailshort}}-Service erfasst werden, können Sie Sicherheitsvorfälle identifizieren, unbefugten Zugriff erkennen und Vorschriften sowie interne Prüfanforderungen einhalten.

Sie können die {{site.data.keyword.cloudaccesstrailshort}}-Aktivitätenprotokolle beispielsweise verwenden, um die folgenden Informationen zu ermitteln:

* Benutzer, die API-Aufrufe an Cloud-Services abgesetzt haben
* Ausgangs-IP-Adresse, von der die API-Aufrufe stammen
* Zeitpunkt (Zeitmarke), an dem die API-Aufrufe erfolgt sind
* Status des API-Aufrufs


## Erfassen von Ereignissen
{: #activity_tracker_ov_collect}

Der {{site.data.keyword.cloudaccesstrailshort}}-Service erfasst Aktivitätsdaten, die sich auf API-Aufrufe und andere Aktionen beziehen, die für ausgewählte Cloud-Services in {{site.data.keyword.cloud_notm}} ausgeführt werden. 

* Ereignisse werden automatisch erfasst. 
* Die in {{site.data.keyword.cloudaccesstrailshort}} erfassten Ereignisse erfüllen den Standard der Cloud Auditing Data Federation (CADF). Der CADF-Standard definiert ein vollständiges Ereignismodell, das alle Informationen beinhaltet, die zum Zertifizieren, Verwalten und Prüfen der Sicherheit von Anwendungen in Cloud-Umgebungen erforderlich sind.
* {{site.data.keyword.cloudaccesstrailshort}} speichert und gruppiert Ereignisse nach Domäne. Es gibt eine Kontodomäne pro Region und eine Bereichsdomäne (Spacedomäne) pro Cloud Foundry-Bereich. 

Das CADF-Ereignismodell umfasst die folgenden Komponenten:

<table>
  <caption>Tabelle 1. Verfügbare Komponenten in einem CADF-Ereignismodell</caption>
  <tr>
    <th>Komponente</th>
	<th>Beschreibung</th>
  </tr>
  <tr>
    <td>Aktion</td>
	<td>Die Aktion ist die Operation oder Aktivität, die ein Initiator ausführt, auszuführen versucht, oder auf deren Beendigung der Initiator wartet.</td>
  </tr>
  <tr>
    <td>Initiator</td>
	<td>Der Initiator ist die Ressource, die einen API-Aufruf absetzt und ein CADF-Ereignis generiert. Welches Ereignis ausgelöst wird, ist von der Aktion abhängig, die von dem API-Aufruf angefordert wird.</td>
  </tr>
  <tr>
    <td>Beobachter</td>
	<td>Der Beobachter ist die Ressource, die einen CADF-Datensatz aus den in einem CADF-Ereignis verfügbaren Informationen erstellt und speichert.</td>
  </tr>
  <tr>
    <td>Ergebnis</td>
	<td>Das Ergebnis ist der Status, den die Aktion im Ziel herbeiführt.</td>
  </tr>
  <tr>
    <td>Ziel</td>
	<td>Das Ziel ist die Ressource, in der die Aktion ausgeführt wird, auszuführen versucht wird oder auf die Beendigung wartet.</td>
  </tr>
</table>


Beachten Sie Folgendes beim Arbeiten mit dem {{site.data.keyword.cloudaccesstrailshort}}-Protokoll in der öffentlichen {{site.data.keyword.IBM_notm}} Cloud:

* Sie können nur Prüfdatensätze für API-Aufrufe speichern, die sich auf in der öffentlichen {{site.data.keyword.IBM_notm}} Cloud ausgeführte Ressourcen beziehen.
* Nur der Speicher der öffentlichen {{site.data.keyword.IBM_notm}} Cloud wird zum Erfassen von Ereignissen verwendet.
* Die Informationen werden 3 Tage gespeichert. Danach werden die Informationen mit der FIFO-Methode (First In, First Out) gelöscht.
* CADF-Ereignisse des Typs *Aktivität* werden vom {{site.data.keyword.cloudaccesstrailshort}}-Service unterstützt.


## Bereitstellen von Activity Tracker
{: #activity_tracker_ov_provision}

Um Ereignisse anzeigen zu können, die über eine Kontodomäne verfügbar sind, müssen Sie den {{site.data.keyword.cloudaccesstrailshort}}-Service in einem Cloud Foundry-Bereich (Space) in der Region bereitstellen, in der die API-Aktivität überwacht werden soll. Nur der **Kontoeigner** kann Ereignisse für ein Konto anzeigen.

Zum Anzeigen von Ereignissen, die über eine Bereichsdomäne (Space Domain) verfügbar sind, müssen Sie den {{site.data.keyword.cloudaccesstrailshort}}-Service in dem Bereich (Space) bereitstellen, in der die API-Aktivität überwacht werden soll.

Informationen zur Vorgehensweise beim Bereitstellen des {{site.data.keyword.cloudaccesstrailshort}}-Service finden Sie in [{{site.data.keyword.cloudaccesstrailshort}}-Service bereitstellen](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-provision#provision).



## Aktivitätenprotokolle analysieren
{: #activity_tracker_ov_analyze}

Sie können Aktivitätenprotokolle mit der {{site.data.keyword.cloudaccesstrailshort}}-Benutzerschnittstelle in {{site.data.keyword.cloud_notm}} oder mit dem Open-Source-Tool Kibana analysieren. Sie können Ereignisse überwachen, die in einem bestimmten Bereich oder auf Kontoebene verfügbar sind.

Sie können Aktivitätenprotokolle für die letzten 24 Stunden mit der {{site.data.keyword.cloudaccesstrailshort}}-Benutzerschnittstelle in {{site.data.keyword.cloud_notm}} suchen, analysieren und überwachen. Weitere Informationen finden Sie in [Zur {{site.data.keyword.cloudaccesstrailshort}}-Benutzerschnittstelle navigieren](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-launch_at_ui#launch_at_ui).

Sie können Aktivitätenprotokolle für die letzten 3 Tage mit Kibana über das Kibana-Dashboard in {{site.data.keyword.cloudaccesstrailshort}} suchen, analysieren und überwachen. Sie können auch eigene angepasste Dashboards erstellen. * **Hinweis:** Dieses Feature ist für Benutzer im Rahmen des **Premium-Plans** verfügbar.

* Weitere Informationen zum Starten von Kibana finden Sie in [Zum Kibana-Dashboard navigieren](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-launch_kibana#launch_kibana). 
* Eine Liste der Felder, die Sie zum Analysieren von Ereignissen in Kibana verwenden können, finden Sie in [{{site.data.keyword.cloudaccesstrailshort}}-Ereignisfelder](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-at_event#at_event).



## Regionen
{: #activity_tracker_ov_regions}

Der {{site.data.keyword.cloudaccesstrailshort}}-Service ist in den folgenden Regionen verfügbar:

* Deutschland
* Sydney
* Vereinigtes Königreich (nur Lite-Plan ist verfügbar)
* Vereinigte Staaten (Süden)


## Serviceplan
{: #activity_tracker_ov_plan}

Der {{site.data.keyword.cloudaccesstrailshort}}-Service stellt mehrere Pläne bereit.

Sie können einen Plan über die Benutzerschnittstelle (UI) für {{site.data.keyword.cloud_notm}} oder über die Befehlszeile ändern. Sie können für Ihren Plan jederzeit ein Upgrade oder eine Herabstufung vornehmen. Weitere Informationen zu Upgrades des Serviceplans finden Sie in [Plan ändern](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-change_plan#change_plan). 

Die folgende Tabelle liefert einen Überblick über die verfügbaren Pläne:

<table>
    <caption>Tabelle 1. Funktionen für Ereignisaufnahme, -aufbewahrung und -export</caption>
      <tr>
        <th>Plan</th>
        <th>Ereignisaufnahme</th>
        <th>Ereignisaufbewahrung</th>
		<th>Ereignisexport</th>
      </tr>
      <tr>
        <td>Lite (Standardwert)</td>
        <td>Nein</td>
        <td>Letzte 3 Tage</td>
		<td>Nein</td>
      </tr>
      <tr>
        <td>Premium</td>
        <td>Ja</td>
        <td>Konfigurierbare Anzahl von Tagen</td>
		<td>Ja</td>
      </tr>
</table>

<table>
    <caption>Tabelle 2. Funktionen zum Verwalten und Anzeigen von Ereignissen</caption>
      <tr>
        <th>Plan</th>
		    <th>API</th>
		    <th>CLI</th>
        <th>Kibana</th>
      </tr>
      <tr>
        <td>Lite (Standardwert)</td>
		    <td>Nein</td>
		    <td>Nein</td>
        <td>Nein</td>
      </tr>
      <tr>
        <td>Premium</td>
		    <td>Ja</td>
		    <td>Ja</td>
        <td>Ja</td>
      </tr>
</table>

**Hinweis:** Die monatlichen Kosten für den Ereignisspeicher werden als Durchschnittswert für den Abrechnungszyklus berechnet.

## Sicherheit
{: #activity_tracker_ov_security}

Beachten Sie beim Arbeiten mit dem {{site.data.keyword.cloudaccesstrailshort}}-Service die folgenden Informationen zur Sicherheit:

* IBM Services, die {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse erstellen, entsprechen der Sicherheitsrichtlinie für {{site.data.keyword.IBM_notm}} Cloud. Weitere Informationen finden Sie unter [Vertrauen Sie der Sicherheit und dem Datenschutz von IBM Cloud ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/cloud/security){: new_window}.
* Der {{site.data.keyword.cloudaccesstrailshort}}-Service erfasst vom Benutzer eingeleitete Aktionen, die den Status von Cloud-Services ändern. Über diese Informationen ist kein direkter Zugriff auf Datenbanken oder Anwendungen möglich.
* Nur berechtigte Benutzer können {{site.data.keyword.cloudaccesstrailshort}}-Ereignisprotokolle anzeigen und überwachen. Jeder Benutzer wird durch eine eindeutige persönliche ID in {{site.data.keyword.cloud_notm}} identifiziert.
