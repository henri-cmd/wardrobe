# Wardrobe

A single-file web app to take stock of your clothes, spot the gaps, and weigh up what to buy — built to help you simplify your wardrobe.

No build step, no dependencies, no account. Open `index.html` in a browser and go. Everything is saved locally in that browser via `localStorage`.

**Live:** <https://henri-cmd.github.io/wardrobe/>

## Features

- **Inventory** — log what you own (name, category, colour, brand, season), grouped by category with a live distribution strip and colour swatches. Tag items **keep / donate** to declutter.
- **Wishlist** — your **gaps** and the **options** to fill them, sorted into the same categories as your wardrobe. Gaps carry a priority; options carry a price, status (considering / shortlisted / bought / passed), a link, and a running shortlist total. Each category shows how many you already own, so you can tell whether something fills a real gap.
- **Add by link** — paste a product link on an item or option and it auto-fills the **name** and **image** (via the [microlink](https://microlink.io) metadata service); or paste an image URL yourself. Thumbnails show throughout.
- **Custom categories** — add your own categories (inline in any category dropdown, or in Settings) alongside the built-ins; they group and persist like the rest.
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

The only network call is optional: when you use **Add by link**, the URL is sent to the hosted [microlink](https://microlink.io) API to fetch the title and image (free tier ~50/day). Everything else runs entirely in your browser.
