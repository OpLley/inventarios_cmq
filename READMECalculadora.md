# Cemenquin · Calculadora de inventario

Herramienta web móvil para personal de almacén/logística de **Comercial Cemenquin**.
Permite buscar o escanear un producto, capturar cantidades (tarimas, camas y piezas),
adjuntar una foto de evidencia y registrar check-ins en un mapa. Todo en un solo archivo
(`index.html`), sin dependencias de servidor y funcional sin conexión.

## Qué incluye

- **Catálogo embebido** de 189 productos (Cemenquin, Zahori y CementPRO) con su configuración
  de piezas por cama / por tarima.
- **Búsqueda con autocompletado** por clave o descripción (insensible a acentos).
- **Preview del producto** con fotos extraídas de los catálogos.
- **Captura numérica** directa de tarimas, camas y piezas, con total por línea y gran total.
- **Foto de evidencia** por producto (toma con cámara o elige de galería; se comprime sola).
- **Escaneo de código de barras** (modo DEMO) que carga un artículo y registra un check-in con pin en un mapa.
- **Guardado de registros** en el dispositivo (ver sección Base de datos).
- Identidad visual de Cemenquin en tema claro.

## Cómo verlo

Abre `index.html` en un navegador real (**Chrome** o **Safari**). En el celular, evita abrirlo
desde visores de WhatsApp/Drive/Archivos: esos no ejecutan el código. La forma recomendada es
publicarlo con GitHub Pages (abajo) y abrir la URL en el navegador.

## Subirlo a GitHub

### Opción A — desde la web (sin instalar nada)
1. Crea una cuenta en https://github.com y entra.
2. Botón **New** (o **+** arriba a la derecha → *New repository*).
3. Nombre sugerido: `cemenquin-inventario`. Déjalo **Public**. Crea el repositorio.
4. En el repo vacío: **Add file → Upload files**. Arrastra `index.html`, `README.md` y `.gitignore`.
5. **Commit changes**.

### Opción B — desde la terminal (git)
```bash
git init
git add .
git commit -m "Calculadora de inventario Cemenquin"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/cemenquin-inventario.git
git push -u origin main
```

## Publicar con GitHub Pages (obtener una URL para el celular)

1. En el repositorio: **Settings → Pages**.
2. En *Build and deployment* → *Source*: **Deploy from a branch**.
3. Branch: **main** y carpeta **/(root)**. **Save**.
4. Espera ~1 minuto. GitHub te dará una URL del tipo:
   `https://TU_USUARIO.github.io/cemenquin-inventario/`
5. Abre esa URL en Chrome/Safari del celular. Tip: **Agregar a pantalla de inicio**
   para usarla como si fuera una app.

> Al estar en una URL `https://`, también se habilitan correctamente la cámara y el
> almacenamiento local del navegador.

## Base de datos / guardado de registros

**Importante:** GitHub Pages solo publica el archivo (hosting estático); **no es una base de
datos** y no guarda datos en un servidor. El guardado de registros funciona así:

- **Guardado local (incluido):** la app guarda los registros en el **navegador del propio
  dispositivo** usando IndexedDB. El conteo en curso se autoguarda (no se pierde al recargar/cerrar)
  y puedes guardar conteos con nombre desde **Guardar registro** y volver a cargarlos después.
  Limitación: los datos viven en ese celular/navegador; **no se comparten entre dispositivos** y
  pueden borrarse si se limpia el navegador.

- **Base de datos central en la nube (opcional, siguiente paso):** para que varios celulares
  compartan los mismos registros se necesita un backend. Opciones gratuitas que funcionan con
  este sitio estático: **Firebase (Firestore)** o **Supabase**. Es una integración pequeña que
  se puede agregar sin cambiar la estructura del proyecto.

## Estructura

```
cemenquin-inventario/
├── index.html      ← la aplicación completa (HTML + CSS + JS + catálogo + imágenes)
├── README.md
└── .gitignore
```

## Notas técnicas

- Sin dependencias ni build: es HTML/CSS/JS puro. Carga fuentes de Google con respaldo del sistema.
- El catálogo y las imágenes de producto están embebidos en base64 para funcionar sin conexión.
- Las fotos de evidencia se redimensionan (máx. ~1100 px, JPEG) antes de guardarse.
- La cámara y el almacenamiento local requieren contexto seguro (`https://` o `localhost`);
  por eso se recomienda la versión publicada en Pages.

---
© Comercial Cemenquin S.A. de C.V. — Uso interno.
