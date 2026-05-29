# WebOS — Tu Diseñador Web Premium con IA

<div align="center">

**Un prompt. Una página completa. Nivel agencia €2000+.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Works with](https://img.shields.io/badge/Works%20with-Copilot%20%7C%20Claude%20%7C%20Cursor-blue)]()
[![Version](https://img.shields.io/badge/version-3.1.0-green)]()

[Instalación](#-instalación) · [Cómo Funciona](#-cómo-funciona) · [Ejemplos](#-ejemplos-de-prompts) · [FAQ](#-faq)

</div>

---

## 🚀 Instalación

### Opción A — Clonar (recomendado)
```bash
git clone https://github.com/Brayan-Oviedo/web-os.git
```

### Opción B — Dentro de un proyecto existente
```bash
cd tu-proyecto/
git clone https://github.com/Brayan-Oviedo/web-os.git .webos
```

### Opción C — Descargar ZIP (sin Git)
1. Click en el botón verde **"Code"** arriba → **"Download ZIP"**
2. Descomprime en tu carpeta de trabajo

> **Repo público.** No necesitas cuenta de GitHub, ni token, ni autenticación. Cualquiera puede clonar o descargar.

---

## ⚡ Uso Inmediato (según tu IA)

| Tu IA | Qué hacer | Tiempo |
|-------|-----------|--------|
| **GitHub Copilot** | Abre la carpeta en VS Code → Copilot Chat → Agent mode → escribe tu prompt | 0 config |
| **Claude Code** | `cd web-os && claude` → escribe tu prompt | 0 config |
| **Cursor** | Abre la carpeta en Cursor → Chat (Cmd+L) → escribe tu prompt | 0 config |
| **ChatGPT / Open WebUI / otra** | Copia `agents/web-architect.agent.md` como system prompt + skill según tipo | 30 seg |

**¿Por qué 0 config?** Cada IA tiene su archivo de auto-detección:
- GitHub Copilot lee `.github/copilot-instructions.md` automáticamente
- Claude Code lee `CLAUDE.md` automáticamente
- Cursor lee `.cursorrules` automáticamente

**Para IAs sin auto-detección (ChatGPT, Open WebUI, LM Studio, etc.):**
1. Copia el contenido de `agents/web-architect.agent.md` en tu system prompt o custom instructions
2. Si vas a hacer una **landing page** → pega también `skills/ui-ux-pro-max/SKILL.md`
3. Si vas a hacer un **dashboard/app** → pega también `skills/app-ui-premium/SKILL.md`

---

## 💬 Tu Primer Prompt

Una vez configurado, solo escribe:

```
Hazme una landing page para [describe tu negocio/proyecto]
```

La IA genera un archivo HTML completo, production-ready, con animaciones cinematográficas, imágenes reales, y responsive. Lo guardará en `output/`.

---

## 🎯 Qué Problema Resuelve

| El dolor | La realidad |
|----------|-------------|
| Contratar diseñador web | €500–€2000 por página. Semanas de espera. |
| Usar templates | Genéricos. Iguales a 10,000 sitios. Sin personalidad. |
| Pedirle a la IA sin contexto | HTML de 2015. Sin animaciones. Sin scroll effects. Feo. |
| Hacerlo tú mismo | Días buscando inspiración, copiando snippets, ajustando CSS. |

**WebOS elimina todo eso.** Es un sistema de conocimiento (1,929 líneas de reglas profesionales) que la IA lee y aplica. El resultado: páginas que parecen de agencia premium.

---

## 📊 Antes vs Después

| Sin WebOS | Con WebOS |
|-----------|-----------|
| Fade-in genérico en todo | Clip-path reveals, blur-to-sharp, 3D tilt, magnetic buttons |
| Bootstrap/Tailwind plano | Dark cinematic con grain, volumetric lighting, parallax layers |
| "Image placeholder" | Imágenes reales de Unsplash auto-seleccionadas por la IA |
| 3-4 secciones simples | 13 secciones con animación única por cada una |
| "Se ve como template" | "¿Quién te diseñó esto? ¿Cuánto te costó?" |

---

## 🔧 Cómo Funciona

WebOS no genera código por sí solo. **Potencia a tu IA** con conocimiento experto:

```
┌─────────────┐     ┌──────────────────┐     ┌─────────────────┐
│  Tu Prompt  │ ──→ │  IA + WebOS      │ ──→ │  HTML Premium   │
│  (1 frase)  │     │  (1,929 reglas)  │     │  (producción)   │
└─────────────┘     └──────────────────┘     └─────────────────┘
```

La IA detecta automáticamente qué tipo de página quieres:
- **Landing/web/portfolio** → aplica sistema cinematic (GSAP, parallax, 13 secciones)
- **Dashboard/app/admin** → aplica sistema de app (sidebar, tablas, charts, modals)

---

## 📋 Requisitos

| Requisito | Detalle |
|-----------|---------|
| **IA** | Copilot, Claude Code, Cursor, ChatGPT, Open WebUI, o cualquier LLM |
| **Modelo mínimo** | GPT-4o, Claude Sonnet 3.5+, o equivalente |
| **Saber programar** | NO. Solo describir lo que quieres |
| **Instalar algo** | NO. Cero dependencias |
| **Internet** | Sí (el HTML usa CDNs: GSAP, fonts, imágenes) |
| **Sistema operativo** | Windows, macOS, Linux |
| **Hosting** | Cualquiera: Netlify, Vercel, GitHub Pages, o abrir el .html directo |

---

## 🎨 Qué Puede Crear

### Landing Pages Cinematográficas
- Dark premium por defecto (light si lo pides)
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

### Todo output es:
- **Un solo archivo HTML** — sin build, sin npm, sin dependencias locales
- **100% responsive** — móvil, tablet, desktop
- **Cero errores en consola**
- **Producción-ready** — abre el archivo y funciona

---

## 💬 Ejemplos de Prompts

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

## 📁 Estructura

```
web-os/
├── .github/copilot-instructions.md  ← Auto-carga en GitHub Copilot
├── CLAUDE.md                        ← Auto-carga en Claude Code
├── .cursorrules                     ← Auto-carga en Cursor
├── agents/
│   └── web-architect.agent.md       ← Cerebro principal (367 líneas de reglas)
├── skills/
│   ├── ui-ux-pro-max/SKILL.md      ← Sistema cinematic para landings (639 líneas)
│   └── app-ui-premium/SKILL.md     ← Sistema UI para apps/dashboards (978 líneas)
├── examples/                        ← Demos funcionales de referencia
│   ├── demo-landing-cinematic.html
│   └── demo-app-dashboard.html
└── output/                          ← Aquí se guardan tus páginas generadas
```

---

## ⚙️ Stack Técnico (todo via CDN, zero install)

**Landings:**
| Tecnología | Uso |
|------------|-----|
| GSAP 3.12 + ScrollTrigger | Animaciones cinematográficas scroll-driven |
| Lenis 1.1 | Smooth scroll premium |
| Google Fonts | Bebas Neue, Space Grotesk, Inter, JetBrains Mono |
| Unsplash | Imágenes reales auto-sourced |

**Apps/Dashboards:**
| Tecnología | Uso |
|------------|-----|
| Chart.js 4.4 | Gráficos con tema dark |
| Google Fonts | Barlow, Barlow Condensed |
| localStorage | Persistencia + export/import |
| Vanilla JS | SPA routing, state management |

---

## ✅ Quality Gate (automático)

La IA verifica cada output contra estas reglas — no entrega hasta que TODO pase:

- Spacing controlado (max 6vh — nunca "mucho espacio negro")
- Performance (quickTo cursor, grain estático, scroll debounced)
- Variedad obligatoria (cada sección animación diferente)
- Anti-patterns bloqueados (no particles random, no `transition: all`, no fade-up repetido)
- Premium real: clip-path, 3D tilt, counters, blur reveals, magnetic buttons
- 100% capacity: NUNCA entrega versión "simplificada" — siempre full quality

---

## ❓ FAQ

**¿Necesito saber programar?**
No. Solo describe lo que quieres en lenguaje natural.

**¿Funciona en español e inglés?**
Sí. Cualquier idioma.

**¿Puedo usar el HTML en producción?**
Sí. Súbelo a Netlify, Vercel, GitHub Pages, o cualquier hosting.

**¿Puedo modificar el output?**
Claro. Es HTML/CSS/JS estándar.

**¿Funciona sin internet?**
Las instrucciones sí. El HTML generado usa CDNs (GSAP, fonts). Para offline, descarga esas dependencias.

**¿Puedo pedir React/Next.js/Astro?**
Sí. Especifícalo en tu prompt. Default es single-file HTML.

**¿Qué modelo de IA necesito mínimo?**
GPT-4o, Claude Sonnet 3.5+, o equivalente. Modelos pequeños (GPT-3.5, Llama 7B) no siguen instrucciones complejas bien.

---

## 🤝 Contribuir

PRs bienvenidos. Si descubres un patrón premium o mejora al quality gate, abre un issue o PR.

---

## 📄 Licencia

MIT — Úsalo como quieras. Comercial, personal, educativo. Sin restricciones.

---

<div align="center">

**Hecho por [RiseOS](https://github.com/Brayan-Oviedo) — Recurso gratuito para la comunidad.**

⭐ Si te sirve, deja una estrella. Ayuda a que más gente lo descubra.

</div>
