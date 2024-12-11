# Ruta de aprendizaje 1 - Laboratorio 3 - Ejercicio 2: Prueba de la directiva DLP

Holly Dickson está ahora en el momento de su proyecto piloto donde quiere probar la directiva DLP relacionada con los correos electrónicos que contienen información confidencial que creaste en el ejercicio de laboratorio anterior. 

**NOTA:** hemos experimentado problemas intermitentes en el pasado en los que las directivas DLP y las sugerencias de directiva no funcionan según lo previsto en este ejercicio de laboratorio. Esto se debe a problemas de limitación que a veces se producen entre nuestro entorno de laboratorio de máquinas virtuales y el inquilino de prueba de Microsoft 365. Esto no indica la experiencia normal en entornos de producción de Microsoft 365. Tampoco es indicativo de la experiencia de aprendizaje normal. Nos disculpamos si te encuentras con este problema durante este ejercicio de laboratorio.

### Tarea 1: Prueba de la primera regla de directiva DLP

En el ejercicio anterior, creaste una directiva DLP personalizada que busca mensajes de correo electrónico que contienen información confidencial relacionada con las direcciones IP del inquilino de Adatum. Esta directiva incluía dos reglas: una que comprueba si hay correos electrónicos que contienen una sola dirección IP y otra que comprueba si hay correos electrónicos que contienen dos o más direcciones IP. 

En esta tarea, enviarás un correo electrónico de Holly Dickson a Lynne Robbins que prueba la primera regla (dirección IP única). Cuando se desencadena esta regla, se muestra una sugerencia de directiva de correo electrónico en el buzón de Outlook del remitente que le informa que el correo electrónico contiene datos confidenciales. El remitente también recibirá una notificación por correo electrónico, pero el correo electrónico se enviará al destinatario.

1. En LON-CL1, en el explorador Edge, todavía deberías tener la sesión iniciada en Microsoft 365 como **Holly Dickson**. 

2. Ahora enviarás un correo electrónico de Holly a Lynne Robbins e incluirás una dirección IP en el cuerpo del correo electrónico. <br/>

    En **Microsoft Edge**, selecciona la pestaña **Inicio | Pestaña Microsoft 365** y, a continuación, selecciona el icono de **Outlook** en la columna de iconos de la aplicación en el lado izquierdo de la pantalla. Cuando se abra Outlook en la Web, deberías iniciar sesión automáticamente como Holly Dickson.  <br/>

    **Nota:** si **Outlook en la Web** ya estaba abierto, comprueba que has iniciado sesión como **Holly** comprobando el icono de usuario en la esquina superior derecha (el círculo **HD**). Si Outlook estaba abierto para cualquier otro usuario, cierra la pestaña y repite las instrucciones de este paso para abrir Outlook en la Web para Holly.

3. En la esquina superior izquierda de la pantalla, selecciona **Correo nuevo**. 

4. En el panel de mensajes que aparece a la derecha de la pantalla, escribe la siguiente información:

    - Para: escribe **Lynne** y selecciona **Lynne Robbins** en la lista de usuarios que aparece.

    - Agregar un asunto: **Prueba de directiva DLP 1**

    - Área de mensaje: **Hola Lynne - Configuraré esta dirección IP: 192.168.0.1**

    **Nota:** la redacción de este correo electrónico con datos confidenciales (en este caso, una dirección IP), desencadenará la directiva de direcciones IP que creaste anteriormente y, en concreto, la regla de dirección IP única. Por lo tanto, se debe mostrar una **sugerencia de directiva** que indique que el mensaje de correo electrónico infringe una directiva organizativa. Omitirás esta sugerencia de directiva y enviarás el correo electrónico de todos modos para probar el resto de la directiva DLP, que enviará un correo electrónico de notificación a Holly.

5. Una vez que se muestre la sugerencia de directiva, selecciona **Enviar.**

6. Selecciona la carpeta **Elementos enviados** de Holly para comprobar que se envió el correo electrónico.

7. Selecciona la carpeta **Bandeja de entrada** de Holly. Holly debe recibir un correo electrónico de **Microsoft Outlook** con el asunto: Notificación: **Prueba de directiva DLP 1**. Selecciona este correo electrónico y revisa su contenido. 

8. Cambia a **LON-CL2**. 

9. Si necesitas iniciar sesión en la máquina virtual, la cuenta **LON-CL2\admin** local debería aparecer de forma predeterminada. Por tanto, escribe **Pa55w.rd** en el campo **Contraseña** para iniciar sesión. 

10. En la barra de tareas, selecciona el icono del explorador **Edge**.

11. En el explorador Edge, escribe la siguiente dirección URL: **https://outlook.office365.com**

12. En la ventana **Elegir una cuenta**, selecciona la cuenta de Lynne Robbins (**LynneR@xxxxxZZZZZZ.onmicrosoft.com**, donde xxxxxZZZZZZ es el prefijo del inquilino proporcionado por el proveedor de hospedaje del laboratorio). En la ventana **Escribir contraseña**, escribe la nueva contraseña de usuario que asignaste a la cuenta de Lynne y, a continuación, selecciona **Iniciar sesión**. 

13. En la ventana **¿Mantener la sesión iniciada?**, activa la casilla **No volver a mostrar** y, a continuación, selecciona **Sí**.

14. En la Bandeja de entrada de Lynne, comprueba que recibió el correo electrónico de Holly Dickson que tiene la línea de asunto: **Prueba de directiva DLP 1**. Selecciona el mensaje para comprobar que no se quitó el contenido que contiene la dirección IP. 

15. Deja abierta la pestaña Outlook en el explorador Edge para la siguiente tarea.

16. Vuelve a **LON-CL1**.

    
### Tarea 2: Prueba la segunda regla de directiva DLP

En el ejercicio anterior, creaste una directiva DLP personalizada que busca mensajes de correo electrónico que contienen información confidencial relacionada con las direcciones IP del inquilino de Adatum. Esta directiva incluía dos reglas: una que comprueba si hay correos electrónicos que contienen una sola dirección IP y otra que comprueba si hay correos electrónicos que contienen dos o más direcciones IP. 
    
En esta tarea, enviarás un correo electrónico de Holly Dickson a Lynne Robbins que pruebe la segunda regla (varias direcciones IP). Cuando se desencadena esta regla, se muestra una sugerencia de directiva de correo electrónico en el buzón de Outlook del remitente que le informa que el correo electrónico contiene datos confidenciales. El correo electrónico se bloqueará, pero el remitente puede invalidar el correo electrónico bloqueado y permitir que se envíe.  

1. En LON-CL1, en el explorador Edge, todavía deberías estar conectado en Microsoft 365 como **Holly Dickson**. 
    
2. Ahora enviará un segundo mensaje de Holly a Lynne que contiene varias direcciones IP. Repite el proceso como antes para crear un correo electrónico a Lynne Robbins con la siguiente información: 

    - Agregar un asunto: **Prueba de directiva DLP 2**

    - Área de mensaje: **Hola Lynne - Probaré las siguientes direcciones IP: 192.168.0.1 y 172.16.0.1**

    **Nota:** La redacción de este correo electrónico con datos confidenciales (en este caso, varias direcciones IP), desencadenará la directiva de direcciones IP que creaste anteriormente y, en concreto, la regla de varias direcciones IP. Por lo tanto, se debe mostrar una **sugerencia de directiva** que indique que el mensaje de correo electrónico infringe una directiva organizativa. Omitirás esta sugerencia de directiva y enviarás el correo electrónico de todos modos para probar el resto de la directiva DLP, que bloqueará el correo electrónico. Una vez que pruebes el bloqueo de correo electrónico, invalidarás el bloqueo al escribir una justificación comercial para enviar esta información confidencial y luego intentarás volver a enviar el correo electrónico.

3. Una vez que se muestre la sugerencia de directiva, selecciona **Enviar**. Deberías recibir inmediatamente un cuadro de diálogo **Envío bloqueado** que indique que el mensaje incluye uno o varios destinatarios que no están autorizados para recibir información confidencial. Selecciona **Aceptar**. <br/>

    **Sugerencia:** normalmente, invalidarías el bloqueo antes de enviarlo, pero en este caso queríamos que experimentaras el bloqueo para ver cómo funciona. En los pasos siguientes, invalidarás el bloqueo e intentarás volver a enviar el correo electrónico.

4. Selecciona la carpeta **Elementos enviados** de Holly para comprobar que no se envió el correo electrónico.

5. Selecciona la carpeta **Bandeja de entrada** de Holly. Observa que el mensaje de correo electrónico ya no se muestra. Selecciona la carpeta **Borradores** de Holly, que contiene una copia del correo electrónico. Selecciona el correo electrónico.

6. Para enviar este correo electrónico, debes invalidar el bloqueo ANTES de seleccionar el botón **Enviar**. Para invalidar el bloqueo, en la sugerencia de directiva que aparece en la parte superior del mensaje, selecciona **Mostrar detalles**.

7. En el mensaje detallado que aparece en la sugerencia de directiva, selecciona **Invalidar**.

8. En el cuadro de diálogo que aparece, la opción **Tengo una justificación comercial** está seleccionada de forma predeterminada. Deje esta opción seleccionada y escribe **Se debe informar a Lynne sobre las direcciones IP que estoy probando** en el campo **Escribir explicación aquí**. Selecciona **Invalidar**. <br/>

    Observa cómo ha cambiado el mensaje de sugerencia de directiva para indicar que has elegido enviar el mensaje aunque parezca que contiene información confidencial.

9. Selecciona la carpeta **Elementos enviados** de Holly para comprobar que se envió el correo electrónico.

10. Selecciona la carpeta **Bandeja de entrada** de Holly. Holly debe recibir un correo electrónico de **Microsoft Outlook** con el asunto: **Notificación: Prueba de directiva DLP 2**. Selecciona este correo electrónico y revisa su contenido.
    
11. Cambia a **LON-CL2**. 

12. Todavía deberías tener la sesión iniciada en **Outlook en la Web** en la máquina virtual LON-CL2 como **Lynne Robbins**. En el explorador **Edge**, el buzón de Lynne debe estar abierto en **Outlook en la Web** desde el momento en que lo usaste por última vez en la tarea anterior.

13. En la Bandeja de entrada de Lynne, comprueba que recibió el correo electrónico de Holly Dickson que tiene la línea de asunto: **Prueba de directiva DLP 2**. Selecciona el mensaje para comprobar que no se quitó el contenido que contiene las direcciones IP. 

14. Deja abierta la pestaña Outlook en el explorador Edge para la siguiente tarea.

15. Vuelve a **LON-CL1**.

    
# Fin del laboratorio 3
