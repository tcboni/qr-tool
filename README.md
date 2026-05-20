# QR Tool

A full-featured QR code and barcode utility that runs entirely in your browser.

**[→ Open QR Tool](https://tcboni.github.io/qr-tool/)**

## Features

### Compose

- **QR codes** for text/URL, Wi-Fi credentials, contacts (vCard), email, SMS, phone, location, and calendar events
- **1D barcodes**: Code 128, Code 39, EAN-13, EAN-8, UPC-A, ITF
- Customize foreground / background colors (color picker + hex input + preset swatches, including transparent)
- Error correction level (L / M / Q / H)
- Module style (square / rounded / dots)
- Finder eye style (square / rounded / circle / leaf)
- Frame styles (none / thin / thick / double / corners)
- Quiet zone, export size, center logo
- Live regeneration on every keystroke — no Generate button to click

### Decode

- Live camera scanning (uses browser-native `BarcodeDetector`)
- Drag, paste, or upload an image
- Auto-detects payload type (URL, Wi-Fi, contact, etc.) with contextual actions (open, copy password, download `.vcf`, open in maps, etc.)

### Batch

- Generate many codes at once from a line-separated list
- Optional labels per line
- Download all as PNGs or print as a sheet

### Library

- Pre-made templates for common patterns (Wi-Fi, vCard, payment URIs, app links, product barcodes, etc.)
- One click loads the template into Compose

### Saved

- Locally-stored library of saved codes with search and reuse
- Stored in `localStorage` — never leaves your machine

### Share

- Encode the entire current composition into a URL hash (`#s=…`)
- Recipients open the link and get the same code with all your settings

## Keyboard shortcuts

| Shortcut           | Action                                                      |
| ------------------ | ----------------------------------------------------------- |
| `⌘/Ctrl + 1` … `5` | Switch section (Compose / Decode / Batch / Saved / Library) |
| `⌘/Ctrl + S`       | Save current code                                           |
| `⌘/Ctrl + D`       | Download PNG                                                |
| `⌘/Ctrl + E`       | Download SVG                                                |
| `⌘/Ctrl + L`       | Copy share link                                             |
| `⌘/Ctrl + P`       | Print                                                       |
| `?`                | Show shortcuts help                                         |
| `Esc`              | Close help                                                  |

## Technical notes

- Single `index.html` file. CSS and JS are inline.
- No external scripts, no CDN, no fonts, no analytics.
- **QR encoder** implemented from scratch (ISO/IEC 18004 Model 2) — supports versions 1–40, all 4 error correction levels, numeric / alphanumeric / byte modes with UTF-8, automatic mode selection, automatic mask selection.
- **1D barcode encoders** (Code 128, Code 39, ITF, EAN-13, EAN-8, UPC-A) implemented from scratch.
- **Decoding** uses the browser-native `BarcodeDetector` API (Chrome, Edge, Safari). Firefox falls back to "no scan available" — image upload and camera both depend on this API.
- State persistence via `localStorage`.
- Share-link payload is base64-encoded JSON in the URL hash — no server, no shortener.
