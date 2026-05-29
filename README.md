# WebOS — Premium Web Builder for AI Assistants

> Turn any AI (Claude Code, GitHub Copilot, Cursor, ChatGPT) into a €2000+ web designer.  
> One sentence = cinematic landing page or premium dashboard. Single-file HTML. Zero config.

---

## ⚡ Setup (30 seconds)

### Option A — Clone into your project
```bash
git clone https://github.com/YOUR_USER/webos.git .webos
```

### Option B — Download and drop
Download this repo and place it anywhere in your project.

---

## 🚀 Usage

### GitHub Copilot (VS Code)
1. Place this folder in your project root (or anywhere)
2. Open Copilot Chat → Agent mode
3. Just describe what you want:

```
Hazme una landing page para una pizzería premium estilo MOZZA, dark cinematic
```

Copilot reads `.github/copilot-instructions.md` automatically.

### Claude Code
1. Place this folder in your project root
2. Claude reads `CLAUDE.md` automatically
3. Just ask:

```
Build a SaaS dashboard for a fitness app with metrics, charts, and dark theme
```

### Cursor
1. Place this folder in your project root
2. Cursor reads `.cursorrules` automatically
3. Ask naturally:

```
Landing page para marca de sneakers premium, estilo Adidas x Foot Locker
```

### Any other AI (ChatGPT, Open WebUI, etc.)
1. Copy the content of `agents/web-architect.agent.md` into your system prompt
2. For landings, also paste `skills/ui-ux-pro-max/SKILL.md`
3. For apps/dashboards, paste `skills/app-ui-premium/SKILL.md`

---

## 📁 Structure

```
webos/
├── .github/copilot-instructions.md  ← Auto-loaded by GitHub Copilot
├── CLAUDE.md                        ← Auto-loaded by Claude Code
├── .cursorrules                     ← Auto-loaded by Cursor
├── agents/
│   └── web-architect.agent.md       ← The brain (main agent instructions)
├── skills/
│   ├── ui-ux-pro-max/SKILL.md      ← Cinematic landing page patterns
│   └── app-ui-premium/SKILL.md     ← App/Dashboard UI system
├── examples/                        ← Demo outputs for reference
└── output/                          ← Your generated pages go here
```

---

## 🎯 What It Does

### Landing Pages (cinematic)
- Dark premium aesthetic (€2000+ level)
- GSAP + ScrollTrigger + Lenis smooth scroll
- 13 mandatory sections with unique animations each
- 3D tilt cards, magnetic buttons, counter animations
- Clip-path reveals, blur-to-sharp text, parallax layers
- Real images from Unsplash (auto-sourced)
- Film grain overlay, custom cursor, volumetric lighting

### App/Dashboard UIs
- Warm-dark palette with collapsible sidebar
- Metric cards, tables, forms, modals, toasts
- Chart.js integration (dark theme)
- localStorage persistence (ld/sv pattern)
- Export/Import data backup
- SPA routing without frameworks

---

## 💬 Example Prompts

| Prompt | Result |
|--------|--------|
| "Landing para estudio de arquitectura minimalista" | Dark cinematic, Ken Burns hero, horizontal gallery |
| "Dashboard CRM para agencia de marketing" | Sidebar + metrics + tables + charts + modals |
| "Página de producto para audífonos premium" | Product-as-art hero, spotlight, 3D tilt, parallax |
| "Portfolio de fotógrafo, estilo editorial" | Split layouts, image reveals, smooth scroll |
| "SaaS landing for meditation app, English" | Organic mood, gradient mesh, gentle animations |
| "Panel admin para gestionar inventario" | Full CRUD app with filters, export, responsive |

---

## ⚙️ Tech Stack (all via CDN, zero install)

**Landings:**
- GSAP 3.12 + ScrollTrigger (animations)
- Lenis 1.1 (smooth scroll)
- Google Fonts (Bebas Neue, Space Grotesk, Inter)

**Apps:**
- Barlow + Barlow Condensed (typography)
- Chart.js 4.4 (charts)
- Pure CSS + vanilla JS (no frameworks)

---

## 📋 Quality Standards

Every output passes a quality gate:
- ✅ Single HTML file, production-ready
- ✅ Responsive (375px → 1440px)
- ✅ No console errors
- ✅ Real images (not placeholders)
- ✅ Unique animation per section
- ✅ Performance: quickTo cursor, static grain, debounced scroll
- ✅ No generic templates — every page feels custom

---

## 🆓 License

MIT — Use it however you want. Commercial, personal, whatever.

---

## 🙏 Credits

Built by the RiseOS ecosystem. Extracted as a free standalone tool for the community.
