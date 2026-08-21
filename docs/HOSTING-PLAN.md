# Hosting Plan — Green Flag Club

A step-by-step runbook to take the site from a folder on your Mac to
`gfc.ie` with `info@gfc.ie` arriving in your Gmail.

Follow the phases in order. Each one leaves you with something that works, so
you can stop after any phase and still have a live site.

- **Phase 1** gets you online in about 5 minutes, free.
- **Phase 2** makes the contact form actually email you.
- **Phases 3–5** add the domain and `info@gfc.ie`.

---

## Domain availability — checked 19 Aug 2026

I ran a live WHOIS query against the IE Domain Registry:

| Domain | Status |
|---|---|
| **`gfc.ie`** | **Available** |
| **`greenflagclub.ie`** | **Available** |
| `gfc.com` | Taken — registered 1995 |
| `greenflagclub.com` | Taken — registered 2017 |
| `greenflag.ie` | Taken — registered 2004 |

This is the clearest argument for going `.ie`: both names you'd actually want
are free, while the `.com` versions were gone decades ago. A three-letter
`.ie` being unregistered is unusual — worth moving on sooner rather than later.

Two caveats. Availability can change at any time, and a registrar may class a
three-letter domain as premium and charge more than the usual €20–30. You'll
find out at checkout. If `gfc.ie` turns out to be premium-priced,
`greenflagclub.ie` is the fallback and is also free.

---

## The recommended stack

| Layer | Choice | Year one | Ongoing |
|---|---|---|---|
| Hosting | Netlify to start, Cloudflare Pages long-term | €0 | €0 |
| Contact form | Formspree free | €0 | €0 |
| Domain | `gfc.ie` at Blacknight | ~€6 inc VAT | ~€31 inc VAT |
| Email | Zoho Mail free | €0 | €0 |

Total running cost: **the domain only** — about €6 in year one and about €31 a
year after that. Everything else stays on free tiers at this size.

**Why start on Netlify:** you publish by dragging a folder onto a web page, with
no account and no command line. Nothing else is that fast.

**Why move to Cloudflare Pages later:** Netlify's free tier moved to a credits
model in 2026 — roughly 15GB of bandwidth or 20 deploys a month, shared. For a
page built around large photos that's a real ceiling. Cloudflare Pages has
genuinely unlimited bandwidth on free. Moving hosts is just re-uploading the
same folder, so there's no cost to starting on Netlify and switching.

Full comparison of every option with prices:
**[OPTIONS-AND-COSTS.md](OPTIONS-AND-COSTS.md)**.

---

## Phase 1 — Get it online (5 minutes, free, no card)

1. Open <https://app.netlify.com/drop>
2. Drag the whole `website` folder onto the page
3. Wait a few seconds — it's live at something like
   `heroic-matcha-a1b2c3.netlify.app`
4. Open the link on your phone and check it looks right

Then claim it so it doesn't expire:

5. Click **Sign up** and create a free account (GitHub or email, either is fine)
6. **Site configuration → Change site name** → set it to `greenflagclub`
7. You now have `greenflagclub.netlify.app` permanently

**To update the site later:** go to your site → **Deploys** → drag the folder
onto the drop zone again. The old version is kept, so you can roll back from
the Deploys list if you break something.

- [ ] Site is live and loads on my phone
- [ ] Account created and site renamed

---

## Phase 2 — Connect the contact form (10 minutes, free)

Right now the form falls back to opening the visitor's mail app. That breaks
for anyone without mail configured, so do this before you share the link.

**Why this step exists:** the site is static — there's no server behind it, and
a browser cannot send email on its own. Formspree is the piece that receives
the submission and relays it to your inbox.

1. Go to <https://formspree.io> and sign up **using gfcinfoireland@gmail.com**
2. **+ New Form** → name it `Green Flag Club website` → **Create**
3. Copy the endpoint — it looks like `https://formspree.io/f/xtsdcbwq`
4. Open `index.html` and find this line (around line 601):

   ```js
   const FORM_ENDPOINT = "";
   ```

   Paste your endpoint in:

   ```js
   const FORM_ENDPOINT = "https://formspree.io/f/xtsdcbwq";
   ```

5. Save, then re-upload the folder to Netlify (Phase 1, "to update")
6. Go to the live site and send yourself a test message
7. **Check your Gmail and click Formspree's confirmation link.** Nothing is
   delivered until you do this. It's the step everyone misses.
8. Send a second test and confirm it lands in the inbox

Once live: visitor submits → Formspree emails gfcinfoireland@gmail.com → you
hit Reply and it goes straight back to the visitor.

- [ ] Endpoint pasted and re-uploaded
- [ ] Confirmation link clicked
- [ ] Test message received in Gmail

---

## Phase 3 — Buy gfc.ie (15 minutes + up to 2 working days)

`.ie` is not sold by the usual international registrars. Buy from an Irish one:

| Registrar | Notes |
|---|---|
| [Blacknight](https://www.blacknight.com) | Irish, well known, good support |
| [Hosting Ireland](https://www.hostingireland.ie) | Irish |
| [Register365](https://www.register365.com) | Irish |

### The eligibility check

`.ie` requires a **verifiable connection to Ireland**. Since 2018 you no longer
have to justify the specific name — you just prove the connection, then you can
register any available domain.

What you'll upload depends on who's registering:

- **As an individual:** Irish passport, birth certificate, driver's licence or
  PPS card. Irish residents can instead use proof of residence — a recent bank
  statement, a Revenue letter, or similar official document.
- **As a business:** a CRO company number, a Registered Business Name, or a VAT
  number. A non-Irish company can qualify by showing it trades with Irish
  customers.

A human reviews this, so it is **not instant** — allow up to a couple of
working days. Applications get rejected for mismatched details, so make sure
the name on your ID matches the name on the registration exactly.

### While buying

- [ ] Check whether `gfc.ie` is priced normally or as a premium three-letter
      domain. If premium and too expensive, take `greenflagclub.ie`.
- [ ] **Turn on auto-renew.** A lapsed domain is the single most common way
      small businesses lose their web presence.
- [ ] Note whether the registrar includes **email forwarding** free with the
      domain. You probably won't need it — Phase 5 recommends Zoho instead —
      but it's the simplest fallback if Zoho's free plan isn't available in
      your region.

---

## Phase 4 — Point the domain at the site (30 minutes + DNS wait)

1. In Netlify: **Domain management → Add a domain** → type `gfc.ie`
2. Netlify offers you one of two routes:
   - **Nameservers** — it gives you a few addresses to paste into your
     registrar's control panel. Simpler. Take this one *unless* you're doing
     the Cloudflare email route in Phase 5.
   - **DNS records** — you add an A record and a CNAME manually at the
     registrar. More steps, same result.
3. Paste whichever it gives you into the registrar's DNS or nameserver settings
4. Wait. DNS changes take anywhere from a few minutes to a few hours to spread
   worldwide. There is nothing to fix during this time — resist the urge to
   change settings because it "isn't working yet."
5. Netlify issues the HTTPS certificate automatically and free once the domain
   resolves. You never buy an SSL certificate.

- [ ] `https://gfc.ie` loads the site
- [ ] `https://www.gfc.ie` also works (Netlify handles both)
- [ ] The padlock shows in the browser

---

## Phase 5 — info@gfc.ie

This is separate from the contact form. The form keeps working either way —
this is about having a professional address on the site and on Instagram.

**Pick one route only.** Routes A and C both set MX records on your domain, and
a domain can only have one mail handler — configuring both will break mail.

Wherever a route says "add DNS records", add them where your DNS actually lives,
which depends on what you chose in Phase 4: your registrar's panel if you added
records manually, Netlify's DNS panel if you switched to Netlify's nameservers,
or Cloudflare's if you're on Route C.

### Route A — Zoho Mail free (recommended)

The only free option that gives you a **real mailbox**, so you can send *as*
`info@gfc.ie` rather than just receive at it. Free for up to 5 users.

1. Go to <https://www.zoho.com/mail/> and sign up for the free plan, choosing
   **"Sign up with a domain I already own"** → `gfc.ie`
2. Zoho gives you DNS records (a TXT record to verify ownership, then MX
   records for mail). Add them wherever your DNS lives — see the note above.
3. Wait for verification — usually minutes
4. Create the mailbox `info@gfc.ie`
5. Optionally set Gmail to fetch from it, or just use Zoho's webmail and phone
   app

Two caveats before you commit: the free plan is region-restricted, so confirm
it's offered to you at signup, and it has no IMAP/POP — you use Zoho's own
webmail and app rather than Apple Mail. Zoho Mail Lite (~€1/month) removes the
IMAP restriction if that matters.

### Route B — Registrar forwarding (simplest, if included)

If your registrar includes email forwarding, use it. In their control panel,
create a forward: `info@gfc.ie` → `gfcinfoireland@gmail.com`. That's the whole
job — usually two fields and a save button. Nothing else to configure.

### Route C — Cloudflare Email Routing (free, if your registrar charges)

Free forever, but it requires moving your DNS to Cloudflare.

1. Create a free Cloudflare account and **Add a site** → `gfc.ie`
2. Cloudflare gives you two nameservers — set those at your registrar
   (this replaces what you did in Phase 4, so do this *instead of* Netlify's
   nameservers)
3. Back in Netlify, use the **DNS records** option and add those records in
   Cloudflare's DNS panel. Set them to **DNS only** (grey cloud, not orange) so
   Netlify keeps handling the HTTPS certificate.
4. In Cloudflare: **Email → Email Routing** → let it add the MX and SPF records
   automatically
5. Add `gfcinfoireland@gmail.com` as the destination → Cloudflare emails you a
   verification link → click it
6. Create the route: `info@gfc.ie` → that destination

Mail to `info@gfc.ie` now arrives in your normal Gmail.

### The catch you should know about now

Routes B and C are **forwarding** — they receive mail, not send it. Replies go
out from your Gmail address, not from `info@gfc.ie`. Route A (Zoho) is a real
mailbox and does not have this problem, which is why it's the recommendation.

The usual workaround is Gmail's "Send mail as", but **Google is removing that
for non-Google addresses in January 2027**. Receiving keeps working
indefinitely; sending *as* the domain from inside Gmail stops.

So: if you only need to receive at `info@gfc.ie`, forwarding is free and fine
forever. If you want replies to come *from* `info@gfc.ie`, use Route A — it's
also free. Google Workspace (~€7/user/month) does the same thing with a Gmail
interface if you'd rather pay for the familiarity.

- [ ] Only one of Routes A/B/C configured
- [ ] Test: email `info@gfc.ie` from your phone and confirm it arrives
- [ ] If you used Route A, send *from* `info@gfc.ie` and confirm it goes out

---

## Phase 6 — Put the new address on the site

Once `info@gfc.ie` works, update the site. In `index.html`, search for
`gfcinfoireland` — there are **5 mentions**:

- `const TO_EMAIL = "..."` in the script
- the `mailto:` link in the contact list
- the address shown in the contact list
- the note under the form button
- the `mailto:` link in the footer

Replace all five, save, re-upload to Netlify.

**Leave Formspree pointed at the Gmail account** unless you have a reason to
change it — it already works, and the Gmail inbox is where the forwarded mail
lands anyway.

- [ ] All 5 mentions updated
- [ ] Re-uploaded and the form still delivers

---

## Costs

| Item | Year one | Ongoing |
|---|---|---|
| Hosting (Netlify or Cloudflare Pages) | €0 | €0 |
| Formspree (50 msgs/month) | €0 | €0 |
| `gfc.ie` at Blacknight | ~€6 inc VAT | ~€31 inc VAT |
| Zoho Mail free — `info@gfc.ie` | €0 | €0 |
| **Total** | **~€6** | **~€31/year** |

Note the year-two jump: Blacknight's €4.99 is a first-year intro price
excluding VAT, and renewal is €24.99 + VAT. That's the one cost surprise in
this plan, so it's flagged here rather than left to find later.

Every alternative and its price — other hosts, form services, mailbox
providers, and what Squarespace or Wix would cost instead — is in
**[OPTIONS-AND-COSTS.md](OPTIONS-AND-COSTS.md)**.

---

## Timeline

| Phase | Hands-on | Waiting |
|---|---|---|
| 1 — Get online | 5 min | — |
| 2 — Form email | 10 min | — |
| 3 — Buy domain | 15 min | Up to 2 working days for review |
| 4 — Connect domain | 30 min | Minutes to hours for DNS |
| 5 — info@gfc.ie | 20 min | Minutes |
| 6 — Update site | 10 min | — |

Phases 1 and 2 can be done tonight. The rest depends on the `.ie` review.

---

## If something goes wrong

**Domain shows a Netlify "not found" page.** DNS hasn't finished propagating,
or the records point at the wrong place. Wait a few hours first, then re-check
the records against what Netlify shows.

**Certificate warning / "not secure".** The certificate is issued after DNS
resolves. Give it an hour. If it persists in Cloudflare Route B, check your DNS
records are grey-cloud (DNS only), not orange — proxying in front of Netlify is
the usual cause.

**`.ie` application rejected.** Almost always mismatched details between your ID
and the registration form. Fix and resubmit — there's no penalty.

**Form stopped working after moving to the domain.** Formspree endpoints aren't
domain-locked, so this is normally just an old cached copy. Hard-refresh with
**Cmd + Shift + R**, and confirm you re-uploaded after editing.

**I need to undo a deploy.** Netlify → **Deploys** → pick an earlier one →
**Publish deploy**. Instant rollback.

---

## Related documents

- **[OPTIONS-AND-COSTS.md](OPTIONS-AND-COSTS.md)** — every option at each step
  with prices, and total cost scenarios
- **[GUIDE.md](GUIDE.md)** — running and editing the site: photos, flavours,
  copy, troubleshooting
- **[../README.md](../README.md)** — what's in the project folder
