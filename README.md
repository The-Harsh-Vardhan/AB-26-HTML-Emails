# Abhivyakti 2026 — HTML Email Documentation

> IIIT Nagpur's Annual Cultural Fest | 19 – 21 March 2026

This repository contains all resources related to the promotional HTML emails for **Abhivyakti 2026**, including iterative email versions, design references, content drafts, wireframes, and a pre-send checklist.

---

## 📂 Repository Structure

```
Abhivyakti 2026/
├── README.md                    ← You are here
├── Desktop Wireframe.md         ← Desktop layout wireframe
├── Mobile Wireframe.md          ← Mobile layout wireframe
├── prompt1.txt                  ← Initial prompt / brief
├── HTML Email/
│   ├── Checklist.md             ← Pre-send QA checklist
│   ├── Content.txt              ← Finalized email copy (desktop + mobile)
│   ├── Tips.md                  ← Tips for importing, sending & creating HTML mails
│   ├── mail1.html → mail23.html ← Iterative HTML email versions
│   └── Reference Designs/
│       └── Event Posters/       ← Visual inspiration & poster assets
├── Feedback Images/             ← Screenshots / feedback from reviews
└── More Images/                 ← Additional image assets
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

## 🔁 Version History

The email went through **23 iterations** (mail1.html → mail23.html), progressively adding:

| Version Range | Key Changes |
|---|---|
| mail1 – mail2 | Initial structure and content layout |
| mail3 – mail8 | Real images, asset integration, visual polish |
| mail9 – mail12 | Mobile responsiveness fixes, dark mode support |
| mail13 – mail16 | Logo bars, circus characters, UX improvements |
| mail17 – mail18 | Asset refinements, banner updates |
| mail19 – mail20 | Callout box centering fix |
| mail21 | Button renames, content cleanup, mobile pass card sizing |
| mail22 | Gmail forwarding fixes (view-in-browser header, clean HTML) |
| mail23 | Optimized preheader text + invisible padding |

> **Tip:** Always iterate. Each version was reviewed, tested, and improved. The final result (mail23) is the cumulative output of all iterations.

---

## 📚 Additional Resources

- [Tips.md](HTML%20Email/Tips.md) — Practical tips for importing, sending, and creating HTML mails
- [Checklist.md](HTML%20Email/Checklist.md) — Pre-send QA checklist
- [Content.txt](HTML%20Email/Content.txt) — Finalized email copy
- [Desktop Wireframe.md](Desktop%20Wireframe.md) — Desktop layout plan
- [Mobile Wireframe.md](Mobile%20Wireframe.md) — Mobile layout plan
