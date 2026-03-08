# Prompt: Write Email Subject Line & Preheader Text

> Use this prompt to generate compelling subject lines and optimized preheader (preview) text for HTML emails.

---

## Prompt

```
Write email subject lines and preheader text for a promotional HTML email.

**Email context:**
- Event/Product: [Name]
- Key selling points: [e.g., "25+ events, live performances, prizes worth ₹3L"]
- Target audience: [e.g., "college students aged 18-22"]
- Tone: [e.g., "exciting, urgent, FOMO-inducing" or "professional, informative"]
- Any date pressure: [e.g., "event is in 10 days", "early bird ends tomorrow"]

**Generate:**

1. **5 subject line options** — each under 50 characters (so they don't get cut off on mobile). Mix these styles:
   - Curiosity-driven
   - Urgency/FOMO
   - Benefit-focused
   - Question format
   - Emoji-enhanced (use sparingly — 1 emoji max)

2. **3 preheader text options** — each 40-90 characters. The preheader appears after the subject line in the inbox list. It should:
   - Complement the subject line (don't repeat it)
   - Add new information or a secondary hook
   - End cleanly (no cut-off mid-word)

3. **The HTML code** to add the preheader right after `<body>`:
   ```html
   <!-- Preheader -->
   <div style="display:none; max-height:0px; overflow:hidden; opacity:0;
               mso-hide:all; font-size:1px; line-height:1px;">
     [Preheader text here]
   </div>
   <!-- Invisible padding to prevent Gmail from pulling body content into preview -->
   <div style="display:none; max-height:0px; overflow:hidden; opacity:0;
               mso-hide:all; font-size:1px; line-height:1px;">
     &nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;
   </div>
   ```

**Important:**
- The second div with `&nbsp;&zwnj;` characters acts as invisible padding so Gmail doesn't pull random body text into the inbox preview.
- Include `mso-hide:all` for Outlook compatibility.
```
