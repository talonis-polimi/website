# website

Public landing site for Talonis, served as a static site via GitHub Pages at
[talonis.org](https://talonis.org).

## Structure

| Path | Purpose |
| --- | --- |
| `index.html` | The entire landing page (single file) |
| `CNAME` | Tells GitHub Pages the custom domain is `talonis.org` |
| `robots.txt` | Crawler permissions |
| `.well-known/security.txt` | RFC 9116 vulnerability disclosure policy |
| `assets/` | Reserved for `logo.svg` and `og-image.png` (not yet added) |

## Editing

- All page content lives in `index.html`. Edit the HTML directly and commit to `main`.
- Styling uses [Tailwind CSS](https://tailwindcss.com/) loaded from the browser CDN
  (`@tailwindcss/browser@4`), so utility classes work with no build step.
- Keep the page to a single `index.html` file until there is a reason to split it.

## Deployment

There is no build pipeline. GitHub Pages serves the repository root directly:

1. Commit and push to `main`.
2. In the repository settings, set **Pages → Source** to *Deploy from a branch*,
   branch `main`, folder `/ (root)`.
3. `CNAME` keeps the site bound to `talonis.org`; configure the DNS records with
   the domain registrar to point at GitHub Pages.

No `package.json`, Node.js, or GitHub Actions are required. If the site grows,
Tailwind can later be migrated to a compiled CSS build without changing the markup.
