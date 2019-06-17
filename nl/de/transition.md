---

copyright:
  years: 2016, 2019
lastupdated: "2019-06-06"

keywords: IBM Cloud, Activity Tracker, migration

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


# Wechsel zu {{site.data.keyword.at_full_notm}}
{: #transition}

{{site.data.keyword.cloudaccesstrailfull}} wird ab 09. Mai 2019 nicht mehr verwendet. [Weitere Informationen](https://www.ibm.com/blogs/cloud-archive/2019/04/deprecating-ibm-cloud-activity-tracker/). Der Service wird durch {{site.data.keyword.at_full_notm}} ersetzt. [Weitere Informationen](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started). {:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} wird nicht mehr verwendet. Ab 09. Mai 2019 können keine neuen {{site.data.keyword.cloudaccesstrailshort}}-Instanzen mehr bereitgestellt werden. Vorhandene Instanzen des Premium-Plans werden bis 30. September 2019 unterstützt. Wenn Sie die Aktivitäten Ihres {{site.data.keyword.cloud_notm}}-Kontos weiterhin verfolgen möchten, stellen Sie eine Instanz von [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) bereit.
{: deprecated}


Führen Sie für die Migration auf {{site.data.keyword.at_full_notm}} die folgenden Schritte aus: 

1. Speichern Sie eine Kopie der Ereignisse, die in {{site.data.keyword.cloudaccesstrailfull}} gespeichert werden, für eine Langzeitsuche. Sie können die Befehlszeilenschnittstelle von {{site.data.keyword.cloudaccesstrailshort}} oder die API verwenden.  

    Stellen Sie sicher, dass Bereichsereignisse für jeden Cloud Foundry-Bereich gespeichert werden, in dem sich eine traditionelle Instanz von {{site.data.keyword.cloudaccesstrailshort}} befindet, sowie für jede Kontodomäne in jeder aktuell überwachten Region. 

    * [Ereignisse über die Befehlszeilenschnittstelle herunterladen](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-downloading_events).

    * [Ereignisse über die API herunterladen](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-downloading_events_api).

2. Stellen Sie [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-provision) bereit. 

    Sie können nur eine Instanz pro Region bereitstellen.  
    
3. Erstellen Sie Zugriffsgruppen und konfigurieren Sie diese, um Berechtigungen in {{site.data.keyword.cloud_notm}} zu verwalten.  

    * [Einem Benutzer oder einer Service-ID Administratorberechtigungen erteilen](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-iam_manage_events).

    * [Einem Benutzer oder einer Service-ID Benutzerberechtigungen erteilen](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-iam_view_events).

4. Definieren Sie Ansichten und Dashboards in {{site.data.keyword.at_full_notm}} für die Analyse und Verwaltung von Ereignissen. [Weitere Informationen](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-views). 

    Die Migration von Kibana-Dashboards in LogDNA-Dashboards ist nicht automatisiert. Sie müssen neue Dashboards manuell implementieren.  

    Hinweis: In LogDNA sind Histogramme und Kreisdiagramme die einzigen Visualisierungen, die implementiert werden können. 

5. [Optional] Konfigurieren Sie die Archivierung für die {{site.data.keyword.at_full_notm}}-Instanz.  

    Ereignisse können in {{site.data.keyword.cos_full_notm}} (COS) archiviert werden. [Weitere Informationen](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-archiving). 

    **Hinweis:** Für die Bereitstellung einer COS-Instanz für die Archivierung von Ereignissen und die Verwaltung archivierter Ereignisse sind Sie verantwortlich.  

    Dieser Schritt ist nur für {{site.data.keyword.at_full_notm}}-Instanzen mit einem kostenpflichtigen Plan erforderlich. 

6. Sie können andere Features wie z. B. [Alerting](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-alerts) erkunden. 


Wenn Sie alle Vorbereitungen getroffen haben und die Überwachung der Cloud-Aktivitäten mithilfe der traditionellen {{site.data.keyword.cloudaccesstrailshort}}-Instanzen stoppen möchten, führen Sie de folgenden Schritte aus: 

1. Löschen Sie die traditionellen {{site.data.keyword.cloudaccesstrailshort}}-Instanzen aus der {{site.data.keyword.cloud_notm}}-Konsole. 
2. Entfernen Sie alle Berechtigungen der Benutzer für die Arbeit mit diesen traditionellen Instanzen.  


