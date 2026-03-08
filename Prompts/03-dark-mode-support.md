# Prompt: Add Dark Mode Support to an HTML Email

> Use this prompt to add dark mode compatibility to an existing HTML email.

---

## Prompt

```
Add dark mode support to this HTML email. Follow these steps:

1. **Meta tags** — Ensure these are in the `<head>`:
   - `<meta name="color-scheme" content="light dark">`
   - `<meta name="supported-color-schemes" content="light dark">`

2. **CSS media query** — Add a `@media (prefers-color-scheme: dark)` block inside the existing `<style>` tag.

3. **Strategy for dark mode overrides:**
   - Do NOT change inline styles (they can't be overridden by media queries without `!important` + class selectors).
   - Instead, add CSS classes to key elements and override them in the dark mode media query with `!important`.
   - Example: Add `class="body-bg"` to the body/outer table, then in the media query: `.body-bg { background-color: #1a1a1a !important; }`

4. **What to adjust in dark mode:**
   - Background colors — darken light backgrounds, ensure sufficient contrast
   - Text colors — lighten dark text so it's readable on dark backgrounds
   - Button colors — ensure CTAs remain visible and have good contrast
   - Border colors — adjust if they become invisible
   - Image backgrounds — add fallback background colors behind transparent PNGs

5. **Do NOT change:**
   - Image sources (no need for dark mode image variants unless provided)
   - Layout or spacing
   - Font families or sizes

6. **Testing note:** Add a comment at the top listing which email clients support dark mode CSS:
   - ✅ Apple Mail, Outlook (macOS), Outlook.com, Gmail (Android app)
   - ⚠️ Partial: Gmail (web), Yahoo
   - ❌ Outlook (Windows desktop) — ignores `prefers-color-scheme`

[Paste your HTML email code here]
```
