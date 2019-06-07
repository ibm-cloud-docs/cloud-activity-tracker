---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, VSI events, tutorial

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


# Supervisión de {{site.data.keyword.BluVirtServers_short}} y de {{site.data.keyword.baremetal_short}} con {{site.data.keyword.cloudaccesstrailshort}}
{: #vsi}

Utilice esta guía de aprendizaje para aprender a configurar usuarios en una cuenta de
{{site.data.keyword.cloud_notm}}, de manera que pueda supervisar sucesos de
{{site.data.keyword.cloudaccesstrailshort}} generados por dichos usuarios cuando trabajen con
{{site.data.keyword.BluVirtServers_short}} y {{site.data.keyword.baremetal_short}}.
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} está en desuso. A partir del 9 de mayo de 2019, no se pueden suministrar nuevas instancias de {{site.data.keyword.cloudaccesstrailshort}}. Las instancias existentes del plan premium recibirán soporte hasta el 30 de septiembre de 2019. Para seguir supervisando la actividad de la cuenta de {{site.data.keyword.cloud_notm}} suministre una instancia de [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}

Los {{site.data.keyword.BluVirtServers}} son servidores virtuales escalables que se adquieren con núcleos dedicados y asignaciones de memoria. Constituyen una opción ideal si necesita recursos de cálculo, que se pueden añadir en cuestión de minutos, con acceso a características como plantillas de imágenes. 
* Para obtener más información, consulte [{{site.data.keyword.BluVirtServers_short}}](/docs/vsi?topic=virtual-servers-about-virtual-servers#about-virtual-servers). 
* Para ver la lista de acciones que generan un suceso de {{site.data.keyword.cloudaccesstrailshort}}, consulte el apartado [Sucesos generados por {{site.data.keyword.BluVirtServers_short}}](/docs/vsi?topic=virtual-servers-at_events#at_events).

{{site.data.keyword.baremetal_short}} son servidores físicos de un solo arrendatario que le proporcionan rendimiento y control con acceso de bajo nivel a los recursos de hardware. 
* Para obtener más información, consulte [{{site.data.keyword.baremetal_long}}](/docs/bare-metal?topic=bare-metal-about#about).
* Para ver la lista de acciones que generan un suceso de {{site.data.keyword.cloudaccesstrailshort}}, consulte el apartado [Sucesos generados por {{site.data.keyword.baremetal_short}}](/docs/bare-metal?topic=bare-metal-bm-at-events#bm-at-events).

**Para que un usuario genere sucesos de {{site.data.keyword.BluVirtServers_short}} y de {{site.data.keyword.baremetal_short}} {{site.data.keyword.cloudaccesstrailshort}}, el usuario debe tener acceso a los recursos de la infraestructura en la consola de IBM Cloud.**
{: tip}

## Paso 1. Enlazar la cuenta de Softlayer con una cuenta de {{site.data.keyword.cloud_notm}}
{: #vsi_step1}

** Para generar sucesos de {{site.data.keyword.cloudaccesstrailshort}}, la cuenta de Softlayer debe estar enlazada a una cuenta de {{site.data.keyword.cloud_notm}}. Para obtener más información, consulte [Cómo cambiar a IBMid y enlazar cuentas](/docs/account?topic=account-unifyingaccounts#link_accounts).

Tenga en cuenta la siguiente información cuando enlace la cuenta de Softlayer a una cuenta de {{site.data.keyword.cloud_notm}}:
* Todas las cuentas nuevas recibirán automáticamente un IBMid y las cuentas existentes de SoftLayer, excepto las cuentas federadas SAML, estarán habilitadas para conmutar a la autenticación de IBMid.
* Cada cuenta de SoftLayer que tenga previsto enlazar a una cuenta de {{site.data.keyword.cloud_notm}} debe ser propiedad de un IBMid único con una dirección de correo electrónico exclusiva.
* Para pasar de una cuenta de SoftLayer existente a un IBMid, cree un IBMid y utilice el código de registro para confirmarlo.
* Después de cambiar a una cuenta de IBMid, puede enlazar la cuenta de SoftLayer y la cuenta de {{site.data.keyword.cloud_notm}} para utilizar la infraestructura como servicio (IaaS) combinada y los recursos de la plataforma como servicio (PaaS). 

Siga los pasos siguientes para enlazar una cuenta:
1. [Solicite un IBMid y un código de registro](/docs/account?topic=account-unifyingaccounts#reqIBMidandregcode)
2. [Confirme el IBMid con el código de registro](/docs/account?topic=account-unifyingaccounts#confIBMiduseregcode)
3. [Enlace la cuenta de IBMid](/docs/account?topic=account-unifyingaccounts#link_user_account)


## Paso 2. Otorgar a los usuarios permisos de la infraestructura
{: #vsi_step2}

**Nota:** si otorga los permisos desde el *portal de la infraestructura {{site.data.keyword.cloud_notm}}*,
el usuario no tiene acceso desde el panel de control de la *infraestructura de {{site.data.keyword.cloud_notm}}* para gestionar dispositivos y no se generan sucesos de {{site.data.keyword.cloudaccesstrailshort}}. **Debe otorgar el permiso de infraestructura a un usuario a través de la cuenta de {{site.data.keyword.cloud_notm}} para gestionar dispositivos. Estas acciones generan sucesos de {{site.data.keyword.cloudaccesstrailshort}}.**
{: tip}

Siga los pasos siguientes para otorgar a un usuario el permiso de la infraestructura:

1. [Inicie sesión en {{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://cloud.ibm.com/login){:new_window}.
    
	Después de iniciar la sesión con su ID de usuario y contraseña, se abre la interfaz de usuario de {{site.data.keyword.cloud_notm}}.

2. En la barra de menús, pulse **Gestionar** &gt; **Cuenta** y, a continuación, seleccione **Usuarios**. 

3. Elija un usuario al que desee otorgar permisos para trabajar con dispositivos.

4. Seleccione **Asignar acceso**.

5. Seleccione **Asignar acceso a la cuenta de SoftLayer**. Se abre el portal de la infraestructura {{site.data.keyword.cloud_notm}} en el contexto de {{site.data.keyword.cloud_notm}}.

6. Defina los permisos que desea otorgan al usuario para gestionar dispositivos. Seleccione **Permisos de portal**. A continuación, en la sección **Dispositivos**, otorgue al usuario los permisos que necesita el usuario para gestionar los dispositivos. Por ejemplo, puede cambiar permisos para `Ver detalles del servidor virtual`, `Reiniciar servidor y ver información del sistema IPMI`, `Actualizar servidor` o `Emitir recargas de SO e iniciar el kernel de rescate`.

7. Guarde los permisos del portal. Cuando seleccione **Acceso a dispositivos**, se le solicitará que guarde los cambios. Pulse **Guardar**.

8. Defina los dispositivos que puede gestionar el usuario. En la sección **Acceso a dispositivos**, seleccione los dispositivos físicos. A continuación, pulse **Actualizar acceso a dispositivos**.






