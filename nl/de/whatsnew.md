---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, news

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

# Neuerungen
{: #whatsnew}

Informieren Sie sich über die neuesten Funktionen und Integrationen für {{site.data.keyword.cloudaccesstrailshort}}.
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} wird nicht mehr verwendet. Ab 09. Mai 2019 können keine neuen {{site.data.keyword.cloudaccesstrailshort}}-Instanzen mehr bereitgestellt werden. Vorhandene Instanzen des Premium-Plans werden bis 30. September 2019 unterstützt. Wenn Sie die Aktivitäten Ihres {{site.data.keyword.cloud_notm}}-Kontos weiterhin verfolgen möchten, stellen Sie eine Instanz von [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) bereit.
{: deprecated}

Die aktuelle Liste der Services, die mit {{site.data.keyword.cloudaccesstrailshort}} integriert sind, finden Sie in [Cloud-Services](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-cloud_services#cloud_services).
{: important}


## März 2019
{: #march2019}

* {{site.data.keyword.cloudaccesstrailshort}}-Befehlszeilenschnittstelle

Es wurde ein Problem bei der Activity Tracker-Befehlszeilenschnittstelle festgestellt. Dieses Problem wird mit einer neuen Version der Befehlszeilenschnittstelle behoben. 

Wenn Sie sich über die Befehlszeile bei {{site.data.keyword.cloud_notm}} anmelden, indem Sie `ibmcloud login` verwenden, und dann {{site.data.keyword.cloudaccesstrailshort}}-Befehle ausführen, wird der Fehler `Fehler: Keine Berechtigung` für jeden ausgeführten {{site.data.keyword.cloudaccesstrailshort}}-Befehl ausgegeben.  

Als temporäre Lösung melden Sie sich mit den nachfolgend aufgeführten Befehle bei {{site.data.keyword.cloud_notm}} an, um die Befehlszeilenschnittstelle weiter zu verwenden. 

| Region | Befehl |
|--------|---------|
| `Vereinigte Staaten (Süden)` | `bx login -a api.ng.bluemix.net -o OrgName -s SpaceName` |
| `EU (DE)`    | `bx login -a api.eu-de.bluemix.net -o OrgName -s SpaceName` |
| `EU (DE)`    | `bx login -a api.au-syd.bluemix.net -o OrgName -s SpaceName` |
{: caption="Tabelle 1. Befehle" caption-side="top"} 

## Februar 2019
{: #february2019}

* **Sie können den {{site.data.keyword.GlobalizationPipeline_short}}-Service mit {{site.data.keyword.cloudaccesstrailshort}} überwachen. **

    {{site.data.keyword.GlobalizationPipeline_short}} ermöglicht es Anwendungsentwicklern, übersetzte Anwendungen schnell für globale Kunden freizugeben.

    Weitere Informationen zu den {{site.data.keyword.cloudaccesstrailshort}}-Ereignissen finden Sie in [Von {{site.data.keyword.GlobalizationPipeline_short}} generierte Ereignisse](/docs/services/GlobalizationPipeline?topic=GlobalizationPipeline-gpat_events#gpat_events).








