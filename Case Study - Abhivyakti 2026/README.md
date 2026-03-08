[← Back to main guide](../README.md)

# Case Study: Abhivyakti 2026 — HTML Email

> **Abhivyakti 2026** — IIIT Nagpur's Annual Cultural Fest | 19 – 21 March 2026

This is a real-world case study showing how a promotional HTML email was built from scratch for a college cultural fest. It went through **23 iterations** over multiple phases — from initial wireframe to production-ready email — and demonstrates every concept covered in the [main guide](../README.md).

Use this as a reference for what a full email development workflow looks like in practice.

---

## 📂 Folder Structure

```
Case Study - Abhivyakti 2026/
├── README.md                  ← You are here
├── Final-Email.html           ← ✅ Production-ready final email
├── Checklist.md               ← Pre-send QA checklist
├── Content.txt                ← Finalized email copy (desktop + mobile)
├── Tips.md                    ← Tips for importing, sending & creating HTML mails
├── Desktop-Wireframe.md       ← Desktop layout wireframe
├── Mobile-Wireframe.md        ← Mobile layout wireframe
├── Email-Iterations/
│   └── mail1.html → mail23.html  ← All 23 iterative versions
├── Reference-Designs/
│   └── Event Posters/         ← Visual inspiration & poster assets
├── Feedback-Images/           ← Screenshots / feedback from reviews
└── More-Images/               ← Additional design assets
```

> **Note:** For a step-by-step tutorial on building HTML emails from scratch, see the [Getting Started guide](../Guide/01-Getting-Started.md). For common mistakes and email client support details, see the full [Guide](../Guide/).

---

## 🎨 Design System

| Element           | Value                                      |
| ----------------- | ------------------------------------------ |
| **Background**    | `#5A0F14` (deep maroon)                    |
| **Panel**         | `#8B1E24` (lighter maroon)                 |
| **Gold Accent**   | `#E7C27D` (muted gold)                     |
| **Button Accent** | `#F5C945` (bright gold)                    |
| **Body Text**     | `#F6E6C3` (warm cream)                     |
| **Dark / Footer** | `#3D0A0D` (near-black maroon)              |
| **Heading Font**  | Georgia, 'Times New Roman', serif          |
| **Body Font**     | Arial, Helvetica, sans-serif               |
| **Max Width**     | 600px                                      |

---

## 🔁 Version History & Project Timeline

The email went through **23 iterations** (mail1.html → mail23.html). Below is a rough timeline of what was needed at each stage, what problems came up, and how they were solved.

---

### Phase 1 — Getting Started (mail1 – mail2)

**What was needed:** A promotional HTML email for Abhivyakti 2026 — IIIT Nagpur's Annual Cultural Fest (19–21 March 2026). Content was ready in `Content.txt`, reference designs and event posters were provided, and wireframes for desktop and mobile layouts were drafted.

| Version | What Happened |
|---|---|
| **mail1** | First draft. Set up the table-based HTML structure, added all sections (hero, events, passes, how-to-register, footer), applied the maroon + gold color scheme from the reference designs. Used placeholder/reference images. |
| **mail2** | Content refinements, basic styling fixes, layout adjustments based on initial review. |

**Key decisions made early:**
- Table-based layout (for email client compatibility)
- 600px max-width container
- Color palette: `#5A0F14` maroon bg, `#F5C945` gold buttons, `#F6E6C3` cream text
- Georgia/serif for headings, Arial/sans-serif for body

---

### Phase 2 — Real Images & Visual Polish (mail3 – mail8)

**What was needed:** Replace placeholder images with actual hosted assets (uploaded to imgbb.com). Integrate the circus/carnival theme visuals from the design team.

| Version | What Happened |
|---|---|
| **mail3** | Started integrating real images — banner, logo, seal |
| **mail4** | More asset integration, layout adjustments for image sizing |
| **mail5** | Visual polish — spacing, padding, typography tweaks |
| **mail6** | Further image refinements, asset alignment fixes |
| **mail7** | Added more design assets (prize pool graphic, ornaments) |
| **mail8** | Visual polish pass — consistent styling across all sections |

**Challenges in this phase:**
- Images needed to be hosted online (imgbb.com) since email clients don't support local files
- Getting image sizes right across different email clients
- Balancing visual richness with email file size (images should be < 300KB each)

---

### Phase 3 — Mobile & Dark Mode (mail9 – mail12)

**What was needed:** The email looked good on desktop but was broken on mobile. Also needed dark mode support for users with dark theme email clients.

| Version | What Happened |
|---|---|
| **mail9** | Added `@media (max-width: 620px)` responsive rules — stacking columns, adjusting font sizes |
| **mail10** | Fixed mobile button sizing (full-width CTAs on mobile) |
| **mail11** | Dark mode support — added `color-scheme` meta tags, `@media (prefers-color-scheme: dark)` overrides |
| **mail12** | Mobile + dark mode polish — tested and fixed edge cases |

**Key responsive classes created:**
- `.mobile-stack` — Stack side-by-side columns vertically
- `.mobile-hide` — Hide decorative elements on mobile
- `.mobile-pad` — Add safe padding on small screens
- `.mobile-btn` — Full-width buttons on mobile

---

### Phase 4 — Character Assets & UX (mail13 – mail16)

**What was needed:** Add the circus character illustrations (girl, magician, ringmaster) to the email body. Add a logo bar. General UX improvements.

| Version | What Happened |
|---|---|
| **mail13** | Added IIIT Nagpur golden logo to the hero section |
| **mail14** | Integrated circus character assets — girl, magician |
| **mail15** | Added ringmaster (flipped), positioned characters alongside intro text |
| **mail16** | Logo bars, final character placement tweaks, UX improvements to pass cards and event grid |

**Assets added in this phase (all hosted on ibb.co):**
- Girl character (`Girl-Asset.png`)
- Magician (`Magician-Alone.png`)
- Ringmaster flipped (`Ring-Master-Alone-Flipped.png`)
- IIIT Nagpur golden logo (`iiitn-logo-golden.png`)
- Top center ornament (`Top-Center-Asset-High-Quality.png`)
- AB'26 golden icon (`AB-26-Plain-Icon-Golden.png`)

---

### Phase 5 — Asset Refinements (mail17 – mail18)

**What was needed:** Updated banner design from the design team, prize pool asset refresh.

| Version | What Happened |
|---|---|
| **mail17** | Swapped in updated banner (`AB-26-Updated-Banner.png`) |
| **mail18** | Updated prize pool asset (`Prize-Pool-asset-updated-2.png`), final visual alignment |

---

### Phase 6 — Layout & Content Changes (mail19 – mail21)

**What was needed:** The callout box ("Pro Shows, Pro Nights...") was stuck inside the left text column — needed to be centered as its own full-width row. Also needed several text/button changes and mobile sizing fixes.

| Version | What Happened |
|---|---|
| **mail19** | Pulled the callout box out of the left column and centered it as a full-width row (but was based on an older file accidentally) |
| **mail20** | Same callout box centering fix, correctly based on mail18 |
| **mail21** | **6 changes in one go:** (1) "Get Your Pass" → "Register Now" everywhere, (2) Removed the "IIIT Nagpur's Cultural Fest" h1, (3) Removed contact email/phone from certain sections, (4) "Register" → "Get Participation Pass" on pass cards, (5) Equal-size pass cards on mobile (`max-width: 280px; margin: 0 auto`), (6) Events grid — 2 columns on desktop, 1 column on mobile |

**Manual edits after mail21 (done outside AI):**
- Commented out primary CTA in final section
- Changed tagline to "Will you be in the crowd, or in the spotlight?"
- Changed phone number to 8602527698
- Updated the IMPORTANT warning text

---

### Phase 7 — Gmail Forwarding Fixes (mail22)

**What was needed:** When the email was forwarded within Gmail, the entire body collapsed under "..." (a known Gmail behavior with forwarded HTML emails).

| Version | What Happened |
|---|---|
| **mail22** | **4 Gmail-safe fixes:** (1) Updated preheader text format, (2) Added "View in browser" header row at the top, (3) Removed commented-out HTML blocks (Gmail can choke on large HTML comments), (4) Cleaned up leftover commented-out code |

**Manual edit after mail22:**
- Changed "student pass" → "IIITN pass" in the IMPORTANT warning section

---

### Phase 8 — Preheader Optimization (mail23)

**What was needed:** Better Gmail inbox preview text. The old preheader was generic — wanted something punchier that would show up well in the inbox list.

| Version | What Happened |
|---|---|
| **mail23** | Replaced preheader text with: *"25+ events, pro shows, and prizes — get ready for the biggest fest on campus."* Added invisible `&nbsp;&zwnj;` padding div to prevent Gmail from pulling random body text into the preview. Added `mso-hide:all; font-size:1px; line-height:1px;` for better Outlook compatibility. |

---

### Summary of What Was Needed at Each Stage

| Stage | Problem / Need | Solution |
|---|---|---|
| **Content** | Get email copy ready | Used ChatGPT to draft, refined manually in `Content.txt` |
| **Structure** | Email clients don't support modern CSS | Table-based layout, inline CSS, 600px container |
| **Images** | Can't use local images in email | Hosted on imgbb.com, used direct URLs |
| **Mobile** | Email broken on phones | `@media` queries, `.mobile-stack`, full-width buttons |
| **Dark mode** | Looked bad in dark theme clients | `color-scheme` meta + `prefers-color-scheme` overrides |
| **Characters** | Needed circus theme visuals | Positioned girl/magician/ringmaster alongside text columns |
| **Gmail** | Forwarded email collapsed under "..." | Select-all-copy-paste workaround + clean HTML structure |
| **Preview text** | Generic inbox preview | Custom preheader + invisible padding to block body text bleed |
| **Iteration** | Never perfect on first try | 23 versions, each reviewed and improved |

> **Key takeaway:** HTML email development is an iterative process. Expect to go through many versions. Test on real devices and email clients after each major change.

---

## 📚 Files in This Case Study

- [Final-Email.html](Final-Email.html) — The production-ready final email
- [Tips.md](Tips.md) — Practical tips for importing, sending, and creating HTML mails
- [Checklist.md](Checklist.md) — Pre-send QA checklist
- [Content.txt](Content.txt) — Finalized email copy
- [Desktop-Wireframe.md](Desktop-Wireframe.md) — Desktop layout plan
- [Mobile-Wireframe.md](Mobile-Wireframe.md) — Mobile layout plan
- [Email-Iterations/](Email-Iterations/) — All 23 iterative versions

---

[← Back to main guide](../README.md)
