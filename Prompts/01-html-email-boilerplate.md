# Prompt: HTML Email Boilerplate

> Use this prompt to generate a production-ready HTML email skeleton with maximum email client compatibility.

---

## Prompt

```
Create a complete HTML email boilerplate with the following requirements:

1. **DOCTYPE & HTML tag** — Use XHTML 1.0 Transitional doctype. Add `xmlns`, `xmlns:v`, and `xmlns:o` attributes for Outlook VML support.

2. **Head section must include:**
   - `<meta charset="UTF-8">`
   - `<meta name="viewport" content="width=device-width, initial-scale=1.0">`
   - `<meta http-equiv="X-UA-Compatible" content="IE=edge">`
   - `<meta name="x-apple-disable-message-reformatting">` (prevents Apple Mail auto-resizing)
   - `<meta name="color-scheme" content="light dark">`
   - `<meta name="supported-color-schemes" content="light dark">`
   - Outlook-specific conditional comment with `<o:OfficeDocumentSettings>`, `<o:AllowPNG/>`, and `<o:PixelsPerInch>96</o:PixelsPerInch>`

3. **Style block** — Include a `<style>` block with:
   - CSS reset (margin, padding, border-spacing reset for tables, image display block)
   - Responsive media query `@media only screen and (max-width: 620px)` with utility classes: `.container`, `.mobile-stack`, `.mobile-pad`, `.mobile-hide`, `.mobile-center`, `.mobile-btn`
   - Dark mode media query `@media (prefers-color-scheme: dark)` with placeholder overrides

4. **Body structure:**
   - `margin:0; padding:0;` on `<body>`
   - Preheader div (hidden preview text) + invisible `&nbsp;&zwnj;` padding div
   - Outer wrapper `<table>` (100% width, background color)
   - Inner container `<table>` (600px max-width, centered)
   - Placeholder rows for: header, hero, content, CTA, footer

5. **All layout tables** must have `role="presentation"`, `cellpadding="0"`, `cellspacing="0"`.

6. Use inline styles on all elements. The `<style>` block is only for responsive and dark mode overrides.

Output the complete HTML file ready to use.
```
