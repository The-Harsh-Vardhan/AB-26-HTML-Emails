# Prompt: Create an Email Footer Section

> Use this prompt to generate a well-structured footer for HTML emails with social links, contact info, and legal text.

---

## Prompt

```
Create a footer section for an HTML email with the following:

**Content to include:**
- Organization name: [Name]
- Social media links: [List platforms and URLs — e.g., Instagram: url, Twitter/X: url, YouTube: url, LinkedIn: url]
- Contact email: [email]
- Contact phone: [phone number]
- Website: [URL]
- Address (optional): [physical address]
- Unsubscribe link: [URL or placeholder]
- Legal/copyright text: [e.g., "© 2026 Organization Name. All rights reserved."]

**Layout:**
1. Top divider — a thin horizontal line or gold decorative divider separating footer from content
2. Social media icons row — inline images or text links, centered, with spacing between them
3. Contact info — email and phone, centered
4. Organization name + address
5. Unsubscribe link — clearly visible but not prominent
6. Copyright text — small, muted color

**Technical requirements:**
- Table-based layout
- All styles inline
- Background color: [hex — typically darker than the email body]
- Text color: [hex — muted/lighter]
- Font size: 12-13px for footer text
- Links should have `color: [hex]` and `text-decoration: underline`
- Social icon images: 24-32px width, with `alt` text for each platform
- On mobile, stack or wrap social icons if needed
- `role="presentation"` on all tables

**For social icons, use this format:**
```html
<a href="[URL]" target="_blank" style="text-decoration:none;">
  <img src="[ICON_URL]" width="28" height="28" alt="[Platform]"
       style="display:inline-block; width:28px; height:28px; border:0;">
</a>
```

Generate the complete footer HTML.
```
