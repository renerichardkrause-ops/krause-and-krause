# Krause Management

Personal-brand website for **Krause Management** — René-Richard Krause, a
revenue & sales advisor for Estonian B2B founders in the €1–10M range.

- **René-Richard Krause** — Revenue, sales, go-to-market

> **Note:** The site originally launched as a two-person practice ("Krause &
> Krause", with cousin Revo Krause covering legal/tax/change). Revo can't be
> marketed while in his current public-sector role, so the live site is
> René-Richard solo. All of Revo's removed copy is stashed in
> `../revo-stash.md` for a clean re-add later.

## Stack

Single static HTML file. No build step.

- `index.html` — the entire site, with inline CSS and a small IntersectionObserver
- Google Fonts: Instrument Serif + IBM Plex Sans + IBM Plex Mono
- No JS framework, no bundler, no dependencies

## Run locally

```bash
# Python
python3 -m http.server 4321

# or any static server
npx serve -l 4321 .
```

Open <http://localhost:4321>.

## Deploy

Drag the folder into any static host — GitHub Pages, Cloudflare Pages, Vercel, Netlify. Nothing to configure.

## To do before going public

- [ ] Final domain
- [ ] Replace the `mailto:` with a Cal.com / SavvyCal embed when a booking tool is chosen
- [ ] Fill the registry code + registered address in the footer imprint
- [ ] Estonian translation (Phase 2)
