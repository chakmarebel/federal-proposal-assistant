---
name: red-team-review
description: Use this skill to review proposal drafts like a government evaluator and identify weaknesses, gaps, ambiguity, and redundancy. Reads from drafts/ and writes findings to reviews/.
---

# Red Team Review Skill

## Review Gate Mode
At the start of this skill, ask the user which review gate they want to run — or infer from context (e.g., if `reviews/compliance-check.md` doesn't exist yet → Pink; if it exists → Red or later).

| Mode | When to Run | Focus |
|------|------------|-------|
| **Pink Team** | After first complete draft | Compliance only — does every requirement have a response? |
| **Red Team** | After Pink issues resolved | Narrative quality and evaluator strength |
| **Gold Team** | After Red issues resolved | Mock evaluation — how would government evaluators score this? |
| **White Glove** | Final pass before submission | Editorial QA, formatting, submission checklist |
| **Full Review** | Default if no mode specified | All four passes combined |

If no mode is specified, ask before proceeding.

---

## Pink Team — Compliance Review

**Purpose:** Find every hole before writing quality is assessed. A non-compliant proposal is disqualified before it's evaluated.

**Inputs:** `working/requirement-matrix.md`, `working/proposal-plan.md` (compliance framework), all files in `drafts/`

**Process:**
1. Load the compliance framework from `working/proposal-plan.md`
2. For each requirement, find the specific paragraph(s) in the draft that address it
3. Mark as: ✅ Addressed / ⚠️ Partial / ❌ Missing

**Output table:**
| Req ID | Requirement | Status | Draft Location | Gap / Issue |
|--------|-------------|--------|---------------|-------------|

**Also check:**
- Required page limits not exceeded
- Required attachments present (resumes, past performance forms, etc.)
- Required formatting (fonts, margins, page numbers, headers/footers)
- Required section titles match solicitation language exactly

**Write to:** `reviews/compliance-check.md`

**Pink Team is complete when:** Zero ❌ Missing. All ⚠️ Partial items are either resolved or accepted risks.

---

## Red Team — Narrative Quality Review

**Purpose:** Read like a GS-14 evaluator with 15 minutes and a scoring rubric. Find everything that will cost points.

**Inputs:** All files in `drafts/`, `working/proposal-plan.md` (win themes, evaluation criteria), `working/competitor-assessment.md`

**Review categories:**
1. **Technical credibility** — is the architecture real and defensible?
2. **Differentiation** — why this team over competitors? Is it explicit?
3. **Evaluator clarity** — can every answer be found in under 30 seconds?
4. **Evidence** — every claim backed by proof (past performance, benchmarks, deployed systems)?
5. **Risk reduction** — are risks acknowledged and mitigated explicitly?
6. **Redundancy** — same content in multiple sections?
7. **Win themes** — are the 3-5 win themes woven through every section?
8. **Graphics alignment** — do visuals reinforce the narrative, or just decorate it?

**Output table:**
| Issue | Severity | Section | Why It Hurts Score | Recommended Fix |
|-------|----------|---------|-------------------|-----------------|

**Recommended rewrites:** For the top 3–5 issues, provide the specific rewritten text — copy-paste ready.

**Write to:** `reviews/red-team-notes.md`

---

## Gold Team — Mock Evaluation

**Purpose:** Simulate what the source selection board will do. Score the proposal against the evaluation criteria as if you are the government.

**Inputs:** All files in `drafts/`, evaluation criteria and weights from `working/proposal-plan.md`

**Process:**
1. For each evaluation factor, assign a rating: Outstanding / Good / Acceptable / Marginal / Unacceptable
2. Provide the rationale an evaluator would write
3. Identify what would need to change to improve the rating by one level

**Output:**

| Evaluation Factor | Weight | Rating | Evaluator Rationale | What Would Improve It |
|------------------|--------|--------|--------------------|-----------------------|
| [Factor 1] | High/Med/Low | Outstanding/Good/Acceptable/Marginal | | |

**Overall assessment:** Would we win based on this draft? Yes / Likely / Uncertain / No

**Write to:** `reviews/gold-team-assessment.md`

---

## White Glove — Final QA

**Purpose:** Catch everything that could embarrass the team or trigger a non-compliance finding on submission day.

**Checklist — run every item:**

**Editorial:**
- [ ] No double spaces after periods
- [ ] Consistent section numbering throughout (e.g., "5." not "5.0")
- [ ] No informal language (check: "Govt", "ours", "we've", contractions in formal sections)
- [ ] All acronyms defined on first use in each major section
- [ ] No run-on sentences; no sentence fragments
- [ ] Consistent verb tense throughout each section

**Formatting:**
- [ ] Page count within limits (by volume if applicable)
- [ ] Font, size, and margin compliance
- [ ] Heading styles applied correctly (not manual bold on Normal paragraphs)
- [ ] Figure captions present and numbered sequentially
- [ ] No floating/anchored images that may shift across systems
- [ ] Header and footer match requirements (document title, company, page numbers)
- [ ] Classification and distribution marking present (if required)
- [ ] Cover page complete with all required elements

**Content completeness:**
- [ ] All required attachments included (resumes, PPQs, certifications, representations and certifications)
- [ ] All cross-references resolve correctly
- [ ] No placeholder text remaining ([TBD], [TO BE PROVIDED], [INSERT])
- [ ] Pricing volume matches technical volume commitments (no orphaned commitments)

**Submission:**
- [ ] File naming convention matches solicitation requirements
- [ ] File format matches solicitation requirements (PDF, DOCX, etc.)
- [ ] Submission portal/method confirmed
- [ ] Submission deadline confirmed with timezone

**Write to:** `reviews/white-glove-checklist.md`

---

## Full Review (Default)
Runs all four passes in sequence. Write findings to all four output files. Present a consolidated summary at the end: total issues by severity, recommendation on whether the proposal is ready to submit.

---

## Output Files (by mode)
- Pink Team → `reviews/compliance-check.md`
- Red Team → `reviews/red-team-notes.md`
- Gold Team → `reviews/gold-team-assessment.md`
- White Glove → `reviews/white-glove-checklist.md`
- Full Review → all four files

**Critical Rule: Always write to files — never just display in chat.**

## Lessons Learned (SOCPAC Session)

### Structural Issues to Catch
- **Section duplication is the #1 problem.** Overview sections (e.g., "What is [Your Company]") and detail sections (e.g., "Addressing the Execution Gap") almost always repeat the same capabilities. Flag every instance and recommend which section should own which content.
- **Closing paragraphs that restate the section.** Section 2 closing ("These challenges are interconnected...") should pivot to the solution, not summarize the section. Flag circular closings.
- **Tables already in graphics.** If a capabilities table appears as both a graphic and inline text, flag the duplication and recommend removing one.

### Editorial Issues to Catch
- Double spaces after periods
- Inconsistent section numbering ("5.0" vs "5.")
- Informal language in formal documents ("Govt" → "Government", "ours" → "[Your Company]")
- Run-on sentences — especially when incorporating reviewer feedback (e.g., eval sentence with missing punctuation)
- Grammar breaks when mixing verb forms ("tasks integrating tools, reference local data" — inconsistent tense)
- Manual bold on Normal paragraphs instead of proper Heading styles

### Formatting Issues to Catch
- Missing figure captions/numbering
- Font mismatch between body (Times New Roman) and headers/footers (default Aptos)
- Floating images (anchored positioning) that may shift when document is opened on different systems
- Missing UNCLASSIFIED/distribution marking
- Missing header/footer document identification
- Blank spacer paragraphs instead of proper paragraph spacing

### Tone Issues to Catch
- Data capture framed as mandatory when it should be optional
- Commitments that imply customer obligations
- Hardware-specific claims (e.g., "16GB VRAM") when model selection isn't finalized
- Overpromising on timelines without qualifying assumptions

### Review Delivery Format
Present findings in two parts:
1. **Priority fixes table** — numbered, with severity (High/Medium/Low), location, and effort estimate
2. **Recommended rewrites** — for the top 3-5 issues, provide the specific rewritten text, not just a description of what to fix. The author should be able to copy-paste the fix.
