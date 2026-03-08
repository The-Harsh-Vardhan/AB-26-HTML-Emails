# Testing Your HTML Email

> Tools, workflow, and checklist for making sure your email looks right everywhere before you hit send.

---

## Why Testing Matters

You built your email, it looks great in Chrome — but that means almost nothing. Your recipients will view it in Gmail, Outlook, Apple Mail, Yahoo, and Samsung Mail, each with its own rendering quirks. The only way to catch issues is to test across real clients.

---

## Testing Workflow

### Step 1: Browser Preview

Open your HTML file in Chrome or Firefox. This catches basic issues:

- [ ] Layout renders centered at 600px
- [ ] Text is readable
- [ ] Images load (if using public URLs)
- [ ] Links point to the right URLs
- [ ] No broken HTML (check DevTools console for errors)

**Responsive check:** Open DevTools (F12) → Toggle device toolbar (Ctrl+Shift+M) → Set width to 375px → Verify mobile layout stacks correctly.

---

### Step 2: Send a Test Email to Yourself

The most reliable test. Here's how:

#### Using Gmail (free)
1. Open your HTML file in a browser
2. Press `Ctrl+A` (select all) then `Ctrl+C` (copy)
3. Open Gmail → Compose
4. Click in the compose body and press `Ctrl+V` (paste)
5. Send it to yourself

> **Tip:** Use an extension like **Mail Brother** (Chrome/Edge) to paste raw HTML directly into Gmail's compose window without rendering issues.

#### Using PutsMail (free)
1. Go to [putsmail.com](https://putsmail.com/)
2. Paste your HTML code
3. Enter your email address
4. Click "Send" — you'll receive the email in your inbox

#### Using your ESP (SendGrid, Mailchimp, etc.)
Most email service providers have a "Send Test Email" feature. Use it before sending to your list.

---

### Step 3: Cross-Client Testing

Test in as many clients as possible:

| Priority | Client | How to Test |
|----------|--------|-------------|
| 🔴 High | Gmail (web) | Send test email, open in browser |
| 🔴 High | Gmail (Android app) | Send test email, open on phone |
| 🔴 High | Gmail (iOS app) | Send test email, open on iPhone |
| 🔴 High | Outlook (web/365) | Log into outlook.com |
| 🟡 Medium | Outlook (Windows desktop) | Open in Outlook 2019/365 desktop app |
| 🟡 Medium | Apple Mail | Send to an iCloud email, open on Mac/iPhone |
| 🟡 Medium | Yahoo Mail | Send to a Yahoo address |
| 🟢 Low | Samsung Mail | Open on a Samsung phone |
| 🟢 Low | Thunderbird | Open in Thunderbird desktop client |

#### Paid testing tools

| Tool | What It Does | Free Tier? |
|------|-------------|------------|
| [Litmus](https://www.litmus.com/) | Screenshot previews in 90+ email clients | Limited free |
| [Email on Acid](https://www.emailonacid.com/) | Cross-client previews + spam testing | 7-day trial |
| [Testi@](https://testi.at/) | Email rendering previews | Free limited |

---

### Step 4: Test Forwarding

Gmail has a known issue where forwarded HTML emails collapse under "..." if:
- The HTML is too complex or deeply nested
- There are large comment blocks in the source

**How to test:**
1. Send the email to yourself in Gmail
2. Forward it to another address
3. Check if the full content is visible or collapsed

**Fix:** Remove large HTML comments, minimize nesting, keep HTML clean.

---

### Step 5: Test Dark Mode

1. Enable dark mode on your phone (Settings → Display → Dark theme)
2. Open the test email in Gmail (Android) or Apple Mail
3. Check:
   - [ ] Text is readable against the dark background
   - [ ] Buttons are visible and have good contrast
   - [ ] Images (especially transparent PNGs) aren't invisible
   - [ ] No white/light boxes around images that shouldn't have them

---

## Pre-Send Checklist

Run through this before every send:

### Content
- [ ] Subject line is set and under 50 characters
- [ ] Preheader text is compelling and shows in inbox preview
- [ ] All text is proofread (no typos, no placeholder content)
- [ ] Dates, times, prices are correct

### Links
- [ ] Every link works (click-test each one)
- [ ] All links have `target="_blank"`
- [ ] CTA buttons link to the right destination
- [ ] Unsubscribe link works
- [ ] Social media links are correct

### Images
- [ ] All images load (hosted on public URLs, not local files)
- [ ] Every `<img>` has `alt` text
- [ ] Every `<img>` has `display:block`, `width` attribute, `height:auto`, `border:0`
- [ ] Each image is under 300KB
- [ ] Total email images are under 1MB combined

### Layout
- [ ] Desktop: centered at 600px, all sections aligned
- [ ] Mobile: content stacks vertically, text is readable
- [ ] Buttons are thumb-friendly on mobile (minimum 44px tap target)
- [ ] No horizontal scrolling on mobile

### Technical
- [ ] HTML file size is under 80KB (Gmail clips at 102KB)
- [ ] `role="presentation"` on all layout tables
- [ ] `cellpadding="0"` and `cellspacing="0"` on all tables
- [ ] No JavaScript in the email
- [ ] Outlook conditional comments present in `<head>`
- [ ] Dark mode meta tags present

### Accessibility
- [ ] Color contrast meets WCAG AA (4.5:1 for text)
- [ ] `alt` text on all meaningful images, `alt=""` on decorative ones
- [ ] Heading hierarchy is logical (h1 → h2 → h3)
- [ ] Links are descriptive ("Register Now", not "Click here")

---

## Debugging Tips

### "My email looks fine in Chrome but broken in [client]"

1. **Gmail mobile strips `<style>` blocks** — Are all critical styles inline?
2. **Outlook ignores `max-width`** — Did you set `width` as an HTML attribute?
3. **Images have gaps** — Did you add `display:block` to `<img>` tags?
4. **Button has no padding in Outlook** — Are you using the table → td → a pattern?
5. **Text is tiny on mobile** — Did you add responsive font-size overrides?

### "Gmail shows weird preview text"

Your preheader is missing or broken. Add it right after `<body>`:
```html
<div style="display:none; max-height:0; overflow:hidden; opacity:0;
            mso-hide:all; font-size:1px; line-height:1px;">
  Your preview text here.
</div>
```

### "Email is clipped in Gmail"

Your HTML is over 102KB. To reduce size:
- Remove comments and commented-out code
- Remove redundant inline styles
- Simplify nested tables
- Use shorter attribute values and hex colors

Check size: open the file in your editor and look at the file size, or use `wc -c yourfile.html` in the terminal.

---

## Navigation

← [Design System](04-Design-System.md) · [Glossary](Glossary.md) →
