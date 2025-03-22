# Ruta de aprendizaje 1 - Laboratorio 3 - Ejercicio 1: Administración de directivas DLP  

En tu rol como Holly Dickson, la nueva administradora de Microsoft 365 de Adatum, tienes Microsoft 365 implementado en un entorno de laboratorio virtualizado. A medida que continúes con el proyecto piloto de Microsoft 365, los pasos siguientes serán implementar directivas de prevención de pérdida de datos (DLP) en Adatum. Comenzarás creando una directiva DLP personalizada en este ejercicio y, a continuación, probarás las directivas DLP relacionadas con el archivado de mensajes de correo electrónico y los correos electrónicos con datos confidenciales. 

### Tarea 1: Creación de una directiva DLP con configuración personalizada

En este ejercicio, crearás una directiva de prevención de pérdida de datos (DLP) en Microsoft Purview Portal para proteger la información confidencial de ser compartida por los usuarios. La directiva DLP que crees informará a los usuarios si quieren compartir contenido que contiene direcciones IP. 

La directiva contendrá dos reglas o acciones, cada una de las cuales depende del número de direcciones IP del mensaje. Si el mensaje contiene una dirección IP, la directiva notificará a las personas con una sugerencia de directiva y procederá a enviar el mensaje por correo electrónico. Sin embargo, si el contenido contiene dos o más direcciones IP, el mensaje se bloqueará, se enviará un correo electrónico de incidente con un nivel de confidencialidad alto al remitente y se mostrará una sugerencia de directiva que permita al remitente invalidar la el bloqueo del correo electrónico si el remitente proporciona una justificación comercial dentro de la sugerencia de directiva.

1. En LON-CL1, en el explorador Edge, todavía deberías tener la sesión iniciada en Microsoft 365 como **Holly Dickson**. 

2. En **Microsoft Edge**, Microsoft Purview Portal debe estar abierto; si no es así, abre una nueva pestaña y ve a **https://compliance.microsoft.com**.

3. En **Microsoft Purview Portal** , selecciona **Soluciones** en el panel de navegación, **Prevención de pérdida de datos** y, a continuación, selecciona **Directivas**.

4. En la página **Directivas**, selecciona la opción **+Crear directiva** en la barra de menús para iniciar el asistente para **crear directivas**.

5. En la página **Iniciar con una plantilla o crear una directiva personalizada**, la columna **Categorías** muestra las categorías de directiva. Cada categoría de directiva proporciona plantillas que se pueden usar para crear ese tipo de directiva, excepto para la categoría **Personalizado**. Esta categoría no proporciona ninguna plantilla específica; en su lugar, permite a las organizaciones crear directivas personalizadas desde cero. Al seleccionar una categoría, aparece la columna **Plantillas** que muestra las plantillas disponibles entre las que elegir para la categoría seleccionada. Al seleccionar una plantilla, aparece otra columna que muestra el tipo de información que se protege en esa plantilla. <br/> 

    Por ejemplo, selecciona **Financiero** en el panel lateral y desplázate por las distintas plantillas que puedes elegir en la columna **Plantillas**. Selecciona una o dos de las plantillas para ver qué tipo de información protege. Si lo deseas, selecciona cada una de las categorías restantes para ver qué tipo de plantillas se proporcionan. 
  
6. Para este laboratorio, crearás una directiva DLP personalizada. Selecciona **Personalizado** en la columna **Categorías**, selecciona la plantilla **Directiva personalizada** en la columna **Plantillas** y, a continuación, selecciona **Siguiente**.

7. En la página **Nombre de la directiva DLP**, escribe la siguiente información y, a continuación, selecciona **Siguiente**:  <br/>

      - Nombre: **Directiva DLP de dirección IP**
      - Descripción: **Esta directiva detecta la presencia de direcciones IP en los correos electrónicos. Los usuarios finales reciben una notificación de detección y los administradores reciben otra notificación. Los correos electrónicos con 2 o más direcciones IP no se pueden enviar.**

8. En la página **Asignar unidades de administración**, selecciona **Siguiente**. 

9. En la página **Elegir dónde asignar la directiva**, comprueba que el botón de alternancia **Estado** está establecido en **Activado** para las siguientes ubicaciones (si alguna de estas ubicaciones no está establecida en **Activado** de forma predeterminada, establécelo en **Activado** ahora): <br/>

    - **Correo electrónico de Exchange**
    - **Sitios de SharePoint**
    - **Cuentas de OneDrive**
    - **Chats y mensajes de canales de Team**

    Establece todas las demás ubicaciones en **Desactivado** y, a continuación, selecciona **Siguiente**.

10. En la página **Definir configuración de directiva**, la opción **Crear o personalizar reglas DLP avanzadas** debe establecerse de forma predeterminada (si aún no está seleccionada de forma predeterminada, selecciónala ahora) y luego selecciona **Siguiente**. 

11. En **Personalizar reglas avanzadas DLP**, selecciona la opción **+ Crear regla** en la barra de menús.

12. En la página **Crear regla**, escribe la siguiente información:
    
      - Nombre: **Regla de dirección IP única**
    
      - Descripción: **El correo electrónico contiene una dirección IP**
    
      - En la sección **Condiciones**, selecciona **+Agregar condición** y, a continuación, selecciona **Contenido contiene** en el menú desplegable que aparece. Después, escribe la siguiente configuración de condición:
    
        - En la ventana **Contenido contiene**, selecciona el menú desplegable **Agregar** y, a continuación, selecciona **Tipos de información confidencial**.
        
        - En el panel **Tipos de información confidencial**, escribe **IP** dentro del campo **Buscar** y luego presiona Entrar.
        
        - En los resultados de la búsqueda, activa la casilla **Dirección IP** y, a continuación, selecciona **Agregar**.
        
     - Desplázate hacia abajo en la sección **Notificaciones de usuario**, establece **Use las notificaciones para informar a los usuarios y para enseñarles a usar correctamente la información confidencial** en **Activado**.

    - Activa la casilla **Notificar a los usuarios en el servicio de Office 365 con una sugerencia de directiva**. En la sección **Sugerencias de directiva**, activa la casilla **Personalizar el texto de la sugerencia de directiva**. 

        - Holly quiere que personalices el mensaje de sugerencia de directiva, así que escribe el siguiente texto en este campo: **ATTENTION! You have entered sensitive information (an IP address) in this message. You will not be prevented from sending this message, but please review whether the recipients are authorized to see this sensitive data.** 

    - Activa la casilla **Mostrar la sugerencia de directiva como un cuadro de diálogo para el usuario final antes de enviar (disponible solo para la carga de trabajo de Exchange)**. 
    
    - En la sección **Informes de incidentes**, comprueba que el conmutador de alternancia **Enviar una alerta a los administradores cuando se produce una coincidencia de regla** esté en **Activado** (si es necesario, establécelo en **Activado**).

    - Selecciona el botón **Guardar** en la parte inferior de la página.

13. En la página **Personalizar reglas DLP avanzadas**, ahora debería aparecer la **Regla de dirección IP única** que acabas de crear. Selecciona la opción **+Crear regla** para crear la segunda regla DLP. 

14. En la página **Crear regla**, escribe la siguiente información:
    
    - Nombre: **Regla de varias direcciones IP**
    
    - Descripción: **El correo electrónico contiene dos o más direcciones IP**
    
    - En la sección **Condiciones**, selecciona **+Agregar condición** y, a continuación, selecciona **Contenido contiene** en el menú desplegable que aparece. Después, escribe la siguiente configuración de condición:
    
        - En la ventana **Contenido contiene**, selecciona el menú desplegable **Agregar** y, a continuación, selecciona **Tipos de información confidencial**.
        
        - En el panel **Tipos de información confidencial**, escribe **IP** dentro del campo **Buscar** y luego presiona Entrar.
        
        - Selecciona la casilla **Dirección IP** y luego **Aceptar**.

        - En la sección **Tipos de información confidencial**, se muestra el tipo de información de **Dirección IP**. En el lado derecho de la fila Dirección IP, la configuración **Recuento de instancias** se establece de **1** a **Cualquiera**. Cambia el valor del primer campo de 1 a **2**. Al realizar este cambio, esta regla solo se aplicará si aparecen 2 o más direcciones IP en el correo electrónico. 
    
    - En la sección **Acciones**, selecciona **+Agregar acción**. En el menú desplegable que aparece, selecciona **Restringir acceso o cifrar el contenido en ubicaciones de Microsoft 365**. A continuación, escribe la siguiente configuración de acción:

    - Si no aparecen opciones en la sección **Restringir acceso o cifrar el contenido en ubicaciones de Microsoft 365**, selecciónalo ahora para expandir esta sección. Esta sección debe mostrar la opción **Impedir que los usuarios reciban correo electrónico o accedan a archivos compartidos de SharePoint, OneDrive y Teams**, que está seleccionada de forma predeterminada. Deja la opción seleccionada.

    - En la opción **Impedir que los usuarios reciban correo electrónico o accedan a archivos compartidos de SharePoint, OneDrive y Teams**, selecciona la opción **Bloquear todos**.
    
    - En la sección **Notificaciones de usuario**, establece el conmutador de alternancia **Usar notificaciones para informar a los usuarios y ayudar a educarles sobre el uso apropiado de información confidencial** en **Activado**. 

    - Activa la casilla **Notificar a los usuarios en el servicio de Office 365 con una sugerencia de directiva**. En la sección **Sugerencias de directiva**, activa la casilla **Personalizar el texto de la sugerencia de directiva**. 

        - Holly quiere que personalices el mensaje de sugerencia de directiva, así que escribe el siguiente texto en este campo: **¡ATENCIÓN! Has escrito información confidencial (varias direcciones IP) en este mensaje. Se te bloqueará si intentas enviar este mensaje. Invalidar este bloqueo, indica que has autorizado el envío de esta información confidencial a los destinatarios.** 

    - Activa la casilla **Mostrar la sugerencia de directiva como un cuadro de diálogo para el usuario final antes de enviar (disponible solo para la carga de trabajo de Exchange)**. 
    
    - En la sección **Invalidaciones de usuario**, activa la casilla **Permitir invalidaciones de archivos de Microsoft 365 y elementos de Microsoft Fabric**. Esto habilita configuraciones adicionales que indican cómo se controlarán las invalidaciones. Activa cada una de las casillas para las dos opciones siguientes:

        - **Requerir una justificación comercial para invalidar**.
        - **Invalidar automáticamente la regla si la notifican como un falso positivo**
    
    - En la sección **Informes de incidentes**, comprueba que el conmutador de alternancia **Enviar una alerta a los administradores cuando se produce una coincidencia de regla** está en **Activado** (si es necesario, establécelo en **Activado**).

    - Selecciona el botón **Guardar** en la parte inferior de la página.

15. En la página **Personalizar reglas DLP avanzadas**, ahora debería aparecer la **Regla de dirección IP única** y la **Regla de varias direcciones IP**. Selecciona **Siguiente**.

16. En la página **Modo de directiva**, selecciona **Activar la directiva inmediatamente** y, luego, selecciona **Siguiente**.

17. En la página **Revisar y finalizar**, revisa la directiva que acabas de crear. Si es necesario corregir algo, selecciona la opción **Editar** correspondiente y realiza las correcciones necesarias. Cuando todo aparezca Correcto, selecciona **Enviar**.

18. La página **Nueva directiva creada** puede tardar más o menos un minuto en aparecer. Cuando lo haga, selecciona **Listo**.

19. Deja abierto el explorador Edge. No cierres ninguna de las pestañas.


Ahora has creado una directiva DLP que busca direcciones IP en los correos electrónicos y documentos que se envían o comparten en tu organización.


### Tarea 2: Desactivación de la característica Enviar a Kindle que omite las directivas DLP

Holly Dickson, administradora de Microsoft 365 de Adatum, ha conocido recientemente la característica **Enviar a Kindle** en Microsoft 365 que permite enviar documentos de Microsoft Word directamente a la biblioteca de Kindle en cuestión de minutos. Un archivo transferido puede aparecer como un libro de Kindle con tamaños de fuente ajustables o como un documento impreso con diseños fijos para conservar el formato de diseño de página. 

El problema con esta característica es que las directivas DLP no tienen en cuenta el uso compartido de archivos de Word en Kindle, que en efecto omite los controles DLP. Dado que Adatum no usará esta característica **Enviar a Kindle**, Holly quiere desactivarla para evitar la posibilidad de que los usuarios omitan las directivas DLP de la empresa. 

Para desactivar esta configuración, deberás crear una directiva para aplicaciones de Office en el Centro de administración de Microsoft Intune. En la directiva que crearás, agregarás la configuración **Desactivar enviar a Kindle** a la directiva y, a continuación, habilitarás esta configuración. Al habilitar esta configuración en la directiva, se desactiva la característica **Enviar a Kindle** una vez que termines de crear la directiva. En ese momento, los usuarios ya no podrán enviar documentos de Word a su biblioteca de Kindle.

**Nota:** este problema es algo que debes considerar abordar en las implementaciones reales de Microsoft 365. Para obtener más información sobre la característica **Enviar a Kindle**, consulta https://support.microsoft.com/office/send-to-kindle-a53d880d-9952-4bf1-abc5-6bce8db5a273.

1. En LON-CL1, en el explorador Edge, todavía deberías tener la sesión iniciada en Microsoft 365 como **Holly Dickson**. 

2. En el explorador Edge, busca la pestaña **Centro de administración de Microsoft 365**. En el panel de navegación del Centro de administración de Microsoft 365, en el grupo **Centros de administración**, selecciona **Administrador de punto de conexión**.

3. En el **Centro de administración de Microsoft Intune**, que abre una nueva pestaña, selecciona **Aplicaciones** en el panel de navegación.

4. En la página **Aplicaciones | Información general**, en el panel de navegación central, selecciona **Directivas para aplicaciones de Office** en la sección **Directiva**.

5. En la página **Aplicaciones | Directivas para aplicaciones de Office**, selecciona el botón **Crear**. Esto inicia el asistente para crear una nueva directiva. En los pasos restantes, habilitarás la configuración **Desactivar enviar a Kindle** dentro de esta directiva.

6. En la página **Comienza con los conceptos básicos**, escribe **Desactivar la opción Enviar a Kindle** en el campo **Nombre** y luego selecciona **Siguiente**.

7. En la página **Elegir el ámbito**, selecciona la opción **Esta configuración de directiva se aplica a todos los usuarios** y, a continuación, selecciona **Siguiente**.

8. En la página **Configurar opciones**, observa las métricas que se muestran encima de la lista de opciones. Hay más de 2200 configuraciones de aplicaciones de Office para la configuración del inquilino. Para localizar rápidamente esta configuración, escribe **Kindle** en el campo **Buscar** y presiona **Entrar**. Esto debe mostrar cualquier directiva con **Kindle** en su nombre.

9. Como puedes ver, solo hay una configuración Kindle, que es **Desactivar enviar a Kindle**. Selecciona esta configuración, que abre el panel **Desactivar enviar a Kindle**.

10. En el panel **Desactivar enviar a Kindle**, se muestran los plataformas y las aplicaciones a las que se aplica esta configuración. En la descripción, selecciona la opción **Mostrar más**. Termina de leer la descripción completa de esta configuración.

11. Selecciona la flecha desplegable en el campo **Opción de configuración**. En el menú desplegable que aparece, selecciona **Habilitado**.

12. Selecciona el botón **Aplicar** en la parte inferior del panel.

13. En la página **Configurar opciones**, debería aparecer la directiva **Desactivar enviar a Kindle** y su **estado** debe estar en **Configurado**. Selecciona **Siguiente**.

14. En la página **Revisar configuración y crear**, selecciona el botón **Crear**. 

15. En la página **Nueva directiva creada**, selecciona **Listo**.
 
16. Deja abierto el explorador Edge. No cierres ninguna de las pestañas.


Al habilitar esta opción **Desactivar enviar a Kindle** en la nueva directiva que acabas de crear, has desactivado la característica **Enviar a Kindle**. Esto impedirá que los usuarios de Adatum envíen documentos de Word a su biblioteca de Kindle, lo que omite las directivas DLP de la empresa.


# Continuar con el laboratorio 3: ejercicio 2 
