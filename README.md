# Tienda para feria de ropa — plantilla gratis (GitHub Pages)

Cada vendedor tiene su propio sitio, con su propio link, y carga sus fotos/videos
desde el celular sin escribir código. Todo gratis, sin servidores ni pagos.

## Cómo funciona

- `index.html` → la vitrina pública que ve la gente (productos "colgados" de una soga).
- `admin.html` → el panel privado donde el vendedor carga sus productos.
- `products.json` y `site.json` → donde se guardan los datos (los actualiza el panel solo).
- El panel sube todo directo a GitHub usando la API de GitHub, sin necesidad de instalar nada.

Cada vendedor necesita su **propio repositorio** (o sea, repetís estos pasos por cada uno).

---

## Paso 1 — Crear cuenta de GitHub (si no tiene)

Entrar a github.com → "Sign up" → es gratis.

## Paso 2 — Crear el repositorio

1. En github.com, arriba a la derecha, tocar **+** → **New repository**.
2. Nombre: por ejemplo `mi-tienda` (sin espacios).
3. Marcar **Public**.
4. Crear.

## Paso 3 — Subir estos archivos

1. Dentro del repo recién creado, click en **Add file → Upload files**.
2. Arrastrar TODOS los archivos de esta carpeta (`index.html`, `admin.html`,
   `style.css`, `app.js`, `admin.js`, `config.js`, `site.json`, `products.json`, y la carpeta `assets`).
3. Click en **Commit changes**.

## Paso 4 — Completar config.js (una sola vez, por tienda)

Este paso lo hacés vos, no el vendedor. Le dice al panel a qué repositorio conectarse,
así el vendedor nunca tiene que saber ni ver esos datos.

1. Dentro del repo en GitHub, abrí el archivo `config.js` y tocá el ícono de lápiz (editar).
2. Reemplazá `TU-USUARIO-DE-GITHUB` por tu usuario real de GitHub.
3. Reemplazá `NOMBRE-DE-ESTE-REPOSITORIO` por el nombre que le pusiste al repo (ej: `mi-tienda`).
4. **Commit changes**.

## Paso 5 — Activar GitHub Pages

1. En el repo, ir a **Settings → Pages**.
2. En "Branch" elegir `main` y carpeta `/ (root)` → **Save**.
3. Esperar 1-2 minutos. La tienda va a quedar en:
   `https://TU-USUARIO.github.io/mi-tienda/`

## Paso 6 — Crear la clave de acceso para el vendedor

Esto es un "token" de GitHub, pero para el vendedor va a ser simplemente **su clave**
— nunca necesita saber qué es GitHub ni cómo funciona.

1. Ir a github.com → foto de perfil → **Settings** (de la cuenta, no del repo).
2. **Developer settings** (al final del menú izquierdo).
3. **Personal access tokens → Fine-grained tokens → Generate new token**.
4. Nombre: por ejemplo el nombre del vendedor. Expiración: la que prefieras (se puede renovar).
5. En "Repository access" elegir **Only select repositories** y elegir su repo
   (o "All repositories" si vas a usar la misma clave para todas las tiendas que administrás).
6. En "Permissions" → **Repository permissions** → buscar **Contents** → poner **Read and write**.
7. Generar y **copiar la clave** (empieza con `ghp_` o `github_pat_`). Solo se muestra una vez.
8. Pasársela al vendedor como le pasarías cualquier contraseña (WhatsApp, papelito, etc.)

## Paso 7 — Lo que hace el vendedor (esto es todo lo que necesita saber)

1. Abrir `https://TU-USUARIO.github.io/mi-tienda/admin.html`
2. Pegar la clave que le diste → **Entrar**. (Solo la primera vez; después el celular la recuerda)
3. Completar nombre de la tienda, WhatsApp, Instagram y colores → Guardar.
4. Cargar cada producto con foto (y video si quiere) → Subir producto.
5. La tienda pública se actualiza sola en menos de un minuto.

El vendedor solo ve un cuadro para pegar su clave — nada de "usuario de GitHub",
"repositorio" ni "token" aparece nunca en su pantalla.

## Para la próxima tienda

Como vos administrás todo desde tu misma cuenta, repetí los pasos 2 a 7 con un
nombre de repositorio distinto por cada vendedor (ej: `tienda-maria`, `tienda-juan`).
Cada uno tiene su propio link tipo `https://tu-usuario.github.io/tienda-maria/`,
y su propio `config.js` completado con ese mismo nombre de repo.

**Atajo:** en el Paso 6, en vez de un token por tienda, podés generar **un solo
token** con acceso a **todos** tus repositorios ("All repositories" o eligiendo
varios en "Only select repositories") y usar ese mismo token en el panel de cada
tienda. Así no tenés que crear uno nuevo cada vez que armás un puesto.

## Si un vendedor no paga (pausar o cortar el acceso)

Hay dos controles independientes, y elegís uno u otro según qué quieras lograr:

**Bloquear que siga cargando/editando fotos** (la tienda queda visible tal cual estaba):
1. GitHub → tu foto de perfil → Settings → Developer settings → Personal access tokens.
2. Buscá el token de esa tienda → **Delete**.
3. Su panel deja de funcionar al toque. Si vuelve a pagar, le generás uno nuevo (Paso 6).

**Ocultar la tienda entera de los clientes** (no solo el panel):
1. Entrá al repo de esa tienda en GitHub → abrí `site.json` → ícono de lápiz (editar).
2. Cambiá `"activa": true` por `"activa": false` → **Commit changes**.
3. En menos de un minuto, en vez del catálogo va a aparecer un cartel de "tienda pausada".
4. Para reactivarla, volvés a poner `"activa": true`.

Este segundo control lo manejás solo vos con tu propia cuenta de GitHub — el
vendedor no lo ve ni lo puede tocar desde su panel, así que no se lo puede
reactivar solo aunque tenga su clave.

## Nuevo o usado

Al cargar cada producto, el panel tiene un campo "Estado" con dos opciones:
Nuevo o Usado. Se muestra como etiqueta sobre la foto en la tienda, y los
clientes pueden filtrar por eso en el buscador ("Solo nuevo" / "Solo usado").

## Sobre los videos

GitHub es gratis pero no está pensado para alojar mucho video. Recomendado:
- Videos cortos y livianos (menos de ~20 MB, el panel avisa si pesa mucho).
- Para videos más largos, mejor subirlos a Instagram/TikTok/YouTube y pegar
  el link en el campo "O link a un video" del panel — se muestra igual en la tienda.

## Elegir los colores de la tienda

En el panel (`admin.html`), dentro de "Datos de tu tienda", hay 6 paletas de colores
para elegir tocando (Feria clásica, Tropical, Boutique, Noche neón, Otoño, Océano).
Se aplican a toda la tienda: banderines, luces, broches, etiquetas y botones.

Si alguien quiere afinar más, tocando "elegir colores a mano" aparecen 6 selectores
de color individuales (fondo + 5 acentos) — son las ruedas de color normales del
celular/navegador, no hay que escribir ningún código.

Esto lo controla únicamente el vendedor desde su panel privado — nadie que visite
la tienda pública puede tocarlo.
