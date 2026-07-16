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

> **⚠️ DELIBERATELY DE-LISTED FROM SEARCH (2026-07-16).** The site is link-only:
> `noindex, nofollow, noarchive` on all pages, sitemap.xml + llms.txt removed,
> AI crawlers blocked in robots.txt, site-removal requests filed in Google Search
> Console and Bing Webmaster Tools. **Do not "fix" this** — it is intentional
> (Töötukassa contract constraint). Search bots must stay ALLOWED in robots.txt
> so they can see the noindex tag. To re-list later: remove the robots meta tags,
> restore sitemap.xml/llms.txt (git history has them at tag/commit before
> 96a1fd1), re-allow AI crawlers, cancel the GSC/Bing removal requests, resubmit
> the sitemap.

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
- [x] Analytics: GA4 (G-QGGPEG941B) + Google Ads (AW-18310440285, Customer ID 857-451-5615) installed with Consent Mode v2; cookie banner ET/EN, `generate_lead` on Cal.com booking, `contact_click` on mailto — see "Analytics & consent" below
- [ ] GA4 admin: mark `generate_lead` as a key event (Admin → Events), then import it into Google Ads as a conversion action (can't be done from code)
- [ ] Google Ads: account is a shell only — do not launch a campaign until there's a client/testimonial + a few weeks of GA4 baseline data
- [x] Favicon (KM monogram, 32/180/512) + og:image 1200×630
- [x] SEO/AI layer: JSON-LD structured data on all 4 pages, rel=canonical, twitter cards — **reversed 2026-07-16**: sitemap.xml + llms.txt removed, AI crawlers blocked, noindex everywhere (see de-listing note above)
- [x] Google Search Console live (2026-07-16): Domain property `krausemanagement.ee` under richard@krausemanagement.ee, auto-verified via Workspace DNS. Later same day: **site-wide removal request filed** (Removals → prefix https://krausemanagement.ee/, ~6 months, renewable/cancellable), sitemap deleted from GSC
- [x] Bing Webmaster Tools live (2026-07-10): site verified via BingSiteAuth.xml + msvalidate meta (keep both — removing them un-verifies). Account: Google SSO as richard@krausemanagement.ee. 2026-07-16: sitemap deleted, **whole-site directory block (URL & cache) active for 90 days** — renew if noindex hasn't fully propagated by expiry
- [ ] Google Business Profile: "Krause Management OÜ" is verified and richard@ has manager access, but primary ownership is still on the personal gmail account — transfer Primary owner to richard@ (user action, from the personal account)
- [ ] Imprint page (footer link is currently dead) or drop the link
- [x] Reconcile capacity claims — unified: max 3 concurrent engagements, at most 2 Sprints
- [x] Scarcity lines rewritten as policy statements (no fake "slots open" claims)
- [ ] Contract clause: founding-client month-1 refund must void playbook usage rights (Sprint is folded into the refundable month 1 — otherwise the playbook can be extracted for free)

## ROI calculator

Both offers pages carry a value calculator (anchors: `#kalkulaator` ET / `#calculator` EN, between the hero and the Sprint section): four sliders (opportunities/month, deal size via a 300 EUR - 300k value ladder, current + target close rate) computing added annual revenue, client-side only. Value-only by design — no fee appears, consistent with the price-free stance. CSS/JS byte-identical between languages; copy entries K1-K6 in `../eesti-copy-polish.md`. GA events: `calculator_used` on first interaction; bookings from it are tagged `roi-calculator` in Cal.com metadata.

## Analytics & consent

GA4 and Google Ads tags load on all 4 pages via `gtag.js`, with **Google Consent Mode v2**: everything defaults to `denied` and only flips to `granted` if the visitor clicks "Nõustun"/"Accept" on the cookie banner (bottom of page, reopenable via the footer "Küpsiste seaded"/"Cookie settings" link). Choice persists in `localStorage` (`km_consent`). This is a legal requirement for EEA traffic — don't remove the consent-default block or reorder it after the `gtag.js` script tag.

Two custom events beyond GA4's automatic ones:
- `generate_lead` — fires when a Cal.com popup booking completes (`bookingSuccessful`). This is the real conversion signal; stronger than the pre-existing page-view goal.
- `contact_click` — fires on any `mailto:` link click.

IDs: GA4 `G-QGGPEG941B` · Ads `AW-18310440285` · Ads Customer ID `857-451-5615`. Set up via Claude Cowork (browser agent) per `../cowork-brief-analytics-ads.md`; tags installed and verified in-browser (DebugView not yet checked live).
