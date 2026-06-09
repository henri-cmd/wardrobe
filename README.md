# Wardrobe

A single-file web app to take stock of your clothes, spot the gaps, weigh up what to buy, and move things on — built to help you simplify your wardrobe.

It follows an item through its whole life: **Inventory** (what you own) → **Selling/Donating** (parting with) → **Decommissioned** (gone), with a **Wishlist** for the gaps you want to fill and the options you're comparing.

No build step, no dependencies, no account. Open `index.html` in a browser and go. Everything is saved locally in that browser via `localStorage`.

**Live:** <https://henri-cmd.github.io/wardrobe/>

## The four tabs

- **Inventory** — what you own (name, category, colour, brand, quantity, season), plus the **gaps** you've noted, grouped by category. "Items owned" counts total pieces, with a **×N** badge for multiples. The 🏷 tag on any item moves it to *For sale* or *To donate*.
- **Wishlist** — a shopping board organised **Category → Gap → Options**. Each gap nests the options you're comparing (brand, price, status, link); options not tied to a gap sit in a *Not tied to a gap* bucket — use the **◇** button to file one under an existing gap (or spin up a new gap on the spot). The **⧉** buttons open product links in bulk — every visible option at once, or just one gap's (or the loose bucket's). Mark an option **Bought** and it converts into an Inventory item and **fills its gap**.
- **Selling/Donating** — items you're parting with, tagged *for sale* (with an inline asking price; the tab totals what you'd recoup) or *to donate*. Mark one gone to send it to Decommissioned.
- **Decommissioned** — what's left your wardrobe (**sold** / **donated** / **retired**), with the price you sold it for and a *recouped from sales* total. Restore anything back to your wardrobe.

## Other features

- **Images** — give any item or option a picture: **upload** a file, **paste** an image, **fetch** it from a product link, or enter an image URL. Uploads are downscaled to fit local storage; click any thumbnail to view it full-size.
- **Add by link** — paste a product link and it auto-fills the **name**, **image** and **brand** (via the [microlink](https://microlink.io) metadata service, with an OpenGraph fallback).
- **Custom categories** — add your own (inline in any dropdown, or in Settings), rename, delete, or **drag to reorder** them. No built-in defaults — the taxonomy is entirely yours.
- **Views & ordering** — switch **any tab** (Inventory, Wishlist, Selling/Donating, Decommissioned) between **list** and image-forward **card** views; each tab remembers your choice. Sort Inventory by recent / name / colour, or pick **Custom order** and drag items to arrange them.
- **Yours, and portable** — JSON export / import for backups; everything (incl. images) stays in your browser. Every destructive action has an **Undo**.

## Keyboard shortcuts

`/` search · `n` new · `1`–`4` switch tabs · `esc` close

## Run it

Just open `index.html`, or serve the folder:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Tech

Plain HTML, CSS and vanilla JavaScript in a single file. Fonts via Google Fonts (DM Sans / DM Mono). State persists in `localStorage`; no backend.

The only network calls are optional: when you use **Add by link**, the URL is sent to [microlink](https://microlink.io) to fetch the title and image, with a [corsproxy.io](https://corsproxy.io) + OpenGraph-parsing fallback for shops microlink's free tier can't read (e.g. antibot-protected stores). Everything else runs entirely in your browser.
