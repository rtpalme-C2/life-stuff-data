# Life Stuff Apps — Design System

## Version 1.4 · May 2026
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


## 8. Filter & Sort Pattern Decisions

### Overview

Two distinct filtering patterns have emerged across Life Stuff apps. Choose based on data structure and use case. This section provides the decision framework.

---

### Pattern A: Labeled Filter-Rows (Stylographic, Sashiko Craft)

#### When to use
- **Multi-faceted data** with several independent filter dimensions (status, category, nib type, etc.)
- **Tabbed or single-view layouts** where filters are reorganized per section
- **Mobile-first requirement:** filters need to stack cleanly on small screens
- **Discoverability important:** users should see all available filters at a glance

#### DOM Structure

```html
<div class="controls" style="flex-direction:column;align-items:stretch;gap:6px">
  <!-- Row 1: Search + inline dropdowns + action button -->
  <div style="display:flex;gap:8px;align-items:center;flex-wrap:wrap">
    <div class="search-wrap"><!-- search input --></div>
    <select><!-- category or maker dropdown --></select>
    <button class="btn-add">+ Add Item</button>
  </div>
  
  <!-- Row 2+: Labeled filter rows for pills or dropdowns -->
  <div class="filter-row">
    <span class="filter-label">Status</span>
    <button class="filter-pill">All</button>
    <button class="filter-pill">Active</button>
  </div>
  
  <!-- Sort as dedicated row with label -->
  <div class="filter-row">
    <span class="filter-label">Sort</span>
    <select>
      <option>Name</option>
      <option>Date</option>
    </select>
  </div>
</div>
```

#### CSS Class Standards

```css
.controls {
  display: flex;
  flex-direction: column;
  align-items: stretch;
  gap: 6px;
  padding: 12px 16px;
  background: white;
  border: 1px solid var(--rule);
  border-radius: 16px;
  box-shadow: 0 2px 8px var(--shadow);
}

.filter-row {
  display: flex;
  align-items: center;
  gap: 6px;
  flex-wrap: wrap;
  margin-bottom: 8px;
}

.filter-label {
  font-size: 0.58rem;
  text-transform: uppercase;
  letter-spacing: 0.12em;
  color: #ccc;
  flex-shrink: 0;
  min-width: 52px;
}

.filter-pill {
  font-family: 'Plus Jakarta Sans', sans-serif;
  font-size: 0.65rem;
  font-weight: 500;
  padding: 4px 12px;
  border-radius: 20px;
  border: 1.5px solid var(--cream-dark);
  background: white;
  color: #aaa;
  cursor: pointer;
}

.filter-pill.active {
  background: var(--gunmetal);
  border-color: var(--gunmetal);
  color: var(--brass-light);
}

.controls select {
  font-family: 'Plus Jakarta Sans', sans-serif;
  padding: 4px 24px 4px 11px;
  border: 1.5px solid var(--sky-thread);
  border-radius: 20px;
  background: transparent;
  cursor: pointer;
}
```

#### Key Rules

1. **Search is inline** — share the first row with category/maker dropdowns
2. **Filter pills get their own rows** — one labeled row per filter type
3. **Sort gets a dedicated row** — label + dropdown, never inline with search
4. **Visual dividers are optional** — use spacing instead
5. **Labels use min-width: 52px** — ensures alignment across rows

#### Apps using this pattern
- **Stylographic:** Status, Nib filters + Sort (Pens, Inks, Accessories tabs)
- **Sashiko Craft:** Category buttons, Status/Form/Use dropdowns, Sort

---

### Pattern B: Sticky Filter Bar (Sashiko Craft variant)

#### When to use
- **Long, scrollable lists** where filter controls should stay visible
- **Single data type** (not multi-tab)
- **Users frequently change filters** while scrolling

#### Key Differences

| Aspect | Pattern A | Pattern B |
|--------|-----------|-----------|
| **Position** | Static | Sticky (top: 0) |
| **Z-index** | Default | 10 |
| **Border** | Full border + radius | Bottom border only |
| **Use case** | Compact controls | Long lists, frequent filtering |

#### CSS for sticky variant

```css
.filters {
  position: sticky;
  top: 0;
  z-index: 10;
  padding: 10px 40px;
  background: white;
  border-bottom: 1px solid var(--sky-thread);
  box-shadow: 0 2px 12px var(--shadow);
}

@media (max-width: 768px) {
  .filters {
    position: static; /* revert to Pattern A on mobile */
    border: 1px solid var(--rule);
    border-radius: 16px;
  }
}
```

#### Apps using this pattern
- **Sashiko Craft:** Inventory list (long, frequent filtering)

---

### Decision Matrix

Use this to choose which pattern for your next app:

| Scenario | Pattern | Rationale |
|----------|---------|-----------|
| Multi-tab layout | A | Each tab gets fresh filter context |
| Long, single-list view | B (or A) | B if scrolling often; A if short |
| Mobile-first priority | A | Rows stack better |
| Deep filtering (5+ dimensions) | A | Rows organize chaos |
| Simple filtering (1-2 dimensions) | A | Safer default |

---

### Implementation Checklist

When building a new app with Pattern A or B:

- [ ] Use `.controls` + `.filter-row` + `.filter-label` class structure
- [ ] Apply color tokens from palette (not hardcoded colors)
- [ ] Include `.filter-pill.active` state styling
- [ ] Test responsive behavior at 768px and 480px breakpoints
- [ ] Ensure Sort gets a dedicated filter-row with label
- [ ] Remove "Sort: " prefix from select options (label is now visible)
- [ ] Use `min-width: 52px` on `.filter-label` for alignment

---

## 9. Rating Modal Pattern

### Overview

A three-state preference modal for capturing user sentiment on inventory items. The modal presents three mutually exclusive options as buttons, with the underlying data model using simple string values (`yes`, `undecided`, `no`). Display labels are semantic and contextualized to the app's domain.

### Data Structure

```javascript
{
  reorder: 'yes' | 'undecided' | 'no'  // underlying data model (never changes)
}
```

The underlying data values are fixed and stable. Only the **display labels** and **button symbols** change per app context.

---

### Default Implementation (Sashiko Craft)

**Label context:** "Rating" (preference to reorder/repurchase)

#### Modal Buttons

```html
<div class="reorder-toggle">
  <button type="button" class="reorder-btn" id="rbtn-yes"   onclick="setReorderModal('yes')">★ Would Buy Again</button>
  <button type="button" class="reorder-btn" id="rbtn-null"  onclick="setReorderModal(null)">— Undecided</button>
  <button type="button" class="reorder-btn" id="rbtn-no"    onclick="setReorderModal('no')">✕ Would Not Buy Again</button>
</div>
```

#### Filter Dropdown

```html
<div class="filter-group">
  <span class="filter-label">Rating</span>
  <select class="filter-select" onchange="setRating(this.value)">
    <option value="All">All</option>
    <option value="yes">★ Would Buy Again</option>
    <option value="undecided">— Undecided</option>
    <option value="no">✕ Would Not Buy Again</option>
  </select>
</div>
```

#### Card Badge

```javascript
const ratingBadge = item.reorder === 'yes' 
  ? `<span class="badge badge-rating-yes">Would Buy Again</span>`
  : item.reorder === 'no'
  ? `<span class="badge badge-rating-no">Would Not Buy Again</span>`
  : '';
```

#### CSS for Button States

```css
.reorder-btn {
  font-family: 'Plus Jakarta Sans', sans-serif;
  font-size: 0.65rem;
  font-weight: 500;
  padding: 6px 14px;
  border: 1.5px solid #ddd;
  border-radius: 8px;
  background: white;
  color: #666;
  cursor: pointer;
  transition: all 0.2s;
}

.reorder-btn:hover {
  border-color: var(--thread-blue);
}

.reorder-btn.active[id="rbtn-yes"] {
  background: rgba(90, 171, 122, 0.15);
  border-color: #5aab7a;
  color: #1a5c38;
}

.reorder-btn.active[id="rbtn-no"] {
  background: rgba(176, 80, 80, 0.10);
  border-color: #b05050;
  color: #7a2020;
}

.reorder-btn.active[id="rbtn-null"] {
  background: var(--sky-thread);
  border-color: var(--thread-blue);
  color: var(--ai-indigo);
}

.badge-rating-yes {
  background: #e6f4ec;
  color: #1a6040;
}

.badge-rating-no {
  background: #f7eaea;
  color: #7a2424;
}
```

---

### Adapting the Pattern for Other Apps

When implementing the Rating modal in a new app, customize **only the display labels and button symbols**. The underlying data structure (`reorder: 'yes'/'undecided'/'no'`) remains constant across all apps.

#### Example: Stylographic App (Hypothetical)

If Stylographic adopted a "Would Use Again" rating for inks:

| State | Display Label | Symbol |
|-------|---------------|--------|
| `yes` | ✓ Would Use Again | ✓ |
| `undecided` | — Undecided | — |
| `no` | ✗ Would Not Use Again | ✗ |

**Key rule:** Never change the underlying data keys (`reorder: yes/undecided/no`). This preserves data portability and consistency across the design system.

---

### Filter Logic

Apps must implement filter state tracking:

```javascript
let activeRating = 'All';  // or 'yes', 'undecided', 'no'

function filterByRating(items) {
  if (activeRating === 'All') return items;
  if (activeRating === 'yes') return items.filter(i => i.reorder === 'yes');
  if (activeRating === 'undecided') return items.filter(i => !i.reorder);
  if (activeRating === 'no') return items.filter(i => i.reorder === 'no');
}
```

---

### Integration Checklist

When adding the Rating modal to a new app:

- [ ] Add `reorder: null` to item schema (or `reorder: 'undecided'` if preferred default)
- [ ] Create modal button group with three states (yes, undecided, no)
- [ ] Implement `setRatingModal(value)` function
- [ ] Add filter dropdown with label and four options (All, yes, undecided, no)
- [ ] Implement filter logic in `filterByRating(items)`
- [ ] Add card badge CSS (`.badge-rating-yes`, `.badge-rating-no`)
- [ ] Test modal state persistence in localStorage
- [ ] Ensure filter state updates grid and summary
- [ ] Test responsive behavior at all breakpoints

---

## 10–25. [Sections 10–25 unchanged from Version 1.0]

> Sections 10 through 25 (Header Pattern, Sync Bar, Config Notice, PAT Modal, Item Modal,
> Form Fields, Toast, Tab Bar, Card, Table, Badge, GitHub Sync Architecture,
> Init Pattern, Meta Tags, Responsive Breakpoints, and New App Checklist) are unchanged
> from Version 1.0. Refer to the previous version or individual app source files.

**Header note (v1.2):** The header eyebrow line (`Chapter N · Name`) has been removed
from all apps. Headers now show only the wordmark and tagline.

---

## Changelog

| Version | Date | Changes |
|---|---|---|
| 1.4 | May 2026 | Added Section 9: Rating Modal Pattern. Documented three-state preference modal (yes/undecided/no) with customizable display labels. Includes integration checklist for other apps. Updated section numbering (was 9–24, now 10–25). |
| 1.3 | May 2026 | Added Section 8: Filter & Sort Pattern Decisions. Documented labeled filter-rows pattern (Pattern A) and sticky filter bar variant (Pattern B). Added decision matrix for choosing patterns. Updated section numbering (was 8–24, now 9–24). |
| 1.2 | May 2026 | Removed all Chapter 1/Chapter 2 references. Added Personal/Business app categorisation. Removed header eyebrow from all apps. Removed life-stuff-hub.html. Updated steady data file reference to steady-inventory.json. |
| 1.1 | May 2026 | Added Journey Intelligence palette. Corrected chapter structure. Added Journey Intelligence repo files. |
| 1.0 | March 2026 | Initial release |
