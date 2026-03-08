# Prompt: Debug & Fix HTML Email Rendering Issues

> Use this prompt when your HTML email looks broken in certain email clients or devices.

---

## Prompt

```
My HTML email has rendering issues. Help me debug and fix them.

**Issue:** [Describe what's broken — e.g., "layout breaks in Outlook", "images don't show on mobile", "text overflows on Gmail", "forwarded email collapses in Gmail"]

**Email client(s) affected:** [e.g., Gmail web, Gmail mobile, Outlook 2019, Apple Mail, Yahoo]

**What I expect:** [Describe the correct behavior]

**What actually happens:** [Describe the broken behavior, attach screenshot if possible]

---

Debug checklist — check and fix these common problems:

1. **Outlook-specific issues:**
   - Is the `<!--[if mso]>` conditional comment present in `<head>` with `<o:OfficeDocumentSettings>`?
   - Are you using `<table>` layout (not flexbox/grid)?
   - Outlook ignores `max-width` — are you setting `width` attribute on tables?
   - Outlook doesn't support `padding` on `<a>` tags — are buttons using the table-td-a pattern?
   - Outlook ignores `border-radius` — is that acceptable?

2. **Gmail-specific issues:**
   - Gmail strips `<style>` blocks on mobile — are all critical styles inline?
   - Gmail clips emails over ~102KB — is the HTML file size under 102KB?
   - Gmail collapses forwarded HTML under "..." — is the HTML clean (no large comment blocks, no excessive nesting)?
   - Gmail pulls body text into preview if preheader is missing — is the preheader + `&nbsp;&zwnj;` padding present?

3. **Image issues:**
   - Are images hosted online (not local paths)?
   - Do all `<img>` tags have `display:block`, `width` attribute + inline width, `height:auto`, `border="0"`?
   - Are images under 300KB each?
   - Is total email size (HTML + images) reasonable?

4. **Mobile/responsive issues:**
   - Is the `@media (max-width: 620px)` query present?
   - Are column `<td>` elements getting `.mobile-stack` class?
   - Are `!important` flags used in media query overrides?
   - Is the viewport meta tag present?

5. **General:**
   - Is `role="presentation"` on all layout tables?
   - Are `cellpadding="0"` and `cellspacing="0"` set on all tables?
   - Is the inner container ≤ 600px?
   - Are there any unclosed tags or malformed HTML?

[Paste your HTML email code here]
```
