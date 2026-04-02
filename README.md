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

## TODO

- [ ] Update all URLs to custom domain when available (search for `himmelfisk.github.io/beaches`)
- [ ] Register with Google Search Console
- [ ] Register with Bing Webmaster Tools
- [ ] Add more destination pages (Palawan, Bali, Siargao, etc.)

