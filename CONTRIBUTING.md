# Contributing

Thanks for your interest in improving this guide! Here's how to contribute.

---

## How to Contribute

1. **Fork** this repository
2. **Create a branch** for your change: `git checkout -b add-template-invoice`
3. **Make your changes** following the guidelines below
4. **Test** any HTML templates in a real email client (Gmail, Outlook)
5. **Open a Pull Request** with a clear description of what you changed and why

---

## What You Can Contribute

### 📖 Guide Improvements
- Fix errors or unclear explanations
- Add missing email client quirks or workarounds
- Update the compatibility matrix with new data
- Add new entries to the common mistakes page

### 📬 New Templates
- Add a new HTML email template to `Templates/`
- Must follow the template requirements below

### 🤖 New Prompts
- Add a new AI prompt to `Prompts/`
- Must follow the prompt format below

### 📚 Case Studies
- Share your own email project as a case study
- Create a subfolder under a new `Case Studies/` directory

### 🐛 Bug Fixes
- Fix broken links, typos, or formatting issues
- Fix rendering bugs in existing templates

---

## Template Requirements

All templates in `Templates/` must:

1. **Use table-based layout** — no flexbox, no grid, no `<div>` layouts
2. **Inline all critical CSS** — `<style>` block only for `@media` queries and dark mode
3. **Max width 600px** container
4. **Include responsive styles** — `@media (max-width: 620px)` breakpoint
5. **Include dark mode** — `@media (prefers-color-scheme: dark)` overrides
6. **Use `role="presentation"`** on all layout tables
7. **Set `cellpadding="0"` and `cellspacing="0"`** on all tables
8. **Include descriptive `alt` text** on all images
9. **Use web-safe fonts** — Arial/Helvetica/sans-serif for body, Georgia/serif for headings
10. **Include HTML comments** explaining each section
11. **Use neutral/brandable colors** — no project-specific branding
12. **Use placeholder images** from `placehold.co` (not external services that may go down)
13. **Keep file size under 80KB** to avoid Gmail clipping (102KB limit)
14. **Include a preheader** with invisible padding

### Template file naming
Use lowercase, hyphenated names: `invoice-receipt.html`, `event-reminder.html`

---

## Prompt Format

All prompts in `Prompts/` must follow this structure:

```markdown
# Prompt: [Descriptive Title]

> One-line description of when to use this prompt.

---

## Prompt

\```
[The actual prompt text the user copies into their AI tool]
\```

---

## Tips (optional)

- Additional context or usage notes
```

### Prompt file naming
Use numbered, hyphenated names: `15-invoice-template.md`, `16-accessibility-audit.md`

---

## Guide Writing Style

- **Be direct** — state facts, skip filler
- **Show code** — every concept should have a code example
- **Use tables** for comparison/reference data
- **Use ✅/❌/⚠️** for at-a-glance status indicators
- **Link to other guide pages** where relevant
- **Avoid jargon** without explaining it (or link to Glossary)

---

## Commit Messages

Use clear, descriptive commit messages:
- `Add invoice template`
- `Fix Outlook button rendering in event-promo template`
- `Add Samsung Mail to compatibility matrix`
- `Update common mistakes: add Gmail clipping entry`

---

## Questions?

Open an issue if you're unsure about anything. We're happy to help!
