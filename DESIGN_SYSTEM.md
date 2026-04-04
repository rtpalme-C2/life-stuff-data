# Life Stuff Apps — Design System
**Version 1.2 · April 2026**
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
  rtpalme-C2/Modern-Heirloom      → modern-heirloom-inventory.html
  rtpalme-C2/Journey-Intelligence → journey-intelligence.html

Data files in rtpalme-C2/life-stuff-data:
  sashiko-inventory.json
  stylographic-inventory.json
  steady-inventory.json
  ritual-data.json
  modern-heirloom-inventory.json
  journey-intelligence.json
```

---

## 3. Chapter Structure

Each app has its own distinct colour palette. Chapter groupings reflect content theme, not shared palette.

| Chapter | App | Purpose | Palette |
|---|---|---|---|
| Chapter 1 · Health | Ritual | Skincare routine | Terracotta / warm brown |
| Chapter 1 · Health | Steady | Weight tracking | Midnight Sage / forest green |
| Chapter 2 · Craft & Life | Sashiko Craft | Sewing supplies | AI Indigo / brass |
| Chapter 2 · Craft & Life | Stylographic | Fountain pens & ink | Gunmetal / brass |
| Chapter 2 · Craft & Life | Modern Heirloom | Luxury resale | Burgundy / rose |
| Chapter 2 · Craft & Life | Journey Intelligence | Travel advisory | Ochre |

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

### Standard Page Background
All apps use **`#F5F2EC`** (washi) as the page background — the same warm off-white as Sashiko Craft. This creates visual consistency across the suite regardless of each app's accent palette.

### Chapter 2 · Craft & Life

#### Sashiko Craft — AI Indigo
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

#### Stylographic — Gunmetal
```css
--gunmetal:    #1E2328;   /* header background */
--gunmetal-mid:#2C3340;   /* sync bar */
--brass:       #B8965A;
--brass-light: #D4AE78;
--brass-pale:  #F2EAD8;
--cream:       #F5F2EC;   /* page background — washi standard */
--cream-dark:  #EDE6D8;   /* borders */
--teal:        #2A4A50;   /* hover state */
--ink:         #1A1C20;
--mist:        #8A9098;
--shadow:      rgba(10,12,16,.15);
--rule:        rgba(184,150,90,.22);
```

#### Modern Heirloom — Burgundy
```css
--mh-dark:     #1C0810;   /* header background */
--mh-mid:      #4A1428;   /* sync bar */
--mh-accent:   #8B2040;   /* active states */
--mh-rose:     #D4617A;   /* primary accent, header rule, eyebrow */
--mh-petal:    #F5F2EC;   /* page background — washi standard */
--mh-petal-dim:#EAE6DF;   /* borders, card backgrounds */
```

### Chapter 1 · Health

#### Ritual — Terracotta
```css
--ritual-dark:   #2D1810;   /* header background */
--ritual-mid:    #5C2A14;   /* sync bar */
--ritual-accent: #C4622A;   /* primary accent, header rule */
--ritual-warm:   #E8A06A;   /* accent light */
--ritual-cream:  #F5F2EC;   /* page background — washi standard */
```

#### Steady — Midnight Sage / Forest
```css
--forest-deep:   #1F3329;   /* header background */
--forest-mid:    #2D4A3A;   /* sync bar, stats bar */
--forest-light:  #4A7A5E;   /* success states */
--parchment:     #F5F2EC;   /* page background — washi standard */
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
```

---

## 6. App Icon Pattern

All icons are **inline SVG, 56×56px** in the header, with `rx:12` rounded square background. Base64 PNG versions (generated via `cairosvg`) embedded in `<head>` for favicon (32×32) and apple-touch-icon (180×180).

### Critical Rules
- Header icon SVG: always `width="56" height="56" viewBox="0 0 56 56"`
- Icon background square must be **visibly distinct** from the header background — use a slightly lighter shade, not the same dark colour
- Icon shapes must **fill the viewBox** — test that the icon reads clearly at small sizes
- Favicons and apple-touch-icons must be **regenerated from the SVG** whenever the icon changes — they are not auto-updated

### Three-Color Construction (all icons)
Every icon uses three tones:
1. **Shadow layer** — darkest shade, offset slightly down/behind for depth
2. **Body layer** — mid shade, the primary visible shape
3. **Accent highlight** — accent color on the topmost or focal element only

### Per-App Icon Reference
| App | Icon | Background | Body | Accent |
|---|---|---|---|---|
| Sashiko Craft | Running stitch (3 offset rows) | `#1A2840` | washi dashes | brass rule |
| Stylographic | Fountain pen nib | `#1E2328` | brass shape | — |
| Ritual | Ceramic cream pot / dome | `#3D1008` | terracotta | warm orange lid |
| Steady | Stacked stones (3 ellipses) | `#1F3329` | forest greens | amber top stone |
| Modern Heirloom | Hermès-style handbag + Kelly clasp | `#3D0F20` | `#6B1E38` body | `#D4617A` toggle |

### Modern Heirloom Handbag — Construction Detail
- Handles: narrow tall arch from upper sides (not spanning full width — avoids briefcase read)
- Handles use `#8B2040` stroke with `#D4617A` highlight stroke on top for visibility
- Flap: top portion of bag body, darker than body (`#4A1428`)
- Clasp plate: `#8B2040`, rectangular with rounded corners
- Toggle bar: `#D4617A` (rose accent)
- Center post: `#8B2040` outer, `#D4617A` inner

---

## 7. Border Radius Scale

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

## 8. Layout

### Full-Width Pattern
All apps use **full-width layout with consistent side padding** — not centered max-width columns.

```css
/* Standard horizontal padding */
header, .sync-bar, .top-bar, .filters, .content { padding-left: 40px; padding-right: 40px; }

/* 768px tablet */
@media (max-width:768px) {
  header { padding: 24px 20px 20px; }
  .sync-bar, .top-bar, .filters, .config-notice { padding-left: 16px; padding-right: 16px; }
}

/* 480px phone */
@media (max-width:480px) {
  header h1 { font-size: 1.7rem; }
  /* app-specific adjustments */
}
```

### Steady / Health apps use max-width column for content (mobile-first data entry)
```css
.main { max-width: 480px; margin: 0 auto; padding: 20px 16px 100px; }
```

---

## 9. Header Pattern

### Structure (all apps)
```html
<header>
  <svg class="header-curves" ...>
    <!-- 3–4 paths tinted to app's accent colour at .14/.08/.05 opacity -->
  </svg>
  <div class="header-inner">
    <!-- App icon: inline SVG, 56×56px, rx:12 rounded square bg -->
    <svg width="56" height="56" viewBox="0 0 56 56" fill="none">...</svg>
    <div>
      <div class="header-eyebrow">Chapter N · Category</div>
      <h1>App <em>Name</em></h1>
      <p>Tagline · Subtitle · Description</p>
    </div>
  </div>
</header>
```

### Header CSS
```css
header {
  background: var(--[app]-dark);   /* darkest palette colour */
  padding: 36px 40px 30px;
  position: relative;
  overflow: hidden;
}
header::after {
  content: ''; position: absolute; bottom: 0; left: 0; right: 0;
  height: 2px;
  background: linear-gradient(90deg, transparent, var(--[app]-rose/brass), transparent);
}
.header-inner { position: relative; display: flex; align-items: center; gap: 22px; }
.header-eyebrow { font-size: .6rem; letter-spacing: .22em; text-transform: uppercase;
  color: var(--[app]-rose/brass-light); margin-bottom: 7px; font-weight: 400; }
header h1 { font-size: 2.2rem; font-weight: 300; color: var(--[app]-petal/washi);
  letter-spacing: .04em; line-height: 1; }
header h1 em { font-style: italic; color: var(--[app]-rose/sky-thread); }
header p { font-size: .68rem; color: rgba(255,255,255,.32);
  margin-top: 7px; letter-spacing: .12em; text-transform: uppercase; }
```

---

## 10. Sync Bar Pattern

### Visual
- **Dark background** extending from the header (app's mid-dark variable)
- Creates a unified brand zone: header → sync bar → content begins
- Pill buttons only, **transparent background** on ghost buttons (never white)

### HTML
```html
<div class="sync-bar">
  <div class="sync-status">
    <div class="sync-dot" id="sync-dot"></div>
    <span id="sync-label">Not connected to GitHub</span>
  </div>
  <div class="sync-actions">
    <button class="btn-sync" onclick="resetLocalData()">Reset local data</button>
    <button class="btn-sync" id="btn-disconnect" style="display:none" onclick="disconnectGitHub()">Disconnect</button>
    <button class="btn-sync primary" id="btn-connect" onclick="openPATModal()">Connect GitHub</button>
  </div>
</div>
```

### CSS
```css
.sync-bar {
  display: flex; align-items: center; justify-content: space-between;
  flex-wrap: wrap; gap: 10px;
  padding: 8px 40px;
  background: var(--[app]-mid);
  border-bottom: 1px solid rgba([accent-rgb],.12);
  font-size: .72rem;
}
.sync-status { display: flex; align-items: center; gap: 8px; color: rgba(255,255,255,.38); }
.sync-dot { width: 7px; height: 7px; border-radius: 50%;
  background: rgba(255,255,255,.18); flex-shrink: 0; transition: background .3s; }
.sync-dot.connected { background: #5aab7a; }
.sync-dot.saving    { background: var(--[app]-rose/brass); animation: pulse .8s infinite; }
.sync-dot.error     { background: #b05050; }
@keyframes pulse { 0%,100%{opacity:1} 50%{opacity:.35} }
.sync-actions { display: flex; gap: 8px; }
.btn-sync {
  font-family: 'Plus Jakarta Sans', sans-serif; font-size: .63rem; font-weight: 500;
  letter-spacing: .1em; text-transform: uppercase;
  padding: 5px 14px; border-radius: 20px;
  border: 1px solid rgba([accent-rgb],.35);
  background: transparent; color: rgba(255,255,255,.7);
  cursor: pointer; transition: all .18s;
}
.btn-sync:hover { border-color: var(--[app]-rose/brass); color: var(--[app]-petal/washi); }
.btn-sync.primary {
  background: var(--[app]-dark); border-color: var(--[app]-rose/brass);
  color: var(--[app]-rose/brass);
}
.btn-sync.primary:hover { background: rgba(0,0,0,.2); }
```

---

## 11. Config Notice Banner

Shown until PAT is configured. Hidden once `configOk()` returns true.

```html
<div class="config-notice" id="config-notice">
  <strong>⚠️ GitHub sync not configured</strong>
  Tap <strong>Connect GitHub</strong> to enter your Personal Access Token.
  The PAT needs <code>contents: write</code> permission on the
  <code>rtpalme-C2/life-stuff-data</code> repo. It is stored only in your
  browser's localStorage and never sent anywhere except the GitHub API.
</div>
```

```css
.config-notice {
  margin: 20px 40px; padding: 16px 20px;
  background: #fff8e6; border: 1.5px solid #f0c040; border-radius: 4px;
  font-size: .8rem; line-height: 1.6; color: #5a4000;
}
.config-notice strong { display: block; margin-bottom: 4px; font-size: .85rem; }
.config-notice code {
  background: #f0e8c8; padding: 1px 6px; border-radius: 4px;
  font-family: monospace; font-size: .78rem;
}
```

**Note:** `border-radius: 4px` is intentionally sharper than content cards — reads as a system alert.

---

## 12. PAT Modal Pattern

```html
<div class="pat-modal-backdrop" id="pat-modal" onclick="patBackdropClose(event)">
  <div class="pat-modal">
    <h2>Connect GitHub Sync</h2>
    <p>
      Enter a GitHub Personal Access Token with <strong>Contents: Read &amp; write</strong>
      permission scoped to the <code>rtpalme-C2/life-stuff-data</code> repository.
      The token is stored only in this browser's localStorage.
    </p>
    <div class="pat-field">
      <label>Personal Access Token</label>
      <input type="password" id="pat-input" placeholder="github_pat_…" autocomplete="off">
    </div>
    <div class="pat-actions">
      <button class="btn-pat-cancel" onclick="closePATModal()">Cancel</button>
      <button class="btn-pat-save" onclick="savePAT()">Save &amp; Sync</button>
    </div>
  </div>
</div>
```

```css
.pat-modal-backdrop {
  display: none; position: fixed; inset: 0;
  background: rgba(20,40,70,.5);
  z-index: 2000; align-items: center; justify-content: center; padding: 1rem;
}
.pat-modal-backdrop.open { display: flex; }
.pat-modal {
  background: var(--[app]-petal/washi);
  border-top: 4px solid var(--[app]-rose/brass);
  border-radius: 16px; padding: 2rem; width: 100%; max-width: 460px;
  box-shadow: 0 16px 48px rgba(20,40,70,.28); animation: slideUp .2s ease;
}
@keyframes slideUp { from{opacity:0;transform:translateY(14px)} to{opacity:1;transform:translateY(0)} }
```

---

## 13. Item / Content Modal Pattern

```css
.modal-backdrop { display:none; position:fixed; inset:0;
  background:rgba(20,40,70,.45); z-index:1000;
  align-items:center; justify-content:center; padding:1rem; }
.modal-backdrop.open { display:flex; }
.modal {
  background: var(--[app]-petal/washi);
  border-top: 4px solid var(--[app]-rose/brass);
  border-radius: 16px; padding: 2rem; width: 100%; max-width: 500px;
  box-shadow: 0 16px 48px rgba(20,40,70,.25);
  animation: slideUp .2s ease; max-height: 90vh; overflow-y: auto;
}
```

**Both PAT modal and item modal use `border-top: 4px solid var(--[app]-rose/brass)` — unified.**

---

## 14. Form Fields (inside modals)

```css
.field { margin-bottom: .9rem; }
.field label { display: block; font-size: .65rem; text-transform: uppercase;
  letter-spacing: .12em; color: #aaa; margin-bottom: .3rem; }
.field input, .field select, .field textarea {
  width: 100%; padding: 7px 10px;
  border: 1.5px solid var(--[app]-petal-dim/sky-thread); border-radius: 8px;
  font-family: 'Plus Jakarta Sans', sans-serif; font-size: .82rem;
  background: white; outline: none; transition: border-color .18s;
}
.field input:focus, .field select:focus, .field textarea:focus {
  border-color: var(--[app]-rose/steel-blue);
}
```

---

## 15. Toast Pattern

```css
.toast {
  position: fixed; bottom: 24px; right: 24px; z-index: 3000;
  background: var(--[app]-dark); color: white;
  padding: 10px 18px; border-radius: 10px; font-size: .76rem;
  letter-spacing: .04em; box-shadow: 0 4px 18px rgba(20,40,70,.3);
  opacity: 0; transform: translateY(8px); transition: all .25s;
  pointer-events: none;
}
.toast.show { opacity: 1; transform: translateY(0); }
```

---

## 16. Tab Bar Pattern (multi-section apps)

```css
.tab-bar { display:flex; gap:2px; padding:0 40px;
  background:white; border-bottom:1px solid var(--rule); }
.tab {
  font-size: .68rem; font-weight: 500; letter-spacing: .1em; text-transform: uppercase;
  padding: 14px 18px; cursor: pointer; border: none; background: none;
  color: #bbb; border-bottom: 2px solid transparent; margin-bottom: -1px;
  transition: all .18s;
}
.tab:hover { color: var(--brass); }
.tab.active { color: var(--gunmetal); border-bottom-color: var(--brass); }
```

---

## 17. Card Pattern (inventory grid)

```css
.card {
  background: white; border-radius: 12px; border: 1px solid var(--sky-thread);
  overflow: hidden; box-shadow: 0 2px 8px var(--shadow);
  transition: transform .2s, box-shadow .2s;
}
.card:hover { transform: translateY(-3px); box-shadow: 0 8px 24px var(--shadow); }
```

---

## 18. Filter Pills Pattern

```css
.filter-btn {
  font-size: .71rem; font-weight: 500; letter-spacing: .06em; text-transform: uppercase;
  padding: 5px 13px; border-radius: 20px; border: 1.5px solid var(--sky-thread);
  background: white; cursor: pointer; transition: all .18s;
}
.filter-btn.active { background: var(--deep-ai); border-color: var(--deep-ai); color: white; }
```

**All filter pill types use the same active colour — no hierarchy distinction between filter dimensions.**

---

## 19. Badge Pattern

```css
.badge {
  font-size: .63rem; font-weight: 500; letter-spacing: .05em;
  text-transform: uppercase; padding: 3px 9px; border-radius: 10px;
}
.badge-delivered { background: #d0e8d8; color: #1a5c38; }
.badge-enroute   { background: #ccdcee; color: #1a3c60; }
.badge-pending   { background: #dde4ec; color: #3a5070; }
```

---

## 20. GitHub Sync Architecture

### Constants (per-app)
```js
const GH_OWNER    = 'rtpalme-C2';
const GH_REPO     = 'life-stuff-data';
const GH_FILE     = '[app-name].json';
const GH_RAW_URL  = `https://raw.githubusercontent.com/${GH_OWNER}/${GH_REPO}/main/${GH_FILE}`;
const GH_API_URL  = `https://api.github.com/repos/${GH_OWNER}/${GH_REPO}/contents/${GH_FILE}`;
const LS_PAT      = '[app]_gh_pat';
const LS_SHA      = '[app]_gh_sha';
const LS_DATA_KEY = '[app]-v1';
```

### Per-App Sync Keys
| App | GH_FILE | LS_PAT | LS_SHA | LS_DATA_KEY |
|---|---|---|---|---|
| Sashiko Craft | sashiko-inventory.json | sashiko_gh_pat | sashiko_gh_sha | sashiko-v2 |
| Stylographic | stylographic-inventory.json | stylo_gh_pat | stylo_gh_sha | stylographic_local |
| Ritual | ritual-data.json | ritual_gh_pat | ritual_gh_sha | ritual_local |
| Steady | steady-inventory.json | steady_gh_pat | steady_gh_sha | steady-v1 |
| Modern Heirloom | modern-heirloom-inventory.json | mh_gh_pat | mh_gh_sha | mh-v1 |
| Journey Intelligence | journey-intelligence.json | ji_gh_pat | ji_gh_sha | ji-v1 |

### DATA_VERSION Contract
```js
// Bump DATA_VERSION when schema changes make old data incompatible.
// Update LS_DATA_KEY to match (e.g. '[app]-v2').
// Minor additions (new optional fields) do NOT require a bump.
const DATA_VERSION = 1;
```

### syncFromGitHub — Standard Pattern
**Critical:** A `404` response means the data file does not yet exist in the repo. This must be caught explicitly and treated as "push local data up to create the file" — not as an error. Without this, the app will fail to connect on first deploy.

```js
async function syncFromGitHub() {
  setSyncStatus('saving', 'Loading from GitHub…');
  try {
    const res = await fetch(GH_RAW_URL + '?t=' + Date.now());
    // 404 = file doesn't exist yet — push local data up to create it
    if (res.status === 404) {
      setSyncStatus('saving', 'Creating data file on GitHub…');
      await saveToGitHub();
      return;
    }
    if (!res.ok) throw new Error('HTTP ' + res.status);
    const text = await res.text();
    if (text && text.trim().startsWith('{')) {
      const parsed = JSON.parse(text);
      const hasData = parsed && parsed._version === DATA_VERSION &&
        Array.isArray(parsed.data) && parsed.data.length > 0;
      if (hasData) {
        supplies = parsed.data;
        persist();
        render();
        setSyncStatus('connected', 'Synced from GitHub · ' + new Date().toLocaleTimeString([],{hour:'2-digit',minute:'2-digit'}));
        await fetchSHA();
        return;
      }
    }
    // File exists but has no usable data — push local up
    setSyncStatus('saving', 'Pushing local data to GitHub…');
    await saveToGitHub();
  } catch(e) {
    setSyncStatus('error', 'GitHub sync failed — working offline');
    showToast('Could not reach GitHub. Changes saved locally.');
  }
}
```

### fetchSHA
```js
async function fetchSHA() {
  try {
    const res = await fetch(GH_API_URL, {
      headers: { 'Authorization': 'Bearer ' + getPAT(), 'Accept': 'application/vnd.github+json' }
    });
    if (!res.ok) return;
    const data = await res.json();
    if (data.sha) setSHA(data.sha);
  } catch(e) {}
}
```

### saveToGitHub
```js
async function saveToGitHub() {
  if (!configOk()) return;
  setSyncStatus('saving', 'Saving to GitHub…');
  pendingSave = true;
  try {
    await fetchSHA();
    const payload = { _version: DATA_VERSION, data: supplies };
    const content = btoa(unescape(encodeURIComponent(JSON.stringify(payload, null, 2))));
    const body = { message: 'AppName update · ' + new Date().toISOString().slice(0,10), content };
    if (getSHA()) body.sha = getSHA();
    const res = await fetch(GH_API_URL, {
      method: 'PUT',
      headers: {
        'Authorization': 'Bearer ' + getPAT(),
        'Accept': 'application/vnd.github+json',
        'Content-Type': 'application/json',
      },
      body: JSON.stringify(body),
    });
    if (!res.ok) { const err = await res.json().catch(()=>({})); throw new Error(err.message || 'HTTP ' + res.status); }
    const result = await res.json();
    if (result.content && result.content.sha) setSHA(result.content.sha);
    pendingSave = false;
    setSyncStatus('connected', 'Saved to GitHub · ' + new Date().toLocaleTimeString([],{hour:'2-digit',minute:'2-digit'}));
  } catch(e) {
    pendingSave = false;
    setSyncStatus('error', 'Save failed — changes kept locally');
    showToast('GitHub save failed: ' + e.message);
  }
}
```

### Helper Functions
```js
function getPAT()  { return localStorage.getItem(LS_PAT) || ''; }
function getSHA()  { return localStorage.getItem(LS_SHA) || ''; }
function setSHA(s) { localStorage.setItem(LS_SHA, s); }
function configOk(){ return !!getPAT(); }

function persist() {
  try { localStorage.setItem(LS_DATA_KEY, JSON.stringify({ _version: DATA_VERSION, data: supplies })); }
  catch(e) {}
}

// persist() always fires first — safety net independent of GitHub
function scheduleSave() {
  persist();
  if (!configOk()) return;
  clearTimeout(saveTimer);
  saveTimer = setTimeout(saveToGitHub, 1200);
}

function resetLocalData() {
  if (!confirm('Clear locally cached data and reload?\n\nYour GitHub token will be kept — only data and the cached SHA are cleared.')) return;
  localStorage.removeItem(LS_DATA_KEY);
  localStorage.removeItem(LS_SHA);
  location.reload();
}
```

### Setup Banner & PAT Modal JS
```js
function updateSetupBanner() {
  const notice = document.getElementById('config-notice');
  if (configOk()) {
    notice.style.display = 'none';
    document.getElementById('btn-connect').style.display    = 'none';
    document.getElementById('btn-disconnect').style.display = '';
  } else {
    notice.style.display = '';
    document.getElementById('btn-connect').style.display    = '';
    document.getElementById('btn-disconnect').style.display = 'none';
  }
}

function openPATModal() {
  document.getElementById('pat-input').value = getPAT();
  document.getElementById('pat-modal').classList.add('open');
  setTimeout(() => document.getElementById('pat-input').focus(), 50);
}
function closePATModal() { document.getElementById('pat-modal').classList.remove('open'); }
function patBackdropClose(e) { if (e.target === document.getElementById('pat-modal')) closePATModal(); }

async function savePAT() {
  const val = document.getElementById('pat-input').value.trim();
  if (!val) { document.getElementById('pat-input').focus(); return; }
  localStorage.setItem(LS_PAT, val);
  closePATModal();
  updateSetupBanner();
  await syncFromGitHub();
}

function disconnectGitHub() {
  if (!confirm('Remove GitHub token from this browser?\n\nLocal data will be kept.')) return;
  localStorage.removeItem(LS_PAT);
  localStorage.removeItem(LS_SHA);
  updateSetupBanner();
  setSyncStatus('disconnected', 'Not connected to GitHub');
}
```

---

## 21. Init Pattern

```js
let saveTimer   = null;
let pendingSave = false;

window.addEventListener('beforeunload', e => {
  if (saveTimer || pendingSave) { e.preventDefault(); e.returnValue = ''; }
});

document.addEventListener('keydown', e => {
  if (e.key === 'Escape') { closeModal(); closePATModal(); }
  if (e.key === 'Enter' && document.getElementById('modal')?.classList.contains('open')
    && e.target.tagName !== 'TEXTAREA') { e.preventDefault(); saveItem(); }
  if (e.key === 'Enter' && document.getElementById('pat-modal')?.classList.contains('open')) {
    e.preventDefault(); savePAT();
  }
});

// ── Init ──
updateSetupBanner();
render();

if (configOk()) {
  syncFromGitHub();
} else {
  setSyncStatus('disconnected', 'Not connected to GitHub');
}
```

---

## 22. Meta Tags (all apps)

```html
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<meta name="apple-mobile-web-app-title" content="[App Short Name]">
<link rel="icon" type="image/png" href="data:image/png;base64,[base64-32x32]">
<link rel="apple-touch-icon" href="data:image/png;base64,[base64-180x180]">
<title>[App Name] — [Subtitle]</title>
```

**Icon rules:**
- Both `rel="icon"` and `rel="apple-touch-icon"` required
- Must be PNG base64 embedded — never a separate file
- Regenerate base64 PNGs via `cairosvg` whenever the icon SVG changes
- iOS home screen: Safari → Add to Home Screen (not Chrome)

---

## 23. Responsive Breakpoints

```css
@media (max-width:768px) {
  header { padding: 24px 20px 20px; }
  .sync-bar, .top-bar, .summary, .filters, .config-notice { padding-left: 16px; padding-right: 16px; }
  .grid { padding: 16px; gap: 12px; }
}
@media (max-width:480px) {
  header h1 { font-size: 1.7rem; }
  .grid { grid-template-columns: 1fr; }
}
```

---

## 24. Checklist — New App

Before shipping any new app, verify:

- [ ] Correct font load string (full weight set including `1,400;1,500`)
- [ ] `DATA_VERSION` constant with comment block
- [ ] `_version` included in GitHub payload
- [ ] `persist()` function present and called first in `scheduleSave()`
- [ ] `syncFromGitHub()` includes explicit 404 handling before generic `!res.ok` throw
- [ ] Config notice banner HTML + CSS (`border-radius: 4px`)
- [ ] PAT modal using CSS `.open` class toggle (not `display:flex/none`)
- [ ] Both modals use `border-top: 4px solid var(--[app]-rose/brass)`
- [ ] Sync bar uses dark background (not light/white)
- [ ] Sync bar ghost buttons use `background: transparent` (not white)
- [ ] Sync bar padding `8px 40px`
- [ ] Filter pills: all active states use same colour — no hierarchy distinction
- [ ] `resetLocalData()` confirm text mentions token is kept
- [ ] `beforeunload` guard in place
- [ ] Escape key closes modals
- [ ] `render()` called at init before `updateSetupBanner()`
- [ ] Mobile breakpoints: 768px and 480px both present
- [ ] Config notice included in mobile padding rule
- [ ] Page background is `#F5F2EC` (washi standard)
- [ ] Icons embedded as base64 PNG (not SVG, not external)
- [ ] Both `rel="icon"` and `rel="apple-touch-icon"` present
- [ ] Base64 PNGs regenerated from current SVG (not from a previous icon version)
- [ ] Icon SVG in header is `width="56" height="56" viewBox="0 0 56 56"`
- [ ] Icon background is visibly distinct from header background
- [ ] Card border-radius 12px
- [ ] Input border-radius 8px
- [ ] `:root` uses app-specific CSS variable names (no leftover template names)
