# Session Insight: Turning One Great Deck into a Reusable Brand System

**Date:** 2026-08-05
**Author:** Senior Presentation Systems Engineer

---

## Task / Problem Summary
After `token-economics-guide.html` was polished into a beautiful, on-brand slide deck, the goal shifted from *fixing one file* to *productizing the result*: create a generic starter so every future Keshet presentation "speaks the same language," and update the documentation so the docs match what actually ships.

---

## Root Cause (of the gap)
The design-system doc (`Keshet-slides-system.md`) still described an **older, aspirational spec**: a 1280×720 canvas with class names like `.slide--dark`, `.slide--light`, `.rainbow-text`, and 7 abstract templates. Meanwhile the **real, shipped deck** used a completely different and more refined system: a 1920×1080 `#deck` with `.page` slides, `.aurora`/`.dark` modes, `.glass`/`.inkcard` surfaces, `.spec`/`.specbar` rainbow helpers, an `<img>` logo in `.wm`, a frosted floating nav, JS scale-to-fit, and print rules. New authors reading the doc would have built something that looked nothing like the reference deck.

---

## What Went Well
1. **Single source of truth extraction.** The exact production CSS/JS was lifted verbatim from `token-economics-guide.html` into `template.html`, guaranteeing pixel-identical machinery rather than a re-implementation that could drift.
2. **Docs aligned to reality without destroying history.** Instead of rewriting the doc, an authoritative **Section 12 — Production Deck System** was appended that explicitly says "sections 1–11 are philosophy; this is what actually ships," with a class reference table.
3. **Author-proofing via comments.** `template.html` leads with a header comment block (how to add a slide, brand rules) and per-slide comments, so the template teaches usage in place.

---

## What Went Poorly
- The doc/implementation divergence had existed silently. It was only caught by reading the real HTML rather than trusting the spec — a reminder that "the code is the spec" for shipped artifacts.

---

## How It Was Solved
1. Read the full `token-economics-guide.html` to inventory every class and the nav/scale/print machinery.
2. Authored `template.html` with the same CSS/JS and 5 heavily-commented example slides (cover, two-column, stat/bars, dark section, closing grid) covering both visual modes.
3. Appended **Section 12** to `Keshet-slides-system.md` documenting the real tokens, modes, class table, official logo snippet, nav, and print flow.
4. Updated `README.md`: added a "Start from the template" workflow step, listed `template.html` and `keshet-logo.png` in the structure, and corrected the print description (1920×1080 pages, not A4).

---

## Tradeoffs or Alternatives Considered
- **Rewrite the whole design doc to the new system** vs. **append an authoritative section.** Chose to append (Section 12) — it preserves the brand philosophy content and the git history while making the production truth unambiguous and easy to point authors to.
- **Templating engine / partials for the logo header** vs. **copy-paste self-contained HTML.** Kept self-contained single-file decks (no build step) to match the existing zero-dependency, GitHub-Pages-friendly architecture.

---

## Tests Added or Updated
- No automated tests (static HTML/docs project). Verification was: `template.html` passed lint with no errors, and the CSS/JS was copied verbatim from the already-verified reference deck so behavior (scaling, nav, print) is known-good.

---

## Lessons Learned
1. **When productizing a one-off, extract, don't re-implement.** Copying the proven machinery avoids subtle drift between the "template" and the reference deck.
2. **Docs must be reconciled with the shipped artifact, not the original intent.** An authoritative "this is what actually ships" section is more valuable than a pristine but inaccurate spec.

---

## Follow-Up Actions
- [ ] Refactor `vibe-coding-guide.html` onto the `template.html` system so all decks match.
- [ ] Consider trimming/merging the older 1280×720 templates (Sections 5–6) or clearly labeling them as legacy, to reduce confusion with Section 12.
- [ ] Add local Heebo `.woff2` to `assets/fonts/` for fully offline PDF export.
