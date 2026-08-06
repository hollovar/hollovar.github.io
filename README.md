# hollovar.github.io

Public website for **Hollovar Labs**, served by GitHub Pages. It carries the company page,
a product page and a privacy policy for each application, and the shared support page.

Live at `https://hollovar.github.io/`

## Why the repository is named this way

The name is not a free choice. GitHub serves a repository named exactly
`<account>.github.io` at the **root** of that account's Pages domain. Any other name becomes
a project site, and the repository name is baked into every URL:

| Repository | Privacy policy URL |
| --- | --- |
| `hollovar.github.io` | `https://hollovar.github.io/tiltflow/privacy/` |
| `hollovar-labs` | `https://hollovar.github.io/hollovar-labs/tiltflow/privacy/` |

The first is the one that goes in the Play Console. It must stay reachable for as long as
the application is published, so it is worth getting right before the first submission.

## One repository, every application

A single account can have only one root Pages site, but that site can serve any number of
pages. Each application gets a folder, so the structure grows without new repositories and
without any published URL ever changing:

```text
/                      Hollovar Labs home (studio)
/support/              shared support and contact page
/tiltflow/             TiltFlow product page
/tiltflow/privacy/     TiltFlow privacy policy
/404.html              sheet-not-found page, with the index of pages
/<next-app>/           …and so on

/assets/style.css      the whole design system, one file
/assets/fonts/         self-hosted Archivo (SIL OFL 1.1) + licence
/assets/screens/       optimised TiltFlow screenshots (WebP, 540px wide)
/assets/icon-512.png   favicon / app icon, from Hollovar_Icon1.png
/assets/icon-180.png   apple-touch-icon
/assets/og.png         1200×630 social preview image
/play-assets/          Play Console developer-page assets, not used by the site
/sitemap.xml /robots.txt
/PRODUCT.md /DESIGN.md durable product and design records
```

A folder with an `index.html` is served at a clean directory URL, so
`/tiltflow/privacy/index.html` is reachable as `/tiltflow/privacy/`.

## No third-party resources

The site loads no web fonts, scripts, analytics or anything else from another company's
server. A site whose main purpose is to state a privacy position should not itself leak
visitors to a third party. Keep it that way: style with `assets/style.css`, and if something
seems to need an external resource, copy it into `assets/` instead. That is exactly why
Archivo is served from `assets/fonts/` rather than from Google Fonts.

The home page states this as a checkable claim ("0 third-party requests loaded by this
website"), so it has to stay true. It is verifiable in about ten seconds in a browser's
network panel, which is the point.

`.nojekyll` is present so GitHub Pages serves the files as they are, with no build step.

## The design: a measured drawing

The site is drawn rather than laid out. The visual world is a **measured survey drawing**: a
pale drafting sheet lying on a graphite drawing board, hairline rules, hatched masonry,
dimension lines in red oxide, and the icon's cyan reserved for one thing only — a live
measured value. Square corners throughout, matte, no glow, no gradients.

This came from the brief's own instruction to bring the raven and castle in as *engineering
drawing* rather than fantasy illustration. The Play icon stays the painterly crest; the
website's identity is a restrained geometric descendant of it.

Each page carries its direction contract as an HTML comment at the top of `<body>`. That is
the record of what the page is meant to be, and it is worth reading before changing a page's
composition.

Two drawings do real work:

- **`/` — the keep in elevation.** Hatched masonry, the raven inked on the parapet, the
  Hungarian etymology (*Hollóvár*, raven castle) set as a vertical dimension.
- **`/tiltflow/` — the phone in section, and it is live.** The phone pivots against a dash-dot
  datum, the tilt angle is dimensioned by an arc, and the application's real thresholds are
  struck as rays. Text inside the drawn phone actually scrolls when the angle passes 12°.
  Drag it, use the arrow keys, or — on an Android phone — tilt the phone itself.

Every number on the site is taken from `TiltFlow.Core/Models/TiltScrollSettings.cs`: start
12.0°, stop 10.0°, full speed 20.0°, low-pass coefficient 0.15. **If those defaults change in
the application, they must change here too** — on `/tiltflow/` in the notes block, the
settings schedule and the "How it works" text, and in the `START`/`STOP`/`FULL` constants in
that page's script.

`DESIGN.md` records the tokens and components in full.

### Typography

One typeface, self-hosted: **Archivo**, as a single variable file carrying both a width and a
weight axis. A drafting office letters with one alphabet and varies the *width* by annotation
rank, so width is a design token here rather than a second font. Two files (`latin`,
`latin-ext`) cover the Hungarian accented characters. SIL Open Font License 1.1;
`assets/fonts/OFL.txt` must stay alongside them.

### Screenshots

`assets/screens/` holds four TiltFlow screens as WebP at 540px wide, mounted on the sheet as
annotated specimens. The Android status bar is deliberately cropped off every one of them: it
carried a clock, battery level and notification icons, which are noise at best and personal
information at worst.

## Local preview

No build step, so any static server works. From the repository root:

```sh
python -m http.server 8099
# or: npx serve .
```

Then open `http://127.0.0.1:8099/`. Opening `index.html` directly from the filesystem will
**not** work correctly, because every path is absolute (`/assets/…`) so that pages nested at
`/tiltflow/privacy/` resolve the same as pages at the root.

## Contact address

`hollovarlabs@gmail.com` — the Hollovar Labs developer address, the same one shown publicly
on the Google Play listing. It appears in `support/index.html` and in the TiltFlow privacy
policy. Change it in both places if it ever moves.

The privacy policy carries a *Last updated* date. Update it whenever the policy text
changes, because the date is the only signal a reader has that they are looking at the
current version.

## Publishing

1. Create a GitHub **organization** named `hollovar`.
2. Create a repository in it named exactly `hollovar.github.io`, public.
3. Push this folder to the default branch.
4. Repository → Settings → Pages → Source: *Deploy from a branch*, branch `main`, folder
   `/ (root)`.
5. Wait for the first build, then confirm these all load:
   - `https://hollovar.github.io/`
   - `https://hollovar.github.io/tiltflow/`
   - `https://hollovar.github.io/tiltflow/privacy/`
   - `https://hollovar.github.io/support/`

## Before TiltFlow goes live on Google Play

The site currently states that TiltFlow is **in review** and deliberately shows no Play link,
because presenting a primary action that leads nowhere is worse than presenting none. When the
listing goes public, three things change:

1. `/tiltflow/` — replace the `In review at Google Play` stamp with a real link button to
   `https://play.google.com/store/apps/details?id=com.hollovar.tiltflow`.
2. `/tiltflow/` — the *Availability* section says the listing is not yet public. Rewrite it.
3. `/` — the studio page says `01 application, currently in review at Google Play` in its
   notes, and the applications index shows an `In review` status. Update both.

## Play Console assets

`play-assets/header-4096x2304.jpg` is the developer-page header image, generated from the same
drawing as the site so the two match. The developer icon is `assets/icon-512.png`. Play
requires the icon at exactly 512×512 and the header at exactly 4096×2304, both non-transparent
and under 1 MB; the committed files meet that.

These are **not** used by the website and exist only for upload to the Play Console.

## Moving to a custom domain later

Add a file named `CNAME` at the repository root containing one line — for example
`hollovar.com` — and point the domain's DNS at GitHub Pages. Every path stays the same, so
the URL already filed with Google Play keeps working. Do not change the folder structure to
achieve this.
