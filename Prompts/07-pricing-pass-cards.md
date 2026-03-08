# Prompt: Create Pass / Pricing Cards for HTML Email

> Use this prompt to generate email-safe pricing or pass cards that display side-by-side on desktop and stack on mobile.

---

## Prompt

```
Create pricing / pass cards for an HTML email with these requirements:

**Card Data:**
- Card 1: [Name], [Price], [Features list], [CTA text], [CTA link]
- Card 2: [Name], [Price], [Features list], [CTA text], [CTA link]
- Card 3 (optional): [Name], [Price], [Features list], [CTA text], [CTA link]

**Layout rules:**
1. Cards sit side-by-side on desktop (using `<td>` cells within a single `<tr>`).
2. On mobile (max-width: 620px), cards stack vertically and center with `max-width: 280px; margin: 0 auto;`.
3. Each card has: a colored header/title bar, price in large text, a feature list, and a CTA button at the bottom.
4. Use table-based layout — no flexbox or grid.
5. Add 10-15px gap between cards on desktop (use padding on `<td>`).

**Styling:**
- Card background: [hex color]
- Card border: 1px solid [hex color] with border-radius (where supported)
- Title bar background: [hex color]
- Price text: large, bold
- Feature list: simple text, one feature per line or with bullet characters (•)
- CTA button: bulletproof table-based button

**Responsive behavior:**
- Add `.mobile-stack` class to each card `<td>`: `display: block !important; width: 100% !important;`
- Add max-width constraint on mobile so cards don't stretch full-width on tablets
- Center cards on mobile with `margin: 0 auto !important;`
- Add vertical spacing between stacked cards: `margin-bottom: 16px !important;`

**Accessibility:**
- Use semantic heading for card titles
- Ensure text contrast meets WCAG AA (4.5:1 ratio)

Generate the complete HTML table structure with inline styles and the responsive CSS.
```
