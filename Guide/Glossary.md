# Glossary

> Key HTML email development terms defined.

---

### Bulletproof Button
A CTA button built with a `<table>` → `<tr>` → `<td>` → `<a>` structure instead of a styled `<a>` tag alone. Called "bulletproof" because it renders correctly in all email clients, including Outlook (which ignores `padding` and `background` on `<a>` tags).

### CAN-SPAM
Short for **Controlling the Assault of Non-Solicited Pornography And Marketing Act** — a US law requiring commercial emails to include a physical mailing address and a working unsubscribe link. Similar laws exist globally (GDPR in the EU, CASL in Canada).

### Clipping (Gmail)
Gmail hides ("clips") the content of emails where the HTML source exceeds approximately **102KB**. A "[Message clipped] View entire message" link appears at the bottom. Most recipients never click it.

### Conditional Comments (MSO)
HTML comments in the format `<!--[if mso]>...<![endif]-->` that only Microsoft Outlook reads. Used to add Outlook-specific fixes like VML background images, table widths, and DPI settings.

### Dark Mode
A display setting that uses dark backgrounds with light text. Email clients that support it (Apple Mail, Outlook.com, Gmail Android) can auto-invert colors or respect `@media (prefers-color-scheme: dark)` CSS overrides.

### Email Clipping
See "Clipping (Gmail)."

### Email Service Provider (ESP)
A platform for sending bulk emails. Examples: Mailchimp, SendGrid, Amazon SES, Brevo, ConvertKit. ESPs handle delivery, tracking, unsubscribe management, and list segmentation.

### Image Blocking
Many email clients (especially corporate Outlook setups) hide images by default until the recipient clicks "Show images." This is why `alt` text on every `<img>` tag is critical — it's the fallback content when images are blocked.

### Inline CSS
CSS written directly on HTML elements using the `style=""` attribute, as opposed to CSS in a `<style>` block or external stylesheet. Most email clients only reliably support inline CSS.

### `@media` Query
A CSS rule that applies styles conditionally based on screen size, color scheme, or other device features. In email, used primarily for responsive design (`@media (max-width: 620px)`) and dark mode (`@media (prefers-color-scheme: dark)`).

### Max-Width
A CSS property (`max-width`) that limits how wide an element can grow. Supported in most email clients except **Outlook for Windows**, which ignores it. Always pair with a `width` HTML attribute on tables as a fallback.

### Mobile Stacking
The technique of making side-by-side columns (created with `<td>` cells) stack vertically on mobile by setting `display: block !important; width: 100% !important;` via a media query. Essential for readability on small screens.

### MSO
Abbreviation for **Microsoft Office**. Used in CSS properties and conditional comments specific to Outlook. Examples: `mso-hide:all`, `mso-line-height-rule:exactly`, `mso-table-lspace`, `<!--[if mso]>`.

### Preheader
The short preview text that appears after the subject line in the inbox listing. Implemented as a hidden `<div>` at the top of the email body with `display:none`. Important for open rates — it's the second thing recipients read (after the subject).

### `role="presentation"`
An HTML attribute added to `<table>` elements used for layout (not data). It tells screen readers to ignore the table structure and read the content as regular text. Required for accessibility.

### VML (Vector Markup Language)
A Microsoft-specific markup language supported only in Outlook for Windows. Used as a workaround for features Outlook doesn't support in CSS, like background images with text overlay. Written inside `<!--[if mso]>` conditional comments.

### Web-Safe Fonts
Fonts that are pre-installed on virtually all operating systems and reliably available in email clients. The main ones:
- **Sans-serif:** Arial, Helvetica, Verdana, Trebuchet MS, Tahoma
- **Serif:** Georgia, Times New Roman, Palatino Linotype
- **Monospace:** Courier New, Courier

### Zero-Width Non-Joiner (`&zwnj;`)
An invisible Unicode character used in preheader padding (`&nbsp;&zwnj;`) to prevent email clients from pulling visible body text into the inbox preview. The alternating pattern of non-breaking spaces and zero-width non-joiners creates invisible content that "fills" the preview area.

---

## Navigation

← [Testing Your Email](05-Testing-Your-Email.md) · [Back to Guide](../README.md)
