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


# Migración a {{site.data.keyword.at_full_notm}}
{: #transition}

{{site.data.keyword.cloudaccesstrailfull}} ha quedado en desuso desde el 9 de mayo de 2019. [Más información](https://www.ibm.com/blogs/cloud-archive/2019/04/deprecating-ibm-cloud-activity-tracker/). El servicio ha sido sustituido por {{site.data.keyword.at_full_notm}}. [Más información](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started).
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} está en desuso. A partir del 9 de mayo de 2019, no se pueden suministrar nuevas instancias de {{site.data.keyword.cloudaccesstrailshort}}. Las instancias existentes del plan premium recibirán soporte hasta el 30 de septiembre de 2019. Para seguir supervisando la actividad de la cuenta de {{site.data.keyword.cloud_notm}} suministre una instancia de [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}


Siga los pasos siguientes para migrar a {{site.data.keyword.at_full_notm}}: 

1. Guarde una copia de los registros que se almacenan en {{site.data.keyword.cloudaccesstrailfull}} para realizar búsquedas a largo plazo. Puede utilizar la CLI de {{site.data.keyword.cloudaccesstrailshort}} o la API. 

    Asegúrese de guardar sucesos de espacio para cada espacio de Cloud Foundry donde tenga una instancia antigua de {{site.data.keyword.cloudaccesstrailshort}}, y para cada dominio de cuenta de cada región que supervise actualmente.

    * [Descarga de sucesos mediante la CLI](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-downloading_events).

    * [Descarga de sucesos mediante la API](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-downloading_events_api).

2. Suministre [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-provision).

    Solo puede suministrar una instancia por región. 
    
3. Cree y configure grupos de acceso para gestionar permisos en {{site.data.keyword.cloud_notm}}. 

    * [Cómo otorgar permisos de administración a un usuario o ID de servicio](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-iam_manage_events).

    * [Cómo otorgar permisos de usuario a un usuario o ID de servicio](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-iam_view_events).

4. Defina vistas y paneles de control en {{site.data.keyword.at_full_notm}} para analizar y gestionar sucesos. [Más información](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-views).

    La migración de paneles de control de Kibana a paneles de control de LogDNA no es automática. Tiene que implementar los nuevos paneles de control de forma manual. 

    Tenga en cuenta que, en LogDNA, los histogramas y los gráficos de tarta son las únicas visualizaciones que puede implementar.

5. [Opcional] Configure el archivado para su instancia de {{site.data.keyword.at_full_notm}}. 

    Puede archivar sucesos en {{site.data.keyword.cos_full_notm}} (COS). [Más información](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-archiving).

    **Nota:** usted es el responsable de suministrar una instancia de COS que se utilice para archivar sucesos y de mantener los sucesos archivados. 

    Este paso solo es necesario para instancias de {{site.data.keyword.at_full_notm}} que tengan un plan de pago.

6. Explore otras características, como el [sistema de alertas](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-alerts).


Cuando esté listo para dejar de supervisar su actividad en la nube a través de instancias antiguas de {{site.data.keyword.cloudaccesstrailshort}}, siga los siguientes pasos:

1. Suprima las instancias antiguas de {{site.data.keyword.cloudaccesstrailshort}} de la consola de {{site.data.keyword.cloud_notm}}.
2. Elimine los permisos de los usuarios para trabajar con dichas instancias antiguas. 


