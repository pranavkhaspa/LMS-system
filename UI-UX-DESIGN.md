# UI/UX Design System

A complete, copy-pasteable design system extracted from the **Course Compass LMS**. This document is the single source of truth for colors, typography, spacing, motion, and component patterns. Drop it into any new project and you get the same visual language.

> **Style:** Dark-first · Glassmorphic · Neon-accented · Gradient-mesh · Aurora background

---

## 1. Design Philosophy

| Principle | Meaning |
|---|---|
| **Dark by default** | Dark surface reduces eye strain for long learning sessions and makes neon accents pop. |
| **Glassmorphism** | Layered translucency + `backdrop-blur` separates surfaces without hard borders. |
| **Gradient mesh** | Soft radial gradients in the background give depth without distraction. |
| **Neon accents** | Cyan / violet / blue used sparingly — never as fills, always as focus. |
| **Motion as feedback** | Hover, focus, and state transitions are 200–500ms ease-out. Nothing bouncy, nothing slow. |
| **Type hierarchy** | Display + Body + Mono. Poppins for impact, Inter for reading, JetBrains Mono for code. |

---

## 2. Color Tokens

All colors are defined as **HSL components** in `:root` so Tailwind's `hsl(var(--token))` pattern works.

### 2.1 Core palette

```css
:root {
  /* ── Surfaces ── */
  --background:        229 63% 5%;     /* #070A14 — deep navy */
  --foreground:        0   0%  91%;    /* #E8E8E8 — body text */
  --card:              225 67% 9%;     /* #0E1424 — card surface */
  --card-foreground:   0   0%  91%;
  --popover:           225 67% 9%;
  --popover-foreground:0   0%  91%;

  /* ── Brand ── */
  --primary:           189 94% 43%;    /* #06B6D4 — cyan */
  --primary-foreground:0   0%  100%;
  --secondary:         258 90% 66%;    /* #8B5CF6 — violet */
  --secondary-foreground:0 0% 100%;
  --accent:            217 91% 60%;    /* #3B82F6 — blue */
  --accent-foreground: 0   0%  100%;

  /* ── Neutrals ── */
  --muted:             222 30% 14%;    /* #1A2238 */
  --muted-foreground:  215 16% 65%;    /* #9BA8BC */
  --border:            222 30% 18%;
  --input:             222 30% 18%;
  --ring:              189 94% 43%;

  /* ── Semantic ── */
  --destructive:       0   84% 60%;
  --destructive-foreground: 0 0% 98%;

  /* ── Extended ── */
  --navy:              222 47% 11%;
  --navy-deep:         229 63% 5%;
  --orange:            16  100% 60%;   /* #FF6633 — brand orange */
  --teal:              175 100% 35%;
}
```

### 2.2 Hex quick-reference

| Token | HSL | HEX | Use |
|---|---|---|---|
| Primary | `189 94% 43%` | `#06B6D4` | CTAs, focus rings, links |
| Secondary | `258 90% 66%` | `#8B5CF6` | Secondary CTAs, highlights |
| Accent | `217 91% 60%` | `#3B82F6` | Info, charts |
| Background | `229 63% 5%` | `#070A14` | App shell |
| Card | `225 67% 9%` | `#0E1424` | Elevated surfaces |
| Muted | `222 30% 14%` | `#1A2238` | Inactive, dividers |
| Foreground | `0 0% 91%` | `#E8E8E8` | Body text |
| Orange | `16 100% 60%` | `#FF6633` | Brand mark, urgent CTAs |

### 2.3 Tailwind config

```ts
// tailwind.config.ts
colors: {
  border:   "hsl(var(--border))",
  input:    "hsl(var(--input))",
  ring:     "hsl(var(--ring))",
  background:    "hsl(var(--background))",
  foreground:    "hsl(var(--foreground))",
  primary:   { DEFAULT: "hsl(var(--primary))",   foreground: "hsl(var(--primary-foreground))" },
  secondary: { DEFAULT: "hsl(var(--secondary))", foreground: "hsl(var(--secondary-foreground))" },
  destructive:{ DEFAULT: "hsl(var(--destructive))", foreground: "hsl(var(--destructive-foreground))" },
  muted:     { DEFAULT: "hsl(var(--muted))",     foreground: "hsl(var(--muted-foreground))" },
  accent:    { DEFAULT: "hsl(var(--accent))",    foreground: "hsl(var(--accent-foreground))" },
  popover:   { DEFAULT: "hsl(var(--popover))",   foreground: "hsl(var(--popover-foreground))" },
  card:      { DEFAULT: "hsl(var(--card))",      foreground: "hsl(var(--card-foreground))" },
  navy:      "hsl(var(--navy))",
  "navy-deep":"hsl(var(--navy-deep))",
  orange:    "hsl(var(--orange))",
  teal:      "hsl(var(--teal))",
}
```

---

## 3. Typography

```css
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700;800&family=Inter:wght@300;400;500;600;700&family=JetBrains+Mono:wght@400;500&display=swap');
```

| Role | Family | Weights | Tailwind class |
|---|---|---|---|
| Display (h1–h6) | **Poppins** | 400–800 | `font-display` |
| Body (paragraphs, UI) | **Inter** | 300–700 | `font-body` |
| Mono (code, snippets) | **JetBrains Mono** | 400–500 | `font-mono` |

### 3.1 Type scale

| Token | Size | Line-height | Weight | Use |
|---|---|---|---|---|
| `text-display-2xl` | 4.5rem (72px) | 1.1 | 700 | Hero |
| `text-display-xl` | 3.75rem (60px) | 1.1 | 700 | Section hero |
| `text-display-lg` | 3rem (48px) | 1.15 | 700 | Page title |
| `text-display-md` | 2.25rem (36px) | 1.2 | 600 | Card title |
| `text-display-sm` | 1.5rem (24px) | 1.3 | 600 | Subhead |
| `text-body-lg` | 1.125rem (18px) | 1.6 | 400 | Lead |
| `text-body` | 1rem (16px) | 1.6 | 400 | Body |
| `text-body-sm` | 0.875rem (14px) | 1.5 | 400 | Caption |
| `text-caption` | 0.75rem (12px) | 1.4 | 500 | Tag, label |

### 3.2 Global rules

```css
body {
  @apply bg-background text-foreground font-body antialiased;
  background-image: radial-gradient(circle at 50% -20%, hsl(var(--primary) / 0.15), transparent 60%);
  background-attachment: fixed;
}
h1, h2, h3, h4, h5, h6 { @apply font-display; }
code, pre { @apply font-mono; }
```

---

## 4. Spacing, Radius, Shadows

### 4.1 Spacing scale
Use the default Tailwind scale: `0, 1, 2, 3, 4, 6, 8, 12, 16, 20, 24, 32, 40, 48, 64` (in 0.25rem units).

Recommended rhythm:
- **Section padding:** `py-16 md:py-24`
- **Container padding:** `px-4 sm:px-6 lg:px-8`
- **Card padding:** `p-6` (compact) · `p-8` (spacious)
- **Stack gap:** `space-y-4` (tight) · `space-y-6` (default) · `space-y-8` (loose)

### 4.2 Border radius

```css
--radius: 0.5rem;          /* 8px — default */
```

| Token | Value | Use |
|---|---|---|
| `rounded-sm` | 4px | Badges, chips |
| `rounded-md` | 6px | Inputs, small buttons |
| `rounded-lg` | 8px | Default — cards, buttons |
| `rounded-xl` | 12px | Feature cards |
| `rounded-2xl` | 16px | Hero cards, course cards |
| `rounded-3xl` | 24px | Modals, drawers |
| `rounded-full` | ∞ | Pills, avatars, circular icons |

### 4.3 Shadows & glows

```css
--shadow-glow-primary:   0 0 30px hsl(var(--primary)   / 0.4);
--shadow-glow-secondary: 0 0 25px hsl(var(--secondary) / 0.35);
--shadow-card:           0 10px 30px -10px hsl(229 63% 0% / 0.6);
```

| Class | Effect | Use |
|---|---|---|
| `shadow-sm` | 0 1px 2px rgba(0,0,0,.05) | Inputs |
| `shadow-md` | 0 4px 6px rgba(0,0,0,.1) | Dropdowns |
| `shadow-lg` | 0 10px 15px rgba(0,0,0,.1) | Popovers |
| `shadow-xl` | 0 20px 25px rgba(0,0,0,.15) | Modals |
| `shadow-[var(--shadow-glow-primary)]` | cyan halo | Active CTAs, hovered cards |
| `shadow-[var(--shadow-glow-secondary)]` | violet halo | Secondary accents |

---

## 5. Gradients & Backgrounds

### 5.1 Brand gradients

```css
--gradient-primary:  linear-gradient(135deg, hsl(189 94% 43%), hsl(217 91% 60%));
--gradient-card:     linear-gradient(145deg, hsl(225 67% 12%), hsl(225 67% 7%));
--gradient-mesh:     radial-gradient(at 20% 20%, hsl(189 94% 43% / 0.25) 0px, transparent 50%),
                     radial-gradient(at 80% 0%,  hsl(258 90% 66% / 0.25) 0px, transparent 50%),
                     radial-gradient(at 0% 100%, hsl(217 91% 60% / 0.15) 0px, transparent 50%),
                     radial-gradient(at 80% 80%, hsl(258 90% 66% / 0.2)  0px, transparent 50%);
```

### 5.2 Text gradient

```css
.text-gradient {
  background-image: linear-gradient(135deg, hsl(var(--primary)), hsl(var(--secondary)));
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
}
```

### 5.3 Aurora background (signature)

```css
.aurora-bg { position: absolute; inset: 0; overflow: hidden; pointer-events: none; }
.aurora-bg::after {
  content: ""; position: absolute; inset: -50%;
  background:
    radial-gradient(circle at 50% 50%, hsl(var(--primary)   / 0.15) 0%, transparent 40%),
    radial-gradient(circle at 80% 20%, hsl(var(--secondary) / 0.15) 0%, transparent 40%);
  filter: blur(80px);
  animation: aurora 15s linear infinite;
}
@keyframes aurora { from { transform: rotate(0deg); } to { transform: rotate(360deg); } }
```

---

## 6. Motion

### 6.1 Keyframes

```css
@keyframes accordion-down { from { height: 0 } to { height: var(--radix-accordion-content-height) } }
@keyframes accordion-up   { from { height: var(--radix-accordion-content-height) } to { height: 0 } }
@keyframes fade-in        { 0% { opacity: 0; transform: translateY(10px) } 100% { opacity: 1; transform: translateY(0) } }
@keyframes scale-in       { 0% { opacity: 0; transform: scale(0.95) } 100% { opacity: 1; transform: scale(1) } }
@keyframes slide-in-right{ 0% { transform: translateX(20px); opacity: 0 } 100% { transform: translateX(0); opacity: 1 } }
@keyframes float          { 0%, 100% { transform: translateY(0) } 50% { transform: translateY(-15px) } }
@keyframes mesh           { 0%, 100% { background-position: 0% 0% } 50% { background-position: 100% 100% } }
```

### 6.2 Animation utilities

| Class | Duration | Easing | Use |
|---|---|---|---|
| `animate-fade-in` | 500ms | ease-out | Page enter |
| `animate-scale-in` | 300ms | ease-out | Modal/dialog |
| `animate-slide-in-right` | 400ms | ease-out | Toast, drawer |
| `animate-accordion-down` | 200ms | ease-out | Disclosure |
| `animate-float` | 6s loop | ease-in-out | Hero decorations |
| `animate-mesh` | 20s loop | ease | Background mesh |

### 6.3 Interaction tokens

- **Hover lift:** `hover:-translate-y-0.5` (2px) for buttons, `hover:-translate-y-1` (4px) for cards
- **Glow on hover:** `hover:shadow-[0_0_25px_hsl(var(--primary)/0.6)]`
- **Press feedback:** `active:translate-y-0`
- **Transition:** `transition-all duration-300` is the default

---

## 7. Component Patterns

### 7.1 Glass card

```css
.glass-card {
  @apply bg-card/70 backdrop-blur-xl border border-border rounded-2xl transition-all duration-300;
}
.glass-card:hover {
  @apply border-primary/30 shadow-[0_0_30px_hsl(var(--primary)/0.1)];
}
```

### 7.2 Course card

```css
.course-card {
  @apply bg-card border border-border rounded-2xl overflow-hidden transition-all duration-500 hover:-translate-y-1;
}
.course-card:hover {
  @apply border-primary/50;
  box-shadow: var(--shadow-glow-primary);
}
```

### 7.3 Buttons

**Primary CTA**
```html
<button class="btn-primary">Get started</button>
```
```css
.btn-primary {
  @apply inline-flex items-center justify-center gap-2
         bg-primary text-primary-foreground font-medium
         px-6 py-3 rounded-xl
         transition-all duration-300
         hover:shadow-[0_0_25px_hsl(var(--primary)/0.6)]
         hover:-translate-y-0.5
         active:translate-y-0;
}
```

**Secondary outline**
```html
<button class="btn-outline-teal">Learn more</button>
```
```css
.btn-outline-teal {
  @apply inline-flex items-center justify-center gap-2
         border-2 border-secondary text-secondary font-medium
         px-6 py-3 rounded-xl
         transition-all duration-300
         hover:bg-secondary hover:text-secondary-foreground
         hover:shadow-[0_0_25px_hsl(var(--secondary)/0.4)]
         hover:-translate-y-0.5
         active:translate-y-0;
}
```

### 7.4 Stat pill

```html
<span class="stat-pill">📈 12k learners</span>
```
```css
.stat-pill {
  @apply flex items-center gap-2 px-4 py-2 rounded-full bg-muted/50 border border-border text-sm;
}
```

### 7.5 Inputs

Use shadcn/ui's `Input` primitive with the global focus ring:

```tsx
<Input
  className="bg-input border-border focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 focus-visible:ring-offset-background"
  placeholder="you@example.com"
/>
```

### 7.6 KPI card (admin)

```css
.kpi-card {
  background: var(--card-bg);
  border: 1px solid var(--border-base);
  @apply rounded-xl p-4 transition-colors duration-200;
}
.kpi-card:hover { border-color: var(--border-hover); }
```

### 7.7 Avatar

- Sizes: `h-8 w-8` (sm), `h-10 w-10` (md), `h-16 w-16` (lg)
- Shape: `rounded-full`
- Fallback: 2-letter initials over a `bg-gradient-to-br from-primary to-secondary`

### 7.8 Badge

```tsx
<Badge className="bg-primary/10 text-primary border border-primary/20">New</Badge>
```

---

## 8. Layout Primitives

### 8.1 Container

```html
<div class="container max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
  <!-- page content -->
</div>
```

```ts
container: {
  center: true,
  padding: "2rem",
  screens: { "2xl": "1400px" },
}
```

### 8.2 App shell

```
┌──────────────────────────────────────────┐
│ Navbar (sticky, glass, blur)             │
├──────┬───────────────────────────────────┤
│      │                                   │
│ Side │  Main content (max-w-7xl)         │
│ bar  │                                   │
│      │                                   │
└──────┴───────────────────────────────────┘
```

- Navbar: `h-16`, `sticky top-0 z-40`, `bg-background/80 backdrop-blur-xl border-b border-border`
- Sidebar: `w-64` (collapsed: `w-16`), `bg-card/60 backdrop-blur-xl border-r border-border`

### 8.3 Section spacing

```html
<section class="py-16 md:py-24">
  <div class="container">
    <h2 class="text-display-md font-display font-bold mb-4">Section title</h2>
    <p class="text-body text-muted-foreground max-w-2xl">Supporting copy goes here.</p>
  </div>
</section>
```

---

## 9. Iconography

- **Library:** [lucide-react](https://lucide.dev) (tree-shakable, consistent 24px grid)
- **Stroke width:** 2 (default) · 1.5 (subtle)
- **Default size:** 16, 20, 24
- **Color:** `text-foreground` (default) · `text-primary` (active) · `text-muted-foreground` (inactive)

```tsx
import { BookOpen, Award, Users } from "lucide-react";
<BookOpen className="h-5 w-5 text-primary" />
```

For brand / logos, use a custom SVG with `stroke="%23ff6633"` (the brand orange).

---

## 10. Dark / Light Mode

Default is **dark**. Light mode is opt-in via `html.light` (admin) or `prefers-color-scheme` (fallback).

### 10.1 Token override pattern

```css
html.light {
  --admin-shell-bg:  #f1f5f9;
  --admin-page-bg:   transparent;
  --admin-surface:   #ffffff;
  --admin-text-primary: #0f172a;
  --admin-text-muted:   #64748b;
  --admin-border:    #e2e8f0;
  /* …overrides… */
}
```

### 10.2 Theme provider (React)

```tsx
// context/ThemeProvider.jsx
const [theme, setTheme] = useState<'dark' | 'light'>('dark');
useEffect(() => {
  document.documentElement.classList.toggle('light', theme === 'light');
  document.documentElement.dataset.theme = theme;
}, [theme]);
```

### 10.3 FOUC-free boot

```html
<script>
  (function () {
    var t = localStorage.getItem('theme');
    var light = t === 'light' || (t === 'system' && matchMedia('(prefers-color-scheme: light)').matches);
    if (light) document.documentElement.classList.add('light');
    document.documentElement.dataset.theme = light ? 'light' : 'dark';
  })();
</script>
```

---

## 11. Accessibility

- **Focus ring:** Always visible — `focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 focus-visible:ring-offset-background`
- **Contrast:** Body text on dark surface passes WCAG AA (≥ 4.5:1). Avoid `text-muted-foreground` for primary copy.
- **Motion:** Respect `prefers-reduced-motion` — wrap keyframes in a media query and reduce to instant transitions.
- **Keyboard:** Every interactive element is reachable via Tab; modals trap focus.
- **ARIA:** Use shadcn/ui primitives — Radix handles ARIA correctly out of the box.

---

## 12. Custom Scrollbar

```css
::-webkit-scrollbar { width: 10px; height: 10px; }
::-webkit-scrollbar-track { background: hsl(var(--background)); border-left: 1px solid hsl(var(--border)); }
::-webkit-scrollbar-thumb {
  background: hsl(var(--muted-foreground) / 0.3);
  border-radius: 9999px;
  border: 2px solid hsl(var(--background));
  transition: background 200ms;
}
::-webkit-scrollbar-thumb:hover { background: hsl(var(--primary) / 0.8); }
```

---

## 13. Snippet: A complete hero

```tsx
<section className="relative overflow-hidden">
  <div className="aurora-bg" />
  <div className="container relative z-10 py-24">
    <span className="stat-pill">✨ New cohort starts Monday</span>
    <h1 className="mt-6 text-display-2xl font-display font-bold">
      Learn <span className="text-gradient">anything</span>, faster.
    </h1>
    <p className="mt-4 text-body-lg text-muted-foreground max-w-xl">
      500+ expert-led courses. Personalized paths. Real progress.
    </p>
    <div className="mt-8 flex gap-4">
      <button className="btn-primary">Get started</button>
      <button className="btn-outline-teal">Browse courses</button>
    </div>
  </div>
</section>
```

---

## 14. Project Bootstrap (5-minute setup)

```bash
# 1. Install Tailwind
npm i -D tailwindcss postcss autoprefixer tailwindcss-animate
npx tailwindcss init -p

# 2. Add the design tokens above to src/index.css (:root + html.light)
# 3. Replace tailwind.config.ts colors with the palette from §2.3
# 4. Install shadcn/ui
npx shadcn-ui@latest init
npx shadcn-ui@latest add button card input badge avatar dialog sheet

# 5. Install icons + fonts
npm i lucide-react
# Add the @import url('https://fonts.googleapis.com/...') line to index.css

# 6. Done — you now have the full Course Compass design language
```

---

## 15. Design Tokens Cheat Sheet

```
Primary:   #06B6D4  (cyan)
Secondary: #8B5CF6  (violet)
Accent:    #3B82F6  (blue)
Orange:    #FF6633  (brand)
Background: #070A14 (navy-black)
Card:      #0E1424
Muted:     #1A2238
Border:    #2A3550
Text:      #E8E8E8
Muted fg:  #9BA8BC

Display font: Poppins
Body font:    Inter
Mono font:    JetBrains Mono

Default radius: 8px (rounded-lg)
Default shadow: 0 10px 30px -10px rgba(0,0,0,0.6)
Default transition: 300ms ease-out
```

Use this cheat sheet as a quick reference when building any screen.
