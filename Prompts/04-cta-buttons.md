# Prompt: Create Bulletproof CTA Buttons for HTML Email

> Use this prompt to generate email-safe CTA (Call to Action) buttons that work across all email clients, including Outlook.

---

## Prompt

```
Create bulletproof CTA buttons for an HTML email. These buttons must work in ALL email clients including Microsoft Outlook (which doesn't support padding on <a> tags properly).

Requirements:

1. **Filled / Primary button:**
   - Use a `<table role="presentation">` wrapper with a single `<tr><td>` that has the background color.
   - Inside the `<td>`, place an `<a>` tag with `display:inline-block`, padding, font styles, and `text-decoration:none`.
   - The `<td>` gets `background-color` and `border-radius`.
   - The `<a>` tag gets the text color, font-family, font-size, font-weight, and padding.
   - Center the button table with `style="margin:0 auto;"`.

2. **Outline / Ghost button:**
   - Same structure as above, but the `<td>` gets `border: 2px solid [color]` instead of background-color.
   - `background-color: transparent` on the `<td>`.
   - The `<a>` tag text color matches the border color.

3. **Mobile responsive:**
   - Add class `.mobile-btn` to the outer `<table>`.
   - In the responsive `@media` query: `.mobile-btn { width: 100% !important; }` and `.mobile-btn td { padding: 0 !important; }` and `.mobile-btn a { display: block !important; width: 100% !important; padding: 16px 0 !important; text-align: center !important; }`

4. **Button specs:**
   - Padding: `16px 36px` (desktop), full-width on mobile
   - Font: Arial, Helvetica, sans-serif
   - Font size: 15px
   - Font weight: bold
   - Border radius: 8px
   - `target="_blank"` on the `<a>` tag

Generate examples with these color combinations:
- Primary: Gold background (#F5C945) with dark maroon text (#3D0A0D)
- Outline: Transparent background with gold border and gold text (#F5C945)

Include the responsive CSS needed in the `<style>` block.
```
