---

copyright:
  years: 2016, 2017

lastupdated: "2017-09-25"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# Activity Tracker
{: #activity_tracker_ov}

Verwenden Sie den {{site.data.keyword.cloudaccesstrailfull}}-Service, um zu verfolgen, wie
Anwendungen mit {{site.data.keyword.Bluemix}}-Services interagieren. {{site.data.keyword.cloudaccesstrailshort}} unterstützt
die Überwachung auf abnormale Aktivitäten und die Einhaltung gesetzlicher Prüfvorschriften. Die erfassten Ereignisse erfüllen den
Standard der Cloud Auditing Data Federation (CADF).
{:shortdesc}

* {{site.data.keyword.cloudaccesstrailshort}} bietet allgemeine Sicherheitsgovernance für Ihre IT-Ressourcen in der Cloud.
* {{site.data.keyword.cloudaccesstrailshort}} bietet eine Lösung für Netzadministratoren zum Erfassen, Speichern, Anzeigen, Suchen und Überwachen der API-Aktivität von einem Punkt aus.
* {{site.data.keyword.cloudaccesstrailshort}} bietet Funktionen zum Herunterladen von Ereignissen, die Sie anschließend zum Erstellen eines Prüfprotokollberichts verwenden können. Sie benötigen diese Berichte möglicherweise, damit Ihre Organisation interne Vorschriften und externe branchen- oder länderspezifische Vorschriften einhalten kann.

Die Einhaltung interner Richtlinien und branchenspezifischer Vorschriften ist eine wichtige Voraussetzung in jeder Unternehmensstrategie, unabhängig davon, wo Anwendungen ausgeführt werden: vor Ort, in einer Hybrid-Cloud oder in einer öffentlichen Cloud. Der {{site.data.keyword.cloudaccesstrailshort}}-Service liefert das Gerüst und die Funktionalität zum Überwachen von API-Aufrufen und zum Nachweisen der Einhaltung von Unternehmensrichtlinien und branchenspezifischen Marktvorschriften.

Beim Arbeiten in einer Cloudumgebung wie {{site.data.keyword.Bluemix_notm}} müssen Sie die Cloudstrategie zum Prüfen und Überwachen von Workloads und Daten in Übereinstimmung mit Ihren internen Richtlinien sowie mit branchen- und länderspezifischen Compliance-Anforderungen planen. Anhand der Informationen, die vom {{site.data.keyword.cloudaccesstrailshort}}-Service erfasst werden, können Sie Sicherheitsvorfälle identifizieren, unbefugten Zugriff erkennen und Vorschriften sowie interne Prüfanforderungen einhalten.

Sie können die {{site.data.keyword.cloudaccesstrailshort}}-Aktivitätenprotokolle beispielsweise verwenden, um die folgenden Informationen zu ermitteln: 

* Benutzer, die API-Aufrufe an Cloud-Services abgesetzt haben
* Ausgangs-IP-Adresse, von der die API-Aufrufe stammen
* Zeitpunkt (Zeitmarke), an dem die API-Aufrufe erfolgt sind
* Status des API-Aufrufs


## Activity Tracker in Bluemix bereitstellen
{: #provision}

Sie müssen den {{site.data.keyword.cloudaccesstrailshort}}-Service in jedem Bereich Ihres {{site.data.keyword.Bluemix_notm}}-Kontos bereitstellen, in dem Sie API-Aktivitäten für Cloud-Services überwachen möchten, die in dem betreffenden Bereich ausgeführt werden.

Informationen zur Vorgehensweise beim Bereitstellen des {{site.data.keyword.cloudaccesstrailshort}}-Service finden Sie in [{{site.data.keyword.cloudaccesstrailshort}}-Service bereitstellen](/docs/services/cloud-activity-tracker/how-to/provision.html#provision).



## Aktivitätenprotokolle erfassen
{: #collect}

Der {{site.data.keyword.cloudaccesstrailshort}}-Service erfasst nur Aktivitätsdaten, die sich auf API-Aufrufe beziehen, und andere Aktionen, die für ausgewählte Cloud-Services in {{site.data.keyword.Bluemix_notm}} ausgeführt werden. Eine Liste der Services finden Sie in [Unterstützte Cloud-Services](/docs/services/cloud-activity-tracker/cloud_services.html#cloud_services).

* Ereignisse werden automatisch erfasst. 
* Die in {{site.data.keyword.cloudaccesstrailshort}} erfassten Ereignisse erfüllen den CADF-Standard (CADF = Cloud Auditing Data Federation). Der CADF-Standard definiert ein vollständiges Ereignismodell, das alle Informationen beinhaltet, die zum Zertifizieren, Verwalten und Prüfen der Sicherheit von Anwendungen in Cloud-Umgebungen erforderlich sind.

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


Beachten Sie Folgendrs beim Arbeiten mit dem {{site.data.keyword.cloudaccesstrailshort}}-Protokoll in der öffentlichen {{site.data.keyword.IBM_notm}} Cloud:

* Sie können nur Prüfdatensätze für API-Aufrufe speichern, die sich auf Ressourcen beziehen, die in der öffentlichen {{site.data.keyword.IBM_notm}} Cloud ausgeführt werden.
* Nur der Speicher der öffentlichen {{site.data.keyword.IBM_notm}} Cloud wird zum Erfassen von Ereignissen verwendet.
* Die Informationen werden 3 Tage gespeichert. Danach werden die Informationen nach dem First In/First Out-Prinzip gelöscht.
* CADF-Ereignisse des Typs *Aktivität* werden vom {{site.data.keyword.cloudaccesstrailshort}}-Service unterstützt.



## Aktivitätenprotokolle analysieren
{: #analyze}

Sie können Aktivitätenprotokolle mit der {{site.data.keyword.cloudaccesstrailshort}}-Benutzerschnittstelle in {{site.data.keyword.Bluemix_notm}} analysieren oder mit dem Open-Source-Tool Kibana. Sie können Ereignisse überwachen, die in einem bestimmten Bereich oder auf Kontoebene verfügbar sind.

Sie können Aktivitätenprotokolle für die letzten 24 Stunden mit der {{site.data.keyword.cloudaccesstrailshort}}-Benutzerschnittstelle in {{site.data.keyword.Bluemix_notm}} suchen, analysieren und überwachen. Weitere Informationen finden Sie in [Zur {{site.data.keyword.cloudaccesstrailshort}}-Benutzerschnittstelle navigieren](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_at_ui.html#launch_at_ui).

Sie können Aktivitätenprotokolle für die letzten 3 Tage mit Kibana über das Kibana-Dashboard in {{site.data.keyword.cloudaccesstrailshort}} suchen, analysieren und überwachen, oder indem Sie eigene angepasste Dashboards erstellen. * **Anmerkung:** Dieses Feature ist für Benutzer im Rahmen des **Premium-Plans** verfügbar.

* Weitere Informationen zum Starten von Kibana finden Sie in [Zum Kibana-Dashboard navigieren](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_kibana.html#launch_kibana). 
* Eine Liste der Felder, die Sie zum Analysieren von Ereignissen in Kibana verwenden können, finden Sie in [{{site.data.keyword.cloudaccesstrailshort}}-Ereignisfelder](/docs/services/cloud-activity-tracker/reference/at_event.html#at_event).



## Regionen
{: #regions}

Der {{site.data.keyword.cloudaccesstrailshort}}-Service ist in den folgenden Regionen verfügbar:

* Vereinigte Staaten (Süden)
* Vereinigtes Königreich (Beta)


## Serviceplan
{: #plan}

Der {{site.data.keyword.cloudaccesstrailshort}}-Service stellt mehrere Pläne bereit.

Sie können einen Plan über die {{site.data.keyword.Bluemix_notm}}-Benutzerschnittstelle ändern oder über die Befehlszeile. Sie können für Ihren Plan jederzeit ein Upgrade oder eine Herabstufung vornehmen. Weitere Informationen zu Serviceplan-Upgrades in {{site.data.keyword.Bluemix_notm}} finden Sie in [Plan ändern](/docs/services/cloud-activity-tracker/plan/change_plan.html#change_plan). 

Die folgenden Tabellen enthalten eine Übersicht über die in den einzelnen  Serviceplänen verfügbaren Features:

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

**Anmerkung:** Die monatlichen Kosten für den Ereignisspeicher werden als Durchschnittswert für den Abrechnungszyklus berechnet.

## Sicherheit
{: #security}

Beachten Sie beim Arbeiten mit dem {{site.data.keyword.cloudaccesstrailshort}}-Service die folgenden Informationen zur Sicherheit:

* IBM Services, die {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse erstellen, entsprechen der Sicherheitsrichtlinie für {{site.data.keyword.IBM_notm}} Cloud. Weitere Informationen finden Sie unter [Vertrauen Sie der Sicherheit und dem Datenschutz von IBM Cloud ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/cloud-computing/learn-more/why-ibm-cloud/security/){: new_window}.
* Der {{site.data.keyword.cloudaccesstrailshort}}-Service erfasst vom Benutzer eingeleitete Aktionen, die den Status von Cloud-Services ändern. Über diese Informationen ist kein direkter Zugriff auf Datenbanken oder Anwendungen möglich.
* Nur berechtigte Benutzer können {{site.data.keyword.cloudaccesstrailshort}}-Ereignisprotokolle anzeigen und überwachen. Jeder Benutzer wird in {{site.data.keyword.Bluemix_notm}} durch eine eindeutige persönliche ID identifiziert.
