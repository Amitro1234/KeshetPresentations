# Evidence-Based Verification Checker Protocol

> Based on the principles from *"Building Claude Skills That Verify Their Own Work"* (Ron Gold, August 2026).  
> **Key Principle:** A strong skill does not merely generate output; it evaluates its own work against binary, observable criteria and repairs any failures prior to completion.

---

## 1. Verification Philosophy

1. **Binary Criteria (Yes / No)**: Every check must be objectively answerable as `PASS` or `FAIL`. Subjective questions (e.g. "Does the slide look nice?") are forbidden.
2. **Observable Evidence**: A `PASS` status requires citing specific code lines, HTML tags, or attributes.
3. **Autonomous Self-Repair**: If ANY check returns `FAIL`, the model must immediately execute the repair step on the HTML file and re-evaluate before presenting the output to the user.

---

## 2. Mandatory 10-Point Binary Checklist

| # | Inspection Item | Binary Criterion (Pass/Fail) | Concrete Evidence Required |
|---|---|---|---|
| **C1** | **RTL & Language Header** | Does the root tag strictly equal `<html dir="rtl" lang="he">`? | Check line in HTML head. |
| **C2** | **Heebo Font Inclusion** | Is Google Fonts Heebo link present in the `<head>`? | `<link href="...family=Heebo...">` exists. |
| **C3** | **Official Logo Watermark** | Does EVERY single `.page` contain `<div class="wm...">` with `<img src="assets/keshet-logo.png"...>`? | Check `.wm` presence in each slide. |
| **C4** | **No SVG Logo Re-creation** | Is the logo rendered solely via the PNG asset (no SVG polygons/hand-drawn shapes)? | Verify absence of `<svg>` logo recreations. |
| **C5** | **Foreign Term Isolation** | Are ALL English words, brand names, and acronyms wrapped in `<span dir="ltr">...</span>`? | Verify terms like `Claude`, `API`, `LLM`, `RAG`. |
| **C6** | **Keshet Rainbow Presence** | Does EVERY slide feature the rainbow accent via `--ks`, `.spec`, `.specbar`, `.dot`, or `.rainbow-border`? | Verify gradient class/property on each slide. |
| **C7** | **Content Density Limits** | Does every slide respect density limits (max 5 bullets, max 3 stats, max 5 steps)? | Count elements per `.page`. |
| **C8** | **No Emojis** | Is the presentation 100% free of emoji characters? | Regex scan for Unicode emojis. |
| **C9** | **Navigation & Controls** | Is the complete `.nav-bar` markup and keyboard/fullscreen script present and untouched? | Verify Section 5 nav bar & JS block. |
| **C10** | **1920×1080 Print CSS** | Is the full `@media print` CSS block present ensuring 1920×1080 landscape output? | Verify `@media print` rules in `<style>`. |

---

## 3. Self-Repair Runbook (Fixes for Common Failures)

If a check fails, immediately apply the corresponding remediation:

```text
[Failure C1: Missing RTL]
-> Action: Replace opening tag with: <html dir="rtl" lang="he">

[Failure C3: Missing logo on slide N]
-> Action: Insert into slide N:
   Light slide: <div class="wm"><img src="assets/keshet-logo.png" alt="Keshet Logo" style="height:56px;width:auto;vertical-align:middle;flex-shrink:0;filter:drop-shadow(0 4px 10px rgba(0,0,0,0.15));"></div>
   Dark slide:  <div class="wm on-dark"><img src="assets/keshet-logo.png" alt="Keshet Logo" style="height:56px;width:auto;vertical-align:middle;flex-shrink:0;filter:drop-shadow(0 4px 10px rgba(0,0,0,0.35));"></div>

[Failure C5: Unwrapped English term]
-> Action: Wrap in <span dir="ltr">term</span>

[Failure C7: Content overflow (>5 bullets / >3 stats)]
-> Action: Split the content across two consecutive slides with a clean subtitle or "(חלק 2)".

[Failure C8: Emojis found]
-> Action: Replace emojis with Keshet styled numbers (<div class="numchip">), dots (<span class="dot">), or badges (<div class="chip">).
```

---

## 4. Verification Execution Schema

When concluding slide generation, perform the mental verification audit:

```markdown
### Verification Summary
- [x] C1: RTL Declared -> PASS (`<html dir="rtl" lang="he">` present)
- [x] C2: Heebo Font -> PASS (Google Fonts CDN loaded)
- [x] C3: Keshet Logo on All Slides -> PASS (`assets/keshet-logo.png` on slides 1..N)
- [x] C4: No SVG Logo Hacks -> PASS (Asset PNG used exclusively)
- [x] C5: LTR Spans on Technical Terms -> PASS (All technical terms isolated)
- [x] C6: Rainbow DNA on Every Slide -> PASS (`.spec` / `.specbar` / `.dot` present)
- [x] C7: Density Boundaries Respected -> PASS (Max 4 bullets / 3 cards per slide)
- [x] C8: No Emojis -> PASS (Zero emoji detected)
- [x] C9: Interactive Navigation -> PASS (Full nav-bar & JS included)
- [x] C10: Print-to-PDF Ready -> PASS (`@media print` included for 1920×1080)
```
