# Alonzo Website — Implementation Plan

A simple, free landing page for **Alonzo**, a mentorship program for Korean computer science students who want to work in the United States. This plan is written so you can either follow it yourself or paste sections into Claude Code / Codex to build.

---

## 1. Goal & scope

A single-page landing site with a top navigation bar containing a few buttons, exactly as Ray asked:

- **Apply** — links out to a Google Form (the application)
- **LinkedIn** — links to the Alonzo LinkedIn page
- **Contact** — email / message link

Everything else (about, how it works, mentors) is supporting content on the same page that the nav scrolls to. No login, no database, no backend — this keeps it free, fast, and almost zero-maintenance.

**Decisions locked in (from your answers):**

- Application form: **Google Form** (button links out to it)
- Hosting: **Netlify or Vercel** (free tier)
- Deliverable: this plan **plus a working demo** (`index.html`)

---

## 2. What the demo already covers

The attached `index.html` is a complete, working single file you can open in any browser. It includes:

- Sticky top nav with **About · LinkedIn · Contact · Apply** (Apply is the highlighted button), and a mobile hamburger menu
- **Hero** section with headline, one-line description, two call-to-action buttons, and three quick stats
- **About** — three cards explaining the program
- **How it works** — a 4-step flow (Apply → Get matched → Meet & grow → Reach your goals)
- **Mentors** — a grid of mentor cards (names pulled from the LinkedIn post as placeholders)
- **Contact** — email + LinkedIn message buttons
- Responsive layout (looks good on phone and desktop), smooth scrolling, no external dependencies

It's intentionally one file with no frameworks so it's trivial to host and edit.

---

## 3. Things to replace before launch

Search the HTML for the word `REPLACE`. There are three real values to fill in:

1. **`APPLICATION_FORM_URL`** — your Google Form link (appears twice: nav button + hero button)
2. **`LINKEDIN_URL`** — the Alonzo LinkedIn page URL (appears three times)
3. **`CONTACT_EMAIL`** — the program's contact email in the `mailto:` link

Also confirm the **mentor names** are correct and that each person is OK being listed publicly. They were lifted from the LinkedIn post as a starting point — get a quick OK before going live.

---

## 4. Recommended structure

Even though it's one page, keep the project folder tidy so it's easy to host and grow later:

```
alonzo-site/
├── index.html        # the landing page (the demo)
├── favicon.ico       # optional: small browser-tab icon
└── README.md         # optional: notes for whoever edits next
```

A single static `index.html` is all Netlify/Vercel need.

---

## 5. Tech stack

| Layer | Choice | Why |
|---|---|---|
| Page | Plain HTML + CSS (one file) | No build step, no dependencies, anyone can edit |
| Interactivity | A few lines of vanilla JS | Mobile menu + footer year only |
| Application form | Google Forms | Free, no backend, results land in a Google Sheet |
| Hosting | Netlify or Vercel (free) | Drag-and-drop or Git deploy, free HTTPS + URL |

You don't need React, a framework, or a database for this. If the program grows (e.g. wanting a separate mentors page or events list), it can be expanded later without redoing anything.

---

## 6. Set up the Google Form (the "Apply" button)

1. Go to **forms.google.com** and create a new form titled "Alonzo Application".
2. Suggested questions: Name, Email, University, Year/grade, Major, Target role/companies in the U.S., Why you want to join, LinkedIn/GitHub (optional).
3. Top-right **Send → link icon (🔗) → Copy** the share link (it looks like `https://forms.gle/...`).
4. Paste that link into the HTML everywhere it says `REPLACE_WITH_YOUR_GOOGLE_FORM`.
5. In the form's **Responses** tab, click the Sheets icon to send applications to a spreadsheet automatically.

This gives you a clean, free application pipeline with zero code.

---

## 7. Deploy for free (Netlify — easiest path)

**Option A — drag and drop (no account setup beyond signup, fastest):**

1. Create a free account at **netlify.com**.
2. Put `index.html` in a folder by itself.
3. On the Netlify dashboard, drag that folder onto the "deploy" area.
4. You instantly get a live URL like `random-name.netlify.app`.
5. Rename it under **Site settings → Change site name** to something like `alonzo.netlify.app`.

**Option B — connect to GitHub (better for ongoing edits):**

1. Push the project to a GitHub repo.
2. In Netlify, **Add new site → Import from Git → pick the repo**.
3. Build command: leave empty. Publish directory: `/` (root).
4. Every time you push a change to GitHub, the site redeploys automatically.

**Vercel** works almost identically: sign up, import the repo (or use `vercel` CLI / drag-drop), no build settings needed for a static page. Either is fine — Netlify's drag-and-drop is the gentlest start.

**Custom domain (optional, costs ~$10–15/yr):** buy a domain (e.g. from Namecheap), then add it under Netlify/Vercel domain settings — they handle HTTPS automatically.

---

## 8. Step-by-step build checklist

A clean order to take this from demo to live:

1. ☐ Review the demo `index.html` in a browser; share with Ray for feedback.
2. ☐ Apply Ray's feedback (copy, colors, section order, what to add/remove).
3. ☐ Create the Google Form and copy its link.
4. ☐ Get the real LinkedIn page URL and contact email.
5. ☐ Replace all three `REPLACE` placeholders in the HTML.
6. ☐ Confirm mentor names + permission; update the mentors grid.
7. ☐ (Optional) add a `favicon.ico`.
8. ☐ Create a free Netlify (or Vercel) account.
9. ☐ Deploy (drag-and-drop or via GitHub).
10. ☐ Test the live site: every nav button, Apply link, LinkedIn link, email link, and check it on a phone.
11. ☐ (Optional) set a custom domain.
12. ☐ Share the live URL with Ray.

---

## 9. If you want to hand this to Claude Code / Codex

A prompt you can paste:

> "I have a single-file static landing page (`index.html`) for a mentorship program called Alonzo. Help me: (1) review and clean up the HTML/CSS, (2) replace the placeholder links for a Google Form, a LinkedIn page, and a contact email, and (3) give me the exact commands to deploy it free on Netlify (or Vercel) from a GitHub repo. It's a static site with no build step."

That's all it needs — the page has no framework or build pipeline, so setup is minimal.

---

## 10. Nice-to-haves for later (not needed for v1)

- A separate **Events** or **Updates** section if the program runs recurring meetups
- **Open Graph tags** so the link previews nicely when shared on LinkedIn/KakaoTalk
- A lightweight **analytics** tool (e.g. Plausible, or free Cloudflare Web Analytics) to see visits
- Korean / English **language toggle**, given the audience

---

*Questions for Ray before building further: preferred program name/wording, brand colors or a logo, which sections to keep, and whether mentors want to be listed by name.*
