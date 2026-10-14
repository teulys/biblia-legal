# Políticas legales (por app)

Páginas estáticas de **Privacidad** y **Términos** para cada app del monorepo. Cada una es
autocontenida (HTML + CSS + un `show(lang)` de JS) y bilingüe: **inglés + el idioma nativo de la Biblia**.

| App | Privacidad | Términos | Idiomas |
| --- | --- | --- | --- |
| Biblia Latina (`com.biblia.latina`) | `biblia_latina/index.html` | `biblia_latina/terms.html` | Español + English |
| Bíblia Ave Maria (`com.biblia.avemaria`) | `biblia_ave_maria/index.html` | `biblia_ave_maria/terms.html` | Português + English |

El contenido se mantiene en sincronía con lo que realmente recopila la app (Google Sign-In, Firebase
Realtime Database, AdMob y almacenamiento local). Si cambia la recopilación de datos, actualizar estas
páginas **y** el formulario *Data safety* de Play / *App Privacy* de App Store.

## Pendientes antes de publicar

- Correo de contacto usado en las cuatro páginas: **teulys@gmail.com** (ya aplicado).
- Confirmar la **fecha de entrada en vigor** (actualmente 14/10/2026).

## Hosting gratuito

### Opción recomendada: GitHub Pages

1. Subir este repo (la carpeta `legal/`) a GitHub.
2. Repo → **Settings → Pages** → *Source*: `Deploy from a branch` → rama `main` → carpeta `/legal`.
3. URLs resultantes (HTTPS automático, gratis):
   - Latina: `https://<usuario>.github.io/<repo>/biblia_latina/` y `.../biblia_latina/terms.html`
   - Ave Maria: `https://<usuario>.github.io/<repo>/biblia_ave_maria/` y `.../biblia_ave_maria/terms.html`
4. Opcional: dominio propio añadiendo un archivo `CNAME`.

### Alternativa: Firebase Hosting (ya se usa Firebase)

```bash
npm i -g firebase-tools
firebase login
firebase init hosting      # public dir: legal
firebase deploy
```

Queda en `https://<proyecto>.web.app/biblia_latina/`, etc. (plan Spark gratuito).

### Otras gratis

Netlify Drop (arrastrar la carpeta → URL `*.netlify.app`), Cloudflare Pages, Vercel, GitLab Pages.

## Checklist de tiendas

- [ ] URL pública HTTPS accesible desde incógnito (una por app).
- [ ] Enlazarla en **Play Console → App content → Privacy policy**.
- [ ] Responder **Data safety** en Play de forma coherente con la política (identificadores de
      dispositivo, datos de cuenta, favoritos, publicidad).
- [ ] Declarar que la app **muestra anuncios** (sección *Ads* de Play).
- [ ] En **App Store Connect → App Privacy**, declarar los tipos de datos y enlazar la URL.
