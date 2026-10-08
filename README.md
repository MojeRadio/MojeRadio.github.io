
# My Radio — PWA radio player

A lightweight, offline-capable **Progressive Web App** for listening to internet radio streams. Built as a single self-contained HTML file with zero build step — just open it and it works.

**Live demo:** https://mojeradio.pages.dev/

---

## ✨ Features

### Playback
- Plays MP3, AAC, OGG streams and **HLS (`.m3u8`)** — with automatic fallback to `hls.js` on browsers without native HLS support
- Automatic stream recovery after dropouts: fast retries, then slow background reconnects, plus wake-from-sleep detection
- **Smart HTTPS routing** — HTTP streams on an HTTPS page are first tried directly via TLS, then routed through a Cloudflare Worker proxy
- **ICY metadata** — reads now-playing track titles directly from the audio stream
- Alternative track-title sources: HTTP JSON/XSPF/7.html endpoints, or manual entry
- **Media Session API** — lock-screen / notification controls (play, pause, prev, next)
- **Wake Lock** — keeps the screen on while playing
- Soft-pause: keeps the stream alive for 60 s after pausing for instant resume
- Sleep timer

### Stations
- Add, edit, delete, reorder (drag & drop on desktop, long-press on touch)
- **Search** via radio-browser.info with genre and country filters
- Share stations as compact base64 links (`?a=...`)
- Import / export station lists as JSON
- **Sync from a remote file** — stations, settings, and parameters pulled from a Google Doc or any URL
- Automatic favicon fetching from multiple sources (radio-browser, site favicons, image search)
- Color auto-detection from station logos

### Interface
- **16 color themes** — light, dark, and neumorphic variants, with automatic sun/moon switching by device preference or Warsaw sunrise/sunset times
- **3 languages** — Ukrainian, Polish, English
- Two view modes: **grid** (paginated) and **list**
- **Compact landscape layout** — auto-activates on wide-low viewports
- Three center-element modes: audio visualizer, pulsing circle, or station logo
- Real audio visualizer (Web Audio API) with automatic simulation fallback
- **5-band equalizer** with 12 presets
- Volume normalization across stations
- Interface scale slider (50–150%)
- PWA install — works offline, appears as a native app

### Privacy / Network
- **No tracking, no analytics, no ads** — all settings stored locally in `localStorage`
- Optional CORS proxy via a self-hosted Cloudflare Worker (the URL is configurable)
- Visitor counter (opt-in, disabled by default)

---

## 🛠 Tech stack

- **Vanilla JavaScript** — no frameworks, no build tools, no dependencies
- **Single HTML file** — the entire app is one `index.html`
- CSS Custom Properties for theming, `clip-path`/`transform` for 60 fps visualizations
- **Cloudflare Worker** as the CORS proxy and ICY metadata endpoint
- Progressive Web App — `manifest.json` + service worker friendly
- Radio station metadata from [radio-browser.info](https://www.radio-browser.info/)

---

## 🚀 Getting started

### Option 1: Use the hosted version
Open https://mojeradio.netlify.app/

### Option 2: Run locally
```bash
git clone https://github.com/<your-username>/<your-repo>.git
cd <your-repo>
# Any static server works:
python3 -m http.server 8000
# or
npx serve
```
Then open `http://localhost:8000`.

> **Note:** microphones, Wake Lock, and Media Session require HTTPS in production. For a fully working deployment, host on Netlify, Cloudflare Pages, GitHub Pages, or any HTTPS-static host.

### Option 3: Self-host the proxy (optional but recommended)
For reliable playback of HTTP streams from an HTTPS page, deploy your own Cloudflare Worker and put its URL in the app's **Sync → Worker URL** field.

---

## ⚙️ Configuration

All settings are managed in-app:

- **Options** — language, theme, view mode, center element, sleep timer
- **Advanced** — scale, equalizer, audio visualizer, volume normalization
- **Sync** — stations file URL, sync interval, worker URL, backup search URL
- **Developer mode** — long-press the play/pause button to toggle. Unlocks diagnostic logs, forced landscape/portrait, proxy testing, and the visitor counter

---

## 🎨 Themes

16 built-in themes with light/dark pairs, plus 3 neumorphic sets:

| Light | Dark |
|---|---|
| Classic · Forest · Blue · Tangerine · Ocean · Burgundy | Indigo dark · Sage · True Black · Copper · Teal · Cherry |
| Neo Light · Neo Sage · Neo Azure | Neo Dark · Neo Sage Dark · Neo Azure Dark |

---

## 🌍 Languages

- 🇺🇦 Українська
- 🇵🇱 Polski
- 🇬🇧 English

Adding a new language is a matter of extending the `I18N` object in the script.

---

## 📄 License

**Personal use only.**

This project is **not** free for commercial use. You may use, modify, and adapt it for your own personal, non-commercial purposes. Any commercial use — including but not limited to resale, monetization, inclusion in a paid product or service, or use inside a for-profit organization — is **strictly prohibited** without the author's prior written permission.

To obtain a commercial license, contact the author directly:

📧 **tsuand@gmail.com**

Attribution to the original author is appreciated but not required for personal use.

---

## 🙏 Credits

- Station metadata: [radio-browser.info](https://www.radio-browser.info/)
- Icons: custom SVG, no external icon fonts
- Font: [Manrope](https://fonts.google.com/specimen/Manrope)

---

## 🇺🇦 Українською

**My Radio** — це легкий офлайн-сумісний PWA-плеєр для інтернет-радіо. Один HTML-файл, без збірки й залежностей.

**Можливості:** підтримка MP3/AAC/OGG/HLS, автовідновлення потоку, ICY-метадані, керування зі шторки (Media Session), Wake Lock, сон-таймер, пошук станцій через radio-browser.info, drag-and-drop сортування, синхронізація списку з віддаленого файлу, імпорт/експорт JSON, 16 кольорових тем (включно з неоморфними), 3 мови, 5-смуговий еквалайзер, реальний і симульований аудіовізуалізатор, вирівнювання гучності, компактний горизонтальний вигляд, масштаб інтерфейсу 50–150%, без трекінгу й реклами.

**Демо:** https://mojeradio.pages.dev/

**Ліцензія:** лише для власного (некомерційного) використання. Для комерційних цілей потрібен попередній письмовий дозвіл автора — пишіть на **tsuand@gmail.com**.


```
pwa  radio  radio-player  internet-radio  vanilla-javascript  no-dependencies  single-file  audio-player  hls  equalizer  web-audio  cloudflare-worker  netlify  offline-first  ukrainian  polish
```


Бейдж `license-personal use only-orange` добре сигналізує користувачам, що це не MIT, а `commercial-contact author-red` — що для комерції треба писати лист.
