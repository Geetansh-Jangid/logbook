# Logbook Implementation Notes

1. **Content Structure:**
   - Articles are stored in `./content/logbook/<slug>/index.md`.
   - Observations are stored in `./content/observations/<slug>/index.md`.
   - Colocated assets (e.g. `./architecture.svg`) reside inside the corresponding entry's folder.
   - Slugs are automatically computed using Astro Content Layer glob loader with custom ID generator `({ entry }) => entry.replace(/\/index\.(md|mdx)$/, '').replace(/\.(md|mdx)$/, '')`.

2. **Styling and Design System:**
   - Typography: Uncut Sans for headings and body; JetBrains Mono NF for code blocks and inline code only.
   - Inline code is styled with high-contrast colors (`#FFA366` in dark, `#C2410C` in light).
   - Minimalist aesthetic: sharp square corners (`border-radius: 0`) on images, diagrams, cards, and modal dialogs.
   - Subtle minimal modal transitions (0.15s ease-out) without hover borders.

3. **Themes & Palette Cycling:**
   - Default color palette is Cursor (`#14120B` dark / `#F7F7F4` light with `#FF5A00` accent).
   - 15 available palettes: Cursor, Slate, Void, Obsidian, Ash, Charcoal, Graphite, Sepia, Sable, Noir, Fog, Steel, Stone, Silver, and Monochrome (plain black & white).
   - 4 continuous taps on the title words "logbook" or "observations" cycles to the next theme.
   - Long press / touch and hold resets the theme back to original (Cursor) and follows browser dark/light mode preference.
   - Re-renders Mermaid diagrams dynamically to reflect the current palette's colors.

4. **Deployment:**
   - Standard deployment under `PUBLIC_BASE_PATH=/logbook` or `PUBLIC_BASE_PATH=/`.
   - Canonical URLs reflect `SITE_URL` with full RSS, Atom, and JSON Feed syndication.
