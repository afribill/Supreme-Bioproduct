# Supreme BioProducts — website

Static site for supremebioproducts.com. No build step, no framework, no dependencies —
it's a single self-contained `index.html` plus three supporting files for SEO.

## Files

- `index.html` — the entire site (all styling, scripts and images are inlined in this one file)
- `robots.txt` — tells search engines they can crawl the site, and points to the sitemap
- `sitemap.xml` — lists the site's URL for search engines
- `og-image.jpg` — the 1200×630 preview image used when the site is shared on WhatsApp, Facebook, LinkedIn, etc.

All four files must stay at the **root** of the repo (not in a subfolder), so they resolve as
`supremebioproducts.com/`, `/robots.txt`, `/sitemap.xml` and `/og-image.jpg`.

## SEO already built in

- Title, meta description, canonical tag, Open Graph and Twitter Card tags
- JSON-LD structured data (Organization: name, Jos address, email, areas of expertise)
- Exactly one `<h1>` on the page, alt text on every image
- `sitemap.xml` + `robots.txt` ready to serve from the domain root

None of this does anything until the site is actually live at `supremebioproducts.com` — see
"Deploying" below. Once it is, submit `sitemap.xml` through Google Search Console (Step 5) to
get it crawled and indexed.

## Deploying

1. Push this repo to GitHub.
2. In Vercel: **Add New Project** → import this repo.
3. Framework Preset: **Other**. No build command, no output directory — Vercel will serve
   `index.html` as-is. Deploy.
4. In the Vercel project's **Settings → Domains**, add `supremebioproducts.com` and
   `www.supremebioproducts.com`, and add the DNS records Vercel gives you at your domain
   registrar. HTTPS is issued automatically once DNS verifies.
5. Once live, add the domain to **Google Search Console** and submit `sitemap.xml` from there —
   that's what actually gets Google to start crawling it.
6. Separately, claim a **Google Business Profile** for the Jos address — this is what makes the
   business show up with a map pin, hours and reviews in local search.

## Editing later

Everything — layout, copy, images — lives inline in `index.html`. Product photos, the hero
background photos, the logo and the banner image are all embedded as base64 data, so the file
is self-contained but not small (~4 MB). That's expected and fine for a single static page;
it just means editing images means re-encoding and re-embedding them, not swapping a file in
an `/images` folder.
