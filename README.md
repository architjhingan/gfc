# Green Flag Club — website

One-page site. No framework, no build step — each `.html` file is self-contained.

```
index.html    the "coming soon" holding page — this is what visitors see
home.html     the full one-page site, ready for launch day
favicon.svg   the leaf mark for the browser tab
images/       your matcha photos go here
docs/         everything you need to know
```

**Preview them:** double-click `index.html` (holding page) or `home.html` (full site).

## Going live properly

Right now `gfc.ie` shows the holding page. When you're ready to launch:

```
mv index.html coming-soon.html   # keep it, in case you want it back
mv home.html index.html          # the full site becomes the front door
```

Both pages share the same brand tokens, fonts and leaf mark, so they look like
one thing. The holding page has an email capture that uses the same
Formspree-or-mailto setup as the contact form on the full site — set
`FORM_ENDPOINT` in both files when you get your endpoint.

## Docs

| Document | What's in it |
|---|---|
| **[docs/GUIDE.md](docs/GUIDE.md)** | Running and editing the site — photos, flavours, copy, the brand, troubleshooting |
| **[docs/HOSTING-PLAN.md](docs/HOSTING-PLAN.md)** | Step-by-step runbook: publishing, buying `gfc.ie`, wiring the contact form, `info@gfc.ie` |
| **[docs/OPTIONS-AND-COSTS.md](docs/OPTIONS-AND-COSTS.md)** | Every option at each step with prices, and total cost scenarios |

## Quick reference

| I want to… | Where |
|---|---|
| Add my photos | GUIDE 5 |
| Launch the full site | see "Going live properly" above |
| Change flavours, prices, text | GUIDE 6 |
| Fix something that's broken | GUIDE 13 |
| Get the site online today | HOSTING-PLAN phase 1 |
| Make the form actually email me | HOSTING-PLAN phase 2 |
| Buy and connect `gfc.ie` | HOSTING-PLAN phases 3–4 |
| Set up `info@gfc.ie` | HOSTING-PLAN phase 5 |
| Compare hosts / see what it all costs | OPTIONS-AND-COSTS |

## Cost at a glance

About **€6 in year one** and **~€31/year** after — the `.ie` domain is the only
thing you pay for. Hosting, the contact form and `info@gfc.ie` are all free at
this size. Breakdown in [docs/OPTIONS-AND-COSTS.md](docs/OPTIONS-AND-COSTS.md).
