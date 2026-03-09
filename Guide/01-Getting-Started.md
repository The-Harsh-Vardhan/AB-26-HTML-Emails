# Getting Started — Build Your First HTML Email

> A step-by-step walkthrough from blank file to a working HTML email with responsive layout.

---

## What You'll Build

By the end of this guide, you'll have a complete, responsive HTML email that looks like this:

```
┌──────────────────────────────────────┐
│           ░░░░░░░░░░░░░░░            │  ← Background (#F5F5F5)
│  ┌──────────────────────────────┐    │
│  │     ████  HEADER  ████      │    │  ← Blue bar (#2563EB)
│  │         My Company          │    │
│  ├──────────────────────────────┤    │
│  │                              │    │
│  │  🖼️  Hero Image              │    │  ← Full-width image
│  │                              │    │
│  ├──────────────────────────────┤    │
│  │                              │    │
│  │  Welcome to Our Newsletter   │    │  ← Content section
│  │  This is your first HTML...  │    │
│  │                              │    │
│  │      [ Get Started ]         │    │  ← CTA button
│  │                              │    │
│  ├──────────────────────────────┤    │
│  │  © 2026 · Unsubscribe       │    │  ← Dark footer
│  └──────────────────────────────┘    │
│                                      │
└──────────────────────────────────────┘
```

It includes: meta tags for every major client, preheader text, a responsive image, a bulletproof CTA button, mobile-first responsive styles, and accessible markup.

---

## Prerequisites

- A **text editor** (VS Code, Sublime Text, or any code editor)
- A **web browser** (Chrome or Firefox — for previewing)
- An **image hosting account** ([imgbb.com](https://imgbb.com/) is free and works well)
- Basic knowledge of HTML and CSS
- **Optional:** A free [Litmus Putsmail](https://putsmail.com/) or [Mail Tester](https://www.mail-tester.com/) account for sending test emails

---

## Why HTML Emails Are Different

HTML emails are **not web pages**. Here's what you're dealing with:

| Web Pages | HTML Emails |
|-----------|-------------|
| Use any modern CSS (flexbox, grid, animations) | Stuck with `<table>` layouts and inline CSS |
| Link external stylesheets | Most clients strip `<link>` and `<style>` blocks |
| JavaScript for interactivity | No JavaScript at all |
| Images from local files work | Images must be hosted online (public URLs) |
| One rendering engine (browser) | Dozens of rendering engines (Gmail, Outlook, Apple Mail, Yahoo, etc.) |
| Consistent behavior | Every client has its own quirks |

**The core rule:** If it works in Outlook (which uses Microsoft Word's rendering engine from 2007), it'll probably work everywhere.

---

## Step 1: HTML Skeleton + Meta Tags

Create a new file called `my-email.html` and add this foundation:

```html
<!DOCTYPE html>
<html lang="en" dir="ltr" xmlns="http://www.w3.org/1999/xhtml"
      xmlns:v="urn:schemas-microsoft-com:vml"
      xmlns:o="urn:schemas-microsoft-com:office:office">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="x-apple-disable-message-reformatting">
  <meta name="color-scheme" content="light dark">
  <meta name="supported-color-schemes" content="light dark">
  <title>My First Email</title>

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
    /* We'll add responsive styles in Step 9 */
  </style>
</head>
<body style="margin:0; padding:0; background-color:#F5F5F5;">
  <!-- Email content goes here -->
</body>
</html>
```

**What each meta tag does:**

| Tag | Purpose |
|-----|---------|
| `charset="UTF-8"` | Ensures special characters render correctly |
| `viewport` | Enables responsive scaling on mobile |
| `X-UA-Compatible` | Forces IE to use the latest rendering mode |
| `x-apple-disable-message-reformatting` | Stops Apple Mail from auto-resizing your text |
| `color-scheme` / `supported-color-schemes` | Enables dark mode support (see Step 9) |
| `dir="ltr"` | Specifies text direction for accessibility |
| `<!--[if mso]>` block | Outlook-specific settings (PNG support, DPI scaling) |

---

## Step 2: Add Preheader Text

The preheader is the short text that appears **after the subject line** in the inbox listing. Without it, email clients pull random text from your email body — which usually looks bad.

Add this right after the opening `<body>` tag, **before** anything else:

```html
<body style="margin:0; padding:0; background-color:#F5F5F5;">

  <!-- Preheader: preview text shown in inbox after subject line -->
  <div style="display:none; max-height:0px; overflow:hidden; opacity:0;
              mso-hide:all; font-size:1px; line-height:1px;">
    Check out what's new this month — updates, features, and more.
  </div>
  <!-- Invisible padding to stop Gmail from pulling body text into preview -->
  <div style="display:none; max-height:0px; overflow:hidden; opacity:0;
              mso-hide:all; font-size:1px; line-height:1px;">
    &nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;
  </div>

  <!-- Rest of the email goes below -->
</body>
```

The second `<div>` with `&nbsp;&zwnj;` (non-breaking space + zero-width non-joiner) acts as invisible padding to prevent Gmail from pulling body content into the preview.

---

## Step 3: Outer Wrapper + Inner Container

After the preheader divs, add the two-table structure that every HTML email uses:

```html
<!-- OUTER WRAPPER: spans full width, provides background color -->
<table role="presentation" width="100%" cellpadding="0" cellspacing="0"
       style="background-color:#F5F5F5;">
  <tr>
    <td align="center" style="padding:20px 10px;">

      <!-- INNER CONTAINER: fixed 600px width, centered -->
      <table class="container" role="presentation" width="600"
             cellpadding="0" cellspacing="0"
             style="max-width:600px; width:100%; background-color:#FFFFFF;">

        <!-- All your email sections go here as <tr> rows -->

      </table>
      <!-- /INNER CONTAINER -->

    </td>
  </tr>
</table>
<!-- /OUTER WRAPPER -->
```

**Key rules:**
- `role="presentation"` — Tells screen readers these tables are for layout, not data
- `cellpadding="0"` and `cellspacing="0"` — Removes default table spacing
- `class="container"` — We'll use this for responsive styles later (Step 9)
- `width="600"` attribute + `max-width:600px` and `width:100%` inline — The attribute is for Outlook (which ignores `max-width`), the inline styles are for everything else
- **600px** is the universal sweet spot — fits in all email client preview panes

---

## Step 4: Add a Header Row

Inside the inner container table, add your first section:

```html
<!-- HEADER -->
<tr>
  <td class="mobile-pad" align="center"
      style="padding:30px 40px; background-color:#2563EB;">
    <h1 style="margin:0; font-family:Georgia, 'Times New Roman', serif;
               font-size:28px; font-weight:bold; color:#FFFFFF;">
      My Company
    </h1>
  </td>
</tr>
```

**Notice:** All styles are inline. This is mandatory because most email clients strip `<style>` blocks. The `class="mobile-pad"` will reduce side padding on small screens (configured in Step 9).

---

## Step 5: Add a Hero Image

A hero image makes your email visually engaging. Images in email **must be hosted online** — local file paths won't work.

```html
<!-- HERO IMAGE -->
<tr>
  <td style="padding:0; line-height:0; font-size:0;">
    <img src="https://your-hosted-image-url.com/hero.jpg"
         alt="Describe the image for screen readers and when images are blocked"
         width="600"
         style="width:100%; max-width:600px; height:auto; display:block;"
    />
  </td>
</tr>
```

**Key image rules:**
- `display:block` — Removes the phantom gap below images caused by inline rendering
- `width="600"` attribute + `width:100%; max-width:600px; height:auto;` inline — The attribute sets the size for Outlook, the CSS makes it responsive everywhere else
- `height:auto` — Maintains aspect ratio when the image scales down on mobile
- Always include a meaningful `alt` text — many users have images blocked by default, and screen readers rely on it
- `line-height:0; font-size:0;` on the `<td>` — Prevents extra spacing around the image in some clients

> **Tip:** Upload images to [imgbb.com](https://imgbb.com/) and use the "Direct link" URL. Keep image file sizes under 200KB when possible — large images slow down loading and contribute to Gmail's 102KB clipping limit.

---

## Step 6: Add a Content Row

```html
<!-- CONTENT -->
<tr>
  <td class="mobile-pad" style="padding:30px 40px;
             font-family:Arial, Helvetica, sans-serif;
             font-size:16px; line-height:1.6; color:#1F2937;">
    <h2 style="margin:0 0 16px; font-family:Georgia, 'Times New Roman', serif;
               font-size:22px; color:#1F2937;">
      Welcome to Our Newsletter
    </h2>
    <p style="margin:0 0 16px;">
      This is your first HTML email. It uses table-based layouts
      and inline CSS to ensure it renders correctly across all
      email clients — from Gmail to Outlook to Apple Mail.
    </p>
    <p style="margin:0;">
      Every section is a &lt;tr&gt; row inside the
      main container table.
    </p>
  </td>
</tr>
```

> **A note on fonts:** We use `Georgia` (serif) for headings and `Arial` (sans-serif) for body text. These are **web-safe fonts** — they're pre-installed on virtually every device. Web fonts (like Google Fonts) only work in Apple Mail, iOS Mail, and a few Android clients. Gmail, Outlook, and Yahoo ignore them completely. Stick with web-safe stacks unless you're okay with fallback rendering.

---

## Step 7: Add a CTA Button

Don't use a styled `<a>` tag alone — it won't render correctly in Outlook. Use the **table-based "bulletproof button"** pattern:

```html
<!-- CTA BUTTON -->
<tr>
  <td class="mobile-pad" align="center" style="padding:10px 40px 30px;">
    <table class="mobile-btn" role="presentation" cellpadding="0"
           cellspacing="0" style="margin:0 auto;">
      <tr>
        <td align="center"
            style="background-color:#2563EB; border-radius:8px;">
          <a href="https://yoursite.com/cta"
             target="_blank"
             style="display:inline-block; padding:16px 36px;
                    font-family:Arial, Helvetica, sans-serif;
                    font-size:16px; font-weight:bold;
                    color:#FFFFFF; text-decoration:none;">
            Get Started
          </a>
        </td>
      </tr>
    </table>
  </td>
</tr>
```

**Why this works:** The `<td>` provides the background color and border-radius. The `<a>` provides the padding and text styling. Outlook renders the `<td>` background even though it ignores padding on `<a>` tags.

The `class="mobile-btn"` makes the button stretch to full width on mobile (Step 9).

> **Outlook edge case:** Outlook ignores `border-radius` and won't apply padding from the `<a>` tag. For pixel-perfect Outlook buttons with rounded corners, use the VML (Vector Markup Language) approach with `<v:roundrect>`. The tool at [buttons.cm](https://buttons.cm) generates these automatically. For most use cases, the pattern above is good enough — the button will render as a rectangle with the correct background color in Outlook.

> **Note:** If your email is sent through an ESP (Email Service Provider) like Mailchimp or SendGrid, the `href` URL will be automatically rewritten with a tracking redirect. Use a clean placeholder URL during development.

---

## Step 8: Add a Footer

```html
<!-- FOOTER -->
<tr>
  <td class="mobile-pad" align="center"
      style="padding:20px 40px; background-color:#1F2937;
             font-family:Arial, Helvetica, sans-serif;
             font-size:12px; line-height:1.6; color:#9CA3AF;">
    <p style="margin:0 0 8px;">
      © 2026 My Company. All rights reserved.
    </p>
    <p style="margin:0;">
      <a href="https://yoursite.com/unsubscribe"
         style="color:#60A5FA; text-decoration:underline;">
        Unsubscribe
      </a>
    </p>
  </td>
</tr>
```

---

## Step 9: Add Responsive + Dark Mode Styles

Go back to the `<style>` block in `<head>` and replace the placeholder comment with these styles:

```css
/* Reset */
body, table, td, a { -webkit-text-size-adjust: 100%; -ms-text-size-adjust: 100%; }
table, td { mso-table-lspace: 0pt; mso-table-rspace: 0pt; }
img { -ms-interpolation-mode: bicubic; border: 0; outline: none; text-decoration: none; }

/* Responsive */
@media only screen and (max-width: 620px) {
  .container {
    width: 100% !important;
    max-width: 100% !important;
  }
  .mobile-pad {
    padding-left: 20px !important;
    padding-right: 20px !important;
  }
  .mobile-stack {
    display: block !important;
    width: 100% !important;
  }
  .mobile-center {
    text-align: center !important;
  }
  .mobile-btn {
    width: 100% !important;
  }
  .mobile-btn a {
    display: block !important;
    width: 100% !important;
    padding: 16px 0 !important;
    text-align: center !important;
  }
}

/* Dark Mode */
@media (prefers-color-scheme: dark) {
  body, .body-bg { background-color: #1A1A2E !important; }
  .container { background-color: #16213E !important; }
  .dark-text { color: #E0E0E0 !important; }
  .dark-link { color: #93C5FD !important; }
}
```

**Where each class is used:**

| Class | Applied to | Purpose |
|-------|-----------|--------|
| `.container` | Inner container `<table>` (Step 3) | Scales to full width on mobile |
| `.mobile-pad` | Content `<td>` elements (Steps 4, 6, 7, 8) | Reduces side padding from 40px to 20px |
| `.mobile-stack` | Side-by-side `<td>` cells (used in multi-column layouts) | Stacks columns vertically |
| `.mobile-center` | Any element needing centered text on mobile | Centers text alignment |
| `.mobile-btn` | CTA button wrapper `<table>` (Step 7) | Stretches button to full width |

> **Dark mode:** The `color-scheme` meta tags you added in Step 1 tell email clients that your email supports dark mode. The `@media (prefers-color-scheme: dark)` query applies overrides when the user's device is in dark mode. Apple Mail and Outlook (macOS/iOS) respect this well. Gmail auto-inverts colors regardless, so the dark mode CSS mainly helps clients that support it natively.

**Important:** The `!important` flags are required to override inline styles from within a media query.

---

## Your Complete First Email

Combining all the steps above, here's the full assembled email. Copy this to compare against your work, or use it as a starting point:

<details>
<summary><strong>Click to expand the complete HTML</strong></summary>

```html
<!DOCTYPE html>
<html lang="en" dir="ltr" xmlns="http://www.w3.org/1999/xhtml"
      xmlns:v="urn:schemas-microsoft-com:vml"
      xmlns:o="urn:schemas-microsoft-com:office:office">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="x-apple-disable-message-reformatting">
  <meta name="color-scheme" content="light dark">
  <meta name="supported-color-schemes" content="light dark">
  <title>My First Email</title>

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
    /* Reset */
    body, table, td, a { -webkit-text-size-adjust: 100%; -ms-text-size-adjust: 100%; }
    table, td { mso-table-lspace: 0pt; mso-table-rspace: 0pt; }
    img { -ms-interpolation-mode: bicubic; border: 0; outline: none; text-decoration: none; }

    /* Responsive */
    @media only screen and (max-width: 620px) {
      .container {
        width: 100% !important;
        max-width: 100% !important;
      }
      .mobile-pad {
        padding-left: 20px !important;
        padding-right: 20px !important;
      }
      .mobile-stack {
        display: block !important;
        width: 100% !important;
      }
      .mobile-center {
        text-align: center !important;
      }
      .mobile-btn {
        width: 100% !important;
      }
      .mobile-btn a {
        display: block !important;
        width: 100% !important;
        padding: 16px 0 !important;
        text-align: center !important;
      }
    }

    /* Dark Mode */
    @media (prefers-color-scheme: dark) {
      body, .body-bg { background-color: #1A1A2E !important; }
      .container { background-color: #16213E !important; }
      .dark-text { color: #E0E0E0 !important; }
      .dark-link { color: #93C5FD !important; }
    }
  </style>
</head>
<body style="margin:0; padding:0; background-color:#F5F5F5;">

  <!-- Preheader: preview text shown in inbox after subject line -->
  <div style="display:none; max-height:0px; overflow:hidden; opacity:0;
              mso-hide:all; font-size:1px; line-height:1px;">
    Check out what's new this month — updates, features, and more.
  </div>
  <div style="display:none; max-height:0px; overflow:hidden; opacity:0;
              mso-hide:all; font-size:1px; line-height:1px;">
    &nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;
  </div>

  <!-- OUTER WRAPPER -->
  <table role="presentation" width="100%" cellpadding="0" cellspacing="0"
         style="background-color:#F5F5F5;">
    <tr>
      <td align="center" style="padding:20px 10px;">

        <!-- INNER CONTAINER -->
        <table class="container" role="presentation" width="600"
               cellpadding="0" cellspacing="0"
               style="max-width:600px; width:100%; background-color:#FFFFFF;">

          <!-- HEADER -->
          <tr>
            <td class="mobile-pad" align="center"
                style="padding:30px 40px; background-color:#2563EB;">
              <h1 style="margin:0; font-family:Georgia, 'Times New Roman', serif;
                         font-size:28px; font-weight:bold; color:#FFFFFF;">
                My Company
              </h1>
            </td>
          </tr>

          <!-- HERO IMAGE -->
          <tr>
            <td style="padding:0; line-height:0; font-size:0;">
              <img src="https://your-hosted-image-url.com/hero.jpg"
                   alt="Describe the image for screen readers"
                   width="600"
                   style="width:100%; max-width:600px; height:auto; display:block;"
              />
            </td>
          </tr>

          <!-- CONTENT -->
          <tr>
            <td class="mobile-pad" style="padding:30px 40px;
                       font-family:Arial, Helvetica, sans-serif;
                       font-size:16px; line-height:1.6; color:#1F2937;">
              <h2 style="margin:0 0 16px; font-family:Georgia, 'Times New Roman', serif;
                         font-size:22px; color:#1F2937;">
                Welcome to Our Newsletter
              </h2>
              <p style="margin:0 0 16px;">
                This is your first HTML email. It uses table-based layouts
                and inline CSS to ensure it renders correctly across all
                email clients — from Gmail to Outlook to Apple Mail.
              </p>
              <p style="margin:0;">
                Every section is a &lt;tr&gt; row inside the main container table.
              </p>
            </td>
          </tr>

          <!-- CTA BUTTON -->
          <tr>
            <td class="mobile-pad" align="center" style="padding:10px 40px 30px;">
              <table class="mobile-btn" role="presentation" cellpadding="0"
                     cellspacing="0" style="margin:0 auto;">
                <tr>
                  <td align="center"
                      style="background-color:#2563EB; border-radius:8px;">
                    <a href="https://yoursite.com/cta"
                       target="_blank"
                       style="display:inline-block; padding:16px 36px;
                              font-family:Arial, Helvetica, sans-serif;
                              font-size:16px; font-weight:bold;
                              color:#FFFFFF; text-decoration:none;">
                      Get Started
                    </a>
                  </td>
                </tr>
              </table>
            </td>
          </tr>

          <!-- FOOTER -->
          <tr>
            <td class="mobile-pad" align="center"
                style="padding:20px 40px; background-color:#1F2937;
                       font-family:Arial, Helvetica, sans-serif;
                       font-size:12px; line-height:1.6; color:#9CA3AF;">
              <p style="margin:0 0 8px;">
                © 2026 My Company. All rights reserved.
              </p>
              <p style="margin:0;">
                <a href="https://yoursite.com/unsubscribe"
                   style="color:#60A5FA; text-decoration:underline;">
                  Unsubscribe
                </a>
              </p>
            </td>
          </tr>

        </table>
        <!-- /INNER CONTAINER -->

      </td>
    </tr>
  </table>
  <!-- /OUTER WRAPPER -->

</body>
</html>
```

</details>

Open `my-email.html` in a browser to preview it. Resize the window below 620px to see the mobile layout.

---

## Common Gotchas

Before you move on, be aware of these frequent pitfalls:

| Gotcha | Details |
|--------|---------|
| **Gmail clips emails over 102KB** | Gmail truncates the HTML and adds a "View entire message" link. Keep your HTML lean — minimize whitespace in production, compress images, and avoid embedding base64 images. |
| **Outlook ignores `max-width`** | Always pair `max-width` in CSS with a `width` HTML attribute as a fallback (as we did in Step 3). |
| **`margin` on `<td>` is unreliable** | Some clients ignore `margin` on table cells. Use `padding` on `<td>` elements instead. |
| **Images blocked by default** | Many corporate Outlook installations block images until the user clicks "Download pictures." Always include descriptive `alt` text and don't put critical info only in images. |
| **`<style>` blocks get stripped** | Gmail (non-Google Workspace), older Yahoo, and some other clients strip `<style>` entirely. Your email must look acceptable with only inline styles — treat `<style>` as a progressive enhancement. |
| **`background-image` in Outlook** | Outlook doesn't support CSS `background-image`. Use VML `<v:image>` for Outlook background images, or design so the background color alone looks fine. |

---

## What's Next

| Topic | Page |
|-------|------|
| What CSS/HTML works in which email client? | [02-Email-Client-Support.md](02-Email-Client-Support.md) |
| Common mistakes that break emails | [03-Common-Mistakes.md](03-Common-Mistakes.md) |
| Build a reusable design system | [04-Design-System.md](04-Design-System.md) |
| Test your email before sending | [05-Testing-Your-Email.md](05-Testing-Your-Email.md) |
| Grab a ready-to-use template | [../Templates/](../Templates/) |
| Use AI to generate components | [../Prompts/](../Prompts/) |
