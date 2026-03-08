# Prompt: Create an Events / Features Grid for HTML Email

> Use this prompt to generate a grid layout for showcasing events, features, or categories in an HTML email.

---

## Prompt

```
Create an events/features grid section for an HTML email:

**Grid Items:** (provide your items)
- Item 1: [Icon/Emoji] [Title] — [Short description]
- Item 2: [Icon/Emoji] [Title] — [Short description]
- Item 3: [Icon/Emoji] [Title] — [Short description]
- Item 4: [Icon/Emoji] [Title] — [Short description]
- Item 5: [Icon/Emoji] [Title] — [Short description]
- Item 6: [Icon/Emoji] [Title] — [Short description]

**Layout rules:**
1. **Desktop:** 2 columns (two `<td>` cells per `<tr>`), so items appear in a 2×N grid.
2. **Mobile:** 1 column — each `<td>` stacks vertically using `.mobile-stack` class.
3. Each grid item is a small card/cell with:
   - An icon or emoji at the top (or to the left)
   - A bold title
   - A one-line description underneath
   - Optional: a subtle background or border to visually separate items
4. Consistent padding inside each cell (12-16px).
5. Consistent gap between cells.

**Technical requirements:**
- Table-based layout with `role="presentation"`.
- All styles inline.
- Responsive class `.mobile-stack` for stacking: `display: block !important; width: 100% !important;`
- On mobile, center-align each item's content.
- Use `valign="top"` on `<td>` elements so content aligns at the top when columns have different heights.

**Styling:**
- Cell background: [hex color or transparent]
- Title: bold, [font-size], [color]
- Description: regular weight, [font-size], [color]
- Icon size: 36-48px (if using images) or inline emoji

Generate the HTML structure with inline styles and responsive CSS.
```
