# Game Day by Grimau Brothers — Landing de conversión

Landing single-file en `index.html`. HTML + CSS + JS embebidos, sin dependencias externas. Mobile-first, responsive (3 breakpoints: 600/800/900px), accesible (WCAG AA), optimizada para conversión y SEO.

---

## 1. Qué tienes que personalizar antes de publicar

Busca estos placeholders en `index.html` y sustitúyelos.

### A. Dominio real
Reemplaza todas las apariciones de `https://gamedaybygrimau.com/` por tu dominio definitivo en:
- `<link rel="canonical">`
- Open Graph (`og:url`, `og:image`)
- JSON-LD (Organization, sameAs)
- `sitemap.xml` y `robots.txt`

### B. Vídeos (YouTube/Vimeo)
Hay 2 huecos para vídeos. Búscalos por `data-video-id`:
```html
<div class="video-frame" data-video-id="VIDEO_ID_1">
```
Reemplaza `VIDEO_ID_1` por el ID real de YouTube. Por ejemplo, si el vídeo es `https://www.youtube.com/watch?v=abc12345`, el ID es `abc12345`.

Si prefieres Vimeo, sustituye el bloque `.video-placeholder` por:
```html
<iframe src="https://player.vimeo.com/video/TU_ID" title="Game Day" allowfullscreen loading="lazy"></iframe>
```

### C. Imágenes (logo, foto jornada, foto Grimau Brothers)
Sustituye estos bloques placeholder:

- **Logo / marca**: el `<span class="brand-mark">` es un círculo CSS naranja. Si tienes un SVG, sustitúyelo por `<img src="logo.svg" alt="Game Day logo" width="36" height="36">`.
- **Foto jornada** (sección "Qué es"): busca `<!-- PLACEHOLDER: Reemplazar con <img...`. Sustituye el div `.what-media` por `<img src="foto-jornada.jpg" alt="Equipo en jornada Game Day" class="what-media">`.
- **Foto Grimau Brothers**: igual, en sección `.founders-photo`.
- **OG image**: crea una imagen 1200×630px (`og-image.jpg`) y súbela a la raíz.

### D. Formulario — conectar a un backend real
En `index.html`, dentro de `<script>`, busca:
```js
// PLACEHOLDER: aquí integra tu endpoint real
```
Opciones recomendadas (más simples a más complejas):
1. **Formspree** (5 min): cambia `<form>` a `<form action="https://formspree.io/f/TU_ID" method="POST">`. Quita el `ev.preventDefault()` del JS.
2. **Resend / Mailgun via webhook** (15 min): un endpoint serverless (Vercel/Netlify Functions) que reciba el form y mande email.
3. **HubSpot / Pipedrive forms**: embebe el form de tu CRM.

### E. WhatsApp
Reemplaza `34000000000` por tu número real (con prefijo internacional, sin `+`, sin espacios) en los dos enlaces `wa.me`.

### F. Logos de clientes
En la sección `.logos-row` hay 6 placeholders `<span class="logo-ph">`. Sustituye cada uno por `<img src="cliente-X.svg" alt="Nombre cliente" height="28">`.

### G. Testimonios
3 testimonios placeholder en `.testimonial-grid`. Sustituye `Nombre apellido` y `Cargo · Empresa` por los reales.

### H. Redes sociales
En el footer, los enlaces de LinkedIn / Instagram / YouTube apuntan a `#`. Pon las URLs reales y añádelas también al JSON-LD (`sameAs`).

### I. Datos de Schema.org
Verifica el JSON-LD en la cabecera: email de contacto, URL del logo, redes sociales. Tras publicar, pasa la URL por [Rich Results Test](https://search.google.com/test/rich-results) para confirmar que Google lee bien Organization + Service + FAQPage.

---

## 2. Estructura de la landing (secciones)

1. **Nav sticky** — anclas a las secciones + CTA primaria
2. **Hero** — H1 + propuesta de valor + CTA primaria + secundaria + scoreboard de stats
3. **Logos clientes** — prueba social temprana
4. **Problema** — 3 dolores que resolvemos (PAS framework)
5. **Qué es Game Day** — definición + lo que es / lo que no es
6. **Metodología** — 3 fases (vestuario, cuartos, post-partido) + detalle Q1-Q4
7. **Vídeos** — 2 vídeos embed
8. **Casos de uso** — 4 momentos donde Game Day funciona
9. **Formatos** — Half Time (4h) y Full Game (8h) destacado
10. **Founders** — autoridad Grimau Brothers
11. **Testimonios** — prueba social profunda
12. **FAQ** — 7 preguntas que cierran objeciones (también JSON-LD FAQPage)
13. **CTA final + formulario** — conversión principal
14. **Footer** — contacto, legal, redes
15. **Sticky CTA móvil** — WhatsApp + Reservar llamada (solo en móvil)

---

## 3. Patrones de marketing aplicados

- **AIDA**: atención (hero) → interés (qué es + metodología) → deseo (casos, testimonios, founders) → acción (CTA + form).
- **PAS**: problema → agitación → solución, en la sección "El problema" y "Qué es".
- **Anchor pricing**: dos formatos con el Full Game destacado como "Más solicitado".
- **Multiple CTAs**: 5 puntos de conversión a lo largo de la página (nav, hero, formatos, CTA final, sticky móvil).
- **Reducción de fricción**: WhatsApp como alternativa al form, copy del CTA específico ("Reservar llamada de descubrimiento" > "Enviar").
- **Prueba social distribuida**: logos arriba, testimonios al final, badges en founders.
- **Scarcity sutil**: no hay urgencia falsa (esto degrada la marca en B2B premium), pero sí promesa de respuesta en <24h.

---

## 4. SEO aplicado

- **Meta title** optimizado <60 caracteres con keyword principal.
- **Meta description** <160 caracteres con CTA implícito.
- **H1 único** y jerarquía H2/H3 limpia.
- **Open Graph + Twitter Card** completos.
- **JSON-LD**: Organization, Service (con Offers para los 2 formatos), FAQPage.
- **Canonical** definido.
- **Lang=es** declarado.
- **Robots.txt** + **sitemap.xml** creados.
- **Alt text** descriptivo en imágenes (cuando sustituyas placeholders, mantén la práctica).
- **Preconnect** a YouTube/Vimeo para los embeds.
- **Lazy loading** en iframes de vídeo (se cargan al hacer click).
- **Texto semántico**: section, article, nav, header, footer, blockquote, figure.

### Para mejorar SEO post-lanzamiento
- Añade un `/blog` con contenido de marca alrededor de keywords como "team building empresa", "kick off comercial", "facilitación equipos directivos".
- Crea páginas de caso de estudio individuales por cliente.
- Google Business Profile si recibís visitas en oficina.
- Backlinks: medios deportivos, RRHH digitales, asociaciones empresariales.

---

## 5. Performance / accesibilidad

- Sin dependencias externas (todo inline) → 1 sola request HTML.
- Sin imágenes pesadas en el HTML (se cargan al sustituir placeholders).
- Iframes de vídeo con `loading="lazy"`.
- `prefers-reduced-motion: reduce` respetado.
- Contraste WCAG AA verificado (naranja sobre negro: 6.4:1; texto principal sobre blanco: >12:1).
- Áreas de tap >44px en todos los botones.
- `aria-label`, `aria-expanded`, `aria-live` en elementos interactivos.
- Skip link no añadido — si quieres, añade `<a href="#main" class="sr-only">Saltar al contenido</a>` al inicio del body.

---

## 6. Cómo abrir y probar

Localmente, abre el archivo en navegador:
```bash
open index.html
```

O sirve con un server simple para probar el form en condiciones más realistas:
```bash
python3 -m http.server 8080
# Luego abre http://localhost:8080
```

Para validar el HTML: https://validator.w3.org/
Para validar el JSON-LD: https://search.google.com/test/rich-results
Para Lighthouse: Chrome DevTools → Lighthouse → Mobile.
