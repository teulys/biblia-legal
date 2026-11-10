# Formulario "Seguridad de los datos" (Play Console)

Guía de respuestas para el formulario **Data safety** de Google Play. Aplica igual a
`biblia_latina`, `biblia_reina_valera` y `biblia_ave_maria`: comparten el mismo código
(`biblia_core`) y los mismos permisos en el manifest de release.

## Por qué Google marcó "We found issues with your Data safety form"

Se respondió **"No"** a *"Does your app collect or share any of the required user data types?"*.
Eso es incoherente con lo que hace la app:

| Evidencia | Qué implica |
| --- | --- |
| `com.google.android.gms.permission.AD_ID` y `ACCESS_ADSERVICES_AD_ID/TOPICS/ATTRIBUTION` en el manifest | La app usa el **ID de publicidad** (Google Mobile Ads) |
| `google_mobile_ads` en `biblia_core` | Se muestran anuncios → datos compartidos con Google |
| Google Sign-In | Se reciben **nombre, correo y foto** de la cuenta |
| Firebase Realtime Database | Se guardan **favoritos** y un **identificador de dispositivo** (`device_id`) |

Play detecta los SDK de anuncios y el permiso `AD_ID` automáticamente, así que la respuesta debe ser **"Yes"**.

## Paso 2 — Data collection and security

> Does your app collect or share any of the required user data types?

**Yes**

> Is all of the user data collected by your app encrypted in transit?

**Yes** — todas las conexiones usan HTTPS y WebSocket sobre TLS.

> Which of the following methods of account creation does your app support?

**OAuth** — el acceso es con "Iniciar sesión con Google"; no hay usuario ni contraseña propios.
No marcar "My app does not allow users to create an account": al iniciar sesión se crea un perfil
de usuario en Firebase (`/users/{googleUserId}`).

> Add a link that users can use to request that their account and associated data is deleted
> (Delete account URL)

Para Reina Valera: `https://teulys.github.io/biblia-legal/biblia_reina_valera/delete-account.html`

Las páginas ya están creadas en `legal/biblia_reina_valera/delete-account.html`,
`legal/biblia_latina/delete-account.html` y `legal/biblia_ave_maria/delete-account.html`.
Incluyen los pasos, los datos que se eliminan, los que se conservan y el plazo de 30 días.

> Do you provide a way for users to request that some or all of their data is deleted, without
> requiring them to delete their account? (Optional)

**Yes** — los favoritos se pueden eliminar dentro de la app (deslizando el elemento), y la página de
eliminación explica cómo solicitar el borrado total por correo sin cerrar la cuenta de Google.

## Paso 3 — Data types

Marcar exactamente estos cuatro tipos:

| Categoría | Tipo de dato | Collected | Shared | Required/Optional | Purpose |
| --- | --- | --- | --- | --- | --- |
| Personal info | **Email address** | Sí | No | Optional | Account management; App functionality |
| Personal info | **Name** | Sí | No | Optional | Account management; App functionality |
| App activity | **Other user-generated content** (favoritos de versículos) | Sí | No | Optional | App functionality |
| Device or other IDs | **Device or other IDs** | Sí | **Sí** | Required | Advertising or marketing; App functionality |

Notas:

- **Device or other IDs** es el dato crítico: cubre el **ID de publicidad** (se comparte con Google
  para publicidad) y el `device_id` aleatorio que la app usa para organizar los favoritos.
- **Email/Name**: solo se recogen si el usuario inicia sesión con Google → **Optional**.
- **No** declarar `Photos`: la app no recopila fotos; solo muestra la URL de la foto de perfil de Google.
- **No** declarar `Crash logs` ni `Diagnostics`: no hay Crashlytics ni Analytics inicializados en el código.
- **No** declarar `Location`, `Contacts`, `Camera`, `Microphone` ni datos de salud: la app no los usa.
- Sobre "Shared": los datos de cuenta y favoritos los procesa Firebase **como proveedor por tu cuenta**
  (no cuentan como "compartidos" según el criterio de Google). Los IDs de dispositivo sí se comparten
  con Google (AdMob) para publicidad. Si prefieres ser más conservador, puedes marcar también
  Email/Name como compartidos con Google; lo importante es que la declaración sea coherente con la
  política de privacidad.

## Paso 4 — Data usage and handling

| Pregunta | Respuesta |
| --- | --- |
| Is all of the user data collected by your app encrypted in transit? | **Yes** (HTTPS y WebSocket TLS) |
| Do you provide a way for users to request that their data be deleted? | **Yes** → correo **teulys@gmail.com** o la URL de la política |
| Do you collect data from children? | **No** |
| Is your app designed for children? | **No** |

## Otras secciones que deben quedar coherentes

- **App content → Ads**: *"Contains ads"* → **Yes**.
- **App content → Privacy policy**: URL pública (por ejemplo
  `https://teulys.github.io/biblia-legal/biblia_reina_valera/`).
- **Target audience**: mayores de 13 años.
- La política de privacidad (`legal/<app>/index.html`) ya describe nombre, correo, foto, `device_id`,
  favoritos y publicidad de AdMob, así que estas respuestas son consistentes con ella.

## Resumen

1. Cambiar la primera respuesta de **No** a **Yes**.
2. Declarar 4 tipos: Email, Name, Other user-generated content, Device or other IDs.
3. Device or other IDs marcado como **Shared** con finalidad de publicidad.
4. Confirmar cifrado en tránsito, borrado por correo y que no es para menores.
