MI AGENDA 2.0 – ANDROID / PWA
================================

INCLUYE
- Conexión OAuth con Google Calendar desde el navegador.
- Lectura de eventos del calendario principal (incluye eventos recurrentes expandidos).
- Creación, edición y eliminación de eventos en Google Calendar.
- Detección de cruces consultando Google Calendar para la fecha seleccionada antes de guardar.
- Recordatorios emergentes de Google Calendar configurables.
- Calendario mensual, resumen y lista de eventos.
- Eventos guardados sin conexión quedan pendientes para sincronizar después.
- Copia de los eventos consultados para visualización cuando no haya conexión (la copia puede quedar desactualizada).

REQUISITO PARA ACTIVAR GOOGLE
La aplicación está preparada para Google Calendar, pero no puede conectarse hasta que se configure un ID de cliente OAuth propio. No se incluye un ID de cliente porque pertenece al proyecto de Google Cloud que debe autorizar el dominio donde se publique esta aplicación.

CONFIGURACIÓN DE GOOGLE CLOUD
1. Entra a https://console.cloud.google.com/ con la cuenta que usará el calendario.
2. Crea un proyecto o selecciona uno.
3. Abre APIs y servicios > Biblioteca y habilita Google Calendar API.
4. Configura la pantalla de consentimiento OAuth. Si la aplicación está en modo de prueba, agrega tu correo como usuario de prueba.
5. Abre APIs y servicios > Credenciales > Crear credenciales > ID de cliente OAuth.
6. Selecciona Aplicación web.
7. En Orígenes autorizados de JavaScript, agrega el origen HTTPS donde alojarás MI AGENDA (ejemplo: https://mi-agenda-tuya.netlify.app). No incluyas una ruta ni una barra final.
8. Copia el ID de cliente OAuth que termina en .apps.googleusercontent.com.
9. Abre MI AGENDA, entra a la pestaña Google, pega ese ID, pulsa Guardar ID y luego Conectar con Google.
10. Acepta el permiso para consultar y administrar eventos de Google Calendar.

IMPORTANTE
- No introduzcas contraseñas ni el secreto de cliente en la aplicación. Solo se usa el ID de cliente OAuth.
- La aplicación usa el alcance https://www.googleapis.com/auth/calendar.events.
- El token de acceso se mantiene en memoria y no se escribe en localStorage. Por seguridad, puede ser necesario volver a conectar tras cerrar o recargar la aplicación.
- Debe publicarse en HTTPS para usar OAuth y Service Worker. No funcionará la conexión Google abriendo index.html directamente desde el almacenamiento del teléfono.
- Se conecta al calendario principal (primary).
- Las alertas se programan como recordatorios emergentes del propio Google Calendar. Asegúrate de que las notificaciones de Google Calendar estén permitidas en Android.
- El detector consulta Google Calendar al guardar un evento. No bloquea un evento si Google no está conectado; en ese caso lo guarda localmente como pendiente y solo puede revisar los eventos locales.
- La aplicación no envía información a un servidor propio. Las llamadas se hacen desde el navegador a Google Calendar API.

INSTALAR EN ANDROID
1. Publica todos los archivos de esta carpeta en un alojamiento HTTPS (por ejemplo, Netlify o GitHub Pages).
2. Configura en Google Cloud el mismo dominio HTTPS que te asignó el alojamiento.
3. Abre la URL publicada con Chrome en Android.
4. Usa el menú ⋮ > Instalar aplicación o Añadir a pantalla principal.

ARCHIVOS
- index.html: aplicación MI AGENDA 2.0.
- manifest.json: configuración de instalación.
- sw.js: caché básica para la aplicación.
- icon-192.png e icon-512.png: iconos.
