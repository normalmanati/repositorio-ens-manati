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

## Paso 3 · Activar tu acceso de editora (Identity + Git Gateway)

Esto es lo que hace que **solo tú** puedas entrar a `/admin`.

1. En el panel de Netlify, entra a tu sitio → **Integrations → Identity → Enable Identity**.
2. En **Identity → Settings**, en "Registration preferences" selecciona **Invite only** (así nadie más se puede registrar).
3. Baja a **Services → Git Gateway → Enable Git Gateway** (esto permite que el panel guarde los cambios en GitHub sin que tú necesites saber usar Git).
4. Vuelve a la pestaña **Identity** y da clic en **Invite users**. Escribe tu propio correo.
5. Revisa tu correo, acepta la invitación y crea tu contraseña.

Con esto, solo las personas que tú invites (en este caso, solo tú) podrán entrar al panel.

## Paso 4 · Empezar a cargar fichas

1. Entra a `tusitio.netlify.app/admin`.
2. Inicia sesión con el correo y contraseña del paso anterior.
3. Verás la colección **"Fichas de investigación"**. Da clic en **Nuevo → Listado de fichas** (o edita el listado existente) y agrega un ítem por cada proyecto: título, autor, año, línea de investigación, resumen y el PDF.
4. Da clic en **Publish**. En 1-2 minutos el sitio público se actualiza solo.
5. Puedes borrar la ficha de ejemplo que trae `content/fichas.json` una vez publiques las tuyas.

---

## Personalizar más adelante

- **Colores y tipografía:** todo está en `css/estilos.css`, con comentarios.
- **Textos de la portada:** están directamente en `index.html` (el bloque `<section class="hero">`).
- **Líneas de investigación:** no hay una lista cerrada — escribes el nombre de la línea libremente al cargar cada ficha, así puedes ajustarlas con el tiempo.
- **Escudo/logo:** por ahora se muestra un círculo con "ENS". Si me compartes el logo real de la institución, lo integro.

## Si algo falla

- Si `/admin` no carga el login: revisa que Identity y Git Gateway estén ambos en verde en Netlify (Paso 3).
- Si publicas una ficha y no aparece en el sitio público: espera 1-2 minutos y refresca — Netlify vuelve a desplegar el sitio en cada cambio.
