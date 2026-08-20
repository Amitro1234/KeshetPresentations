# Design & Structure Guidelines for Corporate HTML Presentations (Keshet)

## Structure & Pagination
- Every presentation is built as a series of "slides," each a full-viewport panel, navigated one-at-a-time (not continuous scrolling).
- Each slide's content is centered both vertically and horizontally using flexbox.
- A floating navigation bar at the bottom: previous/next buttons, clickable dot indicators (one per slide), and a counter ("X / Y").
- Support keyboard navigation (arrow keys) and swipe gestures on mobile.
- Smooth transitions between slides (fade/scale), not abrupt jumps.

## Design & Color
- All colors are defined as global CSS custom properties at the top of the file — not hardcoded per slide. This ensures consistency and lets you update the color scheme in one place.
- A single unified theme across all slides (same background/gradient, same accent color palette) — the last slide (summary) must match the rest, not use a different design.
- A consistent "card" component (glassmorphism/rounded corners/subtle shadow) for all content boxes.
- Logo/branding (Keshet, mako) fixed in the same position on every slide.

## Animation — if used
- A subtle staggered "reveal" entrance animation for elements on each slide — refined and professional, not playful.
- Avoid overly "playful" effects (interactive particle animations, mouse spotlight) unless the guide targets a technical/younger creative audience — for internal corporate guides, restraint is preferred.

## Accessibility & Maintenance
- A single, clean HTML file organized with comments per slide (`<!-- SLIDE N: title -->`).
- Hebrew text with `dir="rtl"`.
- Responsive — test on both wide screens and mobile.

## How to use this
When starting work on a new guide with an AI assistant, attach this document and request: "Build the presentation following the attached presentation-guidelines document" — to maintain consistency across all corporate guides.