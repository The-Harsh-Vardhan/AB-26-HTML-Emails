# Prompt: Make an HTML Email Responsive / Mobile-Friendly

> Use this prompt to add or fix responsive (mobile) styles in an existing HTML email.

---

## Prompt

```
I have an HTML email that looks good on desktop but is broken on mobile. Make it fully responsive with these rules:

1. **Breakpoint:** Use `@media only screen and (max-width: 620px)`.

2. **Container:** Force the main container table to `width: 100% !important; max-width: 100% !important;` on mobile.

3. **Column stacking:** Any side-by-side `<td>` elements that act as columns should stack vertically on mobile. Add class `.mobile-stack` with `display: block !important; width: 100% !important;` to those cells.

4. **Padding:** Add class `.mobile-pad` for safe horizontal padding: `padding-left: 18px !important; padding-right: 18px !important;`.

5. **Hide decorative elements:** Add class `.mobile-hide` with `display: none !important;` to purely decorative images, spacers, or ornaments that waste space on small screens.

6. **Typography scaling:** Increase body text to at least 14px on mobile. Reduce oversized headings proportionally (e.g., 32px desktop → 22px mobile).

7. **Buttons:** Make CTA buttons full-width on mobile with class `.mobile-btn`: `display: block !important; width: 100% !important; text-align: center !important; box-sizing: border-box !important;`.

8. **Images:** Ensure all images have `max-width: 100% !important; height: auto !important;` on mobile so they don't overflow.

9. **Card layouts:** If there are pass/pricing cards or grid items side-by-side, stack them vertically and center them with `max-width: 280px; margin: 0 auto;` on mobile.

10. **Text alignment:** Center-align text blocks that were left-aligned next to images when the layout stacks.

Apply all changes using `!important` in the `@media` query to override inline styles.

[Paste your HTML email code here]
```
