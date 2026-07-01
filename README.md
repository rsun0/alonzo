# Alonzo — landing site

A single static page for the Alonzo Big Tech mentorship program. No build step,
no dependencies, no backend. Open `index.html` in any browser to preview.

## Files

```
index.html             the page
logo.png               brand mark (nav + hero)
favicon.png            browser-tab icon
apple-touch-icon.png   home-screen icon
og-image.png           social share preview (1200x630)
```

## Editing links

The Apply link, contact email, and LinkedIn URL are already filled in. To change
them, edit the one config block at the bottom of `index.html` (search `const ALONZO`):

```js
const ALONZO = {
  applicationFormUrl: "https://forms.gle/FPrAjZwJCHiiRrn2A",
  linkedinUrl: "https://www.linkedin.com/company/alonzokr/",
  contactEmail: "contact@alonzo.kr"   // blank ("") hides the email buttons
};
```

If `applicationFormUrl` is ever blank, the Apply buttons safely show
"Applications opening soon" instead of a dead link.

## Mentors (placeholders for now)

The mentors section shows **placeholder cards** until each mentor confirms they're
OK with their photo/bio being public. The real roster (names, companies, years)
and a ready-to-use card template — including how to add a photo — are kept in an
HTML comment directly under the mentor grid in `index.html`.

To add a real mentor once approved:
1. Put their photo in a `mentors/` subfolder (e.g. `mentors/ray-sun.jpg`).
2. Copy the template from the comment, fill in name / role / bio, and replace one
   placeholder card.

## Become a mentor & partners

- **Become a mentor** section lists the areas we're recruiting for (computer
  networking, quant trading, HCI research) with an email button.
- **Partner Organizations** box links to The Yeon Project on Instagram.

## Deploy for free

Drag this `alonzo-site` folder onto **[Netlify](https://www.netlify.com)** (or
import it on **Vercel** or **Cloudflare Pages**). No build settings are needed for
a static page, and all three serve from a global CDN (reachable from Korea worldwide).

### Custom domain (alonzo.kr)

After deploying, add `alonzo.kr` under the host's domain settings and
point your DNS there — HTTPS is handled automatically. The `og:url` / `og:image`
tags in `index.html` already use this domain, so social previews light up once DNS
is live. If you launch on a temporary `*.netlify.app` URL first, update those two
tags to that URL in the meantime.

---

See [`docs/alonzo_website_plan.md`](docs/alonzo_website_plan.md) for the full plan
and [`docs/alonzo_application_form.md`](docs/alonzo_application_form.md) for the
application-form draft.
