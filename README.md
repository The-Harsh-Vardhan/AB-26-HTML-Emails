# HTML Email Guide — Zero to Hero

> Learn to build production-ready HTML emails from scratch. Table-based layouts, responsive design, dark mode, cross-client compatibility — everything you need, all in one place.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## Why This Guide?

HTML emails are **not** like web pages. Email clients strip out modern CSS, ignore JavaScript, and render layouts with engines from 2007. Building an email that looks great everywhere — Gmail, Outlook, Apple Mail, Yahoo, mobile — requires specific techniques that most web developers never learn.

This guide covers all of it: from your first `<table>` to bulletproof buttons, responsive stacking, dark mode, and avoiding Gmail's 102KB clipping limit.

---

## 📂 Repository Structure

```
├── Guide/                             ← Learn HTML email development
│   ├── 01-Getting-Started.md          ← Build your first email (step-by-step)
│   ├── 02-Email-Client-Support.md     ← What works where (compatibility matrix)
│   ├── 03-Common-Mistakes.md          ← 20 pitfalls and how to fix them
│   ├── 04-Design-System.md            ← Build a reusable color/font system
│   ├── 05-Testing-Your-Email.md       ← Tools and workflow for testing
│   └── Glossary.md                    ← Key terms defined
│
├── Templates/                         ← Ready-to-use starter templates
│   ├── event-promo.html               ← Event / fest promotion
│   ├── newsletter.html                ← Multi-article newsletter
│   ├── announcement.html              ← Simple announcement (beginner-friendly)
│   └── welcome-email.html             ← Welcome / onboarding email
│
├── Prompts/                           ← AI prompts for Copilot / ChatGPT / Claude
│   ├── 00-initial-brief.md            ← Example: full project brief
│   ├── 01-html-email-boilerplate.md   ← Generate an email skeleton
│   ├── 02-responsive-mobile-email.md  ← Add mobile responsiveness
│   ├── 03-dark-mode-support.md        ← Add dark mode
│   ├── 04-cta-buttons.md              ← Create bulletproof buttons
│   ├── 05-promotional-event-email.md  ← Build a full promo email
│   ├── 06-image-hosting-and-optimization.md
│   ├── 07-pricing-pass-cards.md       ← Pricing / pass card layouts
│   ├── 08-events-features-grid.md     ← 2-col grid layouts
│   ├── 09-email-testing-debugging.md  ← Debug rendering issues
│   ├── 10-preheader-and-subject-line.md
│   ├── 11-convert-design-to-email.md  ← Design → code conversion
│   ├── 12-gmail-outlook-fixes.md      ← Client-specific fixes
│   ├── 13-footer-section.md           ← Email footer
│   └── 14-refine-email-copy.md        ← Improve email copy
│
└── Case Study - Abhivyakti 2026/      ← Real-world example (23 iterations)
    ├── README.md                       ← Project timeline & version history
    ├── Final-Email.html                ← Production-ready email
    ├── Checklist.md                    ← Pre-send QA checklist
    ├── Email-Iterations/               ← mail1.html → mail23.html
    └── ...
```

---

## 🚀 Quick Start

### 1. Learn the fundamentals
Read [Guide/01-Getting-Started.md](Guide/01-Getting-Started.md) — build your first HTML email step-by-step.

### 2. Pick a template
Grab a starter template from [Templates/](Templates/) and customize it with your content, colors, and images.

### 3. Use AI to accelerate
Copy a prompt from [Prompts/](Prompts/) into Copilot, ChatGPT, or Claude to generate specific email components.

### 4. Test & send
Follow [Guide/05-Testing-Your-Email.md](Guide/05-Testing-Your-Email.md) to verify your email works everywhere.

---

## 📐 HTML Email Rules at a Glance

| ✅ Supported                  | ❌ Not Supported              |
| ----------------------------- | ----------------------------- |
| `<table>` based layouts       | Flexbox / CSS Grid            |
| Inline CSS (`style="…"`)      | External stylesheets (mostly) |
| Basic `@media` queries        | JavaScript                    |
| `<img>` with hosted URLs      | Local / relative image paths  |
| Simple `background-color`     | Complex CSS animations        |
| `border-radius` (most clients)| `position: absolute/fixed`    |

---

## 🎨 Example Design System

Use this as a starting point — replace with your brand colors:

| Element           | Value                                      |
| ----------------- | ------------------------------------------ |
| **Background**    | `#F5F5F5` (light gray)                     |
| **Container**     | `#FFFFFF` (white)                          |
| **Primary**       | `#2563EB` (blue)                           |
| **Accent**        | `#F59E0B` (amber)                          |
| **Body Text**     | `#1F2937` (dark gray)                      |
| **Muted Text**    | `#6B7280` (gray)                           |
| **Heading Font**  | Georgia, 'Times New Roman', serif          |
| **Body Font**     | Arial, Helvetica, sans-serif               |
| **Max Width**     | 600px                                      |

See [Guide/04-Design-System.md](Guide/04-Design-System.md) for how to build your own.

---

## 📖 Guide Contents

| # | Page | What You'll Learn |
|---|------|-------------------|
| 1 | [Getting Started](Guide/01-Getting-Started.md) | Build your first HTML email from scratch in 8 steps |
| 2 | [Email Client Support](Guide/02-Email-Client-Support.md) | What CSS/HTML works in which email client |
| 3 | [Common Mistakes](Guide/03-Common-Mistakes.md) | 20 pitfalls that break emails — and how to fix them |
| 4 | [Design System](Guide/04-Design-System.md) | Create a reusable color, font, and spacing system |
| 5 | [Testing Your Email](Guide/05-Testing-Your-Email.md) | Tools, workflow, and checklist for email QA |
| — | [Glossary](Guide/Glossary.md) | Key email development terms defined |

---

## 📬 Templates

| Template | Best For | Complexity |
|----------|----------|------------|
| [announcement.html](Templates/announcement.html) | Product launch, update, single message | ⭐ Beginner |
| [welcome-email.html](Templates/welcome-email.html) | User onboarding, first-touch emails | ⭐⭐ Intermediate |
| [newsletter.html](Templates/newsletter.html) | Weekly/monthly content roundup | ⭐⭐ Intermediate |
| [event-promo.html](Templates/event-promo.html) | Event promotion, fest announcements | ⭐⭐⭐ Advanced |

All templates include: responsive mobile layout, dark mode support, accessible markup, and inline comments explaining every section.

---

## 🤖 AI Prompts

The [Prompts/](Prompts/) folder contains 15 copy-paste prompts for AI tools (GitHub Copilot, ChatGPT, Claude). Each prompt is designed to generate a specific email component or solve a specific problem.

Use them to:
- Generate a complete email from a brief
- Add responsiveness to an existing email
- Create bulletproof CTA buttons
- Debug client-specific rendering issues
- Write compelling subject lines and preheader text

---

## 📚 Case Study: Abhivyakti 2026

The [Case Study](Case%20Study%20-%20Abhivyakti%202026/) folder contains a real-world example of this guide in action — a promotional HTML email for IIIT Nagpur's cultural fest that went through **23 iterations**. It includes:

- Every version from first draft to final production email
- Design references, wireframes, and feedback screenshots
- The full project timeline showing what problems came up and how they were solved
- A pre-send QA checklist

It's a transparent look at the iterative process of building a real HTML email.

---

## 🔗 External Resources

- [Can I Email](https://www.caniemail.com/) — Check CSS/HTML support across email clients
- [Litmus](https://www.litmus.com/) — Email testing and previews
- [Email on Acid](https://www.emailonacid.com/) — Cross-client rendering tests
- [MJML](https://mjml.io/) — Framework that compiles to email-safe HTML
- [HTML Email Check](https://www.htmlemailcheck.com/) — Validate your email HTML
- [imgbb](https://imgbb.com/) — Free image hosting for email assets
- [PutsMail](https://putsmail.com/) — Send test HTML emails to yourself

---

## 🤝 Contributing

Contributions are welcome! Whether it's fixing a typo, adding a new template, improving a guide page, or sharing a prompt — check out [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).
