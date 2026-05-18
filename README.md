# CampusTrace — Lost & Found Portal

> A community-driven lost and found web app built for JNTUH campus, featuring AI-powered item matching, an interactive campus map, and a Humanity Score leaderboard.

---

## Features

**Posts Board**
- Report lost or found items with a name, description, location, date, and optional photo
- Mark items as urgent (ID cards, keys, wallets, exam tickets)
- Search and filter posts by type (Lost / Found / Urgent)
- Resolve posts to remove them once an item is returned

**AI-Powered Matching**
- When a new post is submitted, Claude (claude-sonnet-4) automatically scans existing opposite-type posts for potential matches
- If a likely match is found, a banner surfaces the matching person's name and contact details

**Campus Map**
- Interactive Leaflet map centered on JNTUH campus
- Drop a pin while reporting to geo-tag an item's location
- All pinned posts appear on the map with red (lost) and green (found) markers
- Click any marker to see item details

**Humanity Score Leaderboard**
- Points are awarded for community helpfulness:
  - Reporting a found item → **+5 pts**
  - Resolving a lost item → **+10 pts** (or **+15 pts** for urgent items)
  - Original reporter also earns **+5 pts** on resolution
- Weekly leaderboard resets every Monday at 12:00 AM
- "Helpful Human of the Week" crown goes to the top scorer

---

## Tech Stack

| Layer | Technology |
|---|---|
| UI | HTML, CSS, Vanilla JS |
| Fonts | Syne (headings), DM Sans (body) via Google Fonts |
| Map | Leaflet.js + OpenStreetMap tiles |
| AI Matching | Anthropic Claude API (`claude-sonnet-4-20250514`) |
| Storage | Browser `localStorage` |

---

## Project Structure

```
campustrace/
├── index.html          # Single-file app (all HTML, CSS, JS)
└── README.md
```

All logic, styles, and markup live in `index.html`. No build step or framework is required.

---

## Getting Started

**1. Clone or download the repo**

```bash
git clone https://github.com/your-username/campustrace.git
cd campustrace
```

**2. Set up the Anthropic API key**

The AI match feature calls the Anthropic API. In `index.html`, the fetch call to `https://api.anthropic.com/v1/messages` requires a valid API key passed in the request headers.

> ⚠️ For production use, never expose your API key in client-side JavaScript. Route the request through a backend proxy or serverless function instead.

**3. Open in a browser**

```bash
# No server needed — just open the file
open index.html
```

Or serve it locally:

```bash
npx serve .
# Visit http://localhost:3000
```

---

## Usage

**Reporting an item**
1. Click **+ Report Lost** or **+ Report Found** in the navbar
2. Fill in the item name, description, and campus location
3. Optionally upload a photo and drop a pin on the modal map
4. Submit — the AI matcher runs automatically in the background

**Resolving an item**
1. Find the matching post on the board
2. Click **Resolved ✓**
3. Enter your name and contact to claim humanity points
4. The post is removed and scores are updated

**Viewing the map**
- Click the **Campus Map** tab to see all geo-tagged posts
- Red markers = lost items, green markers = found items

**Leaderboard**
- Click the **Humanity Score** tab to view the weekly standings

---

## Data & Privacy

All data is stored in the browser's `localStorage`. No server-side database is used. Clearing browser storage will erase all posts and scores. There is no user authentication — names and contact details are self-reported.

---

## Limitations & Roadmap

- [ ] Backend / database for persistent, cross-device storage
- [ ] User authentication (college email login)
- [ ] Push notifications for AI match alerts
- [ ] Image hosting (currently stored as base64 in localStorage — large photos may hit storage limits)
- [ ] Admin panel for moderation
- [ ] Mobile app (PWA)

---

## Contributing

Pull requests are welcome. For major changes, open an issue first to discuss what you'd like to change.

---

## License

MIT
