# ui-ux-pro-max — Cinematic Premium Stack v4
# Mandatory for WebOS. Produces €2000+ level websites.
# anime.js v4 + Motion + Lenis + GSAP-level scroll + Cinematic lighting.
# Industry-adaptive. Dark premium default. Full parallax depth.

---

## STEP 0 — DESIGN SYSTEM (inline — no external scripts)

Before writing code, define these tokens based on the brief:

```
DESIGN_TOKENS:
  industry: [fashion|tech|gaming|saas|food|fitness|luxury|corporate|creative|ecommerce]
  mood: [cinematic|minimal-luxury|editorial|brutalist|futuristic|organic]
  palette_mode: [dark-dominant|light-dominant|mixed]
  accent_color: [from brand or auto-derive]
  lighting_style: [neon-glow|spotlight|ambient|volumetric|gradient-mesh]
  product_presentation: [pedestal|floating|parallax-layers|editorial-grid|immersive]
  animation_intensity: [subtle|medium|dramatic]
```

### Industry Design Patterns:

**Fashion/Clothing** (como Adidas x Foot Locker):
- Products as ART: dramatic spotlight, dark background, reflective floor
- Vertical light beam dividing composition
- Minimal UI — product IS the content
- Hover: product rotates slightly, light shifts
- Scroll: products slide in from sides with stagger, scale from 0.8→1

**Tech/Gaming** (como robot cinematic):
- Full-bleed hero with particle atmosphere
- Glowing elements (eyes, energy trails, UI accents)
- Lens flares, chromatic aberration on scroll
- Scroll: parallax layers (background → midground → foreground)
- Hover: elements pulse, glow intensifies

**Food/Restaurant** (como MOZZA pizzería):
- Product-as-art: food photographed dramatically on PURE BLACK void
- NO table, NO plate, NO context — just the food floating in darkness
- Single product dominates hero (70%+ of viewport)
- Spotlight cenital: light from above making textures pop
- "SCROLL TO TASTE" / "SCROLL TO EXPLORE" — interactive prompt
- Scroll: product pieces separate/reveal (slice pulls, ingredients float up)
- Nav: ultra-minimal, transparent, doesn't compete with product
- Micro-animations: steam rising, cheese stretching (subtle CSS)
- Sections below: ingredients float in parallax, story reveals cinematically

**SaaS/Dashboard**:
- Glassmorphism cards with gradient borders
- Floating UI mockups with depth (transform: perspective)
- Subtle grid pattern background
- Scroll: cards fly in from different directions

**Luxury/Premium** (any product):
- Maximum negative space, editorial typography
- Single focal product with dramatic lighting
- Gold/warm accents on dark
- Scroll: slow reveals, cinematic pacing

**E-commerce Product**:
- Product pedestal (spotlight from above)
- 360° rotation capability
- Reflective surface below product
- Quick color/variant switches with morph

**Architecture/Real Estate**:
- Full-bleed hero photo with Ken Burns effect (slow zoom on scroll)
- Split-screen layouts (image | text)
- Scroll: horizontal gallery of spaces
- Muted luxury palette, serif typography

**Fitness/Sports**:
- High-energy: dynamic angles, bold typography, diagonal lines
- Video background hero with overlay
- Parallax athlete images
- Scroll: stats counter-up, achievement badges fly in

---

## HERO COMPOSITION PATTERNS (choose based on subject)

### Pattern A — Product-as-Art Isolation (MOZZA style)
Product on pure void. Nothing else above fold except minimal nav + scroll prompt.
```
┌──────────────────────────────────┐
│ logo        nav...     [CTA]     │ ← transparent, ultra-thin
│                                  │
│                                  │
│          [PRODUCT IMAGE]         │ ← 60-70% of viewport, centered
│          floating in void        │
│                                  │
│        ↓ SCROLL TO EXPLORE       │ ← animated bounce
└──────────────────────────────────┘
```

### Pattern B — Parallax Layers (Robot/Gaming style)
Multiple z-layers, text above subject, particles throughout.
```
┌──────────────────────────────────┐
│ logo        nav...     [CTA]     │
│  [BACKGROUND - slow parallax]    │
│    [PARTICLES - medium]          │
│      [SUBJECT - faster]          │
│        [TEXT OVERLAY - fixed]    │
│          [CTA BUTTON]           │
└──────────────────────────────────┘
```

### Pattern C — Editorial Split (Luxury/Fashion)
Product one side, text other side. Asymmetric composition.
```
┌──────────────────────────────────┐
│ logo        nav...     [CTA]     │
│                    │             │
│  HEADLINE          │  [PRODUCT] │
│  subtitle          │   rotated  │
│  [CTA]             │   slightly │
│                    │             │
└──────────────────────────────────┘
```

### Pattern D — Full-Bleed Immersive (Events/Cinema)
Subject fills entire screen. Text overlaid with contrast.
```
┌──────────────────────────────────┐
│ [FULL-BLEED IMAGE/VIDEO]         │
│    logo      nav     [CTA]       │
│                                  │
│       MASSIVE HEADLINE           │
│       with glow/shadow           │
│                                  │
│         ↓ SCROLL                 │
└──────────────────────────────────┘
```

---

## CDN STACK (paste in <head>, ALL required)
```html
<!-- Smooth scroll -->
<script src="https://cdn.jsdelivr.net/npm/lenis@1.1.18/dist/lenis.min.js"></script>
<!-- anime.js v4 — dynamic import -->
<script>
  (async () => {
    const { animate, stagger, createDrawable, onScroll, splitText, scrambleText, morphTo } =
      await import('https://esm.sh/animejs@4.4.1');
    window.anime = { animate, stagger, createDrawable, onScroll, splitText, scrambleText, morphTo };
    window.dispatchEvent(new Event('anime-ready'));
  })();
</script>
<!-- Motion (scroll-linked + viewport triggers, hardware-accelerated) -->
<script src="https://cdn.jsdelivr.net/npm/motion@latest/dist/motion.js"></script>
<!-- Lottie player -->
<script src="https://unpkg.com/@lottiefiles/lottie-player@latest/dist/lottie-player.js"></script>
```

---

## ASSETS AUTO-SOURCING (agent must do this, NOT user)

For ANY page, source real visuals automatically:
1. **Product images**: Use `https://images.unsplash.com/photo-{ID}?w=800&q=80` — search topic on unsplash.com
2. **Background textures**: Use `https://images.unsplash.com/photo-{ID}?w=1920&q=80` for atmospheric bg
3. **Icons**: Use Lucide icons CDN `<script src="https://unpkg.com/lucide@latest"></script>`
4. **Video backgrounds**: Use `https://player.vimeo.com/video/{ID}?background=1` or Pexels video embed
5. **3D assets**: Spline community `https://prod.spline.design/{ID}/scene.splinecode`
6. **Lottie animations**: lottiefiles.com free library

**CRITICAL IMAGE RULES for hero/product isolation:**
- For Product-as-Art heroes: ONLY use images with dark/black backgrounds OR transparent PNGs
- NEVER use product images with colored/bright backgrounds on a dark page (the square bg will show)
- If a product photo has a colored background, it CANNOT be used as an isolated floating product
- Search terms for Unsplash: add "dark background" or "black background" or "studio shot dark"
- Elements that animate (rotate, scale) will EXPOSE any background mismatch — test mentally first
- Set hero product `opacity: 0` in HTML, let JS animate it in (prevents flash of unstyled content)

**RULE**: NEVER deliver a page with placeholder boxes or "Image goes here". Always source a real relevant image from Unsplash using descriptive search terms. Use specific Unsplash photo URLs that match the industry.

---

## CINEMATIC LIGHTING SYSTEM (the secret sauce)

### [L1] Spotlight / Volumetric beam
```css
.spotlight {
  position: absolute; top: -20%; left: 50%; transform: translateX(-50%);
  width: 2px; height: 120%;
  background: linear-gradient(to bottom, transparent, var(--accent, #ef4444), transparent);
  box-shadow: 0 0 60px 20px var(--accent-glow, #ef444440), 0 0 120px 40px var(--accent-glow, #ef444420);
  opacity: 0.8;
}
/* Wider cone variant */
.spotlight-cone {
  position: absolute; top: -10%; left: 50%; transform: translateX(-50%);
  width: 0; height: 0;
  border-left: 80px solid transparent; border-right: 80px solid transparent;
  border-top: 600px solid var(--accent-glow, #ffffff08);
  filter: blur(30px);
}
```

### [L2] Neon glow on elements
```css
.neon-text {
  text-shadow: 0 0 7px var(--accent), 0 0 10px var(--accent), 0 0 21px var(--accent),
               0 0 42px var(--accent-raw, #ff0000), 0 0 82px var(--accent-raw, #ff0000);
}
.neon-border {
  box-shadow: inset 0 0 20px var(--accent-glow, #ef444420),
              0 0 20px var(--accent-glow, #ef444420),
              0 0 40px var(--accent-glow, #ef444410);
  border: 1px solid var(--accent-glow, #ef444440);
}
```

### [L3] Reflective floor (for product showcase)
```css
.product-stage {
  position: relative;
}
.product-stage::after {
  content: ''; position: absolute; bottom: 0; left: 0; right: 0;
  height: 50%; transform: scaleY(-1); opacity: 0.3;
  background: inherit;
  mask-image: linear-gradient(to top, rgba(0,0,0,0.5), transparent 60%);
  -webkit-mask-image: linear-gradient(to top, rgba(0,0,0,0.5), transparent 60%);
  filter: blur(2px);
}
/* Alternative: use a gradient overlay below the product */
.reflection-surface {
  background: linear-gradient(to bottom, var(--accent-glow, #ef444415) 0%, transparent 40%);
  position: absolute; bottom: -2px; left: 0; right: 0; height: 200px;
  filter: blur(1px);
}
```

### [L4] Lens flare (on scroll trigger)
```js
// Trigger on scroll reaching hero bottom
anime.animate('.lens-flare', {
  opacity: [0, 0.6, 0],
  x: ['-100%', '200%'],
  scale: [0.5, 1.2, 0.8]
}, { duration: 2000, ease: 'inOutQuad' });
```

### [L5] Particle atmosphere
```js
// Create floating particles for depth
function createParticles(container, count = 30) {
  for (let i = 0; i < count; i++) {
    const p = document.createElement('div');
    p.className = 'particle';
    p.style.cssText = `position:absolute;width:${2+Math.random()*4}px;height:${2+Math.random()*4}px;
      background:var(--accent,#ef4444);border-radius:50%;opacity:${0.1+Math.random()*0.4};
      left:${Math.random()*100}%;top:${Math.random()*100}%;filter:blur(${Math.random()*2}px)`;
    container.appendChild(p);
  }
  anime.animate('.particle', {
    y: () => `${-20 + Math.random() * 40}px`,
    x: () => `${-10 + Math.random() * 20}px`,
    opacity: () => [0.1 + Math.random() * 0.3, 0.05],
    duration: () => 3000 + Math.random() * 4000,
    loop: true, alternate: true,
    delay: anime.stagger(200)
  });
}
```

---

## PARALLAX DEPTH SYSTEM (multi-layer scroll)

### [P1] Full parallax hero (3+ layers)
```html
<section class="parallax-hero" style="position:relative;height:100vh;overflow:hidden">
  <!-- Layer 0: Background (slowest) -->
  <div class="parallax-layer" data-speed="0.2" style="position:absolute;inset:0;z-index:0">
    <img src="..." style="width:100%;height:130%;object-fit:cover;transform:translateY(-15%)">
  </div>
  <!-- Layer 1: Midground elements -->
  <div class="parallax-layer" data-speed="0.5" style="position:absolute;inset:0;z-index:1">
    <!-- Particles, smoke, atmosphere -->
  </div>
  <!-- Layer 2: Foreground / Subject (fastest) -->
  <div class="parallax-layer" data-speed="0.8" style="position:absolute;inset:0;z-index:2">
    <!-- Main product/character -->
  </div>
  <!-- Layer 3: UI / Text (fixed or subtle move) -->
  <div class="parallax-layer" data-speed="1.0" style="position:relative;z-index:3">
    <!-- Headlines, CTAs -->
  </div>
</section>
```
```js
// Parallax scroll engine
window.addEventListener('scroll', () => {
  const scrolled = window.scrollY;
  document.querySelectorAll('.parallax-layer').forEach(layer => {
    const speed = layer.dataset.speed || 0.5;
    layer.style.transform = `translateY(${scrolled * (1 - speed) * 0.5}px)`;
  });
});
```

### [P2] Section parallax (elements move at different rates within a section)
```js
// Each .parallax-el moves at its own data-speed on scroll
anime.onScroll({
  targets: '.parallax-el',
  translateY: (el) => [0, -100 * (el.dataset.speed || 0.3)],
  ease: 'linear'
});
```

### [P3] Horizontal scroll section (product gallery)
```js
// Horizontal scroll for product showcase
const track = document.querySelector('.horizontal-track');
anime.onScroll({
  container: '.horizontal-section',
  targets: track,
  translateX: ['0%', '-60%'],
  ease: 'linear'
});
```

---

## MOTION PATTERNS — paste ALL, every page

### [1] Lenis smooth scroll
```js
const lenis = new Lenis({ lerp: 0.08, smoothWheel: true, orientation: 'vertical' });
function raf(time) { lenis.raf(time); requestAnimationFrame(raf); }
requestAnimationFrame(raf);
```

### [2] Scroll reveal (Motion — hardware-accelerated)
```js
Motion.inView('.reveal', (el) => {
  Motion.animate(el, { opacity: [0, 1], y: [60, 0], scale: [0.95, 1] },
    { duration: 0.8, easing: [0.16, 1, 0.3, 1], delay: +(el.dataset.delay || 0) });
});
```

### [3] Text split entrance — anime.js v4
```js
window.addEventListener('anime-ready', () => {
  // Word-by-word hero headline
  const splitter = anime.splitText('h1', { words: true });
  anime.animate(splitter.words, {
    y: ['110%', '0%'], opacity: [0, 1], rotateX: [90, 0],
    delay: anime.stagger(80), duration: 900, ease: 'outExpo'
  });
  // Scramble for tech/cyber
  if (document.querySelector('.scramble')) {
    anime.scrambleText('.scramble', { duration: 1500, ease: 'outExpo' });
  }
});
```

### [4] SVG shape reveal + draw
```js
window.addEventListener('anime-ready', () => {
  const paths = document.querySelectorAll('svg .draw-path');
  if (paths.length) {
    const drawables = Array.from(paths).map(p => anime.createDrawable(p));
    anime.animate(drawables, { draw: ['0% 0%', '0% 100%'] },
      { duration: 1200, ease: 'inOutExpo', delay: anime.stagger(200) });
  }
});
```

### [5] Magnetic button
```js
document.querySelectorAll('.magnetic').forEach(btn => {
  btn.addEventListener('mousemove', e => {
    const r = btn.getBoundingClientRect();
    Motion.animate(btn, {
      x: (e.clientX - r.left - r.width / 2) * 0.35,
      y: (e.clientY - r.top - r.height / 2) * 0.35
    }, { duration: 0.4, easing: 'ease-out' });
  });
  btn.addEventListener('mouseleave', () =>
    Motion.animate(btn, { x: 0, y: 0 }, { duration: 0.6, easing: [0.34, 1.56, 0.64, 1] }));
});
```

### [6] 3D tilt card
```js
document.querySelectorAll('.tilt').forEach(card => {
  card.style.transformStyle = 'preserve-3d';
  card.style.transition = 'none';
  card.addEventListener('mousemove', e => {
    const r = card.getBoundingClientRect();
    const rotX = (e.clientY - r.top - r.height / 2) / r.height * -14;
    const rotY = (e.clientX - r.left - r.width / 2) / r.width * 14;
    Motion.animate(card, { rotateX: rotX, rotateY: rotY }, { duration: 0.3, easing: 'ease-out' });
  });
  card.addEventListener('mouseleave', () =>
    Motion.animate(card, { rotateX: 0, rotateY: 0 }, { duration: 0.6, easing: [0.34, 1.56, 0.64, 1] }));
});
```

### [7] Cinematic background (replaces basic aurora)
```html
<!-- Dark atmospheric gradient + animated accent lights -->
<div id="cinema-bg" style="position:fixed;inset:0;z-index:0;pointer-events:none;overflow:hidden;background:#050505">
  <!-- Primary accent glow -->
  <div class="bg-orb" style="position:absolute;width:800px;height:800px;border-radius:50%;
    background:radial-gradient(circle,var(--accent-glow,#ef444412),transparent 70%);
    filter:blur(120px);top:-300px;left:50%;transform:translateX(-50%)"></div>
  <!-- Secondary ambient -->
  <div class="bg-orb" style="position:absolute;width:600px;height:600px;border-radius:50%;
    background:radial-gradient(circle,#7c3aed08,transparent 70%);
    filter:blur(100px);bottom:-200px;right:-100px"></div>
  <!-- Grain texture overlay -->
  <div style="position:absolute;inset:0;opacity:0.03;
    background-image:url('data:image/svg+xml,%3Csvg viewBox=%270 0 256 256%27 xmlns=%27http://www.w3.org/2000/svg%27%3E%3Cfilter id=%27noise%27%3E%3CfeTurbulence type=%27fractalNoise%27 baseFrequency=%270.65%27 numOctaves=%273%27 stitchTiles=%27stitch%27/%3E%3C/filter%3E%3Crect width=%27100%25%27 height=%27100%25%27 filter=%27url(%23noise)%27/%3E%3C/svg%3E')"></div>
</div>
<style>
.bg-orb{animation:float 20s ease-in-out infinite alternate}
@keyframes float{0%{transform:translate(0,0) scale(1)}50%{transform:translate(30px,-20px) scale(1.1)}100%{transform:translate(-20px,30px) scale(0.95)}}
</style>
```

### [8] CountUp on scroll
```js
Motion.inView('.counter-wrap', () => {
  document.querySelectorAll('.counter').forEach(el => {
    const t = +el.dataset.target, s = performance.now();
    const tick = now => {
      const p = Math.min((now - s) / 1600, 1), e = 1 - Math.pow(1 - p, 4);
      el.textContent = Math.floor(e * t).toLocaleString() + (el.dataset.suffix || '');
      if (p < 1) requestAnimationFrame(tick);
    };
    requestAnimationFrame(tick);
  });
});
```

### [9] Product showcase entrance (fashion/ecommerce)
```js
// Products slide in from sides with stagger + scale
Motion.inView('.product-grid', (el) => {
  const items = el.querySelectorAll('.product-item');
  items.forEach((item, i) => {
    const fromX = i % 2 === 0 ? -80 : 80;
    Motion.animate(item, {
      opacity: [0, 1], x: [fromX, 0], scale: [0.8, 1], rotateY: [i % 2 === 0 ? -15 : 15, 0]
    }, { duration: 1, easing: [0.16, 1, 0.3, 1], delay: i * 0.15 });
  });
});
```

### [10] Scroll-triggered morph/transform
```js
// Elements morph as user scrolls through section
window.addEventListener('anime-ready', () => {
  anime.onScroll({
    targets: '.morph-on-scroll',
    translateY: [-50, 50],
    scale: [0.9, 1.1],
    rotateZ: [-5, 5],
    opacity: [0.5, 1],
    ease: 'linear'
  });
});
```

### [11] Cursor light follower (adds to atmosphere)
```js
document.addEventListener('mousemove', (e) => {
  const cursor = document.querySelector('.cursor-light');
  if (cursor) {
    cursor.style.left = e.clientX + 'px';
    cursor.style.top = e.clientY + 'px';
  }
});
```
```html
<div class="cursor-light" style="position:fixed;width:400px;height:400px;border-radius:50%;
  background:radial-gradient(circle,var(--accent-glow,#ef444408),transparent 70%);
  pointer-events:none;z-index:1;transform:translate(-50%,-50%);transition:left 0.3s ease-out, top 0.3s ease-out"></div>
```

### [12] Scroll prompt (animated indicator inviting interaction)
```html
<div class="scroll-prompt" style="position:absolute;bottom:8%;left:50%;transform:translateX(-50%);
  display:flex;flex-direction:column;align-items:center;gap:8px;opacity:0.7">
  <span style="font-size:0.75rem;letter-spacing:0.2em;text-transform:uppercase;color:#fff8">SCROLL TO EXPLORE</span>
  <div style="width:1px;height:40px;background:linear-gradient(to bottom,var(--accent,#ef4444),transparent);
    animation:scrollPulse 2s ease-in-out infinite"></div>
</div>
<style>
@keyframes scrollPulse{0%,100%{opacity:0.4;transform:scaleY(1)}50%{opacity:1;transform:scaleY(1.3)}}
</style>
```
```js
// Auto-hide scroll prompt after first scroll
window.addEventListener('scroll', () => {
  const prompt = document.querySelector('.scroll-prompt');
  if (prompt && window.scrollY > 50) {
    Motion.animate(prompt, { opacity: 0, y: 20 }, { duration: 0.5 });
    setTimeout(() => prompt.remove(), 600);
  }
}, { once: true });
```

### [13] Product-as-Art Hero (isolated product, dramatic entry)
```js
// ⚠️ CRITICAL: scroll parallax MUST wait until entry animation completes
// Otherwise scroll overwrites transform mid-animation = visual glitch
let heroAnimDone = false;

window.addEventListener('anime-ready', () => {
  const hero = document.querySelector('.hero-product');
  if (hero) {
    // Start invisible (set opacity:0 in HTML style attr)
    anime.animate(hero, {
      scale: [0.7, 1], opacity: [0, 1], y: [80, 0], rotateZ: [-8, 0]
    }, { duration: 1400, ease: 'outExpo', delay: 400,
      onComplete: () => { heroAnimDone = true; }
    });
  }
});

// Product reacts to scroll — ONLY after entry animation is done
window.addEventListener('scroll', () => {
  const hero = document.querySelector('.hero-product');
  if (hero && heroAnimDone) {
    const scroll = window.scrollY;
    if (scroll < window.innerHeight) {
      const progress = scroll / window.innerHeight;
      hero.style.transform = `translateY(${progress * 60}px) rotate(${progress * -3}deg) scale(${1 - progress * 0.12})`;
      hero.style.opacity = `${1 - progress * 0.8}`;
    }
  }
});
```
**RULE: Never apply scroll/mousemove transforms to an element while its entry animation is still running. Use `onComplete` callback + flag.**

### [14] Product deconstruction on scroll (pieces separate)
```js
// Items marked with .decon-piece separate on scroll (like pizza slices)
window.addEventListener('scroll', () => {
  const section = document.querySelector('.decon-section');
  if (!section) return;
  const rect = section.getBoundingClientRect();
  const progress = Math.max(0, Math.min(1, -rect.top / rect.height));
  document.querySelectorAll('.decon-piece').forEach((piece, i) => {
    const angle = (i / document.querySelectorAll('.decon-piece').length) * 360;
    const rad = angle * Math.PI / 180;
    const distance = progress * 120; // px to spread
    piece.style.transform = `translate(${Math.cos(rad) * distance}px, ${Math.sin(rad) * distance}px) rotate(${progress * 10 * (i % 2 ? 1 : -1)}deg)`;
    piece.style.opacity = 1 - progress * 0.3;
  });
});
```

### [15] Ingredient/element float-in (for food, components)
```js
// Elements float in from random directions and settle into position
Motion.inView('.float-in-section', (el) => {
  el.querySelectorAll('.float-item').forEach((item, i) => {
    const startX = (Math.random() - 0.5) * 200;
    const startY = 100 + Math.random() * 100;
    const startRotate = (Math.random() - 0.5) * 60;
    Motion.animate(item, {
      x: [startX, 0], y: [startY, 0], rotate: [startRotate, 0],
      opacity: [0, 1], scale: [0.5, 1]
    }, { duration: 1.2, easing: [0.16, 1, 0.3, 1], delay: i * 0.12 });
  });
});
```

---

## PAGE STRUCTURE TEMPLATE (dark premium default)

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>{PROJECT}</title>
  <!-- Tailwind -->
  <script src="https://cdn.tailwindcss.com"></script>
  <script>tailwind.config={theme:{extend:{colors:{accent:'var(--accent,#ef4444)'}}}}</script>
  <!-- CDN Stack (from above) -->
  [INSERT CDN STACK HERE]
  <style>
    :root { --accent: #ef4444; --accent-raw: #ef4444; --accent-glow: #ef444430; }
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body { background: #050505; color: #f5f5f5; font-family: 'Inter', system-ui, sans-serif;
           overflow-x: hidden; }
    main { position: relative; z-index: 1; }
    /* Custom scrollbar */
    ::-webkit-scrollbar { width: 6px; }
    ::-webkit-scrollbar-track { background: #111; }
    ::-webkit-scrollbar-thumb { background: var(--accent); border-radius: 3px; }
  </style>
</head>
<body>
  [cinema-bg]
  [cursor-light]
  <main>
    [CONTENT SECTIONS with .reveal, .tilt, .magnetic, .parallax-layer]
  </main>
  <script>[ALL MOTION PATTERNS INITIALIZED]</script>
</body>
</html>
```

---

## MANDATORY CHECKLIST — block delivery if ANY fails
- [ ] Design tokens defined (industry + mood + palette + lighting)
- [ ] Real images sourced (Unsplash/Pexels/Spline — NO placeholders)
- [ ] CDN stack: Lenis + anime.js v4 + Motion + Lottie in `<head>`
- [ ] `#cinema-bg` background present (NOT plain black), `<main>` has `z-index:1`
- [ ] Cinematic lighting: at least 1 of [spotlight|neon-glow|volumetric-beam|gradient-mesh]
- [ ] `splitText('h1')` word entrance on hero
- [ ] ALL sections/cards have class `reveal` with Motion.inView
- [ ] Parallax: at least 2 layers at different scroll speeds in hero
- [ ] Primary CTA: class `magnetic`
- [ ] Cards/products: class `tilt` (3D perspective hover)
- [ ] Stats (if any): `.counter[data-target]` + countUp
- [ ] Product images (if any): dramatic presentation + hover effect
- [ ] Scroll-triggered animations on EVERY section transition (not just fade)
- [ ] Responsive: mobile-first breakpoints, touch-friendly
- [ ] Performance: will-change on animated elements, GPU-accelerated transforms
- [ ] NO generic look — design clearly matches the INDUSTRY tokens
- [ ] NO `transition:all` — explicit properties only, use outExpo/spring/[0.16,1,0.3,1]
- [ ] Page feels like a €2000 website, not a template
