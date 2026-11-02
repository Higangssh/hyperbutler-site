# hyperbutler-site

The website of [hyperbutler](https://github.com/Higangssh/hyperbutler), served at
**https://hyperbutler.dev** by Cloudflare Pages.

Plain HTML and CSS in `public/`: no build step, no JavaScript, no web fonts, no analytics.
The page loads nothing from any other host.

| File | What it is |
|---|---|
| `public/index.html` | The page |
| `public/style.css` | All styles (no inline styles, so the CSP needs no `'unsafe-inline'`) |
| `public/img/` | Copies of files from the main repository's `assets/brand/` |
| `public/_headers` | Security and cache headers, applied by Cloudflare Pages (not served) |
| `public/robots.txt`, `public/sitemap.xml` | For crawlers |

Facts on the page come from the main repository's `README.md` ("Current status"),
`docs/install.md` and `docs/compare-docker-desktop.md`. When those change, update the page
by hand; never put a number here that is not measured there.

## Preview locally

```
python -m http.server 8000 --directory public
```

## Cloudflare Pages

- Production branch: `main`
- Framework preset: None
- Build command: (empty)
- Build output directory: `public`
- Custom domain: `hyperbutler.dev`

Every push to `main` redeploys the site. Only `public/` is served, so this README is not.

The canonical link, `og:url` and `og:image` at the top of `index.html` name the domain;
every other URL is relative.

## Security headers

`_headers` sets a strict Content-Security-Policy (`default-src 'none'`, images and the
stylesheet from the site itself only, no scripts), HSTS without `preload`, `nosniff`,
`frame-ancestors 'none'` and a restrictive Permissions-Policy. If you add a script, put it
in its own file and add `script-src 'self'`; do not allow inline scripts.

## License

Apache-2.0, like hyperbutler. Docker is a trademark of Docker, Inc.; hyperbutler is not
affiliated with Docker, Inc.
