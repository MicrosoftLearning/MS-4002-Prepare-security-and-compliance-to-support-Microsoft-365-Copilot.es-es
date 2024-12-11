# Ruta de aprendizaje 1 - Laboratorio 2 -Ejercicio 2: Administración de roles y grupos de roles

En este ejercicio, continuarás en tu rol como Holly Dickson, la nueva administradora de Microsoft 365 de Adatum. Como parte del proyecto piloto de Microsoft 365 de Adatum, administrarás la delegación de la administración asignando roles de administrador de Microsoft 365 a varias de las cuentas de usuario de Microsoft 365 creadas por el proveedor de hospedaje del laboratorio. Este ejercicio te proporcionará experiencia en el uso de tres métodos diferentes para asignar estos roles: 1) la asignación de un rol directamente a una cuenta de usuario en el Centro de administración de Microsoft 365, 2) la creación de un grupo de roles, la asignación de roles al grupo de roles y, a continuación, la asignación del grupo de roles a un usuario en el Centro de administración de Microsoft 365 y 3) la asignación de un rol a un usuario con Windows PowerShell. Una vez que hayas asignado roles de administrador de Microsoft 365 a varias de las cuentas de usuario existentes, deberás probar esas asignaciones comprobando que los usuarios tienen los permisos para actuar de acuerdo con sus roles.

### Tarea 1: Asignación de un rol de administrador en el Centro de administración de Microsoft 365

A Holly Dickson se le ha asignado el rol de administradora global de Microsoft 365. A medida que continúes en tu rol como Holly, usarás el Centro de administración de Microsoft 365 para asignar derechos de administrador a uno de los usuarios de Adatum. En esta tarea, asignarás el rol de administrador de facturación a la cuenta de usuario de Diego Siciliani.

1. En el ejercicio de laboratorio anterior, creaste un nuevo dominio para Adatum en LON-DC1. Ahora debes volver a **LON-CL1** para realizar las tareas administrativas de Microsoft 365 en este ejercicio de laboratorio. Como procedimiento recomendado, las tareas administrativas típicas de Microsoft 365 deben realizarse en un equipo cliente en lugar del controlador de dominio de la empresa.  <br/>

    Cambia a **LON-CL1**. 

2. En **LON-CL1**, en el **Centro de administración de Microsoft 365** en el explorador Edge, deberías tener la sesión iniciada como Holly Dickson de un ejercicio de laboratorio anterior. En el panel de navegación, selecciona **Usuarios** y, a continuación, selecciona **Usuarios activos**. 

3. En la lista **Usuarios activos**, selecciona **Diego Siciliani**.  <br/>

    **Nota:** selecciona el nombre de Diego; no actives la casilla situada a la izquierda de su nombre. La casilla se usa normalmente para seleccionar varios usuarios cuando quieras realizar una de las acciones relacionadas con el usuario en la barra de menús que aparece encima de la lista de usuarios, como **Administrar licencias de productos** y **Administrar roles**. Al seleccionar un nombre de usuario, se abre un panel de propiedades específico para ese usuario.

4. En el panel de **Diego Siciliani** que aparecerá, la pestaña **Cuenta** se mostrará de forma predeterminada. En esta pestaña, desplázate hacia abajo hasta la sección **Roles** y selecciona **Administrar roles**. 

5. En la ventana **Administración de roles de administrador**, la opción **Usuario (sin acceso al Centro de administración)** está seleccionada de forma predeterminada. Ahora que quieres asignar a Diego un rol Administrador, selecciona la opción **Acceso al Centro de administración**. Esto habilita una lista de roles de administrador usados habitualmente para la selección. 

6. Diego ha sido ascendido a Administrador de facturación, pero como este rol no aparece en la lista de roles más usados, desplázate hacia abajo y selecciona **Mostrar todo por categoría**. 

7. En la lista de roles ordenados por categoría, desplázate hacia abajo hasta la categoría **Otros**, activa la casilla **Administrador de facturación** y luego selecciona **Guardar cambios**. <br/>

    **Sugerencia:** tenga en cuenta el mensaje que aparece en la parte superior del panel una vez guardado el cambio del rol de administrador. Este mensaje proporciona el siguiente procedimiento recomendado que debes tener en cuenta a medida que mantiene roles administrativos en las implementaciones del mundo real: **Proporcione a los usuarios solo el acceso que necesitan asignándoles el rol menos permisivo.**

8. En la ventana **Administrar roles de administrador**, selecciona la **X** en la esquina superior derecha de la pantalla para cerrarla. Esto te devuelve a la lista **Usuarios activos**. 

9. Permanece conectado a LON-CL1 y al Centro de administración de Microsoft 365 como Holly Dickson.


### Tarea 2: Asignación de un rol de administrador mediante un grupo de roles en el Centro de administración de Microsoft 365

En la tarea anterior, asignaste un rol de administrador directamente a la cuenta de usuario de Diego Siciliani en el Centro de administración de Microsoft 365. En esta tarea, asignarás roles mediante un grupo de roles en su lugar. Crearás un grupo de roles de seguridad, le asignarás roles de administración de usuarios y, a continuación, asignarás el grupo de roles a la cuenta de usuario de Lynne Robbin en el Centro de administración de Microsoft 365.

1. En LON-CL1, deberías tener la sesión iniciada en el Centro de administración de Microsoft 365 como Holly Dickson. Si no es así, inicia sesión ahora.

2. En el **Centro de administración de Microsoft 365**, selecciona **Equipos y grupos** en el panel de navegación y, después, selecciona **Equipos y grupos activos**. 

3. En la página **Grupos y equipos activos**, la pestaña **Equipos y grupos de Microsoft 365** se muestra de forma predeterminada. Selecciona la pestaña **Grupos de seguridad**.

4. En la pestaña **Grupos de seguridad**, selecciona **+Agregar un grupo de seguridad** en la barra de menús. Al hacerlo, se inicia el asistente para **agregar un grupo de seguridad**.

5. En el asistente para **agregar un grupo de seguridad**, en la página **Configurar los conceptos básicos**, escribe **Grupo de roles de administración de usuarios** en el campo **Nombre**. Escribe **Este grupo de roles contiene roles de administración de usuarios** en el campo **Descripción**. Selecciona **Siguiente**.

6. En la página **Editar la configuración**, activa la casilla **Los roles de Azure AD se pueden asignar al grupo** y luego selecciona **Siguiente**.

7. En la página **Revisar y terminar de agregar grupo**, revisa la configuración. Si es necesario cambiar alguna configuración, selecciona la opción **Editar** adecuada y realiza el cambio. Cuando todas las opciones de configuración sean correctas, selecciona **Crear grupo**.

8. Una vez creado el **grupo de roles de administración de usuarios**, selecciona **Cerrar**.

9. Ahora que has creado el grupo de roles, debes asignarle los roles correspondientes. En la página **Grupos y equipos activos**, se muestra la pestaña **Grupos de seguridad**. Selecciona el **grupo de roles de administración de usuarios** para abrir su panel de detalles.

10. En el panel **Grupo de roles de administración de usuarios**, la pestaña **General** se muestra de forma predeterminada. En la sección **Roles**, selecciona **Administrar roles**.

11. En el panel **Administrar roles de administrador** que aparece, selecciona la opción **Acceder al Centro de administración**. En la lista de roles Administrador comunes que aparece directamente debajo de esta opción, activa las casillas **Administrador de usuarios** y **Administrador del éxito de la experiencia del usuario**. A continuación, selecciona la opción **Mostrar todo por categoría**. Desplázate hacia abajo hasta la categoría **Identidad**. Observa cómo ya está seleccionado el rol **Administrador de usuarios**, ya que lo seleccionaste anteriormente en la lista de roles usados habitualmente. En la categoría **Identidad**, selecciona el rol **Administrador del departamento de soporte técnico** y, a continuación, selecciona **Guardar cambios**. 

12. En el panel **Administrar roles de administrador**, los tres roles seleccionados deben aparecer en la opción **Acceder al Centro de administración**. Selecciona la **X** en la esquina superior derecha del panel para cerrarlo.

13. En la pestaña **Grupos de seguridad**, selecciona **Grupo de roles de administración de usuarios**. En el panel **Grupo de roles de administración de usuarios** que aparece, comprueba que los tres roles aparecen en la sección **Roles**. Cierra este panel.

14. Ahora que has asignado los roles al grupo de roles, debes asignar el grupo de roles a la cuenta de usuario de Lynne Robbin. En el **Centro de administración de Microsoft 365**, selecciona **Usuarios activos**.

15. En la página **Usuarios activos**, selecciona **Lynne Robbins**. 

16. En el panel de **Lynne Robbins** que aparecerá, la pestaña **Cuenta** se mostrará de forma predeterminada. En la tarea anterior, cuando asignaste el rol de administrador de facturación a la cuenta de Diego Siciliani, seleccionaste la opción **Administrar roles** en la sección **Roles**. Sin embargo, como asignarás las funciones de Lynne a través de un grupo de roles, debes asignar a Lynne como miembro del grupo de roles de seguridad que acabas de crear. A través de la asignación de grupos, Lynne heredará las funciones asignadas al grupo de roles. Por lo tanto, en la sección **Grupos**, selecciona **Administrar grupos**. 

17. En el panel **Administrar grupos**, selecciona **+Asignar pertenencias**.

18. En el panel **Asignar pertenencias**, activa la casilla **Grupo de roles de administración de usuarios** y selecciona **Agregar(1)**.

19. Una vez que aparezca una notificación de **Guardado** en la parte superior de la página, cierra este panel. 

20. Para comprobar que Lynne heredó los roles asignados al grupo de roles de administración de usuarios, selecciona **Lynne Robbins** en la lista de usuarios activos. 

21. En el panel **Lynne Robbins** que aparece, en la pestaña **Cuenta** que se muestra de forma predeterminada, deberías ver los tres roles de administración de usuarios asignados a Lynne. En la sección **Roles****, selecciona **Administrar roles**.

22. En el panel **Administrar roles de administrador** que aparece, en la opción **Acceder al Centro de administración**, ten en cuenta los tres roles seleccionados y el nombre del grupo desde el que se asignaron a Lynne. Observa también cómo se atenúan los tres roles. Esto indica que no se puede anular la selección de los roles de esta ventana. Dado que los roles se asignaron a Lynne desde un grupo de roles que contenía estos roles, solo puedes anular la asignación de los roles quitando a Lynne como miembro del grupo de roles. Acabas de comprobar que Lynne tiene asignados estos roles. Cierra el panel **Administrar roles de administrador**.

23. Permanece conectado a LON-CL1 y al Centro de administración de Microsoft 365 como Holly Dickson.

### Tarea 3: Asignación de un rol de administrador mediante Windows PowerShell  

En esta tarea, usarás Windows PowerShell para asignar un rol a una cuenta de usuario. Hacerlo te dará experiencia realizando esta función de administración en PowerShell, ya que algunos administradores prefieren realizar un mantenimiento de este tipo mediante PowerShell.

En esta tarea, Holly quiere asignar a Patti Fernández al rol de administrador de soporte técnico del servicio. Para agregar un usuario a un rol de administrador mediante el módulo de PowerShell de Microsoft Graph, primero debes obtener el id. de objeto del usuario y el id. de objeto del rol. En esta tarea, usarás Microsoft Graph para obtener los identificadores respectivos y, a continuación, crear la asignación de roles. 

PowerShell también te permite mostrar todos los usuarios asignados a un rol específico, lo que puede ser muy importante al auditar la implementación de Microsoft 365. En esta tarea, también aprenderás a usar PowerShell para mostrar todos los usuarios asignados a un rol específico.

1. En LON-CL1, selecciona el icono de Windows PowerShell en la barra de tareas que dejaste abierta en un laboratorio anterior. Si cerraste la ventana de PowerShell, abre una instancia con privilegios elevados con la misma instrucción que antes. 

2. En el ejercicio de laboratorio anterior, te conectaste a Microsoft Graph y solicitaste permisos "Directory.ReadWrite.All" para ejecutar los cmdlets que restauraron el grupo eliminado. Para actualizar los objetos Usuario y rol de esta tarea, Holly debe solicitar ahora permisos de lectura y escritura para cada objeto. Para solicitar estos permisos, escribe el siguiente comando en el símbolo del sistema y presiona Entrar:  <br/>

        Connect-MgGraph -Scopes 'User.ReadWrite.All', 'RoleManagement.ReadWrite.Directory'

3. En la ventana **Seleccionar una cuenta** que aparece, selecciona la cuenta de Holly Dickson.

4. En el cuadro de diálogo **Permisos solicitados** que aparece, activa la casilla **Consentimiento en nombre de la organización** y, a continuación, selecciona **Aceptar**.

5. Holly quiere asignar a **Patti Fernández** al rol **Administrador de soporte técnico del servicio**. Para asignar este rol mediante Microsoft Graph PowerShell, primero debes obtener el id. de objeto del rol de administrador de soporte técnico del servicio para poder asignárselo a Patti.

    **Importante:** antes de realizar este paso, comprueba que la ventana de PowerShell está en modo de pantalla completa. El nombre del rol aparece en la segunda columna de la salida. Si no estás en modo de pantalla completa, no verás el nombre del rol asociado a cada id. de objeto. 

6. Para asignar un rol en Microsoft Graph PowerShell, primero debes buscar su id. de objeto. Hay dos maneras en las que puedes ver las plantillas de rol: puedes mostrar toda la lista de plantillas de rol o puedes mostrar la plantilla para un rol específico. Como experiencia de aprendizaje, realizarás ambos métodos para que puedas ver la diferencia. <br/>

    Comencemos mostrando la lista completa de plantillas de rol junto con su id. de objeto y el nombre para mostrar. Para ello, escribe el siguiente comando y presiona Entrar: <br/>

        Get-MgDirectoryRoleTemplate | Sort DisplayName | Format-Table Id, DisplayName

    Como puedes ver después de ejecutar este comando, debes desplazarte por la lista de plantillas de rol que buscan el rol de administrador de soporte técnico del servicio. Puedes ver fácilmente lo tedioso que puede ser esto, incluso con la tabla ordenada. Como alternativa, ejecuta el siguiente comando para consultar una plantilla de rol específica; en este caso, la plantilla de rol "Administrador de soporte técnico del servicio": <br/>

        Get-MgDirectoryRoleTemplate | ? DisplayName -eq "Service Support Administrator" | Format-Table Id, DisplayName

    Después de ejecutar este comando, puedes ver que solo muestra la plantilla de rol solicitada. Obviamente, puede haber ocasiones en las que se muestre toda la lista de plantillas de rol. Pero cuando necesites buscar una sola plantilla de rol, la ejecución del segundo comando de PowerShell será mucho más eficaz que tener que desplazarse por toda la lista de plantillas.

7. Para asignar a Patti Fernández el rol de administrador de soporte técnico del servicio recién habilitado, primero debes obtener el id. de objeto de la cuenta de usuario de Patti. Para ello, escribe el siguiente comando y presiona Entrar:

        Get-MgUser -Filter "DisplayName eq 'Patti Fernandez'" | Format-Table ID, DisplayName

8. Ahora que conoces el id. de objeto del rol de administrador de soporte técnico del servicio habilitado recientemente y el id. de objeto de la cuenta de usuario de Patti, puedes asignarle el rol. Realiza los pasos siguientes para completar este proceso, reemplazando los dos identificadores de los valores mostrados en los dos pasos anteriores.

        New-MgRoleManagementDirectoryRoleAssignment -RoleDefinitionId 'paste in the role ID here' -PrincipalId 'paste in Pattis ID here' -DirectoryScopeId '/'

    **Nota:** el parámetro DirectoryScopeId indica que la asignación está en el nivel de inquilino o directorio.

9. Ahora quieres comprobar que se le ha asignado a Patti el rol de administrador de soporte técnico del servicio. Para ello, ejecutaremos dos comandos. El primero obtiene el rol asignado y lo almacena en una variable y el segundo muestra los identificadores de los usuarios asignados al rol.

        $assignedRole = Get-MgDirectoryRole -Filter "DisplayName eq 'Service Support Administrator'"
        Get-MgDirectoryRoleMember -DirectoryRoleId $assignedRole.Id

10. El comando anterior solo muestra los identificadores de los usuarios asignados al rol seleccionado. Sin embargo, puede coincidir con el identificador que se muestra con el id. de Patti para comprobar que a su cuenta se le ha asignado al rol **Administrador de soporte técnico del servicio**. Como puedes ver, Patti es el único usuario asignado al rol. 

11. Ahora repitamos este proceso para ver todos los usuarios asignados al rol de administrador global.

        $assignedRole = Get-MgDirectoryRole -Filter "DisplayName eq 'Global Administrator'"
        Get-MgDirectoryRoleMember -DirectoryRoleId $assignedRole.Id

12. Comprueba que hay varios usuarios de Adatum a los que se les ha asignado el rol de administrador global. En un escenario real, el administrador de Microsoft 365 usaría este comando de PowerShell para supervisar cuántos administradores globales existen en su implementación de Microsoft 365. A continuación, quitarían el rol de administrador global de los usuarios que realmente no deberían tenerlo (recuerda que la guía de procedimientos recomendados es tener entre 2 y 4 administradores globales en una implementación de Microsoft 365, en función del tamaño de la organización).  <br/>

    En el caso de este laboratorio, aunque tu proveedor de hospedaje de laboratorio haya asignado el rol de administrador global a usuarios distintos del Administrador de MOD (y tú se lo hayas asignado a Holly Dickson), dejarás a estos usuarios tal como están. En esta implementación ficticia de Adatum, no tiene sentido perder el tiempo eliminando este rol de sus cuentas. Además, algunas de las tareas futuras del laboratorio se basan en que a estos usuarios se les asigna el rol de administrador global. <br/>

    **IMPORTANTE:** recuerda que, en la implementación real, el administrador de Microsoft 365 debe supervisar el rol de administrador global de forma periódica para mantener el número de usuarios asignados entre 2 y 4.
    
13. Deja abierta la sesión de Windows PowerShell para futuros ejercicios de laboratorio, pero minimízala antes de continuar con la siguiente tarea.


### Tarea 4: Validación de asignaciones de roles 

En esta tarea, comenzarás examinando las propiedades administrativas de dos usuarios, Joni Sherman y Lynne Robbins. Después, iniciarás sesión en la página principal de Microsoft 365 en la máquina virtual cliente 2 (LON-CL2) como cada usuario para confirmar varios de los cambios realizados al administrar su delegación administrativa en las tareas anteriores. Por último, como Lynne Robbins, realizarás dos tareas importantes de mantenimiento de cuentas de usuario: restablecer contraseñas y bloquear cuentas de usuario.

1. En LON-CL1, deberías tener la sesión iniciada en el Centro de administración de Microsoft 365 como Holly Dickson. Si no es así, inicia sesión ahora.

2. En el **Centro de administración de Microsoft 365**, si no muestra los **Usuarios activos**, ve a esa página.  

3. En la lista **Usuarios activos**, selecciona **Joni Sherman**. 

4. En la ventana de propiedades de **Joni Sherman**, la pestaña **Cuenta** se muestra de manera predeterminada. En la sección **Roles**, debes indicar que Joni **no tiene acceso de administrador**. Selecciona la **X** en la esquina superior derecha para cerrar la ventana de propiedades de Joni.

5. En la lista **Usuarios activos**, selecciona **Lynne Robbins**. 

6. En la ventana de propiedades de **Lynne Robbins**, debes indicar que Lynne tiene asignado el rol **Administrador de usuarios**. Cierra la ventana Propiedades de Lynne.

7. Cambia a la máquina virtual cliente 2 (**LON-CL2**).

8. En **LON-CL2**, en la pantalla de inicio de sesión, iniciarás sesión como la cuenta local **LON-CL2/Admin** con la contraseña **Pa55w.rd**.

9. Si aparece la ventana **Redes**, selecciona **Sí**.

10. En la barra de tareas, selecciona el icono de **Microsoft Edge**. Maximiza la ventana del explorador Edge si es necesario.

11. En el explorador **Edge**, ve a **https://portal.office.com**. 

12. Comenzarás iniciando sesión en Microsoft 365 como **Joni Sherman**. En la ventana **Iniciar sesión**, escribe **JoniS@xxxxxZZZZZZ.onmicrosoft.com** (donde xxxxxZZZZZZ es el prefijo de inquilino proporcionado por el proveedor de hospedaje del laboratorio). Puesto que inicias sesión como Joni Sherman, escribe esta **Contraseña de usuario** que te proporciona el proveedor de hospedaje del laboratorio en la ventana **Escribir contraseña**. <br>

    En el cuadro de diálogo **Actualizar contraseña** que aparece, escribe la **Contraseña de usuario** que te proporciona el proveedor de hospedaje del laboratorio en el campo **Contraseña actual**. Después, escribe la Nueva contraseña de usuario en los campos **Contraseña nueva** y **Confirmar contraseña** y selecciona **Iniciar sesión**.

13. En la ventana **¿Mantener la sesión iniciada?**, activa la casilla **No volver a mostrar** y, a continuación, selecciona **Sí**. Si aparece la ventana **Guardar contraseña**, selecciona **Nunca**.

14. Si aparece el cuadro de diálogo **Bienvenido a Microsoft 365** en medio de la página, selecciona la flecha hacia delante (>) dos veces y, a continuación, la marca de verificación para cerrarla.

15. Si aparece una ventana **Buscar más aplicaciones**, **Crear con Microsoft 365** o cualquier otra de tipo introductorio, selecciona la **X** en la esquina superior de la ventana para cerrarla.

16. En la ventana **Bienvenido a Microsoft 365**, que es la página principal de Microsoft 365 de Joni, aparece un panel de navegación en el lateral de la pantalla que indica las aplicaciones a las que el usuario tiene permiso para acceder. En este panel **Aplicaciones**, observa que no se muestra la opción **Administrador**. Esto se debe a que Joni nunca tuvo un rol de administrador de Microsoft 365. 

17. Ahora cerrarás la sesión de Microsoft 365 como Joni. En **Microsoft Edge**, en la parte superior derecha de la página **Bienvenido a Microsoft 365**, selecciona el icono de usuario para **Joni Sherman** (el círculo en la esquina superior con la imagen de Joni) y, en la ventana **Joni Sherman** que aparece, selecciona **Cerrar sesión.** 

18. Ahora volverás a iniciar sesión en Microsoft 365 como **Lynne Robbins**. En la pestaña actual del explorador **Edge**, debe mostrar un mensaje que indica **Joni, se ha cerrado la sesión**. En esta ventana, se te ofrece la opción de volver a iniciar sesión como Joni o iniciar sesión como un usuario diferente. <br/>

    Selecciona **Cambiar a otra cuenta** y, en el campo **Dirección de correo electrónico** que aparece, escribe **LynneR@xxxxxZZZZZZ.onmicrosoft.com** (donde xxxxxZZZZZZ es el prefijo de inquilino proporcionado por el proveedor de hospedaje de laboratorio) y, a continuación, selecciona **Iniciar sesión**. En la ventana **Escribir contraseña**, escribe la **contraseña de usuario** proporcionada por el proveedor de hospedaje del laboratorio y selecciona **Iniciar sesión**. <br>

    En el cuadro de diálogo **Actualizar contraseña** que aparece, escribe la **Contraseña de usuario** que te proporciona el proveedor de hospedaje del laboratorio en el campo **Contraseña actual**. Después, escribe la Nueva contraseña de usuario en los campos **Contraseña nueva** y **Confirmar contraseña** y selecciona **Iniciar sesión**. 

19. Si aparece el cuadro de diálogo **Bienvenido a Microsoft 365**, selecciona la flecha hacia delante (>) dos veces y, a continuación, selecciona la marca de verificación para cerrar la ventana.

20. Si aparece una ventana **Buscar más aplicaciones**, **Crear con Microsoft 365** o cualquier otra de tipo introductorio, selecciona la **X** en la esquina superior de la ventana para cerrarla.

21. En la ventana **Bienvenido a Microsoft 365**, que es la página principal de Microsoft 365 de Lynne, observa que se muestra el icono **Administrador** en el panel de navegación del lateral de la pantalla. Este icono aparece porque a Lynne se le asignó a un rol Administrador de Microsoft 365. Selecciona el icono **Administrador** para abrir el Centro de administración de Microsoft 365.

22. En el **Centro de administración de Microsoft 365**, selecciona **Usuarios** en el panel de navegación y, después, selecciona **Usuarios activos**. 

23. Como **Administrador de usuarios**, Lynne tiene permiso para cambiar las contraseñas de usuario. Recientemente, **Diego Siciliani** y **Pradeep Gupta** se pusieron en contacto con Lynne e informaron de que sus contraseñas podrían haber sido puestas en peligro. Según la directiva de empresa de Adatum, Lynne debe restablecer sus contraseñas a un valor temporal y, a continuación, obligarles a restablecer su contraseña en su siguiente inicio de sesión.   <br/>

    En la lista **Usuarios activos**, a medida que mueves el mouse de una cuenta de usuario a otra, observa el icono de **llave (Restablecer una contraseña)** que aparece a la derecha del nombre de cada usuario. Selecciona el icono de llave que aparece a la derecha del nombre de **Diego Siciliani**.

24. En la ventana **Restablecer contraseña** de Diego, si la casilla **Crear automáticamente una contraseña** muestra una marca de verificación, marca esta casilla para desactivarla. Esto permitirá a Lynne asignarle manualmente a Diego una contraseña temporal.  

25. Escribe **diego** en el campo **Contraseña**. Observa que a la derecha de la contraseña, el sistema muestra un mensaje indicando que se trata de una contraseña **Débil**. Observa también el mensaje que aparece debajo del campo que indica los requisitos de una contraseña segura. Por último, observa que el botón **Restablecer contraseña**, situado en la parte inferior del panel, no está habilitado. **Este botón solo se habilitará una vez que escriba una contraseña segura**.  

26. Comprueba que la casilla **Requerir que este usuario cambie su contraseña cuando inicie sesión por primera vez** está activada (si no es así, selecciónala para que aparezca una marca de verificación). Escribe **Pa55w.rd** en el campo **Contraseña**. Observa que el campo **Contraseña** indica que se trata de una contraseña segura. <br/>

    Sin embargo, ahora selecciona la casilla **Requerir a este usuario que cambie la contraseña la primera vez que inicie sesión** para desactivarla. Tenga en cuenta el mensaje de error que aparece que indica la contraseña (Pa55w.rd) contiene una palabra, frase o serie de números que hace que sea fácil de adivinar. En este caso, escribió una variación de la palabra **password**, que desencadenará este error. El sistema le permite escribir esta contraseña si obliga al usuario a cambiarla en su primer inicio de sesión. Pero si no obliga al usuario a escribir una contraseña diferente en su primer inicio de sesión, no se permitirá esta contraseña.

27. Después de estos dos intentos de contraseña erróneos, Lynne ha decidido permitir que Microsoft 365 genere automáticamente una contraseña. Active la casilla **Crear automáticamente una contraseña** para que muestre una marca de verificación. 
    
28. La contraseña que se genera automáticamente será una contraseña temporal porque Lynne quiere forzar a Diego a cambiarla la próxima vez que inicie sesión. Por lo tanto, compruebe que la casilla **Requerir que este usuario cambie su contraseña cuando inicie sesión por primera vez** muestra una marca de verificación; si la casilla está desactivada, selecciónela para que muestre una marca de verificación.

29. Seleccione **Restablecer contraseña**.

30. Si se le pide que guarde la contraseña, seleccione **nunca** para cerrar la ventana.

31. Debería recibir un mensaje de error que indica que no se puede restablecer la contraseña de Diego porque se le ha asignado un rol Administrador. En el caso de Diego, le asignó el rol Administrador de facturación anteriormente en este ejercicio de laboratorio. Dado que solo los Administradores de empresa pueden cambiar la contraseña de otro administrador y, dado que Lynne no es Administrador de empresa, tendrá que pedir a Holly Dickson que realice este cambio. Seleccione **Cerrar** en el panel **Restablecer contraseña**. 

32. Si aparece una ventana de solicitud de encuesta, seleccione **Cancelar**.

33. Ahora quiere cambiar la contraseña de Pradeep Gupta. En la lista **Usuarios activos**, seleccione el icono de **llave (Restablecer una contraseña)** que aparece a la derecha de **Pradeep Gupta**. 

34. En la ventana **Restablecer contraseña** que aparece para Pradeep, compruebe que la casilla **Crear automáticamente una contraseña** muestra una marca de verificación; si no es así, seleccione esta casilla para que el sistema genere automáticamente una contraseña para Pradeep.  <br/>

    Esta es una contraseña temporal porque Lynne quiere obligar a Pradeep a cambiarla la próxima vez que inicie sesión. Por lo tanto, compruebe que la casilla **Requerir que este usuario cambie su contraseña cuando inicie sesión por primera vez** muestra una marca de verificación; si la casilla está desactivada, selecciónela para que muestre una marca de verificación.
    
35. Seleccione el botón **Restablecer contraseña**.

36. En la ventana **La contraseña se ha restablecido**, debería recibir un mensaje que indica que restableció correctamente la contraseña de Pradeep. Seleccione **Close** (Cerrar).

37. La administración ha descubierto recientemente que el nombre de usuario de Alex Wilber puede haber estado en peligro. En consecuencia, se le ha pedido a Lynne que bloquee la cuenta de Alex para que nadie pueda iniciar sesión con su nombre de usuario hasta que la administración pueda determinar la magnitud del problema. En la lista **Usuarios activos**, active la casilla situada a la izquierda del nombre de **Alex Wilber** (NO seleccione el nombre de Alex).  <br/>

    **Importante:** Puesto que va a ejecutar un comando global en lugar de un comando asociado a la cuenta de Alex, solo quiere que la cuenta esté seleccionada en la lista de usuarios activos. Si se selecciona cualquier otra cuenta de usuario, debe anular la selección de esa cuenta de usuario antes de continuar. Desplácese por la lista de usuarios activos y compruebe que no hay ninguna otra cuenta de usuario seleccionada. Si se selecciona una cuenta distinta de Alex, seleccione la casilla de verificación de la cuenta para desactivarla. **Solo debe seleccionarse la cuenta de Alex Wilber.**

38. En la barra de menús de la parte superior de la página, seleccione el icono de puntos suspensivos **(...)** para mostrar un menú desplegable de acciones adicionales. En el menú que aparece, seleccione **Editar estado de inicio de sesión**.

39. En el panel **Bloquear inicio de sesión** que aparece, compruebe que la dirección de correo electrónico de Alex aparece debajo del encabezado **Bloquear inicio de sesión**. Active la casilla **Impedir que este usuario inicie sesión** y, a continuación, seleccione **Guardar cambios.** 

40. La ventana **Bloquear inicio de sesión** debe mostrar un mensaje que indica que Alex está bloqueado para iniciar sesión (y nadie puede iniciar sesión con el nombre de usuario de Alex en caso de que su nombre de usuario esté realmente en peligro). Además, Alex se desconectará automáticamente de los servicios de Microsoft en 60 minutos. Seleccione el **X** en la esquina superior del panel para cerrarlo. 

41. Acaban de informar a Lynne de que el nombre de usuario de **Nestor Wilke** también ha sido puesto en peligro. Repita los pasos del 37 al 40 para impedir que Nestor inicie sesión (y para impedir que cualquier otra persona utilice su nombre de usuario para iniciar sesión). <br/>

    Cuando intentó bloquear el inicio de sesión de Nestor, debería haber recibido un mensaje de error que indica que **no se pudieron guardar los cambios**. La razón por la que recibió este error es que Nestor es un Administrador global y Lynne no. Solo un Administrador global puede impedir que otro Administrador global pueda iniciar sesión. Lynne tendrá que pedirle a Holly Dickson que haga este cambio. <br/>

    Cierre el panel **Bloquear inicio de sesión**.

42. Anteriormente, bloqueó a Alex Wilber para que no pudiera iniciar sesión. Para comprobar si está bloqueado, intentará iniciar sesión como Alex. Cierre sesión en Microsoft 365 seleccionando el icono de usuario de **Lynne Robbins** (el círculo con la imagen de Lynne en la esquina superior) y en la ventana **Lynne Robbins** que aparece, seleccione **Cerrar sesión.** 

43. Como procedimiento recomendado, cierre todas las pestañas del explorador, excepto la pestaña **Cerrar sesión** una vez que se haya cerrado la sesión. En la pestaña **Cerrar sesión**, vaya a **https://portal.office.com**. 

44. En la ventana **Elegir una cuenta**, seleccione **Usar otra cuenta**. En la ventana **Iniciar sesión**, escriba **AlexW@xxxxxZZZZZZ.onmicrosoft.com** (donde xxxxxZZZZZZ es el prefijo de inquilino proporcionado por el proveedor de hospedaje del laboratorio). En la ventana **Escribir contraseña**, escriba la **contraseña de usuario** proporcionada por el proveedor de hospedaje del laboratorio.  <br/>

    Debería aparecer la ventana **Seleccionar una cuenta** y debería mostrar el siguiente mensaje de error: **Se ha bloqueado la cuenta. Contacte con la persona responsable de soporte técnico para desbloquearla y vuelva a intentarlo.** Acaba de comprobar que Alex (o alguien que ha obtenido el nombre de usuario y la contraseña de Alex) no puede iniciar sesión. <br/>

    **Nota:** El bloqueo de cuenta puede tardar unos minutos en implementarse por completo. Hasta que el bloqueo se haya implementado en el sistema, es posible que Alex pueda iniciar sesión, pero ninguno de los servicios de Microsoft 365 estará disponible y no aparecerá en el portal de Microsoft 365. Una vez desbloqueada la cuenta, los servicios volverán a estar disponibles. <br/>

    Si puede iniciar sesión como Alex, cierre la sesión y espere unos minutos. Esto puede ser un buen momento para tomar un breve descanso. A continuación, intente volver a iniciar sesión como Alex. En este momento, debería recibir el mensaje de error que indica que la cuenta de Alex se ha bloqueado para iniciar sesión. 
    
45. Vuelva a **LON-CL1**. 

46. En **LON-CL1**, debería seguir conectado a **Microsoft 365** como Holly Dickson en su explorador Edge. La lista **Usuarios activos** debe mostrarse en el **Centro de administración de Microsoft 365** desde el inicio de esta tarea. 

47. Tras una investigación adicional, el director de tecnología de Adatum ha determinado que la cuenta de Alex Wilber no se ha puesto en peligro; por lo tanto, le ha pedido a Holly que quite el bloqueo de la cuenta de usuario de Alex. Repita los pasos del 37 al 40 para desbloquear su cuenta. Observe cómo la ventana **Bloquear inicio de sesión** del paso 39 muestra ahora la ventana **Desbloquear inicio de sesión**.  <br/>

    En la ventana **Desbloquear el inicio de sesión**, la casilla **Bloquear el inicio de sesión de este usuario** está seleccionada. Seleccione la casilla para desactivarla y, a continuación, seleccione **Guardar cambios**. <br/>
    
    **IMPORTANTE:** Aparecerá un mensaje de advertencia indicando que pueden pasar hasta 15 minutos antes de que Alex pueda iniciar sesión de nuevo. Dadas las limitaciones de tiempo con la formación, **NO** intentará comprobar si Alex puede volver a iniciar sesión. Si lo desea, puede intentar iniciar sesión como Alex en un momento posterior si está en un descanso o tiene tiempo libre y desea probarlo. Por ahora, permanezca en LON-CL1 y simplemente cierre la ventana **Desbloquear inicio de sesión**.
    
48. En LON-CL1, deje abierto el explorador y todas las pestañas y continúe con el siguiente ejercicio.
    

# Fin del laboratorio 2

