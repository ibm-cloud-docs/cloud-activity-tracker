---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, IAM

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

# Concesión de permisos para ver sucesos
{: #grant_permissions}

En {{site.data.keyword.cloud}}, puede asignar roles de Cloud Foundry, roles de IAM o ambos a un usuario. Estos roles definen las tareas que puede realizar un usuario cuando trabaje con el servicio {{site.data.keyword.cloudaccesstrailshort}}.  
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} está en desuso. A partir del 9 de mayo de 2019, no se pueden suministrar nuevas instancias de {{site.data.keyword.cloudaccesstrailshort}}. Las instancias existentes del plan premium recibirán soporte hasta el 30 de septiembre de 2019. Para seguir supervisando la actividad de la cuenta de {{site.data.keyword.cloud_notm}} suministre una instancia de [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}

## Concesión de permisos para ver sucesos de cuenta
{: #grant_acc_events}

Puede otorgar a un usuario los permisos siguientes para ver los sucesos de la cuenta en una región:

1. Rol de *desarrollador* en un espacio de la región en la que se suministra {{site.data.keyword.cloudaccesstrailshort}}. 

    Para obtener más información, consulte [Concesión de un rol de CF](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-grant_permissions#grant_cf_role).

2. Política de IAM para el servicio {{site.data.keyword.loganalysisshort}} con el rol de *visor* en la región. 

    El rol de visor es el rol de IAM mínimo necesario. 
	
	Para obtener más información, consulte [Concesión de permisos de IAM](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-grant_permissions#grant_iam_policy).


## Concesión de permisos para ver sucesos de espacio
{: #grant_space_events}

Puede otorgar a un usuario el permiso siguiente para ver los sucesos de espacio en una región:

* Rol de *desarrollador* en un espacio de la región en la que se suministra {{site.data.keyword.cloudaccesstrailshort}}. 

    Para obtener más información, consulte [Concesión de un rol de CF](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-grant_permissions#grant_cf_role).


## Concesión de permisos de IAM
{: #grant_iam_policy}

Para otorgar a un usuario un rol de IAM, tenga en cuenta la información siguiente:

* Debe tener permisos para asignar políticas a otros usuarios en la cuenta, o bien debe ser el propietario de la cuenta. Si no es el propietario de la cuenta, debe tener una política de IAM con el rol de **administrador** para el servicio {{site.data.keyword.loganalysisshort}}.

* Cuando defina una política, las regiones que especifique definen las regiones en las que se otorga a un usuario acceso para ver los sucesos de dominio de la cuenta.

Siga los pasos siguientes para otorgar a un usuario permiso para ver sucesos desde un dominio de cuenta:

1. [Inicie sesión en la consola de {{site.data.keyword.cloud_notm}}
![Icono de enlace externo](../../../icons/launch-glyph.svg "Icono de enlace externo")](https://cloud.ibm.com/login){:new_window}.
	
	Después de iniciar la sesión con su ID de usuario y contraseña, se abre la interfaz de usuario de {{site.data.keyword.cloud_notm}}.

2. En la barra de menús, pulse **Gestionar > Cuenta > Usuarios**. 

    La ventana *Usuarios* muestra una lista de usuarios con sus direcciones de correo electrónico para la cuenta seleccionada actualmente.
	
3. Si el usuario es un miembro de la cuenta, seleccione el nombre de usuario de la lista, o pulse **Gestionar usuario** en el menú *Acciones*.

    Si el usuario no es un miembro de la cuenta, consulte [Invitación a usuarios](/docs/iam?topic=iam-iamuserinv#iamuserinv).

4. En la sección **Políticas de acceso**, pulse **Asignar acceso** y, a continuación, seleccione **Asignar acceso a recursos**.

    Se abre la ventana *Asignar acceso a recursos a usuario**.

5. Especifique la información sobre la política. En la tabla siguiente se muestran los campos necesarios para definir una política: 

    <table>
	  <caption>Lista de campos para configurar una política de IAM.</caption>
	  <tr>
	    <th>Campo</th>
		<th>Valor</th>
	  </tr>
	  <tr>
	    <td>Servicios</td>
		<td>*IBM Cloud Log Analysis*</td>
	  </tr>	  
	  <tr>
	    <td>Regiones</td>
		<td>Puede especificar las regiones en las que se va a otorgar acceso al usuario para trabajar con sucesos. Seleccione una o varias regiones individualmente, o seleccione **Todas las regiones actuales** para otorgar acceso a todas las regiones.</td>
	  </tr>
	  <tr>
	    <td>Instancia de servicio</td>
		<td>Seleccione *Todas las instancias de servicio*.</td>
	  </tr>
	  <tr>
	    <td>Roles</td>
		<td>Seleccione uno o varios roles de IAM. <br>Los roles válidos son *administrador*, *operador*, *editor*, y *visor*.</td>
	  </tr>
     </table>
	
6. Pulse **Asignar**.
	
La política que configure es aplicable a las regiones seleccionadas. 


## Concesión de un rol de CF
{: #grant_cf_role}

Para otorgar a un usuario un rol de CF, tenga en cuenta la información siguiente:

* Debe tener permisos en la organización y el espacio para asignar al usuario un rol de Cloud Foundry. 

* Solo el rol de **desarrollador** permite a un usuario ver sucesos.

Siga los pasos siguientes para otorgar a un usuario acceso para ver sucesos del espacio:

1. [Inicie sesión en la consola de {{site.data.keyword.cloud_notm}}
![Icono de enlace externo](../../../icons/launch-glyph.svg "Icono de enlace externo")](https://cloud.ibm.com/login){:new_window}.
	
	Después de iniciar la sesión con su ID de usuario y contraseña, se abre la interfaz de usuario de {{site.data.keyword.cloud_notm}}.

2. En la barra de menús, pulse **Gestionar > Cuenta > Usuarios**. 

    La ventana *Usuarios* muestra una lista de usuarios con sus direcciones de correo electrónico para la cuenta seleccionada actualmente.
	
3. Si el usuario es un miembro de la cuenta, seleccione el nombre de usuario de la lista, o pulse **Gestionar usuario** en el menú *Acciones*.

    Si el usuario no es un miembro de la cuenta, consulte [Invitación a usuarios](/docs/iam?topic=iam-iamuserinv#iamuserinv).

4. Seleccione **Acceso a Cloud Foundry**. A continuación, seleccione la organización.

    Aparecerán los espacios que estén disponibles en dicha organización.

5. Elija un espacio. A continuación, en la acción de menú, seleccione **Editar rol de espacio**.

6. Seleccione **Desarrollador**.
	
7. Pulse **Guardar rol**.




