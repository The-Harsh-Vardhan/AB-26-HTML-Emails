# Prompt: Convert a Design / Screenshot into an HTML Email

> Use this prompt when you have a visual design (Figma, Canva, screenshot, etc.) and need to convert it into a coded HTML email.

---

## Prompt

```
Convert this design into a production-ready HTML email.

**Design reference:** [Attach screenshot, Figma link, or describe the design in detail]

**Instructions:**

1. **Analyze the design** and break it into horizontal sections (rows). Each section becomes a `<tr>` in the main container table.

2. **Identify the layout pattern** for each section:
   - Full-width image/banner → single `<td>` with `<img>`
   - Text block → single `<td>` with styled text
   - Two-column layout → `<tr>` with two `<td>` cells (or nested table)
   - Card grid → nested tables for each card
   - CTA button → bulletproof table-based button

3. **Extract the design system:**
   - Background colors (use exact hex codes from the design)
   - Text colors
   - Font families (use web-safe fallbacks: Georgia/serif for headings, Arial/sans-serif for body)
   - Font sizes for each heading level and body text
   - Spacing/padding values
   - Border radius (note: won't work in Outlook)
   - Button styles

4. **Build the email with:**
   - Table-based layout, 600px max-width container
   - All styles inline
   - `role="presentation"` on layout tables
   - `cellpadding="0"` and `cellspacing="0"` on all tables
   - Responsive breakpoint at 620px
   - Dark mode support
   - Preheader text

5. **For images in the design:**
   - Use placeholder URLs (e.g., `https://via.placeholder.com/600x300`)
   - Add comments noting which design asset each image corresponds to
   - Set correct `width` and `height` attributes based on design dimensions

6. **Match the design as closely as possible** while respecting email client limitations. Note any design elements that cannot be replicated in email (e.g., complex gradients, custom fonts, CSS animations) and suggest fallbacks.

Generate the complete HTML file.
```
