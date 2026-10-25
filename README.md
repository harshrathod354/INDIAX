# INDIAX website

Static website for INDIAX (indiax.co.in): industrial market intelligence and global expansion consulting for Indian manufacturers.

There is no build step and no framework. Every page is a plain HTML file with its CSS and JavaScript inside it.

## Files

```
index.html                  Home page
services.html               Services (five capabilities)
process.html                The five-step method
global.html                 Global markets and region guide
case-studies.html           Case study list with filters
case-study-uae.html         UAE case study
case-study-water.html       Water treatment case study
blog.html                   Insights index
blog-*.html                 Six articles
privacy-policy.html         Privacy Policy
accessibility-statement.html Accessibility Statement
404.html                    "Page not found" page
sitemap.xml                 List of pages for search engines
robots.txt                  Crawl rules, points to the sitemap
_headers                    Security and cache headers (Cloudflare Pages)
images/                     Logos, share image and client logos
```

## Preview locally

Open `index.html` in a browser, or run this in the project folder and visit http://localhost:8000:

```
python3 -m http.server 8000
```

## Deploy

Upload everything in this folder to the top level of the site, keeping the `images` folder next to the HTML files.

**Cloudflare Pages**
1. Create a project and connect this repository (or upload the folder).
2. Framework preset: none. Build command: leave empty. Output directory: `/`.
3. Add `indiax.co.in` as a custom domain and turn on HTTPS.
4. Redirect `www.indiax.co.in` to `indiax.co.in` (a single redirect rule). The canonical tags use the address without `www`.
5. `_headers` applies automatically.

**GitHub Pages**
1. Settings, Pages: publish from the main branch, root folder.
2. Add the custom domain `indiax.co.in` and enable "Enforce HTTPS".
3. GitHub Pages ignores `_headers`, so the security and cache headers will not apply.

Check Cloudflare's and GitHub's current documentation for exact menu names, since they change.

## After deploying

1. Open `/sitemap.xml`, `/robots.txt` and `/404` to confirm they load.
2. Add the site to Google Search Console as a domain, submit `https://indiax.co.in/sitemap.xml`, then request indexing for the home page.
3. Add the site to Bing Webmaster Tools.
4. Test one page in Google's Rich Results Test, and share a link on LinkedIn to check the preview image.
5. Run PageSpeed Insights on the home page.

## What is already set up for SEO

- A unique title, description and canonical tag on every page.
- Open Graph and Twitter tags, using `images/og-image.png` (1200x630).
- Structured data: business details on the home page, breadcrumbs on inner pages, blog post data on the articles.
- `robots.txt`, `sitemap.xml` and a `404.html` set to "noindex".

Web addresses end in `.html` (for example `/services.html`). Canonical tags, the sitemap and menu links all use this style. If your host serves clean addresses instead, change all three together.

## Adding or changing a page

1. Copy an existing page of the same kind and edit the content.
2. Set its `<title>`, meta description, canonical tag, Open Graph tags and structured data in the `<head>`.
3. Add it to `sitemap.xml` and link to it from the menu or footer if needed.
4. The header, footer and styles are repeated in each file. If you change the menu or footer, change it in every page.

## Contact form

The forms open the visitor's email app with the details filled in (a `mailto:` link built by the script at the bottom of each page). To connect a third-party form tool:
1. Search the pages for `mailto:hello@indiax.co.in?subject=` in the form script.
2. Replace that part with a request to your form provider.
3. Update the Privacy Policy so it names the provider.
4. If you add a Content-Security-Policy later, allow the provider's domain.

The blog page also has a newsletter box that needs connecting to your email tool.

## To confirm before launch

- Case study results (3x leads, 15-20% conversion, +15% order intake, 30% pipeline growth): confirm the periods and that you may publish them, and that each client has approved being featured.
- Trade agreement dates on `global.html` ("as of 15 Oct 2026"): check against official sources.
- Privacy Policy: have it reviewed by a lawyer, and update it if you add analytics.
- Client logos on the home page: confirm permission for each.
- Article author name ("By IndiaX Team") and the spelling of the brand name.
- Optional: add `images/hero.jpg` to put a photo behind the home page banner. Without it the page shows a navy background.

## Contact

hello@indiax.co.in | +91 99746 17783
B-1011, Ganesh Glory, Jagatpur, Ahmedabad, Gujarat 382470, India
