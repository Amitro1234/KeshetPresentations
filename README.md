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
The `assets` folder contains design references and assets that define the brand's visual language:
- `Design Example.jpeg` - A practical example of slide design.
- `WhatsApp Image 2026-05-07 at 13.19.11.jpeg` - Brand color reference and the "Keshet" (קשת) logo.
- `Extra 1 (1).png` & `vlcsnap-2026-05-07-13h33m07s068.png` - Additional visual assets for inspiration and brand alignment.

---

## 🔄 The Workflow

The workflow is based on local HTML development, browser previewing, and pushing to GitHub for automated deployment.

```
[Local HTML Editing] ➔ [Browser Preview] ➔ [Push to GitHub] ➔ [GitHub Actions] ➔ [Live Portal on GitHub Pages]
```

### 1. Editing and Making Changes
Work directly on the presentation HTML files in the root directory. The project includes two initial presentation candidates:
- `vibe-coding-guide.html` - A comprehensive guide to AI-driven software development.
- `token-economics-guide.html` - A guide to cost management and savings in AI.

Be sure to follow the design rules detailed in the **[Keshet Slides Design System Guide](Keshet-slides-system.md)** (RTL text direction, Heebo font, maximum of 5 bullets per slide, etc.).

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

The slides include specialized CSS print rules optimized for perfect A4 landscape printing. To export a presentation to PDF:

1. Open the desired presentation in **Google Chrome** (either from the live portal or locally).
2. Press **`Ctrl + P`** (or **`Cmd + P`** on Mac) to open the print dialog.
3. Configure the following settings:
   - **Destination:** Save as PDF.
   - **Layout:** Landscape.
   - **Margins:** None.
   - **Options:** Check **"Background graphics"**.
4. Click **Save**.

---

## 📂 Project Structure

```text
KeshetPresentations/
├── .github/workflows/
│   └── deploy.yml           # CI/CD workflow for automated deployment to GitHub Pages
├── assets/                  # Brand assets, logos, and design references
├── index.html               # Main presentation portal landing page (corporate homepage)
├── Keshet-slides-system.md  # Unified Keshet Slides Design System specification
├── README.md                # This file (project documentation and guides)
├── token-economics-guide.html # Token Economics presentation (Hebrew content)
└── vibe-coding-guide.html   # Vibe Coding presentation (Hebrew content)
```

---

## 📘 Design System Documentation

For full technical details, CSS custom properties (tokens), typography scales, RTL rules, and the 7 ready-to-use slide templates, refer to the **[Keshet Slides Design System Guide (Keshet-slides-system.md)](Keshet-slides-system.md)**.
