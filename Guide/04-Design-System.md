# Design System for HTML Emails

> How to create a reusable set of colors, fonts, spacing, and component styles for consistent email design.

---

## Why You Need a Design System

Without a design system, each email looks slightly different — colors drift, spacing varies, button styles change. A design system gives you:

- **Consistency** across every email you send
- **Speed** — no time wasted picking colors or font sizes each time
- **Brand recognition** — recipients recognize your emails at a glance
- **Easier collaboration** — anyone can build an email that matches the brand

---

## 1. Color Palette

Pick **5–6 colors** that cover all your needs:

| Role | Purpose | Example |
|------|---------|---------|
| **Page Background** | Outer wrapper behind the email | `#F5F5F5` (light gray) |
| **Container Background** | Main email content area | `#FFFFFF` (white) |
| **Primary** | Headings, buttons, accent elements | `#2563EB` (blue) |
| **Secondary** | Supporting elements, secondary buttons | `#64748B` (slate) |
| **Body Text** | Paragraph text | `#1F2937` (near-black) |
| **Muted Text** | Footer, captions, small print | `#6B7280` (gray) |
| **Footer Background** | Footer section | `#1F2937` (dark) |

### How to choose colors
1. Start with your brand's primary color
2. Pick a dark color for text (ensure 4.5:1 contrast ratio against the container background)
3. Pick a light background that doesn't compete with the primary
4. Add a muted gray for secondary text
5. Use a dark color for the footer

**Contrast check:** Use [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/) to verify text is readable.

### Example: Event / Festival Theme

| Role | Color | Hex |
|------|-------|-----|
| Page Background | Deep maroon | `#5A0F14` |
| Panel Background | Lighter maroon | `#8B1E24` |
| Primary Accent | Bright gold | `#F5C945` |
| Muted Accent | Soft gold | `#E7C27D` |
| Body Text | Warm cream | `#F6E6C3` |
| Footer Background | Near-black maroon | `#3D0A0D` |

### Example: Corporate / SaaS Theme

| Role | Color | Hex |
|------|-------|-----|
| Page Background | Light gray | `#F3F4F6` |
| Container | White | `#FFFFFF` |
| Primary | Indigo | `#4F46E5` |
| Accent | Emerald | `#10B981` |
| Body Text | Dark gray | `#111827` |
| Footer Background | Dark slate | `#1E293B` |

---

## 2. Font Stacks

HTML emails can only use **web-safe fonts** reliably. Here are the two stacks you need:

### Heading Font
```css
font-family: Georgia, 'Times New Roman', Times, serif;
```
Georgia gives a classic, editorial feel. Use it for headings, titles, and pull quotes.

### Body Font
```css
font-family: Arial, Helvetica, sans-serif;
```
Arial is universally available and highly readable at small sizes. Use it for paragraphs, labels, and buttons.

### Alternative stacks

| Style | Stack |
|-------|-------|
| Modern sans-serif | `'Trebuchet MS', Arial, Helvetica, sans-serif` |
| Monospace | `'Courier New', Courier, monospace` |
| Friendly sans | `Verdana, Geneva, sans-serif` |
| Clean serif | `'Palatino Linotype', 'Book Antiqua', Palatino, serif` |

> **Note:** Web fonts (`@font-face`) only work in Apple Mail and Outlook for Mac. Every other client will fall back to the system font. Don't depend on them.

---

## 3. Typography Scale

Define a consistent set of sizes:

| Element | Desktop Size | Mobile Size | Weight | Line Height |
|---------|:----------:|:---------:|:------:|:-----------:|
| h1 (hero title) | 32px | 24px | bold | 1.2 |
| h2 (section title) | 24px | 20px | bold | 1.3 |
| h3 (subsection) | 18px | 16px | bold | 1.3 |
| Body text | 16px | 15px | normal | 1.6 |
| Small / caption | 13px | 12px | normal | 1.5 |
| Button text | 15px | 15px | bold | 1.0 |

### Typography in code

```html
<!-- Section title -->
<h2 style="margin:0 0 12px; font-family:Georgia,'Times New Roman',serif;
           font-size:24px; font-weight:bold; line-height:1.3; color:#1F2937;">
  Section Title
</h2>

<!-- Body text -->
<p style="margin:0 0 16px; font-family:Arial,Helvetica,sans-serif;
          font-size:16px; line-height:1.6; color:#1F2937;">
  Body paragraph text goes here.
</p>
```

---

## 4. Spacing System

Use consistent padding values across all sections:

| Use | Value |
|-----|-------|
| Section vertical padding | 30–40px |
| Content horizontal padding | 40px (desktop), 20px (mobile) |
| Between paragraphs | 16px (`margin-bottom`) |
| Between heading and text | 12px |
| Between sections | 0px (use section padding instead) |
| Button padding | 16px top/bottom, 36px left/right |
| Card internal padding | 20–24px |
| Card gap (between cards) | 12–16px |

### Mobile overrides
```css
@media (max-width: 620px) {
  .mobile-pad {
    padding-left: 20px !important;
    padding-right: 20px !important;
  }
  .section-pad {
    padding-top: 24px !important;
    padding-bottom: 24px !important;
  }
}
```

---

## 5. Button Styles

Define two button variants:

### Primary (filled)

```
Background: #2563EB (primary color)
Text: #FFFFFF (white)
Padding: 16px 36px
Border radius: 8px
Font: 15px bold Arial
```

```html
<td style="background-color:#2563EB; border-radius:8px;">
  <a href="#" target="_blank"
     style="display:inline-block; padding:16px 36px;
            font-family:Arial,Helvetica,sans-serif; font-size:15px;
            font-weight:bold; color:#FFFFFF; text-decoration:none;">
    Primary Action
  </a>
</td>
```

### Secondary (outline)

```
Background: transparent
Border: 2px solid #2563EB
Text: #2563EB
Padding: 14px 34px (smaller to account for border)
Border radius: 8px
Font: 15px bold Arial
```

```html
<td style="border:2px solid #2563EB; border-radius:8px; background-color:transparent;">
  <a href="#" target="_blank"
     style="display:inline-block; padding:14px 34px;
            font-family:Arial,Helvetica,sans-serif; font-size:15px;
            font-weight:bold; color:#2563EB; text-decoration:none;">
    Secondary Action
  </a>
</td>
```

---

## 6. Component Reference

### Divider
```html
<tr>
  <td style="padding:0 40px;">
    <hr style="border:0; border-top:1px solid #E5E7EB; margin:0;">
  </td>
</tr>
```

### Spacer (vertical space between sections)
```html
<tr>
  <td style="height:24px; font-size:1px; line-height:1px;">&nbsp;</td>
</tr>
```

### Image (responsive)
```html
<img src="https://example.com/image.png"
     width="520" alt="Description"
     style="display:block; width:520px; max-width:100%; height:auto; border:0;">
```

---

## 7. Documenting Your System

Create a simple reference table for your specific project (paste it at the top of your HTML file as a comment or keep it in a separate document):

```
DESIGN SYSTEM
─────────────
Page BG:     #F5F5F5
Container:   #FFFFFF
Primary:     #2563EB
Text:        #1F2937
Muted:       #6B7280
Footer BG:   #1F2937

Heading:     Georgia, 'Times New Roman', serif
Body:        Arial, Helvetica, sans-serif

H1: 32px bold | H2: 24px bold | Body: 16px regular
Section pad: 30px vertical, 40px horizontal
Button pad:  16px 36px, 8px radius
```

---

## Navigation

← [Common Mistakes](03-Common-Mistakes.md) · [Testing Your Email](05-Testing-Your-Email.md) →
