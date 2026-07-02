# Vast Wireframes — Project Notes

## What This Is
HTML wireframes for the Vast website refresh. Each page is a single self-contained HTML file that opens directly in a browser — no build tools or installs needed.

**GitHub repo:** https://github.com/vast-megan/vast-wireframes
**Live URL:** https://vast-megan.github.io/vast-wireframes/

---

## How to Deploy to GitHub Pages

GitHub Pages is already set up on this repo. Any time you commit and push changes, the live site updates automatically within 1–2 minutes.

**Settings (already configured — don't change):**
- Settings → Pages → Source: **Deploy from a branch**
- Branch: **main**, Folder: **/ (root)**
- Do NOT switch to "GitHub Actions" — it fails for this setup

**The `.nojekyll` file in the repo root is required.** It tells GitHub Pages to skip its default website builder (Jekyll) and just serve the files directly. Don't delete it.

---

## File Structure

```
/                          ← repo root
├── index.html             ← redirects to wireframes/customers.html
├── .nojekyll              ← required for GitHub Pages (do not delete)
├── .gitignore             ← excludes WebsiteRefresh/ and .DS_Store
└── wireframes/
    ├── wireframes-notes.md  ← this file
    ├── customers.html       ← Customers page wireframe
    └── Logos/
        └── Vast_Wordmark_Meteorite_Black_RGB.png
```

---

## Adding a New Page

1. Copy `customers.html` and rename it (e.g. `home.html`)
2. Place it in the `wireframes/` folder
3. Update `index.html` at the root if you want the live URL to open that page by default
4. If the page uses images or logos, put them in `wireframes/Logos/` and reference them as `Logos/filename.png`
5. Commit and push — Pages updates automatically

---

## Asset Path Rules

- All logos and images must use **relative paths** from inside the `wireframes/` folder
- Example: `Logos/Vast_Wordmark_Meteorite_Black_RGB.png` ✓
- Never use absolute paths (starting with `/Users/...`) — they only work on your computer, not on GitHub
- Never reference files from `WebsiteRefresh/` — that folder is excluded from git and won't deploy

---

## DVB Accordion (Dropdown Video Block)

The expandable section component used on the Customers page.

**Behavior:**
- Click a row to open it; the previously open row closes automatically
- First item starts open by default (has the `open` class in the HTML)
- Description text is hidden when collapsed, visible when open (appears to the right of the title on desktop)
- No scroll-triggered behavior — click only

**To add a new DVB item**, copy this HTML block and paste it inside the `.wf-sec` div:

```html
<div class="dvb-item">
  <div class="dvb-row">
    <div class="dvb-title">Section title here</div>
    <div class="dvb-desc">Short description here.</div>
    <div class="dvb-toggle">+</div>
  </div>
  <div class="dvb-body">
    <div class="dvb-img-block">[ Image placeholder label ]</div>
  </div>
</div>
```

---

## Desktop vs. Mobile Preview

Each wireframe has both desktop (1200px) and mobile (390px) views built in. Toggle between them using the buttons in the top-right corner of the page. The layout is controlled by the `setView()` JavaScript function — no need to resize your browser window.

---

## Design Tokens (from the Vast Design System)

| Token | Value | Use |
|---|---|---|
| Meteorite Black | #2A2C2F | Headings, dark backgrounds |
| Moon Rock | #B3ABA3 | Secondary text on dark |
| Warm Gray | #ECE8E3 | Light section backgrounds |
| Warm White | #FDFCF4 | Preferred light background |
| Asteroid Dust | #897F75 | Muted text |
| Solar Orange | #FF5623 | Accent only — not for section backgrounds |

**Spacing scale (4px base):** 4 / 8 / 12 / 16 / 20 / 32 / 40 / 64 / 80 / 96 / 120 / 160px

**Typefaces:** Owners (primary), Phonic Mono (eyebrows/labels only)
