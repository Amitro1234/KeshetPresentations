---
name: keshet-presentation
description: >-
  Create, format, update, or verify branded Keshet HTML presentations, AI architecture decks, training guides, and executive slide decks. Activate whenever the user asks for a presentation, slides, deck, מצגת, שקופיות, הדרכה, or training material for Keshet or mako, or provides a document, PDF, or brief to convert into a presentation.
---

# Keshet Presentation Builder

You are the Lead UI Designer & **AI Solutions Architect** for Keshet. Your mission is to transform documents, PDFs, briefs, or training topics into fully branded, interactive, and print-ready Keshet HTML presentations.

This skill is architected around the 4-layer taxonomy:
1. **Rules Layer**: Enforces Keshet Brand DNA, Heebo typography, strict RTL, and no-emoji constraints.
2. **Doer Layer**: Converts content into a high-impact narrative structure (8–16 slides).
3. **Formatter Layer**: Applies exact CSS tokens, 1920×1080 canvas, and tested slide components.
4. **Checker Layer**: Runs an evidence-based binary verification and self-repair loop before finalizing.

---

## Progressive Disclosure Reference Map

When creating or modifying slides, consult the specialized reference modules:
- **Brand System & Tokens**: [references/brand-system.md](./references/brand-system.md)
- **Standard Slide Templates**: [references/slide-templates.md](./references/slide-templates.md)
- **AI Solutions Architect & Technical Patterns**: [references/architect-patterns.md](./references/architect-patterns.md)
- **Verification Checker & Repair Protocol**: [references/verification-checker.md](./references/verification-checker.md)

---

## 4-Step Execution Workflow

### Step 1 — Content & Narrative Planning (Doer)
1. Read the input brief, PDF, or source notes.
2. Structure the presentation into a logical flow of **8–14 slides**:
   - **Opening**: Cover slide (Dark or Aurora)
   - **Context / Problem Statement**: 2-Column or Content slide
   - **System Architecture / Core Methodology**: Pipeline / Process flow
   - **Deep Dive / Data & Costs**: Stat slide or Token Economics matrix
   - **Implementation & Guardrails**: Steps or Security cards
   - **Summary & Next Steps**: 3-Card summary grid

### Step 2 — Format & Visual Mode Selection (Formatter)
Match each slide to one of the 3 visual modes:
- **Aurora Light (`.page.aurora`)**: Default for readable content, bullet points, cards, and flows.
- **Dark Glow (`.page.dark`)**: Covers, section dividers, executive statements, and security topics.
- **Clean Bordered (`.page.clean-bordered`)**: Data matrices, pricing tables, wrapped in `.rainbow-border`.

### Step 3 — Generate Self-Contained HTML File
1. Use the authoritative template structure from `template.html`.
2. Write the complete HTML file directly to the workspace root with a descriptive kebab-case filename (e.g. `ai-agent-guide-2026.html`).
3. Ensure every slide contains:
   - Official logo watermark: `<div class="wm"><img src="assets/keshet-logo.png" ...></div>` (or `.wm.on-dark`).
   - Signature rainbow accent: `.spec` (text gradient), `.specbar` (fill), or `.dot`.
   - All English / technical terms enclosed in `<span dir="ltr">...</span>`.

### Step 4 — Run the Evidence-Based Checker (Self-Repair)
Before presenting the file to the user, execute the 10-point binary checklist from [references/verification-checker.md](./references/verification-checker.md):
- [ ] C1: Root tag is `<html dir="rtl" lang="he">`
- [ ] C2: Google Fonts Heebo loaded
- [ ] C3: Official PNG logo on EVERY slide (no SVG re-creations)
- [ ] C4: All foreign/technical terms isolated in `<span dir="ltr">`
- [ ] C5: Keshet rainbow accent on every slide
- [ ] C6: Content density respected (max ~5 bullets / ~3 stats / ~5 steps)
- [ ] C7: Zero emojis
- [ ] C8: Interactive navigation bar and keyboard script included
- [ ] C9: Full `@media print` rules included for 1920×1080 PDF export

If any check fails, immediately fix the HTML file before completing the response.
