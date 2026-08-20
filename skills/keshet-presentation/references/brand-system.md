# Keshet Brand & Design System Reference

This document is the authoritative design specification for Keshet slide decks and technical presentations.

---

## 1. Brand DNA & Palette

The Keshet brand identity is centered around its signature 7-color vibrant rainbow gradient paired with deep ink-navy backgrounds and clean frosted glass surfaces.

### 1.1 CSS Variables & Palette Tokens
```css
:root {
  /* Signature 7-Color Keshet Rainbow */
  --ks: linear-gradient(135deg, #E4002B 0%, #FF6D00 15%, #FFD100 30%, #00A651 50%, #00B4D8 70%, #0057B8 85%, #7B2D8E 100%);
  
  /* Brand Core Colors */
  --c-red: #E4002B;
  --c-orange: #FF6D00;
  --c-yellow: #FFD100;
  --c-green: #00A651;
  --c-cyan: #00B4D8;
  --c-blue: #0057B8;
  --c-purple: #7B2D8E;

  /* Neutrals & Surfaces */
  --c-ink: #0A1930;
  --c-ink-dark: #061020;
  --c-muted: #5A6A7A;
  --c-bg-light: #FBFAF8;
  --c-surface-clean: #FAFAF8;

  /* Typography */
  --font: 'Heebo', 'Arial Hebrew', Arial, sans-serif;
}
```

---

## 2. The Three Visual Modes

Every slide (`.page`) must use **exactly one** of these three visual modes:

| Mode | CSS Class | Characteristics & Best For |
|---|---|---|
| **Aurora Light** | `.page.aurora` | Default mode for 80% of slides. Light frosted mesh gradient, maximum legibility for reading, bullets, steps, cards, and diagrams. |
| **Dark Glow** | `.page.dark` | Deep navy base with vibrant cyan/purple/red radial glow. Best for: Covers, section breaks, dramatic statements, executive summaries, security topics. |
| **Clean Bordered** | `.page.clean-bordered` | Wrapped in `.rainbow-border` (3px rainbow frame). Crisp off-white canvas. Best for: Data tables, side-by-side technical comparisons, detailed matrices. |

### Background Gradients Implementation
```css
/* Aurora Light */
.aurora {
  background: 
    radial-gradient(1200px 820px at 10% 6%, rgba(228,0,43,.14), transparent 58%),
    radial-gradient(1150px 900px at 92% 10%, rgba(255,209,0,.20), transparent 58%),
    radial-gradient(1250px 950px at 84% 94%, rgba(0,180,216,.20), transparent 60%),
    radial-gradient(1150px 900px at 12% 96%, rgba(123,45,142,.15), transparent 60%),
    radial-gradient(900px 720px at 50% 52%, rgba(0,166,81,.10), transparent 64%),
    linear-gradient(160deg, #FBFAF8, #F2EFE9);
}

/* Dark Glow */
.dark {
  background: 
    radial-gradient(1200px 900px at 82% 10%, rgba(0,180,216,.30), transparent 55%),
    radial-gradient(1100px 900px at 12% 92%, rgba(123,45,142,.30), transparent 58%),
    radial-gradient(1000px 800px at 50% 50%, rgba(0,87,184,.18), transparent 60%),
    linear-gradient(150deg, #0A1930, #0f2340);
}

/* Clean Bordered */
.clean-bordered { background: #FAFAF8; }
.rainbow-border { background: var(--ks); padding: 3px; border-radius: 24px; overflow: hidden; }
```

---

## 3. Typography & RTL Principles

1. **Google Fonts Heebo**: Always loaded with weights 300, 400, 500, 600, 700, 800, 900.
2. **Text Hierarchy**:
   - Eyebrow Pill: `.eyebrow` (21px, bold, rounded capsule with `.dot`). Add `.on-dark` for dark slides.
   - Main Title: `.title` (70px on content slides, up to 104px on covers, weight 900). Add `.on-dark` for dark slides.
   - Subtitle: `.sub` (29px–33px, weight 500, muted color `#5A6A7A` or `rgba(255,255,255,0.82)` on dark).
   - Card Headings: 24px–32px, weight 800.
   - Body & Points: 20px–26px, weight 500–600.
3. **Strict RTL & Foreign Terms Rule**:
   - Root: `<html dir="rtl" lang="he">`.
   - Every single English term, acronym, code snippet, or model name MUST be enclosed in `<span dir="ltr">...</span>` (e.g. `<span dir="ltr">Claude Sonnet 3.7</span>`, `<span dir="ltr">RAG Pipeline</span>`, `<span dir="ltr">Cost per 1M Tokens</span>`).

---

## 4. UI Component Library

- **Logo Header Watermark (`.wm`)**:
  Positioned top-left (104px from left, 52px from top). Always contains `assets/keshet-logo.png` with height 56px and drop shadow.
- **Glass Card (`.glass`)**:
  Frosted translucent white background (`rgba(255,255,255,0.6)`), rounded 20px, light border and elevation shadow.
- **Ink Card (`.inkcard`)**:
  Deep dark navy gradient card (`#0A1930` to `#13294c`) for heavy emphasis or contrast.
- **Rainbow Text Highlight (`.spec`)**:
  Text with gradient clipping to apply the 7-color Keshet rainbow.
- **Rainbow Accent Bar (`.specbar`)**:
  Full gradient fill for separator bars, progress lines, or numbered discs.
- **Takeaway Strip (`.take`)**:
  Full-width bottom summary banner in deep navy with key insights highlighted in `<span class="hi">...</span>` (bright yellow `#FFD100`).
- **Number Chip (`.numchip`)**:
  56px circle with bold step number. Colors follow step order: 1=Red, 2=Orange, 3=Yellow, 4=Green, 5=Cyan.

---

## 5. Known Traps & Failure Modes (Hard-Won Lessons)

| Failure Mode | The Trap | Required Behavior |
|---|---|---|
| **Logo as SVG / text** | Attempting to draw the Keshet logo using SVG shapes or plain text. | ALWAYS use `<img src="assets/keshet-logo.png" ...>` in `.wm`. |
| **BiDi Punctuation Flip** | Putting punctuation or parentheses near English terms without LTR isolation. | Enclose entire term and related punctuation in `<span dir="ltr">...</span>`. |
| **Slide Content Overflow** | Trying to pack 7+ bullets or 5 dense cards into one slide. | Hard limits: Max ~5 bullets, ~3 stats, ~5 steps. Split over 2 slides if needed. |
| **Using Emojis** | Adding emojis (🚀, 💡, ⚡) to bullets or titles. | Strict prohibition. Use Keshet dots, numbered chips, or `.spec` highlights. |
| **Arbitrary Colors** | Introducing external hex colors (e.g. random blues/purples). | Only use tokens from `--ks` and the defined Keshet palette. |
| **Missing Rainbow DNA** | Creating a plain gray/white slide without any rainbow touch. | Every slide must contain `--ks` via `.spec`, `.specbar`, `.dot`, or borders. |

## 6. Visuals & Imagery Guidelines (Builders & Developers Focus)

When embedding or generating images:
1. **Eye-Level Simplicity (בגובה העיניים)**: Suitable for both technical developers and non-technical builders / product managers.
2. **Intuitive Visual Metaphors**: Use friendly 3D building blocks, clean workspace folders, and simple checklists rather than dense circuit schematics or overwhelming wiring diagrams.
3. **Proportional Integration**:
   - Container: Use `<div class="media-card">` with `object-fit: contain` or `object-fit: cover`.
   - Resolution: 16:9 aspect ratio, clean padding, ensuring no distortion or slide overflow.
