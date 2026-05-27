# Acuerdo Mogos × crescō

One-pager estático encriptado con [StatiCrypt](https://github.com/robinmoisson/staticrypt) (AES-256, client-side).

## Setup local

```bash
npm install
STATICRYPT_PASSWORD="tu-password" npm run build
open dist/index.html
```

El build genera `dist/index.html` con todo el contenido encriptado.

## Deploy

Funciona en cualquier host estático (Vercel, Netlify, Cloudflare Pages, etc.).

Variables de entorno requeridas:
- `STATICRYPT_PASSWORD` — la contraseña real (set en el dashboard del host, NUNCA commiteada)

Configuración:
- **Build command:** `npm run build`
- **Output directory:** `dist`

### Vercel

`vercel.json` ya tiene la config. Solo conecta el repo y agrega la env var.

### Cloudflare Workers

`wrangler.jsonc` + `src/worker.js` ya tienen la config con el binding `ASSETS`.

## Diseño

La pantalla de password usa un template custom (`tools/staticrypt-template.html`) con el sistema de diseño cresco (papel cream, mono accent, lockup `mogos × crescō`).

El one-pager (`proposal/mogos-onepager.html`) es responsive (desktop A4-width + breakpoints en 900px y 420px) e imprimible.

## Estructura

```
proposal/
  mogos-onepager.html      # documento fuente (sin encriptar)
tools/
  staticrypt-template.html # template de la pantalla de password
src/
  worker.js                # entry point para Cloudflare Workers
public/
  og.svg                   # imagen 1200×630 para preview en redes
package.json
vercel.json
wrangler.jsonc
.staticrypt.json           # salt (NO secret)
```
