# Código Descontraído — website

Static company website for Código Descontraído Unipessoal Lda, served by GitHub Pages from the
root of this repository. No build step, no dependencies.

**Live at:** https://orangelash.github.io/codigo-descontraido-pages/

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The whole site — one page, three practice bands, six service lines |
| `404.html` | Not-found page, styled from the same stylesheet |
| `styles.css` | All styling. Design tokens live in `:root` |
| `favicon.svg` | Browser tab icon |
| `icon-180.png` | Apple touch icon for a home-screen bookmark |
| `og.png` | 1200×630 preview card for shared links |
| `robots.txt` | Allows everything |
| `.nojekyll` | Serve the files as-is instead of running Jekyll |

## Enabling GitHub Pages

Repository **Settings → Pages**:

- **Source:** Deploy from a branch
- **Branch:** `main`, folder `/ (root)`

The first deploy takes a minute or two.

## Using a custom domain

Add a `CNAME` file at the root containing the bare hostname:

```
codigodescontraido.com
```

Point the domain's DNS at GitHub Pages — an `ALIAS`/`ANAME` record, or GitHub's four apex `A`
records, or a `CNAME` record for a subdomain — then set the domain under Settings → Pages and
enable **Enforce HTTPS** once the certificate is issued.

**Then update two tags in `index.html`.** `og:url` and `og:image` are absolute and currently point
at the github.io address. Crawlers cache them, and a preview pointing at the old host is worse than
none.

## Design

The site deliberately mirrors the company overview deck, so the two read as one identity: the same
palette, one colour per practice — petrol for technology, amber for training, sienna for assets —
saturated full-bleed bands, and layered circles as the repeating motif.

Icons are one inline SVG sprite at the top of `index.html`, referenced with `<use href="#i-…">`.
Nothing is fetched at runtime except the Google Fonts stylesheet.

## Two things held deliberately

**Disclosure.** The only company details anywhere on the site are the company name and the contact
email. No address, tax number, incorporation date or headcount.

**No invented proof.** No client names, logos, metrics, case studies or testimonials, because there
were none to use. Add them only where they are true and you have permission.

## Editing

Each service line is one `<article class="line">`: a heading, a summary paragraph, then `<h4>`
groups with bullet lists. Copy an existing block to add another.

Colours, spacing and fonts are tokens at the top of `styles.css`. Changing a practice colour there
restyles that whole band.

## Checking a change

The decorative circles sit in bands with `overflow: hidden`, so an element-level overflow check
will flag them and the off-screen skip link. The signal that matters is
`document.documentElement.scrollWidth` equalling the viewport width at phone width — that is what
proves the page does not scroll sideways. Verified at 360px.
