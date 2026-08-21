# Options and Costs

Every choice involved in getting this site online, what each one costs, and
which I'd pick. There are four independent decisions — hosting, the contact
form, the domain, and email at the domain. You can mix and match freely.

**Prices checked 19 August 2026.** They change. Treat these as "what to expect"
and confirm on the provider's own pricing page before you pay. Where a service
bills in US dollars I've said so — Irish VAT at 23% may be added on top for
Irish services.

**Contents**

1. [Quick answer](#1-quick-answer)
2. [Hosting the site](#2-hosting-the-site)
3. [The contact form](#3-the-contact-form)
4. [The domain](#4-the-domain)
5. [Email at your domain](#5-email-at-your-domain)
6. [The all-in-one alternative](#6-the-all-in-one-alternative)
7. [Total cost scenarios](#7-total-cost-scenarios)
8. [What changes the cost later](#8-what-changes-the-cost-later)

---

## 1. Quick answer

| Layer | Pick | Year one | Ongoing |
|---|---|---|---|
| Hosting | Cloudflare Pages | €0 | €0 |
| Contact form | Formspree free | €0 | €0 |
| Domain | `gfc.ie` at Blacknight | ~€6 inc VAT | ~€31 inc VAT |
| Email | Zoho Mail free | €0 | €0 |
| **Total** | | **~€6** | **~€31/year** |

That's the whole site, on your own domain, with `info@gfc.ie`, for about the
price of two coffees in year one and about €31/year after.
=
Two of those picks differ from what I said earlier, because checking the
current numbers changed the answer:

- **Cloudflare Pages over Netlify.** Netlify moved to a credits model in 2026 —
  the free tier is now roughly 15GB of bandwidth and about 20 deploys a month.
  For a page built around large photos, Cloudflare Pages' genuinely unlimited
  bandwidth is the safer free tier.
- **Zoho Mail over plain forwarding.** Zoho's free plan gives you a real mailbox
  that can *send* as `info@gfc.ie`. Forwarding can only receive — and Gmail's
  workaround for sending disappears in January 2027.

Netlify is still the fastest way to get something live tonight, and there's no
harm in starting there and moving later. Details below.

---

## 2. Hosting the site

All four of these are free at this size and all give you HTTPS automatically.
The differences are in how you publish and where the free tier runs out.

| Option | Cost | Free tier | How you publish |
|---|---|---|---|
| **Cloudflare Pages** | Free | **Unlimited bandwidth**, 500 builds/mo, 10GB storage | Drag-and-drop or Git |
| **Netlify** | Free | 300 credits/mo ≈ 15GB bandwidth, ≈20 deploys | Drag-and-drop or Git |
| **GitHub Pages** | Free | 100GB/mo soft limit, 1GB site | Git push only |
| **Vercel** | Free | 100GB/mo, non-commercial use only on free | Drag-and-drop or Git |

**Paid tiers, if you ever outgrow free:** Cloudflare Pages Pro $20/mo (you
won't need it), Netlify Personal $9/mo or Pro $20/mo, Vercel Pro $20/mo.

### Which to pick

**Cloudflare Pages** — best free tier for this site. Unlimited bandwidth means
a busy week or a photo-heavy gallery can never generate a surprise bill or a
throttle. You also get DNS and email routing in the same dashboard, so if you
go the Cloudflare route for email you're managing one account instead of three.

**Netlify** — the easiest possible start: <https://app.netlify.com/drop> takes a
dragged folder with no account at all. Genuinely 60 seconds. The catch is the
2026 credits model — 300 credits covers about 20 deploys *or* about 15GB of
traffic, shared. For a small site that's fine; for a gallery that gets shared
around Instagram it's a real ceiling. Accounts created before September 2025
keep the old 100GB allowance.

**GitHub Pages** — free and reliable, but publishing means Git. If you're not
already comfortable with it, this adds a whole tool to learn for no gain here.

**Vercel** — fine technically, but the free tier is licensed for
non-commercial use. A business selling matcha is commercial, so this would mean
the $20/mo Pro plan. Skip it.

> **Recommendation:** Netlify Drop tonight because it's the fastest thing that
> works, then move to Cloudflare Pages when you set up the domain. Moving is
> re-uploading the same folder — there's nothing to migrate.

---

## 3. The contact form

The site is static, so it has no server and cannot send email by itself.
Something has to receive the submission and relay it. These are the options.

| Option | Cost | Free allowance | Notes |
|---|---|---|---|
| **`mailto:` (as shipped)** | Free | Unlimited | Opens the visitor's mail app. Fails for anyone without one configured. |
| **Formspree** | Free | 50 submissions/mo | Works on any host. One line to set up. |
| **Netlify Forms** | Free | Included on all plans since Apr 2026 | Only works if you host on Netlify. |
| **Cloudflare Worker** | Free | 100k requests/day | You'd have to write it. Not worth it here. |

**Formspree paid tiers,** if 50/month isn't enough: around $10/month for 1,000
submissions, rising to $25/month for 10,000. Billed in USD. Reported entry
pricing varies between sources, so check their page if you get close to the cap.

### Which to pick

**Formspree free.** 50 enquiries a month is a lot for a new business, and it
keeps working if you change hosts — the endpoint is just a URL in your HTML.
Setup is pasting one line into `index.html`.

**Netlify Forms** is equally good *if* you stay on Netlify, and form
submissions became free on all plans in April 2026. But it ties your form to
your host: move to Cloudflare and it stops working. Given the hosting
recommendation above, that's the wrong way round.

**Leave the `mailto:` fallback in place** either way. It's already there and it
costs nothing — it just stops being the primary path.

> **Recommendation:** Formspree free. Revisit only if you pass 50 enquiries in a
> month, which would be a good problem.

---

## 4. The domain

As of 19 Aug 2026, **`gfc.ie` and `greenflagclub.ie` are both unregistered**,
while `gfc.com` (1995) and `greenflagclub.com` (2017) have been taken for
years. That makes `.ie` the obvious route — and it's the right signal for an
Irish matcha brand anyway.

| Option | Year one | Renewal | Notes |
|---|---|---|---|
| **`gfc.ie`** at Blacknight | ~€4.99 + VAT ≈ **€6** | ~€24.99 + VAT ≈ **€31** | Intro offer on first year |
| `gfc.ie` elsewhere | ~€20–30 | ~€20–30 | Hosting Ireland, Register365, Irish Domains |
| `greenflagclub.ie` | Same as above | Same as above | Fallback if `gfc.ie` is premium-priced |
| A `.com` | ~€10 | ~€10 | Both good names already taken |
| `.shop` / `.cafe` / `.coffee` | ~€25–40 | ~€25–40 | Cheap first year, steep renewals — check before buying |

**Watch for these:**

- Blacknight's €4.99 is a **first-year intro price, excluding VAT**. Renewal is
  €24.99 + VAT. Budget for the renewal, not the headline.
- A three-letter domain like `gfc.ie` may be classed **premium** and priced well
  above the standard rate. You'll only find out at checkout. If it is,
  `greenflagclub.ie` is free too and costs the normal rate.
- **`.ie` requires proof of a connection to Ireland** — passport, PPS card,
  driver's licence, proof of residence, or a CRO/VAT number for a business. A
  person reviews it, so allow up to two working days. This is not an extra cost,
  just an extra wait.
- **Turn on auto-renew.** A lapsed domain is the most common way a small
  business loses its site and its email at once.

> **Recommendation:** `gfc.ie` at Blacknight if it prices normally, otherwise
> `greenflagclub.ie`. Either way, budget ~€31/year from year two.

---

## 5. Email at your domain

This is about `info@gfc.ie`. It's independent of the contact form — the form
keeps working whatever you choose here.

The important distinction is **forwarding vs a real mailbox**:

- **Forwarding** receives mail at your domain and drops it into your Gmail.
  Replies go out from your Gmail address, not from `info@gfc.ie`.
- **A mailbox** actually holds the mail and can send *as* `info@gfc.ie`.

Gmail's "Send mail as" used to bridge that gap, but **Google is removing it for
non-Google addresses in January 2027.** So forwarding is a receive-only
solution from that point on.

| Option | Cost | Send as info@? | Notes |
|---|---|---|---|
| **Registrar forwarding** | Usually free with domain | No | Simplest. Two fields in the control panel. |
| **Cloudflare Email Routing** | Free | No | Free forever, but needs your DNS on Cloudflare. |
| **Zoho Mail free** | **Free**, up to 5 users | **Yes** | Real mailbox. Region-restricted; no IMAP/POP on free. |
| **Zoho Mail Lite** | ~$12/user/year (~€1/mo) | Yes | Adds IMAP/POP so it works in Apple Mail etc. |
| **Google Workspace Starter** | ~$6–7/user/month (~€70–80/yr) | Yes | Gmail interface you already know, plus Drive/Docs/Meet. |
| **Microsoft 365 Business Basic** | ~€6/user/month | Yes | Only worth it if you're already in Office. |

### Which to pick

**Zoho Mail's free plan** is the standout here: a genuine mailbox on your own
domain, up to 5 users, at no cost, and it can send as `info@gfc.ie` — so it
doesn't walk into the January 2027 problem. Two honest caveats: the free plan
is region-restricted (confirm it's available to you at signup), and it has no
IMAP/POP, meaning you use Zoho's webmail and mobile app rather than Apple Mail.
If that annoys you, Lite is about €1/month and removes the restriction.

**Forwarding** — registrar or Cloudflare — is the least effort and completely
fine *if you only need to receive*. Enquiries land in the Gmail you already
check, and you reply from Gmail. Many small businesses run this way happily.
Just go in knowing replies won't come from the domain address.

**Google Workspace** is the most expensive option by an order of magnitude
(~€70–80/year vs €0) and you'd mostly be paying for Drive, Docs and Meet you
already have free. Only worth it if you want the Gmail interface specifically
for the domain mailbox.

> **Recommendation:** Zoho Mail free — a real `info@gfc.ie` mailbox at no cost,
> with no 2027 cliff. Fall back to registrar forwarding if Zoho's free plan
> isn't offered in your region.

---

## 6. The all-in-one alternative

Worth knowing what you're *not* paying for. If you'd rather not touch files at
all, Squarespace or Wix bundle hosting, domain, forms and email into one
subscription with a visual editor.

| Option | Cost | What you get | What you give up |
|---|---|---|---|
| **This site** | ~€31/yr | Full control, no lock-in, no monthly fee | You edit an HTML file |
| **Squarespace** | ~€16–25/mo (~€200–300/yr) | Drag-and-drop editor, domain year one included | ~10× the cost; content locked to their platform |
| **Wix** | ~€10–20/mo (~€120–240/yr) | Same idea, cheaper tiers carry ads | Same lock-in |

The gap is roughly **€31/year versus €200–300/year** for the same one-page
result. The trade is that you edit text in a file rather than in a browser. For
a single page you update occasionally, that's a good trade. If you expect to
restructure the site weekly and never want to see code, the subscription buys
you that.

> **Recommendation:** Stay with what's built. Revisit only if editing the file
> turns out to be a genuine barrier.

---

## 7. Total cost scenarios

### Free — no domain

| Item | Cost |
|---|---|
| Cloudflare Pages or Netlify | €0 |
| Formspree free | €0 |
| `greenflagclub.pages.dev` address | €0 |
| Email: keep gfcinfoireland@gmail.com | €0 |
| **Total** | **€0/year** |

Completely legitimate for a market-stall or Instagram-led business. The only
loss is the address in your bio looks less established.

### Recommended

| Item | Year one | Ongoing |
|---|---|---|
| Cloudflare Pages | €0 | €0 |
| Formspree free | €0 | €0 |
| `gfc.ie` at Blacknight | ~€6 | ~€31 |
| Zoho Mail free — `info@gfc.ie` | €0 | €0 |
| **Total** | **~€6** | **~€31/year** |

### If you want everything paid-tier

| Item | Ongoing |
|---|---|
| `gfc.ie` | ~€31/yr |
| Netlify Personal | ~$9/mo |
| Formspree Basic | ~$10/mo |
| Google Workspace | ~$7/mo |
| **Total** | **~€320–350/year** |

Listed only so you can see there's no hidden benefit in it at this scale. None
of these upgrades would make the site better today.

---

## 8. What changes the cost later

Things that would actually move you off the free tiers:

- **More than 50 enquiries a month** → Formspree paid, ~$10/mo. A good problem.
- **Serious traffic on Netlify** → the 300-credit cap. Not an issue on
  Cloudflare Pages, which is the main reason to prefer it.
- **Needing to send from `info@gfc.ie` in Apple Mail** → Zoho Lite, ~€1/mo for
  IMAP.
- **A second staff address** (`orders@`, `events@`) → free on Zoho up to 5
  users; on Google Workspace each one is another ~€7/month.
- **Selling online** → a shop is a different project. Shopify starts around
  €25–30/month; Stripe Payment Links are free plus transaction fees if you only
  need to take payment for a few items.
- **The domain renewal in year two** — the jump from ~€6 to ~€31 is the one
  cost surprise in this plan. It's in the table above so it isn't one.

---

## Related documents

- **[HOSTING-PLAN.md](HOSTING-PLAN.md)** — the step-by-step runbook for actually
  doing all this
- **[GUIDE.md](GUIDE.md)** — running and editing the site
