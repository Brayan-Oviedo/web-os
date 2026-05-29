# WebOS — Tu Diseñador Web Premium con IA

<div align="center">

**Un prompt. Una página completa. Nivel agencia €2000+.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Works with](https://img.shields.io/badge/Works%20with-Copilot%20%7C%20Claude%20%7C%20Cursor-blue)]()
[![Version](https://img.shields.io/badge/version-3.1.0-green)]()

</div>

---

## Requisitos

| Requisito | Detalle |
|-----------|---------|
| **IA compatible** | GitHub Copilot (VS Code), Claude Code, Cursor, ChatGPT, Open WebUI, o cualquier LLM que acepte system prompts |
| **Editor** | VS Code (recomendado), Cursor, o terminal con Claude Code |
| **Modelo mínimo** | GPT-4o, Claude Sonnet 3.5+, o equivalente (modelos pequeños no siguen instrucciones complejas) |
| **Internet** | Sí — el HTML generado usa CDNs (GSAP, Google Fonts, Unsplash) |
| **Programación** | NO necesitas saber código. Solo describir lo que quieres |
| **Instalación** | Cero. No requiere Node.js, npm, ni ninguna dependencia local |
| **Sistema operativo** | Windows, macOS, Linux — cualquiera |
| **Hosting** | El HTML funciona en cualquier hosting: Netlify, Vercel, GitHub Pages, o simplemente abrir el archivo |

### Lo que NO necesitas:
- ❌ No necesitas saber HTML/CSS/JS
- ❌ No necesitas instalar nada (ni Node, ni Python, ni Docker)
- ❌ No necesitas pagar (es MIT, gratuito para siempre)
- ❌ No necesitas experiencia en diseño
- ❌ No necesitas configurar nada manualmente (la IA lo detecta sola)

---

## El Problema

Crear una landing page o dashboard premium toma **días de trabajo**:
- Buscar inspiración, copiar patrones, ajustar animaciones...
- Contratar un diseñador: €500–€2000 por página
- Usar templates: se ven genéricos, iguales a 10,000 sitios más
- Pedirle a una IA sin contexto: produce HTML de 2015, sin animaciones, sin alma

**Resultado**: pierdes tiempo, dinero, o te conformas con algo mediocre.

---

## La Solución

**WebOS** convierte cualquier IA en un diseñador web de nivel agencia premium.

No es un template. No es un framework. Es un **sistema de conocimiento** (1,929 líneas de reglas de diseño profesional) que la IA lee y aplica automáticamente.

```
Tú escribes: "Landing para pizzería premium estilo oscuro cinematográfico"

La IA produce: HTML completo con GSAP, scroll animations, parallax,
               imágenes reales, tipografía premium, responsive, 13 secciones,
               cada una con su propia animación única. Listo para producción.
```

---

## Resultados Reales

| Sin WebOS | Con WebOS |
|-----------|-----------|
| Fade-in genérico en todo | Clip-path reveals, blur-to-sharp, 3D tilt, magnetic buttons |
| Bootstrap/Tailwind básico | Dark cinematic con grain, volumetric lighting, parallax layers |
| Placeholder images | Imágenes reales de Unsplash auto-seleccionadas |
| 3-4 secciones simples | 13 secciones con animaciones únicas por sección |
| "Se ve como template" | "¿Quién te diseñó esto? ¿Cuánto costó?" |

---

## Compatibilidad

| Plataforma | Configuración | Tiempo |
|------------|---------------|--------|
| **GitHub Copilot** (VS Code) | Automática — lee `.github/copilot-instructions.md` | 0 seg |
| **Claude Code** | Automática — lee `CLAUDE.md` | 0 seg |
| **Cursor** | Automática — lee `.cursorrules` | 0 seg |
| **ChatGPT / Open WebUI / cualquier otra** | Copiar contenido de `agents/web-architect.agent.md` como system prompt | 30 seg |

---

## Configuración (menos de 1 minuto)

### Paso 1 — Clonar

```bash
git clone https://github.com/Brayan-Oviedo/web-os.git
```

### Paso 2 — Abrir tu proyecto con tu IA favorita

**Si usas GitHub Copilot, Claude Code, o Cursor**: no hay paso 2. Ya funciona. La IA detecta los archivos de instrucciones automáticamente.

**Si usas otra IA** (ChatGPT, Open WebUI, LM Studio, etc.):
1. Copia el contenido de `agents/web-architect.agent.md` en el system prompt
2. Para landings, añade también `skills/ui-ux-pro-max/SKILL.md`
3. Para dashboards, añade `skills/app-ui-premium/SKILL.md`

### Paso 3 — Pedir lo que necesitas

```
Hazme una landing page para [tu proyecto/negocio]
```

Eso es todo. La IA sabe qué hacer.

---

## Qué Puede Crear

### Landing Pages Cinematográficas
- Dark premium por defecto (override a light si lo pides)
- GSAP + ScrollTrigger + Lenis smooth scroll
- 13 secciones obligatorias con animación única cada una
- Parallax multicapa, custom cursor, film grain
- Counter animations, magnetic buttons, horizontal scroll
- Tipografía: Bebas Neue + Space Grotesk + Inter
- Imágenes reales de Unsplash (no placeholders)

### Dashboards y Apps Premium
- Sistema warm-dark con sidebar colapsable
- Metric cards, tablas, formularios, modales, toasts
- Chart.js con tema oscuro integrado
- Persistencia localStorage (export/import incluido)
- SPA routing sin frameworks — vanilla JS puro
- Tipografía: Barlow + Barlow Condensed

### Ambos generan:
- **Un solo archivo HTML** — sin build, sin dependencias, sin npm install
- **100% responsive** — móvil, tablet, desktop
- **Cero errores en consola**
- **Listo para producción** — abre el archivo y funciona

---

## Ejemplos de Prompts

```
Landing page para marca de sneakers premium, estilo Adidas x Foot Locker
```

```
Dashboard para gestionar clientes de una agencia de marketing, con métricas y gráficos
```

```
Página de producto para audífonos inalámbricos, hero cinematográfico con spotlight
```

```
Portfolio de arquitecto, estilo editorial minimalista con galería horizontal
```

```
SaaS landing para app de meditación, audiencia millennials, colores cálidos
```

```
Panel admin para inventario de tienda, CRUD completo con filtros y export
```

---

## Estructura del Proyecto

```
web-os/
├── .github/copilot-instructions.md  ← GitHub Copilot (auto)
├── CLAUDE.md                        ← Claude Code (auto)
├── .cursorrules                     ← Cursor (auto)
├── agents/
│   └── web-architect.agent.md       ← Cerebro principal (312 líneas)
├── skills/
│   ├── ui-ux-pro-max/SKILL.md      ← Sistema cinematic para landings (639 líneas)
│   └── app-ui-premium/SKILL.md     ← Sistema UI para apps (978 líneas)
├── examples/                        ← Demos funcionales de referencia
│   ├── demo-landing-cinematic.html
│   └── demo-app-dashboard.html
└── output/                          ← Aquí se guardan tus páginas generadas
```

---

## Stack Técnico (todo via CDN, zero install)

**Para Landings:**
| Tecnología | Uso |
|------------|-----|
| GSAP 3.12 + ScrollTrigger | Animaciones cinematográficas |
| Lenis 1.1 | Smooth scroll premium |
| Google Fonts | Bebas Neue, Space Grotesk, Inter |
| Unsplash | Imágenes reales auto-sourced |

**Para Apps:**
| Tecnología | Uso |
|------------|-----|
| Chart.js 4.4 | Gráficos con tema dark |
| Google Fonts | Barlow, Barlow Condensed |
| localStorage | Persistencia de datos |
| Vanilla JS | SPA routing, state management |

---

## Reglas de Calidad (aplicadas automáticamente)

La IA verifica cada output contra un quality gate:

- ✅ Spacing controlado (max 6vh entre secciones — nunca "mucho espacio negro")
- ✅ Performance (quickTo en cursor, grain estático, scroll debounced)
- ✅ Variedad obligatoria (cada sección animación diferente)
- ✅ Anti-patterns bloqueados (no particles entre secciones, no `transition: all`, no fade-up repetido)
- ✅ Premium real: clip-path, 3D tilt, counters, blur reveals, magnetic buttons, letter-spacing animations

---

## FAQ

**¿Necesito saber programar?**
No. Solo necesitas describir lo que quieres en lenguaje natural.

**¿Funciona en español e inglés?**
Sí. Pide en cualquier idioma.

**¿Puedo usar el HTML generado en producción?**
Sí. Cada archivo es production-ready. Súbelo a cualquier hosting (Netlify, Vercel, GitHub Pages, etc.).

**¿Puedo modificar el output?**
Claro. Es HTML/CSS/JS estándar. Edita lo que quieras.

**¿Funciona sin internet?**
El sistema de instrucciones sí. Pero el HTML generado usa CDNs (GSAP, fonts). Para offline, descarga esas dependencias.

**¿Puedo combinarlo con frameworks (React, Next.js, Astro)?**
Sí. Pídele el formato que quieras en tu prompt. El default es single-file HTML por simplicidad.

---

## Contribuir

PRs bienvenidos. Si descubres un patrón premium nuevo o una mejora al quality gate, abre un issue o PR.

---

## Licencia

MIT — Úsalo como quieras. Comercial, personal, educativo. Sin restricciones.

---

<div align="center">

**Hecho por [RiseOS](https://github.com/Brayan-Oviedo) — Extraído como recurso gratuito para la comunidad.**

⭐ Si te sirve, deja una estrella. Ayuda a que más gente lo descubra.

</div>
