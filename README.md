# INDIAX website (editable source)

This is the source for indiax.co.in. The menu and footer are stored once and added to every page by a small build script, so a change to them takes one edit instead of 17.

## Folders

```
src/partials/header.html    The menu (shared by every page)
src/partials/footer.html    The footer and the phone call bar (shared by every page)
src/pages/*.html            One file per page. {{header}} and {{footer}} mark where the shared parts go
public/                     Files copied as they are: images/, robots.txt, sitemap.xml, _headers
build.js                    The build script (needs only Node.js)
dist/                       The finished site, created by the build. Do not edit it
```

## Which file to edit

| I want to change | Edit this file |
|---|---|
| Menu links or the menu button | `src/partials/header.html` |
| Footer text, links, logo or the phone bar | `src/partials/footer.html` |
| The wording of one page | `src/pages/<that page>.html` |
| A page title, description or search tags | the `<head>` of `src/pages/<that page>.html` |
| Images, sitemap, robots.txt, security headers | `public/` |

After editing, rebuild (see below). Never edit files inside `dist/`, because the next build overwrites them.

Two markers inside the partials are filled in by the build:
- `{{cur:services}}` and similar highlight the current page in the menu.
- `{{contact}}` becomes `#contact` on pages that have their own contact form, and `/#contact` (the home page form) on the others.

## Build

Install Node.js (version 18 or newer) once, then in this folder run:

```
node build.js
```

The finished site appears in `dist/`. To preview it:

```
cd dist
python3 -m http.server 8000
```

Then open http://localhost:8000. (Do not double-click the files, because links to the home page use `/`.)

## Publish

**Cloudflare Pages (recommended)**
1. Put this folder in a GitHub repository.
2. In Cloudflare Pages, create a project from that repository.
3. Build command: `node build.js`. Build output directory: `dist`.
4. Add the custom domain `indiax.co.in` and turn on HTTPS. Redirect `www` to `indiax.co.in`.
5. From then on, every change you save to GitHub is built and published automatically. `_headers` is applied by Cloudflare.

**Without a build service**
Run `node build.js` and upload the contents of `dist/` to your host. GitHub Pages ignores `_headers`.

Check Cloudflare's and GitHub's current documentation for exact menu names, since they change.

## Adding a page

1. Copy a page in `src/pages/` that is similar, and rename it.
2. Keep `{{header}}` and `{{footer}}` where they are. Change the content, title, description, canonical tag and structured data.
3. If it should highlight a menu item, name it like the others (for example `blog-something.html` highlights Insights). Otherwise no change is needed in `build.js`.
4. Add it to `public/sitemap.xml`.
5. Run the build.

## SEO already set up

Each page has a unique title, description and canonical tag, Open Graph and Twitter tags (image: `public/images/og-image.png`), and structured data. Web addresses end in `.html`. If you ever switch to clean addresses, change the canonical tags, sitemap and menu links together.

## Contact form

The forms currently open the visitor's email app (a `mailto:` link built by a script at the bottom of each page). To connect a form service, replace that script on each page that has a form. The blog page also has a newsletter box to connect.

## To confirm before launch

- Case study results and the periods behind them, and each client's approval to be featured.
- Trade agreement dates on `global.html` (marked "as of 15 Oct 2026").
- Privacy Policy reviewed by a lawyer.
- Permission to show each client logo on the home page.
- Author name on the articles ("By IndiaX Team").

## Contact

hello@indiax.co.in | +91 99746 17783
B-1011, Ganesh Glory, Jagatpur, Ahmedabad, Gujarat 382470, India
