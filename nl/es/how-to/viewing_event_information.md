---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, view events

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

# Visualización de la información de sucesos
{: #viewing_event_status}

Utilice el mandato `ibmcloud at status` para obtener información sobre los sucesos que se recopilan y almacenan en {{site.data.keyword.cloudaccesstrailshort}} para un espacio de {{site.data.keyword.Bluemix}}.
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} está en desuso. A partir del 9 de mayo de 2019, no se pueden suministrar nuevas instancias de {{site.data.keyword.cloudaccesstrailshort}}. Las instancias existentes del plan premium recibirán soporte hasta el 30 de septiembre de 2019. Para seguir supervisando la actividad de la cuenta de {{site.data.keyword.cloud_notm}} suministre una instancia de [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}


Puede obtener información sobre el tamaño del registro de sucesos, el número de registros y sobre si los sucesos están o no disponibles para su análisis en Kibana. 

Siga los pasos siguientes para ver información sobre el registro de sucesos:

## Paso 1: Iniciar sesión en {{site.data.keyword.cloud_notm}}
{: #viewing_event_status_step1}

Inicie una sesión en {{site.data.keyword.cloud_notm}}. Siga estos pasos:

1. Ejecute el mandato [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) para iniciar una sesión en {{site.data.keyword.cloud_notm}}.
2. Ejecute el mandato [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) para definir la organización y el espacio donde desea suministrar el servicio {{site.data.keyword.cloudaccesstrailshort}}.

**Nota:** establezca la organización y el espacio donde se suministra {{site.data.keyword.cloudaccesstrailshort}}.

## Paso 2: Identificar los sucesos que están disponibles
{: #viewing_event_status_step2}

Utilice el mandato `ibmcloud at status` para ver información sobre los sucesos que están disponibles en un dominio del espacio.

* Para obtener información sobre los sucesos de un dominio del espacio, ejecute el mandato `ibmcloud at status`.
* Para obtener información sobre los sucesos en el dominio de la cuenta, ejecute el mandato `ibmcloud at status` con la opción `-a`.

```
$ ibmcloud at status -a -s YYYY-MM-DD -e YYYY-MM-DD 
```
{: codeblock}
    
donde
    
* *-a* se utiliza para especificar que la solicitud se aplica al dominio de la cuenta.
* *-s* se utiliza para establecer la fecha de inicio en Hora Universal Coordinada (UTC): *AAAA-MM-DD*.
* *-e* se utiliza para establecer la fecha final en Hora Universal Coordinada (UTC): *AAAA-MM-DD*.

Por ejemplo, para ver los sucesos que están disponibles durante las 2 últimas semanas en un dominio del espacio, ejecute el mandato siguiente:

```
$ ibmcloud at status
```
{: codeblock}
    
Por ejemplo, el resultado de ejecutar este mandato es:
    
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

**Nota:** El servicio {{site.data.keyword.cloudaccesstrailshort}} es un servicio global que utiliza la Hora Universal Coordinada (UTC). Los días se definen como días UTC. Para obtener sucesos correspondientes a un día en hora local, es posible que tenga que descargar varios días UTC.
	














