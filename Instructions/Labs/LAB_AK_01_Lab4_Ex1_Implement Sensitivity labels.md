# Ruta de aprendizaje 1 - Laboratorio 4 - Ejercicio 1: Implementación de etiquetas de confidencialidad con Protección de Microsoft Entra ID

En tu rol como Holly Dickson, como nueva administradora de Microsoft 365 de Adatum, tienes Microsoft 365 implementado en un entorno de laboratorio virtualizado. A medida que continúas con el proyecto piloto de Microsoft 365, los pasos siguientes serán implementar las etiquetas de confidencialidad con Microsoft Purview Information Protection en Adatum. En este laboratorio, crearás y publicarás una etiqueta, y probarás una etiqueta publicada. Sin embargo, al hacerlo, no probarás la etiqueta que crees en este laboratorio. En su lugar, probarás una etiqueta diferente.

**Importante:** al publicar una nueva etiqueta de confidencialidad y una directiva de etiquetas, puede tardar hasta 24 horas en propagarse a través de Microsoft 365. Por lo tanto, no podrás probar la etiqueta que crees en este laboratorio. En su lugar, probarás una etiqueta de confidencialidad preexistente denominada **Project - Falcon**. Esta etiqueta preexistente es casi idéntica a la etiqueta que crearás, por lo que básicamente podrás ver los mismos resultados que si hubieras podido probar la etiqueta que crearás. 


### Tarea 1: Instalación del cliente de Microsoft Purview Information Protection

Para implementar etiquetas de confidencialidad como parte del proyecto piloto en Adatum, primero deberás instalar el cliente de **Microsoft Purview Information Protection** desde el Centro de descarga de Microsoft.

1. Al final del laboratorio anterior, estabas en LON-CL2. Cambia a **LON-CL1**.  <br/>

    Todavía deberías tener la sesión iniciada en LON-CL1 como la cuenta de **adatum\administrator** y, en el explorador Edge, todavía deberías tener la sesión iniciada en Microsoft 365 como **Holly Dickson**. 

2. En **Microsoft Edge**, abre una nueva pestaña y escribe (o copia y pega) la siguiente dirección URL en la barra de direcciones: **https://www.microsoft.com/en-us/download/confirmation.aspx?id=53018** <br/>

    Esto iniciará la descarga del cliente de **Microsoft Purview Information Protection**.

3. En la ventana **Descargas** que aparece en la parte superior derecha de la página, verás que se está descargando el archivo **PurviewInfoProtection.exe**. Una vez que el archivo haya terminado de descargarse, selecciona el vínculo **Abrir archivo** que aparece debajo del nombre de archivo.

4. Se abrirá el asistente de **Microsoft Azure Information Protection**. Si el asistente no se muestra en el escritorio, selecciona el icono del asistente en la barra de tareas para mostrar el asistente.

5. En el asistente, en la ventana **Instalar el cliente de Microsoft Purview Information Protection** que aparece, selecciona la casilla **Reconozco que se desinstalará el complemento de AIP para Office (obligatorio)** y desactiva la casilla **Ayudar a mejorar Microsoft Purview Information Protection enviando estadísticas de uso a Microsoft**. Luego selecciona el botón **Acepto**.

6. Cuando la instalación se haya completado, selecciona **Cerrar**.

Has instalado correctamente el **cliente de Microsoft Purview Information Protection** en la máquina virtual LON-CL1.


### Tarea 2: Habilitación de etiquetas de confidencialidad para archivos en SharePoint y OneDrive

En este ejercicio habilitarás etiquetas de confidencialidad para archivos de Office y archivos PDF compatibles de SharePoint y OneDrive. Cuando esta característica está habilitada, los usuarios verán el botón **Confidencialidad** en la cinta de opciones para poder aplicar etiquetas. También verán cualquier nombre de etiqueta que se haya aplicado en la barra de estado. En el caso de SharePoint, los usuarios también pueden ver y aplicar etiquetas de confidencialidad desde el panel de detalles.

La habilitación de esta característica también permite que SharePoint y OneDrive puedan procesar el contenido de los archivos de Office y, opcionalmente, los documentos PDF cifrados mediante una etiqueta de confidencialidad. La etiqueta se puede aplicar en Office para la web o en aplicaciones de escritorio de Office. También se puede cargar o guardar en SharePoint y OneDrive. Hasta que habilites esta característica, estos servicios no podrán procesar archivos cifrados, lo que significa que la coautoría, eDiscovery, la prevención de pérdida de datos, la búsqueda y otras características de colaboración no funcionarán para estos archivos.

Para empezar, debes habilitar las etiquetas de confidencialidad para los archivos en línea de Office almacenados en SharePoint y OneDrive. Luego deberás habilitar la compatibilidad con archivos PDF.

**Nota:** al igual que con todos los cambios de configuración de nivel de inquilino para SharePoint y OneDrive, el cambio tarda unos 15 minutos en surtir efecto.

1. En LON-CL1, en el explorador Edge, todavía deberías tener la sesión iniciada en Microsoft 365 como **Holly Dickson**.

2. En el explorador Edge, todavía debes tener abierta una pestaña para el **Centro de administración de Microsoft 365**. Si no es así, abre una nueva pestaña y escribe la siguiente dirección URL: **https://admin.microsoft.com**.

3. En el **Centro de administración de Microsoft 365**, si es necesario, selecciona **... Mostrar todo**. Selecciona **Cumplimiento** en el grupo **Centros de administración**. Se abrirá Microsoft Purview Portal en una nueva pestaña.

4. Empezarás habilitando las etiquetas de confidencialidad para los archivos en línea de Office almacenados en SharePoint y OneDrive. <br/>

    En **Microsoft Purview Portal**, en la sección **Soluciones** del panel de navegación, selecciona **Protección de información** y, luego, **Etiquetas**.

5. En la página **Etiquetas de confidencialidad**, deberá aparecer el siguiente mensaje en medio de la página: **Your organization has not turned on the ability to process content in Office online files that have encrypted sensitivity labels applied and are stored in OneDrive and SharePoint. You can turn on here, but note that additional configuration is required for Multi-Geo environments.** <br/>

    Debajo de este mensaje se muestra el botón **Activar ahora**. Selecciónalo.  <br/>

    **Nota:** el comando se ejecuta inmediatamente y, una vez que se actualice la página, ya no verás el mensaje ni el botón.

6. Ahora debes habilitar la protección de PDF para archivos de SharePoint y OneDrive. <br/>

    En **Microsoft Purview Portal**, en **Protección de información** en el panel de navegación, selecciona **Etiquetado automático**.

7. En la página **Etiquetado automático**, deberías ver el banner **Proteger archivos PDF con etiquetado automático** en el centro de la página. Selecciona el encabezado de **Proteger archivos PDF con etiquetado automático** para activar la protección de PDF para los archivos de SharePoint y OneDrive. 

8. En el cuadro de diálogo **Directivas de etiquetado automático** que aparece, selecciona **Confirmar** para confirmar que deseas activar la protección de PDF para archivos de SharePoint y OneDrive. 

    **Nota:** el comando se ejecuta inmediatamente y, una vez que se actualice la página, ya no verás el banner **Proteger archivos PDF con etiquetado automático**.

9. Deja el explorador Edge abierto junto con todas las pestañas. 


### Tarea 3: Creación de una etiqueta de confidencialidad

En este ejercicio, crearás una etiqueta de confidencialidad y la agregarás a la directiva predeterminada para que sea válida para todos los usuarios del inquilino de Adatum.

1. En LON-CL1, en el explorador Edge, todavía deberías tener la sesión iniciada en Microsoft 365 como **Holly Dickson**.

2. En el explorador Edge, todavía deberías tener abierta una pestaña para **Microsoft Purview Portal** de la tarea anterior. En **Microsoft Purview Portal**, en el grupo **Protección de información** del panel, selecciona **Etiquetas de confidencialidad**. 

3. En la página **Etiquetas de confidencialidad**, selecciona la opción **+Crear una etiqueta** que aparece en la barra de menús en el medio de la pantalla, debajo del mensaje anterior. Esto inicia el Asistente para una **Nueva etiqueta de confidencialidad**.

4. En el asistente para una **Nueva etiqueta de confidencialidad**, en la página **Proporcionar detalles básicos para esta etiqueta**, escribe la siguiente información:

    - Nombre: **PII**
    
    - Nombre para mostrar: **PII**

    - Descripción para los usuarios: **Documentos, archivos y correos electrónicos con PII**

    - Descripción para los administradores: **Documentos, archivos y correos electrónicos con PII**

    - Color de etiqueta: selecciona uno de los colores que deseas asignar a las etiquetas de confidencialidad

5. Selecciona **Siguiente**.

6. En la página **Definir el ámbito de esta etiqueta**, comprueba que la casilla **Elementos** está activada, así como las casillas **Archivos**, **Correos electrónicos** y **Reuniones** debajo de ella (activa las cuatro casillas ahora, si es necesario). Estas casillas te permiten definir dónde se usará esta etiqueta de confidencialidad para que puedas configurar las opciones de protección aplicables. Selecciona **Siguiente**.

7. En la página **Elegir la configuración de protección para los tipos de elementos seleccionados** , puedes comenzar el proceso de usar la configuración de cifrado para restringir el acceso al contenido al que se aplicará la etiqueta. Cuando se cifra un documento, un correo electrónico o una reunión, el acceso al contenido está restringido, de manera que:  <br/>

    - Solo los usuarios autorizados en la configuración de cifrado de la etiqueta pueden descifrarlo.
    - Permanece cifrado independientemente de dónde se encuentre, dentro o fuera de la organización, incluso si se cambia el nombre del archivo.
    - Está cifrado tanto en reposo (por ejemplo, en una cuenta de OneDrive) como en tránsito (por ejemplo, un mensaje de correo electrónico cuando atraviesa Internet).

   Holly quiere configurar las opciones de cifrado, por lo que, en la página **Elegir opciones de protección para los tipos de elementos seleccionados**, activa la casilla **Control de acceso**. Activa también la casilla **Aplicar marcado de contenido** para que puedas configurar posteriormente los valores de encabezado, pie de página y marca de agua. Selecciona **Siguiente**.

8. Como seleccionaste la opción **Control de acceso** en la página anterior, ahora aparece la página **Control de acceso**. Esta página te permite configurar cómo aplica la etiqueta el cifrado. Ahora puedes elegir:  <br/>

    - **Quitar la configuración del control de acceso si ya se aplica a los elementos:** al seleccionar esta opción, la aplicación de la etiqueta quita el cifrado existente, incluso si se aplicó independientemente de una etiqueta de confidencialidad. Es importante comprender que la configuración puede dar lugar a una etiqueta de confidencialidad que es posible que los usuarios no puedan aplicar cuando no tienen permisos suficientes para quitar el cifrado existente.  
    - **Configurar la configuración del control de acceso:** esta opción activa el cifrado con administración de derechos. También hace que la siguiente configuración sea visible: <br/>
        - ¿Asignar ya permisos o permitir que los usuarios decidan?
        - Acceso del usuario al contenido expira
        - Permitir el acceso sin conexión

    **Nota:** es una estrategia de implementación común configurar inicialmente las etiquetas de confidencialidad para que no apliquen cifrado y, después, editar algunas de las etiquetas existentes para aplicar el cifrado. Este es el enfoque que Holly quiere adoptar. <br/>

    Por lo tanto, selecciona la opción **Quitar la configuración del control de acceso si ya se ha aplicado a los elementos** y, a continuación, selecciona **Siguiente**.

9. Como seleccionaste la opción **Aplicar marcado de contenido** en la página anterior, ahora aparece la página **Marcado de contenido**. Establece el botón de alternancia **Marcado de contenido** en **Activado**. Esto muestra tres opciones que te permiten personalizar cómo deseas marcar archivos y correos electrónicos. <br/>

    Selecciona las tres casillas de verificación. En cada configuración, selecciona **Personalizar texto**. Se abre un panel para personalizar esa configuración en concreto. Escribe la siguiente información en el panel **Personalizar** para cada opción (selecciona **Guardar** después de escribir la configuración para cada opción): <br/>

    - **Agregar una marca de agua** 
        - Texto de marca de agua: **Confidencial: No compartir** (sugerencia: después de escribir este valor, cópialo (Ctrl+C) para que puedas pegarlo (Ctrl+V) en las otras dos configuraciones de texto)
        - Tamaño de fuente: **25**
        - Color de fuente: **Azul**
        - Diseño del texto: **Diagonal**
            
    - **Agregar un encabezado** 
        - Texto de encabezado: **Confidencial: No compartir**
        - tamaño de fuente: **25**
        - Color de fuente: **Rojo**
        - Alinear texto: **Centrar**
            
    - **Agregar un pie de página**
        - Texto del pie de página: **Confidencial: No compartir**
        - tamaño de fuente: **25**
        - Color de fuente: **Rojo**
        - Alinear texto: **Centrar**

10. En la página **Marcado de contenido**, selecciona **Siguiente**. 

11. En la página **Etiquetado automático de archivos y correos electrónicos**, establece el botón de alternancia **Etiquetado automático para archivos y correos electrónicos** en **Activado**. Esto permite una serie de opciones que actualizarás en los pasos siguientes.

12. En **Detectar contenido que coincida con estas condiciones**, selecciona **+Agregar condición** y, a continuación, selecciona **El contenido contiene**.

13. En la ventana **El contenido contiene**, selecciona la flecha desplegable **Agregar** y, a continuación, selecciona **Tipos de información confidencial**.

14. En la ventana **Tipos de información confidencial**, mantén el mouse a la izquierda del encabezado de columna **Nombre**. Activa la casilla que aparece, que selecciona automáticamente todos los tipos de información confidencial. Selecciona **Agregar**, que agregarás todos estos tipos de información confidencial a la etiqueta.

15. En la página **Etiquetado automático de archivos y correos electrónicos**, se mostrarán todos los tipos de información confidencial que seleccionaste. Desplázate hasta la parte inferior de la ventana y actualiza la siguiente configuración:

    - Cuando el contenido coincide con estas condiciones: selecciona **Aplicar automáticamente la etiqueta**

    - Mostrar este mensaje a los usuarios cuando se aplique la etiqueta: escribe **Se ha detectado contenido confidencial y se cifrará**.
        
16. Selecciona **Siguiente**.

17. En la página **Definir la configuración de protección para grupos y sitios**, deja las casillas en blanco y selecciona **Siguiente**.

18. En la página **Etiquetado automático para recursos de datos esquematizados (versión preliminar)**, no habilites el etiquetado automático para los recursos de datos esquematizados (versión preliminar). Selecciona **Siguiente**. 

19. En la página **Revisar la configuración y finalizar**, revisa la información que escribiste. Si es necesario corregir algún valor de configuración, selecciona la opción **Editar** correspondiente y realiza los cambios necesarios. Cuando toda la información sea correcta, selecciona **Crear etiqueta**.

20. Debería aparecer un cuadro de diálogo **Error de cliente** que indique que el blob de reglas generado para la etiqueta que estás intentando crear es demasiado largo. El tamaño máximo de las selecciones de tipo de información confidencial que puedes realizar al mismo tiempo por regla es **49152**. Al seleccionar todos los tipos de información confidencial como hiciste en la ventana **Tipos de información confidencial** unos pocos pasos atrás, has superado este límite. <br/>

    **NOTA: hemos seleccionado todos los tipos de información confidencial a propósito para que recibas este error.** Queríamos que experimentaras este error para que, si se produce en los entornos de producción, sepas por qué recibiste el error y cómo puedes corregirlo.  <br/>

    Para corregir este problema, selecciona **Aceptar** en el cuadro de diálogo **Error de cliente** y, después, en la página **Revisar la configuración y finalizar**, desplázate hacia abajo hasta la sección **Etiquetado automático de archivos y correos electrónicos** y selecciona **Editar**.
    
21. Esto debería devolverte a la página **Elegir configuración de protección para elementos etiquetados** en el asistente. Selecciona **Siguiente** en esta página, selecciona **Siguiente ** en la página **Cifrado** y, a continuación, selecciona **Siguiente** en la página **Marcado de contenido**. Esto te llevará a la página **Etiquetado automático de archivos y correos electrónicos**. 

22. En la página **Etiquetado automático de archivos y correos electrónicos**, a la derecha de la condición **El contenido contiene**, selecciona el **icono de papelera**. Esto quitará la condición **El contenido contiene **existente para la etiqueta **PII** que creaste. <br/>

    En los pasos restantes, agregarás una nueva condición que solo contiene dos tipos de información confidencial en lugar de todos los tipos de información confidencial como lo hiciste originalmente.

23. En la página **Etiquetado automático de archivos y correos electrónicos**, en **Detectar contenido que coincida con estas condiciones**, selecciona **+Agregar condición** y, a continuación, selecciona **El contenido contiene**.

24. En la ventana **El contenido contiene**, selecciona la flecha desplegable **Agregar** y, a continuación, selecciona **Tipos de información confidencial**.

25. En la ventana **Tipos de información confidencial**, en la lista de tipos de información confidencial, selecciona solo las casillas **Número de ruta de ABA** y **Número de seguridad social (SSN) de Estados Unidos** y, a continuación, selecciona **Agregar**. De nuevo en la página **Etiquetado automático de archivos y correos electrónicos**, aparecerán ambos tipos de información confidencial. Seleccione **Siguiente**.

26. En la página **Definir la configuración de protección para grupos y sitios**, deje las dos casillas en blanco y seleccione **Siguiente**.

27. En la página **Etiquetado automático para recursos de datos esquematizados (versión preliminar)**, no habilite el etiquetado automático para las columnas de base de datos. Seleccione **Siguiente**.

28. En la página **Revisar la configuración y finalizar**, seleccione **Crear etiqueta**.

29. En la página **Se creó la etiqueta de confidencialidad**, seleccione la opción **No crear una directiva aún** y, a continuación, seleccione **Listo**. Esto le devuelve a la página **Etiquetas**.

30. Ahora es el momento de publicar la etiqueta **PII**. En la página **Etiquetas**, si la etiqueta **PII** no aparece en la lista de etiquetas, seleccione **Actualizar** en la barra de menús. Una vez que aparezca la etiqueta **PII**, active la casilla que aparece a la izquierda. 

31. Seleccione la opción **Publicar etiqueta** que aparece en la barra de menús situada por encima de la lista de etiquetas. Esto inicia un asistente para **Crear directivas**.

32. En el asistente para **Crear directivas**, en la página **Elegir etiquetas de confidencialidad para publicar**, la etiqueta **PII** ya aparece, por lo que debe seleccionar **Siguiente**. 

33. En la página **Asignar unidades de administración**, seleccione **Siguiente**, ya que va a asignar esta directiva PII al directorio completo de Adatum, en lugar de solo un grupo de unidades de administración.

34. En la página **Publicar en usuarios y grupos**, puede elegir si quiere que la directiva esté disponible para todos los usuarios y grupos, o bien puede limitar la directiva a usuarios y grupos seleccionados. Para este laboratorio, quiere que la directiva esté disponible para todos los usuarios. La opción **Usuarios y grupos** ya está seleccionada de manera predeterminada (si no es así, selecciónela ahora). Esto hará que la directiva esté disponible para todos los usuarios y grupos. Seleccione **Siguiente**.  <br/>

    **Nota:** Al hacerlo en la implementación real, si desea limitar la directiva a un número seleccionado de usuarios o grupos, seleccionaría **Editar** y realizaría esas selecciones. 

35. En la página **Configuración de directiva**, active la casilla **Los usuarios deben proporcionar una justificación para quitar una etiqueta o reducir su clasificación** y, a continuación, seleccione **Siguiente**. 

36. En la página **Aplicar una etiqueta predeterminada a documentos**, seleccione **PII** en el menú desplegable que aparece y, a continuación, seleccione **Siguiente**.

37. En la página **Aplicar una etiqueta predeterminada a los correos electrónicos**, seleccione **PII** en el menú desplegable que aparece y, a continuación, seleccione **Siguiente**.

38. En la página **Aplicar una etiqueta predeterminada a reuniones y eventos de calendario**, seleccione **PII** en el menú desplegable que aparece y, a continuación, seleccione **Siguiente**.

39. En la página **Aplicar una etiqueta predeterminada al contenido de Fabric y Power BI**, seleccione **PII** en el menú desplegable que aparece y, a continuación, seleccione **Siguiente**.

40. En la página **Nombre de la directiva**, escriba **Directiva PII** en el campo **Nombre** y, a continuación, escriba (o copie y pegue) la siguiente descripción para esta directiva de etiqueta de confidencialidad: **El propósito de esta directiva es detectar información confidencial, como números de enrutamiento bancario de ABA y números de seguridad social de EE. UU. en correos electrónicos y documentos, y cifrar esta información cuando se detecta. El usuario debe proporcionar una explicación para quitar la etiqueta de clasificación.** Seleccione **Siguiente**.

41. En la página **Revisar y finalizar**, revise la información que escribió. Si es necesario corregir algo, seleccione la opción **Editar** correspondiente y realice las correcciones necesarias. Cuando toda la información sea correcta, seleccione **Enviar**.

42. En la página **Nueva directiva creada**, seleccione **Listo**.

43. Deje el explorador Edge abierto junto con todas las pestañas. 


### Tarea 4: Asignar una etiqueta de confidencialidad preexistente a un documento

Como se describe en las instrucciones al principio de este laboratorio, no es posible probar inmediatamente la etiqueta de confidencialidad y la directiva de etiquetas que creó en la tarea anterior. Esto se debe a que una nueva directiva de etiquetas tarda hasta 24 horas en propagarse a través de Microsoft 365 y que su etiqueta sea visible en aplicaciones como Microsoft Word y Outlook.

En su lugar, probará una de las etiquetas de confidencialidad preexistentes de Microsoft 365. Para este laboratorio, usará la etiqueta de confidencialidad **Project - Falcon**, que es una etiqueta extremadamente confidencial. Esta etiqueta es similar a la etiqueta que creó en la tarea anterior: la única excepción es que no incluye un encabezado o pie de página. El uso de esta etiqueta preexistente le dará una buena idea de cómo la etiqueta que creó funcionaría en Adatum.

1. En LON-CL1, en el explorador Edge, todavía debe iniciar sesión en Microsoft 365 como **Holly Dickson**.

2. Primero revisará la etiqueta de confidencialidad **Project-Falcon** que aplicará a un documento de esta tarea.  En el explorador Edge, todavía debe tener abierta una pestaña para el portal de **Microsoft Purview** de la tarea anterior. En el portal de **Microsoft Purview**, en el grupo **Protección de la información** del panel, seleccione **Etiquetas**. 

3. En la página **Etiquetas**, en la lista de etiquetas, seleccione la flecha derecha (**>**) junto a ** Extremadamente confidencial** para mostrar las subetiquetas. Al hacerlo, se muestra la etiqueta **Project - Falcon** existente.

4. Seleccione la etiqueta **Project - Falcon** (no la casilla; seleccione el nombre de la etiqueta). Al hacerlo, se abre un panel de detalles de **Project - Falcon**. Revise la información definida para esta etiqueta y cierre el panel cuando haya terminado.  

5. Ahora asignará la etiqueta de confidencialidad **Project-Falcon** a un documento. Seleccione la pestaña **Inicio | Microsoft 365** en el explorador para volver a la página principal de Microsoft 365. Seleccione el icono **Aplicaciones** en el lado izquierdo de la pantalla. En la página **Aplicaciones** que aparece, haga clic con el botón derecho en el icono de **Word** y seleccione **Abrir en una nueva pestaña**. 

6. En la pestaña **Word | Microsoft 365**, en la sección **Crear nuevo** en la parte superior de la página, seleccione **Documento en blanco**.

7. Si aparece una ventana **Opción de privacidad**, seleccione **Cerrar**.

8. Si la cinta de opciones de Word muestra iconos para cada característica, pero no desglosa los iconos por grupo, seleccione la flecha hacia abajo en el lado derecho de la cinta de opciones y, después, en **Diseño de la cinta de opciones**, seleccione**Cinta clásica**. Esto cambiará la cinta de opciones al estilo de cinta tradicional que se desglosa por grupo de características (como Deshacer, Portapapeles, Fuente, Párrafo, Estilos, etc.).

9. En el documento de **Word**, escriba el texto siguiente: **Probar una etiqueta de confidencialidad en un documento con información de identificación personal (PII); en este caso, un número de seguridad social de EE. UU.: 111-11-1111.**

10. Dado que ha habilitado las etiquetas de confidencialidad al principio de este ejercicio, **Word** debe mostrar un grupo **Confidencialidad** en la cinta de opciones de la parte superior de la página. Seleccione la flecha hacia abajo en el grupo **Confidencialidad**. En el menú desplegable que aparece, se debe mostrar la lista de tipos de etiquetas de confidencialidad. Seleccione **Extremadamente confidencial** y, a continuación, en el submenú que aparece, seleccione **Project - Falcon**. <br/>

    **Nota:** Después de 24 horas, la etiqueta que creó en la tarea anterior aparecerá en el submenú Extremadamente confidencial, junto a la etiqueta Project-Falcon. Pero por ahora, usará la etiqueta **Project - Falcon** en su lugar.

11. En el documento, observe cómo la etiqueta aplicó una marca de agua **CONFIDENTIAL - ProjectFalcon** en la parte superior del documento. La etiqueta Project - Falcon se configuró igual que la etiqueta que creó, donde se suponía que la marca de agua aparecía diagonalmente a través del centro de la página. ¿Por qué aparece hacia la parte superior de la página? La respuesta es que está usando **Word para la Web**, que de manera predeterminada la muestra como se ve aquí. Para ver cómo aparecerá para alguien que lee el documento, debe ver el documento en la **Vista de lectura**, algo que hará ahora. <br/>

    Seleccione la pestaña **Vista** y, a continuación, en la cinta de opciones de Word, seleccione **Vista de lectura**. Observe cómo aparece la marca de agua diagonalmente a través del centro del documento. Así es como aparecerá la marca de agua para alguien que lea el documento. Tenga en cuenta que, si usa la aplicación de escritorio de Word, la marca de agua se muestra como la designa la etiqueta, que en este caso sería igual que como la ve aquí en la Vista de lectura. <br/>

    Para salir de la Vista de lectura, seleccione **Editar documento** en la barra de menús de la parte superior de la página. En el menú desplegable que aparece, seleccione **Editar**.

12. En esta primera prueba de validación, quitará esta etiqueta de confidencialidad para que no se aplique a este documento. Una de las opciones de directiva de etiquetas requiere que los usuarios proporcionen justificación para quitar una etiqueta o para seleccionar una etiqueta de clasificación inferior. Ahora comprobará si esta configuración funciona correctamente. <br/>

    En el grupo **Confidencialidad** de la cinta de opciones de Word, seleccione la flecha hacia abajo. En el menú desplegable que aparece, tenga en cuenta que aparece una marca de verificación junto a **Extremadamente confidencial**. Mantenga el mouse sobre **Extremadamente confidencial** para mostrar el submenú. Observe cómo aparece una marca de verificación junto a **Project - Falcon**. Las marcas de verificación identifican la etiqueta actual que se aplica al documento.  <br/>
 
    Para quitar la etiqueta de este documento, seleccione la etiqueta **Project - Falcon** que aparece en este menú desplegable.
    
13. En la ventana **Justificación requerida** que aparece, seleccione la opción **Otro (explicación)**. En el campo **Explicar por qué va a cambiar esta etiqueta**, escriba **Probar lo que sucede cuando se quita una etiqueta de un documento** y, a continuación, seleccione **Cambiar**.

14. Observe cómo ha desaparecido la marca de agua del documento. En el grupo **Confidencialidad** de la cinta de opciones de Word, seleccione la flecha hacia abajo. En el menú desplegable que aparece, tenga en cuenta que mientras se muestra **Extremadamente confidencial** > **Project - Falcon**, no aparecen marcas de verificación junto a ellos. Esto indica que la etiqueta de confidencialidad ya no se aplica a este documento.  

15. Para volver a aplicar la etiqueta de confidencialidad al documento, seleccione **Extremadamente confidencial** > **Project - Falcon** en el menú desplegable. Observe cómo vuelve a aparecer la marca de agua en el documento.

16. Ahora guardará el documento para que pueda compartirlo en la siguiente tarea. Un campo de nombre de documento que contiene una flecha desplegable aparece en la esquina superior izquierda de la página, a la derecha del icono de Word (Word puede mostrar **Document** o **Document1** como nombre de archivo temporal). Seleccione la flecha desplegable. En el menú desplegable que aparece, confirme que la **Ubicación** del archivo indica **Holly Dickson > Documentos**. <br/>

    En el campo **Nombre de archivo**, cambie el nombre del archivo a **ProtectedDocument1** y, a continuación, seleccione fuera de este menú de nombre de archivo (seleccione dentro del documento). Observe que el nuevo nombre asignado al archivo aparece en la barra de título. 

17. Deje abierta la pestaña **ProtectedDocument1** en la que se muestra el documento. Volverá a este documento en la siguiente tarea para compartir el documento con Joni Sherman.

Acaba de crear correctamente un documento de Word que contiene la etiqueta Extremadamente confidencial titulada **Project - Falcon**. 


### Tarea 5: Proteger un documento mediante Microsoft Purview Information Protection

En la tarea anterior, creó un documento de Word y lo protegió con la etiqueta de confidencialidad **Project - Falcon**. Esta etiqueta insertó una marca de agua en el documento. En esta tarea, compartirá el documento que creó con Joni Sherman y restringirá a Joni al permiso "Solo visualización". Esto le permitirá ver cómo Microsoft Purview Information Protection protege el documento en función de los parámetros que configure.

Para comprobar si la protección que asignó al documento funciona, primero enviará el documento a dos personas: a Joni Sherman y a su propia dirección de correo electrónico personal. A continuación, comprobará que Joni solo pueda ver el documento y no editarlo, y comprobará que no pueda acceder al documento, ya que no se ha compartido con usted. Por último, cambiará el permiso en el documento para que Joni pueda editarlo y le enviará un correo electrónico a este documento actualizado para realizar pruebas. El propósito de los dos correos electrónicos a Joni, uno con un vínculo de documento que proporciona acceso de solo lectura y otro con un vínculo de documento que proporciona la capacidad de editar el documento, es ver cómo Microsoft Entra ID Protection puede proporcionar varios niveles de protección de documentos. 

1. En LON-CL1, en el explorador Edge, todavía debe tener iniciada la sesión en Microsoft 365 como **Holly Dickson** desde la tarea anterior con la pestaña **Word** abierta.

2. En el explorador Edge, seleccione la pestaña **Aplicaciones | Microsoft 365**. 

3. En la página **Aplicaciones**, haga clic con el botón derecho en el icono de **Outlook** y seleccione **Abrir en una pestaña nueva**. Esto abre el buzón de Holly en Outlook en la Web en una nueva pestaña del explorador. 

4. En **Outlook en la Web**, seleccione **Nuevo correo** en la parte superior izquierda de la pantalla.

5. Introduzca la siguiente información en el formulario de correo electrónico:

    - A: Escriba **Joni** y, a continuación, seleccione **Joni Sherman** en la lista de usuarios. 

    - CC: Escriba su propia dirección de correo electrónico personal (NO escriba la dirección de correo electrónico de Holly; en su lugar, escriba su propia dirección de correo electrónico personal) y, a continuación, seleccione el mensaje **Usar esta dirección: <your email address>** que aparece

    - Agregar un asunto: **Prueba de documentos protegidos: permiso de Solo visualización**

    - Cuerpo del mensaje: escriba **Abrir el documento protegido adjunto a este correo electrónico e intentar cambiarlo.**

6. En el cuerpo del mensaje, debajo del texto que agregó en el paso anterior, adjuntará un vínculo al documento que creó en la tarea anterior. Sin embargo, para ello, primero debe compartir el documento con Joni Sherman y, al hacerlo, aplicará permisos restringidos de **Solo visualización**. Para ello, debe dejar este correo electrónico y volver al documento y compartirlo con Joni. Una vez que copie el vínculo que se crea durante el proceso de uso compartido, volverá a este correo electrónico y pegará el vínculo. <br/>

    En el explorador Edge, seleccione la pestaña **ProtectedDocument1**, que todavía debe mostrar el documento que creó en la tarea anterior. En la parte superior derecha de la página, debajo del nombre y las iniciales de Holly Dickson, seleccione el botón **Compartir**. En el menú desplegable que aparece, seleccione **Compartir**.

7. En la ventana **Compartir "ProtectedDocument1"** que aparece, seleccione el icono de engranaje (**Configuración de vínculo**) que aparece junto al botón **Copiar vínculo**. 

8. En la ventana **Configuración del vínculo** que aparece, seleccione la opción **Personas que elija**.
    
9. En **Más opciones**, la opción actual es **Puede editar**. Tiene previsto compartir este documento con Joni Sherman, pero solo quiere que Joni pueda ver el documento. Para realizar este cambio de permisos, seleccione **Puede editar**. En el menú que aparece, revise las opciones disponibles. Puede ver que **Puede editar** tiene una marca de verificación junto a ella, lo que indica que esta es la configuración actual. Para limitar Joni al permiso de solo lectura, seleccione **Puede ver** y, a continuación, seleccione **Aplicar**.

10. Esto le devuelve a la ventana **Compartir "ProtectedDocument1"**. Escriba **Joni** en el campo **Agregar un nombre, grupo o correo electrónico**. Aparecerá una lista de usuarios cuyo nombre comienza por **Joni**. Seleccione **Joni Sherman**.

11. En la ventana **Compartir "ProtectedDocument1"**, mantenga el mouse sobre el icono de "ojo" que aparece a la derecha del nombre de Joni. Si lo hace, se debería mostrar **Puede ver**, que es la configuración actual que se asignó a ella para este documento. El icono de "ojo" es la designación de "Puede ver". Seleccione el botón **Copiar vínculo**. 

12. Una vez que aparezca el mensaje **Vínculo copiado** en la parte inferior de la ventana **Compartir "ProtectedDocument1"**, seleccione la X en la esquina superior de la ventana para cerrarlo.

13. En el explorador Edge, seleccione la pestaña **Correo - Holly Dickson -Outlook** para volver al mensaje de correo electrónico. En el cuerpo del mensaje, debajo del texto que agregó anteriormente, pegue (Ctrl+V) el vínculo al documento compartido que acaba de copiar en el Portapapeles. Debería aparecer un vínculo para el archivo denominado **ProtectedDocument1.docx**. 

14. Seleccione **Enviar**.

15. Debería aparecer un mensaje **Los destinatarios no pueden acceder a los vínculos**. Este mensaje es el resultado de Microsoft Entra ID Protection que reconoce el hecho de que incluyó su dirección de correo electrónico personal en el correo electrónico, que no tiene permiso para acceder al documento. Para la prueba de este laboratorio, seleccione **Enviar de todos modos**.

16. Cambie a **LON-CL2**. 

17. En **LON-CL2**, debe tener iniciada la sesión en **Outlook en la Web** como **Lynne Robbins** del ejercicio de laboratorio anterior. Cierre sesión como Lynne.

18. En el explorador Edge, cierre todas las pestañas excepto la pestaña **Cerrar sesión**. En esta pestaña, escriba la siguiente dirección URL en la barra de direcciones: **https://outlook.office365.com** 

19. En la ventana **Elegir una cuenta**, seleccione **Usar otra cuenta**.

20. En la ventana **Iniciar sesión**, escriba **JoniS@xxxxxZZZZZZ.onmicrosoft** (donde xxxxxZZZZZZ es el prefijo de inquilino proporcionado por el proveedor de hospedaje de laboratorio) y, a continuación, seleccione **Siguiente**.

21. En la ventana **Escribir contraseña**, escriba la nueva contraseña de usuario que asignó previamente a la cuenta de Joni y, luego, seleccione **Iniciar sesión**. 

22. Si aparece una ventana de **bienvenida**, seleccione la X para cerrarla.

23. En la **Bandeja de entrada** de Joni en **Outlook en la Web**, debería ver el correo electrónico que Holly acaba de enviar cuya línea de asunto indica que el documento tiene el permiso Solo visualización. Abra este correo electrónico.

24. En el correo electrónico, seleccione el archivo adjunto para abrirlo.

25. En la ventana **Opción de privacidad** que aparece, seleccione **Cerrar**. El documento se abre en **Word en la Web** en una nueva pestaña del explorador titulada **ProtectedDocument1.docx**. Observe cómo aparece el documento en la Vista de lectura en **Word en la Web**. Esta es la indicación de Joni de que tiene permiso de Solo visualización y no puede editar el documento. Para comprobarlo, intente seleccionar en el documento. Tenga en cuenta el mensaje que aparece que indica: **Solo lectura. El documento es de solo lectura.** Note la marca de agua especificada en la directiva **Project - Falcon**. <br/>

    Una vez que haya terminado de revisar el documento, cierre la pestaña **ProtectedDocument1.docx**. 

26. Ahora probará lo que sucede cuando intente abrir el documento que se envió a su dirección de correo electrónico personal. Use su teléfono móvil o PC educativa para acceder a su buzón personal. Abra el correo electrónico que Holly acaba de enviar a su dirección de correo electrónico personal e intente abrir el archivo adjunto. 

27. Como no tiene permiso para acceder al documento, debería aparecer una ventana **Elegir una cuenta**. En un escenario real, podría iniciar sesión con una cuenta que tenga permiso para acceder al archivo o solicitar acceso desde la cuenta **Holly@xxxxxZZZZZZ.onmicrosoft.com**. <br/>

    Para esta prueba, acaba de comprobar que no puede acceder al archivo porque no se ha compartido con usted. También ha comprobado que Joni solo pudo ver el archivo, pero no editarlo. Ahora cambiará los permisos de uso compartido en el archivo y permitirá que Joni lo edite. Lo hará para ver cómo difiere esta experiencia de la que acaba de completar. 

28. Cambie a **LON-CL1**. 

29. En LON-CL1, en el explorador Edge, todavía debería tener iniciada la sesión en Microsoft 365 como **Holly Dickson** y debería tener pestañas abiertas para **Word** y **Outlook**. Seleccione la pestaña **Correo - Holly Dickson - Outlook**. 

30. En el buzón de Holly, cree otro correo electrónico para Joni Sherman. NO incluya su dirección de correo electrónico personal en la línea CC. Introduzca la siguiente información en el formulario de correo electrónico:

    - A: Escriba **Joni** y, a continuación, seleccione **Joni Sherman** en la lista de usuarios. 

    - CC: déjelo en blanco

    - Agregar un asunto: **Prueba de documentos protegidos: permiso de edición**

    - Cuerpo del mensaje: escriba **Abrir el documento protegido adjunto a este correo electrónico e intentar cambiarlo.**

31. Al igual que con el correo electrónico anterior, ahora debe compartir el documento con Joni, pero esta vez con el permiso Editar. Para ello, lleve a cabo los siguientes pasos: <br/>

    - Seleccione la pestaña **ProtectedDocument1** del explorador y, a continuación, en el lado derecho de la barra de menús, seleccione el botón **Compartir**. En el menú desplegable que aparece, seleccione **Compartir**. 
    - En la ventana **Compartir "ProtectedDocument1"**, escriba **Joni** en el campo **Agregar un nombre, grupo o correo electrónico** y, a continuación, seleccione **Joni Sherman**.
    - A la derecha del nombre de Joni se encuentra un icono de lápiz (**Puede editar**). Este es el permiso predeterminado al compartir un documento. Seleccione el botón **Copiar vínculo** para ver lo que sucede.
    - Note el mensaje **Vínculo copiado** que aparece. El mensaje indica que cualquier persona puede editar el documento, aunque haya especificado el nombre de Joni. Esto no es lo que quiere, que es limitar a Joni como la única persona que puede editarlo. Para poner esa restricción en vigor, seleccione el icono de engranaje (**Configuración de vínculo**) situado junto al botón **Copiar vínculo**. 
    - En la ventana **Configuración del vínculo** que aparece, seleccione la opción **Personas que elija**. Esta opción es la clave para limitar el permiso a los usuarios seleccionados. 
    - En **Más opciones de configuración**, si aparece **Puede editar**, selecciona **Aplicar**. Sin embargo, si aparece **Puede ver**, selecciona **Puede ver** y, en el menú que aparece, selecciona **Puede editar** y, a continuación, selecciona **Aplicar**. 
    - En la ventana **Compartir "ProtectedDocument1"**, selecciona el botón **Copiar vínculo**.
    - Observa el mensaje **Vínculo copiado** que aparece. Esta vez el mensaje indica que solo las personas que especifiques pueden editar el documento. En este caso, la edición se limitará a Joni, ya que es la única persona que especificaste. 
    - Selecciona la pestaña **Mail - Holly Dickson - Outlook** en el explorador y, a continuación, pega el vínculo en el cuerpo del mensaje de correo electrónico. 

32. Selecciona **Enviar**.

33. Cambia a **LON-CL2**. 

34. En **LON-CL2**, todavía deberías tener iniciada la sesión en **Outlook en la Web** como **Joni Sherman**. En la **Bandeja de entrada** de Joni, deberías ver el correo electrónico que Holly acaba de enviar cuya línea de asunto indica que el documento tiene permiso para Editar. Abre este correo electrónico.

35. En el correo electrónico, selecciona el archivo adjunto para abrirlo.

36. Cuando Joni tenía el permiso Solo visualización, el documento se abrió en el panel Vista de lectura. Por lo tanto, Joni no pudo editar el documento. Esta versión del documento proporciona permiso de edición a Joni, por lo que esta vez el documento debe abrirse en Word en modo de edición normal. Comprueba que puedes escribir texto en el documento. 

    **Nota:**  en esta tarea, acabas de comprobar que Microsoft Purview Information Protection protegió el documento en función de los parámetros de la directiva PII que configuraste. Cuando a Joni se le asignó el permiso de Solo visualización, el documento se abrió en la Vista de lectura y no pudo cambiarlo. Cuando a Joni se le asignó el permiso Editar, el documento se abrió en Word y pudo cambiarlo. Y como Holly no compartió el documento contigo, no pudiste abrirlo cuando ella envió el documento en un correo electrónico a tu buzón personal. 

## Fin del laboratorio 4


# Felicidades. Acabas de completar el laboratorio final en este curso.
