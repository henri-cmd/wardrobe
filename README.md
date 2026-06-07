# Wardrobe

A single-file web app to take stock of your clothes, spot the gaps, and weigh up what to buy — built to help you simplify your wardrobe.

No build step, no dependencies, no account. Open `index.html` in a browser and go. Everything is saved locally in that browser via `localStorage`.

**Live:** <https://henri-cmd.github.io/wardrobe/>

## Features

- **Inventory** — log what you own (name, category, colour, brand, quantity, season), grouped by category with a live distribution strip. "Items owned" counts total pieces (quantities), and a **×N** badge shows multiples. Tag items **keep / donate** to declutter.
- **Wishlist** — your **gaps** and the **options** to fill them, sorted into the same categories as your wardrobe. Gaps carry a priority; options carry a brand, price, status (considering / shortlisted / bought / passed), a link, and a running shortlist total. Each category shows how many you already own, so you can tell whether something fills a real gap.
- **Images** — give any item or option a picture: **upload** a file, **paste** an image, **fetch** it from a product link, or enter an image URL. Uploads are downscaled to fit local storage; click any thumbnail to view it full-size.
- **Add by link** — paste a product link on an item or option and it auto-fills the **name**, **image** and **brand** (via the [microlink](https://microlink.io) metadata service, with an OpenGraph fallback).
- **Custom categories** — add your own categories (inline in any category dropdown, or in Settings), rename, delete, or **drag to reorder** them; they group and persist like the rest. No built-in defaults — the taxonomy is entirely yours.
- **Views & ordering** — switch Inventory between a **list** and an image-forward **card** view, sort by recent / name / colour, or pick **Custom order** and drag items to arrange them within each category.
- **Flows** — turn a gap into an option, then drop a bought option straight into your wardrobe.
- **Yours, and portable** — JSON export / import for backups; your wardrobe data stays in your browser.

## Keyboard shortcuts

`/` search · `n` new · `1` / `2` switch tabs · `esc` close

## Run it

Just open `index.html`, or serve the folder:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Tech

Plain HTML, CSS and vanilla JavaScript in a single file. Fonts via Google Fonts (DM Sans / DM Mono). State persists in `localStorage`; no backend.

The only network calls are optional: when you use **Add by link**, the URL is sent to [microlink](https://microlink.io) to fetch the title and image, with a [corsproxy.io](https://corsproxy.io) + OpenGraph-parsing fallback for shops microlink's free tier can't read (e.g. antibot-protected stores). Everything else runs entirely in your browser.
