# Tienda virtual — Ferretería

Sitio estático (sin backend) listo para publicar en GitHub Pages. Incluye:

- Catálogo con búsqueda y filtro por categorías
- Carrito de compras → cotización automática por WhatsApp
- Banner de promociones animado
- Panel de administrador para subir productos, categorías y promociones

## Archivos
- `index.html` — toda la tienda y el panel admin (un solo archivo)
- `products.json` — tus productos, categorías, promociones y configuración

## 1. Publicar en GitHub Pages

1. Crea un repositorio nuevo en GitHub (puede ser público o privado con GitHub Pro).
2. Sube estos dos archivos (`index.html` y `products.json`) a la raíz del repositorio (botón **Add file → Upload files**, arrastra los archivos y confirma).
3. Ve a **Settings → Pages**.
4. En "Source" elige la rama `main` y la carpeta `/ (root)`. Guarda.
5. En 1-2 minutos GitHub te dará un link tipo `https://tuusuario.github.io/tu-repo/`. Esa es tu tienda.

## 2. Cómo funciona el panel de administrador

Como el sitio es estático (no tiene servidor propio), el panel de admin **no guarda los cambios automáticamente para todo el mundo**. Funciona así:

1. La tienda **no muestra ningún botón de "Admin"** — tus clientes nunca lo ven. Para entrar tú, agrega `#admin` al final del link de tu tienda y presiona Enter, por ejemplo:
   `https://tuusuario.github.io/tu-repo/#admin`
   Guarda ese link en tus favoritos para no tener que escribirlo cada vez. Te va a pedir la contraseña (por defecto: `ferreteria2026`, cámbiala en el código antes de publicar — búscala en `index.html`, línea con `ADMIN_PASSWORD`).
2. Sube o edita tus productos, categorías y promociones. Verás la vista previa en vivo en ese navegador.
3. Cuando termines, haz clic en **"Descargar products.json"**.
4. Ve a tu repositorio en GitHub, abre el archivo `products.json`, presiona el ícono de lápiz (editar) o usa **Add file → Upload files** para reemplazarlo con el que acabas de descargar.
5. Confirma el cambio ("Commit changes"). En un minuto tu tienda pública se actualiza para todos los visitantes.

Esto significa que puedes ir armando tu catálogo con calma: cada vez que subas un lote de productos, descargas el archivo y lo reemplazas en GitHub.

> **Nota de seguridad:** la contraseña del panel admin es una protección básica pensada para que un visitante casual no entre a editar por curiosidad, pero no es una seguridad real (cualquiera que revise el código puede verla). No subas el catálogo interno de precios de costo ni información sensible del negocio.

## 3. Imágenes de productos

Tienes dos formas de agregar fotos en el panel admin:

- **Subir archivo:** se optimiza automáticamente y queda incrustada dentro de `products.json`. Es la forma más simple, pero si subes muchas fotos el archivo pesará más.
- **URL de imagen:** pegas un enlace (por ejemplo, de una imagen que subiste a Google Drive, Imgur, o tu propio repositorio de GitHub en una carpeta `/imagenes`). Mantiene el archivo liviano — recomendado si vas a cargar muchos productos.

## 4. Conectar tu dominio propio (cuando lo compres)

1. En tu repositorio, ve a **Settings → Pages → Custom domain** y escribe tu dominio (ej. `www.miferreteria.com`).
2. En el panel de tu proveedor de dominio, agrega los registros DNS que GitHub te indique (normalmente un `CNAME` apuntando a `tuusuario.github.io`, o registros `A` si usas el dominio raíz sin `www`).
3. Espera la propagación (puede tardar de minutos a horas) y activa "Enforce HTTPS" en la misma sección cuando esté disponible.

No necesitas cambiar nada más del sitio — sigue funcionando igual, solo cambia el link.

## 5. Probarlo en tu computadora antes de publicar

Si abres `index.html` haciendo doble clic, el navegador puede bloquear la carga de `products.json` por seguridad (CORS). Para probarlo localmente:

```bash
# dentro de la carpeta del proyecto
python3 -m http.server 8000
```

Luego abre `http://localhost:8000` en tu navegador.
