---
title: FAQ soluciones de correo electrónico de OVHcloud
updated: 2020-05-05
---

## FAQ

### ¿Qué hacer si no puedo enviar o recibir mensajes de correo electrónico? 

A menudo, cuando no es posible enviar o recibir un mensaje de correo electrónico, suele deberse a la configuración de la dirección en su cliente de correo. Para comprobarlo, conéctese al [webmail](https://www.ovh.es/mail/){.external} y realice una prueba de envío y recepción desde su dirección.

* Si funciona, deberá comprobar su configuración del software. 
* Por el contrario, si sigue sin poder enviar o recibir mensajes, existen otras soluciones.

Al enviar un mensaje de correo electrónico en su cuenta de correo, ¿recibe un mensaje de error? En caso afirmativo, analice con atención este mensaje, ya que podría indicarle el motivo del fallo (buzón lleno, no existente...).

También puede comprobar si el dominio está entregando los mensajes en el destino correcto. Para ello, desde su [área de cliente de OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.es/&ovhSubsidiary=es), seleccione la zona DNS del dominio y compruebe la configuración de los registros MX. Estos registros deben estar en formato «mx\*.mail.ovh.net.» (sustituya \* por un número entre 0 y 3). Si los registros MX son diferentes, es posible que tenga una solución de correo con un operador diferente a OVHcloud.

**Ideas y consejos**:  Si no puede conectarte a su [webmail](https://www.ovh.es/mail/){.external}, puede que la contraseña no sea la correcta. Compruébela y, si fuera necesario, modifíquela desde el [área de cliente de OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.es/&ovhSubsidiary=es). Para más información, consulte la siguiente documentación: [Uso avanzado del correo de OVHcloud](/pages/web_cloud/email_and_collaborative_solutions/troubleshooting/diagnostic_advanced).

### ¿Cómo configurar mi dirección de correo electrónico y utilizarla con el webmail?

Puede configurar su cuenta de correo con clientes como Outlook, Thunderbird o Mail de Mac, entre otros. OVHcloud pone a su disposición diferentes guías para ayudarle a configurar su dirección de correo. Puede consultar nuestras guías en la [siguiente página](/products/web-cloud-email-collaborative-solutions-mx-plan).

Gracias al [webmail](https://www.ovh.es/mail/){.external}, podrá acceder a su correo en cualquier momento, desde cualquier dispositivo. Una vez que haya creado su cuenta de correo, haga clic aquí para acceder a ella.

**Ideas y consejos**: Si ha configurado su cuenta en un cliente de correo, le recomendamos que utilice el protocolo IMAP. De este modo, los mensajes se almacenarán en el servidor y podrá consultarlos desde cualquier dispositivo a través del [webmail](https://www.ovh.es/mail/){.external}. Para más información, consulte la siguiente documentación: [Primeros pasos con la solución MX Plan](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/email_generalities).

### ¿Cómo gestionar mis servicios de correo electrónico?

Puede gestionar todas sus direcciones de correo electrónico desde el [área de cliente de OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.es/&ovhSubsidiary=es). Una vez conectado, acceda al producto correspondiente. Puede modificar la contraseña de sus direcciones de correo, comprobar el porcentaje de capacidad utilizado, crear nuevas direcciones o eliminar las existentes.

**Ideas y consejos**: En los planes de correo electrónico MX Plan, puede delegar la gestión de una cuenta de correo a otra cuenta de OVHcloud, pero manteniendo el control de la misma. Para ello, solo tiene que configurar una delegación desde su [área de cliente de OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.es/&ovhSubsidiary=es). Acceda a la sección `Correo electrónico` en la columna de la izquierda y seleccione el dominio correspondiente. A continuación, abra la pestaña `Correo electrónico`{.action} y, a continuación, seleccione una opción:

* `Gestionar los elementos compartidos por todas las direcciones de correo electrónico`{.action}  en el lado derecho si desea delegar la administración de todas las cuentas de este dominio.
* `Gestión de la delegación`{.action} si desea delegar la gestión de una cuenta específica (haga clic en `...`{.action} junto a la cuenta).

### ¿Cómo limitar la recepción de spam?

Si desea limitar la recepción del spam, puede configurar filtros de correo (llamados «Filtros» en la solución MX Plan) para eliminar o mover estos mensajes de correo a la carpeta de correo no deseado. Para ello, desde su [área de cliente de OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.es/&ovhSubsidiary=es), acceda a la sección `Correo electrónico` en la columna de la izquierda y seleccione el dominio correspondiente. A continuación, abra la pestaña `Correo electrónico`{.action} y, en la columna «Filtros», haga clic en el icono de «Gestión de los filtros de la cuenta».

Si no ve esta columna, se pueden crear filtros de correo basura configurando reglas de la bandeja de entrada en el [webmail](https://www.ovh.es/mail/){.external}. Consulte [esta guía](/pages/web_cloud/email_and_collaborative_solutions/using_the_outlook_web_app_webmail/creating-inbox-rules-in-owa-mx-plan) para obtener instrucciones detalladas.

**Ideas y consejos**:  Si configura un filtro para limitar la recepción de spam, es posible que los correos electrónicos legítimos también sean considerados como spam («falsos positivos»). En ese caso, le recomendamos que abra un tíquet de asistencia en su [área de cliente de OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.es/&ovhSubsidiary=es). Nuestro equipo de soporte adoptará las medidas necesarias para que estos correos legítimos no sean considerados como spam.

### Mi dirección de correo electrónico está llena, no tengo espacio. ¿Qué puedo hacer?

Si ha contratado [una de nuestras soluciones de correo de OVHcloud](https://www.ovhcloud.com/es/emails/) y tiene una cuenta de correo llena, consulte nuestra guía «[Gestionar el espacio de almacenamiento de una cuenta de correo](/pages/web_cloud/email_and_collaborative_solutions/troubleshooting/email_manage_quota) ». Esta guía le ayudará a determinar si puede optimizar el espacio existente o si es necesario cambiar de solución de correo para aumentar la capacidad de almacenamiento.

### Quiero cambiar de plan de correo para mi dirección, ¿cómo puedo hacerlo conservando su contenido?

Si quiere cambiar [de plan de correo](https://www.ovhcloud.com/es/emails/) para disfrutar de más espacio y funcionalidades, pero quiere conservar el contenido de su dirección existente. Para ello, siga una de nuestras guías de migración:

- [Migrar una dirección de correo MX Plan a una cuenta Email Pro o Exchange](/pages/web_cloud/email_and_collaborative_solutions/migrating/migration_control_panel)
- [Migrar las direcciones de correo electrónico de una plataforma de correo de OVHcloud a otra](/pages/web_cloud/email_and_collaborative_solutions/migrating/migration_control_panel)
- [Migrar manualmente una dirección de correo electrónico](/pages/web_cloud/email_and_collaborative_solutions/migrating/manual_email_migration)
- [Migrar cuentas de correo electrónico mediante OVH Mail Migrator](/pages/web_cloud/email_and_collaborative_solutions/migrating/migration_omm)
- [Migrar una cuenta de Gmail a una cuenta de correo electrónico de OVHcloud mediante OVH Mail Migrator](/pages/web_cloud/email_and_collaborative_solutions/migrating/security_gmail)

### ¿La solución Office 365 Pro Plus incluye licencia Skype?

La solución Office 365 Pro Plus no incluye licencia Skype. Solo se incluye Skype for Business.

## Más información

Interactúe con nuestra comunidad de usuarios en [https://community.ovh.com/en/](https://community.ovh.com/en/){.external}