# Life Stuff Apps — Design System
**Version 1.1 · May 2026**
**Reference implementation: Sashiko Craft**

---

## 1. Architecture Principles

- Every app is a **single-file HTML** — no build tools, no separate asset files, no external CSS or JS files
- **GitHub Pages** for hosting; **GitHub Contents API** for sync
- **localStorage** for primary persistence; GitHub JSON file as sync layer
- Apps are fully independent — each reads/writes only its own data file
- All icons and favicons are **embedded as base64 data URIs** in `<head>` — no separate image files
- **No frameworks** — vanilla HTML, CSS, and JavaScript only

---

## 2. Repository Structure

```
GitHub Org: rtpalme-C2
Data repo:  rtpalme-C2/life-stuff-data (public)

Each app has its own repo:
  rtpalme-C2/Sashiko-Craft        → sashiko-craft-inventory.html
  rtpalme-C2/Stylographic         → stylographic-inventory.html
  rtpalme-C2/Steady               → steady.html
  rtpalme-C2/Ritual               → ritual-routine.html
  rtpalme-C2/Modern-Heirloom      → modern-heirloom.html
  rtpalme-C2/Journey-Intelligence → journey-intelligence.html
                                    proposal-template.html
                                    brand-system.md

Data files in rtpalme-C2/life-stuff-data:
  sashiko-inventory.json
  stylographic-inventory.json
  steady-inventory.json
  ritual-data.json
  journey-intelligence.json
```

---

## 3. Chapter Structure

| Chapter | Theme | Apps |
|---|---|---|
| Chapter 1 · Health | Forest / amber palette | Ritual (skincare), Steady (weight) |
| Chapter 2 · Craft & Life | See per-app palettes below | Sashiko Craft, Stylographic, Modern Heirloom |
| Chapter 2 · Travel Advisory | Warm brown / brass palette | Journey Intelligence |

---

## 4. Typography

### Font
**Plus Jakarta Sans** — loaded from Google Fonts for all apps.

### Standard Load String (all apps must use this exact string)
```html
<link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:ital,wght@0,200;0,300;0,400;0,500;1,200;1,300;1,400;1,500&display=swap" rel="stylesheet">
```

### Weight Usage
| Weight | Usage |
|---|---|
| 200 | Wordmark secondary word (italic), decorative, display titles |
| 300 | `<h1>` wordmark, body copy, panel titles |
| 400 | Default body, labels, tags |
| 500 | Buttons, section headers, eyebrow, emphasis |
| 600 | Stat numbers, card names (inventory apps) |
| italic 200–500 | Available for secondary wordmark, taglines |

### Scale (rem-based)
| Role | Size | Weight |
|---|---|---|
| Wordmark `<h1>` | 2.2rem | 300 |
| Stat / metric number | 1.8–2.1rem | 400–600 |
| Panel title | 1.5–1.7rem | 300–400 |
| Body | 0.82rem | 400 |
| Card name | 1.05rem | 600 |
| Button label | 0.67–0.74rem | 500 |
| Eyebrow / label | 0.6–0.63rem | 400–500 |
| Tagline / caption | 0.68rem | 300–400 |
| Badge / micro | 0.6–0.65rem | 500 |

---

## 5. Colour Palettes

### Journey Intelligence — Warm Brown / Brass
**Chapter 2 · Travel Advisory**
> This is a warm brown/brass palette — NOT cool blue-grey. All values below are correct as of May 2026.

```css
--night-slate:  #1E1609;   /* primary dark, page headers, body text */
--deep-steel:   #2E2410;   /* accent, table headers, sync bar */
--steel:        #6C500F;   /* mid UI, secondary labels, hotel meta */
--warm-silver:  #B8900C;   /* text on dark backgrounds, primary accent */
--silver-mist:  #D4AE3A;   /* subtle highlights, italic wordmark */
--paper:        #F5F2EC;   /* page background, modal background */
--text-main:    #1E1609;   /* body text on paper */
--text-mid:     #4A3410;   /* secondary body text */
--text-dim:     #8C6C2C;   /* captions, labels */
--text-faint:   #C4A86A;   /* footnotes, rules */
--rule:         #DDD0A8;   /* horizontal rules, borders */
--stripe:       #EEE8D4;   /* alternate table rows */
```

**Role assignments:**
- Dark → Night Slate `#1E1609`
- Light → Paper `#F5F2EC`
- Accent → Deep Steel `#2E2410`
- Primary highlight → Warm Silver `#B8900C`

**Icon Mark — Meridian:**
- Vertical ellipse rx=9 ry=21 — the hero, always in Warm Silver `#B8900C`
- Globe circle r=21, faint — recedes into background
- Equator: full-width horizontal line, silver
- 2 latitude hints above/below equator
- Datum point: silver fill, dark center punch (r=2.4 outer, r=1 inner)
- Avoided: planes, compasses, maps, globe-as-primary

**Proposal format:**
- Tool: HTML → PDF via Playwright (Chromium)
- Template: `rtpalme-C2/Journey-Intelligence/proposal-template.html`
- Brand reference: `rtpalme-C2/Journey-Intelligence/brand-system.md`

---

### Sashiko Craft — AI Indigo
```css
--ai-indigo:   #1A2840;   /* header background, primary dark */
--deep-ai:     #2E4A68;   /* sync bar, hover states */
--steel-blue:  #4A7A9B;   /* active states, links */
--thread-blue: #8AAEC4;   /* secondary accent */
--sky-thread:  #C8DCE8;   /* borders, rules */
--washi:       #F5F2EC;   /* page background, modal background */
--brass:       #B8965A;   /* primary accent, header rule */
--brass-light: #D4AE78;   /* button text on dark, hover brass */
--shadow:      rgba(20,40,70,.12);
--ink:         #1A2840;   /* body text */
```

### Stylographic — Gunmetal
```css
--gunmetal:    #1E2328;   /* header background */
--gunmetal-mid:#2C3340;   /* sync bar */
--brass:       #B8965A;
--brass-light: #D4AE78;
--brass-pale:  #F2EAD8;
--cream:       #F5F0E8;   /* page background */
--cream-dark:  #EDE6D8;   /* borders */
--teal:        #2A4A50;   /* hover state */
--ink:         #1A1C20;
--mist:        #8A9098;
--shadow:      rgba(10,12,16,.15);
--rule:        rgba(184,150,90,.22);
```

### Chapter 1 · Health (Ritual, Steady)

#### Steady — Forest
```css
--forest-deep:   #1F3329;   /* header background */
--forest-mid:    #2D4A3A;   /* sync bar, stats bar */
--forest-light:  #4A7A5E;   /* success states */
--parchment:     #F0EADA;   /* page background */
--parchment-dim: #E2D9C8;   /* borders, card backgrounds */
--amber:         #D4B06A;   /* primary accent */
--amber-light:   #E8C97E;   /* hover amber */
--amber-dim:     #A8883E;   /* muted amber */
--text-primary:  #1A2B22;
--text-secondary:#3D5A48;
--text-muted:    #6B8F79;
--text-on-dark:  #F0EADA;
--text-dim:      #C8BEA8;
--warn:          #B85C3A;
--warn-light:    #E8705A;
--radius:        12px;
--radius-sm:     8px;
```

---

## 6. Border Radius Scale

| Name | Value | Usage |
|---|---|---|
| Pill | 20px | Sync buttons, filter pills, action buttons, `+ Add` buttons |
| Modal | 16px | All modals (PAT modal, item modal) |
| Card | 12px | Content cards, metric blocks, control panels |
| Soft | 10px | Stat pills, toast, badges |
| Input | 8px | Form inputs, selects, textareas, modal action buttons |
| Sharp | 2–4px | Config notice alert, Stylographic badges |

**Rule:** Never mix these — pick the correct scale token for each element type and apply consistently.

---

## 7. Layout

### Full-Width Pattern
All apps use **full-width layout with consistent side padding** — not centered max-width columns.

```css
header, .sync-bar, .top-bar, .filters, .content { padding-left: 40px; padding-right: 40px; }

@media (max-width:768px) {
  header { padding: 24px 20px 20px; }
  .sync-bar, .top-bar, .filters, .config-notice { padding-left: 16px; padding-right: 16px; }
}
@media (max-width:480px) {
  header h1 { font-size: 1.7rem; }
}
```

### Steady / Health apps use max-width column for content
```css
.main { max-width: 480px; margin: 0 auto; padding: 20px 16px 100px; }
```

---

## 8–24. [Sections 8–24 unchanged from Version 1.0]

> Sections 8 through 24 (Header Pattern, Sync Bar, Config Notice, PAT Modal, Item Modal,
> Form Fields, Toast, Tab Bar, Card, Table, Filter Pills, Badge, GitHub Sync Architecture,
> Init Pattern, Meta Tags, Responsive Breakpoints, and New App Checklist) are unchanged
> from Version 1.0. Refer to the previous version or the individual app source files
> for those patterns.

---

## Changelog

| Version | Date | Changes |
|---|---|---|
| 1.1 | May 2026 | Added Journey Intelligence palette (warm brown/brass). Corrected Chapter 3 entry. Added Journey Intelligence to repo structure. Sections 8–24 unchanged. |
| 1.0 | March 2026 | Initial release |
