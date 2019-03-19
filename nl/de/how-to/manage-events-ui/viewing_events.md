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



# Ereignisse anzeigen
{: #view_acc_events}

Sie können Ereignisse über die Benutzerschnittstelle (UI) für {{site.data.keyword.cloudaccesstrailshort}} in der {{site.data.keyword.cloud_notm}}-Konsole oder über Kibana anzeigen.
{:shortdesc}
   

## Ereignisse für ein Konto anzeigen
{: #view_acc_events_account_events}

Sie können Ereignisse in einer Kontodomäne von {{site.data.keyword.cloudaccesstrailshort}} über die Benutzerschnittstelle (UI) für {{site.data.keyword.cloudaccesstrailshort}} oder über Kibana anzeigen.

Ein **Kontoeigner** verfügt über die Berechtigungen zum Anzeigen von Ereignissen in einer Kontodomäne von {{site.data.keyword.cloudaccesstrailshort}} über die Benutzerschnittstelle (UI) für {{site.data.keyword.cloudaccesstrailshort}} oder über Kibana.

Als ein **Mitglied eines Kontos** sollten Sie die folgenden Informationen berücksichtigen, wenn Sie Ereignisse für ein Konto in einer Region anzeigen wollen:

* Sie müssen in dem Bereich, in dem {{site.data.keyword.cloudaccesstrailshort}} bereitgestellt wird, über die Rolle *Entwickler* verfügen. Weitere Informationen finden Sie in [CF-Rolle erteilen](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_cf_role).

* Sie müssen über eine IAM-Richtlinie für den {{site.data.keyword.loganalysisshort}}-Service mit der Rolle *Aufgabenberechtigter* in dieser Region verfügen. Die Rolle des Anzeigeberechtigten ist die erforderliche minimale IAM-Rolle. Weitere Informationen finden Sie im Abschnitt [IAM-Berechtigungen erteilen](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_iam_policy).

* Sie können Ereignisse in Kibana anzeigen. Weitere Informationen zum Starten von Kibana finden Sie in [Über einen Web-Browser zu Kibana navigieren](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_kibana.html#launch_Kibana_from_browser).



## Ereignisse für einen Bereich (Space) anzeigen
{: #view_acc_events_space_events}

Sie können Ereignisse in einer Bereichsdomäne von {{site.data.keyword.cloudaccesstrailshort}} über die Benutzerschnittstelle (UI) für {{site.data.keyword.cloudaccesstrailshort}} anzeigen. Wenn Sie über einen Plan vom Typ 'Premium' verfügen, können Sie Ereignisse auch über Kibana anzeigen.

Ein **Kontoeigner** verfügt über die Berechtigungen zum Anzeigen von Ereignissen für jede beliebige {{site.data.keyword.cloudaccesstrailshort}}-Bereichsdomäne.

Als ein **Mitglied eines Kontos** müssen Sie in dem Bereich (Space), in dem {{site.data.keyword.cloudaccesstrailshort}} bereitgestellt wird, über die Rolle *developer* verfügen.


