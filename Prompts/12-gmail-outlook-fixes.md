# Prompt: Fix Gmail & Outlook Specific Issues in HTML Email

> Use this prompt to apply targeted fixes for the two most problematic email clients.

---

## Prompt

```
Review this HTML email and apply all necessary fixes for Gmail and Outlook compatibility.

---

## Gmail Fixes:

1. **Style stripping:** Gmail mobile strips `<style>` blocks entirely. Ensure ALL critical styles are inline on elements. The `<style>` block should only contain `@media` queries (responsive + dark mode).

2. **Class prefix:** Gmail may strip classes. If styling depends on classes outside of `@media` queries, move those styles inline.

3. **Email clipping:** Gmail clips emails larger than ~102KB. Check the HTML file size and suggest reductions if it's close to or over the limit:
   - Remove unnecessary comments
   - Minify repetitive inline styles
   - Compress HTML structure
   - Report the current file size

4. **Forwarding collapse:** When a Gmail user forwards an HTML email, Gmail may collapse the entire body under "..." if:
   - There are large commented-out HTML blocks → remove them
   - The HTML is excessively nested → simplify structure
   - There are hidden elements with lots of content → minimize hidden content

5. **Preview text bleed:** Ensure the preheader `<div>` is immediately after `<body>` and the `&nbsp;&zwnj;` padding div follows it. Without this, Gmail pulls visible body text into the inbox preview.

6. **Image display:** Gmail may not show images by default. Ensure every `<img>` has meaningful `alt` text as fallback.

---

## Outlook Fixes:

1. **Conditional comments:** Ensure `<!--[if mso]>` block is in `<head>` with:
   ```xml
   <o:OfficeDocumentSettings>
     <o:AllowPNG/>
     <o:PixelsPerInch>96</o:PixelsPerInch>
   </o:OfficeDocumentSettings>
   ```

2. **Layout:** Outlook uses Word's rendering engine. It does NOT support:
   - `max-width` → set explicit `width` attribute on tables
   - `padding` on `<a>` tags → use table-td-a button pattern
   - `border-radius` → graceful degradation (square corners in Outlook is OK)
   - `background-image` in CSS → use VML for Outlook background images
   - `display:flex` or `display:grid` → tables only
   - `line-height` on block elements behaves differently → set on inline elements

3. **Images:** Outlook may add extra spacing around images. Fix with:
   - `display:block` on all `<img>` tags
   - `border="0"` attribute
   - `Mso-line-height-rule: exactly;` on parent `<td>` if needed

4. **Spacing:** Outlook interprets `margin` inconsistently. Use `padding` on `<td>` elements instead of `margin` on child elements.

5. **Font rendering:** Outlook defaults to Times New Roman if the specified font isn't available. Always include safe fallbacks: `font-family: Arial, Helvetica, sans-serif;`

6. **DPI scaling:** The `<o:PixelsPerInch>96</o:PixelsPerInch>` setting prevents Outlook from scaling the email on high-DPI displays.

---

Apply all fixes and return the corrected HTML.

[Paste your HTML email code here]
```
