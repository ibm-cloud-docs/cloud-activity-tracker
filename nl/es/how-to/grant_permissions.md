---

copyright:
  years: 2017, 2018

lastupdated: "2018-07-09"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# Concesión de permisos para ver sucesos
{: #grant_permissions}

En {{site.data.keyword.Bluemix}}, puede asignar roles de Cloud Foundry, roles de IAM o ambos a un usuario. Estos roles definen las tareas que puede realizar un usuario cuando trabaje con el servicio {{site.data.keyword.cloudaccesstrailshort}}.  
{:shortdesc}

## Concesión de permisos para ver sucesos de cuenta
{: #grant_acc_events}

Puede otorgar a un usuario los permisos siguientes para ver los sucesos de la cuenta en una región:

1. Rol de *desarrollador* en un espacio de la región en la que se suministra {{site.data.keyword.cloudaccesstrailshort}}. 

    Para obtener más información, consulte [Concesión de un rol de CF](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_cf_role).

2. Política de IAM para el servicio {{site.data.keyword.loganalysisshort}} con el rol de *visor* en la región. 

    El rol de visor es el rol de IAM mínimo necesario. 
	
	Para obtener más información, consulte [Concesión de permisos de IAM](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_iam_policy).


## Concesión de permisos para ver sucesos de espacio
{: #grant_space_events}

Puede otorgar a un usuario el permiso siguiente para ver los sucesos de espacio en una región:

* Rol de *desarrollador* en un espacio de la región en la que se suministra {{site.data.keyword.cloudaccesstrailshort}}. 

    Para obtener más información, consulte [Concesión de un rol de CF](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_cf_role).


## Concesión de permisos de IAM
{: #grant_iam_policy}

Para otorgar a un usuario un rol de IAM, tenga en cuenta la información siguiente:

* Debe tener permisos para asignar políticas a otros usuarios en la cuenta, o bien debe ser el propietario de la cuenta. Si no es el propietario de la cuenta, debe tener una política de IAM con el rol de **administrador** para el servicio {{site.data.keyword.loganalysisshort}}.

* Cuando defina una política, las regiones que especifique definen las regiones en las que se otorga a un usuario acceso para ver los sucesos de dominio de la cuenta.

Siga los pasos siguientes para otorgar a un usuario permisos para ver sucesos desde un dominio de cuenta:

1. Inicie una sesión en la consola de {{site.data.keyword.Bluemix_notm}}.

    Abra un navegador web e inicie el panel de control de {{site.data.keyword.Bluemix_notm}}: [http://bluemix.net ![Icono de enlace externo](../../../icons/launch-glyph.svg "Icono de enlace externo")](http://bluemix.net){:new_window}
	
	Después de iniciar la sesión con su ID de usuario y contraseña, se abre la interfaz de usuario de {{site.data.keyword.Bluemix_notm}}.

2. En la barra de menús, pulse **Gestionar > Cuenta > Usuarios**. 

    La ventana *Usuarios* muestra una lista de usuarios con sus direcciones de correo electrónico para la cuenta seleccionada actualmente.
	
3. Si el usuario es un miembro de la cuenta, seleccione el nombre de usuario de la lista, o pulse **Gestionar usuario** en el menú *Acciones*.

    Si el usuario no es un miembro de la cuenta, consulte [Invitación a usuarios](/docs/iam/iamuserinv.html#iamuserinv).

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
		<td>Seleccione uno o varios roles de IAM. <br>Los roles válidos son: *administrador*, *operador*, *editor*, y *visor*.</td>
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

1. Inicie una sesión en la consola de {{site.data.keyword.Bluemix_notm}}.

    Abra un navegador web e inicie el panel de control de {{site.data.keyword.Bluemix_notm}}: [http://bluemix.net ![Icono de enlace externo](../../../icons/launch-glyph.svg "Icono de enlace externo")](http://bluemix.net){:new_window}
	
	Después de iniciar la sesión con su ID de usuario y contraseña, se abre la interfaz de usuario de {{site.data.keyword.Bluemix_notm}}.

2. En la barra de menús, pulse **Gestionar > Cuenta > Usuarios**. 

    La ventana *Usuarios* muestra una lista de usuarios con sus direcciones de correo electrónico para la cuenta seleccionada actualmente.
	
3. Si el usuario es un miembro de la cuenta, seleccione el nombre de usuario de la lista, o pulse **Gestionar usuario** en el menú *Acciones*.

    Si el usuario no es un miembro de la cuenta, consulte [Invitación a usuarios](/docs/iam/iamuserinv.html#iamuserinv).

4. Seleccione **Acceso de Cloud Foundry** y luego seleccione la organización.

    Aparece la lista de espacios disponibles en dicha organización.

5. Elija un espacio. A continuación, en la acción de menú, seleccione **Editar rol de espacio**.

6. Seleccione **Desarrollador**.
	
7. Pulse **Guardar rol**.




