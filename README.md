# AB'26 HTML Emails

> Abhivyakti 2026 — IIIT Nagpur's Annual Cultural Fest | 19 – 21 March 2026

This repository contains all resources related to the promotional HTML emails for **Abhivyakti 2026**, including the final email, all iterative versions, design references, content drafts, wireframes, tips, and a pre-send checklist.

---

## 📂 Repository Structure

```
AB'26 HTML Emails/
├── README.md                        ← You are here
├── Final IIITN Students Mail.html   ← ✅ Final production-ready email
├── Checklist.md                     ← Pre-send QA checklist
├── Content.txt                      ← Finalized email copy (desktop + mobile)
├── Tips.md                          ← Tips for importing, sending & creating HTML mails
├── Desktop Wireframe.md             ← Desktop layout wireframe
├── Mobile Wireframe.md              ← Mobile layout wireframe
├── prompt1.txt                      ← Initial prompt / brief
├── Email Iterations/
│   └── mail1.html → mail23.html     ← All 23 iterative HTML email versions
├── Reference Designs/
│   └── Event Posters/               ← Visual inspiration & poster assets
├── Feedback Images/                 ← Screenshots / feedback from reviews
└── More Images/                     ← Additional design assets
```

---

## 📧 How to Make an HTML Email

### 1. Understand the Constraints

HTML emails are **not** like web pages. Email clients (Gmail, Outlook, Apple Mail, etc.) strip out or ignore many modern CSS features. Keep these rules in mind:

| ✅ Supported             | ❌ Not Supported              |
| ------------------------ | ----------------------------- |
| `<table>` based layouts  | Flexbox / CSS Grid            |
| Inline CSS (`style="…"`) | External stylesheets (mostly) |
| Basic `@media` queries   | JavaScript                    |
| `<img>` with hosted URLs | Local / relative image paths  |
| Simple `background-color`| Complex CSS animations         |

### 2. Set Up the HTML Skeleton

Start with this boilerplate that ensures maximum compatibility:

```html
<!DOCTYPE html>
<html lang="en" xmlns="http://www.w3.org/1999/xhtml"
      xmlns:v="urn:schemas-microsoft-com:vml"
      xmlns:o="urn:schemas-microsoft-com:office:office">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="x-apple-disable-message-reformatting">
  <meta name="color-scheme" content="light dark">
  <meta name="supported-color-schemes" content="light dark">
  <title>Your Email Title</title>

  <!--[if mso]>
  <noscript>
    <xml>
      <o:OfficeDocumentSettings>
        <o:AllowPNG/>
        <o:PixelsPerInch>96</o:PixelsPerInch>
      </o:OfficeDocumentSettings>
    </xml>
  </noscript>
  <![endif]-->

  <style type="text/css">
    /* Reset styles + responsive rules go here */
  </style>
</head>
<body style="margin:0; padding:0; background-color:#5A0F14;">
  <!-- Email content -->
</body>
</html>
```

**Key meta tags explained:**
- `x-apple-disable-message-reformatting` — Stops Apple Mail from auto-resizing text.
- `color-scheme` / `supported-color-schemes` — Enables dark mode support.
- `<!--[if mso]>` — Conditional comments that only Microsoft Outlook reads, used to fix Outlook-specific rendering.

### 3. Use Table-Based Layouts

Everything is built with nested `<table>` elements. Here's the general pattern:

```html
<!-- Outer wrapper: full-width background -->
<table role="presentation" width="100%" cellpadding="0" cellspacing="0"
       style="background-color:#5A0F14;">
  <tr>
    <td align="center" style="padding:20px 10px;">

      <!-- Inner container: fixed 600px width -->
      <table role="presentation" class="container" width="600"
             cellpadding="0" cellspacing="0"
             style="max-width:600px; width:100%;">

        <!-- Each row is a section -->
        <tr>
          <td> <!-- section content --> </td>
        </tr>

      </table>
    </td>
  </tr>
</table>
```

**Rules:**
- Always use `role="presentation"` on layout tables (for accessibility).
- Set `cellpadding="0"` and `cellspacing="0"` to avoid unexpected gaps.
- Keep the inner container at **600px max-width** — the sweet spot for email clients.
- Use `width` attribute + inline `max-width` style for safety.

### 4. Inline All Critical CSS

Most email clients ignore `<style>` blocks (Gmail on mobile, older clients). Critical styles **must** be inline:

```html
<!-- ✅ Do this -->
<td style="padding:20px; background-color:#8B1E24; color:#F6E6C3; font-family:Georgia, serif;">

<!-- ❌ Not this -->
<td class="hero-section">
```

You can keep a `<style>` block in `<head>` for responsive media queries and dark mode — Gmail desktop and Apple Mail will read it.

### 5. Add Responsive (Mobile) Styles

Use a `@media` query for screens narrower than 620px:

```css
@media only screen and (max-width: 620px) {
  .container { width: 100% !important; max-width: 100% !important; }
  .mobile-stack { display: block !important; width: 100% !important; }
  .mobile-pad { padding-left: 18px !important; padding-right: 18px !important; }
  .mobile-hide { display: none !important; }
  .mobile-center { text-align: center !important; }
  /* ... more mobile overrides */
}
```

**Common patterns:**
- **Stack columns vertically** on mobile with `.mobile-stack { display: block !important; width: 100% !important; }`
- **Hide decorative elements** with `.mobile-hide { display: none !important; }`
- **Adjust font sizes** for readability on small screens.

### 6. Support Dark Mode

Add both meta tags (`color-scheme`, `supported-color-schemes`) and a `prefers-color-scheme` media query:

```css
@media (prefers-color-scheme: dark) {
  .btn-accent-bg { background-color: #F5C945 !important; }
  .btn-accent-text { color: #3D0A0D !important; }
  .callout-bg { background-color: #4A0B0B !important; }
}
```

Use class-based selectors with `!important` to override inline styles in dark mode.

### 7. Add Preheader (Preview) Text

The preheader is the short text that appears after the subject line in the inbox. Add it right after `<body>`:

```html
<div style="display:none; max-height:0px; overflow:hidden; opacity:0;
            mso-hide:all; font-size:1px; line-height:1px;">
  Your preview text goes here.
</div>
<!-- Invisible padding to prevent Gmail from pulling body content -->
<div style="display:none; max-height:0px; overflow:hidden; opacity:0;
            mso-hide:all; font-size:1px; line-height:1px;">
  &nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;
</div>
```

The second `<div>` with `&nbsp;&zwnj;` characters acts as invisible padding so Gmail doesn't pull random body text into the preview.

### 8. Host Images Online

Images in HTML emails **must** be hosted online — email clients do not support local file paths.

**Steps:**
1. Go to [imgbb.com](https://imgbb.com/) and upload your image.
2. After uploading, find your image in the profile/gallery section.
3. Click **"Copy HTML Image Link"** — it gives you a direct URL like `https://i.ibb.co/XXXXX/image-name.png`
4. Use it in your `<img>` tag:

```html
<img src="https://i.ibb.co/XXXXX/image-name.png"
     width="200" alt="Description"
     style="display:block; width:200px; height:auto;">
```

**Image best practices:**
- Always set a `width` attribute **and** inline `width` style.
- Add `height:auto` so it scales proportionally.
- Use `display:block` to prevent phantom spacing.
- Keep file size under **300 KB** per image for fast loading.
- Always include descriptive `alt` text.

### 9. Create CTA Buttons

Use table-based "bulletproof buttons" that work everywhere, including Outlook:

```html
<table role="presentation" cellpadding="0" cellspacing="0" style="margin:0 auto;">
  <tr>
    <td align="center" style="background-color:#F5C945; border-radius:8px;">
      <a href="https://your-link.com"
         target="_blank"
         style="display:inline-block; padding:16px 36px; font-family:Arial, sans-serif;
                font-size:15px; font-weight:bold; color:#3D0A0D; text-decoration:none;">
        REGISTER NOW
      </a>
    </td>
  </tr>
</table>
```

For outline-style buttons, use `border` instead of `background-color`:

```html
<td align="center" style="border:2px solid #F5C945; border-radius:8px;">
  <a href="…" style="color:#F5C945; …">EXPLORE EVENTS</a>
</td>
```

### 10. Structure Your Email Sections

A well-structured promotional email typically follows this order:

1. **Preheader** — Hidden preview text
2. **View in Browser link** — Fallback for rendering issues
3. **Seal / Logo** — Brand identity
4. **Hero Section** — Main visual with title, date, key info, and primary CTA
5. **Gold Divider / Visual Break** — Decorative separator
6. **Introduction** — Compelling copy with supporting visuals
7. **Pass / Pricing Cards** — What's being offered
8. **Events / Features Grid** — What's included
9. **How-to / Steps** — Registration instructions
10. **Final CTA** — One last push to register
11. **Footer** — Contact info, social links, unsubscribe

### 11. Test Before Sending

Use the [Checklist.md](HTML%20Email/Checklist.md) to run through pre-send checks:

- ✅ All links work (test on both desktop and mobile)
- ✅ Images load (use public URLs, not local files)
- ✅ Mobile layout stacks correctly
- ✅ Desktop layout is centered at ~600px
- ✅ Subject line and preview text are set
- ✅ No broken characters or encoding issues

---

## 🎨 Design System

| Element           | Value                                      |
| ----------------- | ------------------------------------------ |
| **Background**    | `#5A0F14` (deep maroon)                    |
| **Panel**         | `#8B1E24` (lighter maroon)                 |
| **Gold Accent**   | `#E7C27D` (muted gold)                     |
| **Button Accent** | `#F5C945` (bright gold)                    |
| **Body Text**     | `#F6E6C3` (warm cream)                     |
| **Dark / Footer** | `#3D0A0D` (near-black maroon)              |
| **Heading Font**  | Georgia, 'Times New Roman', serif          |
| **Body Font**     | Arial, Helvetica, sans-serif               |
| **Max Width**     | 600px                                      |

---

## 🔁 Version History & Project Timeline

The email went through **23 iterations** (mail1.html → mail23.html). Below is a rough timeline of what was needed at each stage, what problems came up, and how they were solved.

---

### Phase 1 — Getting Started (mail1 – mail2)

**What was needed:** A promotional HTML email for Abhivyakti 2026 — IIIT Nagpur's Annual Cultural Fest (19–21 March 2026). Content was ready in `Content.txt`, reference designs and event posters were provided, and wireframes for desktop and mobile layouts were drafted.

| Version | What Happened |
|---|---|
| **mail1** | First draft. Set up the table-based HTML structure, added all sections (hero, events, passes, how-to-register, footer), applied the maroon + gold color scheme from the reference designs. Used placeholder/reference images. |
| **mail2** | Content refinements, basic styling fixes, layout adjustments based on initial review. |

**Key decisions made early:**
- Table-based layout (for email client compatibility)
- 600px max-width container
- Color palette: `#5A0F14` maroon bg, `#F5C945` gold buttons, `#F6E6C3` cream text
- Georgia/serif for headings, Arial/sans-serif for body

---

### Phase 2 — Real Images & Visual Polish (mail3 – mail8)

**What was needed:** Replace placeholder images with actual hosted assets (uploaded to imgbb.com). Integrate the circus/carnival theme visuals from the design team.

| Version | What Happened |
|---|---|
| **mail3** | Started integrating real images — banner, logo, seal |
| **mail4** | More asset integration, layout adjustments for image sizing |
| **mail5** | Visual polish — spacing, padding, typography tweaks |
| **mail6** | Further image refinements, asset alignment fixes |
| **mail7** | Added more design assets (prize pool graphic, ornaments) |
| **mail8** | Visual polish pass — consistent styling across all sections |

**Challenges in this phase:**
- Images needed to be hosted online (imgbb.com) since email clients don't support local files
- Getting image sizes right across different email clients
- Balancing visual richness with email file size (images should be < 300KB each)

---

### Phase 3 — Mobile & Dark Mode (mail9 – mail12)

**What was needed:** The email looked good on desktop but was broken on mobile. Also needed dark mode support for users with dark theme email clients.

| Version | What Happened |
|---|---|
| **mail9** | Added `@media (max-width: 620px)` responsive rules — stacking columns, adjusting font sizes |
| **mail10** | Fixed mobile button sizing (full-width CTAs on mobile) |
| **mail11** | Dark mode support — added `color-scheme` meta tags, `@media (prefers-color-scheme: dark)` overrides |
| **mail12** | Mobile + dark mode polish — tested and fixed edge cases |

**Key responsive classes created:**
- `.mobile-stack` — Stack side-by-side columns vertically
- `.mobile-hide` — Hide decorative elements on mobile
- `.mobile-pad` — Add safe padding on small screens
- `.mobile-btn` — Full-width buttons on mobile

---

### Phase 4 — Character Assets & UX (mail13 – mail16)

**What was needed:** Add the circus character illustrations (girl, magician, ringmaster) to the email body. Add a logo bar. General UX improvements.

| Version | What Happened |
|---|---|
| **mail13** | Added IIIT Nagpur golden logo to the hero section |
| **mail14** | Integrated circus character assets — girl, magician |
| **mail15** | Added ringmaster (flipped), positioned characters alongside intro text |
| **mail16** | Logo bars, final character placement tweaks, UX improvements to pass cards and event grid |

**Assets added in this phase (all hosted on ibb.co):**
- Girl character (`Girl-Asset.png`)
- Magician (`Magician-Alone.png`)
- Ringmaster flipped (`Ring-Master-Alone-Flipped.png`)
- IIIT Nagpur golden logo (`iiitn-logo-golden.png`)
- Top center ornament (`Top-Center-Asset-High-Quality.png`)
- AB'26 golden icon (`AB-26-Plain-Icon-Golden.png`)

---

### Phase 5 — Asset Refinements (mail17 – mail18)

**What was needed:** Updated banner design from the design team, prize pool asset refresh.

| Version | What Happened |
|---|---|
| **mail17** | Swapped in updated banner (`AB-26-Updated-Banner.png`) |
| **mail18** | Updated prize pool asset (`Prize-Pool-asset-updated-2.png`), final visual alignment |

---

### Phase 6 — Layout & Content Changes (mail19 – mail21)

**What was needed:** The callout box ("Pro Shows, Pro Nights...") was stuck inside the left text column — needed to be centered as its own full-width row. Also needed several text/button changes and mobile sizing fixes.

| Version | What Happened |
|---|---|
| **mail19** | Pulled the callout box out of the left column and centered it as a full-width row (but was based on an older file accidentally) |
| **mail20** | Same callout box centering fix, correctly based on mail18 |
| **mail21** | **6 changes in one go:** (1) "Get Your Pass" → "Register Now" everywhere, (2) Removed the "IIIT Nagpur's Cultural Fest" h1, (3) Removed contact email/phone from certain sections, (4) "Register" → "Get Participation Pass" on pass cards, (5) Equal-size pass cards on mobile (`max-width: 280px; margin: 0 auto`), (6) Events grid — 2 columns on desktop, 1 column on mobile |

**Manual edits after mail21 (done outside AI):**
- Commented out primary CTA in final section
- Changed tagline to "Will you be in the crowd, or in the spotlight?"
- Changed phone number to 8602527698
- Updated the IMPORTANT warning text

---

### Phase 7 — Gmail Forwarding Fixes (mail22)

**What was needed:** When the email was forwarded within Gmail, the entire body collapsed under "..." (a known Gmail behavior with forwarded HTML emails).

| Version | What Happened |
|---|---|
| **mail22** | **4 Gmail-safe fixes:** (1) Updated preheader text format, (2) Added "View in browser" header row at the top, (3) Removed commented-out HTML blocks (Gmail can choke on large HTML comments), (4) Cleaned up leftover commented-out code |

**Manual edit after mail22:**
- Changed "student pass" → "IIITN pass" in the IMPORTANT warning section

---

### Phase 8 — Preheader Optimization (mail23)

**What was needed:** Better Gmail inbox preview text. The old preheader was generic — wanted something punchier that would show up well in the inbox list.

| Version | What Happened |
|---|---|
| **mail23** | Replaced preheader text with: *"25+ events, pro shows, and prizes — get ready for the biggest fest on campus."* Added invisible `&nbsp;&zwnj;` padding div to prevent Gmail from pulling random body text into the preview. Added `mso-hide:all; font-size:1px; line-height:1px;` for better Outlook compatibility. |

---

### Summary of What Was Needed at Each Stage

| Stage | Problem / Need | Solution |
|---|---|---|
| **Content** | Get email copy ready | Used ChatGPT to draft, refined manually in `Content.txt` |
| **Structure** | Email clients don't support modern CSS | Table-based layout, inline CSS, 600px container |
| **Images** | Can't use local images in email | Hosted on imgbb.com, used direct URLs |
| **Mobile** | Email broken on phones | `@media` queries, `.mobile-stack`, full-width buttons |
| **Dark mode** | Looked bad in dark theme clients | `color-scheme` meta + `prefers-color-scheme` overrides |
| **Characters** | Needed circus theme visuals | Positioned girl/magician/ringmaster alongside text columns |
| **Gmail** | Forwarded email collapsed under "..." | Select-all-copy-paste workaround + clean HTML structure |
| **Preview text** | Generic inbox preview | Custom preheader + invisible padding to block body text bleed |
| **Iteration** | Never perfect on first try | 23 versions, each reviewed and improved |

> **Key takeaway:** HTML email development is an iterative process. Expect to go through many versions. Test on real devices and email clients after each major change.

---

## 📚 Additional Resources

- [Final IIITN Students Mail.html](Final%20IIITN%20Students%20Mail.html) — The production-ready final email
- [Tips.md](Tips.md) — Practical tips for importing, sending, and creating HTML mails
- [Checklist.md](Checklist.md) — Pre-send QA checklist
- [Content.txt](Content.txt) — Finalized email copy
- [Desktop Wireframe.md](Desktop%20Wireframe.md) — Desktop layout plan
- [Mobile Wireframe.md](Mobile%20Wireframe.md) — Mobile layout plan
- [Email Iterations/](Email%20Iterations/) — All 23 iterative versions
