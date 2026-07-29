# Repositorio de Investigación — Escuela Normal Superior de Manatí

Sitio público de consulta + panel editor privado, sin costo, usando GitHub + Netlify.

**Cómo funciona:**
- La carpeta completa es tu sitio web.
- `index.html` = página pública (la ve cualquier persona, sin login).
- `admin/` = panel editor (solo tú puedes entrar, con usuario y contraseña).
- Cuando cargas una ficha desde `/admin`, se guarda automáticamente en `content/fichas.json`, y la página pública la muestra al instante.

No necesitas tocar código para el uso diario. El código ya está listo; solo lo conectas siguiendo estos pasos una sola vez.

---

## Paso 1 · Crear el repositorio en GitHub

1. Crea una cuenta gratuita en [github.com](https://github.com) si no tienes una.
2. Crea un repositorio nuevo, por ejemplo `repositorio-ens-manati`. Puede ser público.
3. Sube todos los archivos de esta carpeta a ese repositorio (puedes arrastrarlos desde la web de GitHub, con el botón "Add file → Upload files").

## Paso 2 · Publicar el sitio en Netlify

1. Crea una cuenta gratuita en [netlify.com](https://netlify.com) usando "Sign up with GitHub" (así quedan conectadas automáticamente).
2. En el panel de Netlify: **Add new site → Import an existing project → GitHub** y elige tu repositorio.
3. Deja la configuración por defecto (ya incluye `netlify.toml`) y da clic en **Deploy**.
4. En un par de minutos tendrás una URL como `nombre-al-azar.netlify.app`. Ese ya es tu sitio público.
   - Opcional: en **Site configuration → Domain management** puedes ponerle un nombre más claro (gratis, ej. `repositorio-ensmanati.netlify.app`) o conectar un dominio propio si más adelante consigues uno.

## Paso 3 · Activar tu acceso de editora (login con GitHub)

Esto es lo que hace que **solo tú** puedas entrar a `/admin`. Como tú eres la dueña del repositorio, iniciar sesión con tu propia cuenta de GitHub ya te da acceso — sin sistema de usuarios aparte.

1. Edita `admin/config.yml` directamente en GitHub (ícono del lápiz ✏️) y reemplaza `TU-USUARIO-DE-GITHUB` por tu usuario real de GitHub. Guarda el cambio.
2. En [github.com/settings/developers](https://github.com/settings/developers) → **OAuth Apps** → **New OAuth App**. Como **Authorization callback URL** pon exactamente `https://api.netlify.com/auth/done`. Registra la aplicación y copia el **Client ID** y el **Client Secret**.
3. En Netlify: **Project configuration → Access & security → OAuth → Install provider → GitHub**, y pega ahí el Client ID y el Client Secret.

Con esto, solo quien tenga acceso de escritura a tu repositorio de GitHub (o sea, solo tú) podrá entrar al panel.

## Paso 4 · Empezar a cargar fichas

1. Entra a `tusitio.netlify.app/admin`.
2. Clic en **Login with GitHub** y autoriza el acceso (solo la primera vez).
3. Verás la colección **"Fichas de investigación"**. Da clic en **Nuevo → Listado de fichas** (o edita el listado existente) y agrega un ítem por cada proyecto: título, autor, año, línea de investigación, resumen y el PDF.
4. Da clic en **Publish**. En 1-2 minutos el sitio público se actualiza solo.
5. Puedes borrar la ficha de ejemplo que trae `content/fichas.json` una vez publiques las tuyas.

---

## Personalizar más adelante

- **Colores y tipografía:** todo está en `css/estilos.css`, con comentarios.
- **Textos de la portada:** están directamente en `index.html` (el bloque `<section class="hero">`).
- **Líneas de investigación:** no hay una lista cerrada — escribes el nombre de la línea libremente al cargar cada ficha, así puedes ajustarlas con el tiempo.
- **Escudo/logo:** ya está integrado (`img/escudo.png`), tomado del escudo real de la institución.

## Si algo falla

- Si `/admin` no carga el login o da error al autenticar: revisa que el **Client ID** y **Client Secret** en Netlify (Paso 3) sean exactamente los que copiaste de GitHub, y que la **Authorization callback URL** en GitHub sea exactamente `https://api.netlify.com/auth/done`.
- Si ves un error de "repo not found" en el panel: revisa que en `admin/config.yml` el campo `repo:` tenga tu usuario de GitHub correcto y el nombre exacto del repositorio.
- Si publicas una ficha y no aparece en el sitio público: espera 1-2 minutos y refresca — Netlify vuelve a desplegar el sitio en cada cambio.
