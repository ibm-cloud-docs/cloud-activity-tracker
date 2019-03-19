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


# Evénements Cloud Foundry
{: #cf}

Utilisez le service {{site.data.keyword.cloudaccesstrailfull}} pour suivre l'interaction avec les services de plateforme de base dans {{site.data.keyword.Bluemix}}. 
{:shortdesc}


La liste suivante présente les différentes tâches de plateforme de base qui envoient des événements au service {{site.data.keyword.cloudaccesstrailshort}} : 

* Mise à disposition d'un service, suppression d'un service et modification du nom d'un service.
* Accord, mise à jour et révocation de rôles d'espace Cloud Foundry affectés à des utilisateurs dans le compte.
* Création d'une clé d'API de plateforme, changement de nom d'une clé de plateforme et suppression d'une clé de plateforme.


## Evénements générés lors de l'interaction avec des services de catalogue
{: #cf_catalog}

Lors de la mise à disposition, de la suppression ou du changement de nom d'un service, un événement est généré et envoyé au domaine d'espace dans {{site.data.keyword.cloudaccesstrailshort}} qui est associé à l'espace Cloud Foundry où le service est disponible dans le compte.  

Par exemple, vous mettez à disposition le service A dans l'espace B de la région us-south. Un événement est généré. Pour voir l'événement, vous devez mettre à disposition le service {{site.data.keyword.cloudaccesstrailshort}} dans la région us-south, dans le même espace que celui où vous avez mis à disposition le service. Ensuite, vous pouvez afficher l'événement via l'interface utilisateur du service {{site.data.keyword.cloudaccesstrailshort}}.

Le tableau suivant répertorie les actions de catalogue qui génèrent des événements :

<table>
  <caption>Actions de catalogue</caption>
  <tr>
    <th>Action</th>
	  <th>Description</th>
  <tr>
  <tr>
    <td>`audit.service_instance.create`</td>
	<td>Un événement est créé lorsque vous mettez un service à disposition dans un espace Cloud Foundry. </td>
  </tr>
  <tr>
    <td>`audit.service_instance.update`</td>
	<td>Un événement est créé lorsque vous modifiez le nom d'un service disponible dans un espace Cloud Foundry. </td>
  </tr>
  <tr>
    <td>`audit.service_instance.delete`</td>
	<td>Un événement est créé lorsque vous supprimez un service d'un espace Cloud Foundry dans le compte. </td>
  </tr>
</table>


 	

## Evénements générés lors de la gestion des rôles Cloud Foundry dans le compte
{: #cf_cfroles} 

Lorsque vous accordez ou révoquez (supprimez) un rôle Cloud Foundry affecté à un utilisateur dans le compte, un événement est généré et envoyé au domaine d'espace dans {{site.data.keyword.cloudaccesstrailshort}} qui est associé à l'espace Cloud Foundry où le rôle est accordé ou révoqué.  

Par exemple, vous accordez le rôle *Responsable d'espace* à l'utilisateur A dans l'espace B de la région Sud des Etats-Unis (us-south). Un événement est généré. Pour voir l'événement, vous devez mettre à disposition le service {{site.data.keyword.cloudaccesstrailshort}} dans la région us-south, dans le même espace que celui où vous gérez les droits CF de l'utilisateur. Ensuite, vous pouvez afficher l'événement via l'interface utilisateur du service {{site.data.keyword.cloudaccesstrailshort}}.


Le tableau suivant répertorie les actions qui génèrent des événements {{site.data.keyword.cloudaccesstrailshort}} lorsque vous gérez les rôles Cloud Foundry d'un utilisateur :

<table>
  <caption>Actions qui gèrent des rôles Cloud Foundry</caption>
  <tr>
    <th>Action</th>
	<th>Description</th>
  <tr>
  <tr>
    <td>`audit.user.space_manager_add`</td>
	<td>Accorde le rôle *Responsable* à un utilisateur dans un espace Cloud Foundry.</td>
  </tr>
  <tr>
    <td>`audit.user.space_developer_add`</td>
	<td>Accorde le rôle *Développeur* à un utilisateur dans un espace Cloud Foundry.</td>
  </tr>
  <tr>
    <td>`audit.user.space_auditor_add`</td>
	<td>Accorde le rôle *Auditeur* à un utilisateur dans un espace Cloud Foundry.</td>
  </tr>
  <tr>
    <td>`audit.user.space_manager_remove`</td>
	<td>Supprime le rôle *Responsable* de l'utilisateur dans un espace Cloud Foundry.</td>
  </tr>
  <tr>
    <td>`audit.user.space_developer_remove`</td>
	<td>Supprime le rôle *Développeur* de l'utilisateur dans un espace Cloud Foundry.</td>
  </tr>
  <tr>
    <td>`audit.user.space_auditor_remove`</td>
	<td>Supprime le rôle *Auditeur* de l'utilisateur dans un espace Cloud Foundry.</td>
  </tr>
</table>






	
 	
 	
