# Getting Started — Build Your First HTML Email

> A step-by-step walkthrough from blank file to a working HTML email with responsive layout.

---

## Prerequisites

- A **text editor** (VS Code, Sublime Text, or any code editor)
- A **web browser** (Chrome or Firefox — for previewing)
- An **image hosting account** ([imgbb.com](https://imgbb.com/) is free and works well)
- Basic knowledge of HTML and CSS

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
    /* We'll add responsive styles here later */
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
| `color-scheme` / `supported-color-schemes` | Enables dark mode support |
| `<!--[if mso]>` block | Outlook-specific settings (PNG support, DPI scaling) |

---

## Step 2: Outer Wrapper + Inner Container

Inside `<body>`, add the two-table structure that every HTML email uses:

```html
<body style="margin:0; padding:0; background-color:#F5F5F5;">

  <!-- OUTER WRAPPER: spans full width, provides background color -->
  <table role="presentation" width="100%" cellpadding="0" cellspacing="0"
         style="background-color:#F5F5F5;">
    <tr>
      <td align="center" style="padding:20px 10px;">

        <!-- INNER CONTAINER: fixed 600px width, centered -->
        <table role="presentation" width="600" cellpadding="0" cellspacing="0"
               style="max-width:600px; width:100%; background-color:#FFFFFF;">

          <!-- All your email sections go here as <tr> rows -->

        </table>

      </td>
    </tr>
  </table>

</body>
```

**Key rules:**
- `role="presentation"` — Tells screen readers these tables are for layout, not data
- `cellpadding="0"` and `cellspacing="0"` — Removes default table spacing
- `width="600"` attribute + `max-width:600px` and `width:100%` inline — The attribute is for Outlook (which ignores `max-width`), the inline styles are for everything else
- **600px** is the universal sweet spot — fits in all email client preview panes

---

## Step 3: Add a Header Row

Inside the inner container table, add your first section:

```html
<!-- HEADER -->
<tr>
  <td align="center" style="padding:30px 40px; background-color:#2563EB;">
    <h1 style="margin:0; font-family:Georgia, 'Times New Roman', serif;
               font-size:28px; font-weight:bold; color:#FFFFFF;">
      My Company
    </h1>
  </td>
</tr>
```

**Notice:** All styles are inline. This is mandatory because most email clients strip `<style>` blocks.

---

## Step 4: Add a Content Row

```html
<!-- CONTENT -->
<tr>
  <td style="padding:30px 40px; font-family:Arial, Helvetica, sans-serif;
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
      Every section is a <code>&lt;tr&gt;</code> row inside the
      main container table.
    </p>
  </td>
</tr>
```

---

## Step 5: Add a CTA Button

Don't use a styled `<a>` tag alone — it won't render correctly in Outlook. Use the **table-based "bulletproof button"** pattern:

```html
<!-- CTA BUTTON -->
<tr>
  <td align="center" style="padding:10px 40px 30px;">
    <table role="presentation" cellpadding="0" cellspacing="0"
           style="margin:0 auto;">
      <tr>
        <td align="center"
            style="background-color:#2563EB; border-radius:8px;">
          <a href="https://example.com"
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

---

## Step 6: Add a Footer

```html
<!-- FOOTER -->
<tr>
  <td align="center"
      style="padding:20px 40px; background-color:#1F2937;
             font-family:Arial, Helvetica, sans-serif;
             font-size:12px; line-height:1.6; color:#9CA3AF;">
    <p style="margin:0 0 8px;">
      © 2026 My Company. All rights reserved.
    </p>
    <p style="margin:0;">
      <a href="https://example.com/unsubscribe"
         style="color:#60A5FA; text-decoration:underline;">
        Unsubscribe
      </a>
    </p>
  </td>
</tr>
```

---

## Step 7: Add Responsive Styles

Go back to the `<style>` block in `<head>` and add mobile overrides:

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
  .mobile-hide {
    display: none !important;
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
```

Now add `class="container"` to your inner container table:

```html
<table role="presentation" class="container" width="600" ...>
```

And add `class="mobile-pad"` to content `<td>` elements to adjust padding on mobile.

**Important:** The `!important` flags are required to override inline styles from within a media query.

---

## Step 8: Add Preheader Text

Add this right after the opening `<body>` tag, **before** the outer wrapper table:

```html
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
```

The preheader is the short text that appears after the subject line in the inbox listing. Without it, email clients pull random text from your email body — which usually looks bad.

The second `<div>` with `&nbsp;&zwnj;` (non-breaking space + zero-width non-joiner) acts as invisible padding to prevent Gmail from pulling body content.

---

## Your Complete First Email

Combining all the steps above, you now have a working HTML email with:

- ✅ Full meta tag support (Outlook, Apple Mail, dark mode)
- ✅ Centered 600px container
- ✅ Header, content, button, and footer sections
- ✅ Responsive mobile layout
- ✅ Preheader text
- ✅ Accessible markup (`role="presentation"`, semantic headings)

Open `my-email.html` in a browser to preview it. Resize the window below 620px to see the mobile layout.

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
