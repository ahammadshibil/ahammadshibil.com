# Site Context — ahammadshibil.com

## File structure

- Single file: `index.html`
- No build step, no framework. Plain HTML + CSS + vanilla JS.
- Deploy: push to GitHub → Netlify/Vercel auto-deploys.

## Owner

- **Name:** Ahammad Shibil
- **Location:** Chennai, India
- **Role:** Investment Analyst, Speciale Invest (pre-seed/seed deeptech VC)
- **Background:** Biology researcher (IISER Kolkata, BS-MS) → founder (Inarihealth) → ops (TeOra) → VC → founding bio-AI company
- **Writing:** Atoms & Cells — atomsandcells.substack.com
- **Twitter:** @ShibilAhammad
- **LinkedIn:** /in/ahammadshibil
- **GitHub:** /ahammadshibil
- **Medium:** @shibilahammad
- **Email:** shibil.ahammad@specialeinvest.com

## Design system

### Fonts

- Body / headings: **EB Garamond** (Google Fonts)
- Labels / meta / nav / tags: **DM Mono** (Google Fonts)

### Colors — Light mode

| Token     | Value     | Use                                    |
|-----------|-----------|----------------------------------------|
| --bg      | #f7f4ef   | Page background                        |
| --ink     | #1a1714   | Body text                              |
| --muted   | #8a8178   | Labels, metadata, secondary text       |
| --accent  | #2d5a3d   | Links, hover, CTAs, buttons            |
| --rule    | #ddd8d0   | Dividers, card borders                 |
| --card    | #ffffff   | Card backgrounds                       |

### Colors — Dark mode (`[data-theme="dark"]` on `<html>`)

| Token     | Value     |
|-----------|-----------|
| --bg      | #141210   |
| --ink     | #e8e4de   |
| --muted   | #6b6560   |
| --accent  | #6aab80   |
| --rule    | #2a2722   |
| --card    | #1e1b18   |

## Layout

- Max width: 660px, centered
- Single column throughout
- Section dividers: `<hr />`
- Section labels: `<div class="label">text</div>` — DM Mono, uppercase, tracked

## Navigation

Eight views, JS hash routing via `show(viewName)`:
**home · about · writing · thesis · literature · bookshelf · now · connect**

Nav has dark mode toggle button (`#theme-btn`) top right.

## Writing section

Articles are `<li>` elements inside `#writing-list`.

To add an article:
```html
<li data-cat="CATEGORY">
  <div class="w-row" onclick="togglePreview(this)">
    <span class="date">YEAR</span>
    <span class="w-title">Article Title</span>
    <span class="tag">CATEGORY</span>
  </div>
  <div class="w-preview">
    <p><em>2–3 sentence preview of the piece.</em></p>
    <a href="SUBSTACK_URL" target="_blank">Read on Substack →</a>
  </div>
</li>
```

Valid `data-cat` values: `biology` | `ai` | `investments` | `philosophy`

Only one preview open at a time (accordion). Filter buttons close open previews.

## Literature (poems)

Poems are accordion items inside `#poem-list`:
```html
<li>
  <div class="poem-title" onclick="togglePoem(this)">Poem Title</div>
  <div class="poem-body">
    <p>Line one<br/>Line two</p>
  </div>
</li>
```

## Key JS functions

| Function | What it does |
|----------|-------------|
| `show('view')` | Switch active view |
| `filterWriting('cat', btn)` | Filter writing list by category |
| `goWriting('cat')` | Navigate to writing + filter |
| `togglePreview(rowEl)` | Open/close article preview |
| `togglePoem(titleEl)` | Open/close poem |
| `toggleTheme()` | Switch dark/light, saves to localStorage |
| `handleSubscribe()` | Validate email → redirect to Substack |

## Substack subscribe

- Block lives on home view, above footer
- On submit: validates email, shows confirmation, opens Substack subscribe URL with email pre-filled
- URL pattern: `https://atomsandcells.substack.com/subscribe?email=EMAIL`

## SEO / Meta

- `og:url`: `https://ahammadshibil.com` — update once domain is live
- `og:image`: not set yet — add once you have a profile photo hosted
- Twitter card type: `summary` — upgrade to `summary_large_image` once og:image is added

## Pending / known placeholders

- [ ] Instagram handle — replace `@your_handle` in connect view
- [ ] Portrait photo — replace placeholder div with `<img src="./shibil.jpg">`
- [ ] Grandfather photo — replace placeholder div with `<img src="./grandfather.jpg">`
- [ ] Writing article URLs — replace `#` hrefs with real Substack/Medium post URLs
- [ ] `og:image` meta tag — add once photo is hosted
- [ ] `og:url` — confirm final domain

## Common edit patterns

**Update the Now page:** Find `id="view-now"`, edit content inside. Always include current month/year.

**Change homepage intro line:** Find `<p class="intro">` in `id="view-home"`.

**Add a thesis entry:** Find `id="view-thesis"`, copy an existing `.thesis-entry` block.

**Change accent color:** Update both `--accent: #2d5a3d` (light) and `--accent: #6aab80` (dark) in `:root` and `[data-theme="dark"]`.
