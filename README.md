# ROMSA Industrial — Sitio Web

Sitio web público de ROMSA Industrial. Reemplaza el sitio actual en Wix
(romsaindustrial.com). Es un solo archivo `index.html` autocontenido
(HTML/CSS/JS plano, sin build step, sin framework, sin dependencias
externas por CDN) — el logo va incrustado como `data:image/svg+xml`
directamente en el HTML.

## Cómo activar GitHub Pages

1. En este repositorio, ve a **Settings → Pages**.
2. En **Build and deployment → Source**, selecciona **Deploy from a branch**.
3. En **Branch**, selecciona `main` y la carpeta `/ (root)`. Guarda.
4. GitHub publicará el sitio en `https://lzuniga-romsa.github.io/romsa-industrial-web-/`
   (unos minutos después del primer deploy).

## Cómo conectar el dominio real (romsaindustrial.com)

El dominio está actualmente en DNS de Wix (`ns6.wixdns.net` / `ns7.wixdns.net`),
con esta configuración verificada:

- **Dominio raíz / apex** (`romsaindustrial.com`) → 3 registros **A** apuntando
  a IPs de Wix (`185.230.63.x`).
- **Subdominio `www`** (`www.romsaindustrial.com`) → registro **CNAME** a
  `cdn1.wixdns.net`.

Para apuntar el dominio a este sitio en GitHub Pages, en el panel de DNS de
Wix (Dominios → DNS Records) hay que **reemplazar** esos registros:

### Si se usa el dominio raíz sin `www` (romsaindustrial.com)

Borrar los registros A actuales de Wix y agregar estos 4 registros **A**
(son fijos, los exige GitHub Pages para dominios apex):

```
A   @   185.199.108.153
A   @   185.199.109.153
A   @   185.199.110.153
A   @   185.199.111.153
```

### Si se usa `www.romsaindustrial.com`

Reemplazar el CNAME actual (que apunta a `cdn1.wixdns.net`) por:

```
CNAME   www   lzuniga-romsa.github.io
```

Se recomienda configurar ambos (A en el apex + CNAME en `www`) y luego, en
**Settings → Pages → Custom domain** de este repo, escribir
`romsaindustrial.com` para que GitHub configure el redirect y el
certificado HTTPS automáticamente. También hay que agregar un archivo
`CNAME` en la raíz del repo con el dominio (GitHub lo crea solo al guardar
el Custom domain desde la UI).

**Importante:** los cambios de DNS pueden tardar desde minutos hasta 24-48
horas en propagarse. No apagar el sitio de Wix hasta confirmar que el nuevo
sitio responde correctamente en el dominio.

## Estructura

- `index.html` — el sitio completo (una sola página, sin backend).

## Pendientes conocidos

- Reemplazar los 3 placeholders de la Galería de Proyectos por fotos reales.
- Completar la página de Aviso de Privacidad (buscar el comentario
  `<!-- TODO: aviso de privacidad -->` en `index.html`).
- Agregar seguimiento de Google Tag Manager/Ads cuando exista la cuenta.
