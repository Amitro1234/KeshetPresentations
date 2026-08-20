# Session Insight: Regenerating Diagram Infographic with SVG + Sharp

- **Timestamp**: 2026-08-13
- **Task Summary**: Regenerate the hand-drawn diagram `assets/img-token-breakdown.png` as a clean, modern, minimal 3-column infographic (1600x820px).
- **Root Cause & Constraints**: `pip install pillow` failed with HTTP 403 Forbidden on PyPI downloads in this environment. 
- **Solution**: Used Node.js + `sharp` to render a high-quality SVG vector graphic directly into PNG format.
- **Design Specifications Followed**:
  - Warm background `#F5F3EF`, top 6px Keshet rainbow gradient bar.
  - Three card columns with white fill, rounded corners, drop shadows, and color-coded headers:
    - Left (`#7B8FFF`): "What you can see" (`/cost`, `Console`, `/context`, `⚠ calculation bugs`)
    - Middle (`#FF8C42`): "What you need to see" (`Token attribution`, `Developer spend`, `Per-MCP cost`, `Config drift`)
    - Right (`#4CAF82`): "What you need to do" (`Model defaults`, `Remove unused MCPs`, `Compaction policy`, `Trim skills`)
  - Dark gray (#444444) zigzag/gap separator lines drawn between columns 1→2 and 2→3.
  - Centered bottom caption in italic gray font.
- **Outcome**: The updated image was committed and pushed to GitHub main, updating the live GitHub Pages presentation.
