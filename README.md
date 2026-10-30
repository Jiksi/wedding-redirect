# wedding-redirect

A lightweight single-invitation redirect page with WhatsApp/Open Graph preview metadata. Built with plain HTML, CSS, and JavaScript for Cloudflare Pages.

## Current destination

`https://youtu.be/Qgkq2iOzYzI?si=omC1Ngw7Ao9pmzgG`

## Project structure

```
wedding-redirect/
├── index.html
├── assets/
│   └── preview.svg
├── _headers
├── README.md
└── LICENSE
```

## Configure for another invitation

Edit `index.html`:
1. Update `og:title`, `og:description`, and the Twitter title/description.
2. Replace `assets/preview.svg` with your invitation artwork (prefer a 1200×630 PNG or JPG for broad social-preview compatibility).
3. Update the absolute image URLs in `og:image` and `twitter:image` after choosing your Pages hostname or custom domain.
4. Update `og:url` to the public URL of this page.
5. Change `DESTINATION_URL` and the fallback link's `href`.

## Deploy to Cloudflare Pages

1. Push this repository to GitHub (production branch: `main`).
2. In Cloudflare Dashboard, open **Workers & Pages** → **Create application** → **Pages** → **Connect to Git**.
3. Select `Jiksi/wedding-redirect`.
4. Configure:
   - Production branch: `main`
   - Framework preset: `None`
   - Build command: leave blank (or `exit 0`)
   - Build output directory: `/` (repository root; if the dashboard rejects this, use `.`)
   - Root directory: `/` (default)
5. Deploy. The default hostname is `https://wedding-redirect.pages.dev`.
6. For a custom domain, add it in the Pages project's **Custom domains** settings, then update the Open Graph URLs in `index.html`.

## WhatsApp preview notes

WhatsApp reads Open Graph metadata from the initial HTML response. Keep the `og:*` tags in the HTML; do not create them with JavaScript. The redirect happens in the visitor's browser, allowing link-preview crawlers to read the metadata first.

SVG preview support can vary between social platforms. For the most reliable WhatsApp preview, replace `assets/preview.svg` with a 1200×630 PNG/JPG and update the metadata image URLs accordingly.

WhatsApp may cache previews. After updating metadata or the image, test with a fresh URL or wait for its cache to refresh.
