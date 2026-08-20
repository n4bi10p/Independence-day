# 15 August — India, As We Remember It 🇮🇳

> A cinematic, nostalgic Independence Day memory experience — liquid-glass UI, illustrated storytelling, ambient sound, and a collective memory wall.

**Live:** `https://n4bi10p.github.io/Independence-day` · **Repo:** `https://github.com/n4bi10p/Independence-day` · **Made by:** [Nabil](https://n4bi10p.github.io)

---

## Preview

The site is a single-page editorial experience built as a Vite + React shell with all UI in `index.html` (3470 lines). It blends a nostalgic video backdrop, interactive hotspots, a liquid-glass music player, and a localStorage-backed memory wall.

- **Hero** — Hindi headline, kites canvas, glass nav (Home / Memories), clock, flag dock
- **5 Memory Chapters** — each with a distinct artwork from `public/assets/`
- **Memory Wall** — Pin / Share your memory → saves to `localStorage`, survives reload
- **Live Now / Total Visits** — cross-tab `BroadcastChannel` + `localStorage` counter (nav pill)
- **Music Player** — YouTube playlist, vinyl disc, seek bar `576 × 106.5`, mute with `M` / `SPACE`
- **Hotspots** — 6 beacons on the hero artwork, toggle via eye icon

---

## Features

- Premium liquid-glass design (blur `28–32px`, `saturate 150–175%`, hairline borders)
- Responsive (mobile: 900px breakpoint, stacked chapters)
- YouTube IFrame player with custom seek + vinyl spin + visualizer
- Web Audio ambient bed (optional)
- Petal celebration canvas on memory submit
- Indian flag favicon (`public/favicon.svg`)

---

## Tech Stack

- **Build:** Vite 6 + `@vitejs/plugin-react` + `@tailwindcss/vite`
- **UI:** React 19, Tailwind 4, `lucide-react`, `motion`
- **Server (optional):** Express 4 + `dotenv` (for preview)
- **No backend required** — memories and visits are client-side (`localStorage` + `BroadcastChannel`)

---

## Getting Started

**Prerequisites:** Node.js 18+

```bash
npm install
npm run dev      # http://localhost:3000
npm run build    # → dist/
npm run preview  # serve dist/
```

No env vars needed. The YouTube playlist is public (no API key).

---

## Project Structure

```
.
├── index.html              # entire app (head styles + body + <script>)
├── public/
│   ├── favicon.svg         # Indian flag
│   ├── artwork.png         # master artwork (1536×1024)
│   ├── video.mp4
│   └── assets/             # 11 chapter artworks (copied from assets/)
├── assets/                 # source images (also copied to public/assets)
├── src/
│   ├── main.tsx
│   ├── App.tsx
│   └── index.css
├── vite.config.ts
└── package.json
```

- `public/` is served at `/` by Vite — `public/assets/*.png` → `/assets/*.png`
- `assets/` is the source folder (kept for authoring, copied to `public/assets` for serving)

---

## Scripts

| Command | Description |
|---------|-------------|
| `npm run dev` | Dev server with HMR |
| `npm run build` | Production build |
| `npm run preview` | Preview `dist/` |
| `npm run lint` | `tsc --noEmit` |

---

## Assets & Artwork

Chapter nodes use distinct files (not a single cropped sprite):

- `OpenAI Playground 2026-08-15 at 12.52.29 (0).png` → Chapter 01
- `OpenAI Playground 2026-08-15 at 12.52.29 (1).png` → Chapter 02
- `OpenAI Playground 2026-08-15 at 12.52.42 (0).png` → Chapter 03
- `OpenAI Playground 2026-08-15 at 12.52.42 (1).png` → Chapter 04
- `OpenAI Playground 2026-08-15 at 12.53.19 (1).png` → Chapter 05

Postage stamps on memory cards use `/assets/artwork.png`.

---

## Persistence

- **Memories:** `localStorage["ind_memories_v1"]` — array of `{id, text, author, dateLabel, stampPos, ts}`. Empty state shows “No memories yet”.
- **Total visits:** `localStorage["ind-total-visits"]` incremented on each load.
- **Live now:** `BroadcastChannel("ind-live-visitors")` peer map with 4s TTL, rendered every 2s.

---

## Deployment

Any static host works (GitHub Pages, Vercel, Netlify):

```bash
npm run build
# upload dist/ — public/ is already inlined/copied by Vite
```

For GitHub Pages, set `base` in `vite.config.ts` if serving from `/Independence-day/`.

---

## Credits

- Design & code — [Nabil](https://n4bi10p.github.io) (`made by Nabil` pill at bottom-right)
- Illustrations — OpenAI / ChatGPT generated for 15 August series
- Type — Tiro Devanagari Hindi, Rozha One, Cormorant Garamond, Plus Jakarta Sans, Caveat

---

## License

MIT — do what you want, keep the attribution.
