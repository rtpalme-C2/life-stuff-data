# Life Stuff Apps — Design System

## Version 1.6 · October 2026
**Reference implementation: Sashiko Craft** (search, sort, filters and summary pills: The Collection, section 8)

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
  rtpalme-C2/The-Collection  → the-collection.html   (formerly the Modern Heirloom app and repo;
                                 modern-heirloom-inventory.html has been deleted)

Data files in rtpalme-C2/life-stuff-data:
  sashiko-inventory.json
  stylographic-inventory.json
  steady-inventory.json
  ritual-data.json
  journey-intelligence.json
  the-collection-inventory.json
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
| The Collection (formerly Modern Heirloom) | Luxury Resale | Hermès, Louis Vuitton and luxury goods inventory and sales |
| Sashiko Craft | Sashiko | Embroidery supplies management and sales |

**Note:** Personal collection items (Stylographic, etc.) would move to The Collection if a decision is made to sell them.

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
| 500 | Buttons, section headers, emphasis (`strong` = 500) |
| italic 200–500 | Available for the secondary wordmark word |

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

### The Collection (formerly Modern Heirloom) — Plum / Champagne
```css
--mh-dark: #1C0810;
--mh-mid: #4A1428;
--mh-accent: #8B2040;
--mh-rose: #DCC9A6;
--mh-petal: #F5F2EC;
--mh-petal-dim: #EAE6DF;
```

---

## 6. Border Radius Scale

| Name | Value | Usage |
|---|---|---|
| Pill | 20px | Sync buttons, filter pills, action buttons, `+ Add` buttons |
| Modal | 16px | All modals (PAT modal, item modal) |
| Card | 12px | Content cards, metric blocks, control panels |
| Input | 8px | Form inputs, selects, textareas, modal action buttons |
| Sharp | 4px | Config notice alert, inline `code`, Stylographic badges |

**Only these radii are allowed:** 4, 8, 12, 16, 20 px and `50%` (plus directional forms such as `16px 16px 0 0`). No 2, 3, 5, 6, 9, 10px.

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


## 8. Search, Sort, Filters and Summary Pills (v1.6)

One toolbar, in the same place, on every app that shows a list of records. Apps differ in **which**
sort options and filters they offer, never in **where** those controls sit or how they look. This
section replaces the v1.3 Pattern A / Pattern B framework. Its inline filter rows survive as the
"few filters" variant (8.3), and the sticky bar survives as an option (8.7).

Reference implementation for this section: **The Collection**. (The rest of the system still uses
Sashiko Craft as reference.)

### 8.1 Standard order, top to bottom

1. **Summary pills** (8.5), when the app has numbers worth summarising
2. **Toolbar row:** Search · Sort · Filters · Add button
3. **Active-filter chips** and the results note (8.4), only while a filter or search is active
4. **The list** (cards or table)

### 8.2 Search and Sort

- **Search** is the flexible-width first control. A magnifier icon sits inside it, 36px left padding.
  It matches every descriptive text field on the record (The Collection: name, brand, category, notes, product code, colour, material, model size) and runs as the user types.
- **Sort** is a select plus a direction toggle (`↑` / `↓`), side by side, placed right after Search.
  It is never a labeled filter row. The v1.3 rule "Sort gets a dedicated row" is withdrawn.
  - Option text is the field name only ("Date acquired", "Asking price"). No "Sort:" prefix.
  - Every sort has a default direction (dates and amounts descending, names ascending).
  - **Records missing the sort value always go last**, in both directions.
  - Number sorts compare numbers, never text. Name sorts ignore case and accents.
  - The sort choice is remembered per tab or view while the app is open.
  - Each app (and each tab) keeps its own list of sort fields. The Collection offers, per tab:
    Collection: Date acquired, Price paid (USD), Name, Brand. Wishlist: Name, Brand, Target price.
    Listed: Asking price, Margin, and similar. Sold: Date sold, Sold price, Profit, and similar.
    The control is identical everywhere.
- On phones the toolbar wraps: Search takes the full first line, then Sort, Filters and Add share the next.

### 8.3 Filters adapt to how many there are

| Filters in the app (per view) | Presentation |
|---|---|
| 1 to 3 | **Inline labeled rows** under the toolbar (the v1.3 Pattern A rows: `.filter-row`, `.filter-label` with `min-width: 52px`, pills or selects) |
| 4 or more | **Filters button** (`Filters` / `Filters · N`) opening a popover with one labeled select per filter and a "Clear all" link |

The threshold counts the filters shown on one tab or view. A filter that does not apply to a view is
hidden there and cleared when the user switches to that view (Status on a Wishlist, for example).

Filters button and popover rules:
- The popover is anchored under the button, `min(270px, 86vw)` wide, `max-height: 70vh`, scrolls inside.
- Label is `Filters` with no count, or `Filters · N` where N is the number of active filters.
- Every control in the popover is a `<select>` whose first option is "All …".
- Closes on outside click and on Escape.
- Closed lists (see 8.6) are always selects. Free-text fields get a search match, not a filter select.

### 8.4 Active-filter chips and results note

When any filter or the search is active, show under the toolbar:
- One **chip** per active filter (`Source: Outlet ×`). Clicking a chip removes that filter.
- A **results note**: `Showing 3 of 9`. It counts within the current tab or view.
- Both disappear when nothing is active.

### 8.5 Summary pills

A row of fixed-size pills showing totals for the **records currently shown** (they follow search and filters).

- **Anatomy:** small uppercase label, large value, optional one-line note (`.stat-note`).
- **Size:** every pill is the same size: 160px wide on desktop (`repeat(auto-fill, 160px)`, equal row height),
  two per row on phones. Pills never stretch to different widths.
- **Notes say what was left out.** "2 without an asking price", "1 not counted (needs a sold price and
  USD cost)". A total that silently skips records is a bug.
- Amounts are shown in USD, whole dollars. A record with a foreign-currency cost and no USD amount
  is left out of totals and is counted in the note.
- Pill labels are plain nouns: Pieces, Total, Budget, Value, Profit.

### 8.6 Dropdown or free text

| Use a **closed dropdown** when the value... | Use **free text** (with type-ahead where values repeat) when the value... |
|---|---|
| drives a filter, sort, total or badge | only describes the record |
| has a small, stable set of answers | is the brand's own wording (colour name, model size, material) |
| must be comparable across records | is a place or a person |

Where a dropdown can't cover every case, add **Other** plus a small notes field. Do not widen the list
to fit one record. Values are stored with one fixed spelling (a short code, or the label exactly as shown), never as free variants. Matching for filters ignores case and accents
(`Hermes` and `Hermès` are the same filter entry; saving corrects the spelling to the canonical form).

### 8.7 Optional: sticky variant

Long single-list apps may make the toolbar sticky (`position: sticky; top: 0; z-index: 10`, bottom border
only, reverting to static at 768px and below). This changes only position, not contents.

### 8.8 Current conformance (reviewed 2026-10-03 from each app's source)

| App | Search | Sort | Filters | Summary | Needs |
|---|---|---|---|---|---|
| The Collection | In toolbar | In toolbar, select + direction | Popover (9+) | Pills | Reference. Conforms |
| Stylographic | Own control per tab | Dedicated labeled **row** per tab | Selects and labeled rows | `.metric` cards | Move Sort next to Search; adopt pills; use popover if a tab passes 3 filters |
| Ritual | Own control (products) | Dedicated labeled **row** | Labeled rows | Own stat styles | Move Sort next to Search; adopt pills |
| Sashiko Craft | In top bar | Inside the filter group, not by Search | Category buttons plus selects | `.stat` cards | Move Sort next to Search; filters are 4 or more, so move them behind a Filters button; adopt pills |
| Journey Intelligence | In toolbar | **None** | One status select | `stats-grid` | Add Sort; adopt pills |
| Steady | Not applicable (no record list) | Not applicable | Not applicable | `.stats-bar` | Adopt pill look if it ever shows a record list |

Apps are brought into line when they are next changed. No app is rebuilt only to conform.

### 8.9 Implementation checklist

- [ ] Toolbar order is Search, Sort, Filters (or inline rows), Add
- [ ] Sort has a direction toggle, field-name-only options, missing values last, remembered per view
- [ ] Filters at 4 or more sit behind the Filters button with an active count
- [ ] Chips remove their filter; results note reads `Showing X of Y`
- [ ] Filters that don't apply to a view are hidden and cleared on view change
- [ ] Summary pills are one fixed size, follow the current filters, and note what they exclude
- [ ] Colours come from palette tokens, not hard-coded values
- [ ] Tested at 768px and 480px, and with an empty list, one record, and every record filtered out

### 8.10 Component CSS (palette variables are per app)

```css
.toolbar { padding: 20px 40px 0; display: flex; align-items: center; gap: 12px; flex-wrap: wrap; }
.search-wrap { flex: 1; min-width: 180px; position: relative; }
.sort-wrap { display: flex; gap: 6px; align-items: center; }
.sort-wrap .filter-select { max-width: 170px; }
.sort-dir, .filters-btn { padding: 9px 12px; border-radius: 8px; border: 1px solid var(--border); background: #fff; cursor: pointer; }
.filters-pop { display: none; position: absolute; right: 0; top: calc(100% + 8px); z-index: 50;
  width: min(270px, 86vw); max-height: 70vh; overflow-y: auto; background: #fff; border: 1px solid var(--border);
  border-radius: 12px; padding: 14px; flex-direction: column; gap: 12px; }
.filters-pop.open { display: flex; }
.chips { display: flex; flex-wrap: wrap; gap: 6px; padding: 12px 40px 0; }
.chip { font-size: 0.6875rem; padding: 5px 10px; border-radius: 20px; background: #fff; border: 1px solid var(--accent-soft); color: var(--accent); cursor: pointer; }
.results-note { padding: 10px 40px 0; font-size: 0.6875rem; color: var(--text-dim); }
.stats-row { padding: 20px 40px 0; display: grid; gap: 12px; grid-template-columns: repeat(auto-fill, 160px); grid-auto-rows: 1fr; }
.stat-pill { background: var(--card-bg); border: 1px solid var(--border); border-radius: 12px; padding: 12px 18px;
  display: flex; flex-direction: column; gap: 3px; min-width: 0; }
.stat-label { font-size: 0.5rem; letter-spacing: .18em; text-transform: uppercase; color: var(--text-dim); font-weight: 500; }
.stat-value { font-size: 1.2rem; font-weight: 500; letter-spacing: -.02em; }
.stat-note { font-size: 0.5625rem; color: var(--text-dim); margin-top: 2px; line-height: 1.35; }
@media (max-width: 480px) { .stats-row { grid-template-columns: repeat(2, minmax(0, 1fr)); } .search-wrap { flex: 1 1 100%; } }
```

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

**Header note (v1.5):** Headers show the wordmark only — no eyebrow line (`Chapter N · Name`) and no tagline.
The `<h1>` is weight 300, `clamp(…, 2.2rem)` maximum.

---

## 26. Sync Safety, Dates and Escaping (v1.5)

Every app that syncs to GitHub follows these rules. They exist because an app that starts with an
empty or seed-filled local copy and a failed read can otherwise overwrite the real data file.

**Push guard.** Declare `let remoteReady = false; let localTrusted = false;` and
`function pushAllowed() { return remoteReady || localTrusted; }`.
- `remoteReady = true` only after the remote read is confirmed: a parsed JSON body, an empty body,
  or (for apps that create their own file) a 404. A network error, a non-404 HTTP error or an HTML
  body leaves it `false`.
- `localTrusted = true` only when the device started with real cached data. Seed or default data is
  never trusted. Do not persist seed data to local storage when a token is configured.
- `scheduleSave()` and `saveToGitHub()` both return early when `!pushAllowed()`, setting the status
  "Not synced yet — changes kept locally".
- The "GitHub has no data — push local data up" bootstrap is allowed because the empty remote was
  confirmed first.

**Count guard (v1.6).** `saveToGitHub()` also refuses a push that would cut the record list sharply:
keep `lastKnownCount` (set after every confirmed read or save) and block when `lastKnownCount >= 3` and the
new list is under 60% of it (`items.length < Math.ceil(0.6 * lastKnownCount)`), showing a toast. It catches a
bad load that passes the checks above. It cannot see edits made on another device. Implemented in The
Collection; recommended for every app that holds records.

**Save timer.** The debounced save is `saveTimer = setTimeout(() => { saveTimer = null; saveToGitHub(); }, 1200)`.
The `beforeunload` guard tests `saveTimer || pendingSave`, so `saveTimer` must be cleared when it fires.

**Dates.** Never use `new Date().toISOString().slice(0,10)` for a user-facing date or a commit
message (it is the UTC date; after about 7 pm US Central it is tomorrow). Use `localYMD()`.

**Escaping.** User-typed text placed into `innerHTML` or an attribute goes through `esc()`.
Numbers, dates and constants need no escaping.

**Secrets.** The GitHub token lives under `LS_PAT`. Stylographic also keeps an Anthropic API key under
`LS_ANTHROPIC` (`stylographic_anthropic_key`) for its in-app AI feature; it is stored only in that
browser's local storage. "Reset local data" leaves it in place, like the GitHub token.

## 27. Status Colours and Storage Constants (v1.5)

**Status colours.** Every app defines the status variables it uses under the canonical names, each with
`-bg`, `-text` and `-border` variants: `--ok`, `--warn`, `--err`, `--info`, `--neutral`. Only the values
change per app. Journey Intelligence also keeps `--green`, `--amber` and `--red` as ruled exceptions.

**Storage constants.** Each app has one set, with its own prefix: `LS_PAT`, `LS_SHA`, `LS_DATA_KEY`
(plus `LS_SHOTS_KEY` in Steady; `LS_KEY` in Journey Intelligence and Ritual is the same constant under its
older name). A token key is never shared between apps. `DATA_VERSION` is per app.

---

## 28. Data Conventions (v1.6)

Written from The Collection's field clean-up. They apply to every app that stores records.

- **Money is a number.** Stored as a JSON number; **missing is `null`**, never `""` or text such as `"550.00"`.
  Parse form input with `numOrNull()` before saving; format only when displaying. For a foreign-currency
  purchase store the amount paid, `costCurrency`, and a separate `costUSD` (the USD amount on the card
  statement). Totals, margins and profit use USD only and count excluded records in a note (8.5).
- **Dates** are `YYYY-MM-DD` local dates (section 26).
- **Closed lists** (8.6) store one fixed spelling. Where a record doesn't fit, use `Other` plus a notes field.
- **One fact, one field.** A field answers one question. Example: "Bought" (new or pre-owned when acquired)
  and "Condition" (shape today) are separate, as are "Size" (class used for filtering) and "Model size"
  (the brand's own name, such as GM or Cabine).
- **Migrating existing records.** When a field changes shape, migrate in code on load (local cache, remote
  read and seed data), per record, **idempotently, gated on the new field being absent or the old shape
  being present**, then save if anything changed. Show the old-to-new mapping to the owner before building it.
- **Keep old keys.** Do not delete the old field in the same release (`origin` and `accompanied` stay in The
  Collection's data after migration), so the previous app version and a rollback keep working.
- **Do not bump `DATA_VERSION` to migrate.** In The Collection a remote file whose `_version` differs is
  treated as "no data", so bumping would make the app overwrite GitHub with local or seed data. Check an
  app's sync code before ever bumping its version.
- **Back up before a migration goes live.** Copy the data file, or use the app's Download backup button.
- **Deploying.** Test copies are uploaded under a unique file name, not the live name. Every upload is
  checked byte-for-byte against the intended file before it is promoted.

## 29. Multi-select Chip Group (v1.6)

For "which of these apply" fields (The Collection: Accessories). A wrapping row of pill-shaped checkboxes;
tapping toggles one. Selected chips fill with the app's darkest accent. Stored as an **array of the chip labels**.
Pair it with a one-line free-text notes field for anything not on the list. A fact that already has its own
toggle (Receipt) stays out of the chip list.

```css
.acc-grid { display: flex; flex-wrap: wrap; gap: 8px; }
.acc-opt { display: inline-flex; align-items: center; gap: 6px; padding: 7px 12px; border: 1px solid var(--border);
  border-radius: 999px; font-size: 13px; cursor: pointer; background: #fff; }
.acc-opt:has(input:checked) { background: var(--accent-dark); color: #fff; border-color: var(--accent-dark); }
```

---

## Changelog

| Version | Date | Changes |
|---|---|---|
| 1.6 | October 2026 | Replaced section 8: one standard toolbar (Search, Sort with direction, Filters, Add), filters adapt to count (1 to 3 inline rows, 4 or more behind a Filters button), active-filter chips and results note, and a standard summary-pill component; Sort moves out of its own row (v1.3 rule withdrawn). Added conformance review of all apps. Added sections 28 (data conventions: numeric money, migrations, version caution) and 29 (multi-select chip group), and the count guard to section 26. Removed the retired Modern Heirloom data file from the repo listing. |
| 1.5 | October 2026 | Corrected The Collection palette to match the live app. Added sections 26–27 (push guard, save timer, local dates, escaping, status colours, storage constants). Radius scale restricted to 4/8/12/16/20/50% (removed Soft 10px). Headers: no eyebrow, no tagline. Modern Heirloom renamed The Collection (repo The-Collection). Incorporates the October 2026 audit rulings. |
| 1.4 | May 2026 | Added Section 9: Rating Modal Pattern. Documented three-state preference modal (yes/undecided/no) with customizable display labels. Includes integration checklist for other apps. Updated section numbering (was 9–24, now 10–25). |
| 1.3 | May 2026 | Added Section 8: Filter & Sort Pattern Decisions. Documented labeled filter-rows pattern (Pattern A) and sticky filter bar variant (Pattern B). Added decision matrix for choosing patterns. Updated section numbering (was 8–24, now 9–24). |
| 1.2 | May 2026 | Removed all Chapter 1/Chapter 2 references. Added Personal/Business app categorisation. Removed header eyebrow from all apps. Removed life-stuff-hub.html. Updated steady data file reference to steady-inventory.json. |
| 1.1 | May 2026 | Added Journey Intelligence palette. Corrected chapter structure. Added Journey Intelligence repo files. |
| 1.0 | March 2026 | Initial release |
