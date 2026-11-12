# Políticas legales (por app)

Páginas estáticas de **Privacidad**, **Términos** y **Eliminación de cuenta** para cada app del
monorepo. Cada una es autocontenida (HTML + CSS + un `show(lang)` de JS) y bilingüe:
**inglés + el idioma nativo de la Biblia**.

| App | Privacidad | Términos | Eliminación de cuenta | Idiomas |
| --- | --- | --- | --- | --- |
| Biblia Latina (`com.biblia.latina`) | `biblia_latina/index.html` | `biblia_latina/terms.html` | `biblia_latina/delete-account.html` | Español + English |
| Biblia Reina Valera (`com.biblia.reinavalera`) | `biblia_reina_valera/index.html` | `biblia_reina_valera/terms.html` | `biblia_reina_valera/delete-account.html` | Español + English |
| Biblia Reina Valera 1960 (`com.teulys.bibliareinavalera1960`) | `biblia_reina_valera_1960/index.html` | `biblia_reina_valera_1960/terms.html` | `biblia_reina_valera_1960/delete-account.html` | Español + English |
| Biblia Latinoamericana de Hoy (`tjsoft.com.biblialatinoamericanadehoy`) | `biblia_latinoamericana_de_hoy/index.html` | `biblia_latinoamericana_de_hoy/terms.html` | `biblia_latinoamericana_de_hoy/delete-account.html` | Español + English |
| Biblia Palabra de Dios para Todos (`tjsoft.biblia.palabradedios`) | `biblia_palabra_de_dios_para_todos/index.html` | `biblia_palabra_de_dios_para_todos/terms.html` | `biblia_palabra_de_dios_para_todos/delete-account.html` | Español + English |
| Biblia Hispanoamericana BLPH (`com.tjsof.biblia.biblialapalabrahisp`) | `biblia_hispanoamericana_blph/index.html` | `biblia_hispanoamericana_blph/terms.html` | `biblia_hispanoamericana_blph/delete-account.html` | Español + English |
| Biblia Dios Habla Hoy (`com.teulys.bibliadioshablahoy`) | `biblia_dios_habla_hoy/index.html` | `biblia_dios_habla_hoy/terms.html` | `biblia_dios_habla_hoy/delete-account.html` | Español + English |
| Biblia de las Américas (`com.tjsof.biblia.lasamericas`) | `biblia_de_las_americas/index.html` | `biblia_de_las_americas/terms.html` | `biblia_de_las_americas/delete-account.html` | Español + English |
| Nueva Biblia al Día (`com.biblia.nuevabibliaalda`) | `nueva_biblia_al_dia/index.html` | `nueva_biblia_al_dia/terms.html` | `nueva_biblia_al_dia/delete-account.html` | Español + English |
| Biblia Versión Internacional (`tjsoft.com.bibliaversioninternacional`) | `biblia_version_internacional/index.html` | `biblia_version_internacional/terms.html` | `biblia_version_internacional/delete-account.html` | Español + English |
| Biblia La Palabra (`com.tjsof.biblia.biblialapalabra`) | `biblia_la_palabra/index.html` | `biblia_la_palabra/terms.html` | `biblia_la_palabra/delete-account.html` | Español + English |
| Biblia Reina Valera 1977 (`tjsoft.biblia.reinavalera1977`) | `biblia_reina_valera_1977/index.html` | `biblia_reina_valera_1977/terms.html` | `biblia_reina_valera_1977/delete-account.html` | Español + English |
| Bíblia Ave Maria (`com.biblia.avemaria`) | `biblia_ave_maria/index.html` | `biblia_ave_maria/terms.html` | `biblia_ave_maria/delete-account.html` | Português + English |

La página de **eliminación de cuenta** es la URL que Play exige en el formulario *Data safety* cuando
la app permite crear cuenta (aquí vía OAuth de Google). Ver `data-safety.md` para el detalle de las
respuestas del formulario.

El contenido se mantiene en sincronía con lo que realmente recopila la app (Google Sign-In, Firebase
Realtime Database, AdMob y almacenamiento local). Si cambia la recopilación de datos, actualizar estas
páginas **y** el formulario *Data safety* de Play / *App Privacy* de App Store.

## Pendientes antes de publicar

- Correo de contacto usado en las páginas: **teulys@gmail.com** (ya aplicado).
- Fecha de entrada en vigor: Latina y Ave Maria 14/10/2026; Reina Valera, Reina Valera 1960, Latinoamericana de Hoy, Palabra de Dios para Todos, Hispanoamericana BLPH, Dios Habla Hoy, Biblia de las Américas, Nueva Biblia al Día, Biblia Versión Internacional, Biblia La Palabra y Biblia Reina Valera 1977 10/11/2026.

## Hosting gratuito (repo público dedicado)

El repo del monorepo es **privado** y GitHub Pages necesita un repo público (o plan Enterprise), así que
este sitio se publica desde un **repo público dedicado** que contiene solo esta carpeta. Las páginas de
políticas deben ser públicas de todos modos, así que lo único que se expone es este contenido.

### 1. Crear el repo público

Crea en GitHub un repo **público y vacío** (sin README ni licencia), por ejemplo `biblia-legal`.

### 2. Publicar esta carpeta en ese repo

Desde la raíz del monorepo:

```bash
git remote add legal git@github.com:teulys/biblia-legal.git   # una sola vez
git subtree push --prefix=legal legal main
```

### 3. Activar GitHub Pages

En el repo nuevo: **Settings → Pages → Deploy from a branch → `main` → `/ (root)`**.

### URLs resultantes

Con el repo llamado `biblia-legal` (HTTPS automático, gratis):

- Índice del sitio: `https://teulys.github.io/biblia-legal/`
- Latina: `https://teulys.github.io/biblia-legal/biblia_latina/` y `.../biblia_latina/terms.html`
- Reina Valera: `https://teulys.github.io/biblia-legal/biblia_reina_valera/` y `.../biblia_reina_valera/terms.html`
- Reina Valera 1960: `https://teulys.github.io/biblia-legal/biblia_reina_valera_1960/` y `.../biblia_reina_valera_1960/terms.html`
- Latinoamericana de Hoy: `https://teulys.github.io/biblia-legal/biblia_latinoamericana_de_hoy/` y `.../biblia_latinoamericana_de_hoy/terms.html`
- Palabra de Dios para Todos: `https://teulys.github.io/biblia-legal/biblia_palabra_de_dios_para_todos/` y `.../biblia_palabra_de_dios_para_todos/terms.html`
- Hispanoamericana BLPH: `https://teulys.github.io/biblia-legal/biblia_hispanoamericana_blph/` y `.../biblia_hispanoamericana_blph/terms.html`
- Dios Habla Hoy: `https://teulys.github.io/biblia-legal/biblia_dios_habla_hoy/` y `.../biblia_dios_habla_hoy/terms.html`
- Biblia de las Américas: `https://teulys.github.io/biblia-legal/biblia_de_las_americas/` y `.../biblia_de_las_americas/terms.html`
- Nueva Biblia al Día: `https://teulys.github.io/biblia-legal/nueva_biblia_al_dia/` y `.../nueva_biblia_al_dia/terms.html`
- Biblia Versión Internacional: `https://teulys.github.io/biblia-legal/biblia_version_internacional/` y `.../biblia_version_internacional/terms.html`
- Biblia La Palabra: `https://teulys.github.io/biblia-legal/biblia_la_palabra/` y `.../biblia_la_palabra/terms.html`
- Biblia Reina Valera 1977: `https://teulys.github.io/biblia-legal/biblia_reina_valera_1977/` y `.../biblia_reina_valera_1977/terms.html`
- Ave Maria: `https://teulys.github.io/biblia-legal/biblia_ave_maria/` y `.../biblia_ave_maria/terms.html`

### Actualizar el sitio tras cualquier cambio en `legal/`

```bash
git subtree push --prefix=legal legal main
```

### Alternativas sin repo público

- **Firebase Hosting** (ya se usa Firebase): `firebase init hosting` con `public` = `legal` y
  `firebase deploy` → `https://<proyecto>.web.app/...` (plan Spark gratuito).
- **Netlify / Cloudflare Pages / Vercel**: sus planes gratis despliegan desde repos **privados**.
- **Netlify Drop**: arrastrar la carpeta `legal/` y obtienes una URL `*.netlify.app`.

## Checklist de tiendas

- [ ] URL pública HTTPS accesible desde incógnito (una por app).
- [ ] Enlazarla en **Play Console → App content → Privacy policy**.
- [ ] Responder **Data safety** en Play de forma coherente con la política (identificadores de
      dispositivo, datos de cuenta, favoritos, publicidad).
- [ ] Declarar que la app **muestra anuncios** (sección *Ads* de Play).
- [ ] En **App Store Connect → App Privacy**, declarar los tipos de datos y enlazar la URL.
