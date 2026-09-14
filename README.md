# RT Clock — Connect

A copy of [RT Clock v2.1](https://github.com/jfailing/rt-clock) with every external network call removed, for viewing in locked-down/offline environments (e.g. Posit/RStudio Connect on a corporate network with no internet access).

## What's different from the main repo

The only external calls in the original files were three Google Fonts `<link>` tags (one per file: `rt-clock-v2.1.html`, `rt-clock-config.html`). There were no `fetch`/`XMLHttpRequest`/`WebSocket` calls anywhere — it's mock-data mode already. Those links are removed here, and every font reference across the four themes (Classic, Minimal, Premium, Control Room) and the config editor's font picker has been swapped for an OS-native/web-safe equivalent:

| Original (Google Font) | Native replacement |
|---|---|
| Rajdhani | Trebuchet MS / Segoe UI |
| IBM Plex Mono | Consolas / Courier New |
| IBM Plex Sans | Segoe UI / Arial |
| Jost | Calibri / Segoe UI |
| Cormorant Garamond | Constantia / Cambria / Georgia |
| Barlow Condensed | Arial Narrow / Segoe UI |
| JetBrains Mono | Consolas / Courier New |
| Share Tech Mono | Consolas / Courier New |
| Orbitron | Segoe UI (editor chrome) / Consolas (font picker option) |
| Exo 2 | Calibri |
| Oswald | Arial Narrow |
| Bebas Neue | Impact |

`speechSynthesis` and `AudioContext` (Web Speech / Web Audio APIs) are untouched — they're local browser APIs, not network calls, and work fine offline.

Everything else — layout, alarm logic, canvas rendering, config editor, localStorage persistence — is identical to the source. This repo is a snapshot; it isn't kept in sync automatically with the main `rt-clock` repo.

## Files

- `rt-clock-v2.1.html` — main clock display
- `rt-clock-config.html` — configuration editor (opens in an iframe from the main display)

Both are self-contained, no build step, no dependencies. Open `rt-clock-v2.1.html` directly, or serve both files from the same directory.
