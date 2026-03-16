# Plan de mejora responsive (fase actual)

## Estado actual
- La normalización de nombres para hosting Linux ya quedó aplicada.
- Ahora el foco es responsive y UX móvil.
- **Decisión vigente:** Fase 1 (assets faltantes) queda pospuesta temporalmente; se mantiene `onerror` como fallback hasta completar el banco final de imágenes.

## Hallazgos del análisis
1. **Imágenes/medios faltantes (impacto alto):**
   - No existen carpetas en `public/`: `testimonios`, `talleres`, `logros`, `plan-lector`.
   - Referencias activas en:
     - `src/pages/testimonios.astro`
     - `src/pages/talleres.astro`
     - `src/pages/logros.astro`
     - `src/pages/niveles/primaria.astro`
     - `src/pages/niveles/secundaria.astro`
2. **Imágenes ocultas en móvil por diseño sin fallback visible:**
   - Uso repetido de `hidden md:block` para bloques de imagen absoluta en:
     - `src/components/home/BienvenidosSection.astro`
     - `src/pages/nosotros/bienvenido.astro`
     - `src/pages/nosotros/mision-vision.astro`
     - `src/pages/nosotros/filosofia.astro`
3. **Carruseles con UX móvil débil:**
   - Flechas del hero solo visibles en hover (`src/components/HeroCarousel.astro`), en touch quedan prácticamente ocultas.
   - Dots de testimonios mezclan desktop+mobile en un solo `querySelectorAll`, con riesgo de index incorrecto en móvil (`src/components/home/TestimoniosSection.astro`).
4. **Offsets y alturas rígidas:**
   - Filtros sticky usan `top-16` con navbar alta (`src/pages/talleres.astro`, `src/pages/logros.astro`).
   - Hay muchos bloques con alturas fijas (`h-[400px]`, `h-[450px]`, `h-[650px]`), lo que complica móviles pequeños.
5. **Rutas internas potencialmente inválidas (afecta UX):**
   - CTAs en home apuntan a rutas no existentes: `/admisiones`, `/modelo-educativo`, `/instalaciones` (`src/pages/index.astro`).

## Plan de ejecución recomendado
1. **Fase 1: asegurar contenido visible (pospuesta)**
   - Resolver assets faltantes (subir archivos reales o mapear a existentes).
   - Eliminar dependencia de `onerror` como mecanismo principal.
2. **Fase 2: corregir layout móvil en secciones críticas**
   - Refactor de secciones con imagen lateral absoluta:
     - Mantener versión desktop actual.
     - Agregar bloque de imagen móvil (`md:hidden`) con `aspect-*` estable.
3. **Fase 3: carruseles y navegación táctil**
   - Hero: mostrar flechas en móvil sin hover y ampliar áreas táctiles.
   - Testimonios: separar dots por breakpoint o filtrar dots visibles antes de bindear índices.
4. **Fase 4: spacing y tipografía adaptativa**
   - Ajustar `top-*` de sticky según altura real del navbar.
   - Reemplazar alturas rígidas por `aspect-ratio` + `min-h` razonable.
   - Escalar títulos `text-5xl`/`text-6xl` con tamaños base menores en móvil.
5. **Fase 5: QA responsive formal**
   - Validación por breakpoints: `320`, `375`, `390`, `414`, `768`, `1024`, `1280`.
   - Probar portrait/landscape, menú móvil, carruseles, sticky, y tap targets.
   - Build final y smoke test de rutas clave.

## Criterios de aceptación
- No hay imágenes críticas desaparecidas en móvil.
- No hay contenido tapado por navbar, sidebar o WhatsApp float.
- Carruseles navegables por touch con feedback claro.
- Sin scroll horizontal no intencional.
- Build de producción en verde.
