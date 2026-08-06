# Code Review Fixes — KeshetPresentations Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Apply all 6 MAJOR and 2 MINOR findings from the 2026-08-05 code review to harden the KeshetPresentations portal and skill.

**Architecture:** Static HTML presentation system deployed to GitHub Pages via GitHub Actions. No build step, no package manager — all fixes are direct edits to HTML, Markdown, and YAML files. One skill file drives AI-assisted content creation.

**Tech Stack:** Vanilla HTML/CSS/JS, GitHub Actions, Markdown skill file (Claude / Cursor Cowork compatible).

## Global Constraints

- All HTML must remain single-file, self-contained (no external JS/CSS beyond Google Fonts).
- RTL Hebrew direction (`<html dir="rtl" lang="he">`) must be preserved on all presentation files.
- The CSS design system (1920×1080 canvas, aurora/dark modes, rainbow token) must not change.
- `template.html` is the canonical starting point — any structural fix here propagates to all future decks automatically.
- `assets/keshet-logo.png` path must remain unchanged (referenced by every slide).
- Do not change slide content in `vibe-coding-guide.html` or `token-economics-guide.html`.

---

### Task 1: Scope GitHub Pages artifact — stop publishing internal files

**Priority:** Highest — internal docs are currently live on the public portal URL.

**Files:**
- Modify: `.github/workflows/deploy.yml`

**Interfaces:**
- Produces: a `_site/` staging directory containing only `*.html` + `assets/`

- [ ] **Step 1: Open `.github/workflows/deploy.yml`**

The current file has `path: '.'` which uploads everything — including
`docs/session-insights/`, `skills/`, `cursor-prompt-*.md`, etc.

- [ ] **Step 2: Replace the upload step with a build + scoped upload**

Find this block (lines ~27-33):
```yaml
      - name: Upload Pages Artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: '.'
```

Replace it with:
```yaml
      - name: Prepare deploy artifact
        run: |
          mkdir -p _site
          cp *.html _site/
          cp -r assets _site/

      - name: Upload Pages Artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: '_site'
```

- [ ] **Step 3: Verify the full updated workflow looks like this**

```yaml
name: Deploy Keshet Presentations to GitHub Pages

on:
  push:
    branches:
      - main
      - master

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: false

jobs:
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Repository
        uses: actions/checkout@v4

      - name: Setup Pages
        uses: actions/configure-pages@v5

      - name: Prepare deploy artifact
        run: |
          mkdir -p _site
          cp *.html _site/
          cp -r assets _site/

      - name: Upload Pages Artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: '_site'

      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

- [ ] **Step 4: Commit**

```bash
git add .github/workflows/deploy.yml
git commit -m "fix: scope GitHub Pages artifact to html+assets only"
```

---

### Task 2: Fix `template.html` — add missing `<title>` and viewport meta

**Files:**
- Modify: `template.html` (lines 28-34, the `<head>` block)

**Interfaces:**
- Produces: a template `<head>` that all future decks inherit correctly

- [ ] **Step 1: Open `template.html` and locate the `<head>` block**

It currently starts at line 28 and looks like:
```html
<html dir="rtl" lang="he"><head>
<meta charset="utf-8">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Heebo:...&display=swap" rel="stylesheet">

<style>
```

There is no `<title>` tag and no `<meta name="viewport">`.

- [ ] **Step 2: Replace the opening `<head>` block**

Find:
```html
<html dir="rtl" lang="he"><head>
<meta charset="utf-8">
<link rel="preconnect" href="https://fonts.googleapis.com">
```

Replace with:
```html
<html dir="rtl" lang="he"><head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>שם המצגת — קשת</title><!-- ← שנה לשם המצגת -->
<link rel="preconnect" href="https://fonts.googleapis.com">
```

- [ ] **Step 3: Verify the head block now reads**

```html
<html dir="rtl" lang="he"><head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>שם המצגת — קשת</title><!-- ← שנה לשם המצגת -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Heebo:wght@300;400;500;600;700;800;900&display=swap" rel="stylesheet">

<style>
```

- [ ] **Step 4: Commit**

```bash
git add template.html
git commit -m "fix: add missing title and viewport meta to template.html"
```

---

### Task 3: Fix the SKILL.md — remove Cowork-only tool call, fix hardcoded path

**Files:**
- Modify: `skills/keshet-presentation/SKILL.md`

**Interfaces:**
- Produces: a skill that works correctly in Claude Code CLI (not just Cowork)

- [ ] **Step 1: Fix the hardcoded save path in Section 3 and Section 9**

In Section 3 ("Build the HTML file"), find:
```
Single self-contained HTML file. Save it to `C:\Users\amit.rosen\KeshetPresentations\` with a descriptive kebab-case name (e.g. `ai-strategy-2026.html`).
```

Replace with:
```
Single self-contained HTML file. Save it to the current working directory (the KeshetPresentations repo root) with a descriptive kebab-case name (e.g. `ai-strategy-2026.html`). The Write tool resolves the path automatically — use the filename only, no absolute path prefix.
```

- [ ] **Step 2: Fix the same path in Section 9, step 4**

Find:
```
4. **Save to workspace** — `C:\Users\amit.rosen\KeshetPresentations\<name>.html`
```

Replace with:
```
4. **Save to workspace** — Write the file as `<name>.html` in the current working directory (repo root). Do not use an absolute path.
```

- [ ] **Step 3: Fix the `mcp__cowork__present_files` call in the output checklist (Section 8)**

Find:
```
- [ ] Present the file to the user with `mcp__cowork__present_files`
```

Replace with:
```
- [ ] Present the file to the user — call `SendUserFile` with the saved file path so the user gets a clickable card in the chat.
```

- [ ] **Step 4: Fix the same call in Section 9, step 5**

Find:
```
5. **Present the file** — call `mcp__cowork__present_files` so the user gets a clickable card.
```

Replace with:
```
5. **Present the file** — call `SendUserFile` with the saved file path so the user gets a clickable card in the chat.
```

- [ ] **Step 5: Add the viewport meta to the required HTML shell in Section 3**

In the "Required HTML shell" code block, find:
```html
<meta charset="utf-8">
<link rel="preconnect" href="https://fonts.googleapis.com">
```

Replace with:
```html
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title><!-- שם המצגת — קשת --></title>
<link rel="preconnect" href="https://fonts.googleapis.com">
```

- [ ] **Step 6: Add viewport + title to the Section 8 output checklist**

After the existing line:
```
- [ ] `<html dir="rtl" lang="he">`
```

Add:
```
- [ ] `<meta name="viewport" content="width=device-width, initial-scale=1.0">` present
- [ ] `<title>` tag set to the presentation's name
```

- [ ] **Step 7: Commit**

```bash
git add skills/keshet-presentation/SKILL.md
git commit -m "fix: replace cowork tool with SendUserFile, remove hardcoded path, add viewport to skill template"
```

---

### Task 4: Resolve Mode 3 inconsistency — add "Clean Bordered" to the skill

**Context:** `Keshet-slides-system.md` documents 3 visual modes (Aurora, Dark Glow, Clean Bordered)
but `SKILL.md` only implements 2. This task adds the missing "Clean Bordered" CSS + slide snippet
to the skill so it matches the system spec.

**Files:**
- Modify: `skills/keshet-presentation/SKILL.md`
- Modify: `template.html` (add the CSS class and a demo slide)

- [ ] **Step 1: Add the `.clean-bordered` CSS class to Section 4 of SKILL.md**

In Section 4 (Full CSS), find the `.dark { ... }` rule line and add after it:
```css
.clean-bordered { background: #FAFAF8; }
/* Usage: wrap .page.clean-bordered inside a .rainbow-border div */
.rainbow-border { background: var(--ks); padding: 3px; border-radius: 24px; overflow: hidden; }
```

- [ ] **Step 2: Add the Clean Bordered snippet to Section 6 of SKILL.md**

After the "### Closing grid / summary" section, add:

````markdown
### Clean Bordered slide (for comparisons, tables, step-by-step)

```html
<!-- Outer rainbow border wrapper — required for this mode -->
<div class="rainbow-border" style="position:absolute;top:0;left:0;width:1920px;height:1080px;">
  <div class="page clean-bordered">
    <div class="wm"><img src="assets/keshet-logo.png" alt="Keshet Logo" style="height:56px;width:auto;vertical-align:middle;flex-shrink:0;filter:drop-shadow(0 4px 10px rgba(0,0,0,0.15));"></div>
    <div class="hd">
      <div class="eyebrow"><span class="dot"></span>השוואה / נתונים</div>
      <h1 class="title">כותרת השקופית</h1>
      <p class="sub">הסבר קצר.</p>
    </div>
    <div class="glass f1 fx col" style="padding:48px 56px;gap:22px;margin-top:34px;justify-content:center;">
      <!-- content here -->
    </div>
  </div>
</div>
```

Note: The `.rainbow-border` wrapper replaces the `.page` positioning — the inner `.page` uses `position:relative` (not absolute) when nested this way, and the outer wrapper is `position:absolute`.
````

- [ ] **Step 3: Update the slide-type table in SKILL.md Section 2 to include Clean Bordered**

Find the table row for "Comparison / two topics":
```
| Comparison / two topics | Two-column (Aurora, `.glass` + `.inkcard`) |
```

Add a new row after it:
```
| Data table / detailed comparison | Clean Bordered (`.clean-bordered`, rainbow wrapper) |
```

- [ ] **Step 4: Add `.clean-bordered` CSS to `template.html`**

In `template.html`, find the `.dark { ... }` line and add the two new rules after it:
```css
/* Clean Bordered — white slide with a 3px rainbow border on all 4 edges */
.clean-bordered { background: #FAFAF8; }
.rainbow-border { background: var(--ks); padding: 3px; border-radius: 24px; overflow: hidden; }
```

- [ ] **Step 5: Commit**

```bash
git add skills/keshet-presentation/SKILL.md template.html
git commit -m "feat: add Clean Bordered (Mode 3) CSS and snippet to skill and template"
```

---

### Task 5: Add HTML validation step to CI

**Files:**
- Modify: `.github/workflows/deploy.yml`

- [ ] **Step 1: Add a validate step before the prepare step**

In `.github/workflows/deploy.yml`, after the `Setup Pages` step, add:

```yaml
      - name: Validate HTML
        run: npx --yes html-validate@9 "*.html"
```

- [ ] **Step 2: Create `.htmlvalidate.json` in the repo root**

Create the file with these settings (permissive enough for the presentation patterns):

```json
{
  "extends": ["html-validate:recommended"],
  "rules": {
    "no-inline-style": "off",
    "prefer-native-element": "off",
    "void-style": "off",
    "no-trailing-whitespace": "off",
    "attr-quotes": "off",
    "require-sri": "off",
    "wcag/h30": "off",
    "wcag/h37": "warn",
    "no-redundant-role": "off",
    "heading-level": "off"
  }
}
```

- [ ] **Step 3: Verify the workflow step order is**

```
Checkout → Setup Pages → Validate HTML → Prepare artifact → Upload → Deploy
```

- [ ] **Step 4: Commit**

```bash
git add .github/workflows/deploy.yml .htmlvalidate.json
git commit -m "ci: add html-validate step to GitHub Actions pipeline"
```

---

### Task 6: Fix `index.html` — add missing Google Fonts preconnect hints

**Files:**
- Modify: `index.html` (line 7, `<head>` section)

- [ ] **Step 1: Open `index.html` and locate the fonts link**

It currently reads (line 7):
```html
  <link href="https://fonts.googleapis.com/css2?family=Heebo:wght@300;400;500;700;800&display=swap" rel="stylesheet">
```

There are no `<link rel="preconnect">` hints above it (unlike all presentation files which have them).

- [ ] **Step 2: Add preconnect hints before the fonts link**

Find:
```html
  <link href="https://fonts.googleapis.com/css2?family=Heebo:wght@300;400;500;700;800&display=swap" rel="stylesheet">
```

Replace with:
```html
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Heebo:wght@300;400;500;700;800&display=swap" rel="stylesheet">
```

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "fix: add Google Fonts preconnect hints to index.html"
```

---

### Task 7: Add `.gitignore`

**Files:**
- Create: `.gitignore`

- [ ] **Step 1: Create `.gitignore` in the repo root**

```
# OS
.DS_Store
Thumbs.db
desktop.ini

# Editor
.vscode/
.idea/
*.swp
*.swo
*~

# Build artifacts
_site/

# Cursor
.cursor/
```

- [ ] **Step 2: Commit**

```bash
git add .gitignore
git commit -m "chore: add .gitignore"
```

---

## Verification Checklist (run after all tasks)

Open each file in a browser and confirm:

- [ ] `index.html` — loads, shows both cards, fonts render correctly
- [ ] `template.html` — browser tab shows "שם המצגת — קשת", slides navigate with arrow keys
- [ ] `vibe-coding-guide.html` — unchanged, works as before
- [ ] `token-economics-guide.html` — unchanged, works as before
- [ ] GitHub Actions dry-run (push to a branch, not main): all 5 steps shown in the CI log, HTML validate passes

---

## Task Summary

| # | Finding | File | Severity |
|---|---------|------|----------|
| 1 | Scope deploy artifact (stop publishing internal files) | `deploy.yml` | 🟡 MAJOR |
| 2 | Add `<title>` and `<meta name="viewport">` | `template.html` | 🟡 MAJOR |
| 3 | Fix Cowork tool + hardcoded path | `SKILL.md` | 🟡 MAJOR |
| 4 | Add Mode 3 Clean Bordered to skill + template | `SKILL.md`, `template.html` | 🟡 MAJOR |
| 5 | Add HTML validator to CI | `deploy.yml`, `.htmlvalidate.json` | 🟡 MAJOR |
| 6 | Add Google Fonts preconnect to portal | `index.html` | 🟢 MINOR |
| 7 | Add `.gitignore` | `.gitignore` | 🟢 MINOR |
