---
name: new-proposal
description: Scaffold a new proposal directory from the standard template. Use when starting a new white paper, proposal, or response. Creates the directory structure, copies boilerplate, and guides initial setup.
---

# New Proposal Skill

## Purpose
Create a clean, ready-to-use proposal workspace for a new effort.

## When to Use
- Starting a new white paper, proposal, or RFI response
- User says "new proposal", "start a proposal", "new white paper", or similar

## Workflow

### Step 1: Gather Basic Info
Ask the user for:
1. **Short name** (used as directory name, e.g., "socpac", "mystic-depot", "idx26")
2. **Full title** (e.g., "[Your Company] Support to SOCPAC")
3. **Customer/program** (e.g., "SOCPAC CTO Bala Selvam")
4. **Proposal type** — be specific: SBIR Phase I / SBIR Phase II / CSO / OTA / BAA / White Paper / Competitive RFP / IDIQ Task Order / RFI / Recompete
5. **Due date** (if known)

### Step 1b: Confirm Capture Mode
Default capture mode is **Responsive** for SBIR, CSO, OTA, BAA, and white papers.

For each new proposal, confirm or override:
> This proposal is a [type]. Suggested mode: **[Responsive / Full Capture]**.
> Keep this, or override?
>
> - **Full Capture** — for competitive RFPs, IDIQ task orders, recompetes: complete Bidder Comparison Chart, formal BOE, PPQ-format past performance
> - **Responsive** — for SBIR, CSO, OTA, BAA, white papers: competitive landscape overview, vehicle-appropriate pricing, relevant experience narratives

**Auto-suggest by type:**
- SBIR / CSO / OTA / BAA / White Paper → Responsive
- Competitive RFP / IDIQ Task Order / Recompete → Full Capture
- RFI → always Responsive

### Step 2: Create Directory Structure
Create `proposals/[short-name]/` with:
```
[short-name]/
├── inputs/
│   ├── 00_priority/
│   ├── 01_customer/
│   ├── 02_yourCompany/
│   ├── 03_teammates/
│   ├── 04_patterns/
│   ├── 05_graphics/
│   └── 06_notes/
├── working/
├── drafts/
└── reviews/
```

### Step 3: Seed Boilerplate
Copy these reference files into the appropriate input directories:
- `reference/boilerplate/company-description.md` → `inputs/02_yourCompany/`
- `reference/boilerplate/contract-vehicles.md` → `inputs/02_yourCompany/`
- `reference/boilerplate/past-performance.md` → `inputs/02_yourCompany/`
- `reference/boilerplate/components-table.md` → `inputs/02_yourCompany/`
- `reference/boilerplate/distribution-statements.md` → `inputs/00_priority/`

### Step 4: Create Proposal Brief
Create `working/proposal-brief.md` with:
```markdown
# [Full Title]

## Basics
- **Short name:** [short-name]
- **Proposal type:** [SBIR Phase I / CSO / OTA / BAA / White Paper / Competitive RFP / etc.]
- **Customer:** [customer/program]
- **Due date:** [date or TBD]
- **Created:** [today's date]

## Capture Mode
**[Full Capture / Responsive]** ← Edit this line to override for this proposal

- **Full Capture**: Complete competitive analysis (Bidder Comparison Chart), formal BOE cost volume, PPQ-format past performance
- **Responsive**: Competitive landscape overview, vehicle-appropriate pricing, relevant experience narratives
- *All skills read this field automatically. Change it here to change behavior across the entire proposal.*

## Key Questions to Answer
1. What problem does the customer have?
2. What is our company's unique value for this customer?
3. What specific commitments can we make?
4. What proof points are most relevant?
5. Who is the decision maker?

## Next Steps
1. Drop source materials (solicitation, customer context) into `inputs/00_priority/` and `inputs/01_customer/`
2. Run `/customer-intel` to research the customer and build a profile (AI-found facts + relationship template for you to fill in)
3. Run `/proposal-manager` to analyze the solicitation, build the compliance framework, assess bid/no-bid, and define win themes
4. Run `/competitor-assessment` (competitive bids only) to identify competitors, build the Bidder Comparison Chart, find teaming gaps, and generate strategy statements
5. Run `/capture-scorecard` to assess readiness across 9 dimensions before committing to full proposal effort
6. Run `/proposal-solution-architect` to design the solution against the approved plan and competitor assessment
7. Run `/past-performance` to map your PP repository to evaluation criteria and draft narratives
8. Run `/pricing-analyst` to build the cost model and cost volume narrative
9. Run `/proposal-graphics` to create visual concepts
10. Run `/proposal-writer` to draft sections
11. Run `/red-team-review` (Pink → Red → Gold → White Glove) to identify gaps before submission
```

### Step 5: Copy Graphics Templates
Copy branded HTML graphic templates from previous proposals (if they exist) into `inputs/05_graphics/` as starting points:
- `graphic-1-three-tier-architecture.html`
- `graphic-2-lifecycle-loop.html`
- `graphic-6-capabilities-table.html`
- `graphic-7-objectives.html`
- `graphic-8-operational-capabilities.html`

These are reusable templates — text content changes per proposal, visual structure stays the same.

### Step 6: Confirm Setup
Tell the user:
1. What was created
2. What to drop into `inputs/` next
3. Which skill to run first (`/proposal-manager`)

## Rules
- Always create the full directory structure, even if some folders will be empty initially
- Always seed the boilerplate files — they save 30+ minutes per proposal
- Always create the proposal brief — it's the anchor document for the effort
- If graphic templates exist from a previous proposal, copy them as starting points
