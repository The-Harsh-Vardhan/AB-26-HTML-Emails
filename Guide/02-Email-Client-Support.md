# Email Client Support Matrix

> What CSS and HTML features work in which email clients. Use this as a quick reference before using any CSS property.

---

## The Landscape

Every email client uses a different rendering engine. Here are the big ones:

| Client | Rendering Engine | Notes |
|--------|-----------------|-------|
| Gmail (Web) | Custom (strips most `<style>`) | Supports `<style>` in `<head>` since 2016, but still strips some |
| Gmail (Android/iOS) | Custom | Strips `<style>` blocks on mobile apps |
| Outlook 2007–2019 (Windows) | **Microsoft Word** | The worst offender. No `max-width`, limited CSS |
| Outlook 365 (Web) | Custom | Better than desktop Outlook, still limited |
| Outlook (Mac) | WebKit | Actually pretty good |
| Apple Mail (macOS/iOS) | WebKit | Best email rendering engine. Supports almost everything |
| Yahoo Mail | Custom | Supports `<style>` blocks, decent CSS support |
| Samsung Mail | WebKit-based | Reasonable support |
| Thunderbird | Gecko | Good CSS support, smaller user base |

---

## CSS Feature Support

| Feature | Gmail Web | Gmail Mobile | Outlook (Win) | Outlook (Mac) | Apple Mail | Yahoo |
|---------|:---------:|:------------:|:--------------:|:--------------:|:----------:|:-----:|
| `<style>` in `<head>` | ✅ | ❌ | ✅ | ✅ | ✅ | ✅ |
| Inline `style=""` | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| `@media` queries | ✅ | ❌ | ❌ | ✅ | ✅ | ✅ |
| `max-width` | ✅ | ✅ | ❌ | ✅ | ✅ | ✅ |
| `margin` | ⚠️ | ⚠️ | ⚠️ | ✅ | ✅ | ✅ |
| `padding` | ✅ | ✅ | ⚠️¹ | ✅ | ✅ | ✅ |
| `border-radius` | ✅ | ✅ | ❌ | ✅ | ✅ | ✅ |
| `background-image` (CSS) | ✅ | ✅ | ❌ | ✅ | ✅ | ✅ |
| `background-color` | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| `float` | ❌ | ❌ | ❌ | ✅ | ✅ | ❌ |
| `flexbox` | ❌ | ❌ | ❌ | ✅ | ✅ | ❌ |
| `grid` | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ |
| `position` | ❌ | ❌ | ❌ | ⚠️ | ✅ | ❌ |
| `display:none` | ✅ | ✅ | ❌² | ✅ | ✅ | ✅ |
| `prefers-color-scheme` | ⚠️ | ✅ | ❌ | ✅ | ✅ | ⚠️ |
| Web fonts (`@font-face`) | ❌ | ❌ | ❌ | ✅ | ✅ | ❌ |
| `<video>` | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ |
| SVG (`<svg>`) | ❌ | ❌ | ❌ | ⚠️ | ✅ | ❌ |
| VML | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ |
| CSS shorthand³ | ✅ | ✅ | ⚠️ | ✅ | ✅ | ✅ |
| `line-height` | ✅ | ✅ | ⚠️ | ✅ | ✅ | ✅ |
| `letter-spacing` | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| `text-align` | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| `width`/`height` (attr) | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |

**Footnotes:**
1. ⚠️¹ Outlook ignores `padding` on `<a>`, `<p>`, and `<div>` tags. Use padding on `<td>` instead.
2. ❌² Outlook uses `mso-hide:all` instead of `display:none`.
3. ⚠️³ Outlook handles CSS shorthand (`border`, `font`, `background`) inconsistently. Always use longhand properties.

---

## Practical Takeaways

### Always do these (works everywhere):
- ✅ Use `<table>` based layouts
- ✅ Inline all critical CSS with `style=""`
- ✅ Set `width` as an HTML attribute on tables (for Outlook)
- ✅ Use `cellpadding="0"` and `cellspacing="0"`
- ✅ Use `background-color` (not `background-image`) for solid backgrounds
- ✅ Use `text-align` and `vertical-align` for positioning
- ✅ Use padding on `<td>` elements for spacing
- ✅ Set `role="presentation"` on layout tables
- ✅ Use web-safe font stacks (Arial, Georgia, etc.)

### Progressive enhancement (use with fallback):
- ⚠️ `border-radius` — Falls back to square corners in Outlook (acceptable)
- ⚠️ `@media` queries — Put responsive styles here, but ensure email is readable without them
- ⚠️ `prefers-color-scheme` — Dark mode enhancement; light mode must work without it
- ⚠️ `<style>` block in `<head>` — Use for media queries only; never put critical styles here

### Never use (unsupported in major clients):
- ❌ Flexbox / CSS Grid
- ❌ JavaScript
- ❌ External stylesheets (`<link rel="stylesheet">`)
- ❌ `position: absolute/fixed/relative`
- ❌ `float`
- ❌ Web fonts (except Apple Mail and Outlook Mac)
- ❌ CSS animations / transitions
- ❌ `<video>` or `<audio>` (except Apple Mail)

---

## Outlook-Specific Workarounds

Outlook for Windows uses **Microsoft Word's rendering engine**, which is the most limited of all email clients. Here are the key workarounds:

| Problem | Workaround |
|---------|------------|
| Ignores `max-width` | Set `width` as an HTML attribute: `<table width="600">` |
| Ignores `padding` on `<a>` | Use the table → td → a button pattern |
| Ignores `border-radius` | Accept square corners or use VML for rounded buttons |
| Ignores `background-image` (CSS) | Use VML `<v:rect>` for background images |
| Ignores `display:none` | Use `mso-hide:all` on elements to hide |
| Scales on high-DPI displays | Add `<o:PixelsPerInch>96</o:PixelsPerInch>` in head conditional |
| Adds gaps around images | Add `display:block` and `border:0` to all `<img>` tags |
| Defaults to Times New Roman | Always specify full font stack with safe fallbacks |

---

## Gmail-Specific Notes

| Behavior | Impact |
|----------|--------|
| Strips `<style>` blocks on mobile apps | All critical styles must be inline |
| Clips emails over ~102KB | Keep total HTML file size under 102KB |
| Strips `class` attributes (older behavior) | Don't rely on classes for layout — only for media query overrides |
| Collapses forwarded email under "..." | Keep HTML clean, remove large comment blocks |
| Pulls body text into preview without preheader | Always add preheader + `&nbsp;&zwnj;` padding |
| May not show images by default | Always include meaningful `alt` text |

---

## Live Reference

For the most up-to-date support data, check:
- **[Can I Email](https://www.caniemail.com/)** — The "Can I Use" of email development
- **[Campaign Monitor CSS Guide](https://www.campaignmonitor.com/css/)** — Detailed CSS property support per client

---

## Navigation

← [Getting Started](01-Getting-Started.md) · [Common Mistakes](03-Common-Mistakes.md) →
