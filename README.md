# Madhuri Homes

The public single-page website for Madhuri Homes — a real-estate
practice affiliated with Keller Williams.

Static HTML/CSS/JS. No build step. No framework. Drop into any
static host. Hosts free on Cloudflare Pages or GitHub Pages.

## Preview locally

```bash
cd ~/work/workspace/madhurihomes
python3 -m http.server 4000
# open http://127.0.0.1:4000
```

Or any other static server. There is nothing to install.

## Edit content

All placeholder content lives in `index.html` and is wrapped in
SQUARE BRACKETS so it's easy to find:

| Placeholder | Where | Replace with |
| --- | --- | --- |
| `[MARKET]` | hero, about, OG meta | Her city/metro (e.g. *Austin, TX*) |
| `[YEARS]` | about stats | Years in real estate (e.g. *5*) |
| `[EMAIL]` | contact, privacy | Her business email |
| `[PHONE]` | contact, privacy | Her phone (`tel:` link compatible) |
| `[HANDLE]` | contact | Instagram handle (without `@`) |

Find/replace across the file. Total time: ~3 minutes.

### Swap in her portrait

Drop a 4:5 portrait at `assets/portrait.jpg` (recommended size:
800 × 1000). The page already references it. If the file is missing,
the page automatically shows a serif monogram "M" fallback — no
broken image icon.

### Swap the hero photo

The hero pulls from Unsplash by default. To use her own photography:

1. Drop the image at `assets/hero.jpg`
2. In `style.css`, find `.hero__image` and replace the Unsplash URL
   with `/assets/hero.jpg`

Same for the approach section (`.approach__image`).

## Deploy to Cloudflare Pages (recommended, ~5 minutes)

1. Push this folder to a GitHub repo (separate from IntentLayer).
2. Go to https://dash.cloudflare.com → Workers & Pages → **Create →
   Pages → Connect to Git**.
3. Pick the repo. Build settings:
   - Build command: *(leave empty)*
   - Build output directory: `/`
4. Click **Save and Deploy**. Live in ~60s at
   `https://<project>.pages.dev`.
5. To attach `madhurihomes.com`:
   - In the same Cloudflare Pages project → Custom domains →
     Add → `madhurihomes.com`
   - Cloudflare auto-creates the DNS records and provisions SSL.
   - **The domain must already be on Cloudflare DNS** for this to
     be one-click — which it is, since we registered it with
     Cloudflare Registrar.

## Deploy to GitHub Pages (alternative, ~3 minutes)

1. Push to a GitHub repo.
2. Repo settings → Pages → Source: `main` branch / root.
3. Live at `https://<user>.github.io/<repo>/`.
4. Custom domain: settings → Pages → Custom domain → enter
   `madhurihomes.com`. Add the GitHub-provided CNAME / A records to
   Cloudflare DNS.

## Design notes

- **Type:** Fraunces (serif) for headlines, Inter (sans) for body.
  Both loaded from Google Fonts. No self-hosting.
- **Palette:** warm bone whites, deep ink, sage accent. Tested for
  WCAG AA contrast.
- **Motion:** ken-burns on hero (22s loop), fade-in-on-scroll for
  every section. Respects `prefers-reduced-motion`.
- **Mobile-first.** Single-column up to 800px; multi-column above.
- **No tracking, no analytics.** Add Plausible or Cloudflare Web
  Analytics later if needed — both are privacy-respecting.

## Privacy policy URL

The privacy section uses `#privacy` as its anchor. After deploy, the
canonical URL is:

```
https://madhurihomes.com/#privacy
```

Use this URL in the Meta Lead Ad form's Privacy Policy field. Meta
accepts anchor URLs.

## Brokerage compliance

The footer carries the standard Keller Williams attribution line:

> Each Keller Williams office is independently owned and operated.

Adjust if she's affiliated with a specific KW market center that
requires more language (e.g., *Keller Williams Realty — Frisco*).
