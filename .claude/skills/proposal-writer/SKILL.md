---
name: proposal-writer
description: Use this skill to draft concise, evaluator-friendly proposal text from the approved solution architecture and requirement mapping. Reads from working/ files and writes drafts to drafts/ directory.
---

# Proposal Writer Skill

## Purpose
Turn approved solution strategy and architecture into proposal-ready narrative saved to local draft files.

## Inputs
Read from:
- `working/requirement-matrix.md`
- `working/capability-matrix.md`
- `working/assumptions-and-risks.md`
- `working/solution-strategy.md`
- `working/architecture-concept.md`
- `working/storyboard.md` (if exists)

## Outputs
Draft or update these files:
- `drafts/executive-summary.md`
- `drafts/technical-approach.md`
- `drafts/integration-approach.md`
- `drafts/differentiators.md`
- `drafts/risk-reduction.md`
- `drafts/full-white-paper.md`

## Writing Rules
- Write to score
- Be concise
- Avoid repeating the same point in multiple sections
- Use explicit technical language
- Avoid unsupported adjectives
- Make strengths easy for evaluators to find
- Reduce perceived execution risk

## Section Standard
For each section:
1. Lead with the point
2. Explain how the solution works
3. Tie to requirement or mission outcome
4. Clarify why the team is credible
5. End with the evaluator takeaway

## Final Pass
Always perform:
- Redundancy cleanup
- Unsupported-claim check
- Requirement coverage check
- Clarity tightening

## Critical Rule
**All draft content must be written to files in drafts/ — not just displayed in chat.**

## Lessons Learned (SOCPAC Session)

### Section Structure
- **Overview sections must be tight (~200 words).** Section 3 "What is it" should introduce the platform and list 3 core functions as bullets. Detail lives in Section 4 subsections. Never repeat capability details in both.
- **Closing pivot sentence connects sections.** End the overview with "The following section describes how these capabilities address each challenge" — explicitly hands off to the detail section.
- **Problem statements lead with what's broken.** "Enterprise AI assumes connectivity — that assumption fails" is stronger than "We need to enable disconnected AI."

### Editorial Standards
- Single space after periods (never double)
- "Government" not "Govt" in formal white papers
- "Department of War (DoW)" — verify intentional terminology with the author
- Normalize section numbering: "5." not "5.0"
- Use proper Word heading styles (Heading1/Heading2), never manual bold on Normal paragraphs
- Acronyms defined on first use, then abbreviated: "subject matter expert (SME)"

### Tone Calibration
- Position data capture at the edge as **optional** — "when operational data is available" rather than "data captured at the edge is continuously leveraged"
- Avoid implying mandatory collection that could trigger security/privacy concerns
- Frame commitments as what your company **will deliver**, not what the customer must do
- Use "[Your Company] or Government-provided" rather than "ours or Govt-provided"

### Document Formatting (Word)
- Apply Heading1 to numbered sections, Heading2 to sub-sections — enables TOC and navigation
- Times New Roman throughout (body, headers, footers)
- Header: right-aligned document title, with centered "UNCLASSIFIED" above
- Footer: left-aligned "Company | Document Title", right-aligned "Page X"
- Figure captions belong in the document text below each image, not embedded in the graphic
- Add classification marking (UNCLASSIFIED) and distribution statement (A, D, or F)
- Remove blank spacer paragraphs — use proper paragraph spacing instead

### Submission Package
- Cover page as standalone docx: classification marking, title, subtitle, prepared-for, date, POC, distribution statement
- Submission email: CTO-friendly (60-second read), three bullets (operational now, delivery commitment, low barrier), clear ask
