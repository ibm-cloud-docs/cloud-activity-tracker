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

# Novedades
{: #whatsnew}

Obtenga información sobre las últimas características e integraciones correspondientes a {{site.data.keyword.cloudaccesstrailshort}}.
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} está en desuso. A partir del 9 de mayo de 2019, no se pueden suministrar nuevas instancias de {{site.data.keyword.cloudaccesstrailshort}}. Las instancias existentes del plan premium recibirán soporte hasta el 30 de septiembre de 2019. Para seguir supervisando la actividad de la cuenta de {{site.data.keyword.cloud_notm}} suministre una instancia de [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}

Para ver la lista más reciente de servicios integrados con {{site.data.keyword.cloudaccesstrailshort}}, consulte [Servicios de Cloud](/docs/services/cloud-activity-tracker/reference?topic=cloud-activity-tracker-cloud_services#cloud_services).
{: important}


## Marzo de 2019
{: #march2019}

* CLI de {{site.data.keyword.cloudaccesstrailshort}}

Se ha identificado un problema con la CLI de Activity Tracker. Se publicará una nueva versión de la CLI para solucionar el problema.

Si inicia la sesión en {{site.data.keyword.cloud_notm}} desde la línea de mandatos utilizando `ibmcloud login` y, a continuación, ejecuta mandatos de {{site.data.keyword.cloudaccesstrailshort}}, recibe el siguiente error: `Error: No autorizado` en todos los mandatos de {{site.data.keyword.cloudaccesstrailshort}} que ejecuta. 

Mientras tanto, para seguir trabajando con la CLI, inicie la sesión en {{site.data.keyword.cloud_notm}} utilizando los siguientes mandatos:

| Región | Mandato |
|--------|---------|
| `EE. UU. sur` | `bx login -a api.ng.bluemix.net -o OrgName -s SpaceName` |
| `UE DE`    | `bx login -a api.eu-de.bluemix.net -o OrgName -s SpaceName` |
| `UE DE`    | `bx login -a api.au-syd.bluemix.net -o OrgName -s SpaceName` |
{: caption="Tabla 1. Mandatos" caption-side="top"} 

## Febrero de 2019
{: #february2019}

* **Puede supervisar el servicio {{site.data.keyword.GlobalizationPipeline_short}} con {{site.data.keyword.cloudaccesstrailshort}}.**

    {{site.data.keyword.GlobalizationPipeline_short}} permite que los desarrolladores de aplicaciones puedan publicar rápidamente aplicaciones traducidas a clientes globales.

    Para obtener más información sobre los sucesos de {{site.data.keyword.cloudaccesstrailshort}}, consulte [Sucesos generados por {{site.data.keyword.GlobalizationPipeline_short}}](/docs/services/GlobalizationPipeline?topic=GlobalizationPipeline-gpat_events#gpat_events).








