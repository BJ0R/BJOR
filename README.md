# ✨ Interactive GitHub README + CSS Micro‑Interaction

> A polished README template with tasteful interactivity that works on GitHub, plus a **CSS‑only micro‑interaction** demo you can host via **GitHub Pages**.

<p align="center">
  <img src="https://img.shields.io/badge/License-MIT-informational" alt="license badge"/>
  <img src="https://img.shields.io/github/stars/yourname/yourrepo?style=social" alt="stars badge"/>
  <img src="https://img.shields.io/badge/Live%20Demo-GitHub%20Pages-blue" alt="demo badge"/>
</p>

<p align="center">
  <strong>🧪 Live Demo:</strong> <a href="https://yourname.github.io/yourrepo">yourname.github.io/yourrepo</a>  
  <em>(Update the link after enabling GitHub Pages.)</em>
</p>

---

## Overview

This template gives you:

* A **visually appealing README** with subtle built‑in interactivity using native `<details>` disclosure elements (fully supported on GitHub).
* A **CSS‑only micro‑interaction** (no JS) — a “Star” button with ripple + sparkle effects — shipped as a small `/demo` site for GitHub Pages.
* Accessibility‑minded, lightweight styles with `prefers-reduced-motion` support.

> ⚠️ **Why a separate demo?** GitHub READMEs are sandboxed (no custom `<style>` or JS). To ship a real CSS micro‑interaction, we host a tiny demo at `/demo` and link to it.

---

## 🌟 README Micro‑Interaction (works on GitHub)

You can add tasteful, zero‑CSS interactivity right in this README using `<details>`:

<details>
  <summary><strong>Click to reveal a tiny confetti GIF + tips</strong></summary>
  <br>
  🎉 *Surprise!* Use `<details>` to hide long sections, FAQs, or previews. Combine with small GIFs/SVGs for delight without extra CSS.
</details>

---

## 🚀 Quick Start

1. **Copy these files** into your repo (see file blocks below).
2. Push to GitHub.
3. **Enable GitHub Pages**: *Settings → Pages → Source: `main` → `/root`* (or `/docs` if you prefer).
4. Update the demo link at the top of this README.

---

## 🧩 File Tree

```
.
├── README.md                    # This file
└── demo/
    ├── index.html               # Micro‑interaction demo (no JS)
    └── styles.css               # Tiny, accessible CSS
```

---

## 📄 README.md (drop‑in)

Copy the entire contents of this document into your `README.md` and tweak the badges/links.

> The real micro‑interaction lives in `/demo`. For a quick peek, open it locally or via GitHub Pages.

---

## 🧪 /demo — CSS‑only Micro‑Interaction

### `demo/index.html`

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>CSS Micro‑Interaction – Star Button</title>
  <link rel="stylesheet" href="styles.css" />
  <meta name="color-scheme" content="light dark" />
</head>
<body>
  <main class="wrap" aria-label="CSS micro‑interaction demo">
    <section class="card">
      <h1>Star this project</h1>
      <p class="muted">A tiny, accessible, CSS‑only micro‑interaction (no JS).</p>

      <!-- Accessible toggle: checkbox holds state, label acts as button -->
      <input type="checkbox" id="star-toggle" class="visually-hidden" aria-label="Toggle star" />
      <label for="star-toggle" class="star-btn">
        <svg class="icon" viewBox="0 0 24 24" aria-hidden="true">
          <path d="M12 17.27L18.18 21l-1.64-7.03L22 9.24l-7.19-.61L12 2 9.19 8.63 2 9.24l5.46 4.73L5.82 21z"/>
        </svg>
        <span class="label">Star</span>
      </label>

      <p class="hint">Tip: try click, hover, and focus. Toggle persists while the page is open.</p>
    </section>

    <footer class="footer">
      <a href=".." class="back">← Back to README</a>
    </footer>
  </main>
</body>
</html>
```

### `demo/styles.css`

```css
/* -- Design tokens ------------------------------------------------------- */
:root {
  --bg: #0b0b10;
  --panel: #12121a;
  --text: #e9e9ef;
  --muted: #a5a7b0;
  --primary: #7aa2ff;
  --accent: #ffd166;
  --ring: #89b4fa;
  --shadow: 0 10px 30px rgba(0,0,0,.35);
}

@media (prefers-color-scheme: light) {
  :root { --bg:#fafafa; --panel:#ffffff; --text:#0b0b10; --muted:#69707f; --shadow:0 10px 30px rgba(0,0,0,.08); }
}

/* -- Layout -------------------------------------------------------------- */
* { box-sizing: border-box; }
html, body { height: 100%; }
body { margin:0; font: 16px/1.6 system-ui, -apple-system, Segoe UI, Roboto, Inter, sans-serif; background:var(--bg); color:var(--text); }
.wrap { min-height:100%; display:grid; place-items:center; padding: 48px 20px; }
.card { width:min(720px, 92vw); background:var(--panel); border-radius:24px; padding:32px; box-shadow:var(--shadow); border:1px solid rgba(255,255,255,.06); }
.card h1 { margin:0 0 6px; font-weight:750; letter-spacing:.2px; }
.card .muted { margin:0 0 20px; color:var(--muted); }
.footer { margin-top: 24px; text-align:center; }
.back { color:var(--primary); text-decoration:none; }
.back:hover { text-decoration:underline; }

/* -- Accessibility helpers ---------------------------------------------- */
.visually-hidden { position:absolute; width:1px; height:1px; margin:-1px; padding:0; overflow:hidden; clip:rect(0 0 0 0); clip-path: inset(50%); border:0; white-space:nowrap; }
:focus-visible { outline: none; box-shadow: 0 0 0 3px var(--ring); border-radius: 12px; }

/* -- Star button --------------------------------------------------------- */
.star-btn { position: relative; display:inline-grid; grid-auto-flow:column; align-items:center; gap:.6rem; cursor:pointer; user-select:none; border-radius:16px; padding:12px 18px; background:linear-gradient(180deg, rgba(255,255,255,.06), rgba(0,0,0,.08)); border:1px solid rgba(255,255,255,.10); transition: transform .15s ease, border-color .2s ease; }
.star-btn .icon { width:22px; height:22px; fill: none; stroke: none; }
.star-btn .label { font-weight:650; letter-spacing:.2px; }

/* Hover lift + subtle ripple seed */
.star-btn:hover { transform: translateY(-1px); }
.star-btn:active { transform: translateY(0); }

/* Ripple on click (no JS): use ::after seeded & animated on :active) */
.star-btn::after { content:""; position:absolute; inset:0; border-radius: inherit; pointer-events:none; opacity:0; background: radial-gradient( circle at var(--x,50%) var(--y,50%), rgba(255,255,255,.35), transparent 45% ); }
.star-btn:active::after { animation: ripple .5s ease forwards; }

@keyframes ripple { from { opacity:.35; } to { opacity:0; transform: scale(1.08); } }

/* Sparkle burst when checked */
.star-btn::before { content:""; position:absolute; inset:-6px; border-radius:inherit; pointer-events:none; opacity:0; background:
  radial-gradient(6px 6px at 20% 30%, var(--accent), transparent 60%),
  radial-gradient(5px 5px at 75% 35%, #fff6b3, transparent 60%),
  radial-gradient(4px 4px at 40% 80%, #ffe08a, transparent 60%),
  radial-gradient(5px 5px at 60% 65%, #fff, transparent 60%);
  filter: blur(.2px);
}

/* Checkbox drives state */
#star-toggle:checked + .star-btn { border-color: rgba(255,209,102,.7); box-shadow: 0 8px 24px rgba(255,209,102,.18), inset 0 0 0 1px rgba(0,0,0,.06); }
#star-toggle:checked + .star-btn .icon { fill: var(--accent); }
#star-toggle:checked + .star-btn .label::after { content:"d"; /* Star -> Starred */ }

#star-toggle:checked + .star-btn::before { animation: burst .6s cubic-bezier(.2,.7,.2,1) forwards; }

@keyframes burst {
  0% { opacity:0; transform: scale(.8) rotate(0deg); }
  20% { opacity:1; transform: scale(1.04) rotate(8deg); }
  100% { opacity:0; transform: scale(1.3) rotate(0deg); }
}

/* Motion safety */
@media (prefers-reduced-motion: reduce) {
  .star-btn, .star-btn::before, .star-btn::after { transition: none; animation: none !important; }
}

/* Pointer‑positioned ripple (progressive enhancement) ------------------- */
/* Without JS, we default ripple center to 50%/50%. To enhance, you can
   optionally add a tiny JS snippet to set --x/--y on pointermove/down.
   Purists can omit; the effect still works. */
```

---

## 🧭 How it works

* **State without JS:** A hidden checkbox `#star-toggle` holds the on/off state. The label next to it is the clickable control.
* **Animations:**

  * Press ripple: `:active` triggers `::after` with a radial‑gradient that fades out.
  * Success burst: `#star-toggle:checked + .star-btn::before` fires a one‑shot sparkle keyframe.
  * Icon fill: the star path fills with `--accent` when checked.
* **A11y:** The input has an `aria-label`, focus is visible, and motion respects `prefers-reduced-motion`.

---

## 🛠 Local preview

Open `demo/index.html` in a browser (double‑click). That’s it.

---

## 🌐 Publish on GitHub Pages

1. Push the repo to GitHub.
2. Go to **Settings → Pages**.
3. Set **Source** to your branch (e.g., `main`) and **/root** (or `/docs`).
4. Your demo will be available at `https://<username>.github.io/<repo>/`.

> Update the Live Demo link at the top of the README.

---

## ✅ Checklist

* [ ] Replace `yourname/yourrepo` in badges & links
* [ ] Enable GitHub Pages
* [ ] Tweak colors/rounding in `styles.css`
* [ ] Add a project banner image or SVG logo

---

## 📎 Extras (optional)

* Add a small **SVG banner** or logo at the top of the README for branding.
* Record a short **GIF** of the micro‑interaction and embed it in the README.
* Add a **dark/light** logo swap using two images with a `<picture>` element on the demo page.

---

## 📝 License

MIT — do whatever, just keep the notice.
