# Mi amiga la vaca — versión con cuenta y sincronización

Esta versión añade registro e inicio de sesión por correo y contraseña, recuperación de contraseña y sincronización de los registros de la finca entre dispositivos mediante Supabase. La app está preparada para publicarse como sitio estático gratis en GitHub Pages.

## Publicar o actualizar en GitHub Pages
1. Descarga y descomprime este paquete.
2. Sube **todos** los archivos de esta carpeta a la raíz de tu repositorio GitHub, reemplazando los archivos anteriores: `index.html`, `manifest.webmanifest`, `sw.js`, `icon.svg` y `README.md`.
3. En GitHub, abre **Settings → Pages** y confirma que Pages publique desde la rama `main`, carpeta `/ (root)`.
4. Abre la dirección exacta que GitHub muestra en Pages.

## Ajuste necesario en Supabase (una sola vez)
Para que los enlaces de confirmación de correo vuelvan a tu sitio:
1. Abre [Finca Viva en Supabase](https://supabase.com/dashboard/project/nlgrrqdxfwrqyfzhxavl).
2. Ve a **Authentication → URL Configuration**.
3. En **Site URL**, pega la URL exacta de GitHub Pages, por ejemplo `https://TU-USUARIO.github.io/mi-amiga-la-vaca/` (usa tu URL real, no el ejemplo).
4. Añade esa misma URL en **Redirect URLs** y guarda.

## Cómo probar
1. Abre tu sitio de GitHub Pages.
2. Escribe tu correo y una contraseña de al menos 6 caracteres y pulsa **Crear cuenta gratis**.
3. Si Supabase solicita confirmar el correo, abre el mensaje recibido y pulsa el enlace. Revisa Spam si no aparece.
4. Regresa al sitio e inicia sesión. Registra un animal y espera el aviso de sincronización.
5. Abre el mismo sitio en otro dispositivo e inicia sesión con la misma cuenta: los registros deberían aparecer allí también.

## Datos y seguridad
- La clave incluida en `index.html` es una clave **publishable** de Supabase diseñada para uso público en el navegador. No incluyas nunca una clave `service_role` ni una clave secreta en GitHub.
- Los registros de la app se sincronizan como un documento JSON por finca. La tabla `ranch_app_data` tiene RLS activado y las políticas limitan la lectura a miembros de la finca y la escritura a administradores/propietarios.
- Los datos locales que ya existan en este navegador se combinan con los datos de la nube al iniciar sesión por primera vez.
- La app necesita conexión a internet para iniciar sesión y sincronizar. La aplicación puede instalarse como PWA; el guardado local sirve como respaldo temporal si la conexión falla.
- El asistente sigue siendo un asistente sencillo basado en reglas, no una IA veterinaria. Las alertas se muestran dentro de la app; no son notificaciones push.

## Archivos
- `index.html`: aplicación web.
- `manifest.webmanifest`: configuración instalable.
- `sw.js`: caché de recursos PWA.
- `icon.svg`: icono.
