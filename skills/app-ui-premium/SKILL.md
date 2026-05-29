# app-ui-premium — Premium Application UI Stack v1.0
# Knowledge skill for WebOS. Produces premium single-file HTML apps/dashboards.
# Complements ui-ux-pro-max (landings) with app-specific patterns.
# Use when: dashboard, CRM, tool, panel, admin, SPA, app, sistema.
# Does NOT replace cinematic landing patterns — ADDS a new category.

## 100% CAPACITY — MANDATORY
Every output MUST use ALL components below. No partial deliveries.
- Every interaction MUST be functional (filters filter, modals reset, nav renders pages).
- Every visual pattern MUST be applied (metric lines, shadows, noise, glow checkboxes).
- If the quality gate has a checkbox, it SHIPS. No exceptions. No "simplified version".
- SUMAR VALOR, NUNCA RESTAR.

---

## WHEN TO LOAD THIS SKILL

Load when the request matches ANY of:
- dashboard, panel, admin, CRM, sistema, herramienta, tool, app
- Single-page application, SPA, data-driven
- Tables, forms, sidebar navigation, CRUD
- "quiero un sistema para...", "necesito gestionar..."

DO NOT load for: landing page, sitio web, portfolio, ecommerce storefront, marketing page.
Those use ui-ux-pro-max instead.

---

## STEP 0 — APP DESIGN TOKENS

Before writing code, define these tokens:

```
APP_TOKENS:
  palette_mode: [warm-dark|cool-dark|warm-light]
  accent: [gold|blue|green|purple|red|custom]
  density: [compact|comfortable|spacious]
  complexity: [simple-crud|multi-module|full-dashboard]
  charts: [none|chart-js|minimal-custom]
  persistence: [localStorage|none|indexedDB]
  navigation: [sidebar-collapsible|sidebar-fixed|top-tabs|bottom-tabs]
```

---

## PALETTE SYSTEM — WARM DARK (default for apps)

```css
:root {
  /* === Backgrounds === */
  --app-bg: #090908;
  --app-surface: linear-gradient(135deg, rgba(20,19,18,0.96), rgba(13,12,12,0.98));
  --app-surface-hover: linear-gradient(135deg, rgba(26,24,22,0.96), rgba(16,15,14,0.98));
  --app-metric: linear-gradient(135deg, rgba(22,20,18,0.97), rgba(12,11,11,0.99));
  --app-input-bg: rgba(8,8,7,0.8);
  --app-modal-backdrop: rgba(0,0,0,0.7);

  /* === Accent (gold default — override per project) === */
  --accent: #d4a832;
  --accent-light: #f0c84a;
  --accent-glow: rgba(212,168,50,0.14);
  --accent-bg: rgba(212,168,50,0.07);

  /* === Borders === */
  --border: rgba(212,168,50,0.14);
  --border-subtle: rgba(255,255,255,0.04);
  --border-strong: rgba(212,168,50,0.3);

  /* === Text hierarchy === */
  --text-primary: #e8e6de;
  --text-secondary: #7a7870;
  --text-tertiary: #424038;
  --text-accent: #d4a832;

  /* === Semantic === */
  --color-success: #3d8a5a;
  --color-danger: #b84848;
  --color-info: #3d6aaa;
  --color-purple: #7a4ab8;
  --color-amber: #c89b3c;
  --color-grey: #3a3830;

  /* === Radii === */
  --radius-card: 14px;
  --radius-sm: 9px;
  --radius-pill: 20px;

  /* === Shadows === */
  --shadow-card: 0 0 0 1px rgba(0,0,0,0.3), 0 2px 8px rgba(0,0,0,0.45);
  --shadow-input: inset 0 1px 4px rgba(0,0,0,0.5), inset 0 0 0 1px rgba(0,0,0,0.3);
  --shadow-modal: 0 25px 60px rgba(0,0,0,0.6), 0 0 0 1px rgba(212,168,50,0.1);
}
```

### COOL-DARK Variant (override for tech/SaaS apps)
```css
:root {
  --app-bg: #060608;
  --accent: #3d8aff;
  --accent-light: #6aadff;
  --accent-glow: rgba(61,138,255,0.14);
  --accent-bg: rgba(61,138,255,0.07);
  --border: rgba(61,138,255,0.14);
  --text-primary: #e2e4ea;
  --text-secondary: #6a7080;
}
```

---

## TYPOGRAPHY — APP STACK

```css
@import url('https://fonts.googleapis.com/css2?family=Barlow:wght@400;500;600;700;900&family=Barlow+Condensed:wght@700;900&display=swap');

/* Page titles */
.page-title {
  font-family: 'Barlow Condensed', sans-serif;
  font-weight: 900;
  font-size: 26px;
  text-transform: uppercase;
  letter-spacing: -0.01em;
  color: var(--text-primary);
}

/* Metric numbers */
.metric-value {
  font-family: 'Barlow Condensed', sans-serif;
  font-weight: 900;
  font-size: 32px;
  color: var(--text-primary);
  text-shadow: 0 1px 4px rgba(0,0,0,0.5);
}

/* Body text */
body {
  font-family: 'Barlow', sans-serif;
  font-weight: 400;
  color: var(--text-primary);
  -webkit-font-smoothing: antialiased;
}

/* Labels, small text */
.label {
  font-family: 'Barlow', sans-serif;
  font-weight: 600;
  font-size: 11px;
  text-transform: uppercase;
  letter-spacing: 0.04em;
  color: var(--text-secondary);
}
```

---

## BACKGROUND ATMOSPHERE (app-level — subtle, not cinematic)

```css
body {
  background: var(--app-bg);
  position: relative;
}
body::before {
  content: '';
  position: fixed; inset: 0; z-index: 0; pointer-events: none;
  background:
    radial-gradient(ellipse 600px 400px at 20% 30%, rgba(212,168,50,0.04), transparent),
    radial-gradient(ellipse 500px 500px at 80% 70%, rgba(212,168,50,0.03), transparent),
    radial-gradient(ellipse 900px 600px at 50% 50%, rgba(0,0,0,0.4), transparent);
}
```

### SVG Noise Texture (for sidebar or surfaces)
```css
.noise-surface::after {
  content: '';
  position: absolute; inset: 0; pointer-events: none; z-index: 1;
  opacity: 0.035;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.65' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E");
}
```

---

## COMPONENT: COLLAPSIBLE SIDEBAR

```css
.sidebar {
  position: fixed; top: 0; left: 0; height: 100vh;
  width: 48px; /* collapsed */
  background: linear-gradient(180deg, #0f0e0d, #0a0908);
  border-right: 1px solid var(--border-subtle);
  transition: width 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  z-index: 100;
  overflow: hidden;
  display: flex; flex-direction: column;
}
.sidebar:hover { width: 216px; }

/* Logo */
.sidebar .logo {
  width: 32px; height: 32px;
  border-radius: 50%;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  margin: 12px auto 8px;
}
.sidebar:hover .logo { width: 52px; height: 52px; }

/* Brand text (hidden when collapsed) */
.sidebar .brand-text {
  max-height: 0; opacity: 0; overflow: hidden;
  transition: max-height 0.3s ease, opacity 0.25s ease;
  text-align: center; padding: 0 12px;
}
.sidebar:hover .brand-text { max-height: 60px; opacity: 1; }

/* Section labels */
.sidebar .section-label {
  font-size: 9px; font-weight: 700; text-transform: uppercase;
  letter-spacing: 0.08em; color: var(--text-tertiary);
  padding: 16px 14px 4px; max-height: 0; opacity: 0; overflow: hidden;
  transition: max-height 0.3s ease, opacity 0.2s ease;
}
.sidebar:hover .section-label { max-height: 40px; opacity: 1; }

/* Nav items */
.nav-item {
  display: flex; align-items: center; gap: 10px;
  padding: 8px 14px; cursor: pointer;
  border-radius: var(--radius-sm);
  margin: 1px 6px;
  transition: background 0.2s;
}
.nav-item:hover { background: rgba(212,168,50,0.06); }
.nav-item.active { background: rgba(212,168,50,0.1); }
.nav-item.active .nav-dot { background: var(--accent); box-shadow: 0 0 6px var(--accent-glow); }

.nav-dot {
  width: 6px; height: 6px; min-width: 6px;
  border-radius: 50%; background: var(--text-tertiary);
  transition: background 0.2s, box-shadow 0.2s;
}

.nav-text {
  font-size: 13px; font-weight: 500; color: var(--text-secondary);
  white-space: nowrap;
  max-width: 0; opacity: 0; overflow: hidden;
  transition: max-width 0.3s cubic-bezier(0.4, 0, 0.2, 1), opacity 0.25s ease;
}
.sidebar:hover .nav-text { max-width: 180px; opacity: 1; }
.nav-item.active .nav-text { color: var(--text-primary); }

/* Main content offset */
.app-content {
  margin-left: 48px;
  padding: 24px 28px;
  transition: margin-left 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}
```

---

## COMPONENT: METRIC CARDS

```css
.metric-card {
  background: var(--app-metric);
  border-radius: var(--radius-card);
  padding: 20px 22px;
  position: relative;
  box-shadow: var(--shadow-card);
  overflow: hidden;
}
/* Top highlight line (light catch) */
.metric-card::before {
  content: '';
  position: absolute; top: 0; left: 10%; right: 10%;
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(255,255,255,0.08), transparent);
}
/* Bottom accent line */
.metric-card::after {
  content: '';
  position: absolute; bottom: 0; left: 15%; right: 15%;
  height: 2px;
  background: linear-gradient(90deg, transparent, var(--accent), transparent);
  opacity: 0.6;
}
```

### Metric Grid Layout
```css
.metrics-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 16px;
  margin-bottom: 24px;
}
```

---

## COMPONENT: SURFACE CARDS (content containers)

```css
.card {
  background: var(--app-surface);
  border: 1px solid var(--border);
  border-radius: var(--radius-card);
  padding: 24px;
  box-shadow: var(--shadow-card);
}
.card:hover {
  background: var(--app-surface-hover);
  border-color: var(--border-strong);
}
```

---

## COMPONENT: FORMS & INPUTS

```css
.input, .select, .textarea {
  width: 100%;
  background: var(--app-input-bg);
  border: 1px solid var(--border-subtle);
  border-radius: var(--radius-sm);
  padding: 10px 14px;
  color: var(--text-primary);
  font-family: 'Barlow', sans-serif;
  font-size: 14px;
  box-shadow: var(--shadow-input);
  transition: border-color 0.2s, box-shadow 0.2s;
  outline: none;
}
.input:focus, .select:focus, .textarea:focus {
  border-color: var(--accent);
  box-shadow: var(--shadow-input), 0 0 0 2px rgba(212,168,50,0.1);
}
.input::placeholder { color: var(--text-tertiary); }

.textarea {
  min-height: 80px;
  resize: vertical;
}

/* Input label */
.field-label {
  display: block;
  font-size: 12px; font-weight: 600;
  color: var(--text-secondary);
  margin-bottom: 6px;
  text-transform: uppercase;
  letter-spacing: 0.03em;
}

/* Input group (label + input) */
.field-group {
  margin-bottom: 16px;
}
```

### Premium Checkbox (glow when checked)
```css
.checkbox-wrap {
  display: flex; align-items: center; gap: 10px;
  cursor: pointer; padding: 6px 0;
}
.checkbox-custom {
  width: 18px; height: 18px; min-width: 18px;
  border-radius: 5px;
  background: rgba(8,8,7,0.9);
  border: 1px solid rgba(255,255,255,0.08);
  box-shadow: inset 0 1px 3px rgba(0,0,0,0.5);
  display: flex; align-items: center; justify-content: center;
  transition: all 0.2s;
}
.checkbox-wrap input:checked + .checkbox-custom {
  background: var(--accent);
  border-color: var(--accent-light);
  box-shadow: 0 0 8px rgba(212,168,50,0.4), inset 0 1px 2px rgba(255,255,255,0.2);
}
.checkbox-wrap input:checked + .checkbox-custom::after {
  content: '✓';
  font-size: 11px; font-weight: 900;
  color: #090908;
}
.checkbox-wrap input { display: none; }
.checkbox-label {
  font-size: 14px; color: var(--text-primary);
}
.checkbox-wrap input:checked ~ .checkbox-label {
  text-decoration: line-through;
  color: var(--text-secondary);
}
```

---

## COMPONENT: TABLES

```css
.table-wrap {
  overflow-x: auto;
  border-radius: var(--radius-card);
  border: 1px solid var(--border);
}
table {
  width: 100%;
  border-collapse: collapse;
  font-size: 13px;
}
th {
  text-align: left;
  padding: 12px 16px;
  font-size: 11px; font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.04em;
  color: var(--text-tertiary);
  background: rgba(12,11,10,0.6);
  border-bottom: 1px solid var(--border);
}
td {
  padding: 12px 16px;
  color: var(--text-primary);
  border-bottom: 1px solid rgba(255,255,255,0.03);
  vertical-align: middle;
}
tr:hover td {
  background: rgba(212,168,50,0.03);
}
/* Truncated cell */
.cell-truncate {
  max-width: 200px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

/* Avatar chip in table */
.avatar-chip {
  width: 28px; height: 28px;
  border-radius: 50%;
  display: inline-flex; align-items: center; justify-content: center;
  font-size: 10px; font-weight: 700;
  color: #fff;
  margin-right: 8px;
  vertical-align: middle;
}

/* Delete button in table row */
.btn-delete {
  width: 24px; height: 24px;
  border-radius: 50%;
  border: none;
  background: rgba(184,72,72,0.1);
  color: var(--color-danger);
  cursor: pointer;
  font-size: 12px;
  transition: background 0.2s;
}
.btn-delete:hover {
  background: rgba(184,72,72,0.25);
}
```

---

## COMPONENT: BADGES

```css
/* Base badge */
[class*="badge-"] {
  display: inline-block;
  font-size: 9px; font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.04em;
  padding: 3px 8px;
  border-radius: var(--radius-pill);
}
.badge-gold { background: var(--accent-bg); color: var(--accent-light); border: 1px solid rgba(212,168,50,0.15); }
.badge-green { background: rgba(61,138,90,0.1); color: #5cb87a; border: 1px solid rgba(61,138,90,0.15); }
.badge-red { background: rgba(184,72,72,0.1); color: #d06060; border: 1px solid rgba(184,72,72,0.15); }
.badge-blue { background: rgba(61,106,170,0.1); color: #6a9fd4; border: 1px solid rgba(61,106,170,0.15); }
.badge-amber { background: rgba(200,155,60,0.1); color: #d4a832; border: 1px solid rgba(200,155,60,0.15); }
.badge-purple { background: rgba(122,74,184,0.1); color: #a070d4; border: 1px solid rgba(122,74,184,0.15); }
.badge-grey { background: rgba(58,56,48,0.3); color: var(--text-secondary); border: 1px solid rgba(255,255,255,0.06); }

/* Special badges (inline in table headers) */
.badge-api {
  font-size: 8px; padding: 2px 6px;
  background: rgba(61,106,170,0.12);
  color: #6a9fd4;
  border-radius: var(--radius-pill);
  border: 1px solid rgba(61,106,170,0.2);
}
.badge-api::before {
  content: '';
  display: inline-block;
  width: 5px; height: 5px;
  border-radius: 50%;
  background: #3d6aaa;
  margin-right: 4px;
  vertical-align: middle;
}
.badge-scraped {
  background: rgba(122,74,184,0.12);
  color: #a070d4;
  border-color: rgba(122,74,184,0.2);
}
.badge-scraped::before { background: #7a4ab8; }
```

---

## COMPONENT: MODALS

```css
.modal-overlay {
  position: fixed; inset: 0;
  background: var(--app-modal-backdrop);
  backdrop-filter: blur(4px);
  z-index: 1000;
  display: flex; align-items: center; justify-content: center;
  opacity: 0; pointer-events: none;
  transition: opacity 0.25s ease;
}
.modal-overlay.active {
  opacity: 1; pointer-events: auto;
}
.modal {
  background: linear-gradient(135deg, rgba(22,20,18,0.98), rgba(12,11,10,0.99));
  border: 1px solid var(--border);
  border-radius: var(--radius-card);
  padding: 28px;
  width: 90%; max-width: 520px;
  max-height: 85vh; overflow-y: auto;
  box-shadow: var(--shadow-modal);
  transform: translateY(20px) scale(0.97);
  transition: transform 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}
.modal-overlay.active .modal {
  transform: translateY(0) scale(1);
}
.modal-title {
  font-family: 'Barlow Condensed', sans-serif;
  font-weight: 900; font-size: 20px;
  text-transform: uppercase;
  margin-bottom: 20px;
  color: var(--text-primary);
}

/* Close on click outside */
/* JS: overlay.onclick = (e) => { if (e.target === overlay) closeModal(); } */
```

### Modal Form Grid (2-column on wide, 1-column on narrow)
```css
.modal-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 12px;
}
.modal-grid .full-width { grid-column: 1 / -1; }
```

---

## COMPONENT: TOAST NOTIFICATIONS

```css
.toast-container {
  position: fixed; bottom: 24px; right: 24px;
  z-index: 2000;
  display: flex; flex-direction: column; gap: 8px;
}
.toast {
  background: linear-gradient(135deg, rgba(20,19,17,0.97), rgba(12,11,10,0.99));
  border: 1px solid rgba(212,168,50,0.25);
  border-radius: var(--radius-sm);
  padding: 12px 18px;
  font-size: 13px; color: var(--text-primary);
  box-shadow: 0 4px 16px rgba(0,0,0,0.4);
  animation: toastIn 0.3s ease-out, toastOut 0.3s ease-in 1.9s forwards;
}
@keyframes toastIn { from { opacity: 0; transform: translateX(30px); } to { opacity: 1; transform: translateX(0); } }
@keyframes toastOut { from { opacity: 1; transform: translateX(0); } to { opacity: 0; transform: translateX(30px); } }
```

```js
function toast(msg) {
  const c = document.querySelector('.toast-container') || (() => {
    const d = document.createElement('div');
    d.className = 'toast-container';
    document.body.appendChild(d);
    return d;
  })();
  const t = document.createElement('div');
  t.className = 'toast';
  t.textContent = msg;
  c.appendChild(t);
  setTimeout(() => t.remove(), 2200);
}
```

---

## COMPONENT: PROGRESS BARS

```css
.progress-bar {
  width: 100%; height: 8px;
  background: rgba(8,8,7,0.8);
  border-radius: 4px;
  overflow: hidden;
  box-shadow: inset 0 1px 3px rgba(0,0,0,0.4);
}
.progress-fill {
  height: 100%;
  background: linear-gradient(90deg, var(--accent), var(--accent-light));
  border-radius: 4px;
  box-shadow: 0 0 10px rgba(212,168,50,0.4);
  transition: width 0.6s cubic-bezier(0.4, 0, 0.2, 1);
}
```

---

## COMPONENT: BUTTONS

```css
.btn {
  font-family: 'Barlow', sans-serif;
  font-weight: 600; font-size: 13px;
  padding: 10px 20px;
  border-radius: var(--radius-sm);
  border: none;
  cursor: pointer;
  transition: all 0.2s;
}
.btn-primary {
  background: linear-gradient(135deg, var(--accent), #b8922a);
  color: #090908;
  box-shadow: 0 2px 8px rgba(212,168,50,0.3);
}
.btn-primary:hover {
  box-shadow: 0 4px 16px rgba(212,168,50,0.4);
  transform: translateY(-1px);
}
.btn-secondary {
  background: transparent;
  border: 1px solid var(--border);
  color: var(--text-secondary);
}
.btn-secondary:hover {
  border-color: var(--accent);
  color: var(--text-primary);
}

/* Tab buttons (filter pills) */
.tab-group {
  display: flex; gap: 4px;
  background: rgba(8,8,7,0.6);
  border-radius: var(--radius-sm);
  padding: 3px;
  border: 1px solid var(--border-subtle);
}
.tab-btn {
  padding: 6px 14px;
  border-radius: 6px;
  font-size: 12px; font-weight: 600;
  color: var(--text-secondary);
  background: transparent;
  border: none; cursor: pointer;
  transition: all 0.2s;
}
.tab-btn.active {
  background: rgba(212,168,50,0.12);
  color: var(--accent-light);
}
```

---

## COMPONENT: CHIPS / TAGS

```css
.chip {
  display: inline-flex; align-items: center; gap: 4px;
  padding: 3px 10px;
  border-radius: var(--radius-pill);
  font-size: 11px; font-weight: 600;
  background: rgba(212,168,50,0.08);
  color: var(--accent-light);
  border: 1px solid rgba(212,168,50,0.15);
}
.chip .chip-remove {
  width: 14px; height: 14px;
  border-radius: 50%;
  display: flex; align-items: center; justify-content: center;
  font-size: 9px;
  background: rgba(184,72,72,0.2);
  color: var(--color-danger);
  cursor: pointer;
  margin-left: 2px;
}
.chip-input-wrap {
  display: flex; flex-wrap: wrap; gap: 6px;
  padding: 8px 12px;
  background: var(--app-input-bg);
  border: 1px solid var(--border-subtle);
  border-radius: var(--radius-sm);
  box-shadow: var(--shadow-input);
  min-height: 40px; align-items: center;
}
.chip-input-wrap input {
  border: none; background: transparent;
  color: var(--text-primary); outline: none;
  font-size: 13px; flex: 1; min-width: 80px;
}
```

---

## COMPONENT: CHART.JS DARK THEME

```js
/* Chart.js configuration for dark premium apps */
function createDarkChart(ctx, type, labels, datasets) {
  return new Chart(ctx, {
    type: type,
    data: { labels, datasets },
    options: {
      responsive: true,
      maintainAspectRatio: false,
      plugins: {
        legend: { display: false },
        tooltip: {
          backgroundColor: 'rgba(20,19,17,0.95)',
          borderColor: 'rgba(212,168,50,0.2)',
          borderWidth: 1,
          titleColor: '#e8e6de',
          bodyColor: '#7a7870',
          cornerRadius: 8,
          padding: 12
        }
      },
      scales: {
        x: {
          grid: { color: 'rgba(255,255,255,0.03)', drawBorder: false },
          ticks: { color: '#7a7870', font: { family: 'Barlow', size: 11 } }
        },
        y: {
          grid: { color: 'rgba(255,255,255,0.03)', drawBorder: false },
          ticks: { color: '#7a7870', font: { family: 'Barlow', size: 11 } }
        }
      }
    }
  });
}

/* Standard bar chart colors */
const chartColors = {
  income: { bg: 'rgba(212,168,50,0.3)', border: '#d4a832' },
  expense: { bg: 'rgba(184,72,72,0.3)', border: '#b84848' },
  neutral: { bg: 'rgba(122,120,112,0.3)', border: '#7a7870' }
};
```

### CDN (add in `<head>`)
```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.js"></script>
```

---

## STATE MANAGEMENT PATTERN (localStorage)

```js
/* === Data Layer === */
function ld(k, d) {
  try { const v = localStorage.getItem(k); return v ? JSON.parse(v) : d; }
  catch { return d; }
}
function sv(k, v) {
  try { localStorage.setItem(k, JSON.stringify(v)); }
  catch { console.warn('Storage full'); }
}

/* === App State Object === */
// Single source of truth. Synced on every mutation.
const S = {};
function initState(schema) {
  // schema = { key: 'storageKey', default: [] }
  schema.forEach(({ key, store, def }) => {
    S[key] = ld(store, def);
  });
}
function save(key, store) {
  sv(store, S[key]);
}

/* === Export / Import === */
function exportData(allKeys) {
  const data = {};
  allKeys.forEach(k => { data[k] = localStorage.getItem(k); });
  const blob = new Blob([JSON.stringify(data, null, 2)], { type: 'application/json' });
  const url = URL.createObjectURL(blob);
  const a = document.createElement('a');
  a.href = url;
  a.download = `backup-${new Date().toISOString().split('T')[0]}.json`;
  a.click();
  URL.revokeObjectURL(url);
  toast('Datos exportados');
}
function importData(file, allKeys, onDone) {
  const reader = new FileReader();
  reader.onload = (e) => {
    try {
      const data = JSON.parse(e.target.result);
      allKeys.forEach(k => {
        if (data[k] !== undefined) localStorage.setItem(k, data[k]);
      });
      onDone();
      toast('Datos importados');
    } catch { toast('Error: archivo inválido'); }
  };
  reader.readAsText(file);
}
```

---

## NAVIGATION PATTERN (SPA routing)

```js
function nav(pageId, clickedEl) {
  // Hide all pages
  document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
  // Show target
  const target = document.getElementById('page-' + pageId);
  if (target) target.classList.add('active');
  // Update nav
  document.querySelectorAll('.nav-item').forEach(n => n.classList.remove('active'));
  if (clickedEl) clickedEl.classList.add('active');
  // Call render function if exists
  if (window['render_' + pageId]) window['render_' + pageId]();
}
```

```css
.page { display: none; }
.page.active { display: block; }
```

---

## SCROLLBAR (custom — minimal)

```css
::-webkit-scrollbar { width: 3px; }
::-webkit-scrollbar-track { background: transparent; }
::-webkit-scrollbar-thumb { background: rgba(212,168,50,0.15); border-radius: 3px; }
::-webkit-scrollbar-thumb:hover { background: rgba(212,168,50,0.3); }
```

---

## RESPONSIVE BREAKPOINTS

```css
/* Tablet — stack metric grid to 2 columns */
@media (max-width: 1024px) {
  .metrics-grid { grid-template-columns: repeat(2, 1fr); }
  .modal { max-width: 90%; padding: 20px; }
}
/* Mobile — sidebar becomes bottom bar or hamburger */
@media (max-width: 768px) {
  .sidebar { display: none; }
  .app-content { margin-left: 0; padding: 16px; }
  .metrics-grid { grid-template-columns: 1fr; }
  .modal-grid { grid-template-columns: 1fr; }
  table { font-size: 12px; }
  th, td { padding: 8px 10px; }
}
```

---

## QUALITY GATE — APP UI

**Structure:**
- [ ] Single HTML file, no external deps besides CDN
- [ ] Responsive (375px / 768px / 1440px)
- [ ] No JS errors in console
- [ ] All data persists in localStorage via ld()/sv()
- [ ] Export/Import functional

**Visual Premium:**
- [ ] Warm-dark bg with subtle radial gradient accents
- [ ] SVG noise texture on sidebar
- [ ] Multi-layer shadows on cards (not flat)
- [ ] Highlight line (top) + accent line (bottom) on metric cards
- [ ] Custom scrollbar (3px, themed)
- [ ] All badges use semantic color system

**Interaction:**
- [ ] Sidebar collapses/expands smoothly (cubic-bezier 0.3s)
- [ ] Modals animate in (translateY + scale)
- [ ] Toast notifications appear/disappear with slide
- [ ] Inputs have focus glow effect
- [ ] Checkboxes have checked glow
- [ ] Confirm before destructive actions

**Data:**
- [ ] State object S synced with localStorage on every mutation
- [ ] Export produces valid .json backup
- [ ] Import restores all state and re-renders
- [ ] Each module has independent render function
- [ ] Filters work in combination (type + time)

---

## CDN STACK (for app-type pages)

```html
<!-- Typography -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Barlow:wght@400;500;600;700;900&family=Barlow+Condensed:wght@700;900&display=swap" rel="stylesheet">
<!-- Charts (if needed) -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.js"></script>
```

NOTE: App UI does NOT use GSAP/Lenis/ScrollTrigger (those are for cinematic landings).
CSS transitions + minimal JS are sufficient for app interactions.
This keeps the file lighter and avoids animation overkill in utility-focused UIs.

---

## TEMPLATE SCAFFOLD (minimal app starting point)

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>{App Name}</title>
  <!-- CDN here -->
  <style>/* Full CSS from tokens + components above */</style>
</head>
<body>
  <div class="sidebar noise-surface">
    <!-- Logo, brand, nav items -->
  </div>
  <main class="app-content">
    <!-- Pages (display:none, .active shows) -->
    <div id="page-dashboard" class="page active">...</div>
    <div id="page-module2" class="page">...</div>
  </main>
  <div class="modal-overlay" id="modal">
    <div class="modal">...</div>
  </div>
  <div class="toast-container"></div>
  <script>
    // State init, nav(), render functions, ld(), sv(), toast()
  </script>
</body>
</html>
```

---

## INTEGRATION WITH WEBOS AGENT

This skill is loaded AUTOMATICALLY by web-architect.agent.md when:
- Request type = app/dashboard/tool/CRM/panel/sistema
- User mentions: gestionar, administrar, módulos, CRUD, data, tabla

When loaded, the agent:
1. Skips cinematic landing sections (no preloader, no horizontal scroll, no parallax)
2. Uses app tokens (warm-dark) instead of cinematic tokens (cool-dark)
3. Structures output as sidebar + pages instead of scroll sections
4. Prioritizes data patterns (tables, forms, charts) over motion patterns
