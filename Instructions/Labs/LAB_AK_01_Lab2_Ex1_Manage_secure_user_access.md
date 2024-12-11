# Ruta de aprendizaje 1 - Laboratorio 2 - Ejercicio 1: Administración del acceso seguro de usuarios 

Las organizaciones deben asegurarse de que el acceso a los datos de su empresa en Microsoft 365 sea siempre seguro. Microsoft 365 muestra a menudo datos confidenciales y privados, incluyendo correos electrónicos, documentos, información del cliente y propiedad intelectual. El acceso no autorizado a Microsoft 365 puede provocar infracciones de datos, robo de identidad y otras actividades malintencionadas. Al proteger el acceso de los usuarios, las organizaciones impedirán que personas no autorizadas accedan a los datos de la empresa y hagan mal uso de ellos o los filtren al trabajar en Microsoft 365.

En el siguiente ejercicio de laboratorio, continuarás en tu rol como Holly Dickson, nueva administradora de Microsoft 365 de Adatum. Realizarás varias funciones de administración de usuarios y grupos en Microsoft 365. Comenzarás creando una cuenta de usuario de Microsoft 365 para Holly, a quien se le asignará el rol de administrador global de Microsoft 365. Crearás varios grupos de Microsoft 365 y asignarás usuarios existentes de Microsoft 365 como miembros de esos grupos. A continuación, eliminarás uno de los grupos y, luego, usarás Windows PowerShell para recuperar el grupo eliminado.

**Nota:** el entorno de máquina virtual proporcionado por el proveedor de hospedaje del laboratorio incluye más de 20 cuentas de usuario de Microsoft 365 existentes, así como un gran número de cuentas de usuario locales existentes. En este curso se usarán varias de las cuentas de usuario de Microsoft 365 existentes en todos los laboratorios. Aunque el proveedor de hospedaje del laboratorio haya creado la cuenta de Administrador MOD, seguirás creando la cuenta de usuario de Holly Dickson, ya que tener más de un usuario que tenga asignado el rol de administrador global de Microsoft 365 es un procedimiento recomendado. También se te proporcionará la experiencia de crear una cuenta de usuario de Microsoft 365 en caso de que no estés familiarizado con el proceso.

Entonces, el director de tecnología de Adatum le pide a Holly que implemente la autenticación multifactor (MFA) y Smart Lockout de Microsoft Entra. Estas características ayudarán a reforzar la administración de contraseñas en toda la organización como preparación para Copilot para Microsoft 365. En cuanto a Smart Lockout, lo implementarás mediante la administración de directivas de grupo. 


### Tarea 1: Creación de una cuenta de usuario de administrador de Microsoft 365 de Adatum

Holly Dickson es la nueva administradora de Microsoft 365 de Adatum. Debido a que no se configuró una cuenta de usuario de Microsoft 365 para ella, inició sesión inicialmente en Microsoft 365 como la cuenta de Administrador MOD (el administrador global predeterminado) del laboratorio anterior. En esta tarea seguirás iniciando sesión como Administrador MOD, durante la cual crearás una cuenta de usuario de Microsoft 365 para Holly. También asignarás el rol de administradora global de Microsoft 365 a la cuenta de Holly. Este rol proporcionará a Holly los permisos necesarios para realizar todas las funciones administrativas dentro de Microsoft 365. Después de esta tarea, iniciarás sesión con la nueva cuenta de Holly y realizarás todos los laboratorios restantes con el rol de Holly. 

**Nota de licencia:** antes de crear la cuenta de Holly, primero comprobarás el número de licencias disponibles. Al hacerlo, observarás que, aunque tu inquilino de laboratorio proporciona 20 licencias de Microsoft 365 E5 (sin Teams) y 20 licencias de Microsoft Teams Enterprise, todas esas licencias ya se asignaron a las cuentas de usuario existentes creadas por el proveedor de hospedaje del laboratorio. Por lo tanto, primero es necesario anular la asignación de cada una de las licencias de usuario existentes para poder asignarlas a Holly.

**Importante:** como procedimiento recomendado en la implementación real, siempre deberías anotar las credenciales de la primera cuenta de administrador global (en este laboratorio, se trata de la cuenta de administrador MOD, cuyo nombre de usuario es admin@xxxxxZZZZZZ.onmicrosoft.com, donde xxxxxZZZZZZ es el prefijo de inquilino asignado por el proveedor de hospedaje del laboratorio). Deberías almacenar esta información de cuenta por motivos de seguridad. **Esta cuenta debería ser una identidad NO personalizada** que posea los privilegios más altos posibles de un inquilino. **No** se debería activar MFA porque no está personalizado. Dado que el nombre de usuario y la contraseña de esta primera cuenta de administrador global suelen compartirse entre varios usuarios, esta cuenta resulta ser un blanco perfecto para ataques. Por lo tanto, siempre se recomienda que las organizaciones creen cuentas de administrador de servicios personalizadas (por ejemplo: un administrador de Exchange, un administrador de SharePoint, etc.) y tengan los mínimos administradores globales personales posibles. Para aquellos administradores globales personales que se creen en la implementación real, a cada uno de ellos se le debería asignar un único usuario (como Holly Dickson) y a cada uno se le debería aplicar la autenticación multifactor (MFA) de Microsoft Entra.  

1. En la máquina virtual **LON-CL1**, el **Centro de administración de Microsoft 365** debe estar abierto en el explorador Microsoft Edge desde el ejercicio de laboratorio anterior. Deberías iniciar sesión en Microsoft 365 como **Administrador MOD**. 

2. Dado que agregarás un nuevo usuario, deberías comenzar comprobando la disponibilidad de licencias antes de agregar la cuenta de usuario. En el panel de navegación del **Centro de administración de Microsoft 365**, selecciona **Facturación** para expandir el grupo Facturación y, a continuación, selecciona **Licencias**. 

3. En la página **Licencias**, la pestaña **Suscripciones** se muestra de forma predeterminada. En la lista de suscripciones, observa que las suscripciones **Microsoft 365 E5 (sin Teams)** y **Microsoft Teams Enterprise** no tienen licencias disponibles. El inquilino del laboratorio proporciona 20 licencias para cada suscripción, pero se han asignado todas las 40 licencias. Como debes asignar a Holly una licencia de **Microsoft 365 E5 (sin Teams)** y una licencia de **Microsoft Teams Enterprise**, primero deberás anular la asignación de las licencias de una cuenta de usuario existente para que estén disponibles para Holly. 

4. En el panel de navegación del **Centro de administración de Microsoft 365**, selecciona **Usuarios** y, a continuación, selecciona **Usuarios activos**. En la lista **Usuarios activos**, verás la lista de cuentas de usuario existentes creadas por el proveedor de hospedaje del laboratorio. Puesto que Christie Cline pasará a un nuevo rol en la empresa y ya no formará parte del proyecto piloto de Microsoft 365, anularás la asignación de las licencias de **Microsoft 365 E5 (sin Teams)** y **Microsoft Teams Enterprise** de su cuenta para reasignarlas a la nueva cuenta de Holly Dickson.

5. En la página **Usuarios activos**, en la lista de usuarios, selecciona **Christie Cline** (selecciona el nombre con hipervínculo de Christie y no la casilla situada junto a su nombre).

6. En el panel de **Christie Cline** que aparecerá, la pestaña **Cuenta** se mostrará de forma predeterminada. Selecciona la pestaña **Licencias y aplicaciones**. En **Licencias (2)**, activa las casillas situadas junto a **Microsoft 365 E5 (sin Teams)** y **Microsoft Teams Enterprise** para desactivarlas y, a continuación, selecciona **Guardar cambios**. Una vez guardados los cambios, cierra el panel **Christie Cline**. 

7. Ya estás listo para crear una cuenta de usuario para Holly Dickson, que es la nueva administradora de Microsoft 365 de Adatum. Al hacerlo, asignarás a Holly el rol de administradora global de Microsoft 365, que proporcionará a Holly acceso global a la mayoría de las características de administración y los datos en todos los servicios en línea de Microsoft. También asignarás a Holly las dos licencias de las que acabas de cancelar la asignación de Christie Cline. <br/>

    En la ventana **Usuarios activos**, selecciona la opción **Agregar un usuario** que aparece en la barra de menús situada encima de la lista de usuarios activos. Esto iniciará el **Asistente para agregar usuarios**.

8. En la página **Configurar los aspectos básicos** del **Asistente para agregar usuarios**, escribe la siguiente información:

    - Nombre: **Holly**

    - Apellido: **Dickson** 

    - Nombre para mostrar: Al hacer una tabulación en este campo, aparecerá **Holly Dickson**.

    - Nombre de usuario: **Holly** <br/>
    
        **IMPORTANTE:** a la derecha del campo **Nombre de usuario** está el campo de dominio. Se rellenará previamente con el dominio en la nube **xxxxxZZZZZZ.onmicrosoft.com** (donde xxxxxZZZZZZ es el prefijo del inquilino proporcionado por el proveedor de hospedaje del laboratorio).<br/>
    
    - Desmarca la casilla **Crear automáticamente una contraseña**, lo que mostrará un nuevo campo para escribir una contraseña definida por el administrador.

    - Escribe la nueva contraseña administrativa en el campo **Contraseña** que aparece (esta es la **nueva contraseña administrativa** que se te pidió que crearas al principio del Laboratorio 1, Ejercicio 1)

    - Borra (desactive) la casilla **Requerir a este usuario que cambie la contraseña la primera vez que inicie sesión** 

9. Selecciona **Siguiente**. Si apareciera un cuadro de diálogo **Guardar contraseña** en la parte superior de la pantalla, selecciona **Nunca**.

10. En la página **Asignar licencias de producto**, escribe la siguiente información: <br/>

    - Selecciona la ubicación: **Estados Unidos**

    - Licencias: En la opción **Asignar una licencia de producto a un usuario**, activa las casillas **Microsoft 365 E5 (sin Teams)** y **Microsoft Teams Enterprise**.

11. Selecciona **Siguiente**.

12. En la página **Configuración opcional**, selecciona la flecha desplegable situada a la derecha de **Roles**. 

13. En la sección **Roles**, selecciona la opción **Acceso al Centro de administración**. Al seleccionar esta opción, los roles de administrador de Microsoft 365 más usados se habilitarán debajo.  <br/>

    **Nota:** todos los roles de administrador se mostrarán si seleccionas **Mostrar todo por categoría**, que aparecerá después del último rol común. Para Holly, no es necesario ver todos los roles de administrador por categoría, ya que Holly tendrá asignado el rol de administrador global que aparecerá en la lista de roles usados habitualmente.

14. Selecciona la casilla **Administrador global**. <br/>

    **Nota:** se mostrará un mensaje de advertencia indicando que Adatum ya tiene 7 administradores globales. En un entorno normal, esto sería excesivo y no se recomienda. Para los fines de este laboratorio, el proveedor de hospedaje del laboratorio asignó el rol de administrador global al Administrador MOD y otras seis cuentas de usuario, algo que no se vería normalmente en una implementación real. Sin embargo, para los fines de este laboratorio sobre el entorno de laboratorio ficticio de Adatum, omite este mensaje. **Dicho esto, la guía de procedimientos recomendados que deberías seguir consiste en tener de dos a cuatro administradores globales en las implementaciones reales de Microsoft 365.** 

15. Selecciona **Siguiente**.

16. En la ventana **Revisar y finalizar**, revisa las selecciones. Si se debiera cambiar algo, selecciona el vínculo **Editar** adecuado y realiza los cambios necesarios. De lo contrario, si todo fuera correcto, selecciona **Terminar de agregar**. 

17. En la página **Se agregó a Holly Dickson a usuarios activos**, en la sección **Detalles del usuario**, selecciona la opción **Mostrar** para comprobar que la contraseña de Holly es la misma **nueva contraseña administrativa** que se te pidió que crearas al principio del Laboratorio 1, Ejercicio 1.  <br/>

    **Nota:** si escribiste accidentalmente una contraseña diferente, una vez que vuelvas a la página **Usuarios activos**, deberás seleccionar el icono **Restablecer una contraseña** (el icono de clave que aparecerá al mover el puntero sobre la cuenta de Holly) para cambiar su contraseña al valor correcto.

18. Selecciona **Cerrar**.

19. Permanece conectado a la máquina virtual del cliente 1 (LON-CL1) con el Centro de administración de Microsoft 365 abierto en el explorador para la siguiente tarea.


### Tarea 2: Actualización del grupo del proyecto piloto de Microsoft 365

Después de completar la tarea anterior, deberías tener la sesión iniciada en el **Centro de administración de Microsoft 365** con la cuenta de **Administrador MOD**. En esta tarea, comenzarás a implementar el proyecto piloto de Microsoft 365 de Adatum como Holly Dickson, nueva administradora de Microsoft 365 de Adatum. Por lo tanto, iniciarás esta tarea al cerrar sesión en Microsoft 365 como Administrador MOD y volverás a iniciar sesión como Holly. 

En una tarea anterior, creaste un grupo de Microsoft 365 para los miembros del equipo de proyecto piloto de Adatum para poder crear un tema personalizado para ese grupo. En esta tarea, agregarás a Holly a este grupo. 

1. En la máquina virtual LON-CL1, el **Centro de administración de Microsoft 365** aún debería estar abierto en el explorador Microsoft Edge desde la tarea anterior. Deberías iniciar sesión en Microsoft 365 como **Administrador MOD**. <br/>

    En la pestaña del **Centro de administración de Microsoft 365**, en la esquina superior derecha de la pantalla, observa que se muestra el nombre del Administrador MOD y el icono de un megáfono. El nombre se muestra debido al tema personalizado que creaste en el ejercicio del laboratorio anterior asociado a un grupo de usuarios de proyectos piloto de Microsoft 365 que incluyó el Administrador MOD. Ten esto en cuenta cuando vuelvas a iniciar sesión como Holly Dickson. <br/>

    Selecciona el icono de usuario o el círculo con las iniciales "MA" del **Administrador MOD** en la esquina superior derecha del explorador. En la ventana **Administrador MOD** que aparece, selecciona **Cerrar sesión.** <br/>
    
    **Importante:** al cerrar la sesión de una cuenta de usuario e iniciar sesión en otra, deberías cerrar todas las pestañas del explorador, excepto la pestaña **Cerrar sesión**. Este es un procedimiento recomendado que ayuda a evitar cualquier confusión cerrando las ventanas asociadas al usuario anterior. Una vez que hayas cerrado la sesión de la cuenta de Administrador MOD, tómate un momento y cierra todas las demás pestañas del explorador, excepto la pestaña **Cerrar sesión**. 
    
2. En el explorador Microsoft Edge, en la pestaña **Cerrar sesión**, escribe la siguiente dirección URL en la barra de direcciones para volver a iniciar sesión en Microsoft 365: **https://portal.office.com**. 

3. En la ventana **Elegir una cuenta**, solo aparecerá la cuenta de administrador de inquilinos del Administrador MOD (la cuenta de admin@xxxxxZZZZZZ.onmicrosoft.com) de la que acabas de cerrar sesión. Selecciona **Usar otra cuenta**. 

4. En la ventana **Iniciar sesión**, escribe **Holly@xxxxxZZZZZZ.onmicrosoft.com** (donde xxxxxZZZZZZ es el prefijo de inquilino proporcionado por el proveedor de hospedaje del laboratorio). Selecciona **Siguiente**.

5. En la ventana **Escribir contraseña**, escribe la nueva contraseña administrativa que asignaste a la cuenta de Holly y, a continuación, selecciona **Iniciar sesión**. 

6. Si aparece el cuadro de diálogo **¿Mantener la sesión iniciada?**, activa la casilla **No volver a mostrar** y, a continuación, activa **Sí.** 

7. Si aparece el cuadro de diálogo **Le damos la bienvenida a Microsoft 365** en medio de la pantalla, ten en cuenta que no hay ninguna opción para cerrarlo. En su lugar, a la derecha de la ventana, selecciona el icono de flecha hacia delante (**>**) dos veces y, a continuación, selecciona el icono de marca de verificación para avanzar a través de las diapositivas de esta ventana de mensajes. 

8. Si aparece la ventana **Crear con Microsoft 365**, selecciona la **X** en la esquina superior de la ventana para cerrarla. 

9. La página **Le damos la bienvenida a Microsoft 365** aparecerá en el explorador Edge, en la pestaña **Inicio | Microsoft 365**. Esta es la página principal de Microsoft 365 de Holly. Observa que las iniciales de Holly aparecen en la esquina superior derecha de la pantalla, sin embargo, no se muestra el nombre de Holly. Esto se debe a que la cuenta de Holly no existía cuando se agregó a los usuarios de proyectos piloto de Microsoft 365 al grupo asociado al tema personalizado en el ejercicio del laboratorio anterior. Como Holly desea ver su nombre en la parte superior de cada ventana de Microsoft 365 cuando inicie sesión en el sistema, primero querrá agregar su cuenta al grupo de usuarios de proyectos piloto de Microsoft 365. <br>

    En la columna de iconos de aplicación que aparece en el panel de navegación del lado de la pantalla, selecciona **Administrador**. Esto abrirá el **Centro de administración de Microsoft 365** en una nueva pestaña del explorador. 

10. En el **Centro de administración de Microsoft 365**, selecciona **Equipos y grupos** en el panel de navegación y, después, en él, selecciona **Equipos y grupos activos**. 

11. En la página **Equipos y grupos activos**, hay una pestaña para ver cada uno de los tipos de grupo. La pestaña **Grupos de Teams y Microsoft 365** se muestra de forma predeterminada. En esta pestaña, selecciona **Proyecto piloto de M365**.

12. En el panel **Proyecto piloto de M365** que se muestra, la pestaña **General** se mostrará de forma predeterminada. Selecciona la pestaña **Pertenencia**.

13. En la pestaña **Pertenencia**, la subpestaña **Propietarios** se mostrará de forma predeterminada en el panel de navegación que aparecerá en el lado del panel. Selecciona la subpestaña **Miembros** que hay debajo de ella.

14. En la subpestaña **Miembros**, selecciona **+Agregar miembros**.

15. En el panel **Agregar miembros de grupo al proyecto piloto de M365** que se muestra, selecciona dentro del campo **Buscar por nombre o dirección de correo electrónico**. En la lista de usuarios que aparece, desplázate hacia abajo y selecciona **Holly Dickson**. Selecciona el botón **Agregar (1)** y, a continuación, cierra el panel **Agregar miembros de grupo al proyecto piloto de M365** una vez que Holly se agregue al grupo.

16. Permanece conectado a LON-CL1 con el **Centro de administración de Microsoft 365** abierto en el explorador para la siguiente tarea.


### Tarea 3: Creación de una directiva de acceso condicional para implementar MFA

Tal y como se indica en el entrenamiento, hay tres maneras de implementar MFA: con directivas de acceso condicional, con valores predeterminados de seguridad y con MFA por usuario heredado (no se recomienda para organizaciones grandes). En este ejercicio, habilitarás MFA mediante una directiva de acceso condicional, que es el método que Microsoft recomienda. 

Adatum le ha pedido a Holly que habilite MFA para todos los usuarios de Microsoft 365, tanto internos como externos. Sin embargo, para probar la implementación del proyecto piloto de Microsoft 365 de Adatum, Holly desea excluir a los miembros del grupo del proyecto piloto de M365 de tener que usar MFA para iniciar sesión. Una vez completado el proyecto piloto, Holly piensa actualizar la directiva quitando la exclusión de este grupo del requisito de MFA. La directiva también incluirá otros dos requisitos. Se requerirá MFA para todas las aplicaciones en la nube y se requerirá MFA incluso aunque los usuarios inicien sesión desde ubicaciones de confianza. 

1. En el ejercicio de laboratorio trabajaste en LON-DC1. En esta tarea, volverás a trabajar en la máquina de cliente 1. <br/>

    Cambia a **LON-CL1**.

2. En la máquina virtual LON-CL1, el **Centro de administración de Microsoft 365** aún debería estar abierto en el explorador Microsoft Edge desde la tarea anterior. Deberías tener la sesión iniciada en Microsoft 365 como **Holly Dickson**.
   
3. En el **Centro de administración de Microsoft 365**, en la sección **Centros de administración** del panel de navegación, selecciona **Identidad**. Al hacerlo, se abrirá el Centro de administración Microsoft Entra en una nueva pestaña del explorador. Si apareciera una ventana indicando **Seleccionar una cuenta**, selecciona la **cuenta de Holly Dickson**.

4. En el **Centro de administración Microsoft Entra**, selecciona **Protección** en el panel de navegación y, a continuación, selecciona **Acceso condicional**.

5. En la página **Acceso condicional | Información general**, selecciona **Directivas** en el panel de navegación central.

6. En la página **Acceso condicional | Directivas**, en la barra de menús de la parte superior de la página, selecciona **+Crear nueva directiva**.

7. En la ventana **Nueva directiva de acceso condicional**, escribe **MFA para todos los usuarios de Microsoft 365** en el campo **Nombre**.

8. Comenzarás definiendo los requisitos de MFA para los usuarios. En el grupo **Usuarios**, selecciona **0 usuarios y grupos seleccionados**. Al hacerlo, se mostrarán dos pestañas: **Incluir** y **Excluir**.

9. En la pestaña **Incluir**, selecciona **Todos los usuarios**. Observa el mensaje de advertencia que aparece. Se abordará esto en los dos pasos siguientes.

10. Selecciona la pestaña **Excluir**. Para evitar el bloqueo del sistema, tal y como se indicaba en el mensaje de advertencia anterior, tendrás que excluir a los administradores globales (en este caso, Holly). Holly también desea excluir a los demás miembros del grupo del proyecto piloto de Microsoft 365 para realizar pruebas. Una vez que la instancia de Microsoft 365 esté activa en Adatum, Holly quitará el grupo del proyecto piloto de la lista Excluir de esta directiva de acceso condicional y, simplemente, se excluirá a sí misma, al administrador MOD y a algunos otros administradores globales. Pero por ahora, Holly quiere excluir todo el grupo del proyecto piloto. <br/>

    Para ello, activa la casilla **Usuarios y grupos**. 

11. En la ventana **Seleccionar usuarios y grupos excluidos** que aparece, selecciona el grupo del proyecto piloto de Microsoft 365. La pestaña **Todos** se muestra de forma predeterminada. Para encontrar rápidamente el grupo del proyecto piloto, selecciona la pestaña **Grupos**. En la lista de grupos activos, activa la casilla situada junto al grupo **Proyecto piloto de M365** y luego selecciona el botón **Seleccionar** de la parte inferior de la ventana. De nuevo en la ventana **Nueva directiva de acceso condicional**, observa el mensaje que aparece en la sección **Usuarios**. 

12. Ahora definirás el requisito de MFA para todas las aplicaciones en la nube. En la sección **Recursos de destino**, selecciona **No hay recursos de destino seleccionados**. Al hacerlo, se mostrarán dos pestañas: **Incluir** y **Excluir**.

13. Selecciona el campo desplegable **Seleccionar a qué se aplica esta directiva** para ver las distintas opciones en el menú desplegable. Selecciona **Recursos (anteriormente aplicaciones en la nube)** . 

14. En la pestaña **Incluir**, observa que la configuración predeterminada sea **Ninguno**. Si no cambiaste esta configuración, ninguna aplicación en la nube requeriría MFA (y eso incluye a Microsoft 365). Por lo tanto, incluso si creaste esta directiva y seleccionaste la opción para requerir MFA para todos los usuarios, pero dejaste esta configuración de **Recursos de destino** en **Ninguno**, cualquier usuario que inicie sesión en Microsoft 365 no tendría que usar MFA. <br/>

    En la pestaña **Incluir**, selecciona la opción **Seleccionar recursos**. Al hacerlo, se muestran dos secciones: **Editar filtro** y **Seleccionar**. En la sección **Seleccionar**, selecciona **Ninguna**. 

15. En el panel **Seleccionar recursos** que aparece, desplázate hacia abajo por la lista de aplicaciones para ver todas las distintas aplicaciones para las que se podría requerir MFA. **NO seleccione ninguna de las aplicaciones.** Queremos que te desplaces por esta lista para que veas el grado de granularidad que obtienes al requerir MFA, si decides limitar MFA a determinadas aplicaciones en las implementaciones del mundo real.  <br/>

    Para Adatum, Holly desea requerir MFA para todas las aplicaciones en la nube, lo que normalmente es un escenario empresarial más común que seleccionar aplicaciones específicas. En la pestaña **Incluir**, selecciona **Todos los recursos (anteriormente "Todas las aplicaciones en la nube")** Adatum no excluirá ninguna aplicación en la nube de la autenticación MFA. Es posible seleccionar la pestaña **Excluir** si deseas ver las opciones que proporciona. Funciona básicamente de la misma forma que la pestaña **Incluir**. Es posible ver esta pestaña, pero NO selecciones ninguna aplicación en la nube para su exclusión. 

16. Por último, definirás el requisito de MFA para todas las ubicaciones de inicio de sesión de usuario. En algunos escenarios, las organizaciones podrían requerir MFA solamente si un usuario iniciase sesión desde una ubicación que no fuera de confianza. Sin embargo, Adatum quiere requerir MFA para todos los usuarios incluidos, independientemente de la ubicación desde la que inicien sesión. <br/>

    En **Condiciones**, selecciona **0 condiciones seleccionadas**. Al hacerlo, se mostrará una lista de posibles condiciones en las que se comprobará la directiva. Para este ejercicio de laboratorio, en la condición **Ubicaciones**, selecciona **Sin configurar**. Al hacerlo, se mostrará un botón de alternancia **Configurar** y dos pestañas: **Incluir** y **Excluir**. Ambas pestañas están deshabilitadas actualmente.

17. Establece el botón de alternancia **Configurar** en **Sí**, lo que habilitará las dos pestañas. 

18. En la pestaña **Incluir**, comprueba que se haya seleccionado **Cualquier red o ubicación** (selecciónalo si es necesario). Selecciona la pestaña **Excluir**. Si la organización reconociera direcciones IP específicas o intervalos de direcciones como "de confianza", será posible excluir el requisito de MFA cuando un usuario inicie sesión desde una de esas ubicaciones. Sin embargo, Adatum desea requerir MFA para todos los intentos de inicio de sesión del usuario, independientemente de su ubicación. Esto incluirá inicios de sesión de usuario internos y externos. Comprueba que la opción **Redes y ubicaciones seleccionadas** está seleccionada y, en la sección **Seleccionar**, comprueba que indica **Ninguno**. Al no especificar ninguna ubicación seleccionada, esta configuración garantizará que ninguna ubicación se excluya de MFA. 

19. En la sección **Controles de acceso**, en el grupo **Conceder**, selecciona **0 controles seleccionados**. Al hacerlo, se mostrará un panel **Conceder**.

20. En el panel **Conceder** que aparecerá, comprueba que la opción **Conceder acceso** esté seleccionada (selecciónala si fuera necesario). Observa todos los controles de acceso disponibles que se pueden habilitar con esta directiva. Esta directiva solo requerirá MFA, por lo que activa la casilla **Requerir autenticación multifactor**. Selecciona el botón **Seleccionar** situado en la parte inferior del panel **Conceder**, que cierra el panel. 

21. En la parte inferior de la ventana **Nueva directiva de acceso condicional**, en el campo **Habilitar directiva**, selecciona **Activar**.

22. Observa el mensaje de advertencia y las opciones que aparecen en la parte inferior de la página que le advierten de no autobloquearse. Selecciona la opción **Entiendo que mi cuenta se verá afectada por esta directiva. Continuar de todos modos.** De hecho, Holly no se verá afectada, ya que es miembro del grupo del proyecto piloto de M365 que se excluye de esta directiva.

23. Haz clic en el botón **Crear** para crear la directiva.

24. En la ventana **Acceso condicional | Directivas** que aparece, comprueba que la directiva **MFA para todos los usuarios de Microsoft 365** aparezca y que su **Estado** esté establecido en **Activado**.

25. Permanece conectado a LON-CL1 con todas las pestañas del explorador de Microsoft Edge abiertas para la siguiente tarea.


### Tarea 4: Prueba de MFA para un usuario incluido y uno excluido

Para probar la directiva de acceso condicional que acabas de crear, cerrarás la sesión de Microsoft 365 como Holly y, a continuación, volverás a iniciar sesión como Adele Vance. Adele no es miembro del grupo del proyecto piloto de M365, por lo que Microsoft Entra debería requerir que use MFA al iniciar sesión. Una vez que inicies sesión como Adele y comprueba que la MFA funciona, cerrarás la sesión como Adele y, a continuación, volverás a iniciar sesión como Holly. Dado que Holly es miembro del grupo del proyecto piloto de M365 que se excluyó del uso de MFA en la directiva de acceso condicional, no deberías tener que usar MFA al iniciar sesión como Holly. Del mismo modo, no tendrás que usar MFA al iniciar sesión como miembros del grupo del proyecto piloto de M365 en los laboratorios restantes de este curso.

**Importante:** para implementar la MFA, deberás usar el teléfono móvil para recibir un código de verificación y escribirlo en el inquilino como segunda forma de autenticación. Si no tuvieras teléfono, aún podrías probar la directiva de acceso condicional. Para los alumnos sin teléfono, al iniciar sesión como Adele Vance, el sistema te pedirá que inicies sesión con una segunda forma de autenticación. En ese momento, simplemente cancela el inicio de sesión y vuelve a iniciar sesión como Holly, lo que no requerirá MFA. Aunque no completarás el inicio de sesión de MFA para Adele, todavía puedes comprobar que el sistema te obliga a usarlo al intentar iniciar sesión como Adele.

1. En la máquina virtual LON-CL1, el **Centro de administración de Microsoft 365** aún debería estar abierto en el explorador Microsoft Edge desde la tarea anterior. Deberías tener la sesión iniciada en Microsoft 365 como **Holly Dickson**. Comenzarás por cerrar sesión en Microsoft 365. En la pestaña **Centro de administración de Microsoft 365**, selecciona el nombre de Holly en la esquina superior derecha del explorador. En la ventana **Holly Dickson** que aparece, selecciona **Cerrar sesión.** 
    
2. Una vez que hayas cerrado la sesión de Microsoft 365 como Holly, cierra la sesión del explorador para borrar la memoria caché. Entonces, selecciona el icono de **Edge** en la barra de tareas para abrir una nueva sesión del explorador. En el explorador, ve a la página **Inicio de Microsoft 365**. Para ello, escribe esta dirección URL en la barra de direcciones: **https://portal.office.com/** 

3. En la ventana **Elegir una cuenta** que aparece, selecciona **Usar otra cuenta**. 

4. En la ventana **Iniciar sesión**, escribe **AdeleV@xxxxxZZZZZZ.onmicrosoft.com** (donde xxxxxZZZZZZ es el prefijo de inquilino que proporcionó el proveedor de hospedaje de laboratorio) y luego selecciona **Siguiente**. En la ventana **Escribir contraseña**, escribe la **contraseña de usuario** proporcionada por el proveedor de hospedaje del laboratorio y selecciona **Iniciar sesión**.

5. Dado que MFA está habilitado para todos los usuarios, excepto para los miembros del grupo del proyecto piloto de M365 (del que Adele no es miembro), aparecerá una ventana **Se necesita más información**. Selecciona **Siguiente**. Esto hará regresar a la página **Microsoft Authenticator**, que es el punto de partida para iniciar sesión con MFA. <br/>

    **Importante:** si no tienes teléfono, hasta aquí has llegado para intentar iniciar sesión como Adele. Aunque no sea posible completar el inicio de sesión, comprobaste que la primera parte de la directiva de acceso condicional funciona, ya que requiere que Adele inicie sesión con MFA. En este punto, ve al paso 18 para que puedas volver a iniciar sesión como Holly.

6. En la página **Microsoft Authenticator** que aparece, descarga esta aplicación móvil o usa un método diferente para la comprobación de MFA. Para los fines de este laboratorio, se recomienda usar el teléfono móvil para no dedicar tiempo a instalar la aplicación Microsoft Authenticator, que quizá no vuelvas a usar después de esta clase de aprendizaje. Selecciona la opción **Quiero configurar otro método** en la parte inferior de la página (**Importante:** NO confundas este vínculo con el de **Quiero usar otra aplicación de autenticación** que aparece encima). 

7. En el cuadro de diálogo **Elegir otro método** que aparece, selecciona la flecha desplegable del campo **¿Qué método quisiera usar?**, selecciona **Teléfono** y, a continuación, elige **Confirmar**. 

8. En la ventana **Teléfono** que aparece, en el campo **¿Qué número de teléfono quieres usar?**, selecciona el país o región y, después, en el campo que hay al lado, escribe el número de teléfono (con el formato específico del país o región). Comprueba que la opción **Recibir un código** esté seleccionada y, a continuación, selecciona **Siguiente**.

9. Recupera el código de verificación del mensaje de texto que se envía al teléfono.

10. En la ventana **Teléfono**, escribe el código de verificación de 6 dígitos en el campo de código y, a continuación, selecciona **Siguiente**. Cuando la ventana **Teléfono** muestre un mensaje indicando que el teléfono se registró correctamente, selecciona **Siguiente**.

11. En la página **Se realizó correctamente**, selecciona **Listo**.

12. Microsoft ha implementado una nueva directiva de seguridad en los inquilinos de prueba que se usan en sus laboratorios de aprendizaje. Todas las cuentas de usuario de prueba predefinidas están configuradas para que los alumnos deban cambiar su contraseña inicial en el siguiente inicio de sesión. Ahora debes hacerlo con Adele. <br>

    En la ventana **Actualizar contraseña** que aparece, escribe la **Contraseña de usuario** que te proporciona el proveedor de hospedaje del laboratorio en el campo **Contraseña actual**. A continuación, en los campos **Nueva contraseña** y **Confirmar contraseña**, escribe la nueva contraseña de usuario que definiste para todos los usuarios de prueba al principio del laboratorio. Selecciona **Iniciar sesión**.

13. Si un cuadro de diálogo **¿Mantener la sesión iniciada?** apareciera, activa la casilla **No volver a mostrar** y, a continuación, activa **Sí.** 

14. Si aparece un cuadro de diálogo **Le damos la bienvenida a Microsoft 365**, selecciona la flecha derecha dos veces y, a continuación, selecciona la marca de verificación.

15. Si aparece una ventana **Crear con Microsoft 365**, selecciona la **X** para cerrarla.

16. En la página **Le damos la bienvenida a Microsoft 365**, selecciona el icono del **Iniciador de aplicaciones** y, a continuación, selecciona **Word**. Esto abre **Microsoft Word Online**. Al hacerlo, se validará que pueda acceder a aplicaciones de Microsoft 365 después de iniciar sesión con MFA.  <br/>

    **Importante:** Ya comprobó que la primera parte de la directiva de acceso condicional que creó funciona. La directiva requiere que un usuario que no sea miembro del equipo de proyectos piloto de Microsoft 365 debe iniciar sesión con MFA. Comprobó que esto funciona cuando inició sesión como Adele. Ahora cerrará sesión como Adele e iniciará sesión como Holly, durante lo cual comprobará que la segunda parte de la directiva de acceso condicional también funciona. NO debería tener que usar MFA al iniciar sesión como Holly, ya que es miembro del grupo del proyecto piloto de M365, que se excluye del requisito de MFA en la directiva de acceso condicional.

17. En la pestaña **Centro de administración de Microsoft 365**, seleccione el icono de la cuenta de Adele en la esquina superior derecha del explorador. En la ventana **Adele Vance** que aparece, clique **Cerrar sesión.** <br/>
    
18. Cierre la sesión del explorador para borrar la memoria caché. Seleccione el icono de **Edge** en la barra de tareas para abrir una nueva sesión del explorador. En el explorador, vaya a la página **Inicio de Microsoft 365**. Para ello, escriba esta dirección URL en la barra de direcciones: **https://portal.office.com/** 

19. En la ventana **Elegir una cuenta**, seleccione **Holly@xxxxxZZZZZZ.onmicrosoft.com** (donde xxxxxZZZZZZ es el prefijo del inquilino proporcionado por el proveedor de hospedaje del laboratorio) y, a continuación, seleccione **Siguiente**. En la ventana **Escribir contraseña**, escriba la nueva contraseña administrativa que definió para todos los usuarios de prueba al principio del laboratorio y, más adelante, asignó a la cuenta de Holly. Selecciona **Iniciar sesión**.

20. Dado que se requiere MFA para todos los usuarios, excepto para los miembros del equipo de proyectos piloto de M365 (de los cuales, Holly es miembro), no se necesitará MFA. Puesto que no se requiere MFA, el sistema muestra la página **Inicio de Microsoft 365** en la pestaña **Inicio | Microsoft 365**. 

21. Si aparece un cuadro de diálogo **Le damos la bienvenida a Microsoft 365**, selecciona la flecha derecha dos veces y, a continuación, selecciona la marca de verificación.

22. Si aparece una ventana **Crear con Microsoft 365**, selecciona la **X** para cerrarla.

23. En la página **Le damos la bienvenida a Microsoft 365**, selecciona el icono **Administrador** del panel lateral para ir al **Centro de administración de Microsoft 365**. <br/>

    **Importante:** ya comprobaste que la segunda parte de la directiva de acceso condicional que creaste funciona. La directiva excluye a los miembros del grupo del proyecto piloto de Microsoft 365 de iniciar sesión con MFA. Holly es miembro de este grupo y no tuvo que iniciar sesión con MFA.

24. Permanece conectado a LON-CL1 con el **Centro de administración de Microsoft 365** abierto en el explorador.


### Tarea 5: Implementación de Smart Lockout de Microsoft Entra

El director de tecnología de Adatum te pidió que implementes Smart Lockout de Microsoft Entra, que ayuda a bloquear a los actores malintencionados que intenten adivinar las contraseñas de los usuarios o usar métodos de fuerza bruta para ser admitidos en la red. Smart Lockout puede reconocer los inicios de sesión que procedan de usuarios válidos y tratarlos de forma distinta a los que provengan de atacantes y otros orígenes desconocidos. 

El director de tecnología está ansioso por implementar Smart Lockout porque bloqueará a los atacantes y permitirá al mismo tiempo que los usuarios de Adatum sigan accediendo a sus cuentas y sean productivos. El director de tecnología pidió a Holly que configure Smart Lockout para que los usuarios no puedan usar la misma contraseña más de una vez y no puedan usar contraseñas que se consideren demasiado sencillas o comunes. 

**Nota:** es posible mantener la configuración de la directiva de bloqueo de cuenta en el Editor de administración de directivas de grupo y en Microsoft Entra a través de su característica Smart Lockout. Esta tarea de laboratorio muestra cómo acceder a cada método, aunque solo actualizarás la configuración de Smart Lockout en Microsoft Entra. Es necesario usar el controlador de dominio de la empresa (LON-DC1) para acceder al Editor de administración de directivas de grupo. 

1. En LON-DC1, selecciona el icono de **Administrador del servidor** en la barra de tareas si ya está abierto; de lo contrario, ábrelo ahora.

2. En **Administrador del servidor**, selecciona **Herramientas** en la barra de menús superior derecha y, en el menú desplegable, selecciona **Administración de directivas de grupo.**

3. Maximiza la ventana **Administración de directivas de grupo**.

4. Deseas editar la directiva de grupo que incluye la directiva de bloqueo de cuentas de la organización. Si fuera necesario, en el árbol de consola raíz del panel lateral, expande **Forest:Adatum.com**, expande **Dominios** y, a continuación, expande **Adatum.com**.  <br/>

    ‎En **Adatum.com**, haz clic con el botón derecho en **Directiva de dominio predeterminada** y, a continuación, selecciona **Editar** en el menú.

5. Maximiza la ventana **Editor de administración de directivas de grupo** que aparece.

6. En el árbol **Directiva de dominio predeterminada** del panel lateral, en **Configuración del equipo**, expande **Directivas**, expande **Configuración de Windows**, expande **Configuración de seguridad** y, a continuación, expande **Directivas de cuenta.**

7. En la carpeta **Directivas de cuenta**, selecciona **Directiva de bloqueo de cuenta**.

8. Como puede ver en el panel central, no se ha definido ninguno de los parámetros de Smart Lockout. En lugar de mantener estos parámetros de bloqueo en el Editor de administración de directivas de grupo, en su lugar usarás el Centro de administración Microsoft Entra. Aunque es posible usar el Editor de administración de directivas de grupo, este método se usa normalmente en entornos de Active Directory local. Te mostramos este editor para que pudieras ver esta alternativa. Sin embargo, para las organizaciones que usen estrictamente servicios basados en la nube, como Microsoft 365, o que encuentren el uso del Centro de administración Microsoft Entra mucho más sencillo que acceder al Editor de administración de directivas de grupo, es preferible usar el **Centro de administración Microsoft Entra** para asignar los valores correspondientes en el contexto de Entra ID. <br/>  

    Ten en cuenta también que el comportamiento de bloqueo y las opciones de personalización difieren entre los dos métodos. Con el Editor de administración de directivas de grupo, se tiene un control más granular sobre la configuración de directivas, incluyendo el umbral de bloqueo de cuentas, la duración del bloqueo y el restablecimiento del contador de bloqueo de cuentas después. Sin embargo, el uso de este método requiere conocimientos sobre directivas de grupo y la administración de Active Directory. Por el contrario, la directiva de bloqueo de cuentas de Microsoft Entra no se puede personalizar tan extensamente. Sin embargo, es más fácil de usar, aunque carece de algunas de las opciones de ajuste disponibles en la directiva de grupo. <br/>

    Para Adatum, Holly eligió usar el Centro de administración Microsoft Entra para configurar la directiva de bloqueo de cuentas de la empresa. En la barra de tareas de la parte inferior de la pantalla, selecciona el icono de **Microsoft Edge**, que debe mostrar el **Centro de administración Microsoft Entra**. 

9. En el **Centro de administración Microsoft Entra**, selecciona **Protección** en el panel de navegación y, a continuación, selecciona **Métodos de autenticación**. 

10. En la página **Métodos de autenticación | Directivas**, en el panel central, en la sección **Administrar**, selecciona **Protección de contraseñas.**

11. En la ventana **Métodos de autenticación | Protección de contraseñas**, en el panel de detalles de la derecha, escribe la siguiente información:

    - En la sección **Smart Lockout personalizado**:

        - **Umbral de bloqueo:** este campo indica el número de inicios de sesión con error permitidos en una cuenta antes de su primer bloqueo. El valor predeterminado es 10. Con fines de prueba, Adatum ha solicitado que establezcas esto en **3**.

        - **Duración del bloqueo en segundos:** esta es la duración en segundos de cada bloqueo. El valor predeterminado es 60 segundos (un minuto). Adatum ha solicitado que cambie esto a **90** segundos.

    - En la sección **Contraseñas prohibidas personalizadas**:

        - **Exigir lista personalizada**: selecciona **Sí**

        - **Lista de contraseñas prohibidas personalizadas:** Escribe los valores siguientes (presiona Entrar después de escribir cada valor para que cada valor esté en una línea independiente):

            - **Password01**

            - **F00tball01**

            - **Se@Hawks1**

            - **Never4get!!**

    - En la sección **Modo**, selecciona **Aplicado**

12. En la barra de menús de la parte superior de la página, selecciona **Guardar**.

13. Ahora deberías probar la funcionalidad de contraseña prohibida. Selecciona el icono de usuario de Holly Dickson de la esquina superior derecha de la pantalla y, en el menú que aparece, selecciona **Ver cuenta**. 

14. En la ventana **Mi cuenta** que aparece, en el icono **Contraseña**, selecciona **CAMBIAR CONTRASEÑA**.

15. Se abrirá una nueva pestaña en la que se mostrará la ventana **Cambiar contraseña**. En el campo **Contraseña antigua**, escribe la contraseña existente de Holly, que es la nueva contraseña administrativa. <br/>

    Escribe **Never4get!!** en los campos **Crear nueva contraseña** y **Confirmar nueva contraseña** y, a continuación, selecciona **Enviar**. Observa el mensaje de error que recibas.

16. En el explorador, cierra la pestaña **Cambiar contraseña**. 

17. Ahora probarás la funcionalidad del umbral de bloqueo. Lo hará con la cuenta de Laura Atkin, que creaste en un ejercicio de laboratorio anterior. Selecciona el icono de usuario de Holly Dickson de la esquina superior derecha de la pantalla y, en el menú que aparece, selecciona **Cerrar sesión**.  

18. Una vez que hayas cerrado la sesión como Holly, aparecerá la ventana **Selección de la cuenta** en la pestaña **Inicio de sesión en Microsoft Entra**. Como procedimiento recomendado al cerrar sesión de un servicio en línea de Microsoft como un usuario y volver a iniciar sesión como otro, cierra todas las pestañas del explorador, excepto **Cerrar sesión** o **Iniciar sesión**. En este caso, cierra las demás pestañas ahora y deja abierta la pestaña **Iniciar sesión**.  <br/>

    En la ventana **Elegir una cuenta**, selecciona **Usar otra cuenta**. 

19. En la ventana **Iniciar sesión**, escribe **laura@xxxxxZZZZZZ.onmicrosoft.com** (donde xxxxxZZZZZZ es el prefijo de inquilino que te asignó el proveedor de hospedaje de laboratorio) y luego selecciona **Siguiente**. 

20. En la ventana **Escribir contraseña**, escribe cualquier combinación aleatoria de letras y números y, a continuación, selecciona **Iniciar sesión**. Observa el mensaje de error de contraseña no válida que aparece. 

    Repite este paso 2 veces más. 
    
    Como estableció el **Umbral de bloqueo** en **3**, deberías recibir un mensaje de error indicando que esta cuenta está bloqueada después del tercer intento erróneo de inicio de sesión. <br/>

    **Nota:** si no recibieras este mensaje de bloqueo después del tercer intento, el sistema aún no habrá terminado de propagar este cambio de umbral de bloqueo a lo largo del servicio. Es posible que el cambio tarde varios minutos en aplicarse. Espera unos minutos y vuelve a iniciar sesión con una contraseña ficticia. Las pruebas de este laboratorio mostraron resultados variables. El cambio a veces se propaga casi inmediatamente para que se produzca el bloqueo después del tercer intento de inicio de sesión. Otras veces pasaron entre 5 y 10 minutos antes de mostrar el mensaje de bloqueo. Continúa este proceso hasta recibir el mensaje de bloqueo, momento en el que la cuenta de Laura se bloqueará temporalmente para evitar el acceso no autorizado.

21. Se te impedirá iniciar sesión de nuevo como Laura hasta que pase la **duración del bloqueo de 90 segundos** que estableciste anteriormente. <br/>

    Una vez que se produzca el bloqueo, espera 90 segundos y vuelve a iniciar sesión como **laura@xxxxxZZZZZZ.onmicrosoft.com** (donde xxxxxZZZZZZ es el prefijo de inquilino que te ha asignado el proveedor de hospedaje del laboratorio). En el campo **Contraseña**, escribe la contraseña de Laura, que es la nueva contraseña de usuario que asignaste a la cuenta de Laura al crearla. 

22. Dado que MFA está habilitado para todos los usuarios, excepto para los miembros del grupo del proyecto piloto de M365 (del que Adele no es miembro), aparecerá una ventana **Se necesita más información** para que puedas completar el proceso MFA para Laura. Esta es la comprobación de que el intento de inicio de sesión con la contraseña real de Laura se realizó correctamente.  <br>

    **Nota:** NO es necesario completar el proceso MFA para Laura, ya que este es el último ejercicio de laboratorio mediante el controlador de dominio LON-DC1. Puedes cerrar todas las aplicaciones en LON-DC1.

# Continuar con el laboratorio 2: ejercicio 2
