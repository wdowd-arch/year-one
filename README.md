# Year one: the Marblehead Independent impact report

A web edition of the 19-page printed report, page for page and word for word, built the
same way as `the-60th`: hand-written HTML and CSS, photographs in the repo, hosted on
GitHub Pages under a subdomain.

```
index.html          the whole page — structure, styles and copy
photos/             57 files: every photograph, headshot and sponsor logo from the
                    report, the linocut with transparency, two regenerated QR codes
                    and the 1,200 x 630 share card
```

No build step, no dependencies. Open `index.html` locally and it works.

## Deploy

1. Create the repo and push these two items.
2. Settings → Pages → Build and deployment → Deploy from a branch → `main` / root.
3. Settings → Pages → Custom domain → `yearone.marbleheadindependent.com`.
   GitHub writes a `CNAME` file into the repo when you save it.
4. At your DNS host, add a CNAME record: `yearone` → `<user>.github.io`.
5. Wait for the certificate, then tick Enforce HTTPS.

That gets the page live at `yearone.marbleheadindependent.com`.

## Serving it at marbleheadindependent.com/year-one/

Same question as `the-60th`, which serves its page from Ghost while its photos and
video load from `60th.marbleheadindependent.com`. Two ways:

- **Ghost page with a custom template.** Add `page-year-one.hbs` to the theme, paste
  the markup from `index.html` into it, and point the `<img src>` values at
  `https://yearone.marbleheadindependent.com/photos/…`. Create a Ghost page with the
  slug `year-one` and Ghost picks up the template automatically. Set the feature
  image and the Facebook and X images in the page's settings sidebar.
- **Cloudflare rule.** Proxy `/year-one/*` to the Pages origin. Nothing in Ghost.

Either way the photographs stay here, in git, versioned.

## Things to change before it goes out

- The photographs came out of the print PDF and are about 1,000 px wide. If the
  originals from Ring, Muller and Rood are to hand, drop them into `photos/` under the
  same filenames; nothing else needs to change.
- The `og:image` and `canonical` URLs in `<head>` assume the two addresses above.
