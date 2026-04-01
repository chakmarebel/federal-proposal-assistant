---
name: proposal-graphics
description: Use this skill to create proposal-ready architecture graphics, anchor graphics, and figure concepts with PowerPoint/Figma-ready structure. Reads from working/ files and writes graphic specs to working/graphics-brief.md.
---

# Proposal Graphics Skill

## Purpose
Translate the solution into clear visuals that strengthen evaluator understanding.

## Inputs
Read from:
- `working/solution-strategy.md`
- `working/architecture-concept.md`
- `drafts/technical-approach.md`
- Any existing images or architecture notes in `inputs/05_graphics/`

## Output
Write to `working/graphics-brief.md` with one section per graphic containing:
1. Graphic objective
2. Figure title
3. One-paragraph explanation
4. ASCII wireframe
5. Component list
6. Layout instructions for PowerPoint/Figma
7. Color/grouping logic
8. Caption text

## Design Rules
- One graphic = one core idea
- Use left-to-right or top-down flow
- Avoid crossing lines
- Reduce text inside boxes
- Group related elements clearly
- Distinguish:
  - Your company's components
  - Partner-provided components
  - Government-provided components
  - External systems/data

## Default Color Logic — Brand Palette
Use your company's brand palette unless the customer specifies otherwise. Update these values to match your brand:
- **Background:** `#191c20` (near-black)
- **Primary accent:** `#ee2929` (brand red) — titles, accent bars, pills, hero elements, glow effects
- **Dark grey:** `#393939` — borders, dividers, secondary structure
- **Medium grey:** `#9f9f9f` — secondary text, subtitles, captions
- **Light grey:** `#c8c8c8` — body text, descriptions
- **White:** `#ffffff` — headings, primary labels
- **Red tint backgrounds:** `rgba(238,41,41,.08)` to `rgba(238,41,41,.15)` — hero tier fills, callout backgrounds
- **Red accent borders:** `rgba(238,41,41,.4)` — commitment callouts, emphasis boxes

### Tier Treatment (for architecture graphics)
- **Enterprise tier:** `#2a2d31` fill, `#393939` stroke
- **GCC tier:** `#2a2d31` fill, `#393939` stroke
- **Edge/Tactical tier (hero):** `rgba(238,41,41,.08)` fill, `#ee2929` stroke — visually emphasized

### Element Patterns
- Title bars: white text, `border-bottom: 2px solid #ee2929`
- Registry/badge pills: `#ee2929` fill, dark text
- Commitment callouts: `rgba(238,41,41,.08)` fill, `#ee2929` border
- Glow filters: `flood-color: #ee2929`
- Row accent bars: 4px wide, `#ee2929`

## Output Formats
1. **Spec in working/graphics-brief.md** — ASCII wireframe, component list, layout instructions, color mapping, caption text
2. **Rendered HTML in inputs/05_graphics/** — browser-viewable HTML files that produce the actual graphic. These are the primary deliverable.

## Critical Rules
- **Write specs to working/graphics-brief.md**
- **Write rendered HTML graphics to inputs/05_graphics/**
- **Every graphic must be legible at half-page print scale** — this is non-negotiable

## Lessons Learned (SOCPAC Session)

### Sizing & Legibility
- **Half-page print is the target.** Every graphic will be screenshotted and embedded in a Word doc at ~5" wide. Design for this from the start.
- **Minimum font sizes:** Titles 28px, headings 22px, body text 17-19px, secondary text 15px, captions 14px. Anything smaller is unreadable when cropped.
- **Minimize whitespace aggressively.** Compact layouts read better at small sizes. Remove spacer elements, reduce padding, tighten gaps.
- **Test text overflow.** Long labels ("Automated LoRA & Fine-Tuning Platform") will overflow small SVG boxes. Always check that text fits within its container.

### Design Patterns That Worked
- **Three-tier architecture:** Horizontal bands stacked vertically, registry pills between tiers, dashed boundary lines with centered labels, flow arrows with tight text labels. Keep it to one scannable page.
- **Lifecycle loop:** Four nodes in a diamond with circular arc arrows. Flow label boxes sit beside the arcs, not on them. Center element holds the key concept.
- **Two-column layout:** Products vs. Services, Technical vs. Operational — column header carries the category, no per-item badges needed. Cleaner and more space-efficient.
- **Capability rows:** Left label column with red accent bar + right description. No emoji icons — accent bars are cleaner and more professional.
- **Swim lane timeline:** Three horizontal rows (Deploy/Adapt/Measure) with phase columns. Gate markers as diamonds below. Commitment callouts highlighted with brand red.

### Anti-Patterns to Avoid
- **Emoji icons in professional graphics.** Replace with accent bars, numbered circles, or simple geometric markers.
- **Text overlapping arrows or boundary lines.** Move labels above/below or into separate callout boxes beside the arrows.
- **IL-level badges (IL-5, IL-6) and DDIL zone badges inside boxes.** These clutter the graphic — mention in the caption text instead.
- **Figure numbers in the graphic title.** Captions with figure numbers belong in the document text, not the graphic itself.
- **Off-brand accent colors.** Stick to your brand palette. Avoid adding colors that aren't in your brand guide.
- **Key metric taglines at bottom of graphics.** These belong in the body text, not the graphic.

### Workflow
1. Write the spec to graphics-brief.md first (wireframe + layout instructions)
2. Build the HTML rendering immediately after — don't wait for approval of the spec alone
3. Show the HTML to the user for feedback
4. Iterate on the HTML directly — specs are reference, HTML is the deliverable
5. Captions are written separately for inclusion in the Word document
