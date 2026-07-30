# Series_db

Bitácora personal de series: seguimiento, valoraciones, tiempo visto, carátulas y
próximos estrenos (con sincronización opcional a Trakt.tv).

Es una app 100% estática (sin backend): todos los datos se guardan en el propio
navegador (localStorage para el texto, IndexedDB para las carátulas). Este repo
solo contiene el código; nada de tus datos personales pasa por GitHub ni por Vercel.

## Estructura

```
index.html          → la app completa (HTML + CSS + JS en un único archivo)
manifest.json        → metadatos para "Añadir a pantalla de inicio"
icons/                → iconos de la app (192, 512, maskable, apple-touch, favicon)
```

## Desplegar en Vercel

1. Sube estos archivos a un repositorio de GitHub (manteniendo `index.html` en la
   raíz del repo, junto a `manifest.json` y la carpeta `icons/`).
2. Entra en [vercel.com](https://vercel.com) → **Add New Project** → importa ese repo.
3. Vercel detecta que es un sitio estático; no hace falta configurar ningún
   "build command" ni "output directory" — déjalo todo por defecto y dale a **Deploy**.
4. En 30-60 segundos tendrás una URL tipo `tu-repo.vercel.app`.

Cada vez que subas cambios al repo (por ejemplo, un `index.html` actualizado que te
pase Claude), Vercel vuelve a desplegar solo. El código se actualiza; **tus datos
guardados en el navegador no se tocan**, porque no viven en el archivo sino en el
propio dispositivo.

## Primera vez que abras la URL de Vercel

Como el almacenamiento del navegador está ligado al dominio, la primera vez que
abras la versión desplegada empezará vacía (no hereda lo que tengas en tu copia
local abierta como archivo). Para pasar tus datos:

1. Abre tu app actual (el archivo local) → menú (⋮) → **Exportar copia de
   seguridad (JSON)**.
2. Abre la URL de Vercel por primera vez → menú (⋮) → **Importar** → selecciona
   ese JSON.

A partir de ahí, esa URL ya es tu app "de verdad", con todo dentro.

## Instalarla como app en el móvil

Con la URL de Vercel abierta en Chrome (Android) o Safari (iOS):

- **Android/Chrome**: menú del navegador → "Añadir a pantalla de inicio" /
  "Instalar aplicación".
- **iOS/Safari**: botón compartir → "Añadir a pantalla de inicio".

Se instalará con su propio icono y abrirá en pantalla completa, sin la barra del
navegador, como una app nativa.

## Trakt.tv

Desde el menú (⋮) dentro de la app puedes pegar tu Client ID de Trakt (se crea
gratis en trakt.tv/oauth/applications). No es una clave secreta sensible: solo
identifica la app frente a la API pública de Trakt.
