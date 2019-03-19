---

copyright:
  years: 2016, 2019
lastupdated: "2019-01-23"

---


{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# Conformité
{: #compliance}

[{{site.data.keyword.Bluemix}} fournit une plateforme cloud et des services qui respectent les normes strictes de sécurité d'IBM.](/docs/security/compliance.html#compliance). Le service {{site.data.keyword.cloudaccesstraillong}} est un service DevOps conçu pour {{site.data.keyword.cloud_notm}}. 
{:shortdesc}


## Règlement général sur la protection des données

Le règlement général sur la protection des données (RGPD) vise à créer une loi harmonisée sur la protection des données au sein de l'Union européenne et a pour objectif de redonner aux citoyens le contrôle de leurs données personnelles, tout en imposant des règles strictes à ceux qui hébergent et "traitent" ces données, n'importe où dans le monde. Ce règlement introduit également des règles en matière de libre circulation des données personnelles au sein et en dehors de l'UE. 

**Clause de protection :** le service {{site.data.keyword.cloudaccesstrailshort}} stocke et affiche les enregistrements d'événement provenant des ressources de cloud qui s'exécutent sur votre compte dans {{site.data.keyword.cloud_notm}}. Les informations personnelles ne doivent être incluses dans aucune des entrées d'événement stockées dans {{site.data.keyword.cloudaccesstrailshort}} car ces données sont accessibles à d'autres utilisateurs au sein de votre entreprise, ainsi qu'à {{site.data.keyword.IBM_notm}} pour permettre la prise en charge du service cloud.

### Régions
{: #compliance_regions}

Le service {{site.data.keyword.cloudaccesstrailshort}} est conforme au RGPD (Règlement général sur la protection des données) dans les régions publiques {{site.data.keyword.cloud_notm}} où le service est disponible.


### Conservation des données
{: #compliance_data_retention}

Le service {{site.data.keyword.cloudaccesstrailshort}} inclut deux référentiels de données où sont stockées vos données d'événement : 

* Un référentiel où les données d'événement sont disponibles pour l'analyse via Kibana. Le plan standard ou Lite stocke uniquement les données dans ce référentiel. Les données sont conservées pendant 3 jours.
* Un référentiel de stockage à long terme qui héberge les données d'événement pour le plan Premium. Les données d'événement sont stockées jusqu'à ce que vous configuriez une règle de conservation ou que vous les supprimiez manuellement. Par défaut, les événements sont conservés indéfiniment.


### Suppression des données
{: #compliance_data_deletion}

Prenez en compte les informations suivantes :

* Les événements qui sont stockés dans le référentiel qui fournit les données pour Kibana sont supprimés au bout de 3 jours.

* Les événements qui sont stockés dans le référentiel à long terme sont supprimés après un certain nombre de jours lorsque vous configurez une règle de conservation, ou lorsque vous les supprimez manuellement. 



Si vous passez d'un plan payant au plan standard ou Lite, les événements situés dans le référentiel de stockage à long terme seront supprimés au bout d'une journée environ.

A tout moment, vous pouvez ouvrir un ticket de demande de service et demander que toutes vos données soient supprimées. Pour plus d'informations sur l'ouverture d'un ticket de demande de service IBM, voir la rubrique décrivant [comment contacter le support](/docs/get-support/howtogetsupport.html#getting-customer-support).



### Informations complémentaires
{: #compliance_info}

Pour plus d'informations, voir :

[{{site.data.keyword.cloud_notm}} - Conformité en matière de sécurité](/docs/security/compliance.html#compliance)

[RGPD - Page officielle {{site.data.keyword.IBM_notm}}](https://www.ibm.com/data-responsibility/gdpr/)



