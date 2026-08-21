# Green Flag Club — Website Guide

Everything you need to run, edit, and publish the site. Written so you can
follow it top to bottom without knowing how to code.

**Contents**

1. [What was built](#1-what-was-built)
2. [The brand](#2-the-brand)
3. [Files in this folder](#3-files-in-this-folder)
4. [Preview it on your Mac](#4-preview-it-on-your-mac)
5. [Adding your photos](#5-adding-your-photos)
6. [Editing the words](#6-editing-the-words)
7. [The contact form and how email actually works](#7-the-contact-form-and-how-email-actually-works)
8. [Putting it online](#8-putting-it-online) — see also **HOSTING-PLAN.md**
9. [Using your own domain](#9-using-your-own-domain)
10. [Email at your domain](#10-email-at-your-domain)
11. [Order of operations](#11-order-of-operations)
12. [Before you go live](#12-before-you-go-live)
13. [Troubleshooting](#13-troubleshooting)

---

## 1. What was built

A single-page website for Green Flag Club, built as one self-contained HTML
file. No framework, no build step, no dependencies to install. You edit the file
in a text editor, drag the folder to a host, and it's live.

**Sections, top to bottom:**

| Section | What's in it |
|---|---|
| Sticky nav | Logo, links, "Say hello" button |
| Hero | Headline, intro, two buttons, three stats, large photo |
| Flavours | Six photo cards — the main gallery |
| Our matcha | Three short value blocks on a cream panel |
| Contact | Contact details and the enquiry form |
| Footer | Logo, Instagram, email, copyright |

**Extras already included:** click any flavour photo to open it full-size
(lightbox), sections fade in as you scroll, the leaf logo is drawn as SVG so it
stays sharp at any size, and there's a spam trap on the form.

It has been checked at desktop width and at a real 390px phone viewport — no
horizontal scrolling, nothing cut off. It also renders fully with JavaScript
switched off, so a script error can never leave the page blank.

---

## 2. The brand

The colours were sampled directly from your logo file rather than eyeballed, so
they match exactly.

| Token | Hex | Where it's used |
|---|---|---|
| Brand green | `#5F6B4C` | Page background |
| Cream | `#F9F3E6` | Text, cards, the form panel |
| Ink | `#212328` | Wordmark |
| Lime | `#C7F04A` | Buttons, highlights, the leaf mark |
| Berry | `#FF6B8A` | Strawberry card |
| Mango | `#FFB020` | Mango Yuzu card |
| Ube | `#A48CF0` | Ube Coconut card |
| Mint | `#4FD1A5` | Mint Chip card |
| Yuzu | `#F7E04B` | Honey Vanilla card |

**Why this palette.** You asked for the logo green as the background plus
vibrant colour. That's also where matcha branding sits right now: an earthy
sage-and-cream base lifted by one electric accent. Good matcha brands
deliberately avoid drowning the page in green — they ground it in warm neutrals
and let a single bright colour do the shouting. Here the brand green is the
ground, cream carries the reading, lime is the shout, and each flavour gets its
own accent so the gallery reads as a range rather than six of the same card.

Cream on brand green measures 5.1:1 contrast, which passes accessibility
standards for body text. If you change the background colour, re-check that.

**The wordmark.** Your logo sets "Green" in near-black and "Flag" in italic
sage green, with CLUB centred underneath in wide-tracked caps — two-tone, and
much lighter in weight than a typical logo. The site keeps that exact
relationship, translated onto the dark green background: "Green" in cream,
"Flag" in italic lime, and the leaf mark in the same lime as "Flag" — because
in your logo the leaf and "Flag" share a colour while "Green" differs. CLUB sits
centred below at 0.5em letter-spacing. The footer uses the full stacked lockup
(leaf above the wordmark) like the original artwork; the nav uses the
horizontal version so it fits in the bar.

If you'd rather the leaf were cream rather than lime — matching your Instagram
avatar exactly — search `style="color:var(--lime)"` in `index.html` and change
those to `style="color:var(--cream)"`.

**Fonts:** Cormorant Garamond for headings (the elegant serif matching your
wordmark, including the italic used for "Flag") and Jost for body text. Both
load free from Google Fonts.

---

## 3. Files in this folder

```
website/
├── index.html              The entire site — HTML, CSS and JavaScript in one file
├── favicon.svg             The leaf mark shown in the browser tab
├── README.md               Short summary pointing at the docs
├── images/                 Your photos go here
└── docs/
    ├── GUIDE.md            This document
    ├── HOSTING-PLAN.md     Step-by-step: publishing, gfc.ie, info@gfc.ie
    └── OPTIONS-AND-COSTS.md  Every option at each step, with prices
```

You will only ever edit `index.html` and add files to `images/`. Nothing in
`docs/` affects the website — those files are for you to read.

---

## 4. Preview it on your Mac

Double-click `index.html`. It opens in your browser. That's it.

Every time you change the file, save it and refresh the browser to see the
change. If a change doesn't appear, hard-refresh with **Cmd + Shift + R**.

If you'd rather serve it properly (closer to how it behaves online), open
Terminal and run:

```bash
cd /Users/architjhingan/PycharmProjects/PythonProject/website
python3 -m http.server 8000
```

Then open <http://localhost:8000>. Press **Ctrl + C** in Terminal to stop.

---

## 5. Adding your photos

Drop your images into the `images/` folder using these exact filenames:

| Filename | Where it appears |
|---|---|
| `hero.jpg` | Large image at the top of the page |
| `classic.jpg` | Classic Ceremonial card |
| `strawberry.jpg` | Strawberry card |
| `mango.jpg` | Mango Yuzu card |
| `ube.jpg` | Ube Coconut card |
| `mint.jpg` | Mint Chip card |
| `vanilla.jpg` | Honey Vanilla card |
| `share.jpg` | Optional — the preview image when the link is shared |

Filenames are case-sensitive. `Classic.JPG` will not work; `classic.jpg` will.

Until a file exists, that slot shows a coloured placeholder printing the exact
filename it's waiting for. Nothing looks broken while you fill the gallery in,
and you always know which photo is missing.

**Photo tips**

- Portrait orientation crops best — the cards are 4:5.
- Resize to about 1200px wide and save as JPG under ~300KB each. Large photos
  straight off a phone are 4–8MB and will make the page slow on mobile data.
- To batch-resize on a Mac: select the files in Finder, open in Preview,
  select all in the sidebar, then **Tools → Adjust Size**.
- Shoot in natural light with a consistent background and edit them the same
  way. A gallery reads as professional when the photos look like a set.

---

## 6. Editing the words

Open `index.html` in any text editor (TextEdit, VS Code, PyCharm — all fine).
Everything visible on the page is plain text between angle brackets. Change the
words, leave the brackets alone.

### Changing a flavour

Search for the flavour name, for example `Mango Yuzu`. You'll find a block like:

```html
<div class="card-top"><h3>Mango Yuzu</h3><span class="pill">Summer</span></div>
<p>Alphonso mango and a squeeze of yuzu. Tart, tropical and unreasonably bright in the sun.</p>
<div class="price"><i></i>€6.10</div>
```

Edit the name, the pill label, the description and the price.

### Adding a new flavour

1. Search for `<!-- ---- CARD:` — that comment marks the first card.
2. Copy one whole block from `<figure class="card"` down to `</figure>`.
3. Paste it directly below, before the closing `</div>` of the gallery.
4. Change five things in the copy: the `--tint` colour, the image filename
   (both in `src` and in the placeholder text), the heading, the description,
   and the price.

For `--tint`, use one of the accent hexes from section 2, or any hex you like.

### Removing a flavour

Delete the whole block from `<figure class="card"` to `</figure>`. The grid
reflows on its own — nothing else to adjust.

---

## 7. The contact form and how email actually works

The form sends to **gfcinfoireland@gmail.com**.

### The thing to understand first

This is a static site. There is no server behind it, and a web browser cannot
send email on its own. Something has to receive the submission and pass it to
your inbox. That's the only job Formspree does below.

### How it behaves right now

With no setup, clicking **Send message** opens the visitor's own email app with
the subject and message pre-filled. It works immediately, but it depends on
them having a mail app configured — which many people on phones and webmail
don't. Fine for testing, not good enough for a live site.

### Connecting it properly (2 minutes, free)

1. Go to <https://formspree.io> and sign up **using gfcinfoireland@gmail.com**.
2. Click **+ New Form**, name it "Green Flag Club website", click **Create**.
3. Copy the endpoint it shows you. It looks like
   `https://formspree.io/f/xtsdcbwq`.
4. Open `index.html`, find this line near the bottom (around line 601):

   ```js
   const FORM_ENDPOINT = "";
   ```

   Paste your endpoint between the quotes:

   ```js
   const FORM_ENDPOINT = "https://formspree.io/f/xtsdcbwq";
   ```

5. Save and re-upload the site.
6. Send yourself a test message through the live form.
7. **Click the confirmation link Formspree emails you.** This step is easy to
   skip and nothing gets delivered until you do it.

### What happens after that

Visitor fills in the form → their browser sends it to Formspree → Formspree
emails gfcinfoireland@gmail.com with the message → you hit Reply and it goes
straight back to the visitor.

Free tier covers 50 submissions per month. A hidden honeypot field is already
built into the form, so bots that fill everything in automatically get silently
discarded.

### Alternative

If you host on Netlify, Netlify Forms does the same job with no third-party
account and 100 submissions/month free. It needs extra attributes on the
`<form>` tag and a change to the JavaScript, so it's more editing than
Formspree's one-line change. Formspree also keeps working if you move hosts.

---

## 8. Putting it online

Full step-by-step runbook: **[HOSTING-PLAN.md](HOSTING-PLAN.md)**.

The short version: drag the `website` folder onto
<https://app.netlify.com/drop>. It's live in about a minute, free, no account
needed to start. To update it later, drag the folder again.

Comparison of every host with prices:
**[OPTIONS-AND-COSTS.md](OPTIONS-AND-COSTS.md)**.

---

## 9. Using your own domain

Full steps, costs and timings: **[HOSTING-PLAN.md](HOSTING-PLAN.md)** phases 3–4.

Worth knowing up front: as of 19 Aug 2026 both **`gfc.ie`** and
**`greenflagclub.ie`** are unregistered, while `gfc.com` and
`greenflagclub.com` have been taken since 1995 and 2017. `.ie` requires proof
of a connection to Ireland and is reviewed by a person, so allow a couple of
working days.

---

## 10. Email at your domain

Full steps: **[HOSTING-PLAN.md](HOSTING-PLAN.md)** phase 5.

The short version: Zoho Mail's free plan gives you a real `info@gfc.ie` mailbox
at no cost. Registrar forwarding and Cloudflare Email Routing are also free but
can only receive, not send.

One thing to know now: forwarding lets you *receive* at the domain, not send
from it, and Gmail's "Send mail as" for non-Google addresses is being removed
in **January 2027**. If you want replies to come from `info@gfc.ie`, use a real
mailbox — Zoho's free plan does this at no cost.

If you switch the site to a domain address, search `gfcinfoireland` in
`index.html` — there are 5 mentions to update.

---

## 11. Order of operations

The sequence that avoids redoing work:

1. Add your photos to `images/` (section 5)
2. Replace the placeholder flavour names, notes and prices (section 6)
3. Preview locally and check it on your phone (section 4)
4. Deploy to Netlify Drop — HOSTING-PLAN phase 1
5. Set up Formspree and send a test message — HOSTING-PLAN phase 2
6. Buy and connect `gfc.ie` — HOSTING-PLAN phases 3–4
7. Set up `info@gfc.ie` and update the addresses — HOSTING-PLAN phases 5–6

Steps 1–5 get you a working public site and can be done in an evening. 6 and 7
depend on the `.ie` eligibility review, so start them when you're ready to
commit to the domain.

---

## 12. Before you go live

The site ships with placeholder content so it looks real while you build it.
Replace it:

- [ ] **Flavour names, tasting notes and prices are invented.** The €5.20–€6.40
      pricing is made up. Swap in your real menu.
- [ ] **The stats in the hero** — "6 flavours", "100% ceremonial grade", "Uji
      single origin" — check these are actually true of your product.
- [ ] **The "Our matcha" section** describes first-harvest Uji leaves and stone
      grinding. Only keep it if it's accurate. Do not claim sourcing you don't
      have.
- [ ] **Photos** — every card should be your own photo, not a placeholder.
- [ ] **Instagram link** is set to `instagram.com/greenflag_club/`. Confirm
      that's right.
- [ ] **Formspree connected** and tested with a real message.

The last two points on accuracy matter more than they look. Food and sourcing
claims on a website are the kind of thing customers repeat back to you.

---

## 13. Troubleshooting

**A photo isn't showing.** The filename doesn't match. Check spelling, and
check the extension is lowercase `.jpg` not `.JPG` or `.jpeg`. The placeholder
tells you the exact filename it wants.

**The form does nothing when I click Send.** Either required fields are empty
(it will tell you), or `FORM_ENDPOINT` is still `""` and your browser has no
mail app set up. Do section 7.

**I submitted a test but got no email.** You almost certainly haven't clicked
Formspree's confirmation link. Check spam too.

**My changes aren't showing.** Save the file, then hard-refresh with
**Cmd + Shift + R**. If it's the live site, re-drag the folder to Netlify.

**The domain shows an error or the old page.** DNS is still propagating. Give
it a few hours before changing anything.

**Everything looks unstyled — plain text on white.** You've opened the file
without its folder, or moved `index.html` away from `images/` and
`favicon.svg`. Keep the folder together.

**The page looks broken on my phone but fine on my laptop.** Hard-refresh on
the phone. It was tested at 390px so the layout itself is sound.
