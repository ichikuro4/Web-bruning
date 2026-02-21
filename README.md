# Brüning School — Sitio Web Oficial

Sitio web institucional del **Colegio Brüning School** (Trujillo, Perú), construido con [Astro 5](https://astro.build) y [Tailwind CSS 4](https://tailwindcss.com). Incluye optimizaciones de SEO, rendimiento (Core Web Vitals) y arquitectura modular por páginas.

---

## ✅ Requisitos previos

- [Node.js](https://nodejs.org/) **v18.17 o superior** (recomendado: v20 LTS)
- [npm](https://www.npmjs.com/) v9 o superior (viene incluido con Node.js)

Verifica tu versión:
```sh
node -v
npm -v
```

---

## 🚀 Inicio rápido

```sh
# 1. Instala las dependencias
npm install

# 2. Inicia el servidor de desarrollo
npm run dev
```

El sitio estará disponible en **http://localhost:4321**

---

## 🧞 Comandos

Todos los comandos se ejecutan desde la raíz del proyecto:

| Comando           | Acción                                              |
| :---------------- | :-------------------------------------------------- |
| `npm install`     | Instala las dependencias                            |
| `npm run dev`     | Inicia el servidor local en `localhost:4321`        |
| `npm run build`   | Genera el sitio estático en `./dist/`               |
| `npm run preview` | Previsualiza el build antes de desplegar            |

---

## 📁 Estructura del proyecto

```text
web-bruningS/
├── public/                        # Archivos estáticos (imágenes, video, fuentes)
│   ├── fonts/                     # Fuentes locales (Panton, Montserrat, Raleway)
│   ├── Galeria/                   # Fotos de galería por categoría
│   ├── Estandares/                # Logos de certificaciones (Cambridge, IBEC)
│   ├── Universidades/             # Logos de universidades de destino
│   ├── Logos/                     # Logos internos del colegio
│   ├── Video_Carrusel.mp4         # Video del hero carousel
│   └── PORTADA.webp               # Imagen OG principal
│
├── src/
│   ├── components/
│   │   ├── home/                  # Secciones exclusivas de la página de inicio
│   │   │   ├── StatsSection.astro
│   │   │   ├── BienvenidosSection.astro
│   │   │   ├── UniversidadesSection.astro
│   │   │   ├── EstandaresSection.astro
│   │   │   ├── TestimoniosSection.astro
│   │   │   └── GaleriaSection.astro
│   │   ├── HeroCarousel.astro     # Carousel hero con video + slides
│   │   ├── Navbar.astro           # Barra de navegación
│   │   ├── Sidebar.astro          # Menú lateral (mobile)
│   │   ├── Footer.astro           # Pie de página
│   │   ├── NivelCard.astro        # Tarjeta de nivel educativo
│   │   └── WhatsAppFloat.astro    # Botón flotante de WhatsApp
│   │
│   ├── layouts/
│   │   └── Layout.astro           # Layout principal (SEO, fuentes, scripts globales)
│   │
│   ├── pages/                     # Rutas del sitio (una carpeta = una sección)
│   │   ├── index.astro            # Página de inicio (/)
│   │   ├── contacto.astro         # /contacto
│   │   ├── logros.astro           # /logros
│   │   ├── talleres.astro         # /talleres
│   │   ├── testimonios.astro      # /testimonios
│   │   ├── informacion-2025.astro # /informacion-2025
│   │   ├── informacion-2026.astro # /informacion-2026
│   │   ├── admision/
│   │   │   ├── costos.astro       # /admision/costos
│   │   │   ├── formas-pago.astro  # /admision/formas-pago
│   │   │   └── matricula.astro    # /admision/matricula
│   │   ├── nosotros/
│   │   │   ├── bienvenido.astro   # /nosotros/bienvenido
│   │   │   ├── campus.astro       # /nosotros/campus
│   │   │   ├── filosofia.astro    # /nosotros/filosofia
│   │   │   └── mision-vision.astro
│   │   └── niveles/
│   │       ├── primaria.astro     # /niveles/primaria
│   │       └── secundaria.astro   # /niveles/secundaria
│   │
│   └── styles/
│       └── global.css             # Estilos globales, fuentes @font-face, Tailwind
│
├── astro.config.mjs               # Configuración de Astro (sitemap, Tailwind, build)
├── package.json
└── tsconfig.json
```

---

## 🛠️ Tecnologías utilizadas

| Tecnología | Versión | Uso |
| :--------- | :------ | :-- |
| [Astro](https://astro.build) | 5.x | Framework principal (SSG) |
| [Tailwind CSS](https://tailwindcss.com) | 4.x | Estilos utilitarios |
| [@astrojs/sitemap](https://docs.astro.build/en/guides/integrations-guide/sitemap/) | 3.x | Generación automática de sitemap |

---

## ⚙️ Configuración destacada

- **`site`**: `https://bruningschool.edu.pe` — necesario para el sitemap y URLs canónicas.
- **`inlineStylesheets: 'auto'`**: Astro decide automáticamente si inlinear CSS o cargarlo como archivo externo según el tamaño.
- **Fuentes locales**: Panton, Montserrat y Raleway se sirven desde `public/fonts/` (sin dependencia de Google Fonts).
- **SEO completo**: cada página tiene `<title>`, `<meta description>`, Open Graph, Twitter Card y URL canónica configurados en `Layout.astro`.
- **JSON-LD**: datos estructurados de tipo `School` incluidos en el `<head>` para motores de búsqueda.
- **Sitemap**: generado automáticamente en `/sitemap-index.xml` al hacer build.

---

## 🌐 Despliegue

El sitio genera archivos estáticos en `./dist/` al ejecutar `npm run build`. Puede desplegarse en cualquier hosting estático:

- [Netlify](https://netlify.com)
- [Vercel](https://vercel.com)
- [GitHub Pages](https://pages.github.com)
- Hosting tradicional (subir contenido de `dist/` por FTP)
