# Prompt: Image Hosting & Optimization for HTML Emails

> Use this prompt to get guidance on preparing, hosting, and embedding images in HTML emails.

---

## Prompt

```
I'm building an HTML email and need help with images. Guide me through:

1. **Image preparation:**
   - What formats work best in email? (PNG vs JPG vs GIF)
   - What's the maximum recommended file size per image?
   - What dimensions should I use for: banner/hero images, logos, icons, character illustrations?
   - Should I use @2x/retina images? If yes, how do I implement them in email HTML?

2. **Hosting images:**
   - I need to host images online because email clients don't support local file paths.
   - Walk me through uploading to imgbb.com (or suggest alternatives).
   - How do I get the direct image URL (not the page URL)?

3. **Embedding in HTML email:**
   - Show me the correct `<img>` tag format for email with all necessary attributes.
   - Include: `src`, `width` (attribute AND inline style), `height:auto`, `display:block`, `alt`, `border="0"`.
   - How do I prevent the phantom spacing gap below images?
   - How do I make images responsive (scale down on mobile)?

4. **Background images in email:**
   - Which email clients support CSS `background-image`?
   - Show me the VML fallback technique for Outlook background images.
   - When should I use background images vs inline `<img>` tags?

5. **Responsive image rules:**
   - Provide the CSS for making images fluid on mobile:
     ```css
     @media only screen and (max-width: 620px) {
       img.fluid { width: 100% !important; max-width: 100% !important; height: auto !important; }
     }
     ```

6. **Accessibility:**
   - Every image must have descriptive `alt` text.
   - Decorative images should have `alt=""` (empty alt, not missing alt).
   - What alt text guidelines should I follow for email?

Provide code examples for each point.
```

---

## Quick Reference: Image `<img>` Tag Template

```html
<img src="https://i.ibb.co/XXXXX/your-image.png"
     width="600" alt="Descriptive text here"
     border="0"
     style="display:block; width:600px; max-width:100%; height:auto;">
```
