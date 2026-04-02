# Beach Explorer

Discover the best beaches across Southeast Asia.

## GitHub Pages

The site is published at: https://himmelfisk.github.io/beaches/

## Site Structure

```
/                          → Hub homepage (all destinations)
/leyte-philippines/        → Beaches of Leyte Province, Philippines
/robots.txt                → Search engine crawling rules
/sitemap.xml               → XML sitemap for search engines
```

## SEO Features

- **Meta tags**: Description, keywords, robots directives, canonical URLs
- **Open Graph + Twitter Cards**: Rich previews when shared on social media
- **JSON-LD Structured Data**: `WebSite`, `TouristDestination`, `Beach`, `FAQPage`, `BreadcrumbList` schemas
- **FAQ section**: 7 frequently asked questions with matching `FAQPage` schema for Google rich snippets
- **Sitemap & robots.txt**: For search engine discovery
- **Image preloading**: Hero image preloaded for better Core Web Vitals
- **Breadcrumb navigation**: Links back to hub from location pages

## Adding a New Destination

1. Create a new directory (e.g. `palawan-philippines/`)
2. Add an `index.html` with SEO meta tags, structured data, and breadcrumb
3. Add a destination card to the hub `index.html`
4. Add the new URL to `sitemap.xml`

## Custom Domain Setup

All SEO-critical URLs (canonical, Open Graph, sitemap, robots.txt, JSON-LD) currently point to the default GitHub Pages URL:

```
https://himmelfisk.github.io/beaches/
```

When you configure a custom domain (e.g. `https://www.beachexplorer.com/`), you need to update these references. Here's how:

### 1. Configure GitHub Pages to use your domain

1. Go to **Settings → Pages** in this repository.
2. Under **Custom domain**, enter your domain (e.g. `www.beachexplorer.com`).
3. Click **Save**. GitHub will create a `CNAME` file in the repo root automatically.
4. Enable **Enforce HTTPS** once the certificate is provisioned.

### 2. Set up DNS records with your registrar

| Type  | Name              | Value                            |
|-------|-------------------|----------------------------------|
| CNAME | `www`             | `himmelfisk.github.io`           |
| A     | `@` (apex domain) | `185.199.108.153`                |
| A     | `@`               | `185.199.109.153`                |
| A     | `@`               | `185.199.110.153`                |
| A     | `@`               | `185.199.111.153`                |

> If you only use a `www` subdomain, the CNAME record alone is sufficient.

### 3. Replace all URLs in the codebase

Run this from the repository root to replace every occurrence in one step:

```bash
# Replace with your actual domain (no trailing slash)
NEW_DOMAIN="https://www.beachexplorer.com"

find . -type f \( -name "*.html" -o -name "*.xml" -o -name "*.txt" \) \
  -not -path './.git/*' \
  -exec sed -i "s|https://himmelfisk.github.io/beaches|${NEW_DOMAIN}|g" {} +
```

**Files that contain URLs to update:**

| File | What to update |
|------|---------------|
| `index.html` | `<link rel="canonical">`, `og:url`, JSON-LD `WebSite.url`, `CollectionPage.url`, `ItemList` URLs |
| `leyte-philippines/index.html` | `<link rel="canonical">`, `og:url`, JSON-LD `WebSite.url`, `TouristDestination.url`, `BreadcrumbList` URLs |
| `sitemap.xml` | All `<loc>` entries |
| `robots.txt` | `Sitemap:` directive |

### 4. Verify

After pushing the changes:

- Visit your custom domain and confirm pages load with HTTPS
- Check `<meta>` tags using [Facebook Sharing Debugger](https://developers.facebook.com/tools/debug/) or [Twitter Card Validator](https://cards-dev.twitter.com/validator)
- Validate structured data with [Google Rich Results Test](https://search.google.com/test/rich-results)
- Submit your sitemap at `https://www.yourdomain.com/sitemap.xml` in [Google Search Console](https://search.google.com/search-console/)

---

## TODO

- [ ] Set up custom domain (see instructions above)
- [ ] Register with Google Search Console
- [ ] Register with Bing Webmaster Tools
- [ ] Add more destination pages (Palawan, Bali, Siargao, etc.)

