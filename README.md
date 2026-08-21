# hollovar.github.io

Public website for **Hollovar Labs**, served by GitHub Pages. It carries the studio page, a
product page and a privacy policy for each application, and the shared support page.

Live at `https://hollovar.github.io/`

Plain HTML and CSS. No build step, no dependencies, no package manager.

## Why the repository is named this way

The name is not a free choice. GitHub serves a repository named exactly
`<account>.github.io` at the **root** of that account's Pages domain. Any other name becomes
a project site, and the repository name is baked into every URL:

| Repository | Privacy policy URL |
| --- | --- |
| `hollovar.github.io` | `https://hollovar.github.io/tiltflow/privacy/` |
| `hollovar-labs` | `https://hollovar.github.io/hollovar-labs/tiltflow/privacy/` |

The first is the one filed in the Play Console. **It must stay reachable for as long as the
application is published**, so `/tiltflow/privacy/` and `/support/` are permanent addresses.
Do not rename, move or restructure them.

## One repository, every application

A single account can have only one root Pages site, but that site can serve any number of
pages. Each application gets a folder, so the structure grows without new repositories and
without any published URL ever changing:

```text
/                      Hollovar Labs home (studio)
/privacy/              studio-wide privacy page, indexing every application policy
/support/              shared support and contact page
/tiltflow/             TiltFlow product page
/tiltflow/privacy/     TiltFlow privacy policy
/404.html              not-found page, with the index of pages
/<next-app>/           …and so on

/assets/style.css      the whole design system, one file
/assets/fonts/         self-hosted Archivo (SIL OFL 1.1) + licence
/assets/screens/       optimised TiltFlow screenshots (WebP)
/assets/icon-*.png     favicons and app icons
/assets/og.png         1200×630 social preview image
/play-assets/          Play Console assets, not used by the site
/sitemap.xml /robots.txt
```

A folder with an `index.html` is served at a clean directory URL, so
`/tiltflow/privacy/index.html` is reachable as `/tiltflow/privacy/`.

`.nojekyll` is present so GitHub Pages serves the files as they are, with no build step.

## No third-party resources

The site loads no web fonts, scripts, analytics or anything else from another company's
server. A site whose main purpose is to state a privacy position should not itself leak
visitors to a third party.

Keep it that way: style with `assets/style.css`, and if something seems to need an external
resource, copy it into `assets/` instead. That is why Archivo is served from `assets/fonts/`
rather than from Google Fonts.

The home page states this as a checkable claim — "0 third-party requests loaded by this
website" — so it has to stay true. Anyone can verify it in a browser's network panel in about
ten seconds, which is the point.

## Keeping the site truthful

Two things on the site are copied from elsewhere and go stale silently:

- **The tilt figures.** Start 12.0°, stop 10.0°, full speed 20.0°, low-pass 0.15 are the real
  defaults from the application's `TiltScrollSettings.cs`. They appear on `/tiltflow/` in the
  notes block, the settings schedule and the "How it works" text, and as the `START` / `STOP`
  / `FULL` constants in that page's script. If the application's defaults change, change them
  in all four places.
- **The privacy policy's *Last updated* date.** Update it whenever the policy text changes,
  and only then. The date is the only signal a reader has that they are looking at the
  current version.

## Local preview

No build step, so any static server works. From the repository root:

```sh
python -m http.server 8099
# or: npx serve .
```

Then open `http://127.0.0.1:8099/`. Opening `index.html` directly from the filesystem will
**not** work, because every path is absolute (`/assets/…`) so that pages nested at
`/tiltflow/privacy/` resolve the same as pages at the root.

## Contact address

`hollovarlabs@gmail.com` — the Hollovar Labs developer address, the same one shown publicly
on the Google Play listing. It appears in `support/index.html` and in the TiltFlow privacy
policy. Change it in both places if it ever moves.

## Play Console assets

`play-assets/header-4096x2304.jpg` is the developer-page header image, generated from the
same drawing as the site so the two match. The developer icon is `assets/icon-512.png`. Play
requires the icon at exactly 512×512 and the header at exactly 4096×2304, both
non-transparent and under 1 MB; the committed files meet that.

Neither is used by the website. They exist only for upload to the Play Console.

## Deployment

Repository → Settings → Pages → Source: *Deploy from a branch*, branch `main`, folder
`/ (root)`. After a push, confirm these all load:

- `https://hollovar.github.io/`
- `https://hollovar.github.io/tiltflow/`
- `https://hollovar.github.io/privacy/`
- `https://hollovar.github.io/tiltflow/privacy/`
- `https://hollovar.github.io/support/`

## Moving to a custom domain later

Add a file named `CNAME` at the repository root containing one line — for example
`hollovar.com` — and point the domain's DNS at GitHub Pages. Every path stays the same, so
the URL already filed with Google Play keeps working. Do not change the folder structure to
achieve this.
