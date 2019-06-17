---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, compliance

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


# Conformidad
{: #compliance}

[{{site.data.keyword.cloud_notm}} proporciona una plataforma y servicios en la nube construidos en base a los estrictos estándares de seguridad de IBM](/docs/overview?topic=overview-security#compliance). El servicio {{site.data.keyword.cloudaccesstraillong}} es un servicio DevOps creado para {{site.data.keyword.cloud_notm}}. 
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} está en desuso. A partir del 9 de mayo de 2019, no se pueden suministrar nuevas instancias de {{site.data.keyword.cloudaccesstrailshort}}. Las instancias existentes del plan premium recibirán soporte hasta el 30 de septiembre de 2019. Para seguir supervisando la actividad de la cuenta de {{site.data.keyword.cloud_notm}} suministre una instancia de [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}

## Normativa general de protección de datos

La Normativa general de protección de datos (GDPR) busca crear un marco de ley de protección de datos armonizado en toda la UE y tiene como objetivo devolver a los ciudadanos el control de sus datos personales, al tiempo que impone reglas estrictas sobre los que alojan y "procesan" estos datos, en cualquier lugar del mundo. La normativa también presenta reglas referentes a la libre circulación de datos personales dentro y fuera de la Unión Europea. 

**Descargo de responsabilidad:** el servicio {{site.data.keyword.cloudaccesstrailshort}} almacena y muestra registros de sucesos de los recursos de la nube que se ejecutan en su cuenta en {{site.data.keyword.cloud_notm}}. No se debe incluir información personal (PI) en ninguna de las entradas de sucesos almacenadas en {{site.data.keyword.cloudaccesstrailshort}}, ya que pueden acceder a estos datos a otros usuarios de la empresa, así como a {{site.data.keyword.IBM_notm}} para poder dar soporte al servicio de nube.

### Regiones
{: #compliance_regions}

El servicio {{site.data.keyword.cloudaccesstrailshort}} cumple con GDPR en las regiones de {{site.data.keyword.cloud_notm}} público en las que está disponible el servicio.


### Retención de datos
{: #compliance_data_retention}

El servicio {{site.data.keyword.cloudaccesstrailshort}} incluye 2 repositorios de datos en los que se almacenan los datos de sucesos: 

* Un repositorio en el que los datos de sucesos están disponibles para su análisis a través de Kibana. El plan estándar o lite solo almacena datos en este repositorio. Los datos se conservan durante 3 días.
* Un repositorio de almacenamiento a largo plazo que aloja datos de sucesos del plan premium. Los datos de sucesos se almacenan hasta que se configura una política de retención o hasta que se suprimen manualmente. De forma predeterminada, los sucesos se conservan indefinidamente.


### Supresión de datos
{: #compliance_data_deletion}

Tenga en cuenta la información siguiente:

* Los sucesos almacenados en el repositorio que proporciona los datos para Kibana se suprimen transcurridos 3 días.

* Los sucesos almacenados en el repositorio a largo plazo se suprimen transcurridos el número de días que configure en la política de retención o cuando los suprime manualmente. 



Si pasa un plan de pago al plan estándar o lite, los sucesos que se encuentran en el repositorio de almacenamiento a largo plazo se suprimirán en aproximadamente un día.

En cualquier momento puede abrir una incidencia de soporte y solicitar que se supriman todos los datos. Para obtener información sobre cómo abrir una incidencia de soporte de IBM, consulte [Obtención de soporte](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support).



### Más información
{: #compliance_info}

Para obtener más información, consulte:

[Conformidad de seguridad de {{site.data.keyword.cloud_notm}}](/docs/overview?topic=overview-security#compliance)

[GDPR - Página oficial de {{site.data.keyword.IBM_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/data-responsibility/gdpr/){:new_window}



