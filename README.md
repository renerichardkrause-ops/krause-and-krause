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

Static HTML, no build step. **Estonian is the main language** (root), English lives under `/en/`. The two language trees are kept in sync by hand — CSS must stay identical (only the `GARANTII`/`GUARANTEE` badge label differs on offers).

- `index.html`, `offers.html` — Estonian (main)
- `en/index.html`, `en/offers.html` — English
- Pages are cross-linked with `hreflang` pairs + an EN/ET toggle in the nav
- Google Fonts: Instrument Serif + IBM Plex Sans + IBM Plex Mono
- No JS framework, no bundler, no dependencies

**Pricing note:** the offers page is deliberately price-free (tailored-offer-only) to maximise inbound leads while gauging the market. The fully priced version is preserved at tag `backup-priced-offers-2026-07-06` / branch `backup/priced-offers`.

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

## To do

- [x] Registry code in the footer (17506985)
- [x] Cal.com popup booking
- [x] Estonian translation, ET as main language
- [x] Domain live: krausemanagement.ee (GitHub Pages custom domain, HTTPS enforced; www + github.io redirect)
- [x] Professional email live: richard@krausemanagement.ee (Google Workspace; MX + DKIM + SPF + DMARC p=none all set at Zone.ee); all mailto: links swapped
- [ ] DMARC upgrade path: add `rua=mailto:richard@krausemanagement.ee`, after a few clean weeks move p=none → p=quarantine
- [ ] Analytics (Plausible/GoatCounter) — needed to gauge the market
- [ ] og:image + favicon
- [ ] Imprint page (footer link is currently dead) or drop the link
- [x] Reconcile capacity claims — unified: max 3 concurrent engagements, at most 2 Sprints
- [x] Scarcity lines rewritten as policy statements (no fake "slots open" claims)
- [ ] Contract clause: founding-client month-1 refund must void playbook usage rights (Sprint is folded into the refundable month 1 — otherwise the playbook can be extracted for free)
