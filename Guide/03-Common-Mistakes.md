# Common Mistakes in HTML Emails

> 20 pitfalls that break emails — and how to fix them. Organized by category.

---

## Layout

### 1. Using `<div>` layouts instead of `<table>`

❌ **Mistake:**
```html
<div style="display:flex; gap:20px;">
  <div style="flex:1;">Column 1</div>
  <div style="flex:1;">Column 2</div>
</div>
```

✅ **Fix:**
```html
<table role="presentation" width="100%" cellpadding="0" cellspacing="0">
  <tr>
    <td width="50%" valign="top" style="padding-right:10px;">Column 1</td>
    <td width="50%" valign="top" style="padding-left:10px;">Column 2</td>
  </tr>
</table>
```

**Why:** Flexbox and grid are unsupported in Gmail, Outlook, and Yahoo. Tables are the only reliable multi-column layout method.

---

### 2. Using `margin` for spacing

❌ **Mistake:**
```html
<p style="margin:20px;">Some text</p>
```

✅ **Fix:**
```html
<td style="padding:20px;">
  <p style="margin:0;">Some text</p>
</td>
```

**Why:** `margin` behaves inconsistently across email clients (especially Outlook). Use `padding` on `<td>` elements instead.

---

### 3. Not setting `cellpadding="0"` and `cellspacing="0"`

❌ **Mistake:**
```html
<table>
  <tr><td>Content</td></tr>
</table>
```

✅ **Fix:**
```html
<table role="presentation" cellpadding="0" cellspacing="0" style="border-collapse:collapse;">
  <tr><td>Content</td></tr>
</table>
```

**Why:** Default table spacing varies by email client. Always zero it out and control spacing explicitly.

---

### 4. Relying on `max-width` without a `width` attribute

❌ **Mistake:**
```html
<table style="max-width:600px; width:100%;">
```

✅ **Fix:**
```html
<table width="600" style="max-width:600px; width:100%;">
```

**Why:** Outlook ignores `max-width` entirely. Without the `width` attribute, your email will stretch to 100% width in Outlook.

---

## Images

### 5. Using local or relative image paths

❌ **Mistake:**
```html
<img src="./images/banner.png">
<img src="C:/Desktop/banner.png">
```

✅ **Fix:**
```html
<img src="https://i.ibb.co/XXXXX/banner.png">
```

**Why:** Email clients cannot access local files or relative paths. All images must be hosted on a public URL.

---

### 6. Missing `display:block` on images

❌ **Mistake:**
```html
<img src="https://example.com/banner.png" width="600">
```

✅ **Fix:**
```html
<img src="https://example.com/banner.png" width="600"
     style="display:block; width:600px; height:auto; border:0;"
     alt="Banner description">
```

**Why:** Without `display:block`, email clients add a small gap (3-5px) below images. This is because `<img>` is inline by default, and the gap is the descender space for text.

---

### 7. Images over 300KB

❌ **Mistake:** Using a 2MB hero image.

✅ **Fix:** Compress images to under 300KB. Use tools like [TinyPNG](https://tinypng.com/) or [Squoosh](https://squoosh.app/).

**Why:** Large images slow down email loading, especially on mobile. Some clients may not load them at all.

---

### 8. Missing `alt` text

❌ **Mistake:**
```html
<img src="https://example.com/logo.png">
```

✅ **Fix:**
```html
<img src="https://example.com/logo.png" alt="Company Logo">
```

For decorative images:
```html
<img src="https://example.com/divider.png" alt="">
```

**Why:** Many email clients block images by default. Without `alt` text, recipients see nothing — breaking the email's readability.

---

## Typography

### 9. Using web fonts or custom fonts

❌ **Mistake:**
```css
font-family: 'Poppins', sans-serif;
```

✅ **Fix:**
```css
font-family: Arial, Helvetica, sans-serif;
```

**Why:** Only Apple Mail and Outlook for Mac support `@font-face`. Every other client falls back to system fonts. Use web-safe stacks: `Arial/Helvetica/sans-serif` or `Georgia/'Times New Roman'/serif`.

---

### 10. Text too small on mobile

❌ **Mistake:** Using 12px body text and 18px headings — unreadable on phones.

✅ **Fix:** Minimum 14px body text on mobile. Use `@media` queries to scale up:
```css
@media (max-width: 620px) {
  .mobile-text { font-size: 16px !important; line-height: 1.5 !important; }
}
```

**Why:** Small text forces users to pinch-zoom, which is a bad experience. iOS may auto-resize text, breaking your layout.

---

## Buttons & Links

### 11. Styling `<a>` tags as buttons without a `<table>` wrapper

❌ **Mistake:**
```html
<a href="#" style="background:#2563EB; padding:16px 36px; color:white; border-radius:8px; display:inline-block;">
  Click Me
</a>
```

✅ **Fix:**
```html
<table role="presentation" cellpadding="0" cellspacing="0">
  <tr>
    <td style="background-color:#2563EB; border-radius:8px;">
      <a href="#" target="_blank"
         style="display:inline-block; padding:16px 36px; color:#FFFFFF;
                font-family:Arial,sans-serif; font-weight:bold; text-decoration:none;">
        Click Me
      </a>
    </td>
  </tr>
</table>
```

**Why:** Outlook ignores `padding` and `background` on `<a>` tags. The table-td-a pattern ensures the button renders correctly everywhere.

---

### 12. Missing `target="_blank"` on links

❌ **Mistake:**
```html
<a href="https://example.com">Visit site</a>
```

✅ **Fix:**
```html
<a href="https://example.com" target="_blank">Visit site</a>
```

**Why:** Without `target="_blank"`, clicking a link in some webmail clients navigates away from the inbox within the same tab.

---

## Responsive

### 13. No `@media` queries for mobile

❌ **Mistake:** Designing only for 600px desktop width with no mobile overrides.

✅ **Fix:** Add a `@media (max-width: 620px)` block with stacking, padding, and font-size adjustments. See [Getting Started, Step 7](01-Getting-Started.md#step-7-add-responsive-styles).

**Why:** Over 60% of emails are read on mobile. A desktop-only email will have tiny text and horizontal scrolling on phones.

---

### 14. Forgetting `!important` in media queries

❌ **Mistake:**
```css
@media (max-width: 620px) {
  .container { width: 100%; }
}
```

✅ **Fix:**
```css
@media (max-width: 620px) {
  .container { width: 100% !important; max-width: 100% !important; }
}
```

**Why:** Inline styles have higher specificity than `<style>` block rules. Without `!important`, your media query overrides won't take effect.

---

### 15. Not stacking columns on mobile

❌ **Mistake:** Two-column layout that stays side-by-side on a 375px phone screen.

✅ **Fix:** Add `class="mobile-stack"` to column `<td>` elements:
```css
@media (max-width: 620px) {
  .mobile-stack { display: block !important; width: 100% !important; }
}
```

**Why:** Two columns at 300px each are too narrow to read comfortably on a phone. Stack them vertically.

---

## Dark Mode

### 16. Not testing dark mode at all

❌ **Mistake:** Designing a dark-themed email without considering that dark mode inverts colors — turning dark backgrounds darker and light text lighter... or not.

✅ **Fix:** Add `color-scheme` meta tags and `@media (prefers-color-scheme: dark)` overrides:
```css
@media (prefers-color-scheme: dark) {
  .body-bg { background-color: #1a1a1a !important; }
  .text-light { color: #E5E5E5 !important; }
}
```

**Why:** Apple Mail, Outlook.com, and Gmail (Android) support dark mode CSS. Without overrides, the client may auto-invert your colors with poor results.

---

### 17. Transparent PNG images on dark backgrounds

❌ **Mistake:** A logo with a transparent background that becomes invisible when dark mode changes the background.

✅ **Fix:** Add a subtle background color or border to images that may blend in:
```html
<img src="logo.png" alt="Logo"
     style="background-color:#FFFFFF; padding:4px; border-radius:4px;">
```

Or use a version of the logo designed for dark backgrounds.

---

## Deliverability & Size

### 18. HTML file over 102KB (Gmail clipping)

❌ **Mistake:** A large HTML email with lots of inline styles, comments, and redundant code.

✅ **Fix:**
- Remove HTML comments (especially large commented-out blocks)
- Remove redundant/duplicate inline styles
- Minimize code — avoid excessive nesting
- Check file size: keep under **80KB** for safety (102KB is Gmail's hard clip limit)

**Why:** When Gmail clips an email, it shows a "[Message clipped] View entire message" link. Most recipients never click it — your CTA is lost.

---

### 19. No preheader text

❌ **Mistake:** Jumping straight into the email body without a hidden preheader.

✅ **Fix:**
```html
<div style="display:none; max-height:0; overflow:hidden; opacity:0;
            mso-hide:all; font-size:1px; line-height:1px;">
  Your preview text here — make it compelling.
</div>
<div style="display:none; max-height:0; overflow:hidden; opacity:0;
            mso-hide:all; font-size:1px; line-height:1px;">
  &nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;
</div>
```

**Why:** Without a preheader, email clients pull the first visible text from your body — which is often "View in browser" or a table cell. The preheader lets you control the inbox preview.

---

### 20. Putting critical styles only in the `<style>` block

❌ **Mistake:**
```html
<style>
  .hero { background-color: #2563EB; padding: 40px; color: white; }
</style>
...
<td class="hero">Welcome</td>
```

✅ **Fix:**
```html
<td class="hero" style="background-color:#2563EB; padding:40px; color:#FFFFFF;">
  Welcome
</td>
```

**Why:** Gmail mobile strips the `<style>` block entirely. If your layout depends on styles defined only there, it breaks on mobile Gmail — one of the largest email clients in the world.

---

## Quick Reference: The Safe Set

If you stick to these, your email will work everywhere:

```
Structure:   <table>, <tr>, <td>, <th>
Styling:     inline style="" on every element
Spacing:     padding on <td> (not margin)
Images:      <img> with display:block, width attr, alt text, hosted URLs
Buttons:     table > tr > td > a pattern
Fonts:       Arial, Helvetica, Georgia, Times New Roman, Courier
Colors:      hex (#FFFFFF), rgb()
Layout:      width attribute on tables, align="center"
Hide:        mso-hide:all (Outlook), display:none (others)
```

---

## Navigation

← [Email Client Support](02-Email-Client-Support.md) · [Design System](04-Design-System.md) →
