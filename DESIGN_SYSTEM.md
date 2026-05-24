# Life Stuff Apps — Design System

## Version 1.2 · May 2026
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

Personal apps:
  rtpalme-C2/Steady          → steady.html
  rtpalme-C2/Ritual          → ritual-routine.html
  rtpalme-C2/Stylographic    → stylographic-inventory.html

Business apps:
  rtpalme-C2/Journey-Intelligence → journey-intelligence.html
                                    proposal-template.html
                                    brand-system.md
  rtpalme-C2/Sashiko-Craft   → sashiko-craft-inventory.html
  rtpalme-C2/Modern-Heirloom → modern-heirloom-inventory.html

Data files in rtpalme-C2/life-stuff-data:
  sashiko-inventory.json
  stylographic-inventory.json
  steady-inventory.json
  ritual-data.json
  journey-intelligence.json
  modern-heirloom-inventory.json
  DESIGN_SYSTEM.md               ← this file
  life-stuff-app-template.html   ← starter template for new apps
  life-stuff-continuity.docx     ← Claude continuity document
```

---

## 3. App Categories

### Personal
Apps for personal daily life tracking. Not for sale or commerce.

| App | Purpose |
|---|---|
| Steady | Personal weight loss journey — weekly weigh-ins, shot tracker, trend chart |
| Ritual | Personal skincare routine — morning & evening steps, product tracking, cycle-aware |
| Stylographic | Personal fountain pen and ink collection — inventory, care log, journal |

### Business
Apps supporting active business operations and commerce.

| App | Business | Purpose |
|---|---|---|
| Journey Intelligence | Fora Travel | Travel advisory — client management, commission tracking |
| Modern Heirloom | Luxury Resale | Hermès, Louis Vuitton and luxury goods inventory and sales |
| Sashiko Craft | Sashiko | Embroidery supplies management and sales |

**Note:** Personal collection items (Stylographic, etc.) would move to Modern Heirloom if a decision is made to sell them.

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
| 200 | Wordmark secondary word (italic), decorative |
| 300 | `<h1>` wordmark, body copy, panel titles |
| 400 | Default body, labels, tags |
| 500 | Buttons, section headers, eyebrow, emphasis |
| italic 200–500 | Available for secondary wordmark, taglines |

### Scale (rem-based)
| Role | Size | Weight |
|---|---|---|
| Wordmark `<h1>` | 2.2rem | 300 |
| Stat / metric number | 1.8–2.1rem | 400–500 |
| Panel title | 1.5–1.7rem | 300–400 |
| Body | 0.82rem | 400 |
| Card name | 1.05rem | 500 |
| Button label | 0.67–0.74rem | 500 |
| Tagline / caption | 0.68rem | 300–400 |
| Badge / micro | 0.6–0.65rem | 500 |

---

## 5. Colour Palettes

### Journey Intelligence — Warm Brown / Brass
> Warm brown/brass palette — NOT cool blue-grey. Correct as of May 2026.

```css
--night-slate:  #1E1609;   /* primary dark, page headers, body text */
--deep-steel:   #2E2410;   /* accent, table headers, sync bar */
--steel:        #6C500F;   /* mid UI, secondary labels */
--warm-silver:  #B8900C;   /* text on dark backgrounds, primary accent */
--silver-mist:  #D4AE3A;   /* subtle highlights, italic wordmark */
--paper:        #F5F2EC;   /* page background */
--text-main:    #1E1609;
--text-mid:     #4A3410;
--text-dim:     #8C6C2C;
--text-faint:   #C4A86A;
--rule:         #DDD0A8;
--stripe:       #EEE8D4;
```

**Proposal format:**
- Tool: HTML → PDF via Playwright (Chromium)
- Template: `rtpalme-C2/Journey-Intelligence/proposal-template.html`
- Brand reference: `rtpalme-C2/Journey-Intelligence/brand-system.md`

---

### Sashiko Craft — AI Indigo
```css
--ai-indigo:   #1A2840;
--deep-ai:     #2E4A68;
--steel-blue:  #4A7A9B;
--thread-blue: #8AAEC4;
--sky-thread:  #C8DCE8;
--washi:       #F5F2EC;
--brass:       #B8965A;
--brass-light: #D4AE78;
--shadow:      rgba(20,40,70,.12);
--ink:         #1A2840;
```

### Stylographic — Gunmetal
```css
--gunmetal:    #1E2328;
--gunmetal-mid:#2C3340;
--brass:       #B8965A;
--brass-light: #D4AE78;
--brass-pale:  #F2EAD8;
--cream:       #F5F0E8;
--cream-dark:  #EDE6D8;
--teal:        #2A4A50;
--ink:         #1A1C20;
--mist:        #8A9098;
--shadow:      rgba(10,12,16,.15);
--rule:        rgba(184,150,90,.22);
```

### Ritual — Brown / Terracotta
```css
--brown:       #2D1810;
--brown-mid:   #7A3520;
--gold:        #C4622A;
--gold-light:  #E8A06A;
--cream-pale:  #FAF6F2;
```

### Steady — Forest
```css
--forest-deep:   #1F3329;
--forest-mid:    #2D4A3A;
--forest-light:  #4A7A5E;
--parchment:     #F0EADA;
--parchment-dim: #E2D9C8;
--amber:         #D4B06A;
--amber-light:   #E8C97E;
--amber-dim:     #A8883E;
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

### Modern Heirloom — Rose / Plum
```css
--mh-dark:  #1C0810;
--mh-mid:   #4A1428;
--mh-rose:  #D4617A;
--mh-petal: #F5F2EC;
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

---

## 7. Layout

### Full-Width Pattern
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

---

## 8–24. [Sections 8–24 unchanged from Version 1.0]

> Sections 8 through 24 (Header Pattern, Sync Bar, Config Notice, PAT Modal, Item Modal,
> Form Fields, Toast, Tab Bar, Card, Table, Filter Pills, Badge, GitHub Sync Architecture,
> Init Pattern, Meta Tags, Responsive Breakpoints, and New App Checklist) are unchanged
> from Version 1.0. Refer to the previous version or individual app source files.

**Header note (v1.2):** The header eyebrow line (`Chapter N · Name`) has been removed
from all apps. Headers now show only the wordmark and tagline.

---

## Changelog

| Version | Date | Changes |
|---|---|---|
| 1.2 | May 2026 | Removed all Chapter 1/Chapter 2 references. Added Personal/Business app categorisation. Removed header eyebrow from all apps. Removed life-stuff-hub.html. Updated steady data file reference to steady-inventory.json. |
| 1.1 | May 2026 | Added Journey Intelligence palette. Corrected chapter structure. Added Journey Intelligence repo files. |
| 1.0 | March 2026 | Initial release |
