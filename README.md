# Keshet Presentations Portal

This is the official presentation system for **Keshet**. This project defines the design, structural, and technical standards for creating, storing, and sharing stunning, fully branded presentations across the organization.

The project allows you to work directly on clean HTML files, make changes, and share them easily via a corporate portal hosted on **GitHub Pages**, which is automatically updated with every code push.

---

## 🌟 The Keshet Brand DNA

The Keshet brand is characterized by rich colors, innovation, and dynamism. The system is designed so that every slide communicates the Keshet brand **even without a logo**, through strict adherence to brand colors, typography, and slide structures.

### 🎨 Three Visual Modes
Every slide in the system uses exactly one of the three following visual modes:
1. **Aurora Light:** Light, clean, and print-friendly slides designed for informative and textual content.
2. **Dark Glow:** Dark and dramatic slides with a subtle colored aura, designed for opening slides, security topics, or creating a strong visual impact.
3. **Clean Bordered:** Slides featuring a thin, elegant rainbow border, designed for comparisons, tables, data, and step-by-step content.

### 📁 Brand Assets Folder (`assets/`)
The `assets` folder contains the brand marks and design references that define the visual language:
- `keshet-logo.png` - **The official Keshet logo** (transparent rainbow squircle with "קשת"). Every slide references this file in its header.
- `Design Example.jpeg` - A practical example of slide design.
- `WhatsApp Image 2026-05-07 at 13.19.11.jpeg` - Brand color reference.
- `Extra 1 (1).png` & `vlcsnap-2026-05-07-13h33m07s068.png` - Additional visual assets for inspiration and brand alignment.

---

## 🔄 The Workflow

The workflow is based on local HTML development, browser previewing, and pushing to GitHub for automated deployment.

```
[Copy template.html] ➔ [Local HTML Editing] ➔ [Browser Preview] ➔ [Push to GitHub] ➔ [GitHub Actions] ➔ [Live Portal on GitHub Pages]
```

### 1. Start a New Presentation from the Template
**Always start by copying [`template.html`](template.html)** and renaming it (e.g. `my-new-guide.html`). The template is a ready-made, fully-branded 1920×1080 deck that already includes the Keshet logo header, the three visual modes, the floating slide navigation (buttons, dots, counter, keyboard + swipe), responsive scaling, and the print-to-PDF rules.

To build your deck, just replace the example slides inside `<div id="deck">` with your own `<div class="page ...">` blocks — **leave the CSS, the nav bar, and the `<script>` untouched** so every presentation speaks the same visual language. The navigation updates automatically based on how many slides you add.

The repo also ships two reference presentations:
- `token-economics-guide.html` - The canonical reference deck (built on this exact system).
- `vibe-coding-guide.html` - A guide to AI-driven software development.

Follow the design rules in the **[Keshet Slides Design System Guide](Keshet-slides-system.md)** — see **Section 12 (Production Deck System)** for the authoritative list of classes and how to use the template (RTL text, Heebo font, one visual mode per slide, the rainbow brand token, max ~5 bullets per slide, etc.).

### 2. Local Preview
Simply open the HTML files (or `index.html`) directly in any modern browser (Chrome, Edge, Safari) to see your changes instantly.

### 3. Push to GitHub
When your changes are ready, push them to the remote GitHub repository:
[https://github.com/Amitro1234/KeshetPresentations](https://github.com/Amitro1234/KeshetPresentations)

### 4. Automated Deployment (GitHub Pages)
On every push to the main branch (`main` or `master`), a **GitHub Actions** workflow automatically triggers, builds, and deploys the portal to **GitHub Pages**.
The result is a beautifully designed, interactive corporate presentation portal accessible to anyone in your organization on any device!

---

## 🚀 Setup Guide

If your local repository is not yet connected to GitHub, run the following commands in your terminal to initialize Git and push the code for the first time:

```bash
# 1. Initialize local repository
git init

# 2. Add all files (including assets and GitHub workflows)
git add .

# 3. Create the initial commit
git commit -m "Initial commit: Keshet Presentations Portal & Design System"

# 4. Set the main branch name
git branch -M main

# 5. Add the remote GitHub repository
git remote add origin https://github.com/Amitro1234/KeshetPresentations.git

# 6. Push the code and set upstream tracking
git push -u origin main
```

---

## 🖨️ Printing and Creating PDFs (Print to PDF)

Each deck includes a `@media print` block that turns every slide into a single 1920×1080 landscape page and hides the floating navigation bar. To export a presentation to PDF:

1. Open the desired presentation in **Google Chrome** (either from the live portal or locally).
2. Press **`Ctrl + P`** (or **`Cmd + P`** on Mac) to open the print dialog.
3. Configure the following settings:
   - **Destination:** Save as PDF.
   - **Layout:** Landscape.
   - **Margins:** None.
   - **Options:** Check **"Background graphics"**.
4. Click **Save**. You get one page per slide, in full brand color.

---

## 📂 Project Structure

```text
KeshetPresentations/
├── .github/workflows/
│   └── deploy.yml           # CI/CD workflow for automated deployment to GitHub Pages
├── assets/                  # Brand assets, logos, and design references
├── index.html               # Main presentation portal landing page (corporate homepage)
├── template.html            # ⭐ Generic starter — copy this to begin any new presentation
├── Keshet-slides-system.md  # Unified Keshet Slides Design System specification
├── README.md                # This file (project documentation and guides)
├── token-economics-guide.html # Token Economics presentation (reference deck, Hebrew content)
└── vibe-coding-guide.html   # Vibe Coding presentation (Hebrew content)
```

---

## 📘 Design System Documentation

For full technical details, CSS custom properties (tokens), typography scales, RTL rules, and slide templates, refer to the **[Keshet Slides Design System Guide (Keshet-slides-system.md)](Keshet-slides-system.md)**. Start with **Section 12 — Production Deck System**, which documents the exact classes used by `template.html` and every live presentation.
