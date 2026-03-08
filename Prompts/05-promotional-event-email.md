# Prompt: Create a Promotional / Event Email

> Use this prompt to generate a complete promotional or event announcement HTML email from scratch.

---

## Prompt

```
Create a complete promotional HTML email for an event with the following details:

**Event Info:**
- Event Name: [Your Event Name]
- Dates: [Event Dates]
- Venue: [Venue / Location]
- Organizer: [Organization Name]
- Registration Link: [URL]
- Theme/Vibe: [e.g., carnival, tech, music, cultural]

**Color Palette:**
- Primary Background: [hex color]
- Secondary/Panel Background: [hex color]
- Accent Color (buttons, highlights): [hex color]
- Text Color: [hex color]
- Dark/Footer Background: [hex color]

**Sections to include (in order):**
1. Hidden preheader text (preview text for inbox)
2. "View in browser" link at the top
3. Logo / seal image
4. Hero section — event name, dates, tagline, primary CTA button
5. Decorative divider
6. Introduction paragraph with supporting imagery
7. Pass / pricing cards (if applicable — list pass types and prices)
8. Events or features grid (2 columns on desktop, 1 on mobile)
9. How to register — numbered steps
10. Final CTA section
11. Footer — social links, contact info, unsubscribe link

**Technical requirements:**
- Table-based layout, 600px max-width container
- All styles inline (use `<style>` block only for @media responsive and dark mode)
- Responsive at 620px breakpoint
- Dark mode support with `prefers-color-scheme` media query
- All layout tables with `role="presentation"`, `cellpadding="0"`, `cellspacing="0"`
- Bulletproof CTA buttons (table-based, not just styled `<a>` tags)
- Use placeholder image URLs (I'll replace them later)
- Include accessibility: alt text on images, semantic heading hierarchy, sufficient color contrast

**Fonts:**
- Headings: Georgia, 'Times New Roman', serif
- Body: Arial, Helvetica, sans-serif

Generate the complete HTML file.
```

---

## Tips

- Replace placeholder image URLs with real hosted URLs (use [imgbb.com](https://imgbb.com/)) before sending.
- Test on desktop and mobile email clients after each major edit.
- Run through [Checklist.md](../Checklist.md) before final send.
