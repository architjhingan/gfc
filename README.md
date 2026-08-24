# Green Flag Club website

No framework, no build step. Plain HTML files sharing one stylesheet.

```
public/               ← ONLY this folder is published to gfc.ie
  index.html          the "coming soon" holding page, what visitors see today
  favicon.svg         the leaf mark for the browser tab
  images/             product photography (see brand/photography/README.txt)

site/                 the full site, finished but parked until launch day
  index.html          home. Hero photo, the story in brief, the four drinks
  menu.html           The GFC Menu. The four drinks
  story.html          Our Story
  find.html           Find Us. Where we pop up, Instagram
  work.html           Work With Us. Enquiry form
  assets/site.css     every page's styling lives here, once
  images, favicon.svg symlinks so the pages preview correctly in place

brand/                logo artwork, the design mockup, social graphics
  photography/        full-resolution product originals, named to match
                      the files in public/images/, plus README.txt describing
                      what each served image is and how to regenerate it
docs/                 hosting, editing and cost notes
wrangler.toml         tells Cloudflare to serve public/ as a static site
```

Anything outside `public/` stays private. It's in the repo but never reachable
on the web, so the unlaunched site isn't public before you're ready.

**Preview:** double-click `site/index.html` for the full site, or
`public/index.html` for the holding page that's live now.

## Editing

Copy lives directly in the HTML. Styling lives in `site/assets/site.css` and is
shared by all five pages, so a colour or type change happens once.

The header and footer are repeated in each of the five pages. That's the price
of having no build step: changing a nav link means changing it in five files.
Search for the link text and you'll find them all.

## Going live

```
git rm site/images site/favicon.svg      # preview-only symlinks
git mv public/index.html coming-soon.html
git mv site/assets public/assets
git mv site/index.html site/menu.html site/story.html site/find.html site/work.html public/
```

Then commit and push. Cloudflare rebuilds and `gfc.ie` serves the full site.

**Before you do:** the enquiry form on `site/work.html` needs an access key
before it can send anything. See "The enquiry form" below.

## The enquiry form

`site/work.html` has a Name / Email / Contact number / Message form. The site is
a folder of static files with no server of ours behind it, so the browser posts
the enquiry straight to FormSubmit, which emails it on. No account, no API key,
no cost. The visitor stays on the page and no mail app opens.

**One thing to do, once:** send a single enquiry from the page. FormSubmit
replies to `info@gfc.ie` with an "Activate Form" link. Click it. Every enquiry
after that lands in the inbox on its own.

Until that link is clicked the form tells the sender it isn't set up yet and
offers a direct email link, rather than losing the message quietly. The reason
is also logged to the browser console.

To point the form at a different inbox, change `TO_EMAIL` at the bottom of
`site/work.html`. Activation just runs once more for the new address.

## Layout rules

Two things keep the five pages looking like one site. Both live at the top of
`site/assets/site.css`:

- **`--pad`** is the only left/right margin on the site. The header, every
  heading, every photo grid and the footer all start at that same edge. No page
  sets its own horizontal spacing.
- **`--gap-y`** is the only vertical rhythm. Every band of content is one of
  three blocks: `.section`, `.band` or `.hero`. All three use it.

Add a section by reaching for one of those three, not by writing new spacing.
A photo that should run edge to edge goes in a `.feature` figure placed outside
`.wrap`, the way the line-up shot does on Our Story.

## How deploys work

The Cloudflare Worker builds from GitHub on every push to `main`. Edit, commit,
push, and it's live in about a minute. Broken builds leave the current site up.

## Docs

| Document | What's in it |
|---|---|
| **[docs/GUIDE.md](docs/GUIDE.md)** | Editing the site: photos, copy, the brand, troubleshooting |
| **[docs/HOSTING-PLAN.md](docs/HOSTING-PLAN.md)** | Domain, email and hosting runbook |
| **[docs/OPTIONS-AND-COSTS.md](docs/OPTIONS-AND-COSTS.md)** | Options at each step with prices |

Note both `GUIDE.md` and `HOSTING-PLAN.md` still describe the old Netlify
route and the previous one-page site. They need a rewrite.

## Cost

About **€6 in year one** and **~€31/year** after. The `.ie` domain is the only
paid item. Hosting on Cloudflare and the Kit mailing list are free at this size.
