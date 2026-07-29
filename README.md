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
/                      Hollovar Labs home
/support/              shared support and contact page
/assets/style.css      shared styles
/tiltflow/             TiltFlow product page
/tiltflow/privacy/     TiltFlow privacy policy
/<next-app>/           …and so on
```

A folder with an `index.html` is served at a clean directory URL, so
`/tiltflow/privacy/index.html` is reachable as `/tiltflow/privacy/`.

## No third-party resources

The site loads no web fonts, scripts, analytics or anything else from another company's
server. A site whose main purpose is to state a privacy position should not itself leak
visitors to a third party. Keep it that way: style with `assets/style.css`, and if something
seems to need an external resource, copy it into `assets/` instead.

`.nojekyll` is present so GitHub Pages serves the files as they are, with no build step.

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

## Moving to a custom domain later

Add a file named `CNAME` at the repository root containing one line — for example
`hollovar.com` — and point the domain's DNS at GitHub Pages. Every path stays the same, so
the URL already filed with Google Play keeps working. Do not change the folder structure to
achieve this.
